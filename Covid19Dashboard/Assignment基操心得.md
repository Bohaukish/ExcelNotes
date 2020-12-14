### HLOOKUP

还是不太熟悉每个参数的意思

=HLOOKUP(新表的索引，搜索范围，列数，是否需要精准搜索）

第一个参数 Lookup_value: 你建立的新的pivottable的index，根据什么查找的

第二个参数：查找的范围（选中整个表 ctrl shift down left）

第三个参数：在查找范围中的第几列（注意是相对于查找的那个表的第几列） Col_index_num（不灵活，如果插入了列，就乱掉了）

第四个参数：一般填FALSE, 为false如果找不到就空着，找exact的内容，为true就会找到最closest的结果

![](https://tva1.sinaimg.cn/large/0081Kckwly1gknhgukn0uj30z00m647r.jpg)

### Format Cells

自定义数据的格式，字体，颜色和符号，临界值

![](https://tva1.sinaimg.cn/large/0081Kckwly1gkn0ifn0g5j312u0mkwmn.jpg)

想了解更多请转战数据自定义格式

### 做图表用：选中不连续的几行按住Command

如果要选中excel不连续的几行 按住command 如果选连续的几行 按shift

### 宏

避免重复动作的好东西，就是录制一个动作，然后给它分配个快捷键，下次要实现同样操作直接快捷键伺候

参考的教程是：

https://www.bilibili.com/video/BV11s411G7yX?t=330&p=5

### 做Dashboard

给Pivot Table加filter: PivotTable Analyze Tab -> Insert Slicer

connect the slicer to every single chart：

Excel做Dashboard的时候 可以直接开个新的sheet然后把前面pivot table生成的chart直接复制粘贴，然后如果多个chart要用同一个slicer，就随便点一个图，新建个slicer，然后点slicer tab -> report connections，