# CMPE 283 - Assignment 1

## Questions
### 1.Team Details: Doing myself   
### 2. Describe in detail the steps you used to complete the assignment.  
In this assignment a kernel module is created which reads various MSR values to determine virtualization features present in CPU.   
>> I use Fedora as my OS so this assigment was performed on a Fedora installed machine. 
#### Steps followed to complete assignment
1. Copied source code provided in `cmpe283-1.c` and `Makefile` into a newly created directory.
2. Intel SDM was referred to identify bit numbers describing the capabilities for proc, exit and entry based controls.
3. Based on that 4 new instances of `capability_info` structs were created:  
    1) primary_proc_based
    2) secondary_proc_based
    3) exit_based
    4) entry_based
    - These instances contains bit number and description about what feature that bit represents.
4. Modified `detect_vmx_features` function to call `report_capabilities` 4 more times with appropriate parameters, to display proc, exit and entry based capabilities.
5. Included `MODULE_LICENSE()` in the module which is required to compile module. Commit showing these changes is https://github.com/hetjagani/cmpe283-1/commit/c3d50cb9276ff68cbe92c045bee04bdeb256671e
6. After modifying code the module was compiled using `make` command. This generated kernel object `cmpe283-1.ko` file which can be loaded into kernel.
7. Kernel module was loaded and removed from the kernel using following commands:
    - `sudo insmod cmpe283-1.ko` this command loads module into kernel
    - `sudo rmmod cmpe283-1` this command unloads module into kernel
8. To see the output of the module `dmesg` command is used to display kernel logs on terminal. The output of module is as follows: 
![Screenshot from 2022-04-14 10-02-07](https://user-images.githubusercontent.com/27214644/163438275-088dfda8-34e2-4817-8db1-e6090ae74d6f.png)
![Screenshot from 2022-04-14 10-02-32](https://user-images.githubusercontent.com/27214644/163438280-fcc1f6e4-9c5f-486f-8b2c-dc2d49d63ed5.png)
![Screenshot from 2022-04-14 10-02-44](https://user-images.githubusercontent.com/27214644/163438290-efcd3ab3-3aad-4f89-b3ca-f8d38f1f83f4.png)

