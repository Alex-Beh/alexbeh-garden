## std::lock_guard vs std::scoped_lock
-  std::lock_guard has an API that is a little safer to use than std::scoped_lock.
	No compile error for the following example if using std::scoped_lock

```cpp
## Incorrect usage
{
   std::scoped_lock lock;  // protect this block
}

## Correct usage
{
   std::scoped_lock lock{mut};  // protect this block
}
```
- General Advice
1. **lock_guard** if you need to lock **exactly 1 mutex** for an entire scope.
2. **scoped_lock** if you need to lock **a number of mutexes that is not exactly 1.**
3. **unique_lock** if you need to unlock within the scope of the block (which includes use with a **condition_variable**).

