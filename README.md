# Huawei Bert

## Overview
本项目主要使用alarm数据和5GC静态知识库两部分数据进行训练,然后对于缺失的token和cell进行恢复。
<br />
我们利用Bert模型设计了mask loss和triple loss对模型进行训练。 <br />
前者包括token的mask和cell的mask，来计算预测值和真实值的mask loss。后者通过Bert生成头实体、关系、尾实体的embedding表示，并通过RotatE的KGE模型来生成triple loss。 

## Dependencies
- ```Python 3```
- ```PyTorch >= 1.8.0```
- ```Transformers>= 4.11.3```
- ```NumPy```

- All experiments are performed with one RTX 3090Ti GPU.

## Prerequisites
我们使用 ``` data_process.py ``` 来生成alarm和kpi的机器数据 <br />
我们使用 ``` /data/5GC静态知识库/deal_serialization.py ``` 生成序列化的三元组数据来计算ke loss。同时也将序列化的实体也作为机器alarm数据的一部分

## Code Structures
代码主要包括一下四个部分
- **main.py**: 包含一些初始化操作和模型训练验证过程
- **model.py**: 该模型包含两个模型，分别为mask loss损失模型和triple loss损失模型
- **dataloader.py**: 它包含两个dataloader构建alarm数据和静态知识库
- **utils.py**: 包含日志信息、随机种子设置、加载mask Loss的数据、加载Triple Loss的数据、ADV Loss的计算

## Train && Valid
```
# Use bash script
bash script.sh
```


