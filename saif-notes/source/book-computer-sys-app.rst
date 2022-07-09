Computer System: A Programmers's Prespective.
==============================================

Preface
********
* a builder’s perspective, describing how to implement the hardware or the systems software, including the operating system, compiler, and network interface.
* a programmer’s perspective, describing how application programmers can use their knowledge of a system to write better programs.
* Arithmetic overflow is a common source of programming errors and security vulnerabilities, yet few other books cover the properties of computer arithmetic from a programmer’s perspective.
* [in the machine-level representation of programs] One certain benefit is that you will develop a thorough and concrete understanding of pointers.
* To this point, you have relied on a conceptual model of the memory system as a linear array with uniform access times.
* Finally, we show you how to improve the performance of application programs by improving their temporal and spatial locality.
* introducing the general concept of exceptional control flow (i.e., changes in control flow that are outside the normal branches and procedure calls).We cover examples of exceptional control flow that exist at all levels of the system, from low-level hardware ex- ceptions and interrupts, to context switches between concurrent processes, to abrupt changes in control flow caused by the receipt of Linux signals, to the nonlocal jumps in C that break the stack discipline.
* Few of our students would have the opportunity to build a computer system. On the other hand, most students, including all computer scientists and computer engineers, would be required to use and program computers on a daily basis
* Topics such as machine language were in; but instead of focusing on how to write assembly language by hand, we would look at how a C compiler translates C con- structs into machine code, including pointers, loops, procedure calls, and switch statements.
* The labs are available from the CS:APP Web page

Chapter 1: A Tour of Computer Systems
**************************************
* Compilation System:

    * Pre-processor: The preprocessor (cpp) modifies the original C program according to directives that begin with the ``#`` character. The result is another C program, typically with the ``.i`` suffix. 
    * Compiler: The compiler (cci) translates the text file hello. i into the text file hello. s, which contains an assembly-language program. Assembly language is useful because it provides a common output language for different compilers for different high-level languages. For example, C compilers and Fortran compilers both generate output files in the same assembly language. (hello.s)
    * Assembler: the assembler (as) translates (hello.s) into machine-language instructions, packages them in a form known as a **relocatable object program**, and stores the result in the object file (hello.o).
    * Linker: The linker (id) handles this merging (merging printf.o precompiled object file into our program). The result is the hello file, which is an executable object file (or simply executable) that is ready to be loaded into memory and executed by the system.

* Buses: Buses are typically designed to transfer fixed-size chunks of bytes known as **words**. The number of bytes in a word (the word size) is a fundamental system parameter that varies across systems. word size = 8/4 bytes = 64/32 bits
* I/O Devices: Each I/O device is connected to the I/O bus by either a **controller** or an **adapter**.
* Main Memory: PhysicaLly, main memory consists of a collection of dynamic random access memory (DRAM) chips. Logically, memory is organized as a linear array of bytes, each with its own unique address (array index) starting at zero.
* CPU: At its core is a word-size storage device (or register) called the program counter (PC). At any point in time, the PC points at (contains the address of) some machine-language instruction in main memory. A processor appears to operate according to a very simple instruction execution model, defined by its **instruction set architecture**. The register file is a small storage device that consists of a collection of **word-size registers**, each with its own unique name.
* We say that **a processor appears to be a simple implementation of its instruction set architecture**, but in fact modern processors use far more complex mechanisms to speed up program execution. Thus, we can distinguish the processor’s instruction set architecture, describing the effect of each machine-code instruction, from its microarchitecture,
* Using a technique known as **direct memory access** (DMA. discussed in Chapter 6), the data travel directly from disk to main memory. without passing through the processor.
* A system spends a lot of time moving information from one place to another. From a programmer’sperspective, much of this copying is overhead that slows down the “realwork”of the program. Thus. a major goal for system designers is to make these copy operations run as fast as possible.
* As semiconductor technology progresses over the years. this processor—memory gap continues to increase. It is easier and cheaper to make processors run faster than it is to make main memory run faster. (paper: It's the memory, STUPID). Here (Cache) comes, they are implemented with a hardware technology known as **static random access memory** (SRAM).
* The idea behind caching is that a system can get the effect of both a very large memory and a very fast one by **exploiting locality**, the tendency for programs **to access data and code in localized regions**. By setting up caches to hold data that are likely to be accessed often, we can perform most memory operations using the fast caches. application programmers who are aware of cache memories can exploit them to improve the performance of their programs by an order of magnitude.
* The main idea of a memory hierarchy is that storage at one level serves as a cache for storage at the next lower level. On some networked systems with distributed file systems, the local disk serves as a cache for data stored on the disks of other systems.
* The operating system has two primary purposes: 
 
    * (1) to protect the hardware from misuse by runaway applications and 
    * (2) to provide applications with simple and uniform mechanisms for manipulating complicated and often wildly different low-level hardware devices. 
    * The operating system achieves both goals via the fundamental abstractions shown in Figure 1.11: processes, virtual memory, and files. As this figure suggests, files are abstractions for I/O devices, virtual memory is an abstraction for both the main memory and disk 1/0 devices, and processes are abstractions for the processor, main memory, and I/O devices.

.. image:: ../static/cs-app-fig-11.png
