# Fall2021-CS481-mpi-examples
## MPI Example Programs

`mpi_vec_sum.c` - allocate and initialize vector locally

`mpi_vec_sum2.c` - allocate and initialize vector on process with rank 0 and use MPI_Scatter to distribute the vector

`mpi_vec_sum3.c` - allocate and initialize vector on process with rank 0 and use MPI_Scatterv to distribute the vector

`blocking.c` - uses blocking send and receive functions to implement a simple broadcast

`nonblocking.c` - uses nonblocking send and receive functions to implement a simple broadcast


## Instructions for compiling and running the programs
Here are few important steps that you MUST follow in order to compile and run MPI programs on the DMC Cluster.

1. Make sure to add `module load openmpi/4.0.5-gnu-pmi2` in the file `~/.bashrc.local.dmc` (make sure that this line added at the end of this file)
2. Remember to logout and login again after adding the line to the `~/.bashrc.local.dmc` file (otherwise, you have to type `module load openmpi/4.0.5-gnu-pmi2` at the command prompt in your shell)
3. If you have completed the above steps and login to the DMC cluster, if you type `which mpicc` you should get the output that looks like this:
```
/mnt/beegfs/apps/dmc/apps/spack_0.15.4/spack/opt/spack/linux-centos7-ivybridge/gcc-9.3.0/openmpi-4.0.5-3xsnyi5ejr5527mpmzwso7kp5lunfbxt/bin/mpicc
```
4. Compile the MPI programs from the textbook or the sample program I have provided using mpicc
5. Create a SLURM job submission script, say, `myscript.sh`, and make sure to enter the following:
```
#!/bin/bash
module load openmpi/4.0.5-gnu-pmi2
srun --mpi=pmi2 ./mat_vec_sum 500000
srun --mpi=pmi2 ./mat_vec_sum 500000
srun --mpi=pmi2 ./mat_vec_sum 500000
```
6. The only change you should make in the above file would be to change the name of the executable and other argument you provide to your program. Otherwise, the first two lines should not be changed.
7. Change the file permissions to have execute permission using the command: 
```
chmod +x myscript.sh
```
9. Use `run_scrip_mpi` to submit the job and make sure to choose the `class` queue and request `number of cores = number of processes.`
