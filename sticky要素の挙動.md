IEに対応するために使えなかったCSSプロパティ。
CSSだけで、動作ができるものはなるべくCSSを使う事で
JSよりも処理の効率も良くなり、作業の工数も減るので積極的に使っていきたいCSSを取り上げていきたいと思います。

position: stickyについて

- position: sticky
    スクロールした際に、親要素を基点にボックス内の指定した位置に固定して表示できる。
    用語、
    スティッキーアイテム： position: sticky;を設定した要素のこと。
    スティッキーコンテナ： position: sticky;を設定した要素の親要素こと。

    position: absolute, fixedと違って高さはなくならない。
    スティッキーコンテナにposition: relative;を設置しなくて大丈夫。
    スティッキーアイテムよりもスティッキーコンテナに高さがあれば、position: stickyを設定するだけで動作する。
    top: 値;left～　等を指定して、スティッキーコンテナを基点に値の位置で固定された状態で表示される。
    z-indexも効く。
    positin: relative;に似た扱いという認識でも大丈夫そう。
    スティッキーコンテナがdisplay:flex;を設定して天地左右中央にスティッキーアイテムを設置した場合(display: flex)も適用される。スクロールした際に画面の表示位置と設定されたtop:値の位置で固定されて表示される。

    https://caniuse.com/?search=sticky

あわせてinset: 0;も紹介。
天地左右中央揃えの記述。
top,bottom,right,left,すべての辺に適用される値をまとめて0にします。
従来の書き方より少なく書けるので、便利。

position: absolute; , position: fixed;に設定すれば天地左右中央揃いが簡単に。
inset: 0;がIE対応していなかった。
top,bottom,right,left,すべての辺に適用される値をまとめて0にします。
従来の書き方より少なく書ける。
https://caniuse.com/?search=inset


<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="RwMNaQY" data-user="tkd_j-line" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/tkd_j-line/pen/RwMNaQY">
  position: sticky の挙動と inset: 0  ; の挙動</a> by TKDTTY (<a href="https://codepen.io/tkd_j-line">@tkd_j-line</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>