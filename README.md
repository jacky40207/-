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
  1. 利用nltk中的stop words來去除摘要中不太具有意義的高頻單字，以節省存儲空間和提高搜索效率
  2. 將論文的種類做onehot編碼
  3. 用sciBERT中的tokenizer來將摘要中的文字進行斷字以及編碼
  4. 取前128個字和後128個字做為輸入資料
# 模型建立
環境以kearas_bert為主，以sciBERT為預訓練模型(https://github.com/allenai/scibert)

1. 取第 4 和 12 層 Transformer Encoder 的 output,使用 globalaveragepooling1d 做展開
2. 將 globalaveragepooling1d 的 output 使用 Maximum 的方式做合併
3. 輸出至 sigmoid function 前做 dropout,dropout rate 為 0.1
# 成果
在vaildation data上得到
precision : 0.43114
recall : 0.94323
FS : 0.59178
# 參考文獻
1. I. Beltagy, K. Lo, and A. Cohan. SciBERT: A pretrained language model for scientific text. In Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Lan­guage Processing (EMNLP­-IJCNLP), pages 3615–3620, Hong Kong, China, Nov. 2019. Association for Computational Linguistics.
2. https://leemeng.tw/attack_on_bert_transfer_learning_in_nlp.html
