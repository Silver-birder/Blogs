# Links
https://silverbirder180.hatenablog.com/entry/2019/07/20/151731

# Title
【増枠】Frontend de KANPAI! #7 - Going on 令和 - 2019年7月19日参加レポート

# Contents
今回はDeNAさん主催のFrontendのイベントに参加してきましたので、
報告しようと思います。
[https://frokan.connpass.com/event/135584/:embed:cite]
[https://twitter.com/hashtag/frokan:embed:cite]

<figure class="figure-image figure-image-fotolife" title="frontend de kanpai">[f:id:silverbirder180:20190720095423j:plain]<figcaption>frontend de kanpai
</figcaption></figure>
<figure class="figure-image figure-image-fotolife" title="frontend de kanpai tech board">[f:id:silverbirder180:20190720095451j:plain]<figcaption>frontend de kanpai tech board</figcaption></figure>
firebaseの勢いがすごい。あとnowも多少人気で、now信者の私とっては嬉しい 。
<figure class="figure-image figure-image-fotolife" title="frontend de kanpai novelty">[f:id:silverbirder180:20190720095654j:plain]<figcaption>frontend de kanpai novelty</figcaption></figure> 

※ [https://twitter.com/DeNACreators/status/1152199891860389888]  
※ [https://twitter.com/antidotech/status/1152154690617872384]  
※ [https://twitter.com/wanami3103/status/1152202843618603008]  

[:contents]

# イベント概要
> 「Frontend de KANPAI!」（以下、FROKAN）は、フロントエンドエンジニアやフロントエンドに興味がある人が集い、ドリンク片手にゆるく交流・技術交換ができるコミュニティを目指しています。

※ [https://frokan.connpass.com/event/135584/]

特徴的だったのが立食形式という点です。
会場には多少の椅子が用意されているものの、ほとんどの人が立ってドリンクを持ちながら、登壇者のお話を聞いていました。

座っていると私はあんまり他の参加者とコミュニケーションしない人です。
椅子があると、その椅子が自身のテリトリーになってしまって閉じこもってしまう気持ちがあります。
しかし、立っているとその縛りがないので、楽にコミュニケーションを取れた感じがありました。
照明が暗かったというところもあると思います。ちなみに、お酒は一切飲んでないです。（笑）

ただ、翌日は少しつらかったです...。
[https://twitter.com/silver_birder/status/1152348180643627008:embed]

普段は、メモをがっつり書いてtwitterに投稿している私ですが、
今回は一切そのようなことをしていません。したがって、ほぼ記憶ベースでイベント内容を報告します。ご了承ください。
誤りありましたら、ご指摘下さい。

# 印象に残ったお話
## ReactとWebComponentsでVanillaな開発
### 日本経済新聞社 宮本 将 さん
WebComponentsに興味がある私は、この発表は気になっていました。
[https://twitter.com/silver_birder/status/1149648900627693572:embed]

内容をざっくり説明すると「CustomElementsをプロダクトとして使っていたけど、つらみがあったのでtypescriptで縛るようにしたよ」
というものでした。CustomElementsはWeb標準の技術ですが、reactやvueのようなpropによる型縛りがありません。
すべて文字列として表現するため、バリデーションチェックがつらいというお話が印象的でした。
そこで、react(JSX) + typescriptを駆使してCustomElementsをWrapすることで上記問題を解決されたそうです。

実際に導入したことによる「つらみ」というものは、プロダクト導入検討している私にとってはありがたいお話でした。
  
そもそも、なぜCustomElementsを導入したのかというお話もありました。
日経さんではWebApplicationというよりStaticなWebSiteに近いプロダクトだそうです。
そのため、reactやvueといったフレームワークは必要以上な機能が多いため却下し、
VanillaなJSでCustomElementsを進めて行こうという経緯があるそうです。
プロダクトの特徴に応じてコンポーネント選択すべきね。

※ CustomElementsっていろんなフレームワークで対応しているんですね。
[https://custom-elements-everywhere.com/:embed:cite]

## 実録フグ料理
### 株式会社ディー・エヌ・エー Takepepe さん
当初、「お、ネタ枠か？」と思っていたのですが、
予想以上に面白いお話でした。

Project Fuguというものがあります。
[https://www.heise.de/developer/artikel/Google-Projekt-Fugu-Die-Macht-des-Kugelfisches-4255636.html:embed:cite]

> Unter dem Codenamen Fugu plant Google die Einführung zahlreicher Webschnittstellen in seinem Webbrowser Chrome, welche die Lücke zwischen Progressive Web Apps und ihren nativen Gegenstücken schließen wollen.

Google翻訳を通すと

> コードネームFuguの下、GoogleはChromeウェブブラウザで数多くのウェブインターフェースを立ち上げることを計画している。これはProgressiveウェブアプリと彼らのネイティブの対応物との間のギャップを埋めるであろう。

つまりChromeウェブブラウザからネイティブな部分を操作できることを目的としています。
今回Takepepeさんが紹介していたのはShape Detection APIです。
バーコードやテキスト、そして顔を形状検出するデモの発表がありました。
どれもサクッと簡単に動作していましたが、まだ実験的な機能なため安定しない部分もあるそうです。

次の画像は顔検出した箇所にモザイクを入れるデモです。これは笑いました。
<figure class="figure-image figure-image-fotolife" title="Shape Detection API Demo">[f:id:silverbirder180:20190720110709j:plain]<figcaption>Shape Detection API Demo</figcaption></figure>
※ [https://twitter.com/antidotech/status/1152180161413931008]

ちなみに、Fuguという名前の由来は、
「ネイティブな部分を操作することは色々な事ができるようになり夢が広がるが、使い所を誤ると危険なもの」という話から
フグの「調理の仕方によって美味しい料理になるが、毒があるので調理の仕方を誤ると危険なもの」という自戒の念を込めてFuguになりました。
ネイティブな部分を操作できるということは、センシティブな情報を取得できてしまうという面があります。
そこが使い方によっては「毒」になるものですね。

## 新しいAPI
### 株式会社ディー・エヌ・エー feb19 さん
[https://speakerdeck.com/feb19/xin-sii-api:embed:cite]

いきなりポエムを語り始めたfeb19さん。
「DeNAの人たちは、みんなこうなのか？」と面白く見ていました。
この発表では、HTML,CSS,JSのAPIが紹介されていました。
LazyLoadという有名なものから、少しマニアックなinverted-colorまで幅広く、よくこんなもの知ってるんだなと驚きました。

# 最後に
フロントエンドのイベントは、今回初めてかもしれません。 参加者の多くは、どちらかというと「陽の者」が多く、ノリが楽しい人たちばかりでした。 参加者の方と技術的な話をしたのですが、やはりreact, vue, augularのワードが多かった印象です。なんだか聞き飽きた印象もありますが、それだけ需要があるのだなと改めて思いました。