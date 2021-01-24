# Linear Regression Analysis using Excel

## Before Analysis

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmthicb74nj31960iqnal.jpg)

### data exploration

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmthnz6xttj31lw0ounn9.jpg)

### Data Dictionary 

understand the data 

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmthuqjiy4j31c00iuamk.jpg)

descriotion of the house price dataset:

 ![](https://tva1.sinaimg.cn/large/008eGmZEly1gmthwdbv8nj314w0oyh8c.jpg)

 ![](https://tva1.sinaimg.cn/large/008eGmZEly1gmthxez7erj314k0gwnhv.jpg)

 ## Univariate Analysis

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmthzqa70kj31bo0l0ne9.jpg)

### Extended data dictionary

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmti1gn68ij31520gwws2.jpg)

### 操作过程：

先把categorical的列都移到最左边去（复制粘贴删除

data tab -> data analysis add-in -> descriptive statistics

kth largest设置为25是3rd quartile value(75%)，kth smallest设为25是 1st quartile value

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtm620hvqj315i0sye33.jpg)

## Outlier Treatment

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtmtgnvd9j31760fcgub.jpg)

### Outlier detection

2 methods:

1. Look at the difference between mean and median. If there's large difference between mean and median values, outlier☑️.

    比如看price这列，mean是

2. Check out the quartile distribution.

   1st quartile - min 和 max - 3rd quartile 差不多


![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtmp9ghuij307i0f8whi.jpg)

mean 22.5跟21.2差不多

10.2 - 5 = 5.2 和 50 - 43.8 = 6.2 差不多

所以price这列没啥outliers

### 画图判断有无

box plot

### Treatment

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtn6d68h4j315s0hwwts.jpg)

capping and floating: define the upper and lower limit. 比如这里给出的\[0.3\*位列1%的数，3\*位列99%的数]。

这里用的第一种方法：

点filter, ascending排序，选出normal value 的最大和超出normal value的

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtojtk3awj310c0pmdra.jpg)

得到另一个表，然后把那两个不正常值改成3*normal的max，改完再把filter其他数据钩上

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtomw7uncj30ke08m779.jpg)

## Missing Value Imputation

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtotkkpqgj31860ea4by.jpg)

数据少就用mean/median换，数据有多删了完事

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtov1bipdj316o0ia4ef.jpg)

这里填0是有前提的if zero makes sense in any particular scenario we can do that.

第三点这个segment based:

For example if we have rainfall data of different cities but the data is missing for some cities, instead of using population mean we can take the mean of neighboring cities or cities belonging to similar region or cities belonging to same state to fill the blanks. 所以business knowledge很重要


### Identifying and treating missing values

找到在filter里有blank

用mean去填，用AVERAGE函数算，算完同上filter筛出再装填(复制的时候只需要复制数值（paste special -> values）就OK，否则default黏贴把有依赖的formula弄上去就出错了)

## Variable Transformation

### Simplify

原数据集里有四个dist，弄一个新列计算四者的average，然后就在新列里面原地copy然后paste values，之后才能删掉这四个原来的columns.

### Transform categorical values into dummy variable 

When you're dummy encoding a categorical variable with k levels, you should only make **k-1** dummy variables, since otherwise you'll get a collinearity with the constant.

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmttfvocvbj31b20g2tob.jpg)

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmttjq1cwqj318o0h2apm.jpg)

⚠️注意：不能把种类由多个的categories弄成1234这样，因为他们之间没有高低rank之分，无hierarchy！

把airport（YES or NO），插入两列分别是airport_YES.然后用IF函数，然后原地复制只要value.

```IF($N2=="yes", 1, 0)```

对于多值的，waterbody这一列，因为有四个unique values，因此建立三个新列，操作同上

对于bus_ter这一列，只有一个值，是常数，删除

## Correlation Analysis

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtv4326khj31c80miwvq.jpg)

### 弄个correlation matrix

data tab -> data analysis add-in -> correlation


把图弄好看点用conditional formatting：

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtvkcbtr6j30za0ektcq.jpg)


