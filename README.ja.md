# MixedShadowSample
Read this in other languages: [English](README.ja.md), 日本語 <br />


## オリジナルのソースコード
  https://github.com/Unity-Technologies/ScriptableRenderPipeline <br/>
  LWRP 1.1.8-previewより派生しました

## イメージ図

### 改造した RenderPipeline
<img src="docs/img/MixShadow.png" width="480px">

※わかりやすくするため、青い影がリアルタイムで描いているshadowでBakeした影は黒です。

### 通常のLWRP
通常のLWRPだとこのように描画されてしまいます。<br />
背景オブジェクトから、地面にリアルタイムの影を落としてしまっています。

<img src="docs/img/NG_Pattern1.png" width="320px">



## RenderPassの流れについて

1.始めにキャラクターだけのShadowMapを生成します<br />
<img src="docs/img/1st_step.png" width="480px" /> <br />

2.キャラクターだけのShadowMapを適応して背景を描きます<br />
<img src="docs/img/2nd_step.png" width="480px" /> <br />

3.キャラクターだけのShadowMapに背景オブジェクトも描き足します<br />
<img src="docs/img/3rd_step.png" width="480px" /> <br />

4.最後にキャラクターを描画します<br />
<img src="docs/img/4th_step.png" width="480px" /> <br />



## これを行う理由について
・キャラクターの周りだけをリアルタイムで処理するようにする事で影の描画負荷を抑えます<br/>
・近距離のみで済むのでShadowの解像度を抑えられます<br/>
・背景の影はBakeしたものなので高品質です。
