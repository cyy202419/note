# 陈阳阳的学习进展（5.10）
1. 尝试GPU加速：在windows上配置wsl，成功实现GPU加速深度学习
2. 尝试了L2正则化，BatchNorm，dropout
3. 所有原子平移L，输出不变，增强数据27倍，按照$\\{(x+a, y+b, z+c)|a,b,c \in \\{-1, 0, 1 \\}\\}$
4. 特征{64个原子xyz坐标/L，L，温度，密度}
<img src="https://github.com/cyy202419/note/assets/64142343/678807ef-54b4-4975-8961-b3081477d99f" alt="DNN" title="DNN" width="500" />
5. 存在过拟合，预测比较差
6. BatchNorm
<img src="https://github.com/cyy202419/note/assets/64142343/d7691a7d-e267-4362-8783-77ad579ddf23" alt="Use BatchNorm" title="Use BatchNorm" width="500" />

### 20% Dropout
<img src="https://github.com/cyy202419/note/assets/64142343/02961886-efac-4240-a0df-d964ed5670a2" alt="Dropout 20%" title="Dropout 20%" width="500" />

### 30% Dropout
![image]()
<img src="https://github.com/cyy202419/note/assets/64142343/9abd9725-ee36-4ae0-91a5-032b70270313" alt="Dropout 30%" title="Dropout 30%" width="500" />


## Hydrogen in a box

### 64个氢原子/分子的示意图
<img src="https://github.com/cyy202419/note/assets/64142343/68366f88-6033-4ec5-99d4-a27cd7a38e60" alt="hydrogen_in_a_box" title="hydrogen_in_a_box" width="400" />

1. 一些想法：如果64个原子存在某种固定的空间顺序，可以尝试相邻坐标点之间的差分作为新特征；否则可以尝试所有可能的成对坐标差分作为特征，共2016个。
2. 数据量过大，利用yield、next生成训练数据
