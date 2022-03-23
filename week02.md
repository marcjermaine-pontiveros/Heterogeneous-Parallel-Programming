# Basic CUDA Programming

Based on this [link](https://ulhpc-tutorials.readthedocs.io/en/latest/cuda/).

The tutorial will cover the aspects of the following:

- Write, compile and run C/C++ programs that both call CPU functions and launch GPU kernels.
- Control parallel thread hierarchy using execution configuration.
- Allocate memory on both GPU and CPU.
- Profile and improve the performance of your application.

## Hello World from GPU

```c
//hello-world.c
#include <stdio.h>

void c_function()
{
    printf("Hello World!");
}

int main()
{
    c_function();
    return 0;
}
```

```c
// hello-world.cu 
#include <stdio.h> 

__global__ 
void cuda_function()
{
   printf("Hello World from GPU!\n"); 
    __syncthreads();               
    // to synchronize all threads
}

int main()
{
    cuda_function<<<1,1>>>();
    cudaDeviceSynchronize();      // to synchronize device call
    return 0;
}


```