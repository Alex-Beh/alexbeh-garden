- `norm()` is the [Frobenius norm](http://mathworld.wolfram.com/FrobeniusNorm.html), the square root of the sum of squares of the components.
- `.normalized()` returns a copy to the original object divided by this norm (i.e. the original object is not changed).
- `.normalize()` divides an object in-place by this norm (i.e. the original object itself is modified).

## Code Example

```c++
Eigen::Vector3d vectorA(1.0, 2.0, 3.0);

auto vectorA_norm = vectorA.norm(); // = 3.74166
// equivalent to sqrt(1*1+2*2+3*3)

auto clone_vectorA = vectorA;

auto normalized_vectorA = vectorA.normalized();
// vectorA == clone_vectorA;

vectorA.normalize();
// vectorA != clone_vectorA;
```

https://stackoverflow.com/questions/48019329/difference-between-norm-normalize-and-normalized-in-eigen
