# Links
https://silverbirder180.hatenablog.com/entry/2020/06/06/222800

# Title
ZoomのMeetingを自動生成するGASライブラリ zoom-meeting-creator を作った

# Contents
みなさん、Zoom使っていますか？ 
ZoomのMeetingを自動生成するGASライブラリを公開しましたので、
そのきっかけと使い方について紹介しようと思います。

[:contents]

# きっかけ
社のSlackで次のqiitaの記事を知りました。

[https://qiita.com/kudota/items/b480610cc3f575a8ec6f:embed:cite]

GASからZoomのMeetingを作れるのって、簡単なんだな〜と思いつつ、
"cronのように使いたい"というSlackのコメントがあったので、サクッと一日で作ってみました。

定期的にZoomのMeeting(IDやパスワード)を更新する会社はあるはずです。
そういう会社にとっては、このツールは、便利かもしれません。

# 作ったもの

[https://github.com/Silver-birder/zoom-meeting-creator:embed:cite]

これをGAS側でライブラリ追加すると使えます。
このGASでは、

* ZoomのMeetingを作成
* Slackとの連携

ができます。この機能を、GASの定期実行を組み合わせれば、"ZoomのMeeting作成をcronのように"使えるようになります。