# cs330---assignment-3-solved
**TO GET THIS SOLUTION VISIT:** [CS330 – Assignment 3 Solved](https://www.ankitcodinghub.com/product/cs330-assignment-3-solved-5/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;115625&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS330 - Assignment 3 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
CS330: Operating Systems

1 Introduction

As part of this assignment, you will be implementing system calls in a teaching OS (gemOS), same as in Assignment-2. We will be using a minimal OS called gemOS to implement these system calls and provide system call APIs to the user space. The gemOS source can be found in the src directory. This source provides the OS source code and the user space process (i.e., init process) code (in src/user directory).

gemOS is a teaching operating system. Typically OS boots on a hardware. To set up

the gemOS, you can refer to the document (Documentation/gemOS Setup.pdf)

The Syscalls Specifications

The specifications of the systems calls that you need to implement are explained below.

• void *mmap(void *addr, sizet length, int prot, int flags)

• int munmap(void *addr, size t length)

• int mprotect(void *addr, size t length, int prot)

• int cfork(void)

• int vfork(void)

mmap(void *addr, size t length, int prot, int flags)

If addr is NULL, then you have to choose a address which is page aligned in the virtual address space to create the mapping. If addr is not NULL, then it should be considered as a hint about where to place the mapping. If requested mappings are free, then you can either create a new mapping or merge with the existing mapping based on the scenarios explained below.

Without hint address

• Always create new mapping (vm area) starting from MMAP AREA START (start) to MMAP AREA END (end). You shouldn’t create new mapping in intermediate addresses unless hint address is specified.

• The subsequent mapping (new mapping) should be created in next contiguous free address in the virtual address space.

• While merging, always choose the first immediate available free space in the virtual address space

With hint address

• When the new mapping follows the end of an existing mapping and has same protection flags as the the existing one, new mapping should be merged with the existing mapping. (Refer to case 1 in the following diagram)

• When the new mapping’s end is followed by the start of an existing mapping and has same protection flags as the existing one, new mapping should be merged with the existing mapping. (Refer to the case 2 in the following diagram)

• When the new mapping cannot be merged with any of the existing mappings, a new mapping should be created (Refer to the case 3 in the following diagram)

Figure 1: mmap with hint addres

The prot argument describes the desired memory protection of the mapping. It can be bitwise OR of one or more of the following flags:

• PROT READ – The protection of the mapping (vm area) is set to READ ONLY. The physical pages which map to this vm area are also set to READ ONLY. If any process tries to write on this physical page it will result in SIGSEGV

• PROT WRITE – The protection of the mapping (vm area) is set to WRITE ONLY. When it comes to physical pages, PROT WRITE implicitly provides read access to them. Hence the physical pages which map to this vm area will have READ WRITE access.

The usage of flags argument is explained below.

• MAP FIXED – Don’t interpret addr as a hint: place the mapping at exactly that address which is passed as an argument to the mmap function. addr must be page-aligned and should be in the multiple of page size. If the specified address is already mapped with some vm area. Then it cannot be used, mmap() will fail in that case.

• MAP POPULATE – Map the physical pages to the mappings(vm area) at the time of creation. If a mapping (vm area) is created without using MAP POPULATE flag. Then created mapping will not have any physical pages mapped with it. The physical pages are mapped on demand (Lazy allocation) whenever they are accessed. The access will in turn result in a page fault and then physical pages are mapped (huge overhead).

RETURN VALUE

On success, mmap() returns a pointer to the mapped area. On error, returns (-1) or EINVAL

munmap(void *addr, size t length)

The munmap() system call deletes the mappings for the specified address range. After the deletion, vm area can either be shrunk or split into two vm area (refer the below figure). Any access to addresses within the deleted vm area result in invalid memory references.

The address addr must be a multiple of the page size (but length need not be). Assume that address passed as an argument is always page aligned. All pages containing a part of the indicated range are unmapped, and subsequent references to these pages will generate SIGSEGV. It is not an error if the indicated range does not contain any mapped pages.

Figure 2: Unmapping of the VM area

RETURN VALUE

On success, munmap() returns 0. On failure, it returns -1 or EINVAL)

mprotect(void *addr, size t length, int prot)