![](https://tva1.sinaimg.cn/large/008eGmZEly1gmtvlfq0flj31uk0hg1fx.jpg)

## Create Regression Model

reference： https://zhuanlan.zhihu.com/p/192647937

### Risidual sum of squares(RSS)

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmuw4hmvnaj30ye0fugs4.jpg)

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmuw6r1jw6j318m0hatgg.jpg)

### Assessing the accuracy of predicted coefficients

Residial Standard Error: The RSE is considered a measure of the lack of fit of the linear regression model to the data. The smaller the RSE is, the better the model fits the data.(因为RSS越小越好啊)

$RSE = \sqrt{\frac{RSS}{n - 2}}$

### Assessing the model accuracy: RSE and R-squared

$R^2 = 1 - \frac{RSS}{TSS}$

RSS: Residual sum of squares

TSS: Total sum of squares

R squared measures the proportion of explained variance from the total variance. If it is close to zero, it indicates that regression did not explain much or divide evenly. This can occur either because our linear model is wrong or because linear was not the right choice for this relationship.

### Application in Excel

data tab -> data analysis -> Regressions

An example for simple linear regression, the relationship between room_num and price：


#### The results of categorical values

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmyr2yt63rj31uz0u0dyf.jpg)

$\beta_0$: the value of all the other predictors multiplied by the conditions

最后那个参数：constant

结果中的coefficient为1.1315 means that if there is an airport and all the other variables are the same, the value of the House price will increase by 1.1315.

p value is low which means there is a statistical evidence of a difference in the house price depending on whether there is an airport or not.

同理，如果是waterbody

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmyraucw8xj31740gw477.jpg)

跟无水体相比，如果有一个Lake，房价升高0.264单位。。。

但是p值低说明no statistical evidence that there will be an impact of these three variables on the house price.


#### Output interpretation

https://www.cnblogs.com/webRobot/p/8464579.html

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmyg4kqa8pj30x60fy7cp.jpg)

- Table 1: 回归统计表

    - Multiple R: 复相关系数R平方根, 用来衡量自变量x与y之间的相关程度的大小, 0.69说明正相关，且系数不低。越高越好。

    - $R^2$: 以测定因变量y的拟合效果。在这里复测定系数为0.4848，表明用用自变量可解释因变量变差的48.48\%。

    - Adjusted R Square: 说明自变量能说明因变量y的48.38\%，因变量y的剩余部分要其他因素来解释。

    - 标准误差：越小越好

    - 观察值: 用于估计回归方程的数据的观察值个数
    

- Table 2: 方差分析表
    
    通过F检验来判定回归模型的回归效果,置信度默认是95%

    - significance F: 回归方程F检验的P值为1.3075E-74，大大小于显著性水平0.05，所以说该回归方程回归效果显著.


- Table 3: 回归参数表

    - room_num的回归系数9.099 > 0(if I increase the room number variable by one unit it will increase the house price by 9.099); 显著水平<0.001,说明非常显著，room_num对house price的影响十分的显著。这个回归方程为：Y= 9.099 * room_num - 34.659


#### Multiple linear regression 

前两张表同理，只是之前的simple用的t-test，而用于三组以上的样本用的F-test


![](https://tva1.sinaimg.cn/large/008eGmZEly1gmys2zgxxuj30x40u0tuh.jpg)

回归系数表：

如果p-value小于显著性水平0.05（用conditional formatting标红了 ），该项的自变量与y相关；大于P值说明这些项的自变量与因变量不存在相关性，因此这些项的回归系数不显著。

coefficient和intercept给出最后的方程

### Using solver

原理是OLS(Ordinary Least Squares)方法。

先把所有的系数设为1，算出sqrt diff(预测值-实际值 开根号)，全列sum一下，开solver，要让sum of sqrt diff最小，通过改变beta即所有系数的值

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmys03efk1j31xe0u0hdu.jpg)

跑出来的结果是：

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmys1a6t6ej31xd0u0qv6.jpg)

其中可以看到sum of sqrt diff为11886.9，跟之前用data analysis自带regression出来的residual 11794.18差不多。









