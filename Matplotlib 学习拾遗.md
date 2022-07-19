# Matplotlib 学习拾遗
## 1. 图像大小设置
```python
import matplotlib.pyplot as plt
fig = plt.figure(figsize=(20,8),dpi=80)
# figsize: 图片长宽
# dpi: 图像清晰度
```
## 2. 数据作图
```python
import matplotlib.pyplot as plt
import numpy as np

x = range(0,10,1) # range(）函数按照整数步长生成对应range区间
				   # range() 函数返回值类型为range
_x = np.arange(0.0,1.0,0.1)# np.arange()函数可以按照浮点数步长生成对应区间
							# np.arange()函数返回值类型为numpy.ndarray
y = [0,1,2,3,6,2,6,8,2,1] # 因变量
plt.plot(list(x),y)#绘制折线图
				   #x轴坐标使用x或list(x)均可，list(x)转换为列表后与Y统一格式
plt.show()#展示绘制结果
```
## 3. 图像保存
```python
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(20,8),dpi=80)
x = range(0,10,1)
y = [0,1,2,3,6,2,6,8,2,1]
plt.plot(x,y)
plt.savefig("./myFig.png")#使用savefig()函数将图片保存至当前工作路径下
						  #使用png格式保证图片在缩放时没有失真变形
    					  #plt.show()与plt.savefig()不能同时使用，会导致图片保存失败
```
## 4. 图像坐标点标签
```python
import matplotlib.pyplot as plt
from matplotlib import rc

plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']#解决中文乱码问题

fig = plt.figure(figsize=(20,8),dpi=80)
x = range(0,10,1)
y = [0,1,2,3,6,2,6,8,2,1]

_x_ticks = ["{}岁".format(i) for i in x]#规定x轴坐标点数字意义（单位）
plt.xticks(x, _x_ticks, rotation=45)#当某一坐标点信息过长可使用rotation参数调整其旋转角度

_y = range(0,9)#新建一个range按照步长涵盖全部y的取值
			   #如果在y的基础上创建_y_ticks则在y取到的点有显示
_y_ticks = ["{}个".format(i) for i in _y]#规定y轴坐标点数字意义（单位）
plt.yticks(_y,_y_ticks)

plt.plot(x,y)
plt.show()
```
## 5. 图像坐标轴标签
```python
import matplotlib.pyplot as plt
from matplotlib import rc

plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']#解决中文乱码问题

fig = plt.figure(figsize=(20,8),dpi=80)
x = range(0,10,1)
y = [0,1,2,3,6,2,6,8,2,1]

_x_ticks = ["{}岁".format(i) for i in x]#规定x轴数字意义（单位）
plt.xticks(x, _x_ticks, rotation=45)#当某一坐标点信息过长可使用rotation参数调整其旋转角度

_y = range(0,9)#新建一个range按照步长涵盖全部y的取值
			   #如果在y的基础上创建_y_ticks则在y取到的点有显示
_y_ticks = ["{}个".format(i) for i in _y]#规定y轴数字意义（单位）
plt.yticks(_y,_y_ticks)

plt.xlabel("用户年龄")# x轴描述
plt.ylabel("玩具数量")# y轴描述

plt.plot(x,y)
plt.show()
````
## 6. 多条曲线
```python
import matplotlib.pyplot as plt
from matplotlib import rc

plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']#解决中文乱码问题

fig = plt.figure(figsize=(20,8),dpi=80)
x = range(0,10,1)
y = [0,1,2,3,6,2,6,8,2,1]
y_2 = [2,6,8,6,2,3,4,5,6,7]

_x_ticks = ["{}岁".format(i) for i in x]#规定x轴数字意义（单位）
plt.xticks(x, _x_ticks, rotation=45)#当某一坐标点信息过长可使用rotation参数调整其旋转角度

_y = range(0,9)#新建一个range按照步长涵盖全部y的取值
			   #如果在y的基础上创建_y_ticks则在y取到的点有显示
_y_ticks = ["{}个".format(i) for i in _y]#规定y轴数字意义（单位）
plt.yticks(_y,_y_ticks)

plt.xlabel("用户年龄")# x轴描述
plt.ylabel("玩具数量")# y轴描述

plt.plot(x,y)
plt.plot(x,y_2)# 因变量y与y_2共用同一一个自变量轴
plt.show()
```
## 7. 曲线格式
```PYTHON
import matplotlib.pyplot as plt
from matplotlib import rc

plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']#解决中文乱码问题

fig = plt.figure(figsize=(20,8),dpi=80)
x = range(0,10,1)
y = [0,1,2,3,6,2,6,8,2,1]
y_2 = [2,6,8,6,2,3,4,5,6,7]

_x_ticks = ["{}岁".format(i) for i in x]#规定x轴数字意义（单位）
plt.xticks(x, _x_ticks, rotation=45)#当某一坐标点信息过长可使用rotation参数调整其旋转角度

_y = range(0,9)#新建一个range按照步长涵盖全部y的取值
			   #如果在y的基础上创建_y_ticks则在y取到的点有显示
_y_ticks = ["{}个".format(i) for i in _y]#规定y轴数字意义（单位）
plt.yticks(_y,_y_ticks)

plt.xlabel("用户年龄")# x轴描述
plt.ylabel("玩具数量")# y轴描述

plt.plot(x,y,color='orange',linestyle="--")#橙色曲线、短折线
plt.plot(x,y_2,color='g',linestyle=":")#绿色曲线、点状折线
plt.show()
```
## 8. 添加图例
```python
import matplotlib.pyplot as plt
from matplotlib import rc

plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']#解决中文乱码问题

fig = plt.figure(figsize=(20,8),dpi=80)
x = range(0,10,1)
y = [0,1,2,3,6,2,6,8,2,1]
y_2 = [2,6,8,6,2,3,4,5,6,7]

_x_ticks = ["{}岁".format(i) for i in x]#规定x轴数字意义（单位）
plt.xticks(x, _x_ticks, rotation=45)#当某一坐标点信息过长可使用rotation参数调整其旋转角度

_y = range(0,9)#新建一个range按照步长涵盖全部y的取值
			   #如果在y的基础上创建_y_ticks则在y取到的点有显示
_y_ticks = ["{}个".format(i) for i in _y]#规定y轴数字意义（单位）
plt.yticks(_y,_y_ticks)

plt.xlabel("用户年龄")# x轴描述
plt.ylabel("玩具数量")# y轴描述

plt.plot(x,y,label="自己"，color='orange',linestyle="--")#橙色曲线、短折线
plt.plot(x,y_2,label="同桌"，color='g',linestyle=":")#绿色曲线、点状折线
plt.legend()#plot()中使用label参数标注图例
			#legend()函数使图例生效
plt.show()
```
