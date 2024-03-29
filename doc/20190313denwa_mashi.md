# 2019/03/13 大量の自動電話応対

今回は、さらに複雑なデータ処理を行ってみます。

- **何件もの電話相手情報を読み込み、**
    - 「株式会社〇〇 田中様 営業」など
- **それぞれに対して適した対応を判定し、**
    - 「お断り」など
- **どのように応対したかをテキストファイルとして記録します**
    - `株式会社〇〇,田中様,営業,お断り`など

## 関数

プログラミングにおいて、基本的には、同じ処理を何回も書き直すことは悪です。なぜかといえば面倒だからです。そこでPythonには一度作ったプログラムをうまく再利用するため、**関数**という機能が用意されています。これは命令文の塊に名前を付け、その名前を一言唱えるだけでその命令文の塊を呼び出せるようにする機能です。

```
# 例
# 関数を定義する
def aisatsu():
  print('お電話ありがとうございます。')
  print('申し訳ありませんが、現在間に合っております。')
  print('失礼いたします。')

# 一言書くだけで関数の中身を実行できる。
aisatsu()
```

関数は入力を受け取り、計算した結果を出力する形にすることもできます。

```
# 担当者名を受け取って挨拶の文章をくっつける
def aisatsu2(name):
  a = name + 'でございますね。お世話になっております。'
  return a

# kekkaにaisatsu2の結果が入れられる
kekka = aisatsu2('田中様')
print(kekka)
```

前回作った電話対応の処理を関数にして、一言で使えるようにしましょう。

## ファイル読み込み

## (メモ)

組み込み型、リスト、関数、複雑な文字列処理(format)、ファイル操作。

数件の電話データがCSVファイルとしてまとまっている。これを読み込んで処理しよう。

ログを作る。

|日付|時間|企業名|担当者名|ご用件|
|:--|:--|:--|:--|:--|
|3月13日|14:15|株式会社〇〇|田中様|SES契約のご提案|

