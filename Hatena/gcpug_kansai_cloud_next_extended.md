# Links
https://silverbirder180.hatenablog.com/entry/2019/05/22/001426

# Title
【大阪】GCPUG Kansai 〜 Cloud Next Extended ～ - 2019年5月14日 参加レポート

# Contents
<figure class="figure-image figure-image-fotolife" title="GCPUG Kansai Cloud Next Extended 案内板">[f:id:silverbirder180:20190521230529j:plain]<figcaption>GCPUG Kansai Cloud Next Extended 案内板</figcaption></figure>
[https://gcpug-osaka.connpass.com/event/128130/:embed:cite]
こちらの参加しましたので、ご報告します。

twitter
[https://twitter.com/hashtag/next19extended:embed:cite]

[:contents]

# 目的
> 2019/04/09 ～ 04/11 にサンフランシスコで開催された
Google Cloud Next '19 San Francisco で発表された
Google Cloud の 新サービスに関する解説や振り返りの内容がメインのイベントとなります！

# セッション紹介
## GCPUG Kansai 紹介

```text
GCPUG Osaka
GCPUG Kobe
GCPUG Kyoto
GCPUG Nara
GCPUG Shiga
GCPUG Wakayama
FJUG Osaka (firebase)
```

関西には、こんなにも多くGCPUGコミュニティがあるみたいです。すごい、いっぱい！
Osakaは、継続して参加しようと思います。GCP大好きですし。

## Cloud Next Recap 1
### 発表者
Ian Lewis(Google)

### 内容
GoogleでKubernetesの担当されているそうです。
また、Pyconや、connpassにも携わっているそうです。

#### Anthos
読み方は、アンソスと呼ぶそうです。難しい...。

特徴として、下記が挙げられるそうで...  
・アプリケーションをモダナイズ  
・ポリシーオートメーション  
・一貫したエクスペリエンス  

よーわからないので、ggってみた。
[https://www.publickey1.jp/blog/19/googleanthoskubernetesgoogle_cloud_next_19.html:embed:cite]

> コンテナ化したアプリケーションをオンプレミスとクラウドのどちらでも実行可能にする、ハイブリッドクラウドおよびマルチクラウドのためのプラットフォーム。

> オンプレミスを含むどのクラウド上にアプリケーションがデプロイされていても、Anthosの管理画面から統合管理可能。

なるほど、Anthosはマルチクラウドを実現するためのプラットフォームなのですね。
ふむふむ、わかりやすい。

また、IstioをベースとしてAnthosが作られたとも発表されていました。
Istioについては、[こちら](https://cloud.google.com/istio/?hl=ja)をご確認下さい。   
Istioの機能の特徴として下記があるそうです。
[https://twitter.com/nankouyuukichi/status/1128245474215858176?s=20:embed]

k8sでは、対象とするクラスタを管理します。規模が拡大するにつれ、
サービスが複雑になってくるケースがあります。その際Istioが、そのあたりを
良い感じに管理してくれると、理解しています。（ざっくり感）  
※ マルチクラスタは既に実現できていた(?)  

Anthosは、その対象範囲をクラウドだけでなく、オンプレ(GKE on Prem)も含めるようにしたと思います。

## CloudRun
これは、下記で一度試した経験があります。
[https://qiita.com/silverbirder/items/6981461a756a48f6e25d:embed:cite]

コンテナとしてdeployできるようになります。
正直、AppEngine, CloudFunction, CoundRunとデプロイサービスが増えてきて、
どれが何に良いのか分からなくなりそうです...。下記に、まとまっていました。
[https://docs.google.com/presentation/d/1DCJlrXQKWN63pAz9vtdVNFhMPHceyiKHK0IrFjcwOcU/edit#slide=id.g5693476139_0_155:embed:cite]

## CloudRun on GKE
こちらは、k8sにCloudRunをdeployできるみたいです。
詳しくは分かりません。

## Knative
[https://cloud.google.com/knative/?hl=ja:embed:cite]
> Knative は、オンプレミス、クラウド、サードパーティのデータセンターなど、場所を選ばず実行できるソース中心でコンテナベースの最新アプリケーションを構築する際には不可欠な一連のミドルウェア コンポーネントです。

んー、なんとなくわからなくないですが、他のサイトを見てみます。

[https://www.apps-gcp.com/knative-overview/:embed:cite]

> Knativeを使用するためには、Kubernetesがインストールされたクラスタを用意する必要がありますが、KnativeはKubernetesと同様にコンテナをオーケストレーションするためのものである、という点は変わりません。
> Knativeは、クラウドにおけるPaaSやFaaSのようなアーキテクチャを、Knativeがインストールされていれば(つまり、Kubernetesクラスタであれば)どこでも実現できるものです。

なるほど。要は、クラウドサービスに依存しないコンテナオーケストレーションなんですね。
GCPを使おうがAWSを使おうが、エンジニアにとって、それは特段大切ではなく、
アプリケーションのプロダクトコードが重要だと思います。そこで、クラウドサービスを
意識せずに、k8sを使うことができちゃうということですね。

## gVisor
[https://www.publickey1.jp/blog/18/gvisorgoogle.html:embed:cite]
従来は、下記のような問題をコンテナは抱えていました。

> コンテナ間でOSのカーネルを共有しているためにコンテナ間の分離レベルは高くなく、同一OS上で稼働している別のコンテナの負荷の影響を受けやすかったり、コンテナからOSのシステムコールを直接呼び出せることなどによるセキュリティ上の課題を引き起こしやすくもあります。

そこで、gVisorの出番

> 従来のコンテナの軽量さを保ちつつ、コンテナの分離について新たな実装を提供することよって、準仮想化に近い、より安全な分離を提供するコンテナランタイム

なるほど〜！（ただ、記事を読んだだけｗ）

## Cloud Next Recap 2
### 発表者
佐藤 一憲(Google)

### 内容
機械学習についてAutoMLを紹介されていました。
私は、そういったものが苦手だったので、よく覚えてないです...

## Cloud Next Recap 3
### 発表者
Kirill Tropin(Google)

### 内容
スピーキングは英語だったので、よく覚えてないです...

## Cloud Run ネタ
### 発表者
ちまめ@rito

### 発表資料
[https://speakerdeck.com/chimame/cloud-run-one-step-ahead:embed:cite]

### 内容
2コマンドでcloudrunできるぐらい、簡単！
ただ、プロダクトとして扱うには、いくつか問題があるそう。

1. docker full buildするみたいで遅い
→ kaniko で、cacheが効くそう。    
[https://github.com/GoogleContainerTools/kaniko:embed:cite]  

2. memoryStoreがまだ未対応(VPC)  

## GCP大阪リージョンとレイテンシ
### 発表者
salamander さん

### 内容
大阪リージョンのレイテンシについて紹介されました。
[https://docs.google.com/presentation/d/1dbGgjr3Z9o-bOxmT5SQ5bRHMEI0Jzh0BQUQkXlEGyYE/edit?usp=sharing:embed:cite]

# 最後に
Googleでは、もはや当たり前のようにKubernetesのサービスを進めている印象でした。
クラウド、オンプレを関係なく動かせるプラットフォームであるAnthosや、
どのクラウドサービスでも関係なく動かせるコンテナオーケストレーションであるKnativeなど、
どこでもkubernetesを動かせるように進めらています。
これは、kubernetesを使えるようにならないと！
下記で、勉強中です！
[https://qiita.com/silverbirder/items/cfaaba136b74b3140902:embed:cite]



