**Also known as**: CoR, Chain of Command.
[Refactoring Guru](https://refactoring.guru/design-patterns/chain-of-responsibility)
Used when a series of nested handlers are needed.
The Chain of Responsibility design pattern is used to pass a request along a chain of handlers. Each handler decides if it can handle the request, and if not, it forwards it to the next handler in the chain. This allows you to create flexible systems that can handle different types of requests without knowing exactly who will handle them beforehand.

![[chain-of-responsibility_uml.png]]
### C++ example:
Chain of Responsibility design pattern, allows to delegate the various responsibilities of brother classes in a sequential manner. It promotes maintainability of sequential and reusable code.
```cpp
/*
    The follwoing application validates strings.
    The different strings it can validate could be login-name, emails-address or password.
*/

#include <iostream>
#include <regex>
#include <vector>

using std::string;

// Handrler interface
class StringValidator {
public:
    virtual ~StringValidator() {};
    virtual StringValidator* setNext(StringValidator* nextValidator) = 0;
    virtual string validate(string) = 0;
};

class BaseValidator: public StringValidator {
protected:
    StringValidator *next = nullptr;
public:
    virtual ~BaseValidator() { delete next; };
    StringValidator* setNext(StringValidator* nextValidator) override {
        next = nextValidator;
        return nextValidator; // this allows to chain validators. See main()
    }

    virtual string validate(string testString) {
        if(next)  // go to next validator if there is one
            return next->validate(testString);
        return "Success!";  // last one in the chain
    }
};

class NotEmptyValidator: public BaseValidator {
public:
    string validate(string testString) {
        puts("Checking if empty...");
        
        if(testString.empty())
            return "Please enter a value";

	  // returning the base validator will invoke the next validator in chain
        return BaseValidator::validate(testString);
    }
};

class LengthValidator: public BaseValidator {
    int minLength;
public:
    LengthValidator(int minLength) : minLength(minLength) {};
    std::string validate(std::string testString) override {
        std::cout << "Checking if length not less than " << minLength << "...\n";
        
        if (testString.length() < minLength)
            return "Please enter at least " + std::to_string(minLength) + "characters\n";
        
        return BaseValidator::validate(testString);
    }
};

class RegexValidator: public BaseValidator {
    std::string patternName;
    std::string regexString;
public:
    RegexValidator(string patternName, string regexString)
    : patternName(patternName), regexString(regexString) {};
    string validate(string testString) override {
        std::cout << "Checking if string is a valid " << patternName << "...\n";
        
        if (!std::regex_match(testString, std::regex(regexString))) {
            return "The value entered is not a valid " + patternName;
        }
        
        return BaseValidator::validate(testString);
    }
};

bool in_vector(const string &value, const std::vector<string> &v) {
    return std::find(v.begin(), v.end(), value) != v.end();
}

class HistoryValidator: public BaseValidator {
    std::vector<std::string> historyItems;
public:
    HistoryValidator(std::vector<std::string> historyItems) : historyItems(historyItems) {};
    std::string validate(std::string testString) override {
        std::cout << "Checking if string is in history...\n";
        
        if (in_vector(testString, historyItems))
            return "Please enter a value that you haven't entered before";
        historyItems.push_back(testString);  
        
        return BaseValidator::validate(testString);
    }
};

int main(int argc, const char* argv[]) {
    std::cout << "Hdello There!" << std::endl;

    StringValidator* emailValidator = new BaseValidator;

    emailValidator->setNext(new NotEmptyValidator)
                  ->setNext(new RegexValidator("email address", "^\\w+([-+.']\\w+)*@\\w+([-.]\\w+)*\\.\\w+([-.]\\w+)*$"));

    std::cout << "Checking Emails ---------------\n";
    std::cout << "Input: \n" << emailValidator->validate("") << "\n\n";
    std::cout << "Input: shaun\n" << emailValidator->validate("shaun") << "\n\n";
    std::cout << "Input: shaun@test.com\n" << emailValidator->validate("shaun@test.com") << "\n\n";
    delete emailValidator;

    StringValidator* passValidator = new BaseValidator;
    std::vector<string> passHistory;
    passValidator->setNext(new NotEmptyValidator)
                 ->setNext(new LengthValidator(5))
                 ->setNext(new HistoryValidator(passHistory));

    std::cout << "Checking passwords ---------------\n";
    std::cout << "Input: \n" << passValidator->validate("") << "\n\n";
    std::string pass_0 = "shaun";
    std::cout << "Input: "+pass_0+"\n" << passValidator->validate(pass_0) << "\n\n";
    std::cout << "Input: shaun@test.com\n" <<  passValidator->validate("shaun@test.com") << "\n\n";
    std::cout << "Input: cahn\n" << passValidator->validate("cahn") << "\n\n";
    std::cout << "Input: zag4a*be\n" << passValidator->validate("zag4a*be") << "\n\n";
    std::cout << "Input: "+pass_0+"\n" << passValidator->validate(pass_0) << "\n\n";
    delete passValidator;

    return 0;
}
```