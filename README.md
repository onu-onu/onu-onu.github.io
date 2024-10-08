# 静的ポートフォリオ
コンテンツはxmlとマークダウンが混じった独自の形式で記述し、コマンドライン上からpythonスクリプトでhtmlに変換する  

## コンテンツの配置
- /res/xml/
    - xmlの置き場所
    - ファイル名は自由
- /res/template*.html
    - htmlのテンプレート
    - xml2html.py内で用いる
- /res/*/contentsTree.csv
    - worksコンテンツの順序を整理するためのcsv
    - treeとなっているが基本的には一方向配列
    - .html同士のリンクの生成に用いる
    - コンテンツジャンルごとに階層が異なる

## xmlの書き方
```xml
<title>タイトル</title>
<info>日付 / コンテンツの形式など</info>
<mov>動画のリンク(推奨:youtube)</mov>
<imgl0>画像のリンク1</imgl0>
<imgr0>画像のリンク2</imgr0>
<imgl1>画像は幾つでも追加できる</imgl1>
<left>
左側の文書コンテンツ
マークダウン形式で記述
インデントはしないほうがいい
</left>

<right>
右側の文書コンテンツ
マークダウン形式で記述
</right>
```


## HTML生成方法
- /xml2html.py
  - xmlをhtmlに変換するpyhtonスクリプト
- 実行コマンド
  ```
  python3 xml2html.py art film code
  ```

## webサーバーでの動作確認
```
cd dist
python3 -m http.server 8000  
```

## 画像のリサイズ
```
sh resize.sh [dirname] [width px]
```
同ディレクトリ下にarchiveディレクトリが生成されて、オリジナル画像を自動的にアーカイブします。