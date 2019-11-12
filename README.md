# 家园守卫战

通过 二零一九 雪梨 信息1113 作业2

这是一款简单的射击游戏，其中玩家控制一个可以抵抗大量入侵太空船的坦克。

需要调用坦克，屏障，入侵者和子弹。
如果玩家获胜或失败，将重新开始游戏。
调用 gradle build 来编译和解决依赖关系。

可以在项目中使用处理库，以允许您创建窗口并绘制图形。
可以通过以下链接访问文档游戏对象与机制该项目包含许多需要在您的应用程序内建模的实体。

## 坦克
这是玩家控制的实体，可以通过按键盘上的左右箭头键来移动并以每帧1像素的速率移动。
储存格为22x16像素，从像素底部的中下部开始显示。
坦克可以发射可击中障碍物或敌方入侵者的弹丸。它可以拍摄多个向侵略者的弹丸。
除了使用左右箭头键移动坦克外，玩家还可以使用空格键发射子弹。
如果敌方弹丸击中了坦克，如果坦克被击中，它将失去生命值3由于坦克已被摧毁，因此游戏应该过渡到“ 游戏结束”屏幕。

## 侵略者
每个入侵者都有一个独特的起始位置，但会与其他入侵者一起及时移动。
入侵者群从屏幕的顶部中间移动到玩家的障碍。
一旦入侵者到达了障碍，游戏应过渡到“ 游戏结束”屏幕。
入侵者将在一个方向上移动30步，然后向下移动并在另一方向上前进30步。
每个横向步将构成一个1像素的运动，每个步每两帧进行一次。
当一个入侵者向下移动，它将向下移动8个像素，并过渡到其他精灵。
入侵者是较大群的一部分，该群以40个入侵者开始（每行10个入侵者，每4行）。
每入侵者为16x16像素，这将与它们的精灵大小相对应。
他们会有相同的碰撞区域作为精灵。
一旦入侵者被击中，就被认为已被摧毁，因此不再应由游戏。
当所有侵略者都受到打击后，这将导致玩家赢得游戏并过渡到下一级屏幕。
每5秒钟，将随机选择一个侵略者以向下发射弹丸。

## 屏障
屏障由7个不同的组件组成，每个组件可以承受3次打击。
一旦组件具有被摧毁，它不再为战车提供保护。
当障碍物受到打击时，它将变为不同的精灵，表示它已损坏。
玩家配有3个屏障，每个屏障左侧屏障距离应用部分中所述的左边界至少20个像素，即中心屏障从屏幕中心开始，右屏障距离右边界至少20像素。
每个障碍位于战车位置上方至少10像素。
坦克和入侵者可能会击中屏障。

## 子弹
坦克和入侵者都可以发射子弹，但是，入侵者的弹丸不会击中其他任何东西入侵者（只有屏障和坦克）。
坦克可以击中障碍物以及任何入侵者。
一旦子弹与另一个实体的影响，它将不复存在。
弹丸为1x3像素，每帧向上传播1px。

## 游戏条件
游戏的目标是让玩家在坦克被摧毁或入侵者登陆之前消灭所有侵略者。

### 满足以下条件时，玩家将获胜：
所有入侵者被摧毁。

### 满足以下条件之一时，计算机将获胜：
入侵者到达屏障（距离屏障10像素）。
坦克被击中3次导致其被摧毁。

## 应用
应用程序需要遵守以下规范640宽480高度的窗口带有黑色背景。
左边界（坦克不能移动到该点）在x 180，右边界在x 460。
必须保持每秒60帧的帧速率。
程序不得出现任何内存泄漏，请在使用前尝试加载所有资产。
您必须使用处理库，不能使用任何其他框架，例如javafx，awt或jogl。
