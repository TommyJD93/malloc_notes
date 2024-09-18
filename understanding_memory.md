# General knowledge about memory handling

## Table of contents

- Abstract

## Abstract

Notes regarding my studies on the memory handling made by the kernel, propedeutic for the project "malloc" for the 42Network masteries. The goal of the project is to recreate the following functions in C lang: malloc, calloc, free. These notes will not be strictly about the topic of the title.

## Types of storage

The storage used by the programs running on a computer comprises two main types:

- primary
- secondary

The primary storage, which is the most expensive, is the RAM. The ram is the most fast accessible storage that we can use to run our programs, but being so expensive limit his size.

The secondary storage, instead, is any HDD or SSD mounted on the computer. The pros of this second type of storage are the low price (compared to the primary) and the dimensions.

Combining these 2 storages we can allow the user to use more memory than his physical for dynamic allocations. This type of memory that is "created" is called **virtual memory**


## Virtual memory

As we said the virtual memory is given by the combination of primary and secondary storage segments of memory. These segments contains the memory addresses that will be reserved for a program. Since this memory is going to emulate the RAM also their structure and disposition will be resembling the structure of the RAM.

The addresses of the virtual memory __does not__ resemble the original addresses of the storage they are picked from. They are infact called __virtual addresses__ and in order to make the MMU (Memory Management Unit) able to distringuish the origin of these virtual addresses we need to make use of "__Page Tables__". These tables serve the purpose of translating the virtual memory addresses used by the process into physical addresses used by the hardware to process the instructions.

_**NOTE**: **Page Tables** and **Pages** are **not** the same thing, page tables are used for translation while pages are the effective "containers" for virtual addresses which are later translated using the page tables._

_Fun fact: this is the reason why technical specifications of games from time to time ask for some free storage on the installation drive, in this way the game processes can make use of that as virtual memory._


### TBL


The TBL (Translation Lookaside Buffer) is a memory cache used to store recent translations of virtual or physical memory. This helps reduce the time taken by the MMU to find a specific address, it can be located between the CPU and CPU Cache or between CPU Cache and the primary storage or between the layers of the multi-level cache.


### Paged virtual memory

Now that we have mentioned pretty much all the elements that cover a role inside the "ecosystem" of the virtual memory, let's dive a little bit more in depth about the rules and roles that orchestrate the memory management of a computer.

First of all let's talk about the **Pages**. These are the storage for our virtual addresses. This "component" eliminate the need for continuos allocations of physical addresses, and does that by breaking apart both physical and virtual memory blocks, their size can range from 4KB to several megabytes. Before going ahed with the explenation, let's look at some terminology.

When we talk about a "page", "memory page" or "virtual page" we are talking about what we just defined as a **Page**. Whie a **page frame** refers to the smallest fixed length contiguos block of physical memory into which memory pages are mapped by the OS.


