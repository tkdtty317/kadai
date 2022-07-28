IEに対応するために使えなかったCSSプロパティ。
CSSだけで、動作ができるものはなるべくCSSを使う事で
JSよりも処理の効率も良くなり、作業の工数も減るので積極的に使っていきたいCSSを取り上げていきたいと思います。

filterプロパティ
ボカシや色調整などの効果をCSSで表現できる機能です。
アニメーションにつかえるので、画像へのマウスオーバー時のエフェクトとして使用できるので、
少ない記述で幅広い効果が得られるので覚えておきたいプロパティ。

種類は全部で10種類

・ぼかし 画像のぼかしの具合を指定する。単位はpx等, %はしようできない。
filter: blur(2px);

・明度 画像の明るさを指定。
100％が基準となっていて、100%から大きくする明るくなり、小さくすると暗くなります。
filter: brightness(150%);

・コントラスト 画像のコントラストを指定します。
100％が基準となっていて、100%から大きくするコントラストが上がり、小さくするとコントラスト下がります。
filter: contrast(120%);

・ドロップシャドウ 画像に影をつける事ができる。
引数は4つあり、「X軸方向の位置」「Y軸方向の位置」「ぼかしの大きさ」「影の色」となります。
最初の2つは必須。
filter: drop-shadow(3px 3px 5px rgba(0,0,0,0.7));

・グレースケール 画像にグレースケールをかける事ができる。
0%を基準に100%で完全にグレースケールされた状態になります。
filter: grayscale(80%);

・色相環 色相を変更することができます。
値は色相環の回転を指定します。基準値は0degです。180degで色相が反転して、360degで元の色相になります。
filter: hue-rotate(45deg);

・階調の反転 階調をどの程度反転させるかを指定します。
0%を基準とし、100%で完全に階調が反転します。
filter: invert(100%);

・不透明度 画像の不透明度を指定します。
100%が元の画像、0%で完全に透明になります。背景色まで見えてしまうので、使い方には注意。
filter: opacity(30%);

・彩度 画像の彩度を指定します。
100%を基準として、100%より大きくすると鮮やかになります。100%より小さくすると彩度が下がり暗い色になります。0で無彩色になります。
filter: saturate(160%);

・セピア 画像をセピア調にします。
0%を基準とし、100%が最大値でセピア調になります。
filter: sepia(80%);

複数のfilterを指定する際は半角スペースを空けてフィルターを並べて記述します。いくつでも可能です。
filter: contrast(50%) blur(3px);


https://caniuse.com/?search=filter

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="VwXeama" data-user="tkd_j-line" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/tkd_j-line/pen/VwXeama">
  filterについて</a> by TKDTTY (<a href="https://codepen.io/tkd_j-line">@tkd_j-line</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>