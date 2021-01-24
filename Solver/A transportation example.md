![](https://tva1.sinaimg.cn/large/008eGmZEly1gmzgki03uwj30y80m0n62.jpg)

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmzgl2iyslj31080f6agq.jpg)

先initial一下等下solver里要改动的数值，为J6:L7

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmzhduycfvj316c0kogw9.jpg)

所以这个问题其实就是：想要通过改变J6:L7里的六个数值（有限制为integer,demand和和supply和的consttains），让Total cost（SUMPRODUCT俩array求和）取min。

⚠️ 加constrains的时候，用的是cal_D和cal_S，这两个是**后面加上去的带公式的cell**！

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmzhm5ium2j312c0e4jwc.jpg)

另外，variables in this problem have a linear relationship among them，因此solving method 选simplex LP

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmzhpgfifgj30qa0oen6j.jpg)

结果：

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmzhrh85whj30g20b2abt.jpg)