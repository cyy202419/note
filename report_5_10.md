# 陈阳阳的学习进展（5.10）
1. 尝试GPU加速：在windows上配置wsl，成功实现GPU加速深度学习
2. 尝试了L2正则化，BatchNorm，dropout
3. 所有原子平移L，输出不变。增强数据，
4. 特征{64个原子xyz坐标/L，L，温度，密度}，对x, y, z加上[-1, 0, 1]的

## Hydrogen in a box

### 64个氢原子/分子的示意图
<img src="https://github.com/cyy202419/note/assets/64142343/68366f88-6033-4ec5-99d4-a27cd7a38e60" alt="hydrogen_in_a_box" title="hydrogen_in_a_box" width="400" />

1. 一些想法：如果64个原子存在某种固定的空间顺序，可以尝试相邻坐标点之间的差分作为新特征；否则可以尝试所有可能的成对坐标差分作为特征，共2016个。
2. 数据量过大，利用yield、next生成训练数据
