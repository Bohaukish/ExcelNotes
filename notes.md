

可参考资源：

https://exceljet.net/excel-functions/excel-sumifs-function

普遍要求：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkbi07uxbmj31f80se1e1.jpg)


![](https://tva1.sinaimg.cn/large/0081Kckwly1gkbi4op5k4j31gw0muqle.jpg)

### 添加add-ins

Tools -> Excel add-ins 把两个都勾选上

然后在Data的tab里就多了：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkdpmafihdj307w03qq34.jpg)

### Anchoring 引用

查看绝对引用 Mac: Command + T, Win: F4

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkbjxq8s1nj30nq07itcj.jpg)

加上了绝对引用dao符"$"的列标zhi和行号为绝对地址，在公式向dao旁边复制版时不会发生变化;没有加上绝对地址符号的列标和行号为相对地址，在公式向旁边复制时会跟着发生变化(非绝对的用黑色小十字架往下拉是可以自动计算的)

$符号要加在固定不动的数值上面去：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkbjws3bztj30f20b8mzy.jpg)

例子：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkbk3i80i8j310207sq6q.jpg)

第一个：行列都不固定 =A7 其他直接下拉右拉
第二个：固定行列 =\$G\$7
第三个：固定行 =A\$7
第四个：固定列 =\$A7


### Financial Formats

#### 基本概念

revenue 财政收入

EBIT(Earnings Before Interest and Tax)：息税前利润；

EBITDA(Earnings Before Interest, Tax, Depreciation and Amortization)：息税折旧摊销前利润。

CAGR: 年均复合增长率，每年的平均增长率，计算的时候只需要第一年和最后一年。公式：(现有价值/基础价值)^(1/年数) - 1

怎么算的：第一年是100，最后一年(第n年)是136，设CAGR=x

100*(1+x)^n=136 => x= (136/100)^1/n - 1
=> 16.6%

注意：2010年到2017年的年数是（2017-2010+1）=8年。

Discount Rate 贴现率，是指将未来支付改变为现值所使用的利率，或指持票人以没有到期的票据向银行要求兑现，银行将利息先行扣除所使用的利率。就是你要损失的钱

贴现就是利率计算的反向操作，把未来的钱换算到现在的钱是多少钱（未来要拿到这么多钱，现在应该投入多少）

贴现率的成分：无风险利率，风险补偿，通货膨胀的等，贴现率越高，以后的钱越来越不值钱。

组合投资：会有风险对冲的情况，一个跌了但另一个涨了，风险就降低了，整个Portfolio Return会平稳一些，可以看看李永乐老师讲这个https://www.bilibili.com/video/BV1K4411G7bm/?spm_id_from=333.788.videocard.10

benchmark return 基本标准资产组合回报

Portfolio Return 证券组合投资收益回报

Correlation：其中一个实现就是计算benchmark和Portfolio回报的相关性，如果相关性高，说明大势涨，我的投资组合也会涨，说明我的投资组合对于市场有一定敏感度。

#### 常用公式

(第一年的Revenue是A 第二年的Revenue是B 第三年的Revenue是C 第一年的EBITA是E1，贴现率是r)

1yr Growth Rate = B/A - 1

Margins = EBITDA/Revenue = E1/A, margin=revenue/profit

CAGR(compound annual growth rate)= (C/A)^(1/N)-1

Discounting(present value) = C/(1+r)^n

Compounding(future value) =PV*(1+r)^N

PV = FV / (1+r)^N

annualized return

Correlation

#### 怎么理解NPV和IRR

（给出一个一个现金流）

净现值（Net Present Value, NPV）：未来要赚这么多钱的话，那我现在要贴多少钱。说的是把未来期望收入的钱换算成现在的钱（**跟算利息类似，不过是反向运算**，例如明年你会赚110元，假设贴现率是10%，那么换算成现在的钱也就是110/(1+10%)=100元，也就是说你明年赚到的110元就相当于现在100元的购买率，反过来就是你现在100元，利息10%，明年你就变成了110元，往后的年份一样算法），然后累加再减去投资成本得到累计净现值。累计净现值越大越好，理论上净现>0项目就可行，表示有赚头。

**净现值（NPV）说的是在考虑货币时间价值（通货膨胀贬值）下我们在项目周期内能赚多少钱。**

**内部报酬率（IRR）说的是在考虑货币时间价值（通货膨胀贬值）下我们在项目周期内我们能承受的最大货币贬值率有多少，更通俗地说就是假设我们去贷款来投资这个项目，所能承受的年最大利率是多少。**
举例来说，如IRR为8%，可以简单解释为以8%的利率借钱投资于此项目，刚好可以不赚不赔。

