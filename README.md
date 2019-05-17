# dynamic-seq2seq
### 基于中文语料和dynamic_rnn的seq2seq模型


### 用法:
    seq = Seq2seq()
    # 预处理
    seq.preprocess()
    # 训练
    seq.train()
    # 预测
    seq.predict("天气")
   

### 效果:
    
    me >  天气
    AI >  地点： 重庆
    气温： 7
    注意： 天气较凉，较易发生感冒，请适当增加衣服。体质较弱的朋友尤其应该注意防护。

### Action:

本项目添加了Action支持，可以定制自己的功能  
后续会加入多轮会话的支持！  

在action.py文件中,注册自己action标签及对应的接口，如:

    #　注意：参数为固定参数
    def act_weather(model, output_str, raw_input):
        #TODO: Get weather by api
        page = requests.get("http://wthrcdn.etouch.cn/weather_mini?city=重庆")
        data = page.json()
        temperature = data['data']['wendu']
        notice = data['data']['ganmao']
        outstrs = "地点： %s\n气温： %s\n注意： %s" % ("重庆", temperature.encode("utf-8"), notice.encode("utf-8"))
        return outstrs


    actions = {
        "__Weather__":act_weather
    }

Tips: 接口的参数暂时固定,后续更新  

同时，训练语料如下设计:

    # Q.txt
    天气
    # A.txt
    __Weather__


