. Test cases drive the design
. You write the tests first then you write the code to make the test pass
. This keeps you focused on the purposes of the code
. code is of no use if your client can't call it

Why developers don't test
. I already know my code works!
. I don't write broken code !
. I have no time!

Basic TTD workflow

```
                    |-- [RED/fail] ------|
                    |                   | write a test case that fails
                    |                   |
                  [REFACOR]--------[Green/ pass]
                  
                    Improve code quality
```

Why is TTD important for DevOps?
. It saves time when developing
. You can code faster and with more confidence
. It ensures the  code is working as expected
.In order to create a DevOps CI/CD pipeline, all testing must be automated