链接：https://www.zhihu.com/question/23193517/answer/309815103

NPV(net present value 净现值) 内部收益率，就是资金流入现值总额与资金流出现值总额相等、净现值等于零时的折现率。

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkchvg5ywyj31480nawhx.jpg)


更多的例子：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkciax90u2j311g0ratrd.jpg)

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkcibfviw0j31160iwwtc.jpg)


#### Excel Finance相关自带函数

- 这几个如果不能完全理解，这几个推荐使用前面的数学方法用公式敲，还不容易出错。

    nper: year of period, pmt: payment 在前面的例子里这个值没列出来因此为0, type: end/begining of the period，空缺就默认end。

    出来是负数，是符合会计里的现金流的，但是在建模里用正数。

    =PV(rate,nper,pmt,fv,type)

    =FV(rate,nper,pmt,pv,type)

    =RATE(nper,pmt,pv,fv,type) 算CAGR的

- 但是以下的还是推荐用公式，简单理解还省时：

    =NPV(rate,value1,value2,...) rate是给出的基准收益率

    =IRR(values) 

    别的函数：

    =SUMPRODUCT(array1,[array2],[array3]...) 将数组间对应的元素相乘，并返回乘积之和，用来计算加权和，回报率恒定时候用

    当每年的回报率波动的时候用：

    =FVSCHEDULE(principle, schedule) 本金，每年的利率表

    也可以用来计算annualized return 每一年平均下来的年化回报率（常用，因为一年涨一年跌的，谁也不知道到底总体涨没涨）：

    =FVSCHEDULE(1, schedule)/年份

    =CORREL(array1, array2)

    如果有多个时间序列还想计算相关性：(在enable analysis tool之后)

    Data tab -> Data analysis -> Correlation

    ![](https://tva1.sinaimg.cn/large/0081Kckwly1gkdpth67j0j318s0dugw4.jpg)

    （最后再Formatting以下就可以

#### COUNTIF和COUNTIFS

另：选中一个范围用Command shift 下键；Windows是ctrl shift 下

奇怪的事情：
 
=COUNTIF(sum range, sum criteria) 中的criteria是一定要双引号的

比如算出所有分数大于85的同学的个数：

=COUNTIF($E$26:$E$31,">85")

另一个奇怪的事情：设计师脑子有水的问题

跟SUMIF的参数顺序是不一样的注意

sumif（条件区域criteria range，求和条件criteria，实际求和区域sum range)

=SUMIFS(sum range, criteria range, criteria 1, criteria range 2, criteria 2,…)

其他的SUMIF、SUMIFS，AVERAGEIF、AVERAGEIFS也是这个尿性


### 别的操作

善用快捷键 建议用windows版本的，按alt可以查看快捷键

给一个表添加filter: data-> add filter，表头就会有下拉菜单

黑科技：想要跟另一个sample表的样式（字体 颜色等）一样：

选中sample表，点Home tab的Format小刷子，然后鼠标变成小刷子去点另一个想统一样式的另一个表。

### 时间函数

=DAYS(end date, start date) 两个日期相隔的天数

=DAYS360(start date, end date) 按一年360天算的相隔天数,金融里有用的 360/Actual

=MONTH(serial_number) 

=DAY(serial_number)

=YEAR(serial_number)

=WEEKDAY(serial_number,[return type]) 返回一个日期的星期，默认一周的第一天是1，如果要把星期一当一周的初始，return tyoe填2。

=EOMONTH(start_date,months)  end of month 一个月的月底,months为0是start_date同月份的月底日期，填1是下个月的月底日期，-1是上个月月底日期

=TODAY()

=NOW()

### VLOOKUP 不灵活

=VLOOKUP(你要找的数据的索引，搜索范围，列数，是否需要精准搜索）

第一个参数 Lookup_value: 你建立的新的pivottable的index，根据什么查找的

第二个参数：查找的范围（选中整个表 ctrl shift down left）

第三个参数：在查找范围中的第几列（注意是相对于查找的那个表的第几列） Col_index_num（不灵活，如果插入了列，就乱掉了）

第四个参数：一般填FALSE, 为false如果找不到就空着，找exact的内容，为true就会找到最closest的结果

填完之后 别的格子 复制，高级粘贴选Format,或者黑十字下拉，注意使用正确的anchor，竖着的是列数固定（比如第I列的人名在第一个参数），横着的是行数固定（第9行的列数在第三个参数），这样整个表只需要一个公式就OK。

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkdw9dsuv3j30ey0760ub.jpg)

