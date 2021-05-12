# Greedy Snake 贪吃蛇

基于原生 `js`

采用面向对象编程思想

部分 `ES6+` 语法

## 思路整理
### Classes
  - 节点 Node:

    用于创建蛇身体每一部分的组成元素，以及食物。

    x: 水平位置
    y: 垂直位置
    type: head / body / food
    el: 每个 node 实例都对应一个 DOM 元素，实际上就是一个个 div 小方块，每个方块在容器内部进行绝对定位，有对应的 top 和 left 值

  - 蛇 Snake:
    存储蛇相关信息，处理移动等逻辑。

  - 游戏 Game:
    用于存储游戏信息和控制游戏整体逻辑，初始化、开始、暂停、结束等。

### 核心原理

  移动的实现：
    
    关于蛇的移动的实现，我们不采用去修改每个元素对应的 `top` 和 `left` 的方法，
    因为当蛇达到一定长度时，每一步移动我们都要去修改很多 DOM 元素，这样做效率低而且性能也不好。

    其实我们每次移动只需要考虑蛇头和蛇尾就可以了，
    当蛇移动时，生成一个新头，添加到身体最前端，然后弹出最后一个元素（即尾部），这样不断进行变化，就实现了蛇的移动；
    如果在移动过程中碰到了食物，则不需要删除当前蛇尾元素，这样则实现了蛇长度的增长。

  食物的生成：

    `while` 循环获取容器内部随机的 x, y 值，当得到第一个不与蛇身体重合的位置时停下。

  碰撞：
    
    即两个 node 之间位置重合（碰到身体、食物）或者超出一定范围（碰到墙壁/出界），通过简单判断 x, y 即可实现。

## 代码实现

    详见源码


