CSV Parser
---

Simple CSV parser that uses templates

Available methods

```cpp
template<typename ... Columns>
bool check_header(Columns &&... cols); // check file header

template<typename ...Args>
bool read_row(Args &... args); // read all values from next line

template<typename Arg>
bool read_col_value(Arg &arg, std::size_t col); // read value from specific column from next line
```

Usage example

```cpp
#include
"CSVParser.h"

int main(){
    CSVParser csvParser("file.csv", 5);
    if (!csvParser.check_header("id", "age", "height", "name", "type")) return 0;
    unsigned long id;
    unsigned int age;
    double height;
    std::string name;
    std::string str_type;
    while (csvParser.read_row(id, age, height, name, str_type)) {
        //do smth
    }
    //...
}
```

**FileReader**

Helper class used as a wrapper of `ifstream`

Available methods

```cpp
bool open_db();
void close_db();
bool is_open() const;
std::string read_line();
bool check_file(); //check if file exists and can be opened for reading
void reset();
bool is_eof() const;
```