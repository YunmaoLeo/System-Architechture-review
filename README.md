## Menu
- [Menu](#menu)
- [Lecture02 Hierachy, Components & Technology](#lecture02-hierachy-components--technology)
  - [Processor(CPU)](#processorcpu)
  - [The ``IAS (von Neumann) Machine``](#the-ias-von-neumann-machine)
  - [The hardware can oly understand ``binary representations``](#the-hardware-can-oly-understand-binary-representations)
  - [Level of Programming Code](#level-of-programming-code)
  - [Morden ISAs:``80x86`` ``MIPS`` ``ARM`` ``PowerPC``](#morden-isas80x86-mips-arm-powerpc)
  - [Technology Trends:](#technology-trends)
  - [MicroProcessor](#microprocessor)
  - [Modern multicore Processor](#modern-multicore-processor)
  - [Manufacturing Chips](#manufacturing-chips)
- [Computer Performance](#computer-performance)
  - [Response Time and Throughput](#response-time-and-throughput)
  - [Relative Performance](#relative-performance)
  - [Measuring Performance](#measuring-performance)
  - [CPU Clocking](#cpu-clocking)
  - [CPU Time](#cpu-time)
  - [Instruction Performance](#instruction-performance)
  - [CPU Performance Equation](#cpu-performance-equation)
- [MIPS32 Programming](#mips32-programming)
  - [Bit,Byte and Word](#bitbyte-and-word)
  - [MIPS Introduction](#mips-introduction)
  - [MIPS32 Structure](#mips32-structure)
  - [Fetch-Execute Cycle (提取－执行周期)](#fetch-execute-cycle-提取执行周期)
  - [MIPS Instruction Field 指令域值](#mips-instruction-field-指令域值)
  - [Caller-saved Registers vs. Callee-saved Registers](#caller-saved-registers-vs-callee-saved-registers)
  - [System call](#system-call)
- [MIPS Signedness (Lecture 5)](#mips-signedness-lecture-5)
  - [Representing Negative Numbers](#representing-negative-numbers)
  - [One's Complement to Represent Negative Numbers](#ones-complement-to-represent-negative-numbers)
  - [Two's Complement Representation](#twos-complement-representation)
  - [MIPS Logical Shift Operation](#mips-logical-shift-operation)
  - [MIPS Multiplication Instructions](#mips-multiplication-instructions)
  - [MIPS Division Instructions](#mips-division-instructions)
- [Machine Code, MIPS Addressing Lecture 06](#machine-code-mips-addressing-lecture-06)
  - [MIPS Instruction Ecoding](#mips-instruction-ecoding)
  - [Registers vs. Memory 寄存器 vs. 存储](#registers-vs-memory-寄存器-vs-存储)
  - [Memory Hierarchy](#memory-hierarchy)
  - [Data Transfer Instruction: ``Load Word``](#data-transfer-instruction-load-word)
  - [Transfering Bytes and Halfwords:](#transfering-bytes-and-halfwords)
  - [MIPS Memory Allcation](#mips-memory-allcation)
- [Lecture 7 MIPS Procedure](#lecture-7-mips-procedure)
  - [Callee vs Caller:](#callee-vs-caller)
  - [MIPS Procedure Calling:](#mips-procedure-calling)
  - [Procedure in MIPS:](#procedure-in-mips)
  - [如果一个程序中有两个procedure且他们都使用$ra则会出现异常](#如果一个程序中有两个procedure且他们都使用ra则会出现异常)
  - [参数传递：](#参数传递)
  - [Recursive](#recursive)
## Lecture02 Hierachy, Components & Technology

### Processor(CPU)
+ Datapath（数据路径）: performs arithmetic operations CPU数据路径负责数学运算
+ Control：负责按照程序的要求控制datapath，memory，I／O等
### The ``IAS (von Neumann) Machine``
+ 今天几乎所有的电脑都是按照IAS—von Neumann machine的架构
+ 使用一个memory来存储instruction操作指令和data
+ 用一个processing unit操作单元来执行数学运算和逻辑操作
+ 一个控制单元来解释memory存储和executing执行中的instructions

### The hardware can oly understand ``binary representations``
+ Programming will firstly translate high-level language code into ``intermidiate-level`` code
+ Then it will translate that ``assembly code`` into the ``machine's language``

### Level of Programming Code
+ Compiler编译器：translate ``high-level language`` into ``assembly language``
+ Instruction: 一个计算机硬件可以理解并执行的指令
+ Assembler汇编器：translate ``symbolic version of instruction`` into ``binary versions``，把指令的符号版本转换为二元版本 即把``Assembly language`` 转化为 ``Machine language``
+ Assembly language: 机器指令的一种符号代表
+ Machine language: 机器指令的二元代表

### Morden ISAs:``80x86`` ``MIPS`` ``ARM`` ``PowerPC``

### Technology Trends:
+ Vacuum tube 真空管
+ Transistor 晶体管
+ Integrated circuit（IC）集成电路
+ Very large scale IC 超大集成电路
+ Ultra large scale IC 超超大集成电路

### MicroProcessor
+ 包含一系列用wires电线关联起来的晶体管
+ 第一个商用的微处理器：Intel 4004

### Modern multicore Processor
+ A single chip contains more than one microprocessor core
+ 同一个处理器芯片涵盖了多个微处理器核
+ 更小的晶体可以实现
  + 每个芯片放置更多的晶体管
  + 更多的处理能力
  + 更便宜且更小的芯片

### Manufacturing Chips
+ 芯片的制作工艺起于silicon硅，是半导体，导电性一般
+ 在进行特殊的工艺以后，既可以实现特别好的导电性，也可以实现特别好的绝缘性
+ 适合作为开关使用


## Computer Performance

### Response Time and Throughput
+ ``Response time` (execution time):程序执行一个任务所需要花费的总时间
+ ``Throughput(bandwidth带宽)``:每个单元时间内可以完成的人物数量
+ 两者的影响因素
  + 将处理器processor替换成更快的版本
  + 给系统增加处理器来实现多核任务处理

### Relative Performance
+ Performance = 1/Execution time 运行时间越短，效果越好
+ ``Performance x / Performance y = Execution time y / Execution time x``

### Measuring Performance
+ Response time: ``完成一个任务的总时间`` ``闪存读取，存储读取，输入输出活动等``
+ CPU Execution time(CPU time)
  + CPU执行时间指的是CPU计算一个特定任务所花费的确切时间
  + 不包括等待I／O及运行其他程序的时间
  + 可以被划分为：
    + User CPU time：花费在一个程序本身的CPU时间
    + System CPU time：花费在OS操作系统所代表执行任务的时间

### CPU Clocking
+ Clock cycle time(clock tick时钟周期): 每一clock周期所花费的时间，clock一般指processor clock
+ Clock frequency(clock rate时钟频率): cycles per second每秒能实现运行周期，是clock period的负数

### CPU Time
+ ``CPU Time = CPU Clock Cycles * Clock Cycle Time``
+ ``CPU Time = CPU Clock Cycles / Clock Rate(Clock frequency)``
+ **提升性能的方式**：
  + 减少Clock Cycles，减少时钟周期
  + 提升Clock frequency(clock rate)
  + 硬件设计者通常需要面临权衡：时钟周期的数量和每周期的长度  ``很多科技在降低时钟周期的同时提升了时钟周期`` 

### Instruction Performance
+ 计算机需要通过执行指令来运行程序，``excution time执行时间依赖于程序中指令的数量``
+ ``Clock Cycles per instruction (CPI)每一指令需要的平均CPU时钟周期数量``
+ ``CPU Clock Cycles ＝ Instruction Count * Cycles per Instruction (CPI)``
+ ``Instruction Count``由programe,ISA and compiler决定
+ ``CPI``: determined by CPU hardware

### CPU Performance Equation
+ ``CPU Time = Instruction Count * CPI * Clock Cycle Time``
+ ``CPU Time = Instuction Count * CPI / Clock Rate``


## MIPS32 Programming
### Bit,Byte and Word
+ Bit: 0 or 1
+ Byte: 8 bits, 256 posiible sequences
+ Word: 目前大多数CPU都是32bits or 64 bits<br>MIPS 32-bit中，a word is 4 bytes long

### MIPS Introduction
+ MIPS:``Microprocessor without Interlocked Processor States``没有互锁处理器状态的微处理器
  + ``Instruction Set Architecture(ISA)`` based on Reduced ``Instruction Set Computing(RISC)``
  + 使指令更简单了，但执行的速度更快
  + 相对于``Complex Instruction Set Computing (CISC):
    + 更`expensive/slow`的memory,写machine code困难
+ 32位的版本由1980年斯坦福团队推出
  + 基本概念是通过使用``deep instruction pipelines深度指令流水线``提升性能
+ 64位的版本在1991年推出
+ 曾用于游戏终端的嵌入式系统，图像工作站等

### MIPS32 Structure
+ ``Words`` are 32-bits (4 bytes)
+ ``Addresses`` are 32-bit words ``2^32 different locations``
+ ``Register 寄存器``也是32位的

### Fetch-Execute Cycle (提取－执行周期)
+ 每一个可编程处理器都实现了一个``fetch-execute cycle 提取－执行周期``
+ 由处理器硬件自动实现，允许处理器遍历程序步骤
+ 通常涵盖四步：
  + ``Fetch the instructoon获取指令`` :从**Program Counter**中的memory address内获取下一个指令，保存在``Instruction Register(IR)``内，在获取操作的尾端，PC又回指向下一个指令
  + ``Decode the instruction解码指令``: 被编码的指令储存在``Instruction Register(IR)``内，它们将会被decoder进行解释
  + ``Execute the instruction``
  + ``Write back回写``：操作的结果会被写入合适的寄存器，Program Counter(PC) 会被更新到一个新的地址，并且进行下一轮的获取指令

### MIPS Instruction Field 指令域值
+ General Format: ``op``6bits ``rs``5bits ``rt``5bits ``rd``5bits ``shamt``6bits ``funct``6bits
+ ``op``: operation code: basic operation of the instruction
+ ``rs``: first source register operand
+ ``rt``: second source register operand
+ ``rd``: destination register operand
+ ``shamt``: shift amount: used in shift instructions
+ ``funct``: function code: select the variant of the operation in the op code field

### Caller-saved Registers vs. Callee-saved Registers
+ ``Caller-saved registers``:呼叫者存储寄存器 ``MIPS32 $t0-$t9``
  + 在calling anything之前保存，returns之后restore
+ ``Callee-saved registers``:被呼叫者存储寄存器``MIPS32 $s0-$s7``
  + 在修改前保存save before modifying; 在returning 之前resotre
+ 呼叫者存储寄存器caller-saved registers are responsibility of the caller
  + 他们的值只有在被call/return后才会保存
+ 被呼叫者存储寄存器callee-saved register are responsibility of the callee
  + Caller can assume that these registers will be restored

+ ``$t0-$t9``:
  + 用于存储暂时的实体变量
  + 不需要在calls之间被保留
+ ``$s0-$s7``:
  + 保持长久的值
  + 应该在calls之间被保留

### System call
+ ``SPIM`` 是MIPS的一个处理器模拟器，名字是MIPS反过来写
  + 将service number 填写进register $v0
  + 把argument values填写进$a0,...$a3(or $f12 for floating point values)
+ May destroy ``$v0-$v1,$a0-$a3,$t0-$t9,$ra``
+ But always preserves $s0-$s7

## MIPS Signedness (Lecture 5)

### Representing Negative Numbers
+ 除去表达数字正负的一位数字后，剩下的七位数字可以表达的范围是(-127 to 127)

### One's Complement to Represent Negative Numbers
+ Negative Numbers:
+ 取正数的二进制的NOT补码
+ 43:00101011
+ -43:11010100

### Two's Complement Representation
+ Negative Numbers 通常由正数的二进制的NOT补码后末位加一
+ 这是最常用的在计算机中表达有符号整数的方法
+ 优势：
  + 加减乘除法的运算和无符号的一样
  + 这一特性允许系统可以更简单地处理高精度算术
  + 此外，0 只有一种单独地表达方式，消除了和-0之间的微妙关系

### MIPS Logical Shift Operation
+ ``sll $s0,$s1,2`` ``srl $s0,$s1,3``
  + shift right logical and shift left logical
  + shifts $s1 right/left 2 bits and stores the result in $s0
+ ``sra $s0,$s1,2``
  + shift right arithmetical
  + 位移$s1 2位，但符号保留``(performing sign extension)``

### MIPS Multiplication Instructions
+ MIPS stores the 64 bit result of the multiplication of two 32 bit registers in two special 32-bit registers ``Hi and Lo``
+ ``mult $s1,$s2<br>mflo $s0``
+ can be encoded as one operation: ``mul $s0,$s1,$s2``
  + 但是``mul``并不会检查overflow 但一个``pseudo-instruction伪指令``乘法可以实现检测overflow ``mulo``

### MIPS Division Instructions
+ ``div $s1,$s2`` 实现了一个带符号的乘法，``余数reminder``放在Hi中，``商quotient``放在Lo中
+ 同样可以使用``mflo``来提取结果``mfhi``
+ 使用``div,divu``时添加三个变量则自动使用了一个伪指令，自动使用了mflo
  + 例如 ``div $s0,$s1,$s2`` 等同于：
    + div $s1,$s2
    + mflo $s0


## Machine Code, MIPS Addressing Lecture 06

### MIPS Instruction Ecoding
+ MIPS 有三种基本格式：``**R,I,J**``
+ ``R-format``: operands are `registers` only 操作只包含寄存器
+ ``I-format``: operands contain immediate 操作包含常数和两个寄存器
+ ``J-format``: operands are immediate only 操作只包含常数，用于跳转

### Registers vs. Memory 寄存器 vs. 存储
+ Processor can access registers directly 处理器可以直接读取寄存器上的内容
+ MIPS32: limit of 32 registers 只有32个寄存器
+ 大部分程序需要的数据比能在寄存器内存放的多
  + 这部分额外的数据则需要被存放在``memory``中
    + `Load`: 将数据从memory转移到register
    + ``store``: 将数据从register转移到memory

### Memory Hierarchy
+ ``Register``
+ ``Main memory``
+ ``Hard disk``
+ 从上往下读取速度递减，容量递增

### Data Transfer Instruction: ``Load Word``
+ Load word: ``lw a, n(b)
  + i.e. ``a = Memory[b+n]``
  + 地址必须是可以整除4的
  + offset n 必须是16bit以内的
    + ``-32768 <= n <= 32767``
+ Store word: ``sw a, n(b)
  + ``Memory[b+n] = a``

### Transfering Bytes and Halfwords:
+ ASCII 字符：1 byte，不同于 word: 4 bytes
+ Halfword: 2 bytes
+ MIPS32中为ASCII和Halfword进行数据转换的操作:
  + ``lb/lbu`` load byte
  + ``lh/lhu`` load halfword
  + ``sb`` store byte
  + ``sh`` store halfword
  + halfwords的地址必须是2的倍数
  + byte地址没有限制

### MIPS Memory Allcation
+ 可以使用``sbrk`` system call 调用额外的memory
+ 下面的代码分配了16 bytes 的空间并且将新memory的地址返回到了$v0
  + ``li $a0,16``
  + ``li $v0, 9``
  + ``syscall #sbrk``


## Lecture 7 MIPS Procedure

### Callee vs Caller:
+ Callee: 被调用的函数就是callee
+ Caller: 调用其他函数的函数

### MIPS Procedure Calling:
+ 需要被传递的参数保存在寄存器``$a0 - $a3``
+ ``return value``返回值保存在寄存器``$v0 ($v1)``
+ ``return address``返回地址保存在``$ra``
+ ``jal label`` --- jump and link
  + 这一指令用于调用一个函数，它执行以下操作:
    + ``$ra: = PC + 4``
    + PC := [label] and calls procedure at address label
+ ``jr rs`` --- jump register
  + 这一操作用来将调用函数的``return address``返回给调用者

### Procedure in MIPS:
+ 返回值被放在了``$v0``

### 如果一个程序中有两个procedure且他们都使用$ra则会出现异常
+ 使用Stack进行解决，``后进先出``
+ ``$sp``: ``stack pointer``stack指针
+ ``$fp``: ``frame pointer``指向procedure frame的第一个word，不会在执行过程中变化

+ Push $s0 onto the stack:
  + ``addi $sp,$sp,-4`` (在stack上分配空间)
  + ``sw $s0,0($sp)`` (保存$s0,-- push)
+ Pop $s0 from the stack:
  + ``lw $s0,0($sp)`` (pop $s0)
  + ``addi $sp,$sp,4`` (deallocate space)

### 参数传递：
+ 如果参数小于等于四，则在``$a0-$a3``进行传递
+ 如果大于四，则前四个在``$a0-$a3``进行传递，后面的放置在``stack``中
+ ``Return Value``保存在$v0,$v1中，如果返回值更多，则用``stack``


### Recursive