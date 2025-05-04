---
title: "Markdownの書き方"
excerpt: "Markdown"
coverImage: "/assets/blog/markdown/cover.png"
date: "2025-05-04T16:15:00+09:00"
author:
  name: "dokunira"
  picture: "/assets/blog/authors/dokunira.jpeg"
ogImage:
  url: "/assets/blog/markdown/cover.png"
---

# Markdown
**Markdown** は、可能な限り読みやすく書きやすいように設計されたマークアップ言語である。プレーンテキストのままでも可読性が高い。

> [!NOTE]  
> **マークアップ言語**とは、文とその構造や表示形式を示した言語である。
> 
> HTMLやXMLなどのマークアップ言語とは異なり、プレーンテキストでも可読性が高いものは**軽量マークアップ言語**と呼ばれる。


## Markdownの歴史
Markdown は John Gruber によって（Aaron Swartz の協力を得て）開発され、2004年にMarkdownをHTMLに変換するためのPerlスクリプト (Markdown.pl) がリリースされた。
https://daringfireball.net/projects/markdown/

Markdown の人気が高まるにつれて、追加機能が実装され、さまざまな方言ができた。 

そこで、Markdown の標準的で明確な構文仕様を作るため John MacFarlane, Martin Woodward, Jeff Atwood らによって CommonMark と呼ばれるプロジェクトが始まった。 

> [!NOTE]
> 当初は Standard Markdown という名前だったが、John Gruber に反対され、CommonMark になった。[^StandardMarkdown]

現在は GitHub や Stack Overflow などの多くのサイトが CommonMark を採用している。
https://commonmark.org/

GitHub では、CommonMark を拡張した GitHub Flavored Markdown (GFM) といくつかの独自の書き込み機能が組み合わされている。[^GitHub上での執筆]
https://github.github.com/gfm/

## Markdown の書き方
Markdown の基本的な書き方を説明する。
CommonMark に含まれない仕様は (extension) として示す。

### 見出し (Headings)
行をハッシュ#とスペースで始めるとヘッダーになる。
#の数が多いほどヘッダーは小さくなる。

```
# Heading 1
## Heading 2
### Heading 3
```

階層構造が壊れるため表示結果は省略する

これが書かれているところまでの階層構造としては、「Markdown」は `# Markdown` 、「Markdownの書き方」は `## Markdown の書き方` 、「見出し (Headings)」は `### 見出し (Headings)` となっている。

### 段落、改行 (Paragraphs, Line Break)
間に1行以上の空白行があると段落になる。
改行するには、行末にバックスラッシュ \\ または２つのスペースを追加する。

```
This is the first
paragraph.

This is the second
paragraph.

This is a\
line break.
```
This is the first
paragraph.

This is the second
paragraph.

This is a\
line break.

### 強調 (Emphasis)
太字または斜体にするには、アスタリスク\*またはアンダースコア\_で囲む。

```
*Italics*  
**Bold**  
```  
*Italics*  
**Bold**  

### 取り消し線 (Strikethrough) (extension)
GFMには取り消し線拡張があり、1つまたは2つのチルダ~で囲む。
3つ以上のチルダでは取り消し線は作成されない。

```
~~Hi~~ Hello, ~there~ world!  
This will ~~~not~~~ strike.
```
~~Hi~~ Hello, ~there~ world!  
This will ~~~not~~~ strike.

> [!NOTE]  
> VScodeのMarkdown Previewでは、1つのチルダだと取り消し線が表示されず、3つ以上のチルダだと外側2つを認識して中の~を残して取り消し線が表示される。(2025年5月現在)


### バックスラッシュエスケケープ (Backslash Escapes)
任意の ASCII 句読点文字はバックスラッシュでエスケープできる。
エスケープされた文字は通常の文字として扱われる。

```
*emphasized*

\*not emphasized\*
```
*emphasized*

\*not emphasized\*


### リスト (Lists)
順序なしリストでは、リストマーカーとしてアスタリスク*、プラス+、またはハイフン-を使用する。

順序付きリストでは、数字の後にピリオド.または右括弧)を使用する。

```
* Apples
* Oranges
* Pears

1. First
2. Second
3. Third
```
* Apples
* Oranges
* Pears

1. First
2. Second
3. Third


### リンク (Links)
リンクはテキスト内にインラインで配置することも、参照としてテキストの下部に配置することもできる。

角括弧[]でリンクテキストを囲み、インラインリンクの場合はリンクURLを丸括弧()で囲む。

