![319540675-6d1f3c1e-ee87-4c6d-93d0-7a953cf193ea](https://github.com/keerthanasivakumar02/Linux-IPC-Shared-memory/assets/150827397/5d123672-4fc4-4527-807a-20005a0b168d)# Linux-IPC-Shared-memory
Ex06-Linux IPC-Shared-memory

# AIM:
To Write a C program that illustrates two processes communicating using shared memory.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Shared Memory

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## Write a C program that illustrates two processes communicating using shared memory.
```
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/shm.h>

int main()
{
	// Generate a unique key using ftok
	key_t key = ftok("shmfile", 65);

	// Get an identifier for the shared memory segment using shmget
	int shmid = shmget(key, 1024, 0666 | IPC_CREAT);
      printf("Shared memory id = %d \n",shmid);
// Attach to the shared memory segment using shmat
	char* str = (char*)shmat(shmid, (void*)0, 0);
	
    printf("Write Data : ");
	fgets(str, 1024, stdin);

	printf("Data written in memory: %s\n", str);

	// Detach from the shared memory segment using shmdt
	shmdt(str);

	return 0;
}
```




## OUTPUT



![319540675-6d1f3c1e-ee87-4c6d-93d0-7a953cf193ea](https://github.com/keerthanasivakumar02/Linux-IPC-Shared-memory/assets/150827397/ba14dba3-f835-4256-a8a6-599f8e2c46f0)

# RESULT:
The program is executed successfully.
