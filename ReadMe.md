***
***

##MMORPG服务端机制验证程序
    在这里你讲看到，从零开始完成一个mmorpg的实现。
    包括c++版本的高效服务器
    unity c#版本的3d演示客户端

##环境
服务器：vs2013
unity： 5.2.0f3
##运行测试程序
  1. 编译运行服务器。默认端口为5150
  2. unity创建新工程，导入TcpDemoV1.4.unitypackage包
  3. 运行客户端,连接服务器，注册账号，登录账号，进入unity3d世界。
  4. 主角红色方块，其他玩家白色方块，选中玩家后变成蓝色方块。
  5. 开始会按照十字架形式自动移动。WSAD移动,数字1魔法攻击，减少10点mp，space普通攻击。
  魔法攻击力0-50，普通攻击0-10，魔法攻击为一个抛物线球。普通攻击为直线运行球。
***
***

##v1.x版本 12/01 - 12/31
  1. MMORPG相关技术验证 ，完成一个最最简单的服务器原形
不使用任何技巧性东西，只要是有c基础的，都可以100%的明白。达到展示mmorpg核心机制的目的。
  2. 服务器c++,文本二进制存储玩家数据，简化序列化过程。
  3. 客户端unity c#
  4. 通信验证,c++流和unity c#交互 (测试2w/s不丢包).
  5. 登录验证,移动同步，战斗同步,属性同步.
  6. 怪物创建和战斗相关(未完成).
***
###更新: 12/19
  1.怪物刷出，增加一个怪物孵化器。设置怪物id，出生点,出生半径，刷怪数量。
  2.怪物AI增加,简单的站立，移动，攻击，和在攻击范围外时追击玩家,直到攻击范围内后，切换到攻击模式，攻击玩家。
  3.EventSystem1.0版本介绍,事件系统雏形验证。增加了事件系统。服务器以后的核心逻辑系统。用于解耦消息收发和处理。用于减少互斥锁的
  使用。在消息队列中集中处理消息，可以减少没必要的数据锁。使用double队列优化性能，因此在增加消息的时候上锁，处理消息的时候无须担心。
  下个版本的eventSystem，增加实时处理功能，即Event到来后，游戏主循环就会立即处理不会等待下一帧才处理,提高事件处理的实时性。
  我们在此将使用windows的事件内核对象,通知主循环事实处理，你可以看到，目前游戏主循环使用的是WaitForMultipleObjects方法来固定时间update，
  这样while中就提供了天然的机制，来实时响应事件的到来。这便是你看到的为何在游戏主循环中使用wait functions系列的函数。
  4.还需要增加一个，地图信息维护，目前是时候增加了。有了地图信息后就可以对怪物AI做简单优化。防止怪物移动或攻击时重叠在一起了。

***
***
##v2.x版本 1/01 - 2/05
  1. v1.x版本基础上进行开发
  2. 服务器代码重构,优化整理,这个版本将会看到是v1.x肮脏的代码简洁优雅话的方式
  使用oop技术，使用事件方式完成通知系统，使用九宫格维护视野等等的优化技巧。
  使用更加优秀的AI，来处理怪物的日常行为。更加智能，更加真实。

***
##v3.x版本
  1. 数据库加入
  2. 服务器其他逻辑系统开发


