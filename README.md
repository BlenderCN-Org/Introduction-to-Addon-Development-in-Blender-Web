<div id="sect_title_img_0_0"></div>

<div id="sect_title_text"></div>

# はじめに

<div id="preface"></div>

###### 　

{% if book.edition >= 2.0 %}
{% if book.format == "pdf" %}

## 第2版執筆にあたって

初版では、執筆当時に筆者がこれまでのアドオンの開発を行う中で、必要とした情報を一通り書きました。当時は、比較的よく利用するBlenderのAPIに絞って執筆を行ったことから、アドオン開発で必要な情報はほとんど書けただろうと、筆者の中で勝手に思っていました。しかし、初版執筆後に本書の初版を改めて読み返してみると、アドオンをこれから開発する人にとって必要な情報が、本当に書けているのだろうかと思うようになります。実際、BlenderのUIを個人向けにカスタマイズするといった、アドオンの初心者が比較的扱いやすい内容を、初版ではほとんど取り上げていませんでした。そのため、第2版出版に対する意欲が次第に高まり、執筆をすることを決めました。

第2版では誤字の修正はもちろんのこと、筆者が初版で不足していると感じた内容（UIの制御や応用的な内容の）について新たに執筆しました。また、第2版は基本的な内容である1章と2章から構成される前編と、応用的な内容である3章と4章から構成される後編に分けました。本来であれば分冊にせず1冊でまとめたほうが良いのですが、ページ数と執筆期間の都合から、2部構成という形をとらせていただきました。

また、第2版では新規に5章を設け、本節で解説した内容を組み合わせて作成したサンプル集を紹介します。複数のAPIを組み合わせることで、アドオンとして実現できることが広がるということを、5章で紹介するサンプルから感じ取っていただければと思います。

{% if book.volume == "1" %}

ここでは、第2版の前編から新規に追加した内容をまとめています。なお初版と同様、サンプルを用いて実際に手を動かしながら理解していく方針で説明します。

* より詳細なアドオンのインストール方法・アンインストール方法・アップデート方法（[1-4節](body/chapter_01/04_Understand_Install_Uninstall_Update_Add-on.md)）
* アドオンのソースコードを複数のファイルに分割する方法（[2-7節](body/chapter_02/07_Divide_Add-on_Source_into_Multiple_Files.md)）
* BlenderのUI制御方法（[2-8節](body/chapter_02/08_Control_Blender_UI_1.md)、[2-9節](body/chapter_02/09_Control_Blender_UI_2.md)、[2-10節](body/chapter_02/10_Control_Blender_UI_3.md)）

{% elif book.volume == "2" %}

ここでは、第2版の後編から新規に追加した内容をまとめています。見て分かるとおり、後編は新規で追加した内容が大半となっています。なお、初版や第2版の前編と同様、サンプルを用いて実際に手を動かしながら理解していく方針で説明します。

* キーボードのキーイベントを扱う方法（[3-2節](body/chapter_03/02_Handle_Keyboard_Key_Event.md)）
* タイマイベントを扱う方法（[3-3節](body/chapter_03/03_Handle_Timer_Event.md)）
* blfモジュールを使ってテキストを描画する方法（[3-5節](body/chapter_03/05_Render_String_with_blf_Module.md)）
* オーディオファイルを再生する方法（[3-6節](body/chapter_03/06_Play_Audio_File.md)）
* アドオンのUIを複数の言語に対応する方法（[3-7節](body/chapter_03/07_Multilingual_Support.md)）
* 座標変換の活用（[3-8節](body/chapter_03/08_Use_Coordinate_Transformation_1.md)、[3-9節](body/chapter_03/09_Use_Coordinate_Transformation_2.md)）
* ユーザー・プリファレンスの活用（[3-10節](body/chapter_03/10_Use_User_Preference.md)）
* アドオンのライセンスの決め方（[4-4節](body/chapter_04/04_Determine_License_of_Add-on.md)）
* アドオンの動作テストを自動化する方法（[4-5節](body/chapter_04/05_Test_Add-on_Automatically.md)）
* アドオンのサンプル集（[5章](body/chapter_05/SUMMARY.md)）


{% endif %}

{% endif %}
{% endif %}

## 本書について

def execute(self, context):

本書は、3DCGソフト「Blender」のアドオンを初めて開発する方を対象とした、アドオン開発の入門書です。
本書を最後まで読むことで、アドオンを開発する際に最低限必要な知識が得られ、読者が独自のアドオンを開発することができるようになります。

本書はアドオン開発の経験がない方が対象としていますが、すでにアドオンの開発を経験されている方でも参考になる情報があると考えています。特に4章では、アドオンの公開方法やデバッグ方法、作ったアドオンをBlender本体に取り込んでもらう方法など、アドオンに関連する周辺の話題も取り上げています。知っておくと後々役立つと思われる情報を載せていますので、余力があればぜひ一読ください。


<div id="space_m"></div>


### Blenderのアドオン開発って面白いの？

筆者は、3DモデルをBlenderで作成していた知人から、Blenderへの新規機能の追加を頼まれたことがきっかけでアドオン開発の世界に入りました。

筆者が初めて作成したアドオンは、3Dビューエリア上で選択したメッシュの面間でUVをコピー＆ペーストする機能を持つものでした。知人から、BlenderにUVをコピーする機能がなくて困ってるという話を聞いたことが、このアドオンを作ったきっかけでした。
Blenderで作成した3Dモデルにテクスチャを設定する時、最近は直接ペイントしたり自動的にUV展開することが多くなってきていますが、頂点数を少なくして応答性を高めるゲーム分野では、いまだにUVを意識する必要があります。

初めてのアドオン開発ということもあり苦労しましたが、無事に記念すべき第1弾となるアドオンが完成しました。作ったアドオンを使った知人から便利だと感想をもらった時は、完成までに苦労したこともあり、嬉しかったです。自分で作成したアドオンを使ったユーザから感想をもらえるのは嬉しく、楽しいものです。

最初に作成したアドオンは、細かい修正を行ってWeb上で公開しました。そして、Web上で様々な意見を取り入れることで改善が進み、UVのコピー・ペースト機能をベースに様々な機能が追加され、複数のUV編集機能を持つアドオンになりました。公開から数年が経った今でも、アドオンに対する要望があります。アドオンを公開することで、自分で開発したアドオンがより高機能になっていくのは、非常におもしろいことです。そしてこれはアドオンの開発を続けてきて言えることですが、アドオン開発を通して他のアドオン開発者やアドオン利用者と交流できるのも、アドオン開発の醍醐味の一つだと思います。

### 本書をなぜ執筆したの？

アドオン開発を始めた当時は、Blenderの標準の機能ですら使い慣れていない状態でした（今もですが）。このため、初めてアドオンを開発した時はどこから手をつけたらよいかわからず、手探りで開発を進めるしかありませんでした。そして当時はアドオン開発の情報源が今以上に少なく、さらに日本語をサポートしているとなると数を数えられるくらいの情報源しかありませんでした。結局他のアドオンのソースコードを読んで改造してデバッグしながらなんとか完成させたのですが、想像していたよりも開発に時間がかかってしまいました。このような背景もあり、アドオンを開発しようと考えている人が同じ苦労をして欲しくないと思い、本書の執筆を決めたのです。

さらに、これまでBlenderを3DCGを作るためのツールとしてのみ使ってきた方にも、本書を読んでアドオンの開発に挑戦してもらいたいという期待を持っています。実際、3DCGを作るためにBlenderを利用するユーザは、開発者が意識していないような改善案や問題意識をBlenderに対して持っていることが多いと筆者は考えています。本書を読むことで、これまでBlenderを使う立場であった方が、アドオン開発に一歩踏み出せたら嬉しいなと思います。

## 本書の読み方

