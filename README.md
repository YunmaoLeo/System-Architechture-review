# System-Architechture-review
|CONTENT|
|-------|
|[Lecture02 Hierachy, Components & Technology](##Lecture02-Hierachy,-Components-&-Technology)|


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