mprotect changes the access protections for the calling process’s memory pages containing any part of the address range in the interval (addr, addr+ len-1). Assume that addr provided as argument is always page aligned. mprotect might create, expand or shrink the vm area mapping(refer to the below figure).

Figure 3: Unmapping of the VM area

If the calling process tries to access memory in a manner that violates the protections, then the kernel generates a SIGSEGV signal for the process. As we are updating the access rights of certain regions in the vm area, the access rights should also be updated accordingly in the underlying physical pages as well if they exist.

The prot argument describes the desired memory protection of the mapping. It can be bitwise OR of one or more of the following flags:

• PROT READ – The protection of the mapping (vm area) is set to READ ONLY. The physical pages which map to this vm area are also set to READ ONLY. If any process tries to write on this physical page, it will result in SIGSEGV

• PROT WRITE – The protection of the mapping (vm area) is set to WRITE ONLY. When it comes to physical pages, PROT WRITE implicitly provides read access to physical pages. Hence the physical pages which map to this vm area will have READ WRITE access.

RETURN VALUE

On success, mprotect() returns 0. If the provided addr does belong to the existing vm area mapping. then mprotect will fail and returns either (-1) or (EINVAL)

cfork(void)

cfork() creates a new process by duplicating the calling process. The new process is referred to as the child process. The calling process is referred to as the parent process.

The child and the parent process run in separate memory spaces. At the time of cfork() both memory spaces have the same content. After cfork(), a write performed by parent or child results in copying of the page and thus child and parent stops sharing the page.

The child and parent has separate user and kernel stack and memory areas shared by them till copy-on-write happens are data segment, mmaped regions. The child and parent continue sharing code region since it is read only regions.

The child process is an exact duplicate of the parent process except for the following points:

• The child has its own unique process ID.

• The child’s parent process ID is the same as the parent’s process ID.

Example

1. int main()

2. {

3. int pid;

4. char * mm1 = mmap(NULL, 4096, PROT_READ|PROT_WRITE, 0);

5. if(mm1 &lt; 0)

6. {

7. printf(“Map failed “);

8. return 1;

9. }

10. mm1[0] = ’A’;

11. pid = cfork();

12. if(pid){

13. mm1[0] = ’B’;

14. printf(“mm1[0] inside parent:%c “,mm1[0]);

15. }

16. else{

17. printf(“mm1[0] inside child:%c “,mm1[0]);

18. }

19. }

Figure 4: After parent called cfork()

After parent performs cfork, the parent and child continues to share the memory regions as shown in figure 4.

Figure 5: After parent writes

After cfork, parent writes to the mapped area as shown in line number 13, which results in copy-on-write and child and parent stops sharing the memory area as shown in figure 5.

mm1[0] inside child:A mm1[0] inside parent:B

In the output shown above, as you can see, the child still sees the unmodified value where as the parent prints the new value.

RETURN VALUE

On success, the PID of the child process is returned in the parent, and 0 is returned in the child. On failure, -1 is returned in the parent, no child process is created, and errno is set appropriately.

vfork(void)

vfork(), just like cfork(), creates a child process of the calling process. vfork() create new processes without copying the page tables of the parent process.

vfork() differs from cfork() in that the calling thread is suspended until the child terminates ( by calling exit(), or abnormally, after delivery of a fatal signal). Until that point, the child shares all memory with its parent, including the stack.

The child and parent has separate kernel stack and memory areas shared by them till child exits are user stack, data segment, mmaped regions, and code.

Example

1.int main()

2.{

3. int pid;

4. char * mm1 = mmap(NULL, 4096, PROT_READ|PROT_WRITE, 0);

5. if(mm1 &lt; 0)

6. {

7. printf(“Map failed “);

8. return 1;

9. }

10. mm1[0] = ’A’;

11. pid = vfork();

12. if(pid)

13. {

14. printf(“mm1[0] inside parent:%c “,mm1[0]);

15. }

16. else

17. {

18. mm1[0] = ’B’;

19. printf(“mm1[0] inside child:%c “,mm1[0]);

20. exit(0);

21. }

22.}

Figure 6: After parent called vfork()

After parent performs vfork, the parent and child continues to share the memory regions as shown in figure 6. The parent is in waiting state after vfork, and child is ready for scheduling. The parent continues in waiting state until child exits.

Figure 7: child writes and exits

After vfork, child writes to the mapped area and exits by calling exit(0).

