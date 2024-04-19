## 陈阳阳的学习汇报

本周我主要完成了以下事情：
1. 软件安装：在自己的电脑上本地安装机器学习所需的软件、依赖
2. 我仔细阅读了您提供的机器学习材料，搜集了overview中提及的一些书籍。
3. 我在自己的计算机上本地正常运行了提供的示例代码，理解和测试程序中的变量、函数。
4. 我开始阅读《Probabilistic Machine Learning》一书，希望系统的回答自己想到的一些问题。
5. 项目实践 - Hydrogen in a Box：
    1. 构建并测试了神经网络模型，探索了不同的数据表示方法和特征组合，并尝试归一化数据和调整特征。
        1. 尝试直接用64个原子坐标(X_1 Y_1 Z_1 ...X_64 Y_64 Z_64) + 盒子大小L，训练根本不收敛
        ![trainwith1200600_2](https://github.com/cyy202419/note/assets/64142343/1a1eb537-76b7-4531-a137-f9b61d890e3e)
        3. 尝试(X_1 Y_1 Z_1 ...X_64 Y_64 Z_64)/L + 盒子大小L，训练收敛，似乎是个正确的方向
       ![trainwith1200600_1](https://github.com/cyy202419/note/assets/64142343/8f5827e0-9470-4956-bdcf-ac0b3e5e37b8)
        5. 尝试(X_1 Y_1 Z_1 ...X_64 Y_64 Z_64)/L + 盒子大小L + 温度 + 密度，温度、密度特征似乎多余
        ![trainwith12006000_3](https://github.com/cyy202419/note/assets/64142343/748bc1c8-8a31-4df1-bd14-6d4cf911ab81)
    2. 尝试不同的训练数据集组合（train on 1200K and 6000K data/train on 1200K and 3000K data）；尝试使用卷积方法来平滑能量数据，降低噪声。![trainwith12006000_4](https://github.com/cyy202419/note/assets/64142343/f4d11820-eaef-4bec-a646-ef7cc5b67972)

    3. 调整learning_rate、batch_size等
 6. 后续计划
    1. 继续《Probabilistic Machine Learning》的学习
    2. 开始“Alanine Dipeptide”
    3. 使用GPU加速；学着写高效的代码
