# 陈阳阳的学习进展（5.10）
## 内容
1. 尝试GPU加速：在windows上配置wsl，成功实现GPU加速深度学习。
2. 阅读`Probabilistic Machine Learning`
3. 探索`Hydrogen in a box`

## Hydrogen in a box
### 增强数据
1. 思路：所有原子平移L，输出不变——分别沿x,y,z轴平移L。
2. 特征：{64个原子xyz坐标/L，L，温度，密度}。由 $\\{(x+a, y+b, z+c)|a,b,c \in \\{-1, 0, 1 \\}\\}$ ，x,y,z为体系坐标，从而增强数据27倍。
3. 结果：过拟合，预测不佳
<img src="https://github.com/cyy202419/note/assets/64142343/678807ef-54b4-4975-8961-b3081477d99f" alt="DNN" title="DNN" width="500" />
 
### L2正则化，BatchNorm
1. L2, BatchNorm的效果不佳
2. BatchNorm效果：
<img src="https://github.com/cyy202419/note/assets/64142343/d7691a7d-e267-4362-8783-77ad579ddf23" alt="Use BatchNorm" title="Use BatchNorm" width="500" />

### Dropout
#### 20% Dropout
<img src="https://github.com/cyy202419/note/assets/64142343/02961886-efac-4240-a0df-d964ed5670a2" alt="Dropout 20%" title="Dropout 20%" width="500" />

#### 30% Dropout
<img src="https://github.com/cyy202419/note/assets/64142343/9abd9725-ee36-4ae0-91a5-032b70270313" alt="Dropout 30%" title="Dropout 30%" width="500" />

#### 40% Dropout
<img src="https://github.com/cyy202419/note/assets/64142343/7decf639-1129-4ef7-b5b1-e7c4300c355a" alt="Dropout 40%" title="Dropout 40%" width="500" />

#### 50% Dropout
<img src="https://github.com/cyy202419/note/assets/64142343/6b92e666-46ef-4ba5-ba9a-9598cd099464" alt="Dropout 50%" title="Dropout 50%" width="500" />

#### 64个氢原子/分子的示意图
<img src="https://github.com/cyy202419/note/assets/64142343/68366f88-6033-4ec5-99d4-a27cd7a38e60" alt="hydrogen_in_a_box" title="hydrogen_in_a_box" width="400" />

##### 一些想法
1. 体系旋转、任意方向平移L；交换任意两个原子坐标，输出应该不变。
2. 如果64个原子存在某种固定的空间顺序，可以用相邻坐标点之间的差分作为新特征；否则可以用所有可能的成对坐标差分作为特征，共2016个。