HLOOKUP同理：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkn6r1cv64j30tu0lmwm3.jpg)

### INDEX和MATCH 推荐使用，取代VLOOKUP

即使之后插入很多行和列，也可以灵活应对

=INDEX(搜索范围，行数，列数） 能找到第几row的内容是什么，这个第二读三个参数一般用MATCH去找

=MATCH(查找的值，搜索范围，[类型]): 找到要找的字段在第几row，其中搜索范围只需要一列或者一行的小范围就可以了，类型为0表示exact match多用


### OFFSET和MATCH 和前面的INDEX选一个就行

=offset(搜索范围的起点（最左上角的那个cell），行数，列数）

其中行数列数也是用MATCH去找

注意：

如果是从最左上角作为起点：（正常 无需改动）

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkdzahnlf7j30iu088tbc.jpg)

如果是从数据区域的最左上角

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkdz9olxb5j30j208iacu.jpg)

那么MATCH1后的要-1

```=OFFSET($C$3,MATCH($H3,$B$3:$B$7,0)-1,MATCH(I$2,$C$2:$F$2,0)-1)```

### Pivot Table

#### 建立Pivot Table和从中抽取数据

选中要弄的整个表，insert->pivot table（如果半天最右边那个Field List界面出不来，就自己去PivotTable Analyze那个tab找）

生成pivot table后 可以双击某个cell，会弹出一个新的表，告诉你这个的数据来源，十分好用。

再抽取Pivot Table里的值,直接打=然后点pivot table里的值（就是值，别点表头），然后自动会有一串GETPIVOTDATA的函数，长这样：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkffy59859j30z20kiqga.jpg)

然后我们只需要改动Asia和Year的值就好，记得anchor好，然后直接下拉就可以生成表了：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkffz6xpzmj30xy0k0qgv.jpg)

#### Grouping in Pivot Table（弄出区间）

eg: Grouping By Date

右键年 -> Group ->

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh59b1jp8j30gg0imaih.jpg)

之后：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5ajckcwj30ck0cmwi6.jpg)

eg: Grouping By Number 统计不同工资区间的人数

把聚集函数sum改成count

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5cxpzzij30e80fi44i.jpg)

然后在表里右键工资 -> Group 设置区间头尾数字和interval

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5g1g9fij30oq0qugyl.jpg)

结果：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5gx0v6zj30ck0g0tgc.jpg)

还可以加入计算百分比：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5kw5cm0j30mg0j07db.jpg)

结果：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5kxzrb9j30hg08swl2.jpg)


#### 在pivot里面加计算字段 Custom calculation in Pivot Table

PivotTable Analyze -> Fields & items & sets -> Calculated Field

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkfzv7sdiij30q40myjv5.jpg)

选完一个点Insert Field就可（或者双击），写完formula点OK，新加的这个计算字段就会出现在PivotTable Fields里就可以拖了。

例子：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5ushdvcj30sm0hc45f.jpg)

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkh5xfxtoij30ze0l2jz7.jpg)


#### 做Correlation的heat map

Data tab -> Data Analysis -> Crrelation

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkg4zdi2oaj319k0gkk42.jpg)

### Solver

#### 解方程

用于解方程和线性规划之类的问题

先设置个xyz的初始值，一般弄成111但是别填000免得有乘除值了的搞出bug，先把三个方程式表达出来，注意乘法用product也可用*也可

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko3gpuwzgj30q008c0v3.jpg)

然后上solver

solver 里面第一个框 随便挑一个式子先列出来，第二个是xyz的在哪(注意在这里的选中一列数字不是按住平常的快捷键，而是悬停右下角白色十字架拖拽)，然后点add添加身剩下的俩方程，最后记得要考虑是否勾选解是否非负（本题无这个限制，但是财务计算有，以及这是个非线性方程组，于是选nonlinear。

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko3mxfxq6j31ia0m8qer.jpg)

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko3kn5is9j30kw0f0tc3.jpg)

然后它自己会一个一个试，最后得到一个最好的解

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko40m8jj8j30vc066mzq.jpg)

另一个例子: 如果有一个未知数需要是int的限制（int的限制也是在add条件里的

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko4hl6908j316u0eu0yv.jpg)

#### 实例：用于算max profit

已知货品的售价和成本，成本小于一万，想max(profit)，每个货品的quantity应该是多少？

