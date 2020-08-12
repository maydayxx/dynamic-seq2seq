# Multiple_Best_opt
### 国家流量预测通话人数预测选择模型


Main files:
 * `Multiple_DrewCountrymo.py` - 该脚本是对一个国家的流量进行数据可视化展示，分析观察该国家在时序上是否存在周期性规律，通过可视化观察设置步长。
 通过运行该脚本得到的结果是在当前路径下生成一张国家的流量可视化折线图`./中国台湾.png`（原脚本中以中国台湾举例子）
 * `Multiple_series_mergerdata.py` - 该脚本是对当前路径下的`./all_voice_data2`进行数据预处理。对多个csv文件进行统一读写。运行的结果为在`./data`文件价下生成
`voice_mo.csv` `voice_mo2.csv` `voice_mo_cnt.csv` `voice_mo_cnt2.csv`四个文件。`voice_mo2.csv`为通话量文件，用于对通话量的训练和预测用；`voice_mo_cnt2.csv`为通话人数，用于对通话人数的训练和预测用。
 说明：`voice_mo.csv`与`voice_mo2.csv`的区别为数据的格式不一样。在神经网络设计中最终采用了`2.csv`格式。
 * `Multiple_series_train_voice_mo.py` - 该脚本为神经网络模型文件。主要用于神经网络模型的搭建与训练。运行该脚本前请确保`./data`文件下生成了`voice_mo2.csv`文件。
 通过模型训练最终生成
 `./model/.h5`模型文件。
 `./Pic_make/通话量mo训练&验证的均方误差_24h7_50n.png`loss函数图
 `./model_mo.png` 神经网络模型可视化
 * `Multiple_series_prediction_mo.py` - 该脚本用于预测。最终生成`./result/predict_country_voice_mo.csv`该文件为预测的通话量文件
 * `Multiple_series_train_voice_mo_cnt.py` - cnt后缀为人数预测
 * `Multiple_Transit_agent.py` - 最优中间商选择算法实现。运行该脚本前请确保已经有了以下文件`./data/rest.csv`运营商到中转商的链路容量。`./data/bandwith.csv`中转商到国家的链路容量。
 `./data/flat_model_rate.csv`中转商到国家的单价。`./data/predict_country_voice_mo.csv`各国家的预测的通话量。满足输入的情况下最终会生成`./result/optimal_matrix.csv`文件为输出的最优矩阵
  * `Multiple_CTP.py` 该脚本是对预测的数据与实际的数据的可视化折线图对比分析。生成`./Pic_make/CTP.png`文件
 
 
Requrement:
 * pandas 1.0.1
 * matplotlib 3.1.3
 * sklearn 0.22.1
 * keras 2.2.5
 * joblib 0.14.1
 * numpy 1.16
 
Others:
 * `Showmakecleandata.ipynb`对原始数据进行处理的可视化jupyter文件
