# 文章分類
Data Description
* Id
    流水編號(無特別意義)
* Title
    論文文章標題
* Abstract
    論文摘要
* Classifications
    論文的分類
* 驗證和訓練資料集
  切分為6650筆和350筆
# 資料處理
  1.利用nltk中的stop words來去除摘要中不太具有意義的高頻單字，以節省存儲空間和提高搜索效率
  2.將論文的種類做onehot編碼
  3.用sciBERT中的tokenizer來將摘要中的文字進行斷字以及編碼
# 模型建立
環境以kearas_bert為主，以sciBERT為預訓練模型(https://github.com/allenai/scibert)

1.取第 4 和 12 層 Transformer Encoder 的 output,使用 globalaveragepooling1d 做展開
2. 將 globalaveragepooling1d 的 output 使用 Maximum 的方式做合併
3. 輸出至 sigmoid function 前做 dropout,dropout rate 為 0.1
