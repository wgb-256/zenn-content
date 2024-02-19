---
title: "生成AI・ChatGPTに支配される前に、押さえるべきAI事情"
emoji: "🧠"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["機械学習", "AI", "初心者"]
published: false
---

# 章立て
1. はじめに
1. AI研究の全体像
1. AI技術関連史
1. 今後のAI技術について
1. おわりに

# 1. はじめに
AIに支配されうる未来が見え始めている。
ChatGPTをはじめとする生成AIにより、技術者に限らず、AIに頼らざるを得ない状況になった。技術進展スピードと影響力を考えると、より一層AIが影響を与える範囲は広がっていくことは間違いない。しかし発展が目まぐるしく、高度すぎる技術になっているため、一朝一夕では最新のAI技術についてキャッチアップすることはできなくなっており、よくわからないままAIに触れることになってしまったり、AIという技術が実はとっつきにくいものになってしまった。
その結果、上辺だけのAI議論、過剰な期待・恐怖、不適切な利用を招いてしまう危険がある。そしてそんなことをしているうちにAIがより高度になり、気づかないうちにAIが人間を支配、すなわち単独で人間社会を最適化し始めるということは、もはや起こりえない夢の話ではなくなってきている。したがって、AIという「技術」に対して向き合うことは今後大変重要になってくるはずである。本記事では、これからAIの勉強を始めたい人や再度情報の整理をしたい人に向け、AI界隈の状況についてまとめた。

# 2. AI研究の全体像
## 2.1. AIが担うタスク
現実世界で用いられるAIは、人間の補助（人間の仕事を手伝う）・代替（人間の代わりに仕事をする）・拡張（人間よりも高度な仕事をする）という立ち位置であることが多い。次章で述べるが、AIの発端は「人間のような知的な機械」という発想である。したがって、AIが担うタスクは、基本的には人間の活動になぞらえるとよいと考えられる。具体的には、入力（見る・聞く・読む 等）により得た情報を処理し（考える）、出力（意思決定・認識・分類・話す・書く 等）を行うことになる。

![AIのタスク](/images/ai_history/AITask.png)

> **note**
嗅覚・触覚・味覚に関するセンサーが一般的でなくそれらを入力とするAIはまだ少ないため、記載していない。今後、それらに加え雰囲気・第六感のような曖昧な情報も取り扱われる可能性も十分ある。

## 2.2. AIプログラムとは
現状、AIは基本的にソフトウェア、特にコンピュータプログラムである。あるプログラムがAIであるというためには何が必要か、私見を述べる。
今回の調査を通して、AIプログラムは「推論（Reasoning）」または「推測（Inference）」を行っていると考えられる。
推論とは、利用可能な情報（証拠・過去事例等）から、結論や新しい情報を導く思考過程であり、推測とは、与えられた情報を越えた判断である[^2-1]。
したがって、あらかじめ決まっている情報に対して、不変の処理を行い、想定通りの結論を得るプログラムはAIとは言えない。
例えば、電卓のようにプログラムに入力される値に制限があり、それに対してどのように処理するかを、設計者がすべて把握できるプログラムはAIとは呼べない。
逆に、何が入力されるかわからない状況で、どのように対処するのかのみを手続き化したプログラムはAIと呼べる。
後述のLogic-based AIは論理的な思考プロセスをプログラム化し、Knowledge-based AIは専門家の知識を体系化して論理をプログラム化し、Machine Learningはデータから何らかのルールを抽出してプログラム化している。
よって、推論または推測が複雑（例えば、人間が論理を立てられない、入力の次元が大きい等）であればあるほど、高度なAIと主張できると考えらえる。

