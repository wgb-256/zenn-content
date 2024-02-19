---
title: "生成AI・ChatGPTに支配される前に、押さえるべきAI事情（1,2,4,5章）"
emoji: "🧠"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["機械学習", "AI", "初心者"]
published: true
---

# 章立て
1. はじめに
1. AI研究の全体像
    **2.1.** AIが担うタスク
    **2.2.** AIと従来プログラムの違い
    **2.3.** AI技術のカテゴリ・分類
    **2.4.** AI研究の視点
1. [AI技術関連史](https://zenn.dev/ttnt_1013/articles/071ea20ac01031)
    **3.1.** ~ 1957年ごろ：「AI」誕生
    **3.2.** 1957~1980年ごろ: Logic-based AI
    **3.3.** 1980~1993年ごろ：Knowledge-based AI
    **3.4.** 1993~2012年ごろ：Machine Learning
    **3.5.** 2013年ごろ以降 ：Deep Learning
1. 今後のAI技術について
    **4.1.** AI倫理（AI Ethics）
    **4.2.** マルチモーダル化
    **4.3.** ハードウェアの進化
    **4.4.** AI開発の自動化・自律化
1. おわりに

# 1. はじめに
AIに支配されうる未来が見え始めている。
ChatGPTをはじめとする生成AIにより、技術者に限らず、AIに頼らざるを得ない状況になった。技術進展スピードと影響力を考えると、より一層AIが影響を与える範囲は広がっていくことは間違いない。しかし発展が目まぐるしく、高度すぎる技術になっているため、一朝一夕では最新のAI技術についてキャッチアップすることはできなくなっており、よくわからないままAIに触れることになってしまったり、AIという技術が実はとっつきにくいものになってしまった。
その結果、上辺だけのAI議論、過剰な期待・恐怖、不適切な利用を招いてしまう危険がある。そしてそんなことをしているうちにAIがより高度になり、気づかないうちにAIが人間を支配、すなわち単独で人間社会を最適化し始めるということは、もはや起こりえない夢の話ではなくなってきている。したがって、AIという「技術」に対してより根本的な部分から向き合うことは今後大変重要になってくる。本記事では、これからAIの勉強を始めたい人や再度情報の整理をしたい人に向け、AI界隈の状況について調査し、まとめた。

# 2. AI研究の全体像
## 2.1. AIが担うタスク
現実世界で用いられるAIは、人間の補助（人間の仕事を手伝う）・代替（人間の代わりに仕事をする）・拡張（人間よりも高度な仕事をする）という立ち位置であることが多い。次章で述べるが、AIの発端は「人間のような知的な機械」という発想である。したがって、AIが担うタスクは、基本的には人間の活動になぞらえればよいと考えられる。具体的には、入力（見る・聞く・読む 等）により得た情報を処理し（考える）、出力（意思決定・認識・分類・話す・書く 等）を行うことになる。

![AIのタスク](/images/ai_history/AITask.png)

> **note**
嗅覚・触覚・味覚に関するセンサーが一般的でなくそれらを入力とするAIはまだ少ないため、記載していない。今後、それらに加え雰囲気・第六感のような曖昧で高度な情報も取り扱われる可能性も十分ある。

## 2.2. AIと従来プログラムの違い
現状、AIは基本的にソフトウェア、特にコンピュータプログラムである。あるプログラムがAIであるというためには何が必要か、私見を述べる。今回の調査を通して、AIプログラムは「推論（Reasoning）」または「推測（Inference）」を行っていると考えられる。
推論とは、利用可能な情報（証拠・過去事例等）から、結論や新しい情報を導く思考過程であり、推測とは、与えられた情報を越えた判断である[^2-1]。したがって、あらかじめ決まっている情報に対して、不変の処理を行い、想定通りの結論を得るプログラムはAIとは言えない。
例えば、電卓のようにプログラムに入力される値に制限があり、それに対してどのように処理するかを、設計者がすべて把握できるプログラムはAIとは呼べない。逆に、何が入力されるかわからない状況で、どのように対処するのかのみを手続き化したプログラムはAIと呼べる。
後述のLogic-based AIは論理的な思考プロセスをプログラム化し、Knowledge-based AIは専門家の知識を体系化して論理をプログラム化し、Machine Learningはデータから何らかのルールを抽出してプログラム化している。よって、推論または推測が複雑（例えば、人間が論理を立てられない、入力の次元が大きい等）であればあるほど、高度なAIと主張できると考えらえる。

[^2-1]:[推論(reasoning, inference)](https://cogpsy.educ.kyoto-u.ac.jp/personal/Kusumi/inference.htm)

## 2.3. AI技術のカテゴリ・分類
### 2.3.1. 思想によるAI実現アプローチの分類
AIを実現するためのアプローチは、基盤とする思想の違いで分類することができる。本節では、中でも大きな潮流であるSymbolic AIとConnectionist AIを中心に述べる。
![AI Categories](/images/ai_history/ai_categories.png)
*AI分類*
#### Symbolic AI
Symbol操作を用いて人間の思考プロセスをプログラム化するいう思想に基づいたAIであり[^10-42] [^3-3]、推測の論理規則によるSymbol処理を行うSymbolicism（象徴主義）的なアプローチ[^3-9]。
1976年にAllen NewellとHerbert Simonから発表された、知能を記号（Symbol）処理によって表現し得るというPhysical Symbol System Hypothesis（物理記号システム仮説）に基づいている[^3-1] [^3-2]。
主に検索木とHeuristicsを用いた最も初期に発展した古典的なアプローチは、特にGOFAI（Good Old-Fashioned AI）と呼ばれ、明示的なロジックに基づいており、説明性が高いとして有用性を主張される場合もある[^3-4] [^3-6]。
これらは、基本的に手作業でアルゴリズムの最適化が行われる[^3-7]。

> **note**
>Symbolic AIの文脈で、SymbolismとSymbolicismのどちら思想も取り上げられる場合があるが[^3-8] [^3-9]、[この記事](https://thecontentauthority.com/blog/symbolism-vs-symbolicism)の _Symbolicismは、システムまたは理論におけるSymbolまたはSymbolic Elementの使用を指す。_ という定義から、今回はSymbolisicmを用いた。

#### Connectionist AI
ニューロンの数学モデルを用いて人工ニューラルネットワーク（ANN: Artificial Neural Network）を構成する手法であり[^10-49]、ANNを利用して知的能力を説明しようとするConnectionism的なアプローチ[^3-10]。Subsymbolic AIとも呼ばれる[^3-5]。
##### Machine Learning（機械学習）
人間がルールを作らずに機械に学習能力を与える研究分野。特に、既存のデータから何らかの関係性やパターンの発見に焦点をおいており[^3-11]、人力では取り扱いが不可能なほどの膨大な量のデータ（Big Data）からモデル（Data-Driven model）を得られることが大きなメリットとなる。ただし昨今では、モデルのブラックボックス性（データから得た学習アルゴリズムを人間が説明できないこと）が問題となる場合も多い。
##### Deep Learning（深層学習）
機械学習の中でも、3層以上の多層ニューラルネットワークを用いてモデルを構築する分野[^3-12]。多層にすることでモデルの表現力が上がり、より高度なアルゴリズムを得ることができる一方、ネットワークの最適化が難しいこと、多大な計算リソースを要すること等が課題として挙げられる。
#### その他のアプローチ
##### Neuro-Symbolic AI
Symbolic AIの記号推論（Symbolic Reasoning）とConnectionist AIのニューラルネットワークの技術を組み合わせ、それぞれの認知能力と説明性を補完しようとするアプローチ[^3-13]。Symbolを用いた論理的な表現をニューラルネットワークに焼き直す手法と、ニューラルパターンから情報を抽出してSymbol表現へマッピング後、Symbolic Reasoningを行う手法の2つに大別される[^3-14]。
##### Actionist AI
機械の自動制御や動物の神経系機能の類似性や関連性をテーマとする人工頭脳学（Cybernetics）[^3-15]を由来とし、知性は認識・行動に依存し、知識・表現・推論は必要ないという思想であるActionism的なアプローチ[^3-16]。外部環境との相互作用に基づいて、環境フィードバックを自律的に認識して適切な行動を行うことによって知的行動が完成すると置いている[^3-17]。
###### 強化学習（Reinforcement Learning）
特定の環境（Environment）で報酬（Rewards）を最大化するために適切な行動（Action）をとることを目的としてプログラム（Agent）を学習させる、環境と相互作用する自己評価学習手法[^3-19] [^3-17]。（大規模な）データセットが不要であるため、学習データに依存せず複雑な振る舞いをモデル化することができるなどの利点を持つ[^3-20]。機械学習の一種とも言うことができる[^3-18]。

>![Reinforcement Learning](https://miro.medium.com/v2/resize:fit:2000/format:webp/0*WC4l7u90TsKs_eXj.png)
*Reinforcement Learning（引用:[^3-19]）*

###### 進化的計算（Evolutionary Computation）
変化する環境に適応するために、多大な可能性から解決策を探索する進化（Evolution）のプロセスを[^3-21]、計算上の問題（特にここではAIの最適化）に応用する手法。主なアルゴリズムとして、遺伝的アルゴリズム（Genetic Algorithm: GA）等が挙げられる。

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
AIに関する研究開発のうち現在最も活発なのは機械学習の分野である。そしてその中でも、およそ本節で挙げる3つの視点での研究活動が行われている[^7-2]（ただし、それぞれ影響を与え合っているため、各取り組みをそれぞれに分類することは難しい）。
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
どのようにAIアルゴリズムを最適化するか、多くの場合ニューラルネットワークパラメータをどのように決めるかという視点[^7-1]。最適化は、利用されるニューラルネットワークが大規模になるにつれ困難であることもあり[^7-3]、昨今非常に活発に研究が行われている。主な課題は、勾配爆発・勾配消失等による解の収束に関する問題、収束速度に関する問題、局所解（Local minima）の取り扱いに関する問題などである[^7-2]。

>![The historical tree of developing optimization algorithms from 1950 to 2022.](/images/ai_history/optimization_timeline.png)
*The historical tree of developing optimization algorithms from 1950 to 2022（引用:[^7-5]）*

>![Local minima and Global minima](https://blog.paperspace.com/content/images/2018/05/challenges-1.png)
*Local minima and Global minima in Optimization（引用:[^7-4]）*

[^7-1]:[Why Optimization Is Important in Machine Learning](https://machinelearningmastery.com/why-optimization-is-important-in-machine-learning/)
[^7-2]:[Optimization for deep learning: theory and algorithms](https://arxiv.org/abs/1912.08957)
[^7-3]:[Thick-Net: Parallel Network Structure for Sequential Modeling](https://arxiv.org/abs/1911.08074)
[^7-4]:[Intro to optimization in deep learning: Gradient Descent](https://blog.paperspace.com/intro-to-optimization-in-deep-learning-gradient-descent/)
[^7-5]:[Survey of Optimization Algorithms in Modern Neural Network](https://www.mdpi.com/2227-7390/11/11/2466)

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

第3章の内容については、下記のリンクを参照ください。
@[card](https://zenn.dev/ttnt_1013/articles/071ea20ac01031)

# 4. 今後注目すべきAI技術関連動向
本章では、特に今後注目すべきAI技術関連の4つトピックについて述べる。AIの精度が向上してきており、本格的な社会実装に対する課題が増えている。
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
AIの技術進展はどんどん加速している。
そのため、現時点の最新技術が何かを拾うだけではなく、技術的および社会的な背景を頭に入れたうえで動向をキャッチアップし、現状を整理していくことでより適切にAI技術をとらえやすくなる。
また、技術的にAIを見る際には、本来は数学的な視点からも発明の変遷を辿るのがベストだが、本記事で記したような状況や背景の全体感を把握をしておけば詳細に入りやすいのではないかと思う。

## 補足：もうちょっと調べたい項目（追記する可能性あり）
割愛した部分を加えて電子書籍化に挑戦するかも
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
[^10-42]: [Symbolic artificial intelligence in *Wikipedia*](https://en.wikipedia.org/wiki/Symbolic_artificial_intelligence)
[^10-49]: [Symbolic vs Connectionist A.I.](https://towardsdatascience.com/symbolic-vs-connectionist-a-i-8cf6b656927)