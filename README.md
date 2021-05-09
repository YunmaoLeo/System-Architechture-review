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