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

### 粗略判断是否有outliers

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

第三点这个wegment based:

For example if we have rainfall data of different cities but the data is missing for some cities, instead of using population mean we can take the mean of neighboring cities or cities belonging to similar region or cities belonging to same state to fill the blanks. 所以business knowledge很重要


### Identifying and treating missing values

找到在filter里有blank

用mean去填，用AVERAGE函数算，算完同上filter筛出再装填(复制的时候只需要复制数值（paste special -> values）就OK，否则default黏贴把formula弄上去就出错了)


## Variable Transformation

### 精简操作

有四个dist，弄一个新列计算四者的average，然后就在新列里面原地copy然后paste values，之后才能删掉这四个原来的columns.

### Transform categorical values into dummy variable 

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmttfvocvbj31b20g2tob.jpg)

![](https://tva1.sinaimg.cn/large/008eGmZEly1gmttjq1cwqj318o0h2apm.jpg)

⚠️注意：不能把种类由多个的categories弄成1234这样，因为他们之间没有高低rank之分，无hierarchy！

比如把airport（YES or NO），插入两列分别是airport_YES.然后用IF函数，然后原地复制只要value.

```IF($N2=="yes", 1, 0)```

对于多值的：













