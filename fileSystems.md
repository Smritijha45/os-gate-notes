# 📘 File Systems – Complete GATE Notes (Operating Systems)

---

# 📌 1. What is a File System?

A **File System** is a method used by the operating system to:

✔ Store data  
✔ Organize files  
✔ Retrieve data efficiently  
✔ Manage disk space  

It provides an abstraction over secondary storage (disk).

---

# 📌 2. File Concept

A **File** is a collection of related data stored on secondary storage.

---

## 🔹 File Attributes

- Name
- Identifier
- Type
- Location
- Size
- Protection
- Time & Date
- Owner

---

## 🔹 File Operations

- create()
- open()
- read()
- write()
- append()
- close()
- delete()
- truncate()

---

# 📌 3. File Types

1️⃣ Regular File  
2️⃣ Directory File  
3️⃣ Special File (Device file)  

---

# 📌 4. Access Methods

---

## 🔹 1. Sequential Access

- Data accessed in order.
- Example: Text files.

---

## 🔹 2. Direct (Random) Access

- File divided into fixed-size blocks.
- Can read/write any block directly.

---

## 🔹 3. Indexed Access

- Index block stores pointers to data blocks.

---

# 📌 5. Directory Structure (Very Important)

---

## 🔹 1. Single-Level Directory

- All files in one directory.
- Name conflicts possible.

---

## 🔹 2. Two-Level Directory

- Separate directory for each user.

---

## 🔹 3. Tree-Structured Directory

- Hierarchical structure.
- Most common.

---

## 🔹 4. Acyclic Graph Directory

- Allows shared files.
- No cycles.

---

## 🔹 5. General Graph Directory

- Allows cycles.
- Requires garbage collection.

---

# 📌 6. File Allocation Methods (Very Important for GATE)

---

# 🔹 1. Contiguous Allocation

Files stored in consecutive blocks.

✔ Fast access  
✔ Simple  
❌ External fragmentation  

---

# 🔹 2. Linked Allocation

Each block points to next block.

✔ No external fragmentation  
❌ Slow random access  

---

# 🔹 3. Indexed Allocation

Index block contains pointers to file blocks.

✔ Direct access  
✔ No external fragmentation  
❌ Extra memory for index block  

---

# 📌 7. Comparison of Allocation Methods

| Feature | Contiguous | Linked | Indexed |
|----------|------------|--------|---------|
| Access | Fast | Sequential | Direct |
| Fragmentation | External | No | No |
| Random Access | Yes | No | Yes |
| Overhead | Low | Pointer overhead | Index block overhead |

---

# 📌 8. Free Space Management

How OS keeps track of free blocks.

---

## 🔹 1. Bit Map (Bit Vector)

- 1 bit per block.
- 0 → Free
- 1 → Allocated

✔ Efficient  
✔ Easy to find free blocks  

---

## 🔹 2. Linked List

- Free blocks linked together.

❌ Slow search  

---

## 🔹 3. Grouping

- First free block stores addresses of next free blocks.

---

## 🔹 4. Counting

- Store starting block + count of contiguous free blocks.

---

# 📌 9. File System Implementation

---

## 🔹 File Control Block (FCB)

Contains metadata of file:

- File name
- Permissions
- Size
- Location pointers

---

## 🔹 Inode (UNIX Concept)

In UNIX-like systems:

- Inode stores file metadata
- Does NOT store filename
- Contains block pointers

---

# 📌 10. Disk Structure

Disk divided into:

- Boot block
- Superblock
- Inode blocks
- Data blocks

---

# 📌 11. Journaling File System

Maintains a log (journal) before actual update.

✔ Prevents corruption  
✔ Faster recovery  

Example:
- ext3
- NTFS

---

# 📌 12. Virtual File System (VFS)

Provides abstraction layer.

Allows multiple file systems:
- FAT
- NTFS
- ext4

---

# 📌 13. Disk Caching

- Frequently accessed blocks stored in main memory.
- Improves performance.

---

# 📌 14. File Sharing & Protection

---

## 🔹 Access Control

- Read
- Write
- Execute

---

## 🔹 Access Control List (ACL)

Specifies user permissions.

---

# 📌 15. Mounting File System

Mounting = Attaching file system to directory tree.

---

# 📌 16. Important GATE Topics

✔ Allocation methods comparison  
✔ External vs Internal fragmentation  
✔ Indexed allocation calculations  
✔ Directory structures  
✔ Free space management  
✔ Inode structure  
✔ Journaling  

---

# 📌 17. Quick Revision Summary

- File system manages disk storage
- 3 main allocation methods
- Indexed allocation supports random access
- Bit map used for free space tracking
- Inode stores metadata
- Tree structure most common directory type
- Journaling prevents data corruption

---


