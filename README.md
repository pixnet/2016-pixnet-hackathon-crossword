# 人工智慧自動克漏字填空

痞客邦為華文區最大原生內容創作平台，擁有眾多閱讀者及大量的優質文章。許多的網友會在此平台上尋找生活娛樂的相關資訊，例如旅遊景點、化妝品牌及美食甜點，故如何從文章當中萃取出相關的人事時地物為相當重要的技術。  
  
比賽題目為選擇題形式的克漏字填空。題目來源為各大部落客的熱門文章，我們在這些文章中挑出特定語句，並將語句中的特定詞彙挖空，產生克漏字的問題。

例如：  
>明太祖朱元璋是明朝的開國皇帝。朱元璋出身平民，幼時貧窮，曾為地主放牛。公元1344年，入皇覺寺，25歲時參加郭子興領導的紅巾軍反抗蒙元政權。先後擊敗了陳友諒、張士誠等其他起義軍，統一南方，後北伐滅元，建立大一統的皇朝，國號「大明」。廟號太祖，諡高皇帝。因年號洪武也俗稱朱洪武或洪武帝。

透過解析以上的文章，參賽者可能會拿到下面這樣的題目：  

```
明太祖︽⊙＿⊙︽是明朝的開國皇帝。  
a. 朱元璋
b. 朱頭皮
c. 朱茵
```  
又或是  

```
明太祖︽⊙＿⊙︽是明朝的開國皇帝。  
a. 洪武帝
b. 朱頭皮
c. 朱茵
```

## 資料集
參賽者將獲得完整的**原始本文**與**範例題目**兩個資料集作為訓練資料。在這裡我們先公布部分範例，於參賽者報名成功後將開放完整資料的下載連結。

#### 原始本文集
* 來自痞客邦站內分類為流行、旅遊的熱門文章，同時也是本次比賽題目的出處。但我們也要提醒大家，**問題的答案未必都與原始文章如出一轍，當答案不存在於原始文章的時候，我們希望參賽者選出最接近的答案**。就像上面的例子一樣。
* 完整資料集會再以 Mail 通知

#### 範例題目
* 我們從原始本文集之中整理出來的題目集合。事實上，參賽者也可以不看原始本文集，單純透過解析範例題目，利用語義分析等方法找出問題與答案之中的規則來回答問題。
* [部分範例](./example/question.example)
* [資料格式](./example/question_schema.md)
* 完整資料集會再以 Mail 通知

因為知道每一位參賽者都追求更高的答對率，追求完美，所以原始文本集與範例題目我們一起給你。

## 比賽規則
各隊必需實作 Slack Bot 作為回答比賽題目的 AI 機器人，各隊的參賽 Bot 會被邀請至擂台頻道，擂台主出題 Bot 會提問題目，再由各隊 Bot 回答計算結果，並由大會計分 Bot 來即時統計分數，答題需兼顧正確性及回覆速度。

* Hackathon Slack Team Link: 
* Slack Integratioin Sample Code: 
* Question & Answer format:
* Slack Integration Library
 * https://github.com/slackhq/python-slackclient
 * https://github.com/lins05/slackbot
 * https://github.com/os/slacker

### 加入 PIXNET Hackathon 2016 Slack Team 步驟說明

1. 主辦單位發 Slack 邀請函至參賽者報名所提供的 mail，請收到後接收即加入 PIXNET Hackathon 2016 Slack Team。
2. 由主辦單位產生 Bot 帳號後，發送每隊一個 Bot Token。 ***[重要] 請妥善保管 Bot Token***，切勿流出或有任何機會被公開在網路，若 Bot Token 遺失或是有任何疑慮，請與主辦單位連絡並由主辦單位視情形判斷是否配發新的 Token。
3. 進入 Slack Team 後可自行加入測試 channel ***#testonetwothree*** (public)，並於賽前由主辦單位邀請加入正式競賽 channel (private)。

### 競賽方式

1. 參考 bot/bot_sample.ipynb 程式範例，開發出屬於自己的答題機器人。
2. 參賽 Bot 必須辨認主辦單位出題 Bot 的發問格式，才能在第一時間掌握題目。
3. 參賽 Bot 必須儘快的回覆標準答案，並 tag ***計分 Bot*** (主辦單位會公布計分 Bot ID) ，依照規定格式將答案送到 channel。
4. 每一輪發問***二十題***，答對一題得 4 分，答案必須在 ***5分鐘*** 內送到 channel 並由計分 Bot 計算排序結果，每次淘汰最低分***3隊***。
5. 剩下前三名時，進入終極PK賽，為***「搶答制」***，第一個把正確答案回答到 channel 的 Bot 得一分其餘零分，先得到10分者獲勝。

### 問答流程

![img](https://docs.google.com/drawings/d/1jnMu_XfnvgdL3SWo8I5U3lVFG0Vg55pv5YihXumSWyI/pub?w=480&h=360)

* 題目格式為

```
"%s [%d] %s \t### %s [END]"
題目 [1] ____ \t### a: __, b: __, c: __, d: __, e: __ [END]
題目 [2] ____ \t### a: __, b: __, c: __, d: __, e: __ [END]

...
題目 [20] ____ \t### a: __, b: __, c: __, d: __, e: __ [END]
```

* 收到 `機器人小朋友請搶答` 後方能開始作答，並開始計時5分鐘
* 回覆格式為

```
@pix_inspector: 請給分 1 : c, 2 : d, 3 : d ... , 20 : d
```

* 計分 Bot 會立即把分數回復於 channel 之中

![img](https://docs.google.com/drawings/d/1DGgGnpfEwl_dTdAugig-pB2sfyz50PJqFpJeNf1J4YM/pub?w=480&h=360)

* 5分鐘時間到，出題 Bot 發 request 請計分 Bot公布排序結果
* 計分 Bot公布排序，並由主辦單位admin手動移除淘汰 Bot

### 評分方式

* 演算法推薦結果正確性 70% 
* 簡報解說 30%（包含簡報內容、演算法設計、資料闡釋與分析等）


## 推薦閱讀
* [Deep Learning, NLP, and Representations](http://colah.github.io/posts/2014-07-NLP-RNNs-Representations/)
* [Vector Representations of Words](https://www.tensorflow.org/versions/r0.7/tutorials/word2vec/index.html)


## 補充說明

* 由於本站內容龐大，人力有所不逮。本次題目為電腦半自動選題加上人工過濾，若題目有疏漏之處還請不吝指正。
* 為確保比賽順暢，詳細規則主辦單位保留細節微調之權利，並於線上說明會統一說明。
