フクロウセレクタとは全称セレクタ*を連ねて、連続する要素の場合にスタイルが当たるようにするものです
* + * このように見た目がフクロウの顔に見えるからフクロウセレクタという事みたいです。
個々の要素ではなく、関係性にスタイルを設定する。
隣接兄弟結合子(+)を使用。
繰り返して要素が並ぶ際、疑似クラス(nth-childとか)を使うよりもシンプルに書けるので記述量が減る。
親要素とちゃんと組み合わせて

* + * {
   /* ここにスタイルを記述します */
}

.box + .box {
    margin-top: 20px
}

クラス間どうしの関係性に要素をあてるような使い方でも、動作が予想しやすいのでいいと思う。

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="NWYaQLx" data-user="tkd_j-line" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/tkd_j-line/pen/NWYaQLx">
  関係性にmarginを設定する。</a> by TKDTTY (<a href="https://codepen.io/tkd_j-line">@tkd_j-line</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>