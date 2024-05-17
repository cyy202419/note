## 陈阳阳的学习进展（5.10）
### 内容
1. 尝试GPU加速：在windows上配置wsl，成功实现GPU加速深度学习。
2. 阅读`Probabilistic Machine Learning(Introduction)`，主要是Chapter 11, 13。
3. 探索`Hydrogen in a box`，能量误差太大了，只训练了压强。
	1. 尝试增强数据。尝试应用L1，L2正则化、dropout、Batchnorm。
	2. 尝试多种超参数搭配；
4. 在看`Effective Python` `流畅的Python`。

### Hydrogen in a box
#### 增强数据
1. 思路：原子平移L，输出不变：分别沿x,y,z轴平移L。
2. 特征：{64个原子xyz坐标/L，L，温度，密度}。由 $\\{(x+a, y+b, z+c)|a,b,c \in \\{-1, 0, 1 \\}\\}$ ，从而增强数据27倍。
3. 结果：

<img src="https://github.com/cyy202419/note/assets/64142343/678807ef-54b4-4975-8961-b3081477d99f" alt="DNN" title="DNN" width="500" />

利用相同的思路可以增强测试集数据：

<img src="https://github.com/cyy202419/note/assets/64142343/b4b1942c-d90e-41a5-baab-f0ff11b75f8d" alt="DNN" title="DNN_MORETEST" width="500" />

 
#### L1, L2正则化，BatchNorm
1. L1正则化（l1_reg=0.001）：

<img src="https://github.com/cyy202419/note/assets/64142343/5fa36e3a-b280-4e4e-a4a1-c3db27190ee1" alt="L1" title="L1" width="500" />

2. L2正则化(l2_reg=0.001):

<img src="https://github.com/cyy202419/note/assets/64142343/216e3c57-9647-41d4-bc32-3f0eb66534e1" alt="L2" title="L2" width="500" />

3. BatchNorm：

<img src="https://github.com/cyy202419/note/assets/64142343/d7691a7d-e267-4362-8783-77ad579ddf23" alt="Use BatchNorm" title="Use BatchNorm" width="500" />

#### Dropout
- dropout_rate = 0.4

<img src="https://github.com/cyy202419/note/assets/64142343/2dc4c658-0483-432b-9443-ef90d2f3da8f" alt="Dropout" title="Dropout" width="500" />

- 增强测试集，

<img src="https://github.com/cyy202419/note/assets/64142343/d0195ee4-5ebe-4963-bd28-857e156a97a4" alt="Dropout_Moretest" title="Dropout_Moretest" width="500" />


### 64个氢原子/分子的示意图
<img src="https://github.com/cyy202419/note/assets/64142343/68366f88-6033-4ec5-99d4-a27cd7a38e60" alt="hydrogen_in_a_box" title="hydrogen_in_a_box" width="400" />

#### 一些想法
1. 体系旋转/延任意矢量平移L/交换任意两个原子坐标，输出应该不变。
	1. 如果64个原子存在某种固定的空间顺序，可以用相邻坐标点之间的差分作为新特征；
	2. 否则可以用所有可能的成对坐标差分作为特征，共2016*3个，如果考虑方向还要 *2。
2. 尝试了将所有原子间距作为特征，共2016个。

 <img src="https://github.com/cyy202419/note/assets/64142343/3b973737-562b-411b-a2e3-640f7cd57ace" alt="2016" title="2016" width="400" />

 - 数学问题：已知所有原子对间距，是否可以唯一确定所有原子相对位置？（似乎不是）

### 计划
1. 尝试使用Pytorch, tensorflow等封装好的工具训练
2. More reading...
