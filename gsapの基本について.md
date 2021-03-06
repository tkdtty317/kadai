## GSAP の基本設定について
JSのアニメーションライブラリ、「GSAP」について。
公式サイト：https://greensock.com/docs/

### 導入方法

- cdnを読み込む
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.1/gsap.min.js"></script>

- 公式サイトからダウンロード、npm,githubからダウンロードして設置等
コアプラグイン
gsap.min.js

//後にプラグインを読み込む際は順番に注意。

### Tween
tweenという単位で動作を作っていきます。

##### Tweenの4つ種類
- to //ゴールの状態を指定。　現在の状態から、指定した状態へとアニメーションします。

    gsap.to(
        アニメーションさせる要素を指定(target),

        // ゴールの状態
        {
            プロバティ名: 値,
            プロバティ名: 値,
        },
        発火からアニメーション開始までの時間(秒で指定) 。指定しない場合は0秒
    )

- from  //開始の状態を指定。　指定した状態から、現在の状態へとアニメーションします。

    gsap.from(
        アニメーションさせる要素を指定(target),

        //開始される状態
        {
            プロバティ名: 値,
            プロバティ名: 値,
        }
    );

- fromTo //開始の状態と、ゴールの状態を指定してアニメーションします。durationはゴール状態の方に指定します。

    gsap.fromTo(
        アニメーションさせる要素を指定(target),

        //開始される状態
        {
            プロバティ名: 値,
            プロバティ名: 値,
        },

        //完了される状態
        {
            プロパティ名:値,
            プロパティ名:値,
        }
    );

- set //状態を即変化させます。to()やform()の前に使うことが殆どだと思います。(CSSを使わずに、GSAP内で指定できます)

    gsap.set(
        ターゲットの要素

        //アニメーションさせない静止状態を指定する。
        {

        }
    );

##### gsap のプロパティ例
x: x軸方向に移動(単位はpx) ※translateX()のショートカット
y: y軸方向に移動(単位はpx) ※translateX()のショートカット
opacity: 透過(0 ～ 1)
scale: 大きさ(単位は倍)
backgroundColor: 背景色 
rotation: 回転
skew: 傾斜変形

trasformOrigin起点の位置を指定。デフォルト："50% 50%"(要素の中央)

指定できるアニメーション
https://greensock.com/docs/v3/GSAP/CorePlugins/CSSPlugin

##### gsap　の特殊なプロパティ例
duration: 値,　// アニメーションしている時間　デフォルト: 0.5
delay: 値, //アニメーションを開始するまでの遅延時間

onStart: 動作 ,  //アニメーションが開始するときに呼び出されるコールバックです。
    - onStartParamas: ["パラメータの値"] ,
onComplete: 動作　//アニメーションが終了するときに呼び出されるコールバックです。
    - onCompleteParamas: ["パラメータの値"] ,
onRepeat: 動作 //アニメーションが新しい反復サイクル(repeat)に入るたびに呼び出されるコールバックです。
    - onRepeatParams:["パラメータの値1","パラメータの値2"]

ease: イージングの値,  //https://greensock.com/docs/v2/Easing
stagger: 秒数, //各ターゲット/エレメントのアニメーションの開始時間をずらします。
reversed: true //逆再生
yoyo: true //

##### アニメーションの制御
to()、from()、fromTo()メソッドはすべてTweenインスタンスを返すので、
変数として保存しておけば、非常に簡単に制御することができます。

const tween = gsap.to(".target", {duration: 1, x: 100});

tween.play();    //アニメーションを再生
tween.pause();   //アニメーションを一旦停止
tween.resume();  //アニメーションの一旦停止から再アニメーション
tween.reverse(); //アニメーションの逆再生
tween.restart()  //アニメーションを最初から再生

#### Timeline
Tweenを連結して、長い(複雑な)アニメーションを作れます。

タイムラインを作成し、.to()を連結してアニメーションを構成します。
初期状態を指定したい場合は、.set()を最初に指定します(timelineの外で指定することも可能)

const tl = gsap.timeline();

tl.to (
    アニメーションさせる要素を指定(target),

    {
        プロパティ: 値,
        プロパティ: 値,
    },
    発火からアニメーション開始までの時間
)
// .toで繋げて記述
.to(
    アニメーションさせる要素を指定(target),

    {
        プロパティ: 値,
        プロパティ: 値,
    },
    発火からアニメーション開始までの時間
)

###### 各Tweenの開始時間の指定
数値以外の指定も可能

+=数値　前のTween終了後に指定時間後　アニメーションスタート
-=数値  前のTween終了前に指定時間前  アニメーションスタート
>数値   1つ前ののTweenの終了時の指定した数値秒後(マイナスも指定可能、数値省略時はデフォルトの0.5になる)
<数値　1つ前のTweenの開始時の指定した数値秒後(マイナスも指定可能、数値省略時はデフォルトの0.5になる)
ラベル	他のラベル名+=数値、他のラベル名-=数値も可能

※　数値ではなく文字列なのでクォーテーションで囲むのを忘れないように。

// 動作のタイミングはコチラを確認　https://greensock.com/position-parameter

###### ラベル
.addlabeLabel('ラベル名', 開始される秒数)
ラベルを使用してタイムライン上の特定の位置をラベリングできます。
ラベルの位置を基準にアニメーションの動作タイミングを設定できます。

###### タイムラインの特殊プロパティ
- repeat: アニメーションを何回繰り返すか。
- repeatDelay: リピート間の時間（秒）を指定します。
- yoyo: trueの場合、繰り返し再生するたびに、前方・後方交互に再生されます。
- delay: タイムラインを開始するまでの時間（秒）を指定します。
- onComplete: タイムラインの再生が終了したときに呼び出される関数です。


##### stragger 
どの順番でアニメーションをしていくか指定できます。

  　from: start … 頭から始める
        　center … 中央から始める
        　edges … 両端から始める
        　random … ランダムに始める
        　end … 最後から始める

    https://greensock.com/docs/v3/Staggers




### ScrollTrigger
スクロールを上下してもらうとアニメーションが開始されたり、位置がリセットされたりします。

#### 導入
cdn
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.1/ScrollTrigger.min.js"></script>

### 記述方法

gsap.to(アニメーションさせる要素, {
    プロパティ: 値

    scrollTrigger: {
        trigger: '',//アニメーションが始まるトリガーとなる要素
        start: 'top center', //アニメーションが始まる位置　'トリガー要素の基点　モニターの基点'
        markers: true, //アニメーションの開始位置、終了位置を目視確認
    }
});

//gsap.set 初期状態を設定
gsap.set('アニメーションさせる要素',{autoAlpha: 0}); //autoAlpha:0を指定すると自動でopacity: 0;とvisibility: hidden;が指定されます。

//gsap.to
gsap.to('.js-demo-section', { 
  autoAlpha: 1, //opacity: 1;とvisibility：visible;がつく
  scrollTrigger: {
    trigger: '.js-trigger',
    start: 'top center'
  }
});

// 初期状態から完了状態までまとめて
gsap.fromTo('.js-demo-section', { 
  autoAlpha: 0, //ここで初期状態を設定
  },
  {
  autoAlpha: 1, //ここでアニメーションさせたい内容を書く
    scrollTrigger: { //スクロールトリガーはこちらに記述
      trigger: '.js-trigger',
      start: 'top center'
    }
  }
});

##### アニメーションのスピードを指定 (ease)






