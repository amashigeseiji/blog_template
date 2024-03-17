# blog template

## プレビュー

以下のコマンドでプレビューできます。

```
npm run watch
```

`http://localhost:8000/`

デフォルトでは8000ポートを利用しますが、環境変数を使ってポート番号を上書きできます。

```
PORT=8001 npm run watch
```

## 記事を書く

`./data/` 以下にマークダウンファイルを入稿します。

ファイル冒頭にコメントで変数を指定できます。  
`title` と `url` と `published`はが必須です。  
`url` は出力先になります。  
`published` は index ファイルがソートするのに利用します。

```markdown
<!--
title: sample article
url: /sample_article
published: 2024/03/18 00:00
-->

トップレベル見出しは `title` 変数が利用されます。  
変えたい場合は template/default.html を修正してください。

## サンプル記事

これはサンプル記事です。ブログ開始のときに削除してください。

## マークダウン

記事は、マークダウン記法で記述し、 `.md` ファイルで保存してください。

リンクは次のように記述します。  
[アンカーテキストはこちら](http://example.com)

リストは次のように記述します。
* リスト1
* リスト2
* リスト3

画像は、 `data/image/` 以下に配置して、パスを指定してください。

`data/image/sample.jpg` などがあれば、次の指定になります。  
`![代替テキストを入力してください](/image/sample.jpg)`

![placeholdの画像](https://placehold.jp/150x150.png)

### 見出し3

スクリプトを記述することができます。

{script}
return (new Date()).toString()
{/script}
```


## テンプレートエンジン

### 変数

コメントに変数を記述できます。

```markdown
<!--
foo: fooVariableContent
bar: varVariableContent
-->
```

and in template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title></title>
</head>
<body>
  {{foo}}
  {{bar}}
</body>
</html>
```

`{{foo}}` と `{{bar}}` は `'fooVariableContent'` と `'barVariableContent'` に置換されます。

### IF

```markdown
<!--
someVariable: true
-->
{if someVariable}
This content will be present.
{/if}

{if undefinedValue}
This content will be removed.
{else}
This is else content.
{/if}
```

### SCRIPT

```markdown
{script}
// write javascript and return value
{/script}
```
