# TFIDFCalculator
PD-2 HW4
# Search Engine I - Search Index Construction for English Corpus based on TF-IDF Calculation

## Introduction

TF-IDF (Term Frequency-Inverse Document Frequency) 是一種用於評估文本中某個詞重要性的方法，它結合了詞頻 (TF) 和逆文檔頻率 (IDF)。TF表示詞在文檔中出現的頻率，而IDF表示該詞在整個語料庫中的普遍性。通過將TF和IDF相乘，我們可以得到該詞在文本中的權重，這個權重可以用來衡量該詞的重要性。

TF-IDF廣泛應用於信息檢索、文本分類、關鍵詞提取等領域。它可以幫助確定文檔與查詢的相關性，文本的分類，以及重要關鍵詞的識別。此外，還可以用於資訊推薦和文本相似度計算。總之，TF-IDF是一種簡單而有效的文本特徵表示方法，可以幫助我們更好地理解和處理文本數據。

TF-IDF (Term Frequency-Inverse Document Frequency) is a method used to evaluate the importance of a word in a text. It combines term frequency (TF), which is the frequency of a word in a document, and inverse document frequency (IDF), which measures the rarity of the word across the entire corpus. By multiplying TF and IDF, the word's weight in the text is obtained, representing its importance.

TF-IDF is widely applied in information retrieval, text classification, and keyword extraction. It helps determine the relevance of a document to a query, classify documents, and identify key keywords. It can also be used for recommendation systems and text similarity calculations. Overall, TF-IDF is a simple yet effective text feature representation method that aids in better understanding and processing textual data.

### TF Calculation

TF指的是在文檔中某個詞的出現頻率，計算公式如下：

TF refers to the frequency of a word in a document. The formula is:

$TF(t, d) = \frac{f_{t,d}}{\sum_{t' \in d} f_{t',d}}$

- $f_{t,d}$: 詞彙$t$在文檔$d$中的出現次數
- $\sum_{t' \in d} f_{t',d}$: 文檔中所有詞彙的總出現次數

### IDF Calculation

IDF 衡量的是詞彙在整個文檔集合中的重要性，計算公式如下：

IDF measures the importance of a word across the entire corpus. The formula is:

$IDF(t, D) = \log{\frac{N}{|\{d \in D : t \in d\}|}}$

- $N$: 文檔集合中的總文檔數
- $|\{d \in D : t \in d\}|$: 包含詞彙$t$的文檔數

### TF-IDF Calculation

TF-IDF是詞頻和逆文檔頻率的乘積，計算公式如下：

TF-IDF is the product of term frequency and inverse document frequency. The formula is:

$TF-IDF(t, d, D) = TF(t, d) \times IDF(t, D)$

TF-IDF值用於衡量詞彙在特定文檔中的重要性，以及在整個文檔集合中的重要性。

TF-IDF values measure the importance of a word in a specific document as well as in the entire document collection.

### Parsing Rules

- 將所有**非英文字元**替換為空白。
- 將所有大寫英文字母轉換為小寫。
- 使用空白字符進行詞彙切分。

Parsing steps:
1. Replace all non-English characters with spaces.
2. Convert all uppercase English letters to lowercase.
3. Use space characters for word segmentation.

## Input Arguments

```bash
java TFIDFCalculator /home/share/hw4/docs.txt tc0.txt
```

- 第一個參數為文本的絕對路徑。
- 第二個參數是測資檔案。

The first argument is the absolute path of the corpus file, and the second is the test file.

## Input Issues

每個測資檔案包含兩行，分別為詞彙和對應的文本編號。

Each test file contains two lines: the first line consists of words to be queried, and the second line contains the corresponding document numbers.

## Output Issues

輸出需要依次計算每個詞彙在指定文本中的TF-IDF值，並保存在 `output.txt` 文件中，數值格式為小數點後五位。

The output should calculate the TF-IDF value of each word in the specified document and store it in the `output.txt` file, with values formatted to five decimal places.

```java
{YOUR_WRITER}.write(String.format("%.5f", tfIdf) + " ");
```

## Example

### Input

測資檔案 `tc0.txt`:

```
same the apple
30 13 100
```

### Output

```
0.02667 0.00019 0.00000
``` 

This output represents the TF-IDF values of the words "same," "the," and "apple" in documents 30, 13, and 100, respectively.
