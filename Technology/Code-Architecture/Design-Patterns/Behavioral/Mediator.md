[Design Guru](https://refactoring.guru/design-patterns/mediator)
- Also known as: Intermediary, Controller
Mediator is a behavioral design pattern that lets you reduce chaotic dependencies between objects. The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object.

### UML
![[mediator.png]]

In this example, the **Mediator** pattern helps you eliminate mutual dependencies between various UI classes: buttons, checkboxes and text labels.
![[mediator_exmpl.png]]
An element, triggered by a user, doesn’t communicate with other elements directly, even if it looks like it’s supposed to. Instead, the element only needs to let its mediator know about the event, passing any contextual info along with that notification.

In this example, the whole authentication dialog acts as the mediator. It knows how concrete elements are supposed to collaborate and facilitates their indirect communication. Upon receiving a notification about an event, the dialog decides what element should address the event and redirects the call accordingly.

### C++ example
#### The problem:
```cpp
/**************
  mediator-pattern

    Implementation of a form with elements like buttons, checkboxes and text-boxes.
    The Problem: Lower level elements are coupled with eachother; for example NameTextBox 
    with SubmitButton or IsMarriedCheckbox with SpousesNameTextBox.
***************/

#include <iostream>


class InterfaceElement {
  protected:
    std::string name;
    bool isVisible = true;
  public:
    InterfaceElement(const std::string & name, bool isVisible) : name(name), isVisible(isVisible) {};
    void setVisibility(bool isVisible) { this->isVisible = isVisible; };
    std::string getDescription() {
        return isVisible
            ? name + " is visible"
            : name + " is NOT visible";
    }
};

class ButtonElement : public InterfaceElement {
  public:
    ButtonElement(const std::string & name, bool isVisible) : InterfaceElement(name, isVisible) {};
    virtual ~ButtonElement() {};
    virtual void click() = 0;
};

class TextBox : public InterfaceElement {
    std::string textValue = "";
  public:
    TextBox(const std::string & name, bool isVisible) : InterfaceElement(name, isVisible) {};
    virtual ~TextBox() {};
    virtual void changeText(const std::string & newValue) { textValue = newValue; };
};

class CheckBox : public InterfaceElement {
    bool isChecked = false;
  public:
    CheckBox(const std::string & name, bool isVisible) : InterfaceElement(name, isVisible) {};
    virtual ~CheckBox() {};
    virtual void setIsChecked(bool isChecked) { this->isChecked = isChecked; };
};

class SubmitButton : public ButtonElement {
  public:
    SubmitButton() : ButtonElement("Submit button", false) {};
    void click() override {
        std::cout << "Submitted!";
    }
};

class NameTextBox : public TextBox {
    SubmitButton *submitButton;
  public:
    NameTextBox(SubmitButton *submitButton) : TextBox("Name textbox", true), submitButton(submitButton) {};
    void changeText(const std::string & newValue) override {
        if (newValue.empty()) {
            submitButton->setVisibility(false);
        } else {
            submitButton->setVisibility(true);
        }
        
        TextBox::changeText(newValue);
    }
};

class SpousesNameTextBox : public TextBox {
  public:
    SpousesNameTextBox() : TextBox("Spouse's name textbox", false) {};
};

class IsMarriedCheckbox : public CheckBox {
    SpousesNameTextBox *spousesNameTextBox;
  public:
    IsMarriedCheckbox(SpousesNameTextBox *spousesNameTextBox) : CheckBox("Is married checkbox", true), spousesNameTextBox(spousesNameTextBox) {};
    void setIsChecked(bool isChecked) override {
        if (isChecked) {
            spousesNameTextBox->setVisibility(true);
        } else {
            spousesNameTextBox->setVisibility(false);
        }
        CheckBox::setIsChecked(isChecked);
    }
};

int main(int argc, const char * argv[]) {
    std::cout << "--- Mediator pattern testing ---\n";

    return 0;
}
```
#### Solution:
```cpp
/**************
  mediator-pattern

    Implementation of a form with elements like buttons, checkboxes and text-boxes.
    The Problem: Lower level elements are coupled with eachother; for example NameTextBox 
    with SubmitButton or IsMarriedCheckbox with SpousesNameTextBox.
***************/

#include <iostream>
#include <unordered_map>

using std::cout;

enum eEvents {
    NAME_ENTERED,
    NAME_ERASED,
    CHECKED_MARRIED,
    UNCHECKED_MARRIED
};

class InterfaceElement;

// Mediator Interface
class Mediator {
  public:
    virtual void notify(InterfaceElement* element, eEvents event) = 0;
};
// concrete implementation of Mediator interface will usually take the form of some container or manager. In this cas its PersonalInfoForm.


class InterfaceElement {
  protected:
    std::string name;
    bool isVisible = true;
    Mediator *form = nullptr;
  public:
    InterfaceElement(const std::string & name, bool isVisible) : name(name), isVisible(isVisible) {};
    void setVisibility(bool isVisible) { this->isVisible = isVisible; };
    std::string getDescription() {
        return isVisible
            ? name + " is visible"
            : name + " is NOT visible";
    }
    void setForm(Mediator* newform) { form = newform; };
};

class ButtonElement : public InterfaceElement {
  public:
    ButtonElement(const std::string & name, bool isVisible) : InterfaceElement(name, isVisible) {};
    virtual ~ButtonElement() {};
    virtual void click() = 0;
};

class TextBox : public InterfaceElement {
    std::string textValue = "";
  public:
    TextBox(const std::string & name, bool isVisible) : InterfaceElement(name, isVisible) {};
    virtual ~TextBox() {};
    virtual void changeText(const std::string & newValue) { textValue = newValue; };
};

class CheckBox : public InterfaceElement {
    bool isChecked = false;
  public:
    CheckBox(const std::string & name, bool isVisible) : InterfaceElement(name, isVisible) {};
    virtual ~CheckBox() {};
    virtual void setIsChecked(bool isChecked) { this->isChecked = isChecked; };
};



// ----- Leaf classes
class SubmitButton : public ButtonElement {
  public:
    SubmitButton() : ButtonElement("Submit button", false) {};
    void click() override {
        std::cout << "Submitted!";
    }
};

class NameTextBox : public TextBox {
public:
    NameTextBox() : TextBox("Name textbox", true) {};
    void changeText(const std::string & newValue) override {
        if (not newValue.empty())
            form->notify(this, eEvents::NAME_ENTERED);
        else
            form->notify(this, eEvents::NAME_ERASED);
        
        TextBox::changeText(newValue);
    }
};

class SpousesNameTextBox : public TextBox {
public:
    SpousesNameTextBox() : TextBox("Spouse's name textbox", false) {};
};

class IsMarriedCheckbox : public CheckBox {
public:
    IsMarriedCheckbox() : CheckBox("Is married checkbox", true) {};
    void setIsChecked(bool isChecked) override {
        if (isChecked)
           form->notify(this, eEvents::CHECKED_MARRIED);
        else
           form->notify(this, eEvents::UNCHECKED_MARRIED);

        CheckBox::setIsChecked(isChecked);
    }
};

class PersonalInfoForm: public Mediator {
  public:
    SubmitButton* submitBtn;
    NameTextBox* nametbox;
    SpousesNameTextBox*  spousesnametbox;
    IsMarriedCheckbox* marriedcbox;

    PersonalInfoForm(SubmitButton* sb, NameTextBox* ntb, SpousesNameTextBox* sntb, IsMarriedCheckbox* mcb):
        submitBtn(sb), nametbox(ntb), spousesnametbox(sntb), marriedcbox(mcb) {
        nametbox->setForm(this);
        marriedcbox->setForm(this);
    };

    void notify(InterfaceElement* element, eEvents event) override {
        switch (event) {
            case NAME_ENTERED:
                std::cout << "name entered\n";
                submitBtn->setVisibility(true);
                break;

            case NAME_ERASED:
                cout << "name erased\n";
                submitBtn->setVisibility(false);
                break;

            case CHECKED_MARRIED:
                cout << "checked married\n";
                spousesnametbox->setVisibility(true);
                break;

            case UNCHECKED_MARRIED:
                cout << "unchecked married\n";
                spousesnametbox->setVisibility(false);
                break;

            default:;
        }
    }

    void present() const {
        cout << "\n       ===== Form ========\n";
        cout << submitBtn->getDescription() << "\n" << nametbox->getDescription() << "\n" << spousesnametbox->getDescription() << "\n" << marriedcbox->getDescription() << "\n";
        cout << "       ===== End Form =====\n";
    }
};

int main(int argc, const char * argv[]) {
    cout << "--- Mediator pattern testing ---\n";
    PersonalInfoForm form( new SubmitButton,
                            new NameTextBox,
                            new SpousesNameTextBox,
                            new IsMarriedCheckbox);

    form.present();
    form.nametbox->changeText("Avner");
    form.present();
    form.marriedcbox->setIsChecked(true);
    form.present();
    form.nametbox->changeText("");
    form.marriedcbox->setIsChecked(false);
    form.present();
    form.submitBtn->click();

    return 0;
}
```