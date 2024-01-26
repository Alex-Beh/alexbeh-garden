## How to add GTest into your project
- TEST(TestSuiteName, TestName)
	- static void SetUpTestSuite()：在第一个TEST之前运行
	- static void TearDownTestSuite()：在最后一个TEST之后运行
- TEST_F(TestFixtureName, TestName)
	- virtual void SetUp()：在TEST_F中测试案例之前运行；
	- virtual void TearDown()：在TEST_F之后运行。
```cpp
int main(int argc, char **argv) {
  printf("Running main() from %s\n", __FILE__);
  testing::InitGoogleTest(&argc, argv);
  return RUN_ALL_TESTS();   
}
```

## GTest Macro
### Assertion
- Success
- Non-fatal failure
- Fatal failure
### Expect
- EXPECT_EQ (\==)
- EXPECT_NE (!=)
- EXPECT_LT (<)
- EXPECT_LE (<=)
- EXPECT_GT (>)
- EXPECT_GE (>=)

## Sample code
```cpp
// in my_gtest_demo_1.cc
#include <gtest/gtest.h>

int add(int lhs, int rhs) { return lhs + rhs; }

int main(int argc, char const *argv[]) {

    EXPECT_EQ(add(1,1), 2); // PASS
    EXPECT_EQ(add(1,1), 1) << "FAILED: EXPECT: 2, but given 1";; // FAILDED

    return 0;
}
```

https://zhuanlan.zhihu.com/p/369466622