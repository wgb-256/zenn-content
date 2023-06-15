---
title: "ChatGPTに支配される前に、押さえるべきAI・機械学習事情"
emoji: "🧠"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["機械学習", "AI", "初心者"]
published: false
---

# 章立て
1. はじめに
1. 機械学習研究の全体像
1. AI技術関連史
1. 論文を読むにあたって
1. おわりに

# はじめに
ChatGPTの勢いがすごい。テキトーに使っていては振り回される

# AI技術関連史
AI技術に対する期待とは

##  ~ 1957（AI創生期）
17世紀に活躍したドイツの学者[Gottfried Wilhelm Leibniz](https://en.wikipedia.org/wiki/Gottfried_Wilhelm_Leibniz)は、安全・時間浪費の観点から計算は人間ではなく機械がするべきであるという考え方を持っており、[Pascalの計算機](https://en.wikipedia.org/wiki/Pascal%27s_calculator)をもとにして、長さの異なる歯をもつシリンダーと移動式の歯車を組み合わせて計算（基本的には自然数の四則演算）を可能にしたStepped reckonerまたはLeibniz Wheel（ライプニッツの車輪）と呼ばれる手動機械式の計算機を、1694年に完成させた[^10-4] [^10-5]。これをきっかけにLeibnizは、数学的記述（mathmatical statement、詳細は以下の**note 1**を参照）の真理値を決定できる機械を作ることができるのではないかと考えるようになった。それが実現できると、機械が論理を扱うことができるようになるため、どういう場合には何をするといった**場合分け処理**や、明確な理由がある**推論**といった[^10-8]、より知的な処理が可能になる。機械が論理を扱うためには、人間が自然に行っているコミュニケーションのような、曖昧さが残る表現やその時によって用法・意味が変わるような**自然言語**（natual langage）ではなく、文法・意味が形式的に与えられて明確に論理が展開できる**形式言語**（formal language）が必要であると考え、Leibnizの研究は形式言語を用いた**形式理論**（formal theory）にも重きが置かれるようになっていった。さらに、Leibnizは活動の中で、現代のコンピュータの基礎となっている2進数演算（binary arithmetics）や[^10-9]、2進数コンピュータ（binary computer）についても功績を残している[^10-10]。

> **note 1**
数学的記述（mathmatical statement）は、正しい（真）か間違っている（偽）かが判断できる「文」であり、言葉や記号（symbol）が含まれる。例えば、言葉を使った「1は2よりも大きい」や、記号を使った「1>2」という文は、「偽」であるmathmatical statementである。

Leibnizの論文がドイツのHannoverで閲覧可能になった1830年代以降、その注目度は急速に高まり、Johann Eduard ErdmannやKurt Gödelなど後の研究に多大な影響を与える[^10-11] [^10-12]。この頃、数学界では数学理論を構築するための演繹的な方法（すでに知られている法則（一般論・ルール）や前提から、階段を登っていくように論理を積み重ねて結論を出す考え方[^10-13]）に注目が集まっており、数学における形式理論（公理理論ともいう）に関する新しい問題が提起されていた[^10-14]。1928年、ドイツの数学者であるDavid HilbertとWilhelm Ackermannは、**Entscheidungsproblem**（ドイツ語。日訳で決定問題、英訳でdecision problem）と呼ばれる、「（一階論理の）すべての数学的記述は、導出可能か」（すべての公理を考慮すれば、命題が証明可能かどうかを判断できるアルゴリズムが存在するかどうか）という問題を提起した[^10-15]。この問題は、「人間の思考プロセスをすべて単純なアルゴリズムで表現することは可能か」と言い換えることができ[^10-18]、もしそのようなことが可能であれば、.......

Note that in its original form (Hilbert & Ackermann 1928), the problem was stated in terms of validity rather than derivability. Given Gödel’s completeness theorem (Gödel 1929) proving that there is an effective procedure (or not) for derivability is also a solution to the problem in its validity form. In order to tackle this problem, one needs a formalized notion of “effective procedure” and Turing’s machines were intended to do exactly that

> **note 2**
数学者や数学団体は自身が発案・直面した未解決問題を公開し、研究を生み出してきた。1900年にHilbertが、パリで開催された国際数学者会議（International Congress of Mathematicians: ICM）および彼の著作で、次の世紀に研究されるべき23の主要な数学的問題が発表された[^10-1] [^10-2] [^10-3]。Entscheidungsproblemは[Hilbertの23の問題](https://ja.wikipedia.org/wiki/%E3%83%92%E3%83%AB%E3%83%99%E3%83%AB%E3%83%88%E3%81%AE23%E3%81%AE%E5%95%8F%E9%A1%8C)のうち、[Diophantine方程式](https://en.wikipedia.org/wiki/Diophantine_equation)に解があるかどうかを決定するアルゴリズムを求める第10問題に関連している。（**第2問題も？？** // Church-turing thesis）

1935年、HilbertのEntscheidungsproblemに興味を持ったAlan Turingは、任意の数学的記述の導出に必要な「形式化された手順」が必要である、として研究を開始した。すなわち、どんな数学的記述も導出できる手順が存在するということは、どんな数学的記述も証明可能であると言える、という考え方である。Turingは翌1936年に発表した論文[^10-22]で、そういう手順が可能である仮想的な機械（UTM: **Universal Turing machine**[^10-26]）を考案し、Entscheidungsproblemが成り立たたないことを証明した[^10-17] [^10-18] [^10-19] [^10-20]。Turingのアプローチで独創的だったのは、UTMを考案するにあたり、それまで発明されていた「機械」に注目するのではなく、子供が勉強で使う方眼紙や何か手順を踏むときの人間の思考など、「人間」に注目した上で、実行する手順を徹底的に曖昧さがない論理的な処理に落とし込んだことである[^10-21]。
UTMの論理性は、1943年に発表された、神経生理学者Warren McCullochと数学者Walter Pittsによるニューロンの数学モデル（MPニューロン、MCPニューロンと呼ばれる）およびそれにより構成されるニューラルネットワークモデルの考案のためのインスピレーションをもたらし[^10-23] [^10-47]、UTMの構成（**note 4**参照）は、Machineへの命令を入力データと同じ記憶領域に配置するstored-program方式と呼ばれ、1945年にアメリカの学者John von Neumannにより発表されたコンピュータの構成（ノイマン型アーキテクチャ、von Neumann model、Princeton architectureなどと呼ばれる）にも強い影響を与えるなど[^10-24] [^10-25] [^10-26]、多大な影響を与えることとなった。
ノイマン型アーキテクチャが発表された1945年末には、世界初の「プログラム可能な（命令の与え方によって様々なタスクをこなすことができる）」計算機であるENIAC（Electronic Numerical Integrator and Computer）[^10-27] [^10-28]、1948年には世界で初めてノイマン型アーキテクチャで動作するManchester Baby（SSEM: Small-Scale Experimental Machineとも呼ばれる）など[^10-29] [^10-30]、続々と電子計算機（以降、コンピュータ）が一般化し（なんでもできるようになり）、同時に高性能化していった。
さらに1951年には、Marvin MinskyとDean Edmondsが、SNARC（Stochastic Neural Analog Reinforcement Calculator）という世界で初めて人工ニューラルネットワークを実装したコンピュータを構築している。SNARCのニューラルネットワークは、MPニューロンの考え方を拡張したHebb理論に基づいており、**学習**することができるようになっている。
Hebb理論は、1949年にカナダの心理学者Donald Olding Hebの[著書](https://pure.mpg.de/rest/items/item_2346268_3/component/file_2346267/content)で提唱された[^10-48]、ニューロンの数学モデルの学習ルールとそのアルゴリズムを含む理論である。複数のニューロンをつなげて作ったニューラルネットワークで、MPニューロンではニューロン間の線が扱える値は0と1のみだったため、ロジックを変えるにはニューロンの接続を変える必要があった。しかし、Hebbが提唱したモデルでは各ニューロン間の接続強度（以降、重み）を設定し0~1の数を扱えるようにすることで、重みを調整してロジックが変えられるようになった。したがって、所望のロジックを得るために重みを調整することを、**学習**と呼ぶことができ

このような流れで、機械の脳がその経験から学習していくという概念がより現実味を帯びる[^10-31]。そして1949年、アメリカのコンピュータ科学者Edmund Berkeleyが著書*Giant Brains, or Machines That Think*で「A machine, therefore, can think.」と言及し[^10-32] [^10-33] [^10-34]、1950年にTuringが発表した論文を「I PROPOSE to consider the question, ‘Can machines think?’」で始めるなど[^10-35]、思考する機械への関心はさらに盛り上がりを見せる。Turingはその論文でTuring Testという。。。

> **note 3**
Turing machineとUniversal Turing Machineの違い

> **note 4**
Turing machineは自身の論文の中でcomputing machineと呼ばれ[^10-22]、無限長のテープと。詳細は割愛。


he network is trained by adjusting the strengths of the connections between neurons based on the outcomes of previous trials. The training of this network was manually done by the operator who would provide feedback to the machine when it produced the right outcome.

1954年にRAND（Research and Development）Corporationで、JOHNNIAC（John von Neumann Numerical Integrator and Automatic Computerの略でvon Neumannも開発に携わった）という計算機が構築され[^10-36]、翌年にかけてコンピュータ科学者・認知心理学者のAllen Newellと政治・経済・社会学者のHerbert Simonを中心にLogic Theoristと呼ばれるプログラムが作成された[^10-37] [^10-38] [^10-39]。Logic Theoristは、人間の数学者の頭脳の能力を模倣するように、Symbolを組み合わせて表現に組み込む「symbolic reasoning」と呼ばれる推論に基づいており[^10-41]、元になる数学定理のから新しい定理を証明することが可能である（しかもいくつかの数学定理は、人間の数学者よりも詳細な証明を示すことができた）[^10-37]。このように、基にする要素から論理規則に基づいて分岐しながら目的の要素を探索するアルゴリズムは、今日でも探索木（search tree）として知られている。Logic Theoristは世界初の人工知能プログラム（**note 6**も参照のこと）と称され、そのアルゴリズムは後に人間が理解できるSymbolを使う**Symbolic AI**に分類される[^10-42]。

上記のように、この頃、「考える機械（thinking machine）」に関する取り組みが非常に活発だったと言えるが、Dartmouth大学の数学助教授だったJohn McCarthyがより明確にその研究領域を発展させるために[^10-45]、DSRPAI（Dartmouth Summer Research Project on Artificial Intelligence、ダートマス会議）でRockefeller財団にセミナーのための資金提供を要請し、その研究領域を**人工知能（Artificial Intelligence）**と名付けた[^10-44]。これが、AIという用語が使われた最初の文書であるとされ[^10-46]、これがAIという研究分野の誕生であり、次節の第一次AIブームの幕明けにつながる（1956年にDSRPAIが開催され、Logic theoristはそこで発表された[^10-43]）。

> **note 5**
Research and Development (RAND) Corporationとは（割愛）

> **note 6**
> Checkers-playing Program

> **note 7**
> John McCarthyの要請原文
We propose that a 2-month, 10-man study of artificial intelligence be carried out during the summer of 1956 at Dartmouth College in Hanover, New Hampshire. The study is to proceed on the basis of the conjecture that every aspect of learning or any other feature of intelligence can in principle be so precisely described that a machine can be made to simulate it. An attempt will be made to find how to make machines use language, form abstractions and concepts, solve kinds of problems now reserved for humans, and improve themselves. We think that a significant advance can be made in one or more of these problems if a carefully selected group of scientists work on it together for a summer.


これらの成功と、主要な研究者 (つまり DSRPAI の参加者) の擁護により、Defense Advanced Research Projects Agency国防高等研究計画局 (DARPA) などの政府機関は、いくつかの機関で AI 研究に資金を提供するようになりました。
(政府は、話し言葉の書き起こしと翻訳、および高スループットのデータ処理ができるマシンに特に関心を持っていました。)


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
[^10-31]: [Oliver Selfridge](https://www.theguardian.com/technology/2008/dec/17/oliver-selfridge-obituary)
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
[^10-43]: [he History of Artificial Intelligence](
https://sitn.hms.harvard.edu/flash/2017/history-artificial-intelligence/)
[^10-44]: [A PROPOSAL FOR THE DARTMOUTH SUMMER RESEARCH PROJECT ON ARTIFICIAL INTELLIGENCE](http://jmc.stanford.edu/articles/dartmouth/dartmouth.pdf)
[^10-45]: [Dartmouth Summer Research Project: The Birth of Artificial Intelligence](https://www.historyofdatascience.com/dartmouth-summer-research-project-the-birth-of-artificial-intelligence/)
[^10-46]: [A Proposal for the Dartmouth Summer Research Project on Artificial Intelligence](http://jmc.stanford.edu/articles/dartmouth.html)
[^10-47]: [The MCP Neuron](https://jontysinai.github.io/jekyll/update/2017/09/24/the-mcp-neuron.html)
[^10-48]: [Donald O. Hebb in *Wikipedia*](https://en.wikipedia.org/wiki/Donald_O._Hebb)

## 1957 ~ 1980（第一次AIブーム～冬）
本節以降では、AIのアルゴリズムの変遷に注目するため発明者や関係者は割愛する。
### boom 1957 ~ 1974

1958 perceptron
1959 General Problem Solver
lambda calculus (λ-calculus)
1965 Expert systems were formally introduced around 1965[20] by the Stanford Heuristic Programming Project led by Edward Feigenbaum, who is sometimes termed the "father of expert systems";: Decision tree
1966 Joseph Weizenbaum’s ELIZA
1968 ムーアの法則

### winter 1974 ~ 1980
問題点
- コンピューターは、十分な情報を保存したり、十分な速度で処理したりすることができませんでした
- 
- 

## 1980 ~ 1993
### boom 1980 ~ 1987
The first “convolutional neural networks” were used by Kunihiko Fukushima in 1979
John Hopfield and David Rumelhart Deep Learningを普及
Edward Feigenbaumのexpert system
日本政府 Fifth Generation Computer Project (FGCP)
In 1989, Yann LeCun Backpropagation
### winter 1987 ~ 1993

## 1993 ~ 2011
### boom
In 1995, Dana Cortes and Vladimir Vapnik developed the support vector machine (a system for mapping and recognizing similar data)
LSTM (long short-term memory) for recurrent neural networks was developed in 1997
In 1998, Leo Breiman formulated AdaBoost as a gradient descent 
Taking this further, Jerome Friedman, in 1999, came up with the generalisation of boosting algorithms, and thus, a new method: Gradient Boosting Machines. 
In 2009, Fei-Fei Li, an AI professor at Stanford launched 
In 2001, a research report by META Group (now called Gartner) describe Bigdata
GPU Alexnet
### winter?
Around the year 2000, The Vanishing Gradient Problem

## 2011 ~ 
### boom
In 1991, Juergen Schmidhuber also published adversarial neural networks
The Generative Adversarial Neural Network (GAN) was introduced in 2014
RNN
attention
The modern Transformer was introduced by Ashish Vaswani et. al. in their 2017 paper "Attention Is All You Need.
Diffusion
ChatGPT

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