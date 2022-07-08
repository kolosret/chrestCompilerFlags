# CHREST Compiler FLAGS
A set of shared compiler flags that can be used in c++ CMake projects.  This can be disabled during configure for any project using these with:

```bash
cmake -B ... -S ... -DenforceChrestCompilerFlags=OFF
```