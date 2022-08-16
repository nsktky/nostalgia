# nostalgia README
サイトURL  
https://nsktky.github.io/nostalgia/

## ポートフォリオサイトの概要
nostalgiaは、私が制作したCreative Codingの作品を紹介するサイトです。

## 使用技術
* vue 2.7.7
* vue-p5 0.8.4
* vue-router 3.5.1
* vuetify 2.6.0

## 当サイトの作成理由
私は2021年12月から毎日Creative Codingを行い、作品を制作しています。  
Creative Codingとは、プログラムを用いて作品(Generative Art)を制作する活動です。  
主にJavaScriptのライブラリであるp5.jsを用いて作品を制作しており、現在までに約260作品を制作しました。  
これらの作品を紹介する場を持ちたいと思い、当サイトを作成しました。  

## コンテンツ一覧
<dl>
  <dt>HOME</dt>
  <dd>Generative Artを全面に表示。サイト名のnostalgiaをテーマに作成。</dd>
  <dt>ART</dt>
  <dd>作成したGenerative Artの一部を展示。</dd>
  <dt>PROFILE</dt>
  <dd>プロフィールを掲載。主にTwitterにて作品を公開しているため、タイムラインを埋め込んだ。</dd>
  <dt>CONTACT</dt>
  <dd>Google Formを埋め込み、コンタクトフォームを作成。</dd>
</dl>

## 技術的ポイント
* vueを使用しSPAとして作成
* vuetifyを用いてサイト全体のデザインを統一。レスポンシブ対応
* vue-routerを使用しルーティングを実現
* メニューバーは常に表示させるよう、App.vueに直接コンポーネントを指定
* HOMEにはvue-p5を使用しGenerative Artを表示
* vue-p5内でHTML側のcanvasタグを作成。canvas要素としてアニメーションを描画

## 改善点
* モバイル環境での描画が重くなるため、処理が軽くなるようコードを書き換えたい
* 独自フォームを作成し、サイトデザインを統一したい
* Generative Artを複数実行し、動く展示会のようにしたい