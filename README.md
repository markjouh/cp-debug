# cp-debug

A debug header for competitive programming.

## Features
- Single header, dependency-free
- ANSI colors to distinguish debug text and for improved readability
- Easily customizable output format

## Setup
Just clone this repo and include it with `-I/your-install-path` when compiling your solutions. That's all.

Optionally, use an `#ifdef` statement like shown in the example below to disable debug statements when compiled on judge machines.

## Example

### sandbox.cpp
```cpp
#include <array>
#include <map>
#include <vector>

#ifdef LOCAL
#include <debug>
#else
#define dbg(...)
#endif

using namespace std;

int main() {
    dbg("String literals look like this");

    vector<vector<int>> vec2d_uneven = {{1}, {22, 333}, {4444, 55555, 666666}};
    dbg("Brackets and parentheses describe the shape of containers", vec2d_uneven);

    vector<int> vec1d = {1, 22, 333};
    vector vec2d = {vec1d, vec1d, vec1d, vec1d};
    vector vec3d = {vec2d, vec2d};
    dbg("Grids are detected from the shape and formatted accordingly", vec1d, vec2d, vec3d);

    tuple<char, int, string> tup3 = {'a', 1, "abcdefg"};
    dbg("Arbitrary tuple types work", tup3);

    map<int, array<tuple<char, int, string>, 2>> mp;
    mp[0] = {tup3, tup3};
    mp[255] = mp[0];
    dbg("Any combination of valid types can be printed", mp);
}
```

### Terminal Output
<img width="872" alt="image" src="https://github.com/user-attachments/assets/da3f0750-adff-49fb-afb8-8e9d9b8a0c9f">

