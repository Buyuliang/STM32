### 系统滴答定时器

我们在初学STM32时，可能会使用循环等待去实现延时，随着学习的深入，这种做法弊端很明显，延时时系统无法进行其他操作，大大降低了系统的效率。所以我们一般在编程时会使用定时器去定时。

 SysTick定时器（系统滴答定时器）是一个倒计时定时器，被捆绑在NVIC中，用于产生SYSTICK异常（异常号：15）。在以前，大多操作系统需要一个硬件定时器来产生操作系统需要的滴答中断，作为整个系统的时基。例如，为多个任务许以不同数目的时间片，确保没有一个任务能霸占系统；或者把每个定时器周期的某个时间范围赐予特定的任务等，还有操作系统提供的各种定时功能，都与这个滴答定时器有关。因此，需要一个定时器来产生周期性的中断，而且最好还让用户程序不能随意访问它的寄存器，以维持操作系统“心跳”的节律。SysTick定时器能产生中断，CM3为它专门开出一个异常类型，并且在向量表中有它的一席之地。它使操作系统和其它系统软件在CM3器件间的移植变得简单多了，因为在所有CM3产品间对其处理都是相同的。该定时器用法也相对简单，主要它由4个寄存器来控制。
- 1、配置时钟源，选择外部时钟（STCLK）还是内部时钟（FCLK），时钟分频等

- 2、计算重载值，并赋值给SysTick重装载数值寄存器重载值*系统周期＝中断周期

- 3、开中断

- 4、使能SysTick定时器

![image](https://user-images.githubusercontent.com/63707976/134792622-ee795c22-a6e1-4bef-9862-94ad1d2a8443.png)
