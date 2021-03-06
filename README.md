# Mathematical-expression-ocr-master
## 百度AI课程第三个项目——数学文本公式识别
### 数据集处理部分：
#### 本项目数据集来自于哈佛NLP实验室提供的im2latex-100k
#### 这个数据集如果直接拿来训练由于存在大量空白的边缘部分造成训练效果极差，需要做一个roi预处理，对应的公式文件也需要在相邻符号之间加入一个空格
### 数据集说明
#### 数据集包含三部分，图像数据集，公式lst文件，以及包含图像与公式对应信息的lst文件
### 建立数据集之间对应关系
#### python preprocess.py
### 建立词表
#### python build_vocab.py
### 训练
#### python train.py
### 测试
#### python evaluate.py
### 算法效果
#### 使用未经预处理的数据集进行训练，BLEU=0.0035
| test | epoch | Batch_size_per_gpu | lr | BLEU |
| :------: | :------: | :------: | :------: | :------: |
| greedy-search | 15 | 4 | 0.0005 | 3.67 |
| greedy-search | 25 | 8 | 0.0001 | 16.32 |
| greedy-search | 50 | 8 | 0.0001 | 13.75 |
| Beam-search | 15 | 4 | 0.0001 | 7.94 |
| Beam-search | 25 | 4 | 0.0001 | 17.83 |
| Beam-search | 50 | 16 | 0.0001 | 28.74 |
| Beam-search | 50 | 8 | 0.0001 | 44.61 |
### 与其他算法效果对比
| model | attention | BLEU |
| :------: | :------: | :------: |
| INFTY | n/a | 51.20 |
| CTC | n/a | 39.20 |
| CAPTION | standard | 52.53 |
| Harvard | standard | 58.41 |
| Harvard | coarse-only | 53.40 |
| Harvard | hieraachical | 60.32 |
| ours | standard | 44.61 |