别的constraint：非负，quantity为int

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko5e47zm1j31da0fw13m.jpg)

为什么结果建议是只进货水果呢，因为水果的profit margin最高（利润率最高，而且其他的货品个数无constraint

接下来加个条件：客户对价格敏感，如何定新的价格

- If the price change goes up more than 20%, then the quantities will drop by 20%. Also, if thep rice drops more than 20%, then the quantities rise by 20%.

- The price movement should be less than 50%

**怎么添加这个条件：在quantity里用nested if**

J27是Constraints Price Change % = (新价格 - 旧价格) / 旧价格

P27是默认初始数量为100

quantity的表达式：

=IF(J27>20%,P27*(1-20%),IF(J27<-20%,P27*(1+20%),P27))

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko6fc7r2kj31tu0mgard.jpg)


### Matrix Multiplication 矩阵相乘

比SUMPRODUCT方便很多

= MMULT(矩阵1，矩阵2)  限制是矩阵自己的相乘的m,n长宽限制

![](https://tva1.sinaimg.cn/large/0081Kckwly1gko7hfrcmjj30ie0bwgp4.jpg)

TRANSPOSE 转置矩阵

```
    1 2 3  -》  1 2
                3 4
    4 5 6       5 6
```

```Fac1 Manage1是（1.97*7%+0.00*64%+1.40*29%）```

因为要竖的乘上横的，所以第二个3X3矩阵需要转置一下

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkphd86qtoj30nw0i8n5o.jpg)

L3的index time sheets那张表是一个金融面试问题，学了ECO才能明白，答案在3.3那个sheet里，根据手写的公式算就可以，constraints就用solver

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpi7wkjosj31ls0tax1s.jpg)

### Indirect 抽取同样format不同sheet的数据

例子（L3 ）中，新表单regression用的是前三个的close（闭市价格），找一个开始时间最晚的，将时间复制到新表regression，然后结合offset和Match把搜索的close列给抽取出来（不需要第三个参数列，因为确定了只在一列中找，填好了第一个黄金公式在右下角双击黑十字架）。

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpkul3n8qj30d401mwei.jpg)


注意：在很多情况下，同一个公司的表格是一致的format，比如在这里不同公司的闭市价都在E列，也就是说，我们现在虽然数据抽取源自于不同的表单，但是公式还是一样的，除了第一个参数的表单名（在这里用的offset抽取，第一个参数是reference的表的左上角第一个cell）在变以外，其他都不需要变。(跟拼凑URL差不多感觉)

观察一下表单名咋写

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpkydkj0nj30vg06oq5x.jpg)

'表单名'!\$E$2，接下来将具体的表单名都换成这个拼凑的格式：

```=OFFSET(INDIRECT("'"&B$1&"'!$E$2"),MATCH($A3,INDIRECT("'"&B$1&"'!$A$2:$A$10046"),0)-1,0)```

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpl38p9stj310u062mzr.jpg)

正确的golden formula是：

```=OFFSET(INDIRECT("'"&B$1&"'!$E$2"),MATCH($A3,INDIRECT("'"&B$1&"'!$A$2:$A$10046"),0)-1,0)/OFFSET(INDIRECT("'"&B$1&"'!$E$2"),MATCH($A2,INDIRECT("'"&B$1&"'!$A$2:$A$10046"),0)-1,0)-1```

### 快速定位和检查error code

继续，用下面一天的/上面一天的-1，有些数据缺失导致的error code，如何快速在大量数据中发现？

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpm24o6dmj31u00ce7ej.jpg)

选中整个表单，点filter，用filter去定位

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpm57xzpnj30w20qikbj.jpg)

然后找原因为啥error，选中要检查的那单个成分，按Fn+F9，就会显示错的那个表达式的值为几

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpm8lw2v3j313m080q7u.jpg)

这个错误源头在于最开始的golden formula写错了，拼凑的地方没全部替换完，别纠结这部分，看着怎么用filter定位叫就行


### Regression

Data -> Data Analysis -> Regression 

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpmlqgyfmj318w0om4m0.jpg)

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpmp2ahbcj30ym0hqdoo.jpg)

### VBA

应对高重复性的工作，做好一个template可以用很多遍

Mac把VBA调出来在reference -> Ribbon & Toolbar -> Developer勾住

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpn31ds62j310o05ejt8.jpg)

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkpmu02banj30uq0mogyw.jpg)

#### 利用宏

tip: 当你不知道VBA代码咋写的时候可以考虑先录制宏搞搞样子，然后去developer的macro里查看并edit宏里自己生成的代码

