## 进程调度模拟

采用 eletron-vue 进行开发

环境安装: node: v14.15.0   npm: 6.14.9

[AppMan](https://github.com/ywymoshi/JSCourse/tree/master/OS/AppMan)

``````
# 切换到目录下
cd apppman
# 安装依赖
npm intall
# 执行
npm run dev
``````

## 作业调度

作业调度又称高级调度，不涉及处理机的分配，主要任务是按一定的原则从外存上处于后备状态的作业中挑选一个（或多个）作业调入主存，为其分配内存、I/O 设备等必要的资源，并建立相应的进程，安排在就绪队列上，以使进程获得竞争处理机的权利。

### 算法一：先来先服务（FCFS）

**基本思想**

- 遵循先进入后备队列的作业，先进行调度的原则。

- 非抢占式算法

**特点**

- 简单，易于编码实现

- 优先考虑作业的等待时间，没有考虑作业的执行时间长短、作业的运行特性和作业对资源的要求

### 算法二：短作业优先（SJF）

**基本思想**

- 根据作业控制块中作业申请时指出的执行时间，选取执行时间最短的作业优先调度；可有抢占或非抢占方式。

- 短作业优先调度算法考虑了作业的运行时间而忽略了作业的等待时间。

### 算法三：高响应比优先（HRRF）

**初衷**

- FCFS 调度算法只片面地考虑了作业的进入时间，短作业优先调度算法考虑了作业的运行时间而忽略了作业的等待时间。

- 响应比高者优先调度算法为这两种算法的折中，使长作业不会长时间等待，但每次调度前都要进行响应比计算。

### 算法四：优先权高者优先（HPF）

**基本思想**

- 系统根据作业的优先权进行作业调度，每次选取优先权高的作业优先调度。作业的优先权通常用一个整数表示，也叫做优先数。优先数的大小与优先权的关系由系统或者用户来规定,本实验采用优先权值越小，优先权越高。

- 优先权高者优先调度算法综合考虑了作业执行时间和等待时间的长短、作业的缓急度、作业对外部设备的使用情况等因素。

### 算法五：时间片轮转（RR）

**基本思想**

- 系统将所有的就绪进程按先来先服务的原则，排成一个队列，每次调度时，把 CPU 分配给队首进程，并令其执行一个时间片。时间片结束之后，将该进程加到就绪队列队尾；然后再把处理机分配给就绪队列中新的首进程。

**优点**

- 系统能在给定的时间内响应所有用户请求。