mm1[0] inside child:B mm1[0] inside parent:B

In the output shown above, as you can see, the parent prints the value which is written by the child.

RETURN VALUE

On success, the PID of the child process is returned in the parent, and 0 is returned in the child. On failure, -1 is returned in the parent, no child process is created, and errno is set appropriately.

Background and Utilities

We have already provided a detailed specification of system calls that you need to implement. In order to make things easier, we have given some template functions, structures and a few utility functions that facilitate object creation and deletion. Lets have look at those functions.

The process control block (PCB) is implemented using a structure named exec context defined in src/include/context.h. One of the important members of exec context for this assignment is the structure structure.

struct vm area:

vm start – The starting address (virtual address) of the vm area mappings.

vm end – The ending address (virtual address) of the vm area mappings.

access flags – The Protection or access flags of the current vm area mappings.

vm next – The pointer to the next vm area mappings.

struct vm area* alloc vm area():

This function is used to create a new vm area mapping and returns a pointer to the created vm area. We won’t be filling or setting any values to members of the vm area. You should only use this function to create vm area in the entire assignment.

void dealloc vm area(struct vm area *vm):

This function is used to delete or deallocate the vm area which is passed as an argument. You should only use this function to delete or deallocate vm area in the entire assignment.

MMAP AREA START &amp; MMAP AREA END:

These are constants defined in the file [src/include/mmap.h] which is used to specify the overall start and end limit of the mmap space. All the mappings (vm area) which are created using the mmap syscalls should reside within this limit. if the hint address is not within limit, then mmap syscalls should return EINVAL or (-1).

pmap(int details):

You can use the pmap methods to check the vm area details. If details is zero. Then pmap will print the count of vm area and pagefaults for the address ranges between MMAP AREA START and MMAP AREA END. If details is 1. Then pmap will dump the entire vm area details.

struct pfn info (in page.h)

This object represents the physical memory page. The pfn info for each page is maintained in list pfn info object, which is indexed by the pfn of physical memroy page.

pfn info object has refcount which is used to maintain count of number of sharers for a physical memory page. This count helps to identify whether to copy a page at the event of a write after cfork(). The page needs to be copied when number of sharers is greater than one.

get pfn info(u32 index) (in page.c)

You can make use of this function to get pfn info object corresponding to a pfn of physical memory page.

increment pfn info refcount(struct pfn info * p)(in page.c)

You can use this method to increment refcount of a physical memroy page at the time of cfork().

decrement pfn info refcount(struct pfn info * p)(in page.c)

You can use this method to decrement refcount of a physical memroy page at the time of copy-on-write after a cfork().

get pfn info refcount(struct pfn info *p)(in page.c)

This method gives current refcount of a physical memroy page.

format of Page Table Entry

The format of PTE entry which maps to 4KB pages in intel x86 architecture is as shown in figure 8. Those who want to know more, can refer Intel Software Manual (page 2831).

Figure 8: PTE Entry

For this assignment, you can ignore bit positions 3-11 and 51-63. You only need to modify bit positions 0, 1, 2 and 12-50.

Page-Fault Error Code

The error codes in intel x86 architecture incase of a page fault is as shown in figure9, which is taken from course slides. User-mode read access to an unmapped page results in error code 0x4, same way user-mode write access to an unmapped page results in error code 0x6. The error code 0x7 indicates user mode write access to read-only page which has page table mapping. Those who want to know more, can refer Intel Software Manual (page 2836). For this assignment, you need to only modify P, W, U bits.

Figure 9: Page-Fault Error Code

mmap():

To implement mmap system call, you are required to provide implementation for the template function vm area map in the file [src/mmap.c]) which takes the current context, address, length, protection and flags as arguments. You are supposed to maintain all the vm area mappings in the singly linked list data structures. The head of singly linked list is inside the current context(current-&gt;vm area).

Based on the request and the hint address, You might be creating (adding a node in singly linked list), shrinking, expanding and merging the vm area in the singly linked list (refer the specification mmap). To create and delete use alloc vm area and dealloc vm area respectively.

munmap():

To implement munmap system call, you are required to provide implementation for the template function vm area unmap in the file [src/mmap.c]) which takes the current context, address, length as arguments. Based on the address and length, You might be deleting and shrinking the (vm area) mappings in the singly linked list (refer the munmap specification).

