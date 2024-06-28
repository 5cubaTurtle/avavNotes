Code to benchmark the `move` function vs passing by value thus copying:
```cpp
#include <chrono>
#include <iostream>
#include <vector>
#include <memory>
using namespace std;
using namespace std::chrono;


int COUNT = 50'000'000;

struct TimeIt
{
    system_clock::time_point start;
    TimeIt() {
        start = system_clock::now();
    }
    ~TimeIt() {
        auto runtime = duration_cast<milliseconds>(system_clock::now()-start).count();
        cout << runtime << " ms" << endl;
    }

};

void benchmark_copy(const vector<shared_ptr<int>> &vec_src)
{
    cout << "benchmark_copy" << endl;
    vector<shared_ptr<int>> vec_dst;
    vec_dst.reserve(COUNT);
    TimeIt ti;
    for(auto &sp : vec_src)
        vec_dst.emplace_back(sp);
}
void benchmark_move(vector<shared_ptr<int>> &&vec_src)
{
    cout << "benchmark_move" << endl;
    vector<shared_ptr<int>> vec_dst;
    vec_dst.reserve(COUNT);
    TimeIt ti;
    for(auto &sp : vec_src)
        vec_dst.emplace_back(move(sp));

}

int main (int arg, char **argv){

    vector<shared_ptr<int>> vec;
    for (int i = 0; i < COUNT; ++i)
        vec.emplace_back(new int);

    benchmark_copy(vec);
    benchmark_move(move(vec));

}
```
Clang compilation flags: `clang++ -std=c++17 -O3 -DNDEBUG`