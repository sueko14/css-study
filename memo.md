# メモ

#### cssは先に読み込まれたもの　＜　後に読み込まれたもの　で上書きされる  
以下だとreset < layout < responsive
```
<head>
  <link rel="stylesheet" href="css/reset.css" >
  <link rel="stylesheet" href="css/layout.css" >
  <link rel="stylesheet" href="css/responsive.css" >
</head>
```

#### css内で他のcssを読み込む  
この場合もimport文の順番が重要。  
```
@import url(css/reset.css)
```

#### セレクタ
- 要素セレクタ (pre とかpとか)
- idセレクタ #
- classセレクタ .
- 子孫クラスタ #container header h1#site-idなど 絞り込み
- 擬似クラス 状態でスタイル分け:hoverとか
  - E:nth-child(n) n番目のE要素。nにodd,evenも指定可
- 擬似要素  ::擬似要素名
  - ::before
  - ::after
  - ::first-letter
  - ::first-line
  - ::marker
- 子セレクタ：子要素のみスタイル適用　要素>要素
- 隣接セレクタ：ある要素の直後に現れる要素だけ指定 要素+要素
- 属性セレクタ　html要素の属性で特定するセレクタ
  - 要素[属性] ある属性を持っている要素だけをターゲット
  - 要素[属性="値"] 
    - ex) input[type="submit"]
  - 要素[属性~="値"] 属性の値が２つ異常ある時に、
- ユニバーサルセレクタ *

#### CSSの優先順位
1. CSSのメディアタイプ。指定があれば最優先
2. 出どころ(origins)による優先度
3. セレクタの詳しさ(specificity)による優先度
4. 書いた順番による優先度  

※インラインで書いたCSSは別格。

##### originsによる優先度

1. ブラウザのデフォルトスタイル
2. ユーザースタイル(ユーザーがブラウザ上で設定したスタイル)
3. 作成者のスタイル(html文書に記述したcss)
4. !important付 作成者のスタイル
5. !important付 ユーザースタイル

##### specificityによる優先度

1. 全称セレクタ *
2. 要素セレクタ
3. classセレクタ
4. idセレクタ

#### CSSの継承
親セレクタに設定したプロパティが、子セレクタにも継承されることがある。  
ただし、継承されるかどうかは<strong>プロパティごと</strong>に決まっている。  

**ざっくりした覚え方**  
- 文字に関するプロパティ：ほとんど継承する
- ボックス、表示位置、配置：継承しない
  - ボックス：width, height, margin, padding, border, ourline, background
  - 表示・配置：overflow, display, float, clear, position, z-index

**強制的に継承させる方法**  
プロパティにinheritをつける。
ただし、継承した場合は「相対性(120%など)」を受け継ぐのではなく、計算後の実際のサイズを受け継ぐ