[^2-1]:[推論(reasoning, inference)](https://cogpsy.educ.kyoto-u.ac.jp/personal/Kusumi/inference.htm)

## 2.3. AI技術のカテゴリ・分類
### 2.3.1. 思想によるAI実現アプローチの分類
AIを実現するためのアプローチは、思想の違いで分類することができる。本節では、中でも大きな潮流であるSymbolic AIとConnectionist AIを中心に述べる。
![AI Categories](/images/ai_history/ai_categories.png)
*AI分類*
#### Symbolic AI
Symbol操作を用いて人間の思考プロセスをプログラム化するいう思想に基づいたAIであり[^10-42] [^3-3]、推測の論理規則によるSymbol処理を行うSymbolicism（象徴主義）的なアプローチ[^3-9]。
1976年にAllen NewellとHerbert Simonから発表された、知能を記号（Symbol）処理によって表現し得るというPhysical Symbol System Hypothesis（物理記号システム仮説）に基づいている[^3-1] [^3-2]。
主に検索木とHeuristicsを用いた最も初期に発展した古典的なアプローチは、特にGOFAI（Good Old-Fashioned AI）と呼ばれ、明示的なロジックに基づいており、説明性が高いとして有用性を主張される場合もある[^3-4] [^3-6]。
基本的に手作業でアルゴリズムの最適化が行われる[^3-7]。

> **note**
Symbolic AIの文脈で、SymbolismとSymbolicismのどちら思想も取り上げられる場合があるが[^3-8] [^3-9]、[この記事](https://thecontentauthority.com/blog/symbolism-vs-symbolicism)の*Symbolicismは、システムまたは理論におけるSymbolまたはSymbolic Elementの使用を指す。*という定義から、今回はSymbolisicmを用いた。

#### Connectionist AI
ニューロンの数学モデルを用いて人工ニューラルネットワーク（ANN: Artificial Neural Network）を構成する手法であり[^10-49]、ANNを利用して知的能力を説明しようとするConnectionism的なアプローチ[^3-10]。Subsymbolic AIとも呼ばれる[^3-5]。
##### Machine Learning（機械学習）
人間がルールを作らずに機械に学習能力を与える研究分野。特に、既存のデータから何らかの関係性やパターンの発見に焦点をおいており[^3-11]、人力では取り扱いが不可能なほどの膨大な量のデータ（Big Data）からモデル（Data-Driven model）を得られることが大きなメリットとなる。ただし昨今では、モデルのブラックボックス性（データから得た学習アルゴリズムを人間が説明できないこと）が問題となる場合も多い。
##### Deep Learning（深層学習）
機械学習の中でも、3層以上の多層ニューラルネットワークを用いてモデルを構築する分野[^3-12]。多層にすることでモデルの表現力が上がり、より高度なアルゴリズムを得ることができる一方、ネットワークの最適化が難しいこと、多大な計算リソースを要すること等が課題として挙げられる。
#### その他のアプローチ
##### Neuro-Symbolic AI
Symbolic AIの記号推論（Symbolic Reasoning）とConnectionist AIのニューラルネットワークの技術を組み合わせ、それぞれの説明性と認知能力を補完しようとするアプローチ[^3-13]。Symbolを用いた論理的な表現をニューラルネットワークに焼き直す手法と、ニューラルパターンから情報を抽出してSymbol表現へマッピング後、Symbolic Reasoningを行う手法の2つに大別される[^3-14]。
##### Actionist AI
機械の自動制御や動物の神経系機能の類似性や関連性をテーマとする人工頭脳学（Cybernetics）[^3-15]を由来とし、知性は認識・行動に依存し、知識・表現・推論は必要ないという思想であるActionism的なアプローチ[^3-16]。外部環境との相互作用に基づいて、環境フィードバックを自律的に認識して適切な行動を行うことによって知的行動が完成すると置いている[^3-17]。
###### 強化学習（Reinforcement Learning）
特定の環境（Environment）で報酬（Rewards）を最大化するために適切な行動（Action）をとることを目的としてプログラム（Agent）を学習させる、環境と相互作用する自己評価学習手法[^3-19] [^3-17]。
（大規模な）データセットが不要であるため、学習データに依存せず複雑な振る舞いをモデル化することができるなどの利点を持つ[^3-20]。機械学習の一種とも言うことができる[^3-18]。

>![Reinforcement Learning](https://miro.medium.com/v2/resize:fit:2000/format:webp/0*WC4l7u90TsKs_eXj.png)
*Reinforcement Learning（引用:[^3-19]）*

###### 進化的計算（Evolutionary Computation）
変化する環境に適応するために、多大な可能性から解決策を探索する進化（Evolution）のプロセスを[^3-21]、計算上の問題（特にここではAIの最適化）に応用する手法。
主なアルゴリズムとして、遺伝的アルゴリズム（Genetic Algorithm: GA）等が挙げられる。

[^3-1]: [Computer Science as Empirical Inquiry: Symbols and Search](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=443653b1905d1ee95bfd504f66f5f3f6487fba56)
[^3-2]: [記号創発問題　─記号創発ロボティクスによる記号接地問題の本質的解決に向けて─](https://www.jstage.jst.go.jp/article/jjsai/31/1/31_74/_pdf/-char/ja)
[^3-3]:[Symbolic Artificial Intelligence](https://primo.ai/index.php?title=Symbolic_Artificial_Intelligence)
[^3-4]:[Reviving Explainability with Good Old-Fashioned AI](https://www.cpq.se/the-cpq-blog/reviving-explainability-with-good-old-fashioned-ai)
[^3-5]:[A Survey on Verification and Validation, Testing and Evaluations of Neurosymbolic Artificial Intelligence](https://arxiv.org/abs/2401.03188)
[^3-6]:[GOFAI Considered Harmful (And Mythical)](http://cs-www.cs.yale.edu/homes/dvm/papers/nogofai.pdf)
[^3-7]:[The Difference Between Symbolic AI and Connectionist AI](https://blog.re-work.co/the-difference-between-symbolic-ai-and-connectionist-ai/)
[^3-8]:[Symbolism Versus Connectionism In AI: Is There A Third Way?](https://www.forbes.com/sites/forbestechcouncil/2020/09/01/symbolism-versus-connectionism-in-ai-is-there-a-third-way/?sh=36000ab07549)
[^3-9]:[Symbolicism and Connectionism: AI Back at a Join Point](https://users.monash.edu/~korb/shadowfax/pubs/dreyfus.pdf)
[^3-10]:[Connectionism](https://plato.stanford.edu/entries/connectionism/)
[^3-11]:[What is machine learning and how does it work? In-depth guide](https://www.techtarget.com/searchenterpriseai/definition/machine-learning-ML)
[^3-12]:[What is deep learning?](https://www.ibm.com/topics/deep-learning)
[^3-13]:[Neurosymbolic AI: Competing or Complementary (to Human) Intelligence](https://www.adalanai.com/post/neurosymbolic-ai-competing-or-complementary-to-human-intelligence)
[^3-14]:[Neurosymbolic AI - Why, What, and How](https://arxiv.org/abs/2305.00813)
[^3-15]:[サイバネティクス](https://www.sophia-it.com/content/cybernetics)
[^3-16]:[Major schools of AI- how they reshape the way we interact with machines and understand artificial intelligence](https://medium.com/@ikraaamzerrouki/major-schools-of-ai-how-they-reshape-the-way-we-interact-with-machines-and-understand-artificial-e7df1e1bd5f3#:~:text=Actionism%20is%20also%20known%20as,knowledge%2C%20representation%2C%20or%20reasoning.)
[^3-17]:[From Independence to Interconnection—A Review of AI Technology Applied in Energy Systems](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8661901)
[^3-18]:[Reinforcement learning](https://www.geeksforgeeks.org/what-is-reinforcement-learning/)
[^3-19]:[Reinforcement Learning, Part 1: A Brief Introduction](https://medium.com/ai%C2%B3-theory-practice-business/reinforcement-learning-part-1-a-brief-introduction-a53a849771cf)
[^3-20]:[The Benefits of Reinforcement Machine Learning](https://www.modev.com/blog/the-benefits-of-reinforcement-machine-learning)
[^3-21]:[Evolutionary Computation: An Overview](https://link.springer.com/chapter/10.1007/3-540-56602-3_163)

### 2.3.2. データの取り扱い方による機械学習手法の分類
データの扱い方で学習方法を下記のように分類できる。
（同様の分類で、強化学習もここにしばしば含まれるが、前述したため割愛する）
#### 教師あり学習（Supervised Learning）
入力データに対する正しい出力が紐づけられている、ラベル付きデータセットを教師データ（Target data）として用いて、主に回帰・分類タスクを行う機械学習モデルを獲得する手法。
#### 教師なし学習（Unsupervised Learning）
入力データに対する出力が紐づけられていない、ラベルなしデータセットを教師データとして用いて、主にクラスタリング・次元削減タスクを行う機械学習モデルを獲得する手法。
#### 半教師あり学習（Semi-supervised Learning）
ラベル付きデータとラベルなしデータの両方を用いる手法（ラベル付きデータの方が少ない場合が多い）。
#### 自己教師あり学習（Self-Supervised Learning）
ラベルのないデータから独自のラベルを自動的に作り、それをもとに学習を進める学習方法[^50-79]。

### 2.3.3. その他、特殊な学習方法
その他の学習方法で、重要と思われる手法を簡単に紹介する。
#### アンサンブル学習
複数のモデルからの予測を結合することで予測の精度を向上させる学習方法[^4-1]。
#### 転移学習
あるタスク向けに学習したモデルを、類似したタスクを実行するモデルの開始点として使用する学習方法[^4-2]。

[^4-1]:[A Comprehensive Guide to Ensemble Learning (with Python codes)](https://www.analyticsvidhya.com/blog/2018/06/comprehensive-guide-for-ensemble-models/)
[^4-2]:[Transfer Learning - 転移学習](https://jp.mathworks.com/discovery/transfer-learning.html)

## 2.4. AI研究の視点
AIに関する研究開発のうち現在最も活発なのは機械学習の分野である。そしてその中でも、およそ下記の3つの視点での研究活動が行われている[^7-2]（ただし、それぞれ影響を与え合っているため、取り組みをそれぞれに分類することは難しい）。
### Representation（Architecture）
AIモデルの構造をどのようにするかという視点。例えば、CNN、RNN、GAN、Transformer等（それぞれ次章でも触れる）、様々なトポロジーが有効であることが示されており[^6-2]、モデル構造がパターンの記憶や検索のプロセスにおいて非常に重要であることがわかっている[^6-4]。
この種の研究では、進化や生物学的なシステムの知見をAIモデルの設計に生かすことや[^6-3]、最適なトポロジー探索の自動化が有効な手段であると考えられている[^6-5]。

> ![Various kinds of neural networks](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*gccuMDV8fXjcvz1RSk4kgQ.png)
*Various kinds of neural networks（引用:[^6-1]）*

[^6-1]:[Cheat Sheets for AI, Neural Networks, Machine Learning, Deep Learning & Big Data](https://becominghuman.ai/cheat-sheets-for-ai-neural-networks-machine-learning-deep-learning-big-data-678c51b4b463)
[^6-2]:[Neural Network Architecture: all you need to know as an MLE [2023 edition]](https://kili-technology.com/data-labeling/machine-learning/neural-network-architecture-all-you-need-to-know-as-an-mle-2023-edition#573)
[^6-3]:[Improving Neural Networks with Neuroscience](https://medium.com/mlearning-ai/improving-neural-networks-with-neuroscience-e7a500ed0ab)
[^6-4]:[Influence of topology on the performance of a neural network](https://arxiv.org/abs/cond-mat/0310205)
[^6-5]:[Finding the Optimal Topology of an Approximating Neural Network](https://www.mdpi.com/2227-7390/11/1/217)

### Optimization
どのようにAIアルゴリズムを最適化するか、多くの場合ニューラルネットワークパラメータをどのように決めるかという視点[^7-1]。最適化は、利用されるニューラルネットワークが大規模になるにつれ困難であることもあり[^7-3]、活発に研究が行われている。主な課題は、勾配爆発・勾配消失等による解の収束に関する問題、収束速度に関する問題、局所解（Local minima）の取り扱いに関する問題などである[^7-2]。

>![Local minima and Global minima](https://blog.paperspace.com/content/images/2018/05/challenges-1.png)
*Local minima and Global minima in Optimization（引用:[^7-4]）*

[^7-1]:[Why Optimization Is Important in Machine Learning](https://machinelearningmastery.com/why-optimization-is-important-in-machine-learning/)
[^7-2]:[Optimization for deep learning: theory and algorithms](https://arxiv.org/abs/1912.08957)
[^7-3]:[Thick-Net: Parallel Network Structure for Sequential Modeling](https://arxiv.org/abs/1911.08074)
[^7-4]:[Intro to optimization in deep learning: Gradient Descent](https://blog.paperspace.com/intro-to-optimization-in-deep-learning-gradient-descent/)

### Generalization
AIによる推論の一般性、すなわち学習データに含まれないようなデータが入力された場合でも正確に推論できるかという視点[^8-1]。この視点は、特に製造業（予知保全や品質管理などのタスク）において顕著なものとなる[^8-2]。主な課題として、偏りのないデータセットの準備、オーバーフィッティング、ラベルの正確性等が挙げられる[^8-2]。

>![Underfitting and Overfitting](https://wp.wwu.edu/machinelearning/files/2017/01/mlconcepts_image5-rnehsa.png)
*Underfitting and Overfitting（引用:[^8-1]）*

[^8-1]:[Generalization and Overfitting](https://wp.wwu.edu/machinelearning/2017/01/22/generalization-and-overfitting/)
[^8-2]:[The Limitations of AI: Why Generalization is a Challenge](https://medium.com/kocdigital/the-limitations-of-ai-why-generalization-is-a-challenge-59c41e78a655)

# 3. AI技術関連史　　
本章では、AI技術がどのように発展したかを追う。中でも前章のAI技術分類と同様に、大きな潮流であるSymbolic AIとConnectionist AIを中心に述べる。
![AI技術関連史](/images/ai_history/ai-hisotry.png)
*AI技術関連史*

## 3.1. ~ 1957年ごろ：「AI」誕生
17世紀に活躍したドイツの学者[Gottfried Wilhelm Leibniz](https://en.wikipedia.org/wiki/Gottfried_Wilhelm_Leibniz)は、安全・時間浪費の観点から計算は人間ではなく機械がするべきであるという考え方を持っており、[Pascalの計算機](https://en.wikipedia.org/wiki/Pascal%27s_calculator)をもとにして、長さの異なる歯をもつシリンダーと移動式の歯車を組み合わせて計算（基本的には自然数の四則演算）を可能にしたStepped reckonerまたはLeibniz Wheel（ライプニッツの車輪）と呼ばれる手動機械式の計算機を、1694年に完成させた[^10-4] [^10-5]。これをきっかけにLeibnizは、数学的記述（mathmatical statement、詳細は以下の**note**を参照）の真理値を決定できる機械を作ることができるのではないかと考えるようになった。それが実現できると、機械が論理を扱うことができるようになるため、どういう場合には何をするといった**場合分け処理**や、明確な理由がある**推論**といった[^10-8]、より知的な処理が可能になる。機械が論理を扱うためには、人間が自然に行っているコミュニケーションのような、曖昧さが残る表現やその時によって用法・意味が変わるような**自然言語**（natual langage）ではなく、文法・意味が形式的に与えられて明確に論理が展開できる**形式言語**（formal language）が必要であると考え、Leibnizの研究は形式言語を用いた**形式理論**（formal theory）にも重きが置かれるようになっていった。さらに、Leibnizは活動の中で、現代のコンピュータの基礎となっている2進数演算（binary arithmetics）や[^10-9]、2進数コンピュータ（binary computer）についても功績を残している[^10-10]。

> **note**
数学的記述（mathmatical statement）は、正しい（真）か間違っている（偽）かが判断できる「文」であり、言葉や記号（symbol）が含まれる。例えば、言葉を使った「1は2よりも大きい」や、記号を使った「1>2」という文は、「偽」であるmathmatical statementである。

Leibnizの論文がドイツのHannoverで閲覧可能になった1830年代以降、その注目度は急速に高まり、Johann Eduard ErdmannやKurt Gödelなど後の研究に多大な影響を与える[^10-11] [^10-12]。この頃、数学界では数学理論を構築するための演繹的な方法（すでに知られている法則（一般論・ルール）や前提から、階段を登っていくように論理を積み重ねて結論を出す考え方[^10-13]）に注目が集まっており、数学における形式理論（公理理論ともいう）に関する新しい問題が提起されていた[^10-14]。1928年、ドイツの数学者であるDavid HilbertとWilhelm Ackermannは、**Entscheidungsproblem**（ドイツ語。日訳で決定問題、英訳でdecision problem）と呼ばれる、「（一階論理の）すべての数学的記述は、導出可能か」（すべての公理を考慮すれば、命題が証明可能かどうかを判断できるアルゴリズムが存在するかどうか）という問題を提起した[^10-15]。この問題は、「人間の思考プロセスをすべて単純なアルゴリズムで表現することは可能か」と言い換えることができ[^10-18]、もしそのようなことが可能であれば、単純なアルゴリズムだけでも実行可能な機械があれば、人間の思考活動を全てそれで再現できるということになる。

> **note**
数学者や数学団体は自身が発案・直面した未解決問題を公開し、研究を生み出してきた。1900年にHilbertが、パリで開催された国際数学者会議（International Congress of Mathematicians: ICM）および彼の著作で、次の世紀に研究されるべき23の主要な数学的問題が発表された[^10-1] [^10-2] [^10-3]。Entscheidungsproblemは[Hilbertの23の問題](https://ja.wikipedia.org/wiki/%E3%83%92%E3%83%AB%E3%83%99%E3%83%AB%E3%83%88%E3%81%AE23%E3%81%AE%E5%95%8F%E9%A1%8C)のうち、[Diophantine方程式](https://en.wikipedia.org/wiki/Diophantine_equation)に解があるかどうかを決定するアルゴリズムを求める第10問題に関連している。

1935年、HilbertのEntscheidungsproblemに興味を持ったAlan Turingは、任意の数学的記述の導出に必要な「形式化された手順」が必要である、として研究を開始した。すなわち、どんな数学的記述も導出できる手順が存在するということは、どんな数学的記述も証明可能であると言える、という考え方である。Turingは翌1936年に発表した論文[^10-22]で、そういう手順が可能である仮想的な機械（UTM: **Universal Turing machine**[^10-26]）を考案し、Entscheidungsproblemが成り立たたないことを証明した[^10-17] [^10-18] [^10-19] [^10-20]。したがって例えば、数学の定理を証明するためのアルゴリズム的な手法は存在せず、総当たり（Brute force）的に証明を試さなければならないということが示されたことになる[^10-54]。
Turingのアプローチで独創的だったのは、UTMを考案するにあたり、それまで発明されていた「機械」に注目するのではなく、子供が勉強で使う方眼紙や何か手順を踏むときの人間の思考など、「人間」に注目した上で、実行する手順を徹底的に曖昧さがない論理的な処理に落とし込んだことである[^10-21]。
UTMの論理性は、1943年に発表された、神経生理学者Warren McCullochと数学者Walter Pittsによるニューロンの数学モデル（MPニューロン、MCPニューロンと呼ばれる）およびそれにより構成されるニューラルネットワークモデルの考案のためのインスピレーションをもたらし[^10-23] [^10-47]、UTMの構成は、Machineへの命令を入力データと同じ記憶領域に配置するstored-program方式と呼ばれ、1945年にアメリカの学者John von Neumannにより発表されたコンピュータの構成（ノイマン型アーキテクチャ、von Neumann model、Princeton architectureなどと呼ばれる）にも強い影響を与えるなど[^10-24] [^10-25] [^10-26]、多大な影響を与えることとなった。
ノイマン型アーキテクチャが発表された1945年末には、世界初の「プログラム可能な（命令の与え方によって様々なタスクをこなすことができる）」計算機であるENIAC（Electronic Numerical Integrator and Computer）[^10-27] [^10-28]、1948年には世界で初めてノイマン型アーキテクチャで動作するManchester Baby（SSEM: Small-Scale Experimental Machineとも呼ばれる）など[^10-29] [^10-30]、続々と電子計算機（以降、コンピュータ）が一般化し（なんでもできるようになり）、同時に高性能化していった。
さらに1951年には、Marvin MinskyとDean Edmondsが、SNARC（Stochastic Neural Analog Reinforcement Calculator）という世界で初めて人工ニューラルネットワーク（ANN: Artificial Neural Network）を実装したコンピュータを構築している。SNARCのニューラルネットワークは、MPニューロンの考え方を拡張したHebb理論に基づいており、**学習**することができるようになっている。
Hebb理論は、1949年にカナダの心理学者Donald Olding Hebの[著書](https://pure.mpg.de/rest/items/item_2346268_3/component/file_2346267/content)で提唱された[^10-48]、ニューロンの数学モデルの学習ルールとそのアルゴリズムを含む理論である。Hebbは、つながっている2つのニューロンが同時に発火すればするほど、それらの接続強度（以降、重み）は強くなるという規則を主張した（これは、後に長期記憶の理論にも影響した）[^10-52]。この規則に基づいて重みを調整すれば、ロジックが変えられる、すなわち所望のロジックを得るために重みを調整すれば、機械が改善されることになるため「学習」と呼ぶことができる（SNARCではHebb則に基づいて重みの更新を人の手で行っていた）[^10-50]。
ただし、純粋な総当たり処理をすべてのタスクに対して行う計算はこの頃のコンピュータの性能では不可能であり[^10-55]、特に探索や認識といった複雑なタスクに対しては、知性的に解を求める方法が求められていたと考えられる。さらに1949年、アメリカのコンピュータ科学者Edmund Berkeleyが著書*Giant Brains, or Machines That Think*で「A machine, therefore, can think.」と言及し[^10-32] [^10-33] [^10-34]、1950年にTuringが発表した論文を「I PROPOSE to consider the question, ‘Can machines think?’」で始めるなど[^10-35]、思考する機械への関心はさらに盛り上がりを見せていた。Turingはその論文でTuring Testという機械の知性を試験する方法を提案している[^10-56]（Turing Testについて詳細は割愛）。

> **note**
Turing machineは論文の中ではcomputing machineと呼ばれている[^10-22]。

> ![Universal Turing Machine](https://web.mit.edu/manoli/turing/www/turing.gif)
*Universal Turing Machine（引用:[^10-57]）*

1954年にRAND（Research and Development）Corporationで、JOHNNIAC（John von Neumann Numerical Integrator and Automatic Computerの略でvon Neumannも開発に携わった）という計算機が構築され[^10-36]、翌年にかけてコンピュータ科学者・認知心理学者のAllen Newellと政治・経済・社会学者のHerbert Simonを中心にLogic Theoristと呼ばれる、IPL（Information Processing Languageというプログラミング言語）を用いたプログラムが作成された[^10-37] [^10-38] [^10-39]。Logic Theoristは、人間の数学者の頭脳の能力を模倣するように、Symbolを組み合わせて表現に組み込む「symbolic reasoning」と呼ばれる推論に基づいており[^10-41]、元になる数学定理のから新しい定理を証明することが可能である（しかもいくつかの数学定理は、人間の数学者よりも詳細な証明を示すことができた）[^10-37]。このように、基にする要素（root）から論理規則に基づいて分岐しながら目的の要素を探索するアルゴリズムは、今日でも探索木（search tree）として知られており、Logic Theoristは解ける保証がない問題に取り組むプログラムを作成した点が一つの大きな発明であると考えられる。また、Logic Theoristは実際の問題を解決するために人間の推論能力をシミュレートした世界初の人工知能プログラムと称され[^10-51]、Symbolを用いて人間の思考プロセスをプログラム化するいう思想に基づいたこのような手法は後に、**Symbolic AI**に分類される[^10-42]。Symbolic AIに対して、人間の脳をモデル化すれば人間と同じように知能をもたせることができるという思想に基づいて、ニューロンの数学モデルを用いてANNを構成する手法は**Connectionist AI**と呼ばれる[^10-49]。

上記のように、この頃、「考える機械（thinking machine）」に関する取り組みが非常に活発だったと言えるが、Dartmouth大学の数学助教授だったJohn McCarthyがより明確にその研究領域を発展させるために[^10-45]、DSRPAI（Dartmouth Summer Research Project on Artificial Intelligence、ダートマス会議）でRockefeller財団にセミナーのための資金提供を要請し、その研究領域を**人工知能**（**Artificial Intelligence**）と名付けた[^10-44]。これが、AIという用語が使われた最初の文書であり[^10-46]、これがAIという研究分野の誕生とされる（1956年にDSRPAIが開催され、Logic theoristはそこで発表された[^10-43]）。

[^10-1]: [Hilbert’s Problems: 23 and Math](https://www.simonsfoundation.org/2020/05/06/hilberts-problems-23-and-math/)
[^10-2]: [The Mathematical Problems of David Hilbert](http://aleph0.clarku.edu/~djoyce/hilbert/)
[^10-3]: [Gottfried Wilhelm Leibniz: An Optimistic Polymath](https://www.historyofdatascience.com/gottfried-wilhelm-leibniz-an-optimistic-polymath/)
[^10-4]: [Stepped reckoner in *Wikipedia*](https://en.wikipedia.org/wiki/Stepped_reckoner)
[^10-5]: [Calculus on Demand](https://math.dartmouth.edu/~m3cod/LeibnizWheelBig.htm)
[^10-6]: [Turing, Leibniz and Hilbert’s Entscheidungsproblem](https://3010tangents.wordpress.com/2014/11/26/turing-leibniz-and-hilberts-entscheidungsproblem/)
[^10-7]: [Mathematical Statements](https://www.math.toronto.edu/preparing-for-calculus/3_logic/we_1_statements.html)
[^10-8]: [Why Logic is Important for Computer Science and Mathematics](https://www.cs.utexas.edu/~rlc/whylog.htm)
[^10-9]: [EXPLANATION OF BINARY ARITHMETIC](https://www.leibniz-translations.com/binary.htm)
[^10-10]: G. Leibniz. De Progressione dyadica Pars I. 15 March 1679. [Principles of binary computers governed by punch cards.]
[^10-11]: [Leibniz’s Influence on 19th Century Logic](https://plato.stanford.edu/entries/leibniz-logic-influence/#SecWavRec)
[^10-12]: [2021: 375th birthday of Leibniz, founder of computer science](https://people.idsia.ch/~juergen/leibniz-father-computer-science-375.html)
[^10-13]: [演繹法と帰納法の違いとは？考え方や鍛え方をご紹介](https://solution.lmi.ne.jp/column/c198)
[^10-14]: [Axiomatic method](https://encyclopediaofmath.org/index.php?title=Axiomatic_method)
[^10-15]: [The Entscheidungsproblem and Alan Turing](https://www.gcsu.edu/sites/files/page-assets/node-808/attachments/brodkorb.pdf)
[^10-16]: [Entscheidungsproblem in *Wikipedia*](https://en.wikipedia.org/wiki/Entscheidungsproblem)

[^10-17]: [Alan Turing The Math Genius, The Cryptanalyst, and The Father Of Computer Science](https://i3l.ac.id/alan-turing-the-math-genius-the-cryptanalyst-and-the-father-of-computer-science/)
[^10-18]: [Alan Turing and the Development of the Electronic Computer](https://sites.math.rutgers.edu/~cherlin/History/Papers2002/turing.html)

[^10-19]: [Turing Machines](https://plato.stanford.edu/entries/turing-machine/)
[^10-20]: [Warren McCulloch and the British cyberneticians](http://sro.sussex.ac.uk/id/eprint/43089/1/McCullochBritCyberneticsV3-final.pdf)
[^10-21]: [Alan Turing](https://plato.stanford.edu/entries/turing/)
[^10-22]: [ON COMPUTABLE NUMBERS, WITH AN APPLICATION TO THE ENTSCHEIDUNGSPROBLEM](https://www.cs.virginia.edu/~robins/Turing_Paper_1936.pdf)

[^10-23]: [LOGICAL CIRCUITS: THE INTELLECTUAL ORIGINS OF THE McCULLOCH–PITTS NEURAL NETWORKS](https://eva.fing.edu.uy/pluginfile.php/103446/course/section/13184/Origins%20McCullock-Pitts.pdf)
[^10-24]: [stored-program computer](https://www.britannica.com/technology/stored-program-concept)
[^10-25]: [Von Neumann architecture in *Wikipedia*](https://en.wikipedia.org/wiki/Von_Neumann_architecture)
[^10-26]: [Universal Turing machine in *Wikipedia*](https://en.wikipedia.org/wiki/Universal_Turing_machine#Stored-program_computer)
[^10-27]: [Modern Computing: A Short History, 1945-2022](https://www.forbes.com/sites/gilpress/2022/04/26/modern-computing-a-short-history-1945-2022/?sh=104b78984332)
[^10-28]: [ENIAC in *Wikipedia*](https://en.wikipedia.org/wiki/ENIAC)
[^10-29]: [Manchester Baby in *Wikipedia*](https://en.wikipedia.org/wiki/Manchester_Baby)
[^10-30]: [The First Modern Computer – The Case for Baby, the Manchester Mk I Prototype （Computer History）](https://learn.saylor.org/mod/book/view.php?id=26579&chapterid=986#:~:text=The%20first%20machine%20to%20successfully,the%20Manchester%20Mk%20I%20Prototype.)
[^10-32]: [Edmund Berkeley in *Wikipedia*](https://en.wikipedia.org/wiki/Edmund_Berkeley)
[^10-33]: [Edmund Berkeley Publishes "Giant Brains," the First Popular Book on Electronic Computers](https://historyofinformation.com/detail.php?id=674)
[^10-34]: [On Thinking Machines, Machine Learning, And How AI Took Over Statistics](https://www.forbes.com/sites/gilpress/2021/05/28/on-thinking-machines-machine-learning-and-how-ai-took-over-statistics/?sh=5c4082232513)
[^10-35]: [COMPUTING MACHINERY AND INTELLIGENCE](https://watermark.silverchair.com/lix-236-433.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAAs0wggLJBgkqhkiG9w0BBwagggK6MIICtgIBADCCAq8GCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQM-NytuzZrWlWhWxjtAgEQgIICgD06RD-2flBuSpnZ5zhvkUVUranRo0reR_6YS2wxVWTwAjHYH3QLqxLSLneyQ2xZlz8tMDyhn6XuVOpUdWgdp5DXonoR48n1dM5uLNaPpG4BNZc3F8cVlHbe4S1KAgYkfr0yxViynRnDXb5-KhjuNJbKA-6VNvrhvBLafhDHJ7txXfLQ9FltmfAnUp9hBgx2nyljjnUqV9hHjb82uAiVVGTIJxnY8pQW6HKW5p69d9NA6qxA6hAtGkqjnTbQHsMbqDmsvxYYF-A-wnoZgIc_sGvFB34llAm49AkqyunWTb5QGsCzUQQh4i_CzweSjoxDT1IWIvA2li9cQudIUBoxX9fzWMhNOj50sQKlWTIidjz8_FgMWbUskGLRcDQWJepyhXQSuEeZUfz-5BraMpDXyyfgy4UqY0UArqrKDxxUJVwyPutXNGBNj8jCwgN3mNIK91N0y3h0YWN0zanDG1IcNQKKU6tCI1tIWEwzZBLUzCjeJ98K25rHhhmcY5qew81eCXw885NYObCvUwAEHK_m7r4YG_klfdnpQXThQyK460HdtwLpAlUd_ySQqIr7a0HVdrO9mj0ZOECzGuuM-2XZDthN_R1_oMaaKUr2VyyipgMkrdOwjonRUNsRPOavdX0W5ek8Tt9uD-HUm2OvL9LVMExA-m29kBLhS2tEXkIRO0f370BEK0s3IGuJNwBgFxDCL859vkB7iBRAyg7WsRnT0nxCLNOfvitBQrJYaGxRJDVi-OaFVZLOB5EN1SNaUlv5U_RztyJqXa9B4rvG8sbSVbY1BfZuJpEB1Rb8wFKBgsPmyAD07wHkUM3M8PvmVJOUvQh4viavLwHYLBFt576Dmec)
[^10-36]: [JOHNNIAC in *Wikipedia*](https://en.wikipedia.org/wiki/JOHNNIAC)
[^10-37]: [Logic Theorist](https://history-computer.com/logic-theorist/)
[^10-38]: [Newell, Simon & Shaw Develop the First Artificial Intelligence Program](https://www.historyofinformation.com/detail.php?id=742)
[^10-39]: [Allen Newell](https://www.britannica.com/biography/Allen-Newell)
[^10-40]: [Logic Theoristと探索木](https://ja.unionpedia.org/c/Logic_Theorist/vs/%E6%8E%A2%E7%B4%A2%E6%9C%A8)
[^10-41]: [A brief history of AI](https://naqviasad86.wixsite.com/asadnaqvi/post/a-brief-history-of-ai)
[^10-42]: [Symbolic artificial intelligence in *Wikipedia*](https://en.wikipedia.org/wiki/Symbolic_artificial_intelligence)
[^10-43]: [The History of Artificial Intelligence](
https://sitn.hms.harvard.edu/flash/2017/history-artificial-intelligence/)
[^10-44]: [A PROPOSAL FOR THE DARTMOUTH SUMMER RESEARCH PROJECT ON ARTIFICIAL INTELLIGENCE](http://jmc.stanford.edu/articles/dartmouth/dartmouth.pdf)
[^10-45]: [Dartmouth Summer Research Project: The Birth of Artificial Intelligence](https://www.historyofdatascience.com/dartmouth-summer-research-project-the-birth-of-artificial-intelligence/)
[^10-46]: [A Proposal for the Dartmouth Summer Research Project on Artificial Intelligence](http://jmc.stanford.edu/articles/dartmouth.html)
[^10-47]: [The MCP Neuron](https://jontysinai.github.io/jekyll/update/2017/09/24/the-mcp-neuron.html)
[^10-48]: [Donald O. Hebb in *Wikipedia*](https://en.wikipedia.org/wiki/Donald_O._Hebb)
[^10-49]: [Symbolic vs Connectionist A.I.](https://towardsdatascience.com/symbolic-vs-connectionist-a-i-8cf6b656927)
[^10-50]: [The Pioneers of AI: Marvin Minsky and the SNARC](https://zahid-parvez.medium.com/history-of-ai-the-first-neural-network-computer-marvin-minsky-231c8bd58409)
[^10-51]: Gugerty L (2006) Newell and Simon’s logic theorist: historical background and impact on cognitive modelling. In: Proceedings of the human factors and ergonomics society annual meeting. Symposium conducted at the meeting of SAGE Publications. Sage, Los Angeles, CA
[^10-52]: [Hebbian Learning](https://thedecisionlab.com/reference-guide/neuroscience/hebbian-learning)
[^10-53]: [The perceptron](https://cs.stanford.edu/people/eroberts/courses/soco/projects/neural-networks/Neuron/index.html)
[^10-54]: [The History and Status of the P versus NP Question](https://dl.acm.org/doi/pdf/10.1145/129712.129771)
[^10-55]: [The Rise In Computing Power: Why Ubiquitous Artificial Intelligence Is Now A Reality](https://www.forbes.com/sites/intelai/2018/07/17/the-rise-in-computing-power-why-ubiquitous-artificial-intelligence-is-now-a-reality/?sh=548777ca1d3f)
[^10-56]: [Turing test in *Wikipedia*](https://en.wikipedia.org/wiki/Turing_test)
[^10-57]:[Universal Turing Machine](https://web.mit.edu/manoli/turing/www/turing.html)

## 3.2. 1957~1980年ごろ: Logic-based AI
本節以降では、AIのアルゴリズムや技術の変遷に注目するため発明者や関係者は割愛する場合がある。
### 1st AI boom
1958年、Connectionist AIの分野では、RosenblattによりPerceptronと呼ばれる単層のニューラルネットワークが発明された。Perceptronは、MPニューロンが0または1の2つの値（ブール値）のみを扱うのに対して、ニューロンの入力に小数点以下を含んだ値を扱うようになり[^20-47]、加えてHebb理論のように前節のSNARC同様に機械が学習する方法も考案された[^20-4] [^20-5] [^20-39]。具体的には、ニューラルネットワークの予測出力と正解の出力（教師データ、Training Data）の差を、**損失関数**（Loss function、Cost function）で**損失**（Loss、Cost、Error）として表し、損失を最小化するようにニューラルネットワークのパラメータを最適化する（**Optimization**）という流れで学習を行った。Rosenblattが用いた学習則（Learning Rule）は、Perceptron Learning Ruleなどと呼ばれる[^20-42] [^20-43] [^20-44]。このように教師データを用いる学習方法は**教師あり学習**（Supervised Learning）と呼ばれ、これに対して教師データを用いないこの頃主流だった学習方法は**教師なし学習**（Unsupervised Learning）と呼ばれるようになっていく。
このように人間がルールを作らずに機械に学習能力を与える研究分野に対して、1959年にArthur Samuelが**Machine Learning**（**機械学習**）という言葉を提唱した[^20-10]。Samuel自身も1952年に[Checkers](https://ja.wikipedia.org/wiki/%E3%83%81%E3%82%A7%E3%83%83%E3%82%AB%E3%83%BC)をプレイするプログラムを作成し[^20-8]（[Alpha-beta pruning](https://lethediana.sakura.ne.jp/tech/archives/uncategorized-ja/2134/)と呼ばれる方法で効率的に戦略を探索させた）、1955年にRot Learningと呼ばれる方式で勝者の戦略を学習可能とし[^20-11]、1959年に当時のベストプレイヤーを打ち負かしている[^20-9]。
この頃、Connectionist AIの発展に必要なことは柔軟で強力な学習ルールであるという認識がされており[^20-46]、1960年にBernard WidrowとMarcian E. HoffによりPerceptronのブール値出力の前に線形関数を加えたモデルであるAdaline（Adaptive Linear Neuron）を[^20-48]、Delta ruleまたはLMS（Least Mean Square） ruleと呼ばれる線形出力をもとに損失を算出し、**GD**（**Gradient Descent**、Batch Gradient Descent、勾配降下）法を用いて損失を最小化する学習則が発表された[^20-45] [^20-49] [^20-50]。また、勾配を計算するためのポイントをランダムに選択する**SGD**（Stochastic Gradient Descent）法も同時期に提案され[^20-52]、Optimizationという分野は損失を最小化する数学的アルゴリズム研究として発展していくことになる。また特にSGD法は今日でも広く用いられており、並列計算が可能なMinibatch GD法や、移動平均処理により損失の振動を抑えたMomentum法など[^20-53]、多くの改善版を生み出す一般的なOptimizerとなっている[^20-51]。これらは、1次の微分項のみを使うためFirst order methodと呼ばれる[^20-54]（Newton法などの高次の微分項を用いた、より高速に収束するOptimization手法も存在したが、計算コストがかかりすぎるため機械学習に用いられることは稀だった[^20-51]）。

> **note**
ニューロンの数学モデルのことをPerceptronと呼ぶこともあり[^10-53]、その場合、MPニューロンが最初のPerceptronとなる。

![Neurons](/images/ai_history/Neurons.png)
*ニューロンモデルの変遷（一部引用:[^20-5]）*

![Supervised Learning Concept](/images/ai_history/supervised_learning.png)
*教師あり学習のコンセプト（一部引用:[^20-58]）*

ただし、この時期のAI研究はSymbolic AIの分野がより大きな盛り上がりを見せていた。
様々な特定のタスクに対するAI（前節のLogic Theoristの場合、定理の証明というタスク）がメインだったが、1959年にAllen NewellとHerbert A. Simonにより**General Problem Solver**（**GPS**）と呼ばれる、一般的なタスクに対応することを意図したAIが発明された[^20-13]。GPSは、到達したい目標へ一足飛びにたどり着けない場合に、目標との差から中間目標を作って徐々に目標に近づく[Means End Analysis](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/2143/)（MEA）と呼ばれる手法を導入しており、GPS以後、MEAはAIに広く利用された[^20-14]。

> **note**
この頃のAIは実際には、論理や幾何学の定理の証明、Chessのような明確に定義された問題にのみ適用可能だったが、他の理論的研究の基礎になっている[^20-12] 。

このようなAI研究の成功に加え、1961年に世界初のICチップが販売[^20-15]（これまでのコンピュータ（IBM704）がメモリ不足だった[^20-16]というAI研究に対するボトルネックを克服するハードウェアの進化）、1965年のムーアの法則[^20-31]、1962年にARPA（Advanced Research Projects Agency、高等研究計画局）にIPTO（Information Processing Techniques Office、情報処理技術局）の設立と[^20-17]、それによるマサチューセッツ工科大学（MIT）、スタンフォード大学（SAIL（Stanford Artificial Intelligence Laboratory）、Stanford HPP（Heuristics Programming Project）等）、カーネギーメロン大学をはじめとするAI研究への投資などにより、AI研究の規模が根本的に変わり、小規模なプロジェクトの集まりから大規模で注目度の高い分野へと推進された[^20-18]。
1965年にはHPPでDENDRAL（DENDRitic ALgorithm）と呼ばれる、化学者が未知の有機分子を特定できるように分子のスペクトル分析を行い構造を示すAIの開発が開始された[^20-19]。SAILのコンピュータPDP-6で作成されたプログラムであり、分子を構成する原子の情報や、探索の優先度など化学者の知識をあらかじめ組み込み、それらを利用して質量分析を行うことができる[^20-21] [^20-22]（プログラムの構成等については[こちら](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/2154/)も参照ください）。**DENDRAL**はルールベースで（ゲーム等ではない）現実の問題のために作られたプログラムであると言われる[^20-20]。次節で述べるが、DENDRALはこの後も開発が継続される。
また、1966年にはMITのMAC time-sharingシステム上で**ELIZA**という自然言語処理のAIプログラムが開発された[^20-25]。GUIを持ち、ユーザーの入力からキーワードやフレーズを認識して事前にプログラムされたフレーズからユーザーへの応答を行うため、世界初のChatbotと称されている[^20-23]。プログラム内では、If-thenルールを用いた、単純なパターンマッチングを行っており、膨大な数の会話パターンを事前に用意しておかなければならなかったが[^20-24]、Rogerian療法のセラピストとして応対するバージョン（DOCTOR）で有名になった[^20-26] [^20-27]。

その他、自らの行動を推論できる初の汎用移動ロボットであるShakey the robotや[^20-28]、世界初のPlannningシステムであるSTRIPS（STanford Research Institute Problem Solver）等も[^20-29] [^20-30]、この頃のAIの例として挙げられるが、詳細は割愛する。

> **note**
AIの研究としてではないが、下記の2つも後に重要となる。
1963年、James MorganとJohn Sonquistにより、学歴と年収などのデータの関係性をを分析（**回帰分析**）するために、数値的な基準を設けてデータを2つに分けることを繰り返してグループ分けを行う、後にAID（Automatic Interaction Detection）と呼ばれる手法が発表された[^20-56] [^20-57]。そして、1972年にはそれをカテゴリ分類へ拡張させたTHAID（THeta Automatic Interaction Detection）と呼ばれる手法も発表された。これらのようにデータを木の枝状に分割していく分析手法は**回帰木**（**Regression Tree**）および**分類木**（**Classification Tree**）、またはそれらをまとめてCART（Classification And Regression Tree）と称され、今日でも発展を続けている。

### 1st AI Winter
前節のような盛り上がりを見せたAI研究も、1960年代後半ごろから冬の時代が訪れた。
Rosenblattに発明されたPerceptronは2種類かつ比較的単純な分類タスク（厳密には、線形分離可能なタスク）にしか対応できないことがわかり[^20-3]、1969年に出版された*Perceptrons: an introduction to computational geometry*という書籍で単純な論理XOR関数を学習できないことを示されるなど[^20-6]、非常に厳しい目を向けられることとなった。またこの頃の多くの研究者が、1965年頃から使われだした**強化学習**（Try and Errorで学習していく方法）に取り組んでいるつもりが、教師あり学習になってしまうケースが多発するなどの混乱もあり、学習アルゴリズムにフォーカスした研究が多くなかった[^20-38]。John AndreaeがSTeLLA（Standard Telecommunication Laboratories[^20-37]）という環境からtrial and errorで学習を行う（後の強化学習）システムを発明しても注目度が上がらない[^20-36]、**次元の呪い**の提唱など[^20-55]、Connectionist AIや機械学習の分野は下火になっていた。
そして、1969年のマンスフィールド修正案により、ARPAの後身となるDARPA（Defense Advanced Research Projects Agency）の投資対象を、基礎研究ではなく具体的な目的をもった研究を重視するように大きく変更された[^20-35]。
それに加え、1973年にScience Research Council（イギリスの科学研究評議会）に向けてAI研究の評価を行ったLighthill reportで、航空機の自動着陸システムがAIよりも従来手法の方が優れていること、AIプログラムの作りこみが難しいこと、組み合わせ爆発問題が起こること等に注目し、AI研究に対して悲観的な見解を示した[^20-32] [^20-33] [^20-34]。
このような流れもあって資金の確保が難しくなり、AI研究の勢いは次第に失速した。AIへの期待は、人間の脳のような柔軟性や汎用性をもってほしいという究極の知性よりも、特定の分野であってもより現実的な問題の解決へと移っていった。

[^20-3]:[The Perceptron: A Perceiving and Recognizing Automaton (Project PARA)](https://blogs.umass.edu/brain-wars/files/2016/03/rosenblatt-1957.pdf)
[^20-3]:[Perceptrons_book in *Wikipedia*](https://en.wikipedia.org/wiki/Perceptrons_(book))
[^20-4]:[Neural Networks: Why Does the Perceptron Rule Only Work for Linearly Separable Data?](https://saturncloud.io/blog/neural-networks-why-does-the-perceptron-rule-only-work-for-linearly-separable-data/)
[^20-5]: [The Rosenblatt’s Perceptron](https://maelfabien.github.io/deeplearning/Perceptron/#)
[^20-6]: [Rosenblatt’s perceptron, the first modern neural network](https://towardsdatascience.com/rosenblatts-perceptron-the-very-first-neural-network-37a3ec09038a)
[^20-7]: [Arthur Samuel: Pioneer in Machine Learning](https://www.researchgate.net/publication/224103556_Arthur_Samuel_Pioneer_in_Machine_Learning)
[^20-8]: [Checkers Research Page](https://www.cs.nott.ac.uk/~pszgxk/games/checkers/research.html)
[^20-9]: [The Rise and Fall of Symbolic AI](https://towardsdatascience.com/rise-and-fall-of-symbolic-ai-6b7abd2420f2)
[^20-10]: [Arthur Samuel (computer scientist) in *Wikipedia*](https://en.wikipedia.org/wiki/Arthur_Samuel_(computer_scientist))
[^20-11]: [11.2 Samuel's Checkers Player](http://incompleteideas.net/book/ebook/node109.html)
[^20-12]: [General Problem Solver (A. Newell & H. Simon)](https://www.instructionaldesign.org/theories/general-problem-solver/)
[^20-13]: [Report on a general problem-solving program](http://bitsavers.informatik.uni-stuttgart.de/pdf/rand/ipl/P-1584_Report_On_A_General_Problem-Solving_Program_Feb59.pdf)
[^20-14]: [Newell, Allen](encyclopedia.com/people/science-and-technology/computers-and-computing-biographies/allen-newell)
[^20-15]: [Vintage Computer Chip Collectibles, Memorabilia & Jewelry](https://www.chipsetc.com/fairchild-semiconductor.html)
[^20-16]: [**Building the Second Mind, 1961-1980: From the Ascendancy of ARPA to the Advent of Commercial Expert Systems**](https://escholarship.org/content/qt82h464gg/qt82h464gg_noSplash_0c64963f432723c12a0e1656888b8558.pdf?t=mnaxni)
[^20-17]: [DARPA's Impact on Artificial Intelligence](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/5294/7228)
[^20-18]: [Developments in Artificial Intelligence](https://nap.nationalacademies.org/read/6323/chapter/11#204)
[^20-19]: [DENDRAL: a case study of the first expert system for scientific hypothesis formation](https://web.mit.edu/6.034/www/6.s966/dendral-history.pdf)
[^20-20]: [An analysis on the dendral expert system](https://www.grin.com/document/213082)
[^20-21]: [Buchanan, Bruce & Feigenbaum, E.A. & Lederberg, J.. (1968). Heuristic DENDRAL: A program for generating explanatory hypotheses in organic chemistry. Machine Intelligence. 4. ](https://www.researchgate.net/publication/23622692_Heuristic_DENDRAL_A_program_for_generating_explanatory_hypotheses_in_organic_chemistry)
[^20-22]: [DENDRAL and Meta-DENDRAL roots of knowledge systems and expert system applications](https://stacks.stanford.edu/file/druid:rv258md4469/rv258md4469.pdf)
[^20-23]: [Story of ELIZA, the first chatbot developed in 1966](https://analyticsindiamag.com/story-eliza-first-chatbot-developed-1966/)
[^20-24]: [Natural Language Processing](https://www.inf.ed.ac.uk/teaching/courses/il1/slides/19-nlp2-2011-11-15.pdf)
[^20-25]:[ELIZA A Computer Program For the Study of Natural Language Communication Between Man And Machine](https://web.stanford.edu/class/cs124/p36-weizenabaum.pdf)
[^20-26]: [ELIZA: a very basic Rogerian psychotherapist chatbot](https://web.njit.edu/~ronkowit/eliza.html)
[^20-27]: [The computational therapeutic: exploring Weizenbaum’s ELIZA as a history of the present](https://link.springer.com/article/10.1007/s00146-018-0825-9)
[^20-28]: [Remembering Shakey, the First Intelligent Robot](https://thenewstack.io/remembering-shakey-first-intelligent-robot/)
[^20-29]: [Blocks World Example](http://www-formal.stanford.edu/jsierra/my-web-page/nmr-98/heuristics-ac/node2.html)
[^20-30]: [Artificial Intelligence Planning STRIPS](https://u.cs.biu.ac.il/~haimga/Teaching/AI/lessons/lesson7.pdf)
[^20-31]: [What Is Moore’s Law and How Does It Impact AI ?](https://www.unite.ai/moores-law/)
[^20-32]: [Artificial Intelligence: A General Survey](https://rodsmith.nz/wp-content/uploads/Lighthill_1973_Report.pdf)
[^20-33]:[Review of ``Artificial Intelligence: A General Survey''](https://www-formal.stanford.edu/jmc/reviews/lighthill/lighthill.html)
[^20-34]:[Lighthill report in *Wikipedia*](https://en.wikipedia.org/wiki/Lighthill_report)
[^20-35]:[Ai Winter](https://academic-accelerator.com/encyclopedia/ai-winter)
[^20-36]:[Reinforcement Learning: An Introduction](https://inst.eecs.berkeley.edu/~cs188/sp20/assets/files/SuttonBartoIPRLBook2ndEd.pdf)
[^20-37]:[1962-6 – “STELLA” CYBERNETIC TORTOISE – JOHN H. ANDREAE AND PETER L. JOYCE (BRITISH)](https://cyberneticzoo.com/cyberneticanimals/1962-6-stella-cybernetic-tortoise-john-h-andreae-and-peter-l-joyce-british/)
[^20-38]: [1.6 History of Reinforcement Learning](http://incompleteideas.net/book/ebook/node12.html)
[^20-39]: [The History of Neural Networks Part 2: Rosenblatt's Perceptron](https://www.linkedin.com/pulse/history-neural-networks-part-2-rosenblatts-perceptron-dr-kais-dukes/)
[^20-40]: [Stochastic gradient descent in *Wikipedia*](https://en.wikipedia.org/wiki/Stochastic_gradient_descent/)
[^20-41]:[Optimization: Stochastic Gradient Descent](http://deeplearning.stanford.edu/tutorial/supervised/OptimizationStochasticGradientDescent/)
[^20-42]:[The Math behind Neural Networks: Part 1 - The Rosenblatt Perceptron](https://www.codeproject.com/Articles/4047091/The-Math-behind-Neural-Networks-Part-1-The-Rosenbl#the-heaviside-step-function)
[^20-43]:[Frank Rosenblatt’s Perceptron, Birth of The Neural Network](https://medium.com/@robdelacruz/frank-rosenblatts-perceptron-19fcce9d627f)
[^20-44]:[PHYS 139/239: Machine Learning in Physics Lecture 2: Perceptron Learning Algorithm & (Stochastic) Gradient Descent](https://jduarte.physics.ucsd.edu/phys139_239/lectures/02_Perceptron_SGD.pdf)
[^20-45]:[Adaptive sampled-data systems](https://www-isl.stanford.edu/~widrow/papers/c1960adaptiveswitching.pdf)
[^20-46]:[A Basic Introduction to Feedforward Backpropagation Neural Networks (after Leverington, 2001)](http://www.webpages.ttu.edu/dleverin/neural_network/neural_networks.html)
[^20-47]:[McCulloch-Pitts Neuron vs Perceptron model](https://medium.com/@manushaurya/mcculloch-pitts-neuron-vs-perceptron-model-8668ed82c36)
[^20-48]:[An adaptive "ADALINE" neuron using chemical "memistors"](https://www-isl.stanford.edu/~widrow/papers/t1960anadaptive.pdf)
[^20-49]:[Single-Layer Neural Networks and Gradient Descent](https://sebastianraschka.com/Articles/2015_singlelayer_neurons.html#adaptive-linear-neurons-and-the-delta-rule)
[^20-50]:[The ADALINE - Theory and Implementation of the First Neural Network Trained With Gradient Descent](https://pabloinsente.github.io/the-adaline)
[^20-51]:[A Survey of Optimization Methods from a Machine Learning Perspective](https://arxiv.org/pdf/1906.06821.pdf)
[^20-52]:[A Stochastic Approximation Method](https://projecteuclid.org/journals/annals-of-mathematical-statistics/volume-22/issue-3/A-Stochastic-Approximation-Method/10.1214/aoms/1177729586.full)
[^20-53]:[Some methods of speeding up the convergence of iteration methods](https://www.mathnet.ru/php/archive.phtml?wshow=paper&jrnid=zvmmf&paperid=7713&option_lang=eng)
[^20-54]:[Stochastic Optimization: First order method](https://ibis.t.u-tokyo.ac.jp/suzuki/lecture/2015/nagoya_intensive/Nagoya2015_2_FirstOrder.pdf)
[^20-55]:[CONSEQUENCES OF THE HUGHES PHENOMENON ON SOME CLASSIFICATION TECHNIQUES](https://www.asprs.org/wp-content/uploads/2010/12/Alonso.pdf)
[^20-56]:[PROBLEMS IN THE ANALYSIS OF SURVEY DATA, AND A PROPOSAL](http://cda.psych.uiuc.edu/statistical_learning_course/morgan_sonquist.pdf)
[^20-57]:[Fifty Years of Classification and Regression Trees](https://pages.stat.wisc.edu/~loh/treeprogs/guide/LohISI14.pdf)
[^20-58]:[Deep Learning Neural Network Algorithm for Computation of SPICE Transient Simulation of Nonlinear Time Dependent Circuits](https://www.mdpi.com/2079-9292/11/1/15)

## 3.3. 1980~1993ごろ：Knowledge-based AI
### 2nd AI boom
前述したDENDRALの研究は、対象とする化学構造の拡大を目指すDendral Project、化学的知識活用の向上を目指すMetaDendral Project、さらなる一般化を目指す[Mycin](https://en.wikipedia.org/wiki/Mycin) Projectに分化するなどして継続されていた[^30-6]。開発当初の検索ベースのアルゴリズム（* Boolean logic and logical reasoning, deterministic model*[^30-10]）で専門家レベルの能力をもったAIとはいかなかったが、「プログラムが問題解決を行うためには（従来重視されていた推論方法よりも）知識が重要である[^30-7]」という考え方に基づいており、これはKnowledge-is-power仮説（後のKnowledge principle）と呼ばれる[^30-5]。専門知識を持つ人間がExpertと称されたことから[^30-8]、このような知識と問題解決方法が分けられた構造を持ちそれぞれ別の開発者（専門知識を持つ人、プログラムを作成する人）が担当できるプログラムを**Expert System**（または**Knowledge based System**）[^30-9]、知識を体系化する取り組みはKnowledge Engineeringと呼ばれるようになった[^30-5]。このような構造をとることにより、プログラマーが必ずしも専門知識を習得したり、専門知識を持つ人がプログラミングを習得する必要がなくなったことが大きな功績の一つといえる[^30-10]。
一方、この頃ICも着々と集積化を進める。1960年代前半にSSI（Small-Scale Integration）レベル、1960年代後半にMSI（Medium-Scale Integration）レベル、1970年代中盤にはLSI（Large-Scale Integration）レベルへ、そして1971年に初のマイクロプロセッサ（Central Processing Unit: CPUとも呼ばれる）Intel 4004が発明されるなど、ムーアの法則通り集積度を上げ、コンピュータの小型化と計算能力向上が順調に進んだ[^30-1] [^30-2]（各レベル詳細は割愛）。それによりMinicomputer（MC）と呼ばれる中規模のコンピュータ（現在の「サーバー」規模のコンピュータ）が市場に出始めることとなった[^30-3]。Minicomputerは企業で大量に購入され、それによりドキュメントが増加、それらを整理・参照するツールの需要が高まった[^30-4]。

> ![Block diagram of Expert System](https://static.javatpoint.com/tutorial/ai/images/expert-systems-in-ai.png)
*Block diagram of Expert System（引用:[^30-59]）*

このような状況の中、1978年にCMUの研究者が、MiniconputerのベンダーであるDECのコンピュータ構成業務をアシストするためのXCON（eXpert CONfigurator）と呼ばれるシステムを開発した[^30-11]。1982年に導入後、年に4000万ドルのコストダウンがされたとされ、AIが産業界で本格的に用いられる例となった[^30-12] [^30-13]。
AIに取り組む研究者の関心がExpert Systemに向いているこの頃、さらに複雑なタスクに対応するため、これまでの常識であったSymbolを用いた決定論的アプローチだけでなく、不確実性・数値を用いた確率的アプローチも注目されるようになってきた[^30-14] [^30-15]。初期の例は、Certainly factorを用いたMYCIN（1975年）[^30-18]、Bayesの定理を用いたPROSPECTOR（1978年）[^30-19]、Fuzzy論理を用いたCADIAG-2（1980年）[^30-17]などが挙げられ、実用的かつ知的レベルの高いAIを目指した取り組みが盛んに行われた。
このようなExpert Systemの発展に伴い、IBMを追い越そうと日本の通商産業省所管の新世代コンピュータ技術開発機構（ICOT：Institute for New Generation Computer Technology）で、国家プロジェクトとして第五世代コンピュータ（FGCS：the Fifth Generation Computer Systems）プロジェクトを推進し[^30-21]、1982年ごろから4億ドルを超える大規模な投資を行った[^30-22]。これに伴い、米国DARPAがSCI（Strategic Computing Initiative）を開始、英国ではAlveyプロジェクトが発足する等、FGCSは海外にも大きな影響を与えた[^30-20]。
1984年に*CART: Classification and Regression Trees.*という研究論文が発表されて以降、CARTを含んだ樹形図を用いてデータを分析するための機械学習アルゴリズムである**決定木**（**Decision Tree**、樹形図自体を決定木と呼ぶ場合もある）に関する研究が活発になった[^30-56]。1986年には、Expert Systemが推論を行うためのルール生成のために機械学習が重要であるとし田植えで、ID3（Iterative Dichotomiser 3）と呼ばれる決定木が開発された[^30-55]。これまでのCARTが各ノードが2種類の分類を行う木（Binary Tree）を想定していたところを、複数種類に分類できる木（Binary Treeに対してGeneral Tree）に対応するなど[^30-57]、ID3は決定木における大きなブレイクスルーとなっている[^30-58]。
基本的にはSymbolic AIの分野でExpert Systemがこのような盛り上がりを見せる一方、Connectionist AIの分野でも大きな進歩があった。
Perceptronを持ちいた階層型のニューラルネットワーク構造を用いたAIは、1979年にNeocognitronと呼ばれるニューラルネットワークが考案され、手書き文字の認識を成功させたことで、AIによる画像のパターン認識が可能であることを示した[^30-23]。Neocognitronは、スライディングウインドウ処理を用いて、画像の中の位置に関わらずパターンを検出することのできる構造であり[^30-24] [^30-25]、後のCNN（Convolution Neural Network、畳み込みニューラルネットワーク）に非常に大きな影響を与えることとなる。
また、ニューロンが相互接続する構造のニューラルネットワークもこの頃発明される。1982年のHopfield networkは、強磁性体による磁場の説明に用いられるIsingモデルに基づいて考案されたニューラルネットワークで[^30-27]、0または1を出力するニューロンが相互に接続されており、パターンを記憶してその情報を利用することができるようになっている[^30-26]。実際には計算効率が悪く非現実的であったが、後のRNN（Recurrent Neural Network）に大きなインスピレーションを与えた[^30-28]。また1985年には、ニューロンの出力を確率的にした制限付きボルツマンマシンが発明されている[^30-30]。
そして教師あり学習の方法について、1986年にDavid Rumelhart、Geoffrey Hinton、Ronald Williamsの論文[^30-31]で発表された**BP**（**Backpropagation、誤差逆伝搬**）**法**が有効であることが示された。BP法により、教師あり学習において教師データとニューラルネットワークの出力の誤差を、逆伝搬させてネットワークが持つパラメータを調整する（誤差が大きいほどパラメータを大きく調整する）ことができ[^30-32]、広く使われるようになった（BP法の基本コンセプトが発明されたのは厳密には1961年とされるが詳細は割愛）[^30-33]。
同1986年、NETTalkという文字から音素（音の最小単位）への変換が可能なニューラルネットワークが発表された。後の一般的なニューラルネットワークのように入力層-隠れ層-出力層という3層の構造を持ち[^30-29]、学習則にはBP法とSGDが用いられ[^20-40]、英語のテキストを読み上げることが可能であることを示した。同様のタスクにExpert Systemで取り組み（読み上げ精度は高いものの）数年間かかったDECtalkと比べて、ニューラルネットワークを用いたモデルは開発期間が短いことを示した[^30-34]。
1989年に発表された論文内での分類用の弱い学習ツール（weak learner）を変換して強力な学習ツール（strong learner）にもできるかどうかという議論から[^30-53] [^30-54]、1990年に同一タスクに対して複数のニューラルネットワークで学習および推定を行い、最終的な出力値を決定する**アンサンブル学習**（**Ensemble Learning**）という手法により、ニューラルネットワークの汎化パフォーマンスを向上できることが示され[^30-50] [^30-51]、これ以降の機械学習研究の中心にアンサンブル学習も存在することとなった[^30-52]。

### 2nd AI Winter
1980年以降に期待されたExpert Systemは、実は1984年にAIの先駆者であるJohn McCarthyに批判されている。主な批判内容は、Expert Systemのプログラム変更が容易でなく変化に対応しづらいこと、人が当たり前に持っている常識的な知識をAIが持っていないため意思決定が不適切になりうること、の2つである[^30-37]。さらに、実際に専門家の知識をルール化することが非常に難しい場合が目立ってきた[^30-39]。すなわち、Expert Systemは構造化されたデータとルール化可能な論理があって初めて可能であり、自然言語や画像等の（曖昧な）データを取り扱うことが困難だった[^30-49]。1987年から1989年にかけてDARPAのISTO (Information Science and Technology Office)には、Expert Systemが非常に限定的な領域でしか成功していない、と結論付けられている[^30-38]。
また、マイクロプロセッサが開発されてから個人で利用するPC（Personal Computer）が低コスト化していった[^30-46]。それに伴い、1987年までにC言語等のコンパイル言語を扱うOSを搭載したAppleやIBMのPCが流通し、多くのExpert Systemが実行されていたLISPマシンのそれを上回ったにも関わらず、コンパイル言語にExpert Systemの開発にマッチしなかったとされている[^30-39]。
そして1980年代後半から、特に機械学習による教師あり学習の性能が注目されてきたが、教師データが十分にとれないことや[^30-43]、BP法による学習に時間がかかる点が問題として認識され[^30-42]、コンピュータの性能向上が期待された。
また最適化の問題点として、複雑な処理に対応しようとニューラルネットワークを多層にすればするほど、損失関数の勾配が指数関数的に変化するため、0に近づきやすくなりBP法での学習が困難になる（ニューラルネットワークの重みが更新されない）という問題（勾配消失問題）が1991年に提唱され[^30-40] [^30-41]、逆に無限大に発散してしまい学習が困難になる問題（勾配爆発問題）が1994年に提唱された[^30-44] [^30-45]。
経済的にも1987年にDARPAはAIに対する投資を中止[^30-13]、1992年に目標をほとんど達成することなくFGCSは正式に終了しており[^30-47]、研究者は学術界や企業からの排斥を恐れて、意図的にAIという用語の使用を避けはじめた（代わりに、機械学習、データ分析、Intelligent System、Big Data、Data scienceといった単語を利用した）[^30-48]。

[^30-1]: [Moore’s Law and Exponential Growth](https://pdhacademy.com/wp-content/uploads/2022/01/Moores-Law-and-Exponential-Growth-course-for-website.pdf)
[^30-2]: [HISTORY OF INTEGRATED CIRCUIT OR IC](https://pijaeducation.com/basic-electronics/embedded-system/history-of-integrated-circuit-ic/)
[^30-3]: [Minicomputers: history, characteristics, uses, examples](https://warbletoncouncil.org/minicomputadoras-14120)
[^30-4]: [History of artificial intelligence: expert systems and AI winters](https://blog.pigro.ai/en/expert-systems)
[^30-5]: [Expert systems](https://dl.acm.org/doi/pdf/10.5555/1074100.1074389)
[^30-6]: [Dendral and Meta-Dendral](https://stacks.stanford.edu/file/druid:xp200rt1512/xp200rt1512.pdf)
[^30-7]: [Feigenbaum, E. A. “The Art of Artificial Intelligence: Themes and Case Studies of Knowledge Engineering,” Proceedings of the International Joint Conference on Artificial Intelligence. Cambridge, MA: MIT Press.]
[^30-8]: [Feigenbaum, E. A., Buchanan, B. G., and Lederberg, J. “On Generality and Problem Solving: A Case Study Using the DENDRAL Program,” in Machine Intelligence]
[^30-9]: [EXPERT SYSTEMS ](https://www.eolss.net/sample-chapters/c15/E6-44-03-04.pdf)
[^30-10]: [Jerry Kaplan, Artificial Intelligence: What Everyone Needs to Know]()
[^30-11]:[XCON](https://aithefuture.wordpress.com/2018/05/08/xcon/)
[^30-12]:[History of Artificial Intelligence (AI) and How it has evolved](https://kusham1998.medium.com/history-of-artificial-intelligence-ai-and-how-it-has-evolved-3d7607e1fff8#)
[^30-13]: [AI History: the 1980s and expert systems](https://www.klondike.ai/en/ai-history-the-1980s-and-expert-systems/)
[^30-14]: [Probability Judgment in Artificial Intelligence and Expert Systems](https://projecteuclid.org/journals/statistical-science/volume-2/issue-1/Probability-Judgment-in-Artificial-Intelligence-and-Expert-Systems/10.1214/ss/1177013426.full)
[^30-15]: [The place of fuzzy logic in AI](https://hal.science/hal-04013770/document)
[^30-16]: [Bayesian Analysis in Expert Systems](https://projecteuclid.org/journals/statistical-science/volume-8/issue-3/Bayesian-Analysis-in-Expert-Systems/10.1214/ss/1177010888.full)
[^30-17]:[CADIAG: APPROACHES TO COMPUTER-ASSISTED MEDICAL DIAGNOSIS](https://www.meduniwien.ac.at/kpa/publications/1985_CIBAM_--_CADIAG_-_Approaches_to_Computer-Assisted_Medical_Diagnosis.pdf)
[^30-18]: [A Model of Inexact Reasoning in Medicine](https://stacks.stanford.edu/file/druid:ts764ph5106/ts764ph5106.pdf)
[^30-19]: [PROSPECTOR: A Computer-Based Consultation System For Mineral Exploration](https://www.sri.com/publication/artificial-intelligence-pubs/prospector-a-computer-based-consultation-system-for-mineral-exploration/)
[^30-20]: [第五世代コンピュータから考える AI プロジェクト](https://www.jstage.jst.go.jp/article/jjsai/29/2/29_115/_pdf)
[^30-21]: [第五世代コンピュータ in *Wikipedia*](https://ja.wikipedia.org/wiki/%E7%AC%AC%E4%BA%94%E4%B8%96%E4%BB%A3%E3%82%B3%E3%83%B3%E3%83%94%E3%83%A5%E3%83%BC%E3%82%BF)
[^30-22]: [Artificial Intelligence in Japan (R&D, Market and Industry Analysis)](https://www.eu-japan.eu/sites/default/files/artificial_intelligence_in_japan.pdf)
[^30-23]: [多層神経回路ネオコグニトロンの学習](https://www.jstage.jst.go.jp/article/fss/30/0/30_318/_pdf)
[^30-24]: [A Brief History of Deep Learning](https://www.dataversity.net/brief-history-deep-learning/)
[^30-25]: [畳み込みニューラルネットワーク](https://ml4a.github.io/ml4a/jp/convnets/)
[^30-26]: [Neural networks and physical systems with emergent collective computational abilities](https://www.pnas.org/doi/epdf/10.1073/pnas.79.8.2554)
[^30-27]: [Hopfield Networks: Neural Memory Machines](https://towardsdatascience.com/hopfield-networks-neural-memory-machines-4c94be821073)
[^30-28]: [Computation by neural networks](https://www.nature.com/articles/nn1100_1170)
[^30-29]:[NETtalk: a parallel network that learns to read aloud](https://papers.cnl.salk.edu/PDFs/NETtalk_%20A%20Parallel%20Network%20That%20Learns%20to%20Read%20Aloud%201988-3562.pdf)
[^30-30]: D. H. Ackley, G. E. Hinton, and T. J. Sejnowski. A learning algorithm for Boltzmann machines. Cognitive Science, pages 147–169, 1985.
[^30-31]: [Learning representations by back-propagating errors](https://www.iro.umontreal.ca/~vincentp/ift3395/lectures/backprop_old.pdf)
[^30-32]: [Solving the Mystery of Backpropagation](https://towardsdatascience.com/solving-the-mystery-of-backpropagation-73b18cae8e40)
[^30-33]:[Back Propagation in Neural Network: Machine Learning Algorithm](https://www.guru99.com/backpropogation-neural-network.html)
[^30-34]:[5.3 Applications 5.3.1 NETtalk](https://neuron.eng.wayne.edu/tarek/MITbook/chap5/5_3.html)
[^30-35]:[LeNet: 最初のCNN構造](https://cvml-expertguide.net/terms/dl/cnn/cnn-backbone/lenet/)
[^30-36]:[Backpropagation Applied to Handwritten Zip Code Recognition](http://yann.lecun.com/exdb/publis/pdf/lecun-89e.pdf)
[^30-37]:[SOME EXPERT SYSTEM NEED COMMON SENSE](https://www-formal.stanford.edu/jmc/someneed/someneed.html)
[^30-38]:[History of the Second AI Winter](https://towardsdatascience.com/history-of-the-second-ai-winter-406f18789d45)
[^30-39]:[AI Watch Historical Evolution of Artificial Intelligence](https://publications.jrc.ec.europa.eu/repository/bitstream/JRC120469/jrc120469_historical_evolution_of_ai-v1.1.pdf)
[^30-40]:[Gradient amplification: An efficient way to train deep neural networks](https://ieeexplore.ieee.org/document/9142152)
(https://ml.jku.at/publications/older/ch7.pdf)
[^30-41]:[The Vanishing Gradient Problem](https://towardsdatascience.com/the-vanishing-gradient-problem-69bf08b15484)
[^30-42]:[Symbolic and Neural Learning Algorithms: An Experimental Comparison](https://link.springer.com/content/pdf/10.1023/A:1022602303196.pdf)
[^30-43]:[THE IMPACT OF ARTIFICIAL INTELLIGENCE ON THE FUTURE OF WORKFORCES IN THE EUROPEAN UNION AND THE UNITED STATES OF AMERICA](https://www.whitehouse.gov/wp-content/uploads/2022/12/TTC-EC-CEA-AI-Report-12052022-1.pdf)
[^30-44]:[Exploding gradient problem](https://golden.com/wiki/Exploding_gradient_problem)
[^30-45]:[Learning long-term dependencies with gradient descent is difficult](http://www.comp.hkbu.edu.hk/~markus/teaching/comp7650/tnn-94-gradient.pdf)
[^30-46]:[History of personal computers in *Wikipedia*](https://en.wikipedia.org/wiki/History_of_personal_computers)
[^30-47]: [2 AI winters and 1 hot AI summer](https://www.entefy.com/blog/2-ai-winters-and-1-hot-ai-summer/)
[^30-48]:[TWO WINTERS AND A SPRING OF ARTIFICIAL INTELLIGENCE](https://medium.com/qed-software/two-winters-and-a-spring-of-artificial-intelligence-71a9901df77d)
[^30-49]:[The History of Artificial Intelligence from the 1950s to Today: The Emergence of NLPs and Computer Vision in the 1990s](https://www.freecodecamp.org/news/the-history-of-ai/#the-emergence-of-nlps-and-computer-vision-in-the-1990s)
[^30-50]:[Neural Network Ensembles](https://www.researchgate.net/publication/3191841_Neural_Network_Ensembles)
[^30-51]:[The strength of weak learnability](https://link.springer.com/article/10.1007/BF00116037)
[^30-52]:[Ensemble learning](http://www.scholarpedia.org/article/Ensemble_learning#History)
[^30-53]:[Cryptographic Limitations on Learning Boolean Formulae and Finite Automata](https://www.cis.upenn.edu/~mkearns/papers/crypto.pdf)
[^30-54]:[The Evolution of Boosting Algorithms From Machine Learning to Statistical Modelling](https://arxiv.org/pdf/1403.1452.pdf)
[^30-55]:[Induction of decision trees](https://hunch.net/~coms-4771/quinlan.pdf)
[^30-56]:[CART: Classification and Regression Trees](https://vincentqin.gitee.io/blogresource-2/cv-books/10-CART.pdf)
[^30-57]:[The Complete Guide to Decision Tree Analysis](https://www.explorium.ai/blog/machine-learning/the-complete-guide-to-decision-trees/)
[^30-58]:[Decision Tree History](https://holypython.com/dt/decision-tree-history/)
[^30-59]:[Expert Systems in Artificial Intelligence](https://www.javatpoint.com/expert-systems-in-artificial-intelligence)

## 3.4. 1993~2012年ごろ：Machine Learning
前述したExpert Systemが困難だった非構造化データ、非線形データを取り扱うため、機械学習技術（特にキーとなったのが決定木、BP法である[^40-76]）がより注目され始める。ただし機械学習研究が盛り上がった初期は、信頼性のあるデータが少なくハードウェアリソースの限界もあり研究の再現性がとれないこと、出力の説明性が乏しいことなどから、比較的教師データが少なくても性能を発揮し、理論保障が可能な数学・統計的なアプローチが主流だった[^40-1] [^40-2] [^40-3]。
例えば自然言語処理（NLP: Natural Language Processing）のタスクに対しては、1990年代に**N-gram言語モデル**と呼ばれる、文章内で次にどの単語がくるかの確率を表したようなモデルの使用が、機械翻訳システムで一般的になり、その後NLPの他の分野にも拡張されたことと合わせて[^40-4]、系列データを扱うのに長けている**隠れマルコフモデル**（**HMMs: Hidden Markov Models**）が広く利用された[^40-5]。例
そして、パターン認識・分類・回帰のタスクに対しては、非線形データ解析の手法であるカーネル法をベースとして1992年に**サポートベクトルマシン**（**SVM: Support Vector Machine**）が提案された[^40-6]。SVMはデータを（基本的には2つの）クラスに分類するとき、可能な限り各クラスが大きく分離されるような平面（MMSH: Maximum Margin Separating Hyperplane）を見つけるアルゴリズムであり[^40-7]、比較的メモリ効率が良く小さなデータセットに向いていたため、手書き文字画像の認識等に用いられた[^40-8] [^40-9]。
この頃、ラベル付きデータとラベルなしデータの両方を学習に用いる**半教師あり学習**（Semi-supervised learning）という手法も普及しだし[^40-60] [^40-61]、学習データの取り扱いの幅も広がってきたといえる。

一方で大規模なデータセットや強力なコンピューティングリソースが必要であるニューラルネットワークの分野は、1994年に**MNIST**（Modified National Institute of Standards and Technology）という学習用に6万、テスト用に1万枚の手書き数字画像を含むデータセットが作成され[^40-13]、翌1995年にLeNetと呼ばれるニューラルネットワークを有するAIが手書き数字画像の分類精度において、SVMを含むその他のアプローチの結果を上回ることが示された[^40-15]（LeNetの研究は1989年ごろから始まっていた[^30-36]）。LeNetはCNN構造をもっており、畳み込み処理に学習可能なパラメータをもたせることでパラメータ・計算の削減に成功した点が重要であり、今後のニューラルネットワーク研究の基盤となっている[^40-14]。
そしてこの1995年には、Windows95・Internet Explorerの発表によりPCとインターネットが多くの人の身近に届いたことで[^40-16] [^40-17]、コンピュータが情報を得やすくなり、大きなデータセットの共有も現実的なものになった。
CNNの他にも、Hopfield networkを拡張した[^40-18]、**LSTM**（Long-Short Time Memory）と呼ばれるRNNが1997年に発表された。LSTMはネットワーク内にMemoryセルと呼ばれる単位で、情報の記憶と忘却を調整することで、RNNで問題となっていた勾配爆発を解決した[^40-20] [^40-21]。さらに、GNN（Graph Neural Network）という[グラフ](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/1367/)を入出力とするリッチなデータ構造に機械学習を用いる構造が発表された[^40-58] [^40-59]。

> **note**
LSTMの元論文にはメモリーセルが情報をforgetするとは書かれていない[^40-19]

そして、アンサンブル学習の研究でも、Weak learnerにより学習された複数の分類機を、並列に実行して出力結果を集約（Aggregation）する**Bagging**（Bootstrap Aggregating、1996年[^40-70]）や、直列に結合して一つの強力な分類機を得る**Boosting**（1990年[^30-51]、1995年[^40-72]）といった、主流となる手法が確立された。
これらを元としたアルゴリズムとして、複数の決定木を用いたBaggingに特徴選択プロセスにランダム性を導入することでモデルのパフォーマンスを向上させた**Random Forest**（2001年）や[^40-73]、使用する学習データセットのサブセット選択にランダム性をもたせることでBoostingをより一般的な学習フレームワークとした**AdaBoost**（Adaptive Boosting、1997年）[^40-74]、AdaBoostとGD法を組み合わせた**Gradient Boost**など[^40-74]、様々な派生形が出現した。

> ![Ensemble Learning](/images/ai_history/ensemble.png)
*アンサンブル学習BaggingとBoostingの概念（引用:[^40-77]）*

その頃世間でも、1997年にIBM社のDeep Blueがチェスの世界チャンピオンに勝利したり[^40-22]、AIを搭載した製品であるSONY社のAIBO（Artificial Interigence roBOt、1999年）[^40-10] [^40-11]、iRobot社のRoomba（2002年）[^40-12]がリリースされる等、AIのニュースが出始めていた。また、2001年にIT調査会社のMETA Group社（2005年にGartner社に買収されている[^40-23]）が**Big Data**を提唱し[^40-24]、データソースの範囲が大幅に増加し、データを統合して新しい洞察を生成することが示唆され[^40-25]、2002年にはC/C++の機械学習ライブラリTorchがリリースされるなど[^40-26]、AIの活躍・進化がますます期待された。
ただし、隠れ層の多いニューラルネットワークは**DNN**（Deep Neural Network）と呼ばれ[^40-32]、より複雑な非線形関係を計算コストを削減して表現できるようになると期待されたが[^40-31]、依然として学習が難しい（勾配消失問題、局所最適化等）とされ、隠れ層は1層または2層というのが定石だった[^40-29]。そんな中、2006年のGeoffrey HintonとRuslan Salakhutdinovの論文で**Autoencoder**を持ちいた次元削減の方法が示され[^40-30]、DNNを分類タスクに適用することも可能になった[^40-33]。これ以降、**Deep Learning**という用語が一般的となり、より注目を浴びていくこととなる[^40-27] [^40-28]。

> ![Network Architecture for an Ordinary Autoencoder](https://www.assemblyai.com/blog/content/images/2022/01/autoencoder_architecture.png)
*Network Architecture for an Ordinary Autoencoder（引用:[^40-78]）*

さらに、アルゴリズム自体だけでなく、データによりアルゴリズムの精度が高まるという考えのもと、2009年に物体認識ソフトウェアの研究のためImageNetという大規模な画像データセットが発表され[^40-34] [^40-35]、翌2010年からILSVRC（ImageNet Large Scale Visual Recognition Challenge）という画像認識AIのコンテストを毎年開催し[^40-39]、この頃およびこれ以後のAIブームの触媒となったといえる。
2009年のスタンフォード大学の論文で、主にグラフィック処理のために利用されていたプロセッサである**GPU**（Graphic Processor Unit）、2006年にNvidia社によって開発されたCUDA[^40-43]と2008年に発表されたそのプログラミングモデル[^40-44]を利用し、AIの学習を並列に実行することで処理を高速化した[^40-36]。これ以来、ニューラルネットワークの学習・推論にGPUが採用されることが多くなった[^40-37]。
そして、2012年のILSCRCでAlexNetと呼ばれるDeep CNNモデルが発表され[^40-40]、他を凌駕する性能を見せた。AlexNetは5つの畳み込み層と3つの全結合層という深い構造をしており多くのパラメータを有していたが、CNNでは初めてGPUで学習を行うことで、以前のモデルよりも4倍高速に処理できた[^40-38] [^40-41] [^40-42]。この成果により、Deep Learningが夢物語ではないこと、実用化する方法を世界に示したといえる。

> ![Alexnet Block Diagram](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*bD_DMBtKwveuzIkQTwjKQQ.png)
*Alexnet Block Diagram（引用:[^40-79]）*

学習に用いるデータセットが大規模になってくると、最適化アルゴリズムついても、2011年に**AdaGrad**（Adaptive Gradient）[^40-62] [^40-63]、2012年に**RMSprop**（Root Mean Square Propagation）といった、勾配の大きさに応じて学習率を調整するように損失の振動を抑制した手法が発表された[^40-64] [^40-65]。また2012年には、更新時に確率的勾配の平均を取るSAG（Stochastic Average Gradient）法なども提案されている[^40-66] [^40-67]。
また、1次法の弱点として、ハイパーパラメータ（ステップ長、バッチサイズ等）調整、並列化による学習プロセスの高速化などが難しいことを上げ、高次法のNewton法を現実的な計算リソースで可能とした**LBFGS**（memory-Limited Broyden–Fletcher–Goldfarb–Shanno algorithm、2007年）をはじめ[^40-68]、さまざまながStochastic Newton法やQuasi Newton法が開発されるなど[^40-69]、Optimizationの研究も活発になってきた。

インターネットの普及が続き、2000年初期あたりからWeb2.0と呼ばれる時代に入る[^40-45]。Facebook（2004年[^40-46]）、Youtube（2005年[^40-47]）、Twitter（2006年[^40-48]）をはじめとした動的コンテンツを有するWebサービスが続々と立ち上がり、2006年ごろからのWi-Fiの普及もあって[^40-49]、Web上で人々が活動するようになった。さらに、MySQLやPostgreSQLなどのデータベースシステムの成長[^40-50]や2008年ごろのIoT（Internet of Things）の誕生[^40-51]など、発生するデータが増加する明らかな兆候が見え始める。このような流れもあり、2009年のIDC（International Data Corporation）社の調査では2020年までにデジタルデータは44倍の35ゼタバイトに増加する（Data explosion）と予測され大きな反響を呼んだ[^40-52]。それにより学習データが重要とされているAI、特に機械学習、特にDeep Learningにより期待がかかるようになった。
また、2008年にGitを使用したソフトウェア開発とバージョン管理のためのプラットフォームであるGithubが公開[^40-54]、このころ勢いをつけていたプログラミング言語であるPythonについて[^40-55]、機械学習プログラミングが容易になるライブラリであるscikit-learn（2007年[^40-57]）、Theano（2007年[^40-56]）などが利用可能となり、AI開発の敷居もますます下がったいえる。

> ![Data growth and expansion (IDC, 2009)](/images/ai_history/IDC_2009.png)
*Data growth and expansion (IDC, 2009) （引用:[^49-80]）*

[^40-1]:[A Quick History of Neural Networks](https://www.analyticsvidhya.com/blog/2020/09/quick-history-neural-networks/)
[^40-2]:[Explained: Neural networks](https://news.mit.edu/2017/explained-neural-networks-deep-learning-0414)
[^40-3]:[*Hacker News*: Neural networks in the 1990s](https://news.ycombinator.com/item?id=36385809)
[^40-4]:[n-grams: AI Terms Explained](https://www.playerzero.ai/advanced/ai-terms-explained/n-grams-ai-terms-explained)
[^40-5]:[A Brief History of Large Language Models](https://www.linkedin.com/pulse/brief-history-large-language-models-bob/)
[^40-6]:[サポートベクトルマシンとカーネル法](https://orsj.org/wp-content/corsj/or65-6/or65_6_304.pdf)
[^40-7]:[Maximum Margin Separating Hyperplane in Scikit Learn](https://www.geeksforgeeks.org/maximum-margin-separating-hyperplane-in-scikit-learn/)
[^40-8]:[Top 4 advantages and disadvantages of Support Vector Machine or SVM](https://dhirajkumarblog.medium.com/top-4-advantages-and-disadvantages-of-support-vector-machine-or-svm-a3c06a2b107)
[^40-9]:[Kernel methoc in *Wikipedia*](https://en.wikipedia.org/wiki/Kernel_method)
[^40-10]:[ロボットによるエンタテインメント市場を創造する4足歩行型エンタテインメントロボット "AIBO（アイボ）"の販売開始](https://www.sony.com/ja/SonyInfo/News/Press/199905/99-046/)
[^40-11]:[Artificial Intelligence Robot](https://www.techopedia.com/definition/14242/artificial-intelligence-robot-aibo)
[^40-12]:[iRobot Introduces Roomba™ Intelligent FloorVac - The First Automatic Floor Cleaner In The U.S.](https://media.irobot.com/2002-09-18-iRobot-Introduces-Roomba-Intelligent-FloorVac-The-First-Automatic-Floor-Cleaner-In-The-U-S)
[^40-13]:[MNIST database in *Wikipedia*](https://en.wikipedia.org/wiki/MNIST_database#cite_note-8)
[^40-14]:[The History of Neural Networks](https://dataconomy.com/2017/04/19/history-neural-networks/)
[^40-15]:[Gradient-Based Learning Applied to Document Recognition](https://axon.cs.byu.edu/~martinez/classes/678/Papers/Convolution_nets.pdf)
[^40-16]:[マイクロプロセッサの誕生からWindows 95の登場までを振り返る](https://pc-kaden.medy.jp/p/a6da8c2a-03c6-444a-bb3d-f5c7af00ab94)
[^40-17]:[1995 Was The Most Important Year For The Web](https://thehistoryoftheweb.com/complete-history/1995-was-the-most-important-year-for-the-web/)
[^40-18]:[Deep learning’s origins and pioneers](https://www.mckinsey.com/featured-insights/artificial-intelligence/deep-learnings-origins-and-pioneers)
[^40-19]:[LONG SHORT-TERM MEMORY](https://www.bioinf.jku.at/publications/older/2604.pdf)
[^40-20]:[What is Long Short Term Memory (LSTM) - Complete Guide](https://www.knowledgehut.com/blog/web-development/long-short-term-memory#long-short-term%C2%A0memory-networks)
[^40-21]:[Wang, Xin & Liu, Yuanchao & Sun, Chengjie & Wang, Baoxun & Wang, Xiaolong. (2015). Predicting Polarities of Tweets by Composing Word Embeddings with Long Short-Term Memory. 1343-1353. 10.3115/v1/P15-1130. ](https://www.researchgate.net/publication/301404520_Predicting_Polarities_of_Tweets_by_Composing_Word_Embeddings_with_Long_Short-Term_Memory)
[^40-22]:[25 years ago today: How Deep Blue vs. Kasparov changed AI forever](https://aibusiness.com/ml/25-years-ago-today-how-deep-blue-vs-kasparov-changed-ai-forever)
[^40-23]:[Gartner Acquisitions](https://www.gartner.com/en/about/acquisitions)
[^40-24]:[What makes Big Data, Big Data? Exploring the ontological characteristics of 26 datasets](https://journals.sagepub.com/doi/pdf/10.1177/2053951716631130)
[^40-25]:[Chapter 9 - The Big Data and Artificial Intelligence: Opportunities and Challenges to Modernise the Policy Cycle](https://www.sciencedirect.com/science/article/pii/B9780128225967000097)
[^40-26]:[Torch: a modular machine learning software library](https://infoscience.epfl.ch/record/82802?ln=en)
[^40-27]:[A Short History Of Deep Learning — Everyone Should Read](https://bernardmarr.com/a-short-history-of-deep-learning-everyone-should-read/)
[^40-28]:[Introduction To Deep Learning - Logix_Quest - Medium](https://aminazahid45.medium.com/introduction-to-deep-learning-334c0c01a145)
[^40-29]:[Auto-encoder based dimensionality reduction](https://www.sciencedirect.com/science/article/abs/pii/S0925231215017671)
[^40-30]:[Reducing the Dimensionality of Data with Neural Networks](https://www.cs.toronto.edu/~hinton/absps/science.pdf)
[^40-31]:[Hands-On Machine Learning with R: Chapter 19 Autoencoders](https://bradleyboehmke.github.io/HOML/autoencoders.html)
[^40-32]:[Auto-Encoders in Deep Learning—A Review with New Perspectives](https://www.mdpi.com/2227-7390/11/8/1777)
[^40-33]:[Lecture 12 Handwritten Digit (MNIST) Recognition Using Deep Neural Networks](https://bkict-ocw.knu.ac.kr/caster/file/lecture/5DE9F88D7ADC6.pdf)
[^40-34]:[ImageNet: A Large-Scale Hierarchical Image Database](https://image-net.org/static_files/papers/imagenet_cvpr09.pdf)
[^40-35]:[ImageNet: A Pioneering Vision for Computers](https://www.historyofdatascience.com/imagenet-a-pioneering-vision-for-computers/)
[^40-36]:[Large-scale Deep Unsupervised Learning using Graphics Processors](http://robotics.stanford.edu/~ang/papers/icml09-LargeScaleUnsupervisedDeepLearningGPU.pdf)
[^40-37]:[A Brief History of GPUs](https://medium.com/neuralmagic/a-brief-history-of-gpus-27122d8fd45)
[^40-38]:[A practical experiment for comparing LeNet, AlexNet, VGG and ResNet models with their advantages and disadvantages.](https://tejasmohanayyar.medium.com/a-practical-experiment-for-comparing-lenet-alexnet-vgg-and-resnet-models-with-their-advantages-d932fb7c7d17)
[^40-39]:[ImageNet database in *Wikipedia*](https://en.wikipedia.org/wiki/ImageNet)
[^40-40]:[ImageNet Classification with Deep Convolutional Neural Networks](https://proceedings.neurips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf)
[^40-41]:[AlexNet and ImageNet: The Birth of Deep Learning](https://www.pinecone.io/learn/series/image-search/imagenet/)
[^40-42]:[The data that transformed AI research—and possibly the world](https://qz.com/1034972/the-data-that-changed-the-direction-of-ai-research-and-possibly-the-world)
[^40-43]:[About CUDA](https://developer.nvidia.com/about-cuda)
[^40-44]:[Manycore Parallel Computing with CUDA](https://developer.download.nvidia.com/presentations/2008/ICS2008/ICS2008_Keynote_MarkHarris_public.pdf)
[^40-45]:[The Evolution of the Internet: Web 1.0, Web 2.0 and Web 3.0.](https://www.linkedin.com/pulse/evolution-internet-web-10-20-30-deepak-lyngdoh/)
[^40-46]:[History of Facebook in *Wikipedia*](https://en.wikipedia.org/wiki/History_of_Facebook)
[^40-47]:[History of Youtube in *Wikipedia*](https://en.wikipedia.org/wiki/History_of_YouTube)
[^40-48]:[Twitter in *Wikipedia*](https://en.wikipedia.org/wiki/Twitter)
[^40-49]:[15 years of WiFi](https://fon.com/fon-wifi-infographic/)
[^40-50]:[Database Management System - DBMS](https://padakuu.com/history-of-database-systems-306-article)
[^40-51]:[A Brief History of Internet of Things (IoT)](https://bytebeam.io/blog/a-brief-history-of-internet-of-things/)
[^40-52]:[IDC: Data explosion goes into the Zettabytes](https://www.itpro.com/622942/idc-data-explosion-goes-into-the-zettabytes)
[^40-53]:[The main challenges and issues of big data management](https://www.researchgate.net/publication/272696610_The_main_challenges_and_issues_of_big_data_management)
[^40-54]:[GitHub in *Wikipedia*](https://en.wikipedia.org/wiki/GitHub)
[^40-55]:[The Rise of the Python Programming Language](https://www.udacity.com/blog/2021/01/the-rise-of-the-python-programming-language.html)
[^40-56]:[Theano in *Wikipedia*](https://en.wikipedia.org/wiki/Theano_(software))
[^40-57]:[scikit-learn in *Wikipedia*](https://en.wikipedia.org/wiki/Scikit-learn)
[^40-58]:[The graph neural network model](https://ro.uow.edu.au/cgi/viewcontent.cgi?article=10501&context=infopapers)
[^40-59]:[What Are Graph Neural Networks?](https://blogs.nvidia.com/blog/2022/10/24/what-are-graph-neural-networks/)
[^40-60]:[Semi-Supervised Learning](https://www.molgen.mpg.de/3659531/MITPress--SemiSupervised-Learning.pdf)
[^40-61]:[A survey on semi-supervised learning](https://www.researchgate.net/publication/337299262_A_survey_on_semi-supervised_learning)
[^40-62]:[AdaGrad: AI Terms Explained](https://www.playerzero.ai/advanced/ai-terms-explained/adagrad-ai-terms-explained)
[^40-63]:[Adaptive Subgradient Methods for Online Learning and Stochastic Optimization](https://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf)
[^40-64]:[RMSProp](https://d2l.ai/chapter_optimization/rmsprop.html)
[^40-65]:[Neural Networks for Machine Learning](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf)
[^40-66]:[A stochastic gradient method with an exponential convergence rate for finite training sets](https://arxiv.org/abs/1202.6258)
[^40-67]:[stochastic average gradientな話](https://vaaaaaanquish.hatenablog.com/entry/2013/12/11/084002)
[^40-68]:[A Stochastic Quasi-Newton Method for Online Convex Optimization](https://proceedings.mlr.press/v2/schraudolph07a/schraudolph07a.pdf)
[^40-69]:[Quasi-Newton methods for machine learning: forget the past, just sample](https://par.nsf.gov/servlets/purl/10313496)
[^40-70]:[Bagging Predictors](https://sci2s.ugr.es/keel/pdf/algorithm/articulo/1996-ML-Breiman-Bagging%20Predictors.pdf)
[^40-71]:[Experiments with a New Boosting Algorithm](https://cseweb.ucsd.edu/~yfreund/papers/boostingexperiments.pdf)
[^40-72]:[Boosting a Weak Learning Algorithm by Majority](https://www.sciencedirect.com/science/article/pii/S0890540185711364)
[^40-73]:[Random Forests](https://link.springer.com/article/10.1023/A:1010933404324)
[^40-74]:[A Decision-Theoretic Generalization of On-Line Learning and an Application to Boosting](https://www.sciencedirect.com/science/article/pii/S002200009791504X)
[^40-75]:[Greedy function approximation: A gradient boosting machine](https://projecteuclid.org/journals/annals-of-statistics/volume-29/issue-5/Greedy-function-approximation-A-gradient-boosting-machine/10.1214/aos/1013203451.full)
[^40-76]:[Support Vector Machines and Kernel Methods](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/1655/1553)
[^40-77]:[Bagging vs Boosting in Machine Learning](https://www.geeksforgeeks.org/bagging-vs-boosting-in-machine-learning/)
[^40-78]:[Introduction to Variational Autoencoders Using Keras](https://www.assemblyai.com/blog/introduction-to-variational-autoencoders-using-keras/)
[^40-79]:[Difference between AlexNet, VGGNet, ResNet, and Inception](https://towardsdatascience.com/the-w3h-of-alexnet-vggnet-resnet-and-inception-7baaaecccc96)
[^49-80]:[The main challenges and issues of big data management](https://www.researchgate.net/publication/272696610_The_main_challenges_and_issues_of_big_data_management?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6Il9kaXJlY3QiLCJwYWdlIjoiX2RpcmVjdCJ9fQ)

## 3.5. 2013年ごろ以降 ：Deep Learning
2013年頃に、メディア報道に「Big Tech」という技術系大企業（Big FourはGoogle、Amazon、Facebook、Apple、Big Fiveはそれらに加えてMicrosoft）を表す用語が現れはじめた[^50-1] [^50-2]。これらの企業は例えば、Appleが音声認識のデジタルアシスタントであるSiriをiPhone 4Sに実装（2011年）[^50-3]、FacebookがFAIR（Facebook Artificial Intelligence Research）を設立（2013年）[^50-6]、Googleが英国のAIスタートアップDeepMind社を買収（2014年）[^50-5]、AmazonがスマートスピーカーにバーチャルアシスタントAlexaを搭載（2014年）[^50-4]、MicrosoftがデジタルアシスタントCortanaをリリース（2014年）など[^50-7]、AIに対しても非常に積極的な動きを見せていた。
この頃、CPU性能の一つであるクロック周波数は頭打ち状態となっていたが、マルチコア化、仮想化等により、コンピュータはさらに高性能になっていった[^50-13]。チップレベルでいえば、集積化が進んでも単位面積当たりの消費電力が変わらないというデナード則（Dennard's scaling）が崩壊し、パフォーマンスを上げつつ発熱等の問題に対応するためにはすべてのコアを同時に使用できないという問題（Dark Silicon）に対して[^50-86]、用途別のアクセラレータやヘテロジニアス構造で対応していくという時代に入り[^50-87]、Deep Learningもより高度化していく。
2013年に、入力を示すベクトル空間を生成する**Embedding**と呼ばれる処理により、単語の意味を表現したWord Embeddingを生成するWord2vecと呼ばれるモデルがGoogleの技術者により発表された[^50-11] [^50-12]。そして2014年に発表されたSeq2seq（Sequence-to-Sequence）モデルでは[^50-18]、RNNでWord Embeddingを行い、さらにRNNで別の言語に変換するという機械翻訳モデルが提案された。このようなEmbeddingを行うEncoderと、それをもとに出力を行うDecoderからなる構造を、[**Encoder-Decoder**](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/2173/)と呼び[^50-19]、自然言語処理（翻訳）でいうと複雑な文構造や慣用的な表現などニュアンスを考慮した処理を可能とした[^50-20]（構造・機能の定性的なまとめは[こちら](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/2173/)もどうぞ）。
2014年にStanford大によりGloVeと呼ばれる事前学習されたモデルが発表され[^50-16]、特に機械翻訳ではWord Embeddingが主流になっていった[^50-14]。

> **note**
Word embeddingという言葉は、2003年に提唱され、2008年の*A unified architecture for natural language processing*という論文で初めて実証されたとされる[^50-14]。入力をベクトル空間に焼き直せばよいので、CNNの畳み込み層を、Image Embeddingとする場合もある[^50-15]。

> ![Embeddings can produce remarkable analogies.](https://developers.google.com/static/machine-learning/crash-course/images/linear-relationships.svg?hl=ja)
*Embeddings can produce remarkable analogies（引用:[^50-88]）*

そしてこの2014年には、2種類のニューラルネット（それぞれ、Generator、Descriminatorと呼ばれる。詳細は割愛）を用いてAIが画像を生成できる事例をしめした**GAN**（Generative Adversarial Neural network）というモデルが発表され[^50-22]、クリエイティブな能力を持つAI、すなわち**生成AI**（**Generative AI**）が見えてきた。
また同2014年に、**Adam**（Adaptive moment estimation）と呼ばれる[^50-82] [^50-83]、RMSrop法とMomentum法を組み合わせたOptimizer、**XGBoost**（eXtream Gradient Boost）と呼ばれるアンサンブル学習法が登場した。

この頃、ドイツの[Industrie 4.0](https://www.plattform-i40.de/IP/Navigation/EN/Home/home.html)（2013年に発表、2015年に拡大[^50-27]）中国の[Made in China 2025（中国製造2025）](https://english.www.gov.cn/2016special/madeinchina2025/)（2015年）、日本の[Society 5.0](https://www8.cao.go.jp/cstp/society5_0/)（2016年）、アメリカの[米国AI研究開発戦略計画（National Artificial Intelligence Research and Development Strategic Plan）](https://www.nitrd.gov/PUBS/national_ai_rd_strategic_plan.pdf)（2016年）など[^50-28]、の戦略などAIを組み込んだ政策レベルの動きも活発化し、国家としてAI技術を前提とした社会を大々的に打ち上げるようになってきた。
また、AI研究においても、2015年には、Google社のエンジニアによりKeras[^50-8]、日本のPreferred Networks社によりChainer[^50-9]、Google社によりTensorflow、翌2016年にFacebook社よりPyTorch[^50-10]というオープンソースのGPUをサポートしたPythonベースの機械学習・Deep Learningのライブラリがリリースされ、さらにAI・機械学習に対する取り組みの敷居が大幅に下がる。さらに同2015年、機械学習モデルの利活用フェーズの考え方として、2009年に発案されたDevOps（Development Operations）の原則[^50-26]を機械学習モデルを組み込んだシステムに適用し、システムの自動化とモニタリングを推進できるMLOps（Machine Operations）というパラダイムも注目され始めた[^50-23] [^50-24] 。
世間的にも、Google社（厳密にはDeepMind社）のAlphaGoというAIが囲碁の世界チャンピオンに勝利し、大きな話題を呼んだ[^50-29]。

2015年、ニューラルネットワークのさらなる多層化に伴う勾配消失・勾配爆発問題への対策として、Microsoft Research社によりResNet（Residual Network）と呼ばれる、ネットワークの層を飛ばしてニューロンを結合させる（スキップ接続）構造を持ったモデルが提案された [^50-30] [^50-31]。 この技術により、数百数千の層を持つ、ますます深いネットワークの可能性が見出された[^50-32]。
そして、Seq2seqモデルでEncoderの出力が固定長であるため長い入力に対応しづらいことなどを問題点とし[^50-35]、**Attention機構**と呼ばれるDecoderが注目すべき部分を示すベクトルを計算するメカニズムを実装したモデルが提案され、制度が向上することが示された（2015年の論文[^50-37]が多く引用された[^50-34]）[^50-33] [^50-36]。このAttention機構を応用したモデルや[^50-39]、画像処理AIに適用した例など[^50-40]、その後さまざまなアルゴリズムのAttention機構が提案された（Attention機構の詳細は[こちら](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/2170/)もどうぞ）。
ただし、Attention機構が高精度化に大きく貢献した一方で、RNNを用いたEncoder-Decoderモデルのようなシーケンシャルな構造では大規模な入力に対して、計算に時間がかかりすぎるという欠点があった[^50-43]。これに対して、そこで2017年にMulti-head Attentionという方式のAttention機構を搭載して並列計算可能となった、**Transformer**と呼ばれるモデルが発表された[^50-38]。このTransformerは入力の全体から注目すべき部分を考慮させる点で、入力のうち特定の部分の前後関係を分析するRNNなどのニューラルネットワークとは、根本的に動作が異なり[^50-41] [^50-42]、CNNやRNNより計算量が抑えられ、訓練が容易で、並列処理CNNもしやすいなどの特長を持つ[^50-44]。
この頃、分散コンピューティングや並列コンピューティングが一般的となってきて、Stchastic LBFGS（2015年）[^50-84]やその改善版が提案されるなど、Optimizationアルゴリズムとして様々なQuasi Newton法なども実用化が見えてきた[^50^85]。

> ![Transformer](https://machinelearningmastery.com/wp-content/uploads/2021/08/attention_research_1-727x1024.png)
*Transformerの構造（引用:[^50-90]）*

産業界全体では、Industrie 4.0のキーテクノロジーの一つにAIが挙げられていることや[^50-45] [^50-46]、この頃のAI技術への投資元のメインは政府ではなく産業界となったこと[^30-39]（DARPAが2018年にAI Next Campaignを打ち出すなど、政府関連も投資は継続している[^50-48]）、2006年ごろから普及しだしたクラウドコンピューティング技術により[^50-47]、多くのソフトウェアがオンプレミスからクラウドへと移行していった反動や、続々とAIのパフォーマンスが人間の能力を超えてきていることもあり[^50-57]、小規模リソースで動作する**Edge AI**が注目されてきた。スマートフォンへのAI実装に向けた開発環境としても、2017年にTensorFlow Lite[^50-53]、2019年にPytorch Mobileが発表された[^50-54]。

> ![State-of-the-art AI performance on benchmarks, relative to human performance](/images/ai_history/1691138939574.jpeg)
*State-of-the-art AI performance on benchmarks, relative to human performance（引用:[^50-57]）*

大量のデータをGPU等大規模な計算リソースで処理できるようになってきたことにより、2019、2020年ごろから、ラベルのないデータから独自のラベルを自動的に作り、それをもとに学習を進める**自己教師あり学習**（**Self-Supervised Learning: SSL**）が注目を浴びてきた[^50-79] [^50-80] [^50-81]。
Transformerモデルは非常に有用であり、2018年には目的や学習方法が異なるGoogle社のBERT（Bidirectional Encoder Representations from Transformers）や[^50-49] [^50-50]（2019年にはGoogleの検索にも導入されている[^50-56]）、OpenAI社のGPT（Generative Pre-Trained Transformer）といった[^50-51] [^50-52]、自然言語系のAIモデルが発表された。言語系のモデルは大規模な学習データを用いると不連続にパフォーマンスが向上することがわかってきて、モデルサイズ（パラメータ数のこと。10億（Billion）単位でカウントされる）を増加している[^50-59]。

> ![Language Model Sizes Over times](https://twosigmaventures.com/wp-content/uploads/sites/2/Model-Size-Over-Time@4x.png)
*Language Model Sizes Over times（引用:[^50-89]）*

このようなモデルは特に**LLMs**（Large Language Models, 大規模言語モデル）と呼ばれ、OpenAI社のGPT-3（2020年7月）[^50-62]、GPT-3.5（2022年3月）[^50-63]、GPT-4（2023年3月）[^50-64]、Google社のLaMDA（2021年3月）[^50-65]、PaLM（2022年4月）[^50-66]、PaLM-2（2023年3月）[^50-67]、Gemini（2023年12月）[^50-68]、Meta社のLLaMa（2023年2月）[^50-60]、LLaMa-2（2023年7月、優先パートナーとしてMicrosoft社が挙げられた）[^50-61]、Anthropic社のClaude（2023年3月）[^50-69]、Claude2（2023年7月）[^50-70]など、現在でも新しいモデルが開発されている。
そしてLLMsは、追加の学習用データセットを用いてFine tuningを行うことで用途に特化したサービスにすることができ[^50-71]、その意味で**基盤モデル**（**Foundation Model**）と呼ばれることもある[^50-72]。中でも、GPT-3.5をChatbot用にFine tuningした**ChatGPT**というサービスは、2022年11月にリリースされて2か月で月間1億人のアクティブユーザーに到達したと推定され、史上最も急速に成長している消費者向けアプリケーションと呼ばれている[^50-73]。これにより、「生成AI」という言葉が爆発的に普及し、オフィスドキュメントのデファクトスタンダードである[^50-74]Microsoft 365にChatGPTを統合したため、技術者でなくてもAIに触れる機械が激増した。
これに伴い、元データを提供する情報検索システムを追加してChatGPTのようなLLMsサービスの機能を拡張するパターンであるRAG（Retrieval Augmentation Generation）パターンや[^50-77]、生成AIに目的の出力を生成させる技術としてPrompt Engineeringなど[^50-78]、新しいコンセプトも続々出現している。
Transformerはそのパフォーマンスの高さから他の分野にも用は拡大し[^50-55] [^50-76]、マシンビジョン（画像認識）向けの**Vision Transformer**（**ViT**、2020年）など[^50-58]、従来のニューラルネットワークが担ってきたタスクを代替する手法としても用いられ始めている。そして、生成AIという観点では、テキストから画像を生成するtext-to-imageモデルと呼ばれる分野も発展し、Stability AI社の[Stable Diffusion](https://huggingface.co/spaces/stabilityai/stable-diffusion)（2022年）、Midjourney社の[Midjourney](https://www.midjourney.com/home/)（2022年）、OpenAI社の[DALL-E3](https://openai.com/dall-e-3)（2023年）などが発表されている。

[^50-1]:[Big Tech in *Wikipedia*](https://en.wikipedia.org/wiki/Big_Tech)
[^50-2]:[Big Tech](https://academic-accelerator.com/encyclopedia/big-tech)
[^50-3]:[Apple's Siri and the Future of Artificial Intelligence](https://forbes.com/sites/erikkain/2011/10/15/apples-siri-and-the-future-of-artificial-intelligence/?sh=37bdf86d29a0)
[^50-4]:[Amazon Alexa in *Wikipedia*](https://en.wikipedia.org/wiki/Amazon_Alexa)
[^50-5]:[Google buys UK artificial intelligence startup Deepmind for £400m](https://www.theguardian.com/technology/2014/jan/27/google-acquires-uk-artificial-intelligence-startup-deepmind)
[^50-6]:[Meta AI in *Wikipedia*](https://en.wikipedia.org/wiki/Meta_AI)
[^50-7]:[A brief history of Cortana, Microsoft's trusty digital assistant](https://www.windowscentral.com/history-cortana-microsofts-digital-assistant)
[^50-8]:[The History of Keras: From Research Project to Industry Standard](https://ts2.space/en/the-history-of-keras-from-research-project-to-industry-standard/)
[^50-9]:[Chainer in *Wikipedia*](https://en.wikipedia.org/wiki/Chainer)
[^50-10]:[PyTorch: all about Facebook’s Deep Learning framework](https://datascientest.com/en/pytorch-all-about-this-framework#:~:text=Based%20on%20the%20former%20Torch,a%20simple%20and%20efficient%20way.)
[^50-11]:[Distributed Representations of Words and Phrases and their Compositionality](https://arxiv.org/abs/1310.4546)
[^50-12]:[Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/abs/1301.3781)
[^50-13]:[MULTI-CORE PROCESSORS](https://medium.com/nerd-for-tech/multi-core-processors-53ee2899f90f)
[^50-14]:[An overview of word embeddings and their connection to distributional semantic models](https://aylien.com/blog/overview-word-embeddings-history-word2vec-cbow-glove)
[^50-15]:[Image Embeddings explained](https://www.picsellia.com/post/image-embeddings-explained)
[^50-16]:[GloVe: Global Vectors for Word Representation](https://nlp.stanford.edu/projects/glove/)
[^50-17]:[Sequence To Sequence ( Seq2Seq )](https://blog.octopt.com/sequence-to-sequence/)
[^50-18]:[Sequence to Sequence Learning with Neural Networks](https://arxiv.org/abs/1409.3215)
[^50-19]:[Sequence to Sequence (seq2seq) and Attention](https://lena-voita.github.io/nlp_course/seq2seq_and_attention.html)
[^50-20]:[The Benefits of AI Seq2Seq Models in Machine Translation and Language Processing](https://ts2.space/en/the-impact-of-ai-seq2seq-models-on-machine-translation-and-language-processing/)
[^50-21]:[AI-generated world: How Generative Adversarial Networks(GANs) are transforming whole industries today](https://www.linkedin.com/pulse/ai-generated-world-how-generative-adversarial-whole-industries-kusyy/)
[^50-22]:[Generative Adversarial Networks](https://arxiv.org/abs/1406.2661)
[^50-23]:[Hidden Technical Debt in Machine Learning Systems](https://papers.nips.cc/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf)
[^50-24]:[Secure MLOps solutions with Azure network security](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/network-security-mlops)
[^50-25]:[MLOps: 機械学習における継続的デリバリーと自動化のパイプライン](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning?hl=ja)
[^50-26]:[What Is DevOps?](https://newrelic.com/devops/what-is-devops)
[^50-27]:[The background to Plattform Industrie 4.0](https://www.plattform-i40.de/IP/Navigation/EN/ThePlatform/Background/background.html)
[^50-28]:[Creation of the National Artificial Intelligence Research and Development Strategic Plan](https://onlinelibrary.wiley.com/doi/10.1609/aimag.v39i2.2803)
[^50-29]:[Artificial intelligence: Google's AlphaGo beats Go master Lee Se-dol](https://www.bbc.com/news/technology-35785875)
[^50-30]:[Deep Residual Learning for Image Recognition](https://arxiv.org/pdf/1512.03385.pdf)
[^50-31]:[Residual Networks (ResNet) – Deep Learning](https://www.geeksforgeeks.org/residual-networks-resnet-deep-learning/)
[^50-32]:[The Impact of Residual Networks on the Advancement of AI](https://ts2.space/en/the-impact-of-residual-networks-on-the-advancement-of-ai/)
[^50-33]:[Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473)
[^50-34]:[Review — Neural Machine Translation by Jointly Learning to Align and Translate](https://sh-tsang.medium.com/review-neural-machine-translation-by-jointly-learning-to-align-and-translate-3b381fc032e3)
[^50-35]:[Seq2Seq with Attention](https://hackmd.io/@kkume/rkjOYwfKD)
[^50-36]:[Sequence to Sequence (seq2seq) and Attention](https://lena-voita.github.io/nlp_course/seq2seq_and_attention.html)
[^50-37]:[NEURAL MACHINE TRANSLATION BY JOINTLY LEARNING TO ALIGN AND TRANSLATE](https://arxiv.org/pdf/1409.0473.pdf)
[^50-38]:[Attention Is All You Need](https://arxiv.org/abs/1706.03762)
[^50-39]:[Attention? Attention!](https://lilianweng.github.io/posts/2018-06-24-attention/)
[^50-40]:[Show, Attend and Tell: Neural Image Caption Generation with Visual Attention](https://proceedings.mlr.press/v37/xuc15.pdf)
[^50-41]:[Transformers Can Mock Part of Human Brain](https://www.infoq.com/news/2022/10/transformers-mock-brain/)
[^50-42]:[AI models are powerful, but are they biologically plausible?](https://news.mit.edu/2023/ai-models-astrocytes-role-brain-0815)
[^50-43]:[Attention is all you need: Discovering the Transformer paper](https://towardsdatascience.com/attention-is-all-you-need-discovering-the-transformer-paper-73e5ff5e0634)
[^50-44]:[CRDS 国立研究開発法人科学技術振興機構 研究開発戦略センター 研究開発の俯瞰報告書 システム・情報科学技術分野（2023年）](https://www.jst.go.jp/crds/pdf/2022/FR/CRDS-FY2022-FR-04/CRDS-FY2022-FR-04_20102.pdf)
[^50-45]:[VDMA Digitalization & Industrie 4.0](https://www.vdma.org/digitalization-industry-40)
[^50-46]:[VDMA Artificial Intelligence](https://www.vdma.org/artificial-intelligence)
[^50-47]:[Docker一強の終焉にあたり、押さえるべきContainer事情](https://zenn.dev/ttnt_1013/articles/f36e251a0cd24e)
[^50-48]:[AI Next Campaign (Archived)](https://www.darpa.mil/work-with-us/ai-next-campaign)
[^50-49]:[Unleashing the Power of BERT: How the Transformer Model Revolutionized NLP](https://arize.com/blog-course/unleashing-bert-transformer-model-nlp/)
[^50-50]:[BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805)
[^50-51]:[GPT: Generative Pre-Trained Transformer (2018)](https://kikaben.com/gpt-generative-pre-training-transformer-2018/)
[^50-52]:[Improving Language Understanding by Generative Pre-Training](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)
[^50-53]:[Announcing TensorFlow Lite](https://developers.googleblog.com/2017/11/announcing-tensorflow-lite.html)
[^50-54]:[Facebook launches PyTorch Mobile for edge ML on Android and iOS devices](https://venturebeat.com/ai/facebook-launches-pytorch-mobile-for-edge-ml-on-android-and-ios-devices/)
[^50-55]:[Stanford CS25: V2 I Introduction to Transformers w/ Andrej Karpathy](https://www.youtube.com/watch?v=XfpMkf4rD6E/)
[^50-56]:[【図解】BERTとは？Googleの新自然言語処理がどう影響するのか](https://satori.marketing/marketing-blog/what-is-bert/)
[^50-57]:[4 Charts That Show Why AI Progress Is Unlikely to Slow Down](https://time.com/6300942/ai-progress-charts/)
[^50-58]:[An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](https://openreview.net/forum?id=YicbFdNTTy)
[^50-59]:[The Promise and Perils of Large Language Models](https://twosigmaventures.com/blog/article/the-promise-and-perils-of-large-language-models/?ref=assemblyai.com)
[^50-60]:[Introducing LLaMA: A foundational, 65-billion-parameter large language model](https://ai.meta.com/blog/large-language-model-llama-meta-ai/)
[^50-61]:[Metaとマイクロソフト、 次世代Llamaを発表](https://about.fb.com/ja/news/2023/07/meta-and-microsoft-introduce-the-next-generation-of-llama/)
[^50-62]:[OpenAI’s new language generator GPT-3 is shockingly good—and completely mindless](https://www.technologyreview.com/2020/07/20/1005454/openai-machine-learning-language-generator-gpt-3-nlp/)
[^50-63]:[OpenAI GPT-3.5](https://lablab.ai/tech/openai/gpt3-5)
[^50-64]:[OpenAI GPT-4](https://lablab.ai/tech/openai/gpt4)
[^50-65]:[LaMDA: our breakthrough conversation technology](https://blog.google/technology/ai/lamda/)
[^50-66]:[Pathways Language Model (PaLM): Scaling to 540 Billion Parameters for Breakthrough Performance](https://blog.research.google/2022/04/pathways-language-model-palm-scaling-to.html)
[^50-67]:[Introducing PaLM 2](https://blog.google/technology/ai/google-palm-2-ai-large-language-model/)
[^50-68]:[Introducing Gemini: our largest and most capable AI model](https://blog.google/technology/ai/google-gemini-ai/)
[^50-69]:[Introducing Claude](https://www.anthropic.com/index/introducing-claude)
[^50-70]:[Claude 2](https://www.anthropic.com/index/claude-2)
[^50-71]:[The Ultimate Guide to LLM Fine Tuning: Best Practices & Tools](https://www.lakera.ai/blog/llm-fine-tuning-guide)
[^50-72]:[Foundation Models and LLMs: a Complete Guide](https://kili-technology.com/large-language-models-llms)
[^50-73]:[ChatGPT sets record for fastest-growing user base - analyst note](https://www.reuters.com/technology/chatgpt-sets-record-fastest-growing-user-base-analyst-note-2023-02-01/)
[^50-74]:[The biggest blocker to LibreOffice adoption? LibreOffice.](https://www.dedoimedo.com/computers/libreoffice-adoption.html)
[^50-75]:[ChatGPTを統合したOfficeの新機能がすごすぎる](https://www.gizmodo.jp/2023/05/microsoft-365-copilot-new-feature.html)
[^50-76]:[A Comprehensive Survey on Applications of Transformers for Deep Learning Tasks](https://arxiv.org/abs/2306.07303)
[^50-77]:[Retrieval Augmented Generation (RAG) in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview)
[^50-78]:[What is Prompt Engineering?](https://aws.amazon.com/what-is/prompt-engineering/)
[^50-79]:[A Survey on Self-supervised Learning: Algorithms, Applications, and Future Trends](https://arxiv.org/pdf/2301.05712.pdf)
[^50-80]:[【初学者向け】対照学習（Contrastive Learning）とは？](https://aiacademy.jp/media/?p=1096)
[^50-81]:[A Cookbook of Self-Supervised Learning](https://arxiv.org/abs/2304.12210)
[^50-82]:[ADAM: A METHOD FOR STOCHASTIC OPTIMIZATION](https://arxiv.org/pdf/1412.6980.pdf)
[^50-83]:[Adam](https://d2l.ai/chapter_optimization/adam.html)
[^50-84]:[A Linearly-Convergent Stochastic L-BFGS Algorithm](https://arxiv.org/abs/1508.02087)
[^50-85]:[A fast quasi-Newton-type method for large-scale stochastic optimisation](https://www.sciencedirect.com/science/article/pii/S2405896320324630)
[^50-86]:[Dark Memory and Accelerator-Rich System Optimization in the Dark Silicon Era](https://arxiv.org/pdf/1602.04183.pdf)
[^50-87]:[AI Accelerators — Part II: Transistors and Pizza (or: Why Do We Need Accelerators)?](https://medium.com/@adi.fu7/ai-accelerators-part-ii-transistors-and-pizza-or-why-do-we-need-accelerators-75738642fdaa)
[^50-88]:[Embeddings: Translating to a Lower-Dimensional Space](https://developers.google.com/machine-learning/crash-course/embeddings/translating-to-a-lower-dimensional-space)
[^50-89]:[The Full Story of Large Language Models and RLHF](https://www.assemblyai.com/blog/the-full-story-of-large-language-models-and-rlhf/)
[^50-90]:[The Transformer Model](https://machinelearningmastery.com/the-transformer-model/)

# 4. 今後注目すべきAI技術関連動向
社会実装に向けた課題が増えている
## 4.1. AI倫理（AI Ethics）
AI倫理は、AIが責任を持って開発および使用されることを保証するために、関係者 (エンジニアから政府関係者まで) が使用する一連の指針で、AIに対して安心・安全なアプローチをとるための研究分野である[^60-1]。近年急激に注目度を増してきており[^60-2]、AI倫理の課題として下記の4点が挙げられている[^60-3]。
1. Explainability（説明可能性）
AIの推測理由を説明できる必要があるという課題。意思決定がAIによってどのように行われるかを理解する必要性が高まっており[^60-6]、金融やヘルスケアなどの分野で注目を集めている[^60-7]。DARPAはDeep Learningをはじめとする高パフォーマンスなAI技術が不透明であることを懸念し、AIを適切に信頼・効果的に管理するため、人間のユーザーに理論的根拠を説明できるAIシステムである**XAI**（eXplainable AI、説明可能AI）のプログラムを2017年に開始[^60-5]、EC（European Commision）がEthics guidelines for trustworthy AIを2019年に発表するなど[^60-8]、国家レベルでも重要な課題として認識されている。
代表的なXAIの手法例として下記の6種類を挙げる。
    - LIME（Local Interpretable Model-agnostic Explanations）
    2016年発表[^60-10]。機械学習モデルの入力データに変動を加えた時、予測（出力データ）にどのような変化が起こるかを検証し、その検証結果から局所的に機械学習モデルと同じ出力をするモデル（ローカルサロゲートモデル）を作成する手法[^60-9]。
    - SHAP（SHapley Additive exPlanations）
    2017年発表[^60-13]。協力型ゲーム理論での、各プレイヤーの課題に対する貢献度を算出するShapley値を、機械学習モデルが用いる特徴量の予測精度に対する貢献度として用いる[^60-12]。これにより、各予測に対して寄与度の高い特徴量を求める手法[^60-11]。
    - Anchor
    2018年発表[^60-14]。機械学習モデルの入力データに変動を加えた時、どれくらいの範囲が同じラベルになるかを検証し、If-Thenルールを作成する手法[^60-15] [^60-16]。
    - Grad-CAM（Graddient-weighted Class Activation Mapping）
    2016年発表[^60-17]。Computer Visionの分野で、特にCNNに対して用いられ、最後の畳み込み層に流入する勾配を分析することで、入力画像内の予測に寄与した重要な領域を強調表示するHeatmapを作成する[^60-18]。Score-CAM[^60-19]やGroup-CAM[^60-20]など様々な派生形も出現している。
    - DeepLIFT（Deep Learning Important FeaTures）
    2017年発表[^60-21]。BP法を用いて、ある入力に対する各ニューロン出力を基準とし、他の入力との出力の差を考えることで特徴量の効果を考えたうえで出力形成に大きな影響を与えたニューロンと重みを見つける[^60-22]。

    ただし、ユーザーによって求める説明が異なること（初心者と専門家に同じ説明をするのが適切ではない等）や、応答速度と説明精度のトレードオフ、継続的なメンテナンス性など、XAIの課題はまだまだ多い[^60-23]。それでも、、2020年のICMLではよりハイレベルな説明可能性をもったXAIとしてXXAI（eXtended XAI）のワークショップが実施されるなど、注目度は高まるばかりである[^60-24]。
1. Responsibility（責任性）
AIに基づく意思決定の結果に対する説明責任を誰がどうとるのか、という課題。
AIを使用してこれまで人間の介入が必要だったタスクを自動化および改善する企業が増えてきており[^60-27]、AIのガバナンスの側面から**RAI**（Responsible AI）として議論されることが多い。Google、Microsoft、IBMは、生成AIを含めたAIの規制を求め、既に独自のガバナンスフレームワークとガイドラインを構築しており[^60-27] [^60-26]、企業のエネルギーがAIの実践をより「責任」を重視する方向に注がれている[^60-28]。
    > **note**
    経済産業省の我が国のAIガバナンスの在り方（ver. 1.1）でAIガバナンスは「AIの利活用によって生じるリスクをステークホルダーにとって受容可能な水準で管理しつつ、そこからもたらされる正のインパクトを最大化することを目的とする、ステークホルダーによる技術的、組織的、及び社会的システムの設計及び運用」と定義されている[^60-25]

1. Fairness（公平性）
データセットに偏見（Bias）が入ってしまうという課題。
例えば、あるデータセットでAIが学習すると医者は男、看護師は女という偏見が入ってしまう[^60-4]、Amazonの採用候補者の選別AIが中立的な方法で評価していなかった[^60-29]等の事例がある。
Biasの入ったAI利用は、より大きなBiasを助長する可能性があるといった社会的問題もあり[^60-30]、アメリカのFederal Trade Commission（FTC）が、人種的に偏ったアルゴリズムの販売や法律に違反する可能性のある方法で使用しないよう警告するなどの対策が講じられている[^60-31]。

1. Misuse（不当利用性）
AIが作成目的以外の（危険な）利用のされ方をしてしまうという課題。
例えば、アメリカの大統領や韓国のニュースキャスターが虚偽のアナウンスをする動画が公開される事例がある[^60-36]。そのような現実に起こっていない画像や動画を生成する技術は**Deepfake**と呼ばれ[^60-35]、問題視されている[^60-33]。
他にも、パスワードの推測にAI技術が利用されるという研究も進んでいるなど[^60-32]、AI技術の適切な利用が必要になっている。

このように、AI技術の社会的な影響が大きくなっている昨今、技術（AIの出力する結果の精度）だけを追い求めておけばよいフェーズではなくなってきている。OpenAI社は、現時点では、近い将来登場すると予測される人間よりもはるかに賢いAIであるSuperintelligence（超知能）を制御、すなわちAIの不正行為を防ぐようなソリューションはないとし、ほぼ人間レベルの“automated alignment researcher”を構築すること目指したチームを結成するなど[^60-34]、AIでAIを監視させることを目指す動きも存在する。

[^60-1]:[AI Ethics: What It Is and Why It Matters](https://www.coursera.org/articles/ai-ethics)
[^60-2]:[AI Ethics: A Long History and a Recent Burst of Attention](https://www.computer.org/csdl/magazine/co/2021/01/09321834/1qmbkXCazy8)
[^60-3]:[AI ethics (AI code of ethics)](https://www.techtarget.com/whatis/definition/AI-code-of-ethics)
[^60-4]:[“AI のゴットファーザー”と称される研究者が Google を退社して人工知能に関する懸念を表明](https://hypebeast.com/jp/2023/5/geoffrey-hinton-godfather-of-ai-quit-google)
[^60-5]:[DARPA’s Explainable Artificial Intelligence Program](https://ojs.aaai.org/aimagazine/index.php/aimagazine/article/view/2850/3419)
[^60-6]:[XAIR: A Systematic Metareview of Explainable AI (XAI) Aligned to the Software Development Process](https://www.researchgate.net/publication/367081479_XAIR_A_Systematic_Metareview_of_Explainable_AI_XAI_Aligned_to_the_Software_Development_Process)
[^60-7]:[Explainability as the key ingredient for AI adoption in Industry 5.0 settings](https://www.frontiersin.org/articles/10.3389/frai.2023.1264372/full)
[^60-8]:[Ethics guidelines for trustworthy AI](https://digital-strategy.ec.europa.eu/en/library/ethics-guidelines-trustworthy-ai)
[^60-9]:[5.7 Local Surrogate (LIME)](https://hacarus.github.io/interpretable-ml-book-ja/lime.html#lime)
[^60-10]:["Why Should I Trust You?": Explaining the Predictions of Any Classifier](https://arxiv.org/abs/1602.04938)
[^60-11]:[SHAP を用いて機械学習モデルを説明する](https://www.datarobot.com/jp/blog/explain-machine-learning-models-using-shap/)
[^60-12]:[Explaining AI - The Key Differences Between LIME and SHAP Methods](https://safjan.com/explaining-ai-the-key-differences-between-lime-and-shap-methods/)
[^60-13]:[A Unified Approach to Interpreting Model Predictions](https://arxiv.org/abs/1705.07874)
[^60-14]:[Anchors: High-Precision Model-Agnostic Explanations](https://homes.cs.washington.edu/~marcotcr/aaai18.pdf)
[^60-15]:[説明可能なAI（Explainable AI：XAI）の各手法調査(2)](https://zenn.dev/pluck/articles/c5360fab91ca53)
[^60-16]:[9.4 Scoped Rules (Anchors)](https://christophm.github.io/interpretable-ml-book/anchors.html#fn61)
[^60-17]:[Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization](https://arxiv.org/abs/1610.02391)
[^60-18]:[Visualizing Model Insights: A Guide to Grad-CAM in Deep Learning](https://www.analyticsvidhya.com/blog/2023/12/grad-cam-in-deep-learning/)
[^60-19]:[Score-CAM: Score-Weighted Visual Explanations for Convolutional Neural Networks](https://arxiv.org/abs/1910.01279)
[^60-20]:[Group-CAM: Group Score-Weighted Visual Explanations for Deep Convolutional Networks](https://arxiv.org/abs/2103.13859)
[^60-21]:[Learning Important Features Through Propagating Activation Differences](https://arxiv.org/abs/1704.02685)
[^60-22]:[Explainability and Auditability in ML: Definitions, Techniques, and Tools](https://neptune.ai/blog/explainability-auditability-ml-definitions-techniques-tools)
[^60-23]:[Survey on Explainable AI: From Approaches, Limitations and Applications Aspects](https://link.springer.com/article/10.1007/s44230-023-00038-y)
[^60-24]:[xxAI - Beyond Explainable AI](https://link.springer.com/book/10.1007/978-3-031-04083-2)
[^60-25]:[我が国の AI ガバナンスの在り方 ver. 1.1](https://www.meti.go.jp/shingikai/mono_info_service/ai_shakai_jisso/pdf/20210709_1.pdf)
[^60-26]:[What Is ‘Responsible AI’ And Why Is Big Tech Investing Billions In It?](https://www.forbes.com/sites/saibala/2023/05/29/what-is-responsible-ai-and-why-is-big-tech-investing-billions-in-it/?sh=4bcca71e227c)
[^60-27]:[Responsible AI: Ways to Avoid the Dark Side of AI Use](https://www.altexsoft.com/blog/responsible-ai/)
[^60-28]:[Companies Committed to Responsible AI: From Principles towards Implementation and Regulation?](https://link.springer.com/article/10.1007/s13347-021-00474-3)
[^60-29]:[Amazon Scraps Secret AI Recruiting Engine that Showed Biases Against Women](https://www.ml.cmu.edu/news/news-archive/2016-2020/2018/october/amazon-scraps-secret-artificial-intelligence-recruiting-engine-that-showed-biases-against-women.html)
[^60-30]:[Fairness in AI and Its Long-Term Implications on Society](https://arxiv.org/abs/2304.09826)
[^60-31]:[AI & Fairness Metrics: Understanding & Eliminating Bias](https://councils.forbes.com/blog/ai-and-fairness-metrics#tag=tech)
[^60-32]:[Malicious Uses and Abuses of Artificial Intelligence](https://documents.trendmicro.com/assets/white_papers/wp-malicious-uses-and-abuses-of-artificial-intelligence.pdf)
[^60-33]:[Misuse of technology to create deepfakes threat to society: President Murmu](https://www.thehindu.com/news/national/misuse-of-technology-to-create-deepfakes-threat-to-society-president-murmu/article67597935.ece)
[^60-34]:[OpenAI、“スーパーインテリジェンス”の人類の敵化防止を目指す新チーム立ち上げ](https://www.itmedia.co.jp/news/articles/2307/06/news127.html)
[^60-35]:[What Are Deepfakes and How Are They Created?](https://spectrum.ieee.org/what-is-deepfake)
[^60-36]:[Deepfakes: The new face of fraud](https://withpersona.com/blog/what-are-deepfakes)

## 4.2. マルチモーダル化
さまざまなタスクに対する機械学習のデータセットのサイズは増え続けており、言語系では1兆点を超えるデータが利用されるようになってきている[^70-1]。そんな中、複数種類のデータを用いた**マルチモーダル**AIの注目度が高まっている。特に、**VLM**（Vision-Language Model）と呼ばれる、大規模な画像-テキストペアのデータセットを学習データとして用いる機械学習モデルに関する研究が盛んで[^70-2]、OpenAI社の[CLIP](https://openai.com/research/clip)（Contrastive Language–Image Pre-training）などが有名である。
その他にも、音声-動画のデータセットからの音声認識や感情認識のタスクに取り組むAIの研究もおこなわれている[^70-2]。
さらに、IoTデバイスで収集されたデータや[^70-3]、メタバースで収集されたデータが利用されるなど（[DAO・メタバースに関する私見](https://medium.com/@ttnt.1013/the-potential-effect-of-daos-on-the-future-7d56b665da73)）、新しいタスクへの展開も考えられる。

[^70-1]:[Trends in Training Dataset Sizes](https://epochai.org/blog/trends-in-training-dataset-sizes)
[^70-2]:[Multimodal Machine Learning:A Survey and Taxonomy](https://arxiv.org/pdf/1705.09406.pdf)
[^70-3]:[Unsupervised Deep Learning for IoT Time Series](https://arxiv.org/pdf/2302.03284.pdf)

## 4.3. ハードウェアの進化
AIを実行するプロセッサとしてGPUが主流であったが、ニューラルネットワークの複雑化や、ネットワーク規模が増大することによる消費電力の問題が懸念される[^80-1]。さらに、自動運転車に搭載する画像処理などには、より高速な処理が必要とされる[^80-2]。そこで、ニューラルネットワーク等のAIアルゴリズムの実行に特化したプロセッサとして**NPU**（Neural Processing Unit）の開発が進められている[^80-3]。NPUは多くの場合AIアルゴリズムのアクセラレータとして働き[^80-4]、Google社のTPU（Tensor Processing Unit）、Apple社のNE（Neural Engine）等が有名である。また、メモリアクセス速度と計算量を確保するため、従来のGPUの50倍以上の大きさのチップを作成する（Cerebras社）[^80-5] [^80-6]、アナログ・インメモリコンピューティング技術を用いる（IBM社）[^80-7]など、様々なアプローチでAI専用Chipへの取り組みが行われている。
また、**量子コンピューティング**もAI技術への応用が期待されている[^80-8]。実用的な量子コンピュータの実現にはまだまだ課題が多いが[^80-9]、最適化問題に特化した量子アニーリング技術を現行のコンピュータで実行可能にした**疑似量子アニーリング**技術により、実用問題の解決事例がすでに発表されている[^80-10] [^80-11]。

[^80-1]:[From GPUs to NPUs: Evolution of AI hardware in smartphones](https://indianexpress.com/article/technology/tech-news-technology/gpu-npu-role-ai-smartphones-9040864/)
[^80-2]:[The Evolution of Neural Processing for Embedded Applications](https://www.synopsys.com/designware-ip/technical-bulletin/neural-processor-npx-ip.html)
[^80-3]:[What is Neural processing unit (NPU)?](https://iq.opengenus.org/neural-processing-unit-npu/)
[^80-4]:[Unlocking the Power of NPUs: Transforming Smartphone AI and Machine Learning](https://medium.com/@craigadebanji46/unlocking-the-power-of-npus-transforming-smartphone-ai-and-machine-learning-1542effddc90)
[^80-5]:[Scaling AI at Cerebras](https://conferences.oreilly.com/artificial-intelligence/ai-ca-2019/cdn.oreillystatic.com/en/assets/1/event/298/Scaling%20AI%20at%20Cerebras%20Presentation.pdf)
[^80-6]:[Why We Need Big Chips for Deep Learning](https://www.cerebras.net/blog/cerebras-wafer-scale-engine-why-we-need-big-chips-for-deep-learning/)
[^80-7]:[IBM Research's latest analog AI chip for deep learning inference](https://research.ibm.com/blog/analog-ai-chip-inference)
[^80-8]:[Quantum Artificial Intelligence Is Closer Than You Think](https://www.forbes.com/sites/jonathanreichental/2023/11/20/quantum-artificial-intelligence-is-closer-than-you-think/?sh=7a829ebc4818)
[^80-9]:[Why don’t we have Quantum Computers already?](https://tomrocksmaths.com/2023/04/19/why-dont-we-have-quantum-computers-already/)
[^80-10]:[NEC　ベクトルアニーリング活用で業務効率化の効果を実証「CEATEC AWARD 2022」トータルソリューション部門 準グランプリ受賞](https://exp.ceatec.com/related/ceatecnews_vol44/)
[^80-11]:[CMOSアニーリングによる信号機制御で渋滞解消など、日立がデモ展示](https://xtech.nikkei.com/atcl/nxt/column/18/01537/00602/)

## 4.4. AI開発の自動化・自律化
学習率、ニューラル ネットワークの隠れ層の数、正則化の強度など、モデルの動作を制御する**ハイパーパラメータ**の設定は、かなりの専門知識と経験を必要とするため、ハイパーパラメーターの最適な組み合わせを自動的に検索し、自動的に機械学習モデルを生成するシステム[^90-3]が注目されている。AIが生成したAIをChild AIと呼ぶこともあり、例えばGoogle社のAutoML、オープンソースのPythonライブラリであるAuto-SklearnやAutoKerasなどが有名である。
またIndustrie 4.0では、物理世界とサイバー世界が相互作用するコンセプトであるCPS（Cyber Physical System）が提唱されている。このCPSを制御し、自律的に動作させるAI技術が考えられている[^90-1] [^90-2]。そして継続的にデータを収集し、自律的に改善を行っていくCPSにAIが組み込まれた場合、AIの改善が自動化されることは容易に想像できる。

> **note**
>製造業におけるCPSの一例として、下記のような継続的な最適化を行う流れが挙げられる。
>1. ロボットの動作をセンサーで取得する
>1. データをIIoT（Industrial IoT）技術により収集・蓄積する
>1. その情報をもとにロボットのDigital Twinを更新する
>1. Digital Twinを用いて制御シミュレーションを行う
>1. AIにより制御方法の最適化を行う
>1. 最適化された制御方法をロボットコントローラへ適用する
>1. ロボットの動作をセンサーで取得する（以下、繰り返し）

![AI automation](/images/ai_history/ai_automation.png)
*AI開発の自動化・自律化の流れ*

[^90-1]:[Supporting AI-powered real-time cyber-physical systems on heterogeneous platforms via hypervisor technology](https://link.springer.com/article/10.1007/s11241-023-09402-4)
[^90-2]:[When Cyber-Physical Systems Meet AI: A Benchmark, an Evaluation, and a Way Forward](https://arxiv.org/abs/2111.04324)
[^90-3]:[AutoML](https://www.run.ai/guides/automl)
[^90-4]:[Can an AI Create Another AI?](https://techevaluate.com/can-an-ai-create-another-ai/)

# 5. おわりに
AI技術の進展はとどまるところを知らないどころか、どんどん加速している。
そのため、現時点の最新技術が何かを拾うだけではなく、技術的な背景を頭に入れたうえで動向をキャッチアップし、現状を整理していくことでより適切にAI技術をとらえやすくなる。
また、技術的にAIを見る際には、本来は数学的な視点からも発明の変遷を辿るのがベストだが、本記事で記したような状況や背景の全体感を把握をしておけば詳細に入りやすいのではないかと思う。

## 補足：もうちょっと調べたい項目（追記する可能性あり）
調査しきれていない部分もあるので、割愛した部分を加えて電子書籍化に挑戦してみてもよいかも
- 動向
    - 初期のニューラルネットワーク
        - [History: The 1940's to the 1970's](https://cs.stanford.edu/people/eroberts/courses/soco/projects/neural-networks/History/history1.html)
        - Hopfiled networkの計算効率の悪さ
            - [Introduction to Neural Network Models of Cognition](https://com-cog-book.github.io/com-cog-book/features/recurrent-net.html#Historical-and-theoretical-background)
        - RosenblattのPerceptronのOptimizer
            - [PERCEPTRON IS NOT SGD: A BETTER INTERPRETATION THROUGH PSEUDOGRADIENTS](https://parameterfree.com/2021/02/14/perceptron-is-not-sgd-a-better-interpretation-through-pseudogradients/)
            - [A Perceiving and recognizing automaton](https://blogs.umass.edu/brain-wars/files/2016/03/rosenblatt-1957.pdf)
            - [THE PERCEPTRON: A PROBABILISTIC MODEL FOR INFORMATION STORAGE AND ORGANIZATION IN THE BRAIN](https://www.academia.edu/60542953/The_perceptron_a_probabilistic_model_for_information_storage_and_organization_in_the_brain)
            - [Optimization: Stochastic Gradient Descent](http://deeplearning.stanford.edu/tutorial/supervised/OptimizationStochasticGradientDescent/)
    - ELIZA効果
    - Game理論との関連性
        - [Artificial Intelligence for Games](https://www.lamsade.dauphine.fr/~cazenave/papers/games.pdf)
    - [more Moore, more than moore](http://www.itrs2.net/uploads/4/9/7/7/49775221/irc-itrs-mtm-v2_3.pdf)
    - GAFAの動き
        - [Facebook’s artificial intelligence research team, FAIR, turns five. But what are its biggest accomplishments?](https://hub.packtpub.com/facebooks-artificial-intelligence-research-team-fair-turns-five-but-what-are-its-biggest-accomplishments/)
        - [GROWING UP WITH ALEXA, SIRI, AND OTHER A.I. TECHNOLOGY](https://sites.bu.edu/cmcs/2017/11/16/growing-up-with-alexa-siri-and-other-a-i-technology/)
- アーキテクチャ
    - Probabilistic AI
    - Neuro Symbolic AI
    - PIML（Physics Informed Machine Learning）
    - Expert System
        - なぜExpert System開発がコンパイル言語とマッチしなかったのか
        - Forward chainとBackward chain
    - Auto encoderと制限付きボルツマンマシンの関係性
- 学習・最適化
    - HeuristicsとReasoning searchの違い
    - Forward searchとBackward search
    - Meta学習
    - 強化学習
        - Mean field
        - Monte calro
        - Q-learning
    - Ensemble学習
        - Stacking
        - Ensemble Deep Learning
    - Zero-shot学習、One-shot学習、A few-shot学習
    - LBFGS以外の高次法
        - LSRI
- その他
    - Symbolの厳密な解釈
    - Turing machineとUniversal Turing Machineの違い
    - EntscheidungsproblemとHilbertの23の問題のうち第2問題にも関連している？（Church-turing thesis）
    - Research and Development (RAND) Corporationの詳細
    - AstrocyteとTransformerの関係
    - 進化的計算
        - [進化的計算](https://www.ai-gakkai.or.jp/resource/my-bookmark/my-bookmark_vol19-no3/)

# 参考
https://en.wikipedia.org/wiki/History_of_artificial_intelligence
https://en.wikipedia.org/wiki/History_of_artificial_neural_networks
https://ourworldindata.org/brief-history-of-ai
https://www.javatpoint.com/history-of-artificial-intelligence
https://www.coe.int/en/web/artificial-intelligence/history-of-ai
https://www.g2.com/articles/history-of-artificial-intelligence
https://www.dataversity.net/brief-history-deep-learning/
https://www.holloway.com/g/making-things-think/sections/the-birth-of-artificial-intelligence-19521956
https://aiqom.ai/en/blogs/The-Evolution-of-Artificial-Intelligence
https://www.sparkfun.com/news/7896
https://www.techslang.com/definition/what-is-an-ai-accelerator/
https://www.sciencedirect.com/science/article/pii/S1566253523001148

[^20-1]: [人工知能用言語 Lispの今と将来](https://www.jstage.jst.go.jp/article/jjsai/24/5/24_681/_pdf)
