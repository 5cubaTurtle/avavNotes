#cpp

### Reading lines from file
```c++
#include <fstream>
#include <string>

int main() 
{ 
    std::ifstream file("Read.txt");
    std::string str; 
    while (std::getline(file, str))
    {
        // Process str
    }
}
```
### Reading numbers from file
```c++
// open file    
ifstream inputFile("/home/shared/data4.txt");
vector<double> rainfall;    // a vector to hold rainfall data

// test file open   
if (inputFile) {        
    double value;

    // read the elements in the file into a vector  
    while ( inputFile >> value ) {
        rainfall.push_back(value);
    }
```
