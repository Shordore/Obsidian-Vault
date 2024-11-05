.TH Project 2 "1" "11/01/24"
.SH NAME
COP4600 Project 2: Memory Management & Layering
.SH SYNOPSIS
The goal of this project is to teach students how to implement a custom memory management system.

.SH DESCRIPTION
.PP
.IP "1."
.B Filepaths and Filenames
.PP
.B /MemoryManager/MemoryManager.h
.PP
Header file with class declarations for the MemoryManager library.
.PP
.B /MemoryManager/MemoryManager.cpp
.PP
Implementation file with function definitions.
.PP
.B /MemoryManager/libMemoryManager.a
.PP
Static library archive created after compilation.
.PP

.IP "2."
.B Tracking Holes and Allocated Regions
.PP
The MemoryManager tracks memory regions using several data structures:
.PP
.B std::map<unsigned int, Hole> holes;
.PP
Tracks free memory regions.
.PP
.B std::map<unsigned int, Hole> tenants;
.PP
Tracks allocated regions using start offsets.
.PP
.B std::map<void*, Hole> tenantAddresses;
.PP
Associates allocated memory addresses with corresponding Hole information.
.PP

.IP "3."
.B Allocation Functions
.PP
.B void* allocate(size_t sizeInBytes);
.PP
Allocates a block of the specified size, using the allocation strategy to find a suitable hole.
.PP
.B void free(void* address);
.PP
Frees the block at the given address, making it able to be reused.
.PP
.B int bestFit(int sizeInWords, void* list);
.PP
Finds the smallest hole that fits the requested size.
.PP
.B int worstFit(int sizeInWords, void* list);
.PP
Finds the largest available hole.
.PP

.IP "4."
.B Other Required Functions
.PP
Additional functions as specified in the project include:
.PP
.B MemoryManager(unsigned int wordSize, std::function<int(int, void*)> allocator)
.PP
Constructor that initializes the MemoryManager, setting word size and allocator function.
.PP
.B ~MemoryManager()
.PP
Destructor that releases all allocated memory to prevent leaks.
.PP
.B void initialize(size_t sizeInWords);
.PP
Sets up the memory manager with a specified number of words.
.PP
.B void shutdown();
.PP
Releases allocated memory and resets internal structures.
.PP
.B void setAllocator(std::function<int(int, void*)> allocator);
.PP
Changes the allocator function for different allocation strategies.
.PP
.B unsigned int getWordSize();
.PP
Returns the word size used for alignment.
.PP
.B void* getMemoryStart();
.PP
Returns the starting address of the memory block.
.PP
.B unsigned int getMemoryLimit();
.PP
Returns the byte limit of the current memory block.
.PP
.B void* getBitmap();
.PP
Returns a bitmap representing the allocation status of regions.
.PP
.B void* getList();
.PP
Returns a list of holes in memory, including offsets and lengths.
.PP
.B int dumpMemoryMap(char* filename);
.PP
Dumps the current memory map to a file using POSIX calls.
.PP

.IP "5."
.B POSIX Calls in dumpMemoryMap
.PP
The \fBdumpMemoryMap\fP function uses the following POSIX system calls:
.PP
.B open()
.PP
Opens or creates the specified file.
.PP
.B write()
.PP
Writes memory map data to the file.
.PP
.B close()
.PP
Closes the file descriptor.
.PP

.SH TESTING
.PP
I used the provided \fBCommandLineTest.cpp\fP file to run a test of the program,
and used valgrind to ensure there was no memory leaks in the program.
.PP


.SH BUGS
.PP
No known bugs. All functions seem to perform as intended.

.SH LINK
https://youtu.be/7SVoeK7IhVc

.SH CITATIONS
.PP
Rohan's P2 discussion video.
.PP
https://www.geeksforgeeks.org/pointers-vs-references-cpp/
.PP
https://www.cs.rit.edu/~ark/lectures/gc/03_00_00.html
.PP
https://www.ibm.com/developerworks/library/pa-dalign/index.html
.PP
https://en.cppreference.com/w/cpp/utility/functional/function
.PP

.SH AUTHOR
Shahyah Darioosh