mprotect():

To implement mprotect system call, you are required to provide implementation for the template function vm area mprotect in the file [src/mmap.c]) which takes the current context, address, length and protection as arguments.

If the provided address is not part of any vm area. Then mprotect will fail the request and return EINVAL or (-1). Based on the request, You might be creating ,shrinking, expanding and merging the vm area in the singly linked list (refer the specification mprotect).

Validation Procedure:

• In this part of the assignment we won’t be validating anything regarding physical pages( mapping physical page, updating page table, page fault handling)

• We will only be validating the state of vm area(nodes in the single linked list) such as number of vm area before and after the syscall operations.

• There can be at most 128 vm area at any point of time. If not then return EINVAL or -1.

• The address ranges for all the above system call should be between the address ranges MMAP AREA START &amp; MMAP AREA END. If not then return EINVAL or -1.

• We will be checking the vm area protection or access rights.

• Assume all the address provided to the syscalls are page-aligned.

We have provided a template function vm area pagefault which takes the current context, address (faulted address) and error code. This function will be called whenever there is read page fault (error code will 4) and write page fault (error code will be 6) in mmap addresses ranging between MMAP AREA START and MMAP AREA END.

For valid access, map a physical page and function should return 1. For invalid access (Write fault on the address which maps to read only vmarea) function should return -1.

mmap()

If a vm area mapping is created without providing a MAP POPULATE flags. Then all the subsequent access to the vm area mapping will result in page fault (Lazy allocation).The vm area pagefault function will be called in case of page fault. You have to map physical page, set access flags and update page table entries of the faulted address.

If a vm area mapping is created with MAP POPULATE flags. Then you have to map physical page, set access flags and update page table entries at the time of vm area creation, Any access to the vm area mapping is created with MAP POPULATE flags should not result in page fault.

munmap()

On unmapping a vm area mapping, if a vm area has physical pages mapped to it then you have to unmap the physcial pages and update the page tables accordingly. mprotect()

On changing the protection or access rights of vm area mappings, if a vm area has physical pages mapped to it. Then you have to update the access rights as the physical page as well.

Validation Procedure:

• We will be validating state of vm area, number of page faults, access right of physical pages and vm area.

cfork()

cfork(copy on write fork) creates a new process by duplicating the calling process. The new process is called child process and the calling process is called parent. The child process and parent process run in separate memory spaces. The child and parent share physical memory pages till either of them modifies it. The page is mapped as read-only to both parent and child initially and at the event of a write, copy of the page is created and PTE entry is updated to point to new page.

You also need to implement handle cow fault(in cfork.c) which will be called from do page fault incase of a copy-on-write fault (error code will be 7). In handle cow fault, you should ensure that the faulting address(cr2) is in a valid range and write is allowed as per access flags of faulting segment/vm area.

cfork copy mm will be called from do cfork(in entry.c). The do cfork(in entry.c) gets a new exec context and copies current execution context. The do cfork finally calls setup child context to create os stack and make child ready for scheduling.

Validation Procedure:

• We will check number of copy-on-write page faults.

• We will check number of pages before and after a write followed by cfork().

vfork()

vfork is same as cfork. vfork differs from cfork in that the calling process is suspended until the child terminates by calling exit(). Until that point, the child shares all memory with its parent, including the stack. The child must not return from the current function and should call exit() in user code. The child process should take care not to modify the memory in unintended ways, since such changes will be seen by the parent process once the child terminates.

As part of this task, you need to implement vfork copy mm (in cfork.c) which is called from do vfork (in entry.c). The functionality of vfork copy mm is to make the child use parent’s page table.

When the child exits, change state of parent to READY in vfork exit handle (in cfork.c), which is called from do exit (in entry.c).

Validation Procedure:

• We will check sharing of page table between parent and child.

• We will check that parent is waiting till child exits.

Submission guidelines

• The assignment is to be done individually. You have to submit only two files (mmap.c and cfork.c). Put these two files in a directory named with your roll number. Create a zip archive of the directory and upload in canvas.

• Don’t modify any other files. We will not consider any file other than mmap.c and cfork.c for evaluation.

• You should remove all printf/prink debug statements from submission files. We will taking diff of your output and expected output for evaluation.

In-case of any issues you should reach out to us at the earliest. All the best!
