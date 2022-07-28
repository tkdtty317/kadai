IEに対応するために使えなかったCSSプロパティ。
CSSだけで、動作ができるものはなるべくCSSを使う事で
JSよりも処理の効率も良くなり、作業の工数も減るので積極的に使っていきたいCSSを取り上げていきたいと思います。


flexboxの余白指定

display: flex;にgap要素が使用できるようになりました。
要素と要素の間の余白(縦・横)を指定するプロパティです。
    gap: 値;

    gap: 縦の値 横の値
    row-gap: 縦の値;
    column-gap: 横の値;

    flex-boxでの指定が可能。要素が横並びではない場合は適用されず。
    要素間のみに指定できるので、外側などに必要のない箇所には余白を発生させない。想定外のカラム落ちなどで予想外の余白みたいな事はなくなります。

- gapで実装するメリット
・親要素で指定することで、子要素の余白管理ができる。記述もシンプル。
・子要素(flex-item)に対して、marginの打消し等の処理が要らない。nth,not系の処理がいらない。

- gapで実装するデメリット
・モダンプラウザには対応しているが、safari少し前のバージョンでは可否が異なる為、レイアウト崩れる原因にもなるかも。
https://caniuse.com/?search=gap

・まとめて指定するため、デザインに余白の統一性が無い場合は、子要素(flex-item)に対して微調整が必要。

今後間違いなく使用する。ただ、デザインについては考えて使用すべき。

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="rNdaMRN" data-user="tkd_j-line" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/tkd_j-line/pen/rNdaMRN">
  gap プロパティについて</a> by TKDTTY (<a href="https://codepen.io/tkd_j-line">@tkd_j-line</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>