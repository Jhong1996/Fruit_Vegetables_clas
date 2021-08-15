# AI达人创造营作业：水果蔬菜分类

## 项目描述
创意名称

    水果蔬菜分类

创意简介

    在超市或者商场，顾客把东西放在称上自动识别称重，减小超市工作人员的工作量

详细说明

  目标应用场景

    超市、商场、水果店等

实现的功能

    对水果蔬菜自动识别称重

解决的问题

    减小超市工作人员的工作量

创意的价值

    为繁琐复杂的重复称重劳动减小人力投入

## 项目结构
```
-|data
-|work
-README.MD
-Fruit_Vegetables_clas.ipynb
```

## 模型训练与调参
使用套件：使用高层API

使用优化器：使用 Adam

调整了那些参数：
```
# 模型配置
# 定义输入
input_define = paddle.static.InputSpec(shape=[-1,3,100,100], dtype='float32', name='img')
label_define = paddle.static.InputSpec(shape=[-1,1], dtype='int64', name='label')

# 实例化网络对象并定义优化器等
model = MyNet()
model = paddle.Model(model, inputs=input_define, labels=label_define)   # 封装模型
optimizer = paddle.optimizer.Adam(learning_rate=0.0003, parameters=model.parameters())

model.prepare(optimizer=optimizer,
              loss=paddle.nn.CrossEntropyLoss(),
              metrics=paddle.metric.Accuracy())
              
              
model.fit(train_data=train_dataset,
          eval_data=eval_dataset,
          batch_size=8,
          epochs=10,
          save_dir='output',
          save_freq=5,
          log_freq=10,
          verbose=1
          )
```

心得：恩，数据很重要，数据集的多样性很重要、很重要、很重要


## 使用方式
A：在AI Studio上[运行本项目](https://aistudio.baidu.com/aistudio/projectdetail/2283732)

B：此处由项目作者进行撰写使用方式。
