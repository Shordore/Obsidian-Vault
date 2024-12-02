.TH Project 3 “1” “12/01/24”
.SH NAME
COP4600 Project 3: File Systems
.SH SYNOPSIS
The goal of this project is to teach students how to implement a file system in userspace.

.SH DESCRIPTION
.PP
.IP “1. Filepaths and Filenames for Source Code”
.PP
The library source code files for this project are located in libWad/Wad.cpp, libwad/Object.h, and libWad/Wad.h. The FUSE daemon source code is located in wadfs/daemon.cpp.
.PP
.IP “2. WAD File Representation in Memory”
.PP
WAD file elements are represented in memory using a combination of an unordered_map and a custom Object class. The unordered_map allows for efficient lookups of file and directory paths, while the Object class represents individual files or directories. Each Object contains attributes such as name, size, offset, and children for directories. This approach keep the file system working, and all the directories, and files in order.
.PP
.IP “3. Required Library Functions”
.PP
.B loadWad:
.PP
loads in the wad and reads all neccesary header, lump variables.
.PP
.B getMagic:
.PP
Simply returns the magic variable which is read in and stored in loadWad.
.PP
.B isContent:
.PP
This function first checks if isDirectory is true as that would mean it is not a file, and if not it looks for the content path in the map_object.
.PP
.B isDirectory:
.PP
Adjusts the path if it is not formatted in the way I want it (making sure there is a "/" at the end) and then searches for it in map_objects and returns the directory status.
.PP
.B getSize:
.PP
This functions simply searches for the path in map_objects and returns the length variable.
.PP
.B getContents:
.PP
Reads data from a file at the specified path into a provided buffer, starting at the given offset and up to the specified length. If the path does not exist or points to a directory, an error is returned.
.PP
.B getDirectory:
.PP
Retrieves the list of child entries (files or directories) for the specified directory path. Ensures the path format is correct before searching the directory structure.
.PP
.B createDirectory:
.PP
Creates a new directory at the specified path. Adjusts the path for proper formatting, verifies the existence of the parent directory, and updates internal data structures to reflect the new directory.
.PP
.B createFile:
.PP
Creates a new file at the specified path. Ensures the file does not already exist, validates the parent directory, and updates internal structures to include the newly created file.
.PP
.B writeToFile:
.PP
Writes data to a file at the specified path, starting from the given offset. If the file does not exist or points to a directory, an error is returned. Updates the file’s length and directory entry information as needed.
.PP
.IP “4. wadfs main()”
.PP
The main() function initializes the FUSE environment, sets up the WAD file path, and invokes fuse_main to start the file system. It parses command-line arguments to determine the WAD file and mount point, ensuring absolute paths are used to prevent runtime issues. It also loads the WAD file into memory using the Wad::loadWad function and passes the library instance to FUSE for use in callbacks.
.PP
.IP “5. Leveraging the Wad Library in Daemon”
.PP
All functions in the daemon use the equivalent function in the wad library.
.PP
.IP “6. Required Callback Functions”
.PP
The callback functions implemented in the daemon include:
.PP
	fuse_getattr: Retrieves the file metadata.
.PP
	fuse_mknod: Creates a file by utilizing the library’s createFile method.
.PP
	fuse_mkdir: Creates a directory by calling createDirectory in the library.
.PP
	fuse_read: Reads file contents using getContents from the library.
.PP
	fuse_write: Writes data to files using writeToFile.
.PP
	fuse_readdir: Lists directory contents by querying getDirectory.
.PP
.SH TESTING
.PP
I tested the library by using the included test cases, and I also utilized my own custom test cases.

.PP
I tested the daemon by mounting it, and testing each function individually to ensure they all work as intended.

.SH BUGS
.PP
There is something wrong with how the wad is lodaed after being deleted, and brought back. It is casuing the bigTest test case to fail but I do not know how to fix it.

.SH LINK
https://youtu.be/A5UXIv4YGSE

.SH CITATIONS
.PP
Ernesto’s P3 discussion video.
https://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/html/
https://engineering.facile.it/blog/eng/write-filesystem-fuse/
https://maastaar.net/fuse/linux/filesystem/c/2019/09/28/writing-less-simple-yet-stupid-filesystem-using-FUSE-in-C/
https://www.cs.hmc.edu/~geoff/classes/hmc.cs137.201601/homework/fuse/fuse_doc.html
http://slade.mancubus.net/index.php?page=about

.SH AUTHOR
Shahyah Darioosh