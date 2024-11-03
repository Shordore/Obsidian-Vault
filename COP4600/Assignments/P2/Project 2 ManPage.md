
.TH Project 2 "1" "11/01/24"
.SH NAME
COP4600 Project 2: Memory Management & Layering
.SH SYNOPSIS
The goal of this project is to teach students how to implement a custom memory management system, simulating dynamic memory allocation and deallocation with specific allocation strategies.

.SH DESCRIPTION
.PP
.IP "1."
.B Filepaths and Filenames
.PP
.B /MemoryManager/MemoryManager.h
.PP
This is the header file containing the class declarations for the MemoryManager library.
.PP
.B /MemoryManager/MemoryManager.cpp
.PP
This is the implementation file where all the function definitions reside.
.PP
.B /MemoryManager/libMemoryManager.a
.PP
This is the static library archive created after compiling the MemoryManager code.
.PP

.IP "2."
.B Tracking Holes and Allocated Regions
.PP
The MemoryManager tracks free memory regions (holes) and allocated regions using several data structures:
.PP
.B std::map<unsigned int, Block> holes;
.PP
This map keeps track of all the free memory regions. The key is the starting word offset, and the value is a Block struct containing the start and length of the hole.
.PP
.B std::map<unsigned int, Block> tenants;
.PP
This map tracks all the allocated memory regions. Similar to holes, the key is the starting word offset, and the value is a Block struct representing the allocated block.
.PP
.B std::map<void*, Block> tenantAddresses;
.PP
This map associates allocated memory addresses with their corresponding Block information, allowing for efficient deallocation.
.PP

.IP "3."
.B Allocation Functions
.PP
The MemoryManager provides the following key allocation functions:
.PP
.B void* allocate(size_t sizeInBytes);
.PP
Allocates a block of memory of the specified size in bytes. It uses the selected allocation strategy (best-fit or worst-fit) to find a suitable hole.
.PP
.B void free(void* address);
.PP
Frees the memory block at the given address, returning it to the pool of available memory and merging adjacent holes if necessary.
.PP
.B int bestFit(int sizeInWords, void* list);
.PP
An allocator function that selects the smallest hole that can accommodate the requested size.
.PP
.B int worstFit(int sizeInWords, void* list);
.PP
An allocator function that selects the largest available hole.
.PP

.IP "4."
.B Other Required Functions
.PP
Additional functions as specified in the project requirements include:
.PP
.B void initialize(size_t sizeInWords);
.PP
Initializes the memory manager with a specified number of words, setting up the initial free memory region.
.PP
.B void shutdown();
.PP
Cleans up the memory manager, freeing all allocated memory and resetting internal structures.
.PP
.B void* getBitmap();
.PP
Returns a bitmap representing the allocation status of memory regions, useful for visualizing memory usage.
.PP
.B void* getList();
.PP
Returns a list of current holes in memory, including their starting offsets and lengths.
.PP
.B int dumpMemoryMap(char* filename);
.PP
Dumps the current memory map to a specified file using POSIX system calls.
.PP

.IP "5."
.B POSIX Calls in dumpMemoryMap
.PP
The \fBdumpMemoryMap\fP function utilizes POSIX system calls to interact with the filesystem:
.PP
.B open()
.PP
Opens or creates the specified file with appropriate permissions.
.PP
.B write()
.PP
Writes the formatted memory map data to the file.
.PP
.B close()
.PP
Closes the file descriptor after writing is complete.
.PP

.SH TESTING
.PP
I tested the MemoryManager library using \fBCommandLineTest.cpp\fP.
.PP
Memory leaks and errors were debugged using \fBvalgrind\fP. By running the test program under valgrind, I was able to identify and fix memory leaks and invalid memory accesses. All allocated memory was properly freed, and the program was verified to be free of segmentation faults and other runtime errors.
.PP

.SH BUGS
.PP
There are no known bugs at this time. All functions have been tested and verified to work as expected.

.SH LINK
Add Link here

.SH CITATIONS
.PP
Rohan's P2 discussion video.
.PP
https://www.geeksforgeeks.org/pointers-vs-references-cpp/
.PP



.SH AUTHOR
Shahyah Darioosh