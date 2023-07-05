遍历别人blog看到了一个有意思的问题:[Magical Hat](https://dirtysalt.github.io/html/general-algorithm.html#:~:text=10.-,%E7%A5%9E%E5%A5%87%E5%B8%BD%E5%AD%90%E9%97%AE%E9%A2%98%20Magical%20Hat,-A%20bunch%20of)，没找到中文的解答，英文的有点难懂，想了一会才明白过来，所以记录一下。

原问题:
>A bunch of men are on an island. A genie comes down and gathers everyone together and places a magical hat on some people’s heads (i.e., at least one person has a hat). The hat is magical: it can be seen by other people, but not by the wearer of the hat himself. To remove the hat, those (and only those who have a hat) must dunk themselves underwater at exactly midnight. If there are n people and c hats, how long does it take the men to remove the hats? The men cannot tell each other (in any way) that they have a hat.
>FOLLOW UP Prove that your solution is correct

翻译:
>一群人在一个岛上。一个精灵下来把大家召集在一起，并把一顶神奇的帽子放在一些人的头上（也就是说，至少有一个人有帽子）。这顶帽子很有魔力：它可以被其他人看到，但戴帽子的人自己却看不到。为了摘掉这顶帽子，那些人（而且只有那些有帽子的人）必须在午夜时分将自己浸入水中。如果有n个人和c顶帽子，这些人需要多长时间才能摘掉帽子？
注:这些人不能（以任何方式）告诉对方他们有一顶帽子。
进阶，证明你的解决方案是正确的。

### 答案
>分类考虑C的情况  
1.C=1,此时只有一个人看到其他人都没带着帽子，于是当晚跑去泡水，问题在一天内解决。  
2.C=2,此时带着帽子的两个人都只看到一个帽子，并且认为`对方是那个唯一戴了帽子的人`，所以第一晚两个人都毫无动作。  
到了第二天他们发现对方都没动，才会察觉到`一定是对方看到我也有帽子`，于是两个人都去洗澡了。  
总共需要两天。  
3.C=3  
第一天，三个人都看到两个帽子，每个人都在想“一定是其他俩人戴了帽子，我没有，与我无关”然后什么都不做。  
第二天,m3看到那两个人都没动，还是没法确定自己，猜测“可能他俩都觉得对方才是有帽子的，所以没动”,所以又是什么都没做。  
第三天，每个人看到的情况都还是没变化，然后意识到`有两个帽子`的想法是错误的，于是一起下水了。  
总共需要三天。  
以此类推，如果有c个帽子就需要c天。  

### 误区  
我一开始想的"在C=3的情况下，第二天每个人看到其他两人还是带着帽子，就应该明白过来`他们两个人都看到的两顶帽子`，然后既然其他两人都看到两个帽子，就说明自己的头上也有一个"。
后来才明白过来"其他两个人都看到两个帽子"这个信息对于m3来说是不存在的，所以他只能最谨慎的假设"只有两个帽子，那两个人没动是因为C=2的原因"。  

写的挺差的解释:
[1](https://placewit.medium.com/hats-and-genie-puzzle-3655bb88de14),[2](https://puzzlefry.com/puzzles/genie-with-c-hats-and-n-men-puzzle/) [3](https://puzzlersworld.com/interview-puzzles/genie-c-hats/) [4](https://codedestine.com/genie-with-c-hats-puzzle/)

几年前看到过的`逻辑和博弈`相关的课程里提到过这个，当时的ppt附有大量的图，还有用逻辑语言来根据部分信息构造全局信息的过程，可惜当时整理材料的意识不强，忘了叫做什么，现在也搜不到了。

### 扩展阅读:   
还是关于帽子的问题，不过要求的是`小组中有人做出猜测，并且每个做出猜测的人都猜对了`,问的是策略。  
[Hamming 码解决帽子问题 ](https://zhiqiang.org/math/game-one-hat.html)  
[帽子游戏二 ](https://zhiqiang.org/math/game-two-hats.html)  
