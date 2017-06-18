# EasyRandom
[![Build Status](https://travis-ci.org/effolkronium/EasyRandom.svg?branch=develop)](https://travis-ci.org/effolkronium/EasyRandom)
[![Build status](https://ci.appveyor.com/api/projects/status/xv0aq60p91j1jnjr/branch/develop?svg=true)](https://ci.appveyor.com/project/effolkronium/easyrandom/branch/develop)
[![Coverage Status](https://coveralls.io/repos/github/effolkronium/EasyRandom/badge.svg?branch=develop)](https://coveralls.io/github/effolkronium/EasyRandom?branch=develop)
<a href="https://scan.coverity.com/projects/effolkronium-easyrandom">
  <img alt="Coverity Scan Build Status"
       src="https://scan.coverity.com/projects/12707/badge.svg"/>
</a>

Random without extra actions for modern C++
- [Design goals](#design-goals)
- [Integration](#integration)
- [Examples](#examples)

## Design goals

There are a few ways to get working with random in C++:
- **C style**

```cpp
#include <time.h>
#include <stdlib.h>

int main() {
  srand(time(NULL));   // should specify seed before using rand() function
  
  // returns a pseudo-random integer between 1 and 9
  return rand() % (9 - 1)) + 1;// should write your own distribution algorihtm
}
```
- **C++11 style**

```cpp
#include <random>

int main() {
  // create source of randomness, and initialize it with non-deterministic seed
  std::random_device r; //create random_device for seeding
  std::mt19937 eng{r()}; // choose and seed random engine

  // choose a specific distribution to generate a pseudo-random integer between 1 and 9
  std::uniform_int_distribution<> dist(1,9);
  
  return dist(eng) // call distribution with engine argument
}
```
- **Random style**

```cpp
#include "EasyRandom.hpp"

using EasyRandom::Random;

int main() {
  return Random::get(1, 9) // Invoke 'get' method to generate  a pseudo-random integer between 1 and 9
  // Yep, that's all.
}

```
EasyRandom class had these design goals:

- **Intuitive syntax**. You can do almost everything with random by simple 'get' method

- **Trivial integration**. All code consists of a single header file [`EasyRandom.hpp`](https://github.com/effolkronium/EasyRandom/blob/develop/source/EasyRandom.hpp). That's it. No library, no subproject, no dependencies, no complex build system. The class is written in vanilla C++11. All in all, everything should require no adjustment of your compiler flags or project settings.

## Integration

## Example
```cpp
Random::get();
```
