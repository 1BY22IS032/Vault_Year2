# File System Module 5

## Files

* The os abstract the physical properties of its storage devices to define a logical storage unit `the file`
* is a named collection of information stored on secondary storage
* is a sequence of bits bytes lines or records the meaning of which is defined by the user

### Attributes of a file

* Name : its name for recongizing easily
* Identifier : a unique tag for the system to identify the file
* Type : info is needed for the system to categorise the files
* Location : is a pointer to the location of the file in memory
* size : is the amt of space taken by the file in memory
* Permission : is the access specifier awared to the file
* creation date : date it was created
* Last modified date ; date it was last modified
* Owner : info about the owner or creator of file

All these are present in the FileControlBlock FCB

## File Access Methods

### Sequential

1. simplest
2. info in file is processed one record after another
3. most common editors used his method

![sequentialAccess](https://cdn.imgchest.com/files/pyq9c22ea24.png)

### Direct (Reletive) Access

1. file is viewed as a numbered sequence of blocks or records
2. In DA there is no restrictions on the order of reading or writing for a direct access file
3. DA files are of great use for immediate access to large amounts of information

## Directory Structure

### Single Level Directory

![SLD](https://cdn.imgchest.com/files/wye3c88dwr4.png)

Advantages:

* simple
* easier to search for files if input size is small

Limitations:

* If the no of files increase, it increases bloat
* all files must have unique names as all are in the same directory
* if the no of file increase
  * users will find it hard to memorize the names
  * searching for files must be important
  
### Two Level Directory

![TLD](https://cdn.imgchest.com/files/g4z9ckkwja7.png)

Each system has 2 directories, MasterFileDirectory MFD and UserFileDirectory UFD

When a user refers to a file, only the specific UFD is searched.
file names can be repeated across MFDs but not UFDs

Limitations:

* Users are isolated from one another
* 2 users can't access the same file
* there are system files that are to be used buy all users. to solve this they repeat the files but this takes up a lot of unnecessary space
* to solve this they implement a special folder that contains the systemfiles that is accessed if the files aren't found in the UFD

### Tree Structured Directories

* the generalization allows users to create their own subdirectoreis and to organise their files accordingly
* a t ree is the most common directory structure
* the tree has a root directory and every file in the system has a unique path name

![TSD](https://cdn.imgchest.com/files/e4gdcoopw94.png)

### Acyclic-Graph Directories

* The main use of AGDs are to enable sharing
* an acycling graph is a setup that alloows directories to share subdirectories and files
