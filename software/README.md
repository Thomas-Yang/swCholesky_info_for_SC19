
# swCholesky
swCholesky is based on parsy_bench(https://github.com/cheshmi/parsy_bench).

## build

### 1.build swGEMM
```bash
    cd swGEMM
    make lib
```

### 2. build swCHOLBLAS
```bash
    cd swCholesky/BLAS_sw
    make lib
```

### 3. build swCholesky

#### build pthread + swCHOLBLAS version
pthread number:: modify #define NUM_CG ?? , ?? should be 1,2,3,4
```bash
    cd swCholesky
    make -f makefile.all sw_cholesky
```

#### build mpe version (not support pthread)
```bash
    module load sw/compiler/gcc530
    cd swCholesky
    make -f makefile.mpe sw_cholesky
```

#### build xMath version (not support pthread)
```bash
    cd swCholesky
    make -f makefile.xmath sw_cholesky
```

## run
Download sparse positive definite matrices, which are of mtx format, to folder ../FloridaSparse/
Some matrices may be too large to run on one node, because of limited main memory
Generate metis permutation files using a x86 machine, to folder ../FloridaSparse/perm_x86/
Modify parameters in test.py, 
       1) mtx_path = ../FloridaSparse/
       2) perm_x86_path = ../FloridaSparse/perm_x86/ 

```bash
    python test.py
```
