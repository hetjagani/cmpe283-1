# CMPE 283 - Assignment 1

## Questions
## 1.Team Details: Doing myself   
## 2. Describe in detail the steps you used to complete the assignment.  
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
