# Links
https://silverbirder180.hatenablog.com/entry/2019/07/27/110811

# Title
Cloud Native Days Tokyo 2019 -2019年7月22-23日参加レポート

# Contents
<figure class="figure-image figure-image-fotolife" title="cloud native days tokyo 2019">[f:id:silverbirder180:20190722232033p:plain]<figcaption>cloud native days tokyo 2019</figcaption></figure>

今回、東京が開催されましたCloud Native Days Tokyo 2019に2日間とも参加してきましたので、報告しようと思います。
セッション毎の報告というより、全体を通した感想を話そうかなと思います。

[:contents]

[https://cloudnativedays.jp/cndt2019/:embed:cite]

リンクをまとめています。    
[https://qiita.com/zaki-lknr/items/1c26bb713aef9645f5e6:embed:cite]

# CNCFの利用率
一日目のKeynoteで印象的だった内容です。 
発表者は、OSDT実行委員長である長谷川さんです。  

来場者アンケート1354人から聞いた「クラウドネイティブ技術を活用フェーズについて」の紹介がありました。
既に本番環境に適用している人は、なんと<b>46%</b>という驚きの結果でした。また、開発環境に至っては、<b>63%</b>ということでした。  
このイベントに参加している時点である程度フィルターはかかっていると思いますが、それでも大きな割合だと感じました。

次の図では、CNCFプロジェクトの180日間におけるCommit数をグラフ化したものです。
生みの親であるGoogleが1位でindependent(個人)が2番目、日本企業Fujitsuが6位です。熱意が伝わってきますね。  　
<figure class="figure-image figure-image-fotolife" title="https://www.stackalytics.com/cncf?date=180">[f:id:silverbirder180:20190724211327p:plain]<figcaption>https://www.stackalytics.com/cncf?date=180</figcaption></figure>
※ 2019/07/24時点

ただ、CNCFのメンバーとして日本企業は<b>17社</b>しかないそうで、まだまだこれからといったところでしょうか。
[https://landscape.cncf.io/format=members:embed:cite]

さらには、Kubernetesから認定された日本企業ではまだないみたいです。残念です。  
[https://kubernetes.io/partners/#kcsp:embed:cite]  

今後は、次のようなカンファレンスが海外でもあるみたいです。ぜひ参加してみたいと思います。  
[https://events.linuxfoundation.org/events/kubecon-cloudnativecon-europe-2019/:embed:cite]
[https://events.linuxfoundation.org/events/kubecon-cloudnativecon-north-america-2019/:embed:cite]

# CloudNativeとは？
> クラウドネイティブ技術は、パブリッククラウド、プライベートクラウド、ハイブリッドクラウドなどの近代的でダイナミックな環境において、スケーラブルなアプリケーションを構築および実行するための能力を組織にもたらします。 このアプローチの代表例に、コンテナ、サービスメッシュ、マイクロサービス、イミューダブルインフラストラクチャ、および宣言型APIがあります。

※ [https://github.com/cncf/toc/blob/master/DEFINITION.md#日本語版]

「スケーラブルなアプリケーションを構築および実行」が重要です。これを実現する手段の１つにKubernetesがあります。
「CloudNative = Kubernetes」ではなく、「CloudNative ∋　Kubernetes」という感じです。

ただ、最近ではKubernetesを違う観点で考える人が増えてきたそうです。
それが、二日目のKeynoteで発表された北山さんのスライドにあります。
[https://speakerdeck.com/shkitayama/change-the-game-change-the-world:embed:cite]

Kubernetesは「platformのためのplatform」と言われるようになりました。
これは、slide.No.9(Kubernetes is a platform)で見て分かる通りで、次のようなことがわかります。

* 運用管理者
  * Self-Healingによってスケールが簡単になる
* アプリケーション開発者
  * 簡単にデプロイすることができる

これらは、たしかに「プラットフォームから得られる価値」になりますが、
逆に次のような考慮が必要なってきます。

* 運用管理者
  * Self-Healingはどこまで信頼性を担保できるか
* アプリケーション開発者
  * ユーザー影響を最小限にするためには、どうればよいか

これらのような「プラットフォームを利用するコスト」が「プラットフォームから得られる価値」よりも大きくなってしまいがちになります。
そこで、Operator (CRD)という概念が最近ホットになっています。

# なぜCRDがホットなのか？
CRDという言葉は様々なセッションで取り上げらていました。
CRDとOperatorについては、下記をご参考下さい。
[https://silverbirder180.hatenablog.com/entry/2019/06/01/182255#CRD%E3%81%A8Operators:embed:cite]

Kubernetesを運用すると、既存のリソースだけでは物足りない所がでてくるそうです。
そういう部分が「プラットフォームを利用するコスト」を大きくしてしまいます。
そこで、オリジナルのカスタマイズしたリソースを独自に開発し、運用を自動化することを目的とした
CRD、Operatorが生まれました。
ただ、独自に1から作るよりも、下記のサイトから使った方が効率的なときもあります。
[https://operatorhub.io/:embed:cite]
けど、結局は困ったとき、ソースコードを読むことになるので、それぐらいの能力がないと、
運用を回せない気がします。

zlabのladicleさんの次のスライドがとてもわかりやすく、まとまっていました。
これは貴重な資料ですね。
[https://speakerdeck.com/ladicle/kuberneteswokuo-zhang-siteri-falseoperesiyonwozi-dong-hua-suru:embed:cite]

ちなみに、独自に1から作ったケースがサイバーエージェントの山本さんの発表で、次のスライドです。  
[https://speakerdeck.com/mayuyamamoto/kuberneteskuo-zhang-woli-yong-sitazi-zuo-autoscalerdeshi-xian-surusutoresuhurinayun-yong-falseshi-jie:embed:cite]

同じくサイバーエージェントの青山さんがライブコーディングされていたリポジトリが次のものになります。
[https://github.com/cloudnativejp/webserver-operator:embed:cite]

# Kubernetesは必要ですか？
Kubernetesを使うべきかの話が2日間でちらほらありました。
次のような議論もあります。
[https://www.atmarkit.co.jp/ait/articles/1907/23/news120.html:embed:cite]

CloudNativeなアプリケーション構築を目指す場合、どうしてもKubernetesを使う方向になりがちですよね。  
今回参加したセッションの多くの企業では、Kubernetesを採用するための検討が下記のような感じでした。

* プレインなKubernetesか、マネージドなKubernetesか
  * 大体はマネージドなKubernetesを使う。
  * かゆい所に手を伸ばすときになって、プレインなKubernetesを使う。
* Kubernetesのエンジニアは何人か。それは専属か
  * どこもKubernetesの知識を保有するエンジニアは少ない。
  * 数人程度で専任で進めることが多い。
* ノウハウを蓄積するために、スモールスタート

様々なセッションがあった中で、とても王道なステップを踏まれている企業がありました。それは、SoftbankPaymentServiceの鈴木さんの次のスライドです。  
[https://www.slideshare.net/JunyaSuzuki1/springpcf-cndt2019-osdt2019-keynote:embed:cite]
企業に適したCloudNative化だなと勉強になりました。  
特に「運用を回すコストを考慮すると、KubernetesではなくPaaSを使う」  というポイントが好きです。  

# Circuit Breaker
耳にタコができるぐらい、この単語を聞きました。
下記のサイトが参考になります。
[https://qiita.com/yasuabe2613/items/3bff44e662c922083264#circuit-breaker:embed:cite]
> 同期リクエストの先で一部のマイクロサービスに障害があると、クライアントやその先の「クライアントのクライアント」までブロッキングが波及することになりかねない。
この問題を、クライアントと実サービスの間に Circuit Breaker と呼ばれるプロキシを介在させて、実サービスの呼び出し失敗が一定基準を超えると、クライアントからのリクエストを即座にリジェクトさせて、ブロッキング連鎖を解消するパターン。

Kubernetesでアプリケーションを構築すると、分散システムの恩恵を受けるために、
アプリケーションをマイクロサービス化する流れになります。そのマイクロサービス化でよく踏む地雷が、
「後ろのAPIが死んだら、連鎖的に他サーバも死ぬ」という現象です。  
これを回避するために、上記のCircuit Breakerパターンを使う企業が多数いらっしゃいました。
本当にいろんなセッションで聞きました...。

# twelve factor app
次のWantedlyさんのスライドが、私の中では話題になりました。
[https://speakerdeck.com/potsbo/k8s-kubernetes-8-factors:embed:cite]

要は、「アプリケーションとしての設計の考え方(twelve factor app)を、インフラ部分でも適用してみた」という感じです。
どれも具体的なところまで説明されており、実際にKubernetesを構築する際に役に立つものだと思います。  

# 技術にフォーカスした発表
今回のイベントでは、何か1つの技術にフォーカスした発表が多くありました。
それぞれ私なりにまとめてみました。ご参考下さい。

## Chaos Engineering
[https://speakerdeck.com/mahito/cndt-osdt-2019-2g1:embed:cite]
## Docker
[https://www.slideshare.net/AkihiroSuda/cndt-docker:embed:cite]
## Envoy
[https://speakerdeck.com/taiki45/cloudnative-days-tokyo-2019-understanding-envoy:embed:cite]
## Logging
[https://speakerdeck.com/yosshi_/kubernetes-loggingru-men:embed:cite]
[https://speakerdeck.com/makocchi/cndt2019-kubernetes-audit-log-c4d4c5f6-6058-40f9-a5fc-abbb36073a1
## LinuxKernel
[https://speakerdeck.com/tenforward/cndt2019:embed:cite]
## Prometheus
[https://speakerdeck.com/tokibi/prometheus-setup-with-long-term-storage:embed:cite]
## Sandbox
[https://docs.google.com/presentation/d/1O9Q9E1hH6mBA5w8oDENnCYObZvij1-Dr_obvsY3X29k/edit:embed:cite]
## Scheduler
[https://speakerdeck.com/ytaka23/cloudnative-days-tokyo-2019:embed:cite]
## Spinnaker
[https://speakerdeck.com/sansanbuildersbox/introduction-to-deployment-patterns-with-spinnaker:embed:cite]9:embed:cite]
## Istio
[https://speakerdeck.com/dangossk/a-deep-dive-into-service-mesh-and-istio-cndt-2019:embed:cite]

# その他
サイバーエージェントさんより、エンジニアにとってとても嬉しいアイテムを頂きました。
[https://twitter.com/ca_adtechstudio/status/1152080444445167616:embed]

さっそく、キーボードにとりつけてみました。最高です！
<figure class="figure-image figure-image-fotolife" title="ergodox with k8s keycap (cyberAgent)">[f:id:silverbirder180:20190724202409j:plain]<figcaption>ergodox with k8s keycap (cyberAgent)</figcaption></figure>

こちらのサービスから作られたそうで、私も自前で何か作ってみようかなと思いました。
[http://www.wasdkeyboards.com/index.php/products/printed-keycap-singles/custom-art-cherry-mx-keycaps.html]

# 最後に
CloudNativeにどっぷり浸かった2日間でした。  
どの企業でもCloudNativeを導入したことによる「つらみ」や「価値」を共有して頂いたおかげで、これから導入する人たち（私を含む）にとっては、有意義な時間でした。  
全てのセッションを吸収できたわけではないですが、ここで記載したスライドだけでも理解を深めたいなと思います。

[https://cloudnativedays.jp/cndk2019/:embed:cite]
今度は大阪で開催されるそうです。これも絶対参加したいなと思います！

# 蛇足（参加するまでの経緯）
筆者はWebが大好きなエンジニアで、Kubernetesについては理解が浅い人間です。主にフロントエンドに注力しています。  
ただ、昨年のDeveloperBoost2018で、サイバーエージェントの青山さんのセッションをうけてKubernetesに興味を持ち始めました。
[https://codezine.jp/article/detail/11291:embed:cite]  
青山さんはKubernetesにとても詳しい方で、世代が近いせいか、私もこれぐらい夢中になれるものを見つけたいと感じるようになりました。  
私はWebに関わるものなら何でも好きで、Kubernetesも含まれます。そこで、青山さん著作の[Kubernetes完全ガイド](http://www.wasdkeyboards.com/index.php/products/printed-keycap-singles/custom-art-cherry-mx-keycaps.html)を全て実践することにしてみました。もちろん<b>お家Kubernetes</b>でです。
実際に触ってみると、スケールする簡単さに驚きました。ほぼコマンド一発でPodが複製されて、「え！？」とびっくりです。  
そこから、段々とハマっていき今回のイベントに参加することになりました。  