```
[CommonMark](https://commonmark.org/)

[Markdown][]

[Markdown - wikipedia][Markdown-Wikipedia]


[Markdown]: https://daringfireball.net/projects/markdown/ "optional title"

[Markdown-Wikipedia]: https://en.wikipedia.org/wiki/Markdown
```
[CommonMark](https://commonmark.org/)

[Markdown][]

[Markdown - wikipedia][Markdown-Wikipedia]


[Markdown]: https://daringfireball.net/projects/markdown/ "optional title"

[Markdown-Wikipedia]: https://en.wikipedia.org/wiki/Markdown


### 画像 (Images)
画像を表示するには、感嘆符!の次に角括弧[]で代替テキスト囲み、インラインリンクの場合は画像のURLを丸括弧()で囲む。

```
![markdown-mark](/assets/blog/markdown/markdown-mark.png)

![markdown-mark-solid][]


[markdown-mark-solid]: /assets/blog/markdown/markdown-mark-solid.png
```
![markdown-mark](/assets/blog/markdown/markdown-mark.png)

![markdown-mark-solid][]


[markdown-mark-solid]: /assets/blog/markdown/markdown-mark-solid.png

### コード (Code)
インラインコードを作成するには、バッククォートで囲む。

コードブロックを作成するには、各行を4スペース分インデントするか、コードブロックの上下の行に3つのバッククォート```を配置する。

    Inline `code`

        indent 4 spaces

    ```
    Or use 3 backticks
    ```

Inline `code`

    indent 4 spaces

```
Or use 3 backticks
```


### シンタックスハイライト (Syntax Highlighting) (extension)
GFM仕様には書かれていないが、GitHubでは、コードブロックの最初の3つのバッククォートの後に言語名を指定することで、シンタックスハイライトができる。

    ```python
    print("Hello World")
    ```
```python
print("Hello World")
```


### 引用ブロック (Blockquotes)
ブロック引用を作成するには、行の先頭に>を付ける。(>の後にスペースは入れても入れなくても良い)

ブロック引用はネストすることができ、他の書式を含めることもできる。

```
> This is the first
> paragraph.
>
> This is a\
> line break.
>
> > Nested line
>
> Last line
```
> This is the first
> paragraph.
>
> This is a\
> line break.
>
> > Nested line
>
> Last line


### 表 (table) (extension)
GFM には表拡張があり、ヘッダー行、区切り行、データ行で構成される。各行のセルはパイプ|で区切る。

```
| Left align | Center align | Right align |
| :--------- | :----------: | ----------: |
| left       |    right     |      center |
| aligned    |   aligned    |     aligned |
```

| Left align | Center align | Right align |
| :--------- | :----------: | ----------: |
| left       |    right     |      center |
| aligned    |   aligned    |     aligned |


### 数式 (mathematical expression) (extension)
GFM仕様には書かれていないが、GitHubのMarkdownでは、次の様にして数式を表示できる。

```
math inline:
$\sqrt{3x-1}+(1+x)^2$

math block: 
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$
```

math inline:
$\sqrt{3x-1}+(1+x)^2$

math block: 
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

### Mermaid diagrams (extension)
GFM仕様には書かれていないが、GitHubのMarkdownでは、次の様にしてマーメイドダイアグラムを表示できる。

    ```mermaid
    graph TD;
        A-->B;
        A-->C;
        B-->D;
        C-->D;
    ```
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

### 脚注 (Footnotes) (extension)
GFM仕様には書かれていないが、GitHubのMarkdownでは、次の様にして脚注を表示できる。

```
Here is a simple footnote[^SimpleFootnote].

A footnote can also have multiple lines[^MultilineFootnote].

[^SimpleFootnote]: My reference.
[^MultilineFootnote]: To add line breaks within a footnote, prefix new lines with 2 spaces.  
  This is a second line.
```
Here is a simple footnote[^SimpleFootnote].

A footnote can also have multiple lines[^MultilineFootnote].

[^SimpleFootnote]: My reference.
[^MultilineFootnote]: To add line breaks within a footnote, prefix new lines with 2 spaces.
  This is a second line.


### 生のHTML (Raw HTML)
<>で囲まれたHTMLタグは、生のHTMLとして解析され、HTMLに変換する際もそのまま出力される。

### コメント (comments) (HTML)
```
<!-- Comment -->
```
<!-- Comment -->

> [!NOTE]
> 出力HTMLにも含めたくない場合は、参照スタイルのリンクを利用して、コメントのように扱うことができる。
>```
> [comment]: <> (This is a comment, it will not be included)
>```
> [comment]: <> (This is a comment, it will not be included)


### 折りたたみセクション (collapsed section) (HTML)

    <details>
    <summary> default close </summary>

    ### header

    ```
    code block
    ```

    </details>


    <details open>
    <summary> default open </summary>

    text within a collapsed section.

    </details>

<details>
<summary> default close </summary>

### header

```
code block
```

</details>


<details open>
<summary> default open </summary>

text within a collapsed section.

</details>


### alert (Alerats) (extension)
GFM仕様には書かれていないが、GitHubのMarkdownでは、次の様にしてアラートを表示できる。

```
> [!NOTE]  
> Useful information that users should know, even when skimming content.

> [!TIP]  
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]  
> Key information users need to know to achieve their goal.

> [!WARNING]  
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]  
> Advises about risks or negative outcomes of certain actions.
```
> [!NOTE]  
> Useful information that users should know, even when skimming content.

> [!TIP]  
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]  
> Key information users need to know to achieve their goal.

> [!WARNING]  
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]  
> Advises about risks or negative outcomes of certain actions.

### オートリンク (Autolinks)

CommonMark では<と>でURLを囲むことでURLがリンクラベルになる。

```
<https://commonmark.org/>
```
<https://commonmark.org/>


### オートリンク (Autolinks) (extension)

GFM では www. や https:// で始まっていれば、<>で囲まなくてもオートリンクとなる。

```
https://daringfireball.net/projects/markdown/ "optional title"
```
https://daringfireball.net/projects/markdown/



[^StandardMarkdown]: Jeff Atwood, "Standard Markdown is now Common Markdown", CODING HORROR, Sep. 2014,
https://blog.codinghorror.com/standard-markdown-is-now-common-markdown/

[^GitHub上での執筆]: "GitHub 上での執筆とフォーマットについて", GitHub Docs, 2025年5月閲覧, 
https://docs.github.com/ja/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github

