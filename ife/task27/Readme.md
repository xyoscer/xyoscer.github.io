##任务描述：使用一些基础的设计模式，来实现一个虚拟宇宙，虚拟宇宙里面有：一个行星，和众多飞船
###飞船由以下部分组成：
       
        1.动力系统，可以完成飞行和停止飞行两个行为，飞船的飞行速度，消耗能量速度，以及充电速率从页面中的选项中选中
        2.能源系统，提供能源，并且在宇宙中通过太阳能充电
        3.信号接收处理系统，用于接收行星上的信号（对发射器发来的信号进行解码，执行）
        4.自爆系统，用于自我销毁
      
 
###行星上的指挥官，指挥官可以通过行星上的信号发射器发布如下命令
     
        1.命令创建一个新的飞船进入轨道，最多可以创建4个飞船，刚被创建的飞船会停留在某一个轨道上静止不动
        2.命令某个飞船开始飞行，飞行后飞船会围绕行星做环绕运动，需要模拟出这个动画效果
        3.命令某个飞船停止飞行
        4.命令某个飞船销毁，销毁后飞船消失、飞船标示可以用于下次新创建的飞船
       
###指挥官通过信号发射器发出的命令是通过一种叫做Mediator的介质进行广播


           1.Mediator是单向传播的，只能从行星发射到宇宙中，在发射过程中，有10%的信息传送失败（丢包）概率，失败了在继续传送，直到传递成功            需要模拟这个丢包率，另外每次信息正常传送的时间需要0.3秒        
           2.指挥官并不知道自己的指令是不是真的传给了飞船，飞船的状态他是不知道的，他只能通过自己之前的操作来假设飞船当前的状态        
          3.每个飞船通过信号接收器，接受到通过Mediator传达过来的指挥官的广播信号，但因为是广播信号，所以每个飞船能接受到指挥官发出给 所           有飞船的所有指令， 因此需要通过读取信息判断这个指令是不是发给自己的        
         4.Mediator上只能传送二进制码的信息，需要对指挥官发送来的信息进行编码处理，然后广播给宇宙中的飞船
           
##任务总结：

   （1）设计模式的学习
   
    -> 创建型设计模式
        构造函数+原型模式 来创建宇宙中的飞船对象，将属性放在构造函数里（用于定义实例属性），方法放在原型里面（用于定义方法），这样可以确保每个实例所有属性的副本但同时又共享着对方法的引用，最大限度节省了内存，而且还利用了构造函数可以传参这个好处
        
   -> 行为型设计模式
   
      状态模式：当一个对象的内部状态发生改变时，会导致其行为的改变，利用这个模式的主要目的就是将条件判断的不同结果转换为状态对象的内部状态，利用状态模式的具体的思路：首先创建一个状态对象，内部保存状态变量（对于飞船就是，start,stop,destroy）,然后内部封装好这三种动作对应的状态，最后状态对象返回一个接口对象，用来飞船的信号接收器对内部状态的调用.
      
      中介者模式：通过中介者封装一系列对象之间的交互，使对象之间不在相互引用，降低他们之间的耦合。根据题目的要求，meditor只是单向的传播指挥官的命令给宇宙中的飞船。
      
  （2）less的简单使用 
       CSS 预处理器的主要目标：提供 CSS 缺失的样式层复用机制、减少冗余代码，提高样式代码的可维护性。
