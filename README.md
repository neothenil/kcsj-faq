## 课程设计常见问题汇总

1. 报错：

![Q1](img/Q1.png)

使用Bamboo-Lattice的时候，需要先运行一个组件的主干卡片，其特点是文件名中含有`main`，
然后再运行分支卡片，其特点是文件名中含有`branch`。各个分支卡片的运行顺序没有特殊要求，
先跑哪个再跑哪个没有影响。

2. 报错：

![Q2_1](img/Q2_1.png)

首先确认输入卡片的`path`中指定的数据库的位置是否正确。当卡片中填写的路径如下时：
```xml
   <path>
       <WIMSNdir>E:\Bamboo\database\ENDF70.69\WIMSN\WIMSNdir.xml</WIMSNdir>
       <subdir>E:\Bamboo\database\ENDF70.69\LSQsub\LSQsubdir.xml</subdir>
       <DepFile>E:\Bamboo\database\DepFile\lavender.dat</DepFile>
   </path>
```
需要保证整个database文件夹存在于E:\Bamboo路径下。

然后需要确保database下的ENDF70.69文件夹中的三个子文件夹下的xml文件中有正确的路径。
WIMSN下面的WIMSNdir.xml，LSQsub下面的LSQsubdir.xml，
还有LSQIRsub下面的LSQsubdir.xml。这三个文件中均有一个`path`标签，需要确保每个文件
对应的`path`标签中应为该文件所在的文件夹路径。假如database在E:\Bamboo路径下，那么
这三个文件中的`path`分别如下：

```xml
<path>E:\Bamboo\database\ENDF70.69\WIMSN</path>
```

```xml
<path>E:\Bamboo\database\ENDF70.69\LSQsub</path>
```

```xml
<path>E:\Bamboo\database\ENDF70.69\LSQIRsub</path>
```

如果又出现了如下报错：

![Q2_2](img/Q2_2.png)

说明没有LSQsub中的xml文件没有改对，按照上面的说明再仔细改一遍。

3. 使用手册中的目录结构和实际的结构不一样

使用手册中说：

![Q3_1](img/Q3_1.png)

但是实际的目录结构并没有使用手册中的那些文件：

![Q3_2](img/Q3_2.png)

这个是因为使用手册中的这一段描述是针对源码的说明，用于课程设计的压缩包中不包含源码。
