[Refactoring Guru](https://refactoring.guru/design-patterns/command)
- Also known as: Action, Transaction
Command is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you pass requests as a method arguments, delay or queue a request’s execution, and support undoable operations.

![[command.png]]
### C++ example
```cpp
/*
	Psudo implementation of a drawing app. Each operation like adding a shape to a canvas or clearing the canvas is decoupled from the button class. Allowing the same operation to be used by several elements in the GUI, i.e. buttons, drop-down-menues, shortcuts, etc.
*/

#include <iostream>
#include <vector>
#include <iterator>

class Canvas {
    std::vector<std::string> shapes;
public:
    void addShape(const std::string & newShape) {
        shapes.push_back(newShape);
    };
    void clearAll() {
        shapes.clear();
    };
    std::vector<std::string> getShapes() { return shapes; };
};


class Command {
public:
    virtual ~Command() {};
    virtual void execute() = 0;
};

class AddShapeCommand: public Command {
    std::string shapeName;
    Canvas* canvas;
public:
    AddShapeCommand(const std::string& shapeName, Canvas* canvas):
        shapeName(shapeName), canvas(canvas) {};
    void execute() { canvas->addShape(shapeName); };
    void rename(const std::string newName) { shapeName = newName; };
};

class ClearCommand: public Command {
    Canvas* canvas;
public:
    ClearCommand(Canvas* canvas):canvas(canvas) {}
    void execute() {
        std::cout<< "Clearing the canvas..." << std::endl;
        canvas->clearAll();
    }
};


class Button {
    Command& command;
public:
    Button(Command& command):command(command) {};
    void click() { command.execute(); }
};

std::string vector2string(const std::vector<std::string> &v) {
    std::string result;
    if (v.empty())
        return "Empty vector";
    else
        for(const std::string& element : v)
            result.append(element + ", ");
    return result;
}

int main(int argc, const char * argv[]) {
    Canvas canvas;
    AddShapeCommand addTriangleCmd("triangle", &canvas);
    AddShapeCommand addSquareCmd("square", &canvas);
    ClearCommand clearCmd(&canvas);

    Button triangleButton(addTriangleCmd);   
    Button squareButton(addSquareCmd);
    Button clear(clearCmd);

    triangleButton.click();
    squareButton.click();
    triangleButton.click();
    triangleButton.click();
    addTriangleCmd.rename("jazo");
    triangleButton.click();
    std::cout<< vector2string(canvas.getShapes()) << std::endl;
   
    clear.click();
    std::cout<< vector2string(canvas.getShapes()) << "\n";

    return 0;
}
```