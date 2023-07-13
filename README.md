# gpt4all-project
本项目为大二下学期深度学习大作业。主要实现了对`pythia-1.4b-gpt4all-pretrain`模型进行`p-tuning`，使其输出带有情绪信息。
本项目参考文献链接：https://blog.csdn.net/qq_35812205/article/details/131647749


项目原计划是对`gpt4all-j`进行本地部署、训练以及微调，部署按照gpt4all官网教程成功实现，但由于gpt4all-j训练所需内存较大，受硬件限制后续操作使用轻量化模型`pythia-1.4b-gpt4all-pretrain`进行替代，本项目所使用的预训练模型与数据集都能在HuggingFace上找到。
整个项目实现过程中分别在colab和kaggle上进行p-tuning训练与测试。


`nice_train.ipynb`在colab上使用`ought/raft`数据集中的`witter_complaints`数据集进行训练，该数据集包含推特用户的言论文字，并有对应的"complaint"或"no complaint"标签。训练完成时training_loss为0.095800，validation_loss为0.101449，微调模型训练效果符合预期。训练完成之后将模型保存到了本地，模型可在本项目model文件夹中找到。


`nice_test.ipynb`在kaggle上导入模型，并对模型进行测试。测试prompt"I had too much work to do so that"，对应output为"I'm not going to do it, I"。我对原模型进行了对比测试，原模型output为"I didn't have time to take a break.I"。对比发现经过`P-Tunning`的模型输出包含更鲜明、更强烈的情感信息。