宏的基本操作介绍：

https://www.bilibili.com/video/BV11s411G7yX?t=330&p=5

写了VBA的时候 Save记得保存为Excel Macro-enabled Workbook即.xlsm

#### 语法

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkqhjubhavj305u0hwjt4.jpg)

循环：

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkqhk2t17jj306y0c60u0.jpg)

eg: 将第A列的前十个数字改成红色字体

For loop要提前知道循环次数，需要一个具体的数；其他两种只需要一个表达式

- For Loop 要提前知道具体的循环次数
  
    =counta 用来计算一个范围内非空白格的个数，如何在VBA里用workbook的formula呢，加个WorksheetFunction.CountA(numberrange),这个numberrange就是整个第A列

    ```
        numberrange = Range(Range("A1"), Range("A1").End(xlDown))
        numberofcells = WorksheetFunction.CountA(numberrange)
        For i = 1 To numberofcells
            If Range("A" & i) < 10 Then
                Range("A" & i).Font.Color = vbRed
            End If
        Next
    ```

好设置步数的：

- Do While 后面跟的是成立的条件
  ```
    Do While Range("A" & i).Value < 10
        Range("A" & i).Font.Color = vbRed
        i = i + 1
    Loop 
  ```

- Do Until 后面跟出界条件
    ```
        Do Until Range("A" & i).Value >= 10
            Range("A" & i).Font.Color = vbRed
            i = i + 1
        Loop
    ```

#### button

eg: 弄一个登录按钮

developer -> button 右键 assign macro

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkqhlvhx6cj30oc0n0dit.jpg)

输入密码，如果是对的也就是666弹出一个选择框，选yes，B2的格子就会填上You sure?...

一个practice:

根据用户输入数字生成new sheets，输入的是空值就退出，如果输入的不是数字就给个提示重头来

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkrnz0yr6ej30ty0ucwhx.jpg)


#### 实用！给自己的表单们弄一个登录登出的功能

也可以自带的encrypt table with password

不登陆成功的话，所有其他的表单都不可见，并且会把所有的登陆登出时间信息记录在log sheet里面。

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkrrseb5moj30rk0zq42m.jpg)

LOG OUT：注意，不能hidden登陆界面，如果worksheet的名字不是landing的话，就隐藏，如果不是即保留。然后继续找log sheet里的最近的空行，把记录弄上去。

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkrrsc07quj30hq0jwtai.jpg)

#### 录入信息的功能

With用于避免重复部分比如
```
Sheets("Trading System").Cells(n, 7) = ordernumber
Sheets("Trading System").Cells(n, 8) = dt
Sheets("Trading System").Cells(n, 9) = tm
...
```

```
With Sheets("Trading System")
    .Cells(n, 7) = ordernumber
    .Cells(n, 8) = dt
    .Cells(n, 9) = tm
    .Cells(n, 10) = TRADER
    .Cells(n, 11) = TICKER
    .Cells(n, 12) = MARKET
    .Cells(n, 13) = "EQUITY"
    .Cells(n, 14) = DIRECTION
    .Cells(n, 15) = PRICE
    .Cells(n, 16) = SHARES
    .Cells(n, 17) = PRICE * SHARES
End With
```



补充的点：

当有那种没有分割的一堆txt的那种样式

data -> text to colulmns -> delimited 选分隔符就可以了

### 一个case study

先把raw data列在同一个时间线上,如果没得就空着 

daily return 就是D2/D1 - 1

profolio value = 本金*(1+daily return)

另:如果小黑色十字架自动填充无用（如果第一个cell跟第二个cell不是一个formula的话，就先复制那个要copyformula的cell,选中要填充的那一整行，然后选paste->）

porfolio weight：购入的某只的比重，刚开始只有microsoft的，后面慢慢购入其他的股票
然后折线图


IFERROR: 如果公式的计算结果为错误值,则 IFERROR 返回您指定的值;否则,它将返回公式的结果。
(因为这道题有的日期是没有值的，为了避免影响求和计算，就将缺失的值设为0)

年化收益率FVSCHEDULE，要用的年份可以在里面再套个IF和YEAR函数，条件不成立就返回0，因为是按年算的 如果不是那一年就变0，不算

另:表做完,format as table,后有N/A不好看怎么弄，选中这个表，点conditional formatting-> new rules -> formatt only cells that contain，并且把这个值弄成浅灰色

![](https://tva1.sinaimg.cn/large/0081Kckwly1gla26x14ebj30km0c80xb.jpg)


