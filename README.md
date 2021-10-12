# QuoteBERT

说明：完成引语提取、引语归因和实体链接任务。引语提取和引语归因采用一个 fine-tunedBERT 模型，实体链接采用 neuralcoref 开源工具包完成。

要求：Python 3、Anaconda 环境
（使用其他虚拟环境需要修改setup.sh）

模型参数：将提供的模型checkpoint下载到 models 目录下。

输入/输出样例：见 input 和 output 目录。每个json文件是一篇新闻，每个输入对应一个输出。

配置：
```
bash setup.sh
```

运行一次：
```
python main.py
```
程序将读入input目录下的所有输入，处理后以相同的文件名输出到output目录中。


JSON 字段含义：

| 字段  |   含义  |
| ---- | ---- |
|   articleNum   |  文件名    |
|   title   |  新闻标题    |
|   time   |  新闻发表时间    |
|   source   |  新闻来源    |
|   content   |  新闻正文（**必须用\n分割**）    |
|   quote   |  引语数组，内含多个引语条目    |
|   quoteSpeakerCharOffsetsFirst   | 说话人字符串在正文的偏移量     |
|   quoteSpeakerCharOffsetsSecond   | 说话人字符串在正文的偏移量      |
|   quotation   | 引语正文     |
|   quoteCharOffsetsFirst   | 引语字符串在正文的偏移量     |
|   quoteCharOffsetsSecond   | 引语字符串在正文的偏移量     |
|   SegmentOffset   | 引语所在段在正文的偏移量     |
|   Type   | 提取引语的方式</br>例如：说话人在引语左侧</br>说话人在引语右侧     |
|   corefMention   | 说话人经过指代消解后的名字     |
|   corefOffsetBegin   | 说话人经过指代消解后的字符串在正文的偏移量     |
|   corefOffsetEnd   | 说话人经过指代消解后的字符串在正文的偏移量     |
|   corefStatus   | 指代消解是否成功     |
|   mention   | 说话人经过实体链接后的名字     |
|   links   | 说话人的维基百科链接     |
|   mentionID   | 说话人的维基数据ID     |
|   mentionSpan   | 被指代消解的字符串</br>例如：he、she、it     |
|   mentionAbout   | 说话人在维基百科的介绍</br>例如：当代著名作家     |
|   mentionProperty   | 说话人具有的属性</br>例如：人、组织、机构     |
|   linkStatus   | 实体链接是否成功     |

