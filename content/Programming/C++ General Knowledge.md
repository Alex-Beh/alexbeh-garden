- Just use using, don't think too much
```
C++98
typedef std::string ABC;
typedef void (*FP) (int, const std::string&);

C++11
using ABC = std::string;
using FP = void (*) (int, const std::string&);

```
- enum class