本書は、はじめてBlenderのアドオンを開発する方を対象としているため、Blenderやアドオンに関する説明から始めています。すでにBlenderを使ったことがある方にとって、前半の解説は当たり前の内容で物足りないかもしれません。このため、本書は前から後ろに進んでいくにつれて、基本的な内容から発展的な内容になるような構成を意識して執筆しています。すでに理解していて読む必要がないと感じた部分は、必要に応じて読み飛ばしてください。また、本書は節ごとにテーマを決めて説明する構成を取っているため、知りたい内容だけに絞って読んでも問題ありません。

本書は、読者の方が実際に手を動かして作業する場面が数多くあります。本を読んだだけで理解することはなかなか難しいので、積極的に手を動かして理解するようにしましょう。特にアドオンのサンプルを用いて説明している節では、必ず読者の環境で動作させて確認してください。サンプルをそのまま動かすだけでも、いろいろ学べることはあります。

それでは、楽しいBlenderアドオン開発の世界を満喫してください！

## 本書で紹介するサンプルのソースコードについて

本書で紹介するアドオンのサンプルのソースコードは、以下のURLからダウンロードすることができます。

{% if book.edition == 1.0 %}

https://github.com/nutti/Introduction-to-Add-on-Development-in-Blender/releases/download/v1/sample_v1.zip

{% elif book.edition == 2.0 %}

https://github.com/nutti/Introduction-to-Add-on-Development-in-Blender/releases/download/v2/sample_v2.zip

{% endif %}



## 前提知識

本書を読むための必須知識と、より高度なアドオンを開発するために知っておくと役立つ推奨知識を示します。


<div id="space_s"></div>


### 必須知識

本書を読むために必要となる必須知識を次に示します。

* Blenderの基礎知識
  * 基本操作
* Pythonの基礎知識
  * 変数（変数宣言、値の代入、型）
  * 四則演算
  * オブジェクト（タプル、リスト、辞書）
  * 関数（関数定義、呼び出し、戻り値）
  * クラス（クラス定義、メンバ変数、メソッド、継承）
  * モジュールのインポート
* 3DCGの知識
  * 基本用語（メッシュ、UV座標、面、法線など）


### 推奨知識

必須知識に加えて次のような知識があると、本書で紹介している以上の高度なアドオンを作成することができます。
なお本書を読むだけであれば、必ずしも必要ではない知識です。

* 数学
  * 三角関数
  * ベクトル演算
  * 行列演算
* 物理
  * 古典力学
  * 流体力学
* 英語
  * 3DCG関連の英語
  * 日常会話で利用する英語(チャット)

{% include "LICENSE" %}

## 誤字・脱字を報告いただける方について

本書内の誤字・脱字を見つけた方は、以下のサポートページや[おわりに](body/Conclusion.md)に記載している連絡先よりご連絡ください。

https://github.com/nutti/Introduction-to-Add-on-Development-in-Blender/issues
https://www.gitbook.com/book/nutti/introduction-to-add-on-development-in-blender/discussions

また、本書の原本が置かれているGitHubページからPull Requestを出すことにより、各自修正した内容について反映依頼を出すことができます。

https://github.com/nutti/Introduction-to-Add-on-Development-in-Blender

なお本書の執筆に貢献いただいた方は、許可を取った上で[おわりに](body/Conclusion.md)の謝辞に名前（またはニックネーム）を掲載させていただきます。

## 本書へのリクエストについて

本書に執筆内容の追加等を希望される方は、以下のサポートページや[おわりに](body/Conclusion.md)に記載している連絡先より、リクエストを出すことができます。

https://github.com/nutti/Introduction-to-Add-on-Development-in-Blender/issues
https://www.gitbook.com/book/nutti/introduction-to-add-on-development-in-blender/discussions


## 本書の内容に関するお問い合わせについて

本書の内容に関する問い合わせについては、以下のサポートページや[おわりに](body/Conclusion.md)に記載している連絡先から問い合わせください。

https://github.com/nutti/Introduction-to-Add-on-Development-in-Blender/issues
https://www.gitbook.com/book/nutti/introduction-to-add-on-development-in-blender/discussions
