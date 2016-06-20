# The Tangle

2016/3 version 0.6

## 概要
私たちはこのペーパの中でIOTA（IoT産業のための暗号通貨)このテクノロジーはblockchain以来のイノベーションであり世界規模のマイクロペイメントを進めることが出来ます

## 1　導入、システムの説明

bitcoinの過去６年間の成功と成長はblockchainテクノロジーの価値を証明した。しかしながらこのテクノロジーはまた数々の欠点を持っている。それらを防ぎならが暗号通貨のためのグローバルプラットフォームとして利用されます。これらの問題の中でもとりわけ注目されるのがなマイクロペイメントの作成不可能性でこれは急速開発されているIoT産業での重要性を持っている、具体的に今の有効なシステムにおいてトランザクションを作るための手数料を払わなければならない。だから転送は最小量でちょうどそれ以降も意味がないさらに何倍もの手数料を払うことになる、一方でブロックのインセンティブとして機能する手数料を取り除くことは簡単ではない。

それはまた暗号通貨が役割が明確で分離されたシステムの中で存在していることが確認されていなければならない

そのようなシステムは差別要素（衝突を作るし衝突した解決手段に多くのリソースを割くことになる）を作ることが避けられない

これら全てはblockchain技術とは本質的に異なる研究を正当化します。その上にbitcoinやほかの多くの暗号通貨をベースにしています

このペーパーにおいて私たちは blockchainless　アプローチを取っています。それは今iota（IoTのために最近デザインされた暗号通貨）の中で稼働し存在している ）

もちろん、すべての理論解析は今動いているシステムからのフィードバックなしては不完全だろう

一般的にIOTAはグローバルblockchainの代わりに次のように動作します。DAG(有向非巡回グラフ)はTangleと呼んでいます。ノードによって呼ばれたトランザクションはTangleのサイトセットで構成される。このエッジセットはこれらの方法で確認出来る
新しいトランザクションが到着すると。それは二つ前のトランザザクションを承認する必要があります（有効辺によって表されます図１参照）もしトランザクションＡとトランザクションBとの有効エッジが存在しない場合でも最低二つの有効パスは存在します。私たちはそれをAはBを間接的承認したと呼んでいます。またgenesis transactionの場合すべての他のトランザクションを承認する（図２参照）

次の通り説明します。まずすべてのトークンのバランスを持つ一つのアドレスがあります次にgenesis transactionがfounderのアドレスに送られます。すべてのトークンがgenesisで作られたことがストレスされます。これはマイングではありません。ある意味では「マイナーはマイニング報酬を受け取った」という意味です

site: tangle graphのトランザクション代表
ネットワークはノードによって構成されそれはトランザクション問題のエンティティです

さて、考え方は以下の通りです
トランザクションを発行するためにユーザは他のトランザクションを承認することが必要ですそのため、ネットワークのセキュリティに貢献することができます
それはノードが承認済みのコンフリクトしていないトランザクションがあることやコンフリクトしたトランザクションを承認しないといったチェックを行うことを想定しています

トランザクションは多くの直接または間接の承認を受けてシステムによってそれ以上の承認になります。他の言葉でよりダブルスペンディングトランザクションを承認するシステムを作ることが難しくなる（あるいは事実上不可能）
これは私たちがトランザクションを承認するためにトランザクションを選び出すことにどのようなルールも課さないということを観察することが大切だということですむしろ私たちが主張するもし多数のノードがいくつかの基準のルールに従っている（特にIoTの文脈でにおいてはノードはプリインストールされたファームウェアを持つチップがあり、合理的な仮定であると思われます）

その後、任意の固定ノードのためにそれは同じルールに固執することをお勧めします


具体的には、トランザクションを発行し、ノードは次のことを行います

- まず、トランザクションを承認するための2つの他のトランザクションをいくつかのアルゴリズムに従って選択します( 一般的にはこれら2つのトランザクションは一致してもよいです。）
- これは、 2つのトランザクションが競合していないこと、競合したトランザクションを承認しないことかどうかをチェックします

- トランザクションが有効であるために、ノードは暗号パズルを解く必要があります。bitcoinと同様のマイニング（例えば、それはnonceをようにそのナンスのハッシュが一緒に見つける必要があります
承認されたトランザクションからのいくつかのデータで特定の形態を有し、
例えば、 正面にゼロの少なくともいくつかの固定番号を持っています。


一般的に、我々はそのように、非同期ネットワークを持っている、ことを観察することが重要です。ノードは、必ずしもトランザクションの同じsetが表示されませんし必要としません。
tangleは競合するトランザクションを含むことがで切ることに留意すべきです。ノードはコンセンサスをアーカイブする必要はない。それぞれの有効なトランザクションはledgerになれる権利を持っています。（それらはすべて存在し得る）でも、コンフリクトしたトランザクションが存在する場合、
どのトランザクションが孤立するか彼らが決定する必要があります

つまり、もはや入力トランザクションによって最終的には間接的に承認されていません
ノードが2つのコンフリクトする取引から決定するために使用する主なルール
は次のようになります。何回もノードはtip selection argorithmを走らせます、そしてそれぞれのトランザクションノードは、二つのどのトランザクションが承認されるかチップの選択を実行します

例えばtip selection argorithm １００回後にトランザクションは97回目に選択されます、私たちはこれを97%の信頼度の確認であると呼んでいます

私たちはまた、次の質問にコメントしてみましょう
：ノードがトランザクションを伝播させるための動機は何ですか？
実は私たちのセットアップ内のノードはモチベーションを持っていません。すべてのノードはいくつかの統計を計算し、それらの中の一つがどれくらいあたらしいトランザクションが隣から取得されたのか、もしある特定のノードが「怠け者」だった場合、たとえトランザクションを発行していなくてもそのネイバーによってドロップされます

従ってそれ自身が承認する新しいトランザクションを共有する直接のインセンティブは持っていません。

それでも懸命に仕事するインセンティブを持っています。
以降のセクションでは、 2章でいくつかの表記を導入した後、我々は議論します

承認する2つのトランザクションを選択するためのアルゴリズム、全体的な取引の承認（第3 、特に3.1節） 、そして可能性を測定するためのルール
攻撃シナリオ（第4節） 。また、万一読者はおびえていること
式で、 （複数の）彼がの終わりに「結論」部分に直接ジャンプすることができます
対応するセクション。

なお、 cryptocurrencyでのDAGの使用方法についてのアイデア
コンテキストは、いくつかのを回にあります、例えば、参照してください。 [3 、 5 、 6 、 7 、 10 ] 。具体的には、作業[ 6 ]
ビットコインの変更を提案している、いわゆるゴーストプロトコルを導入
代わりにblockchainの木台帳主とすることにより、プロトコル。それが示されています
そのような改変の許可は確認時間を短縮し、改善するためのこと
ネットワーク全体のセキュリティ。論文[7 ]著者らは、 DAGベースの検討します
cryptocurrencyモデル。異なる我々のモデルから、 DAGのサイトがブロックであります
（ない個々のトランザクション） 、鉱山労働者は、同様に（取引報酬のために競合し、
ビットコイン）新しいトークンを作成することができます。また、 [ 5 ]ソリューションの仕事であることを観察します
それは、任意の特定については説明しませんが、私たちと少し似ては、提案されました
先端の承認戦略。私たちは、別のアプローチ[ 2 ]、[8]それは作ることを目指しも言及します
ピア・ツー・ピア決済チャネルを確立することによって可能なビットコインマイクロペイメント。
