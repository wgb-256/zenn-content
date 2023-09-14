---
title: "ChatGPTに支配される前に、押さえるべきAI・機械学習事情"
emoji: "🧠"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["機械学習", "AI", "初心者"]
published: false
---

# 章立て
1. はじめに
1. AI研究の全体像
1. AI技術関連史
1. 論文を読むにあたって
1. おわりに

# はじめに
ChatGPTの勢いがすごい。テキトーに使っていては振り回される

# AI研究の全体像
## 用語・分類
AI技術に対する期待とは
AI
- Symbolic AI（Symbolic reasoning）
- Subsymbolic AI
- Machine learning
https://www.linkedin.com/pulse/what-artificial-intelligence-without-machine-learning-claudia-pohlink/
## プログラムとAIプログラムの違い
固定動作：プログラム（人間の偏見の影響を受ける）
自己調整する：AI（人間の想定を超える）
 
# AI技術関連史　　
AI技術に対する期待とは

##  ~ 1957（学問分野としてAIが誕生）
17世紀に活躍したドイツの学者[Gottfried Wilhelm Leibniz](https://en.wikipedia.org/wiki/Gottfried_Wilhelm_Leibniz)は、安全・時間浪費の観点から計算は人間ではなく機械がするべきであるという考え方を持っており、[Pascalの計算機](https://en.wikipedia.org/wiki/Pascal%27s_calculator)をもとにして、長さの異なる歯をもつシリンダーと移動式の歯車を組み合わせて計算（基本的には自然数の四則演算）を可能にしたStepped reckonerまたはLeibniz Wheel（ライプニッツの車輪）と呼ばれる手動機械式の計算機を、1694年に完成させた[^10-4] [^10-5]。これをきっかけにLeibnizは、数学的記述（mathmatical statement、詳細は以下の**note 1**を参照）の真理値を決定できる機械を作ることができるのではないかと考えるようになった。それが実現できると、機械が論理を扱うことができるようになるため、どういう場合には何をするといった**場合分け処理**や、明確な理由がある**推論**といった[^10-8]、より知的な処理が可能になる。機械が論理を扱うためには、人間が自然に行っているコミュニケーションのような、曖昧さが残る表現やその時によって用法・意味が変わるような**自然言語**（natual langage）ではなく、文法・意味が形式的に与えられて明確に論理が展開できる**形式言語**（formal language）が必要であると考え、Leibnizの研究は形式言語を用いた**形式理論**（formal theory）にも重きが置かれるようになっていった。さらに、Leibnizは活動の中で、現代のコンピュータの基礎となっている2進数演算（binary arithmetics）や[^10-9]、2進数コンピュータ（binary computer）についても功績を残している[^10-10]。

> **note 1**
数学的記述（mathmatical statement）は、正しい（真）か間違っている（偽）かが判断できる「文」であり、言葉や記号（symbol）が含まれる。例えば、言葉を使った「1は2よりも大きい」や、記号を使った「1>2」という文は、「偽」であるmathmatical statementである。

Leibnizの論文がドイツのHannoverで閲覧可能になった1830年代以降、その注目度は急速に高まり、Johann Eduard ErdmannやKurt Gödelなど後の研究に多大な影響を与える[^10-11] [^10-12]。この頃、数学界では数学理論を構築するための演繹的な方法（すでに知られている法則（一般論・ルール）や前提から、階段を登っていくように論理を積み重ねて結論を出す考え方[^10-13]）に注目が集まっており、数学における形式理論（公理理論ともいう）に関する新しい問題が提起されていた[^10-14]。1928年、ドイツの数学者であるDavid HilbertとWilhelm Ackermannは、**Entscheidungsproblem**（ドイツ語。日訳で決定問題、英訳でdecision problem）と呼ばれる、「（一階論理の）すべての数学的記述は、導出可能か」（すべての公理を考慮すれば、命題が証明可能かどうかを判断できるアルゴリズムが存在するかどうか）という問題を提起した[^10-15]。この問題は、「人間の思考プロセスをすべて単純なアルゴリズムで表現することは可能か」と言い換えることができ[^10-18]、もしそのようなことが可能であれば、単純なアルゴリズムだけでも実行可能な機械があれば、人間の思考活動を全てそれで再現できるということになる。

Note that in its original form (Hilbert & Ackermann 1928), the problem was stated in terms of validity rather than derivability. Given Gödel’s completeness theorem (Gödel 1929) proving that there is an effective procedure (or not) for derivability is also a solution to the problem in its validity form. In order to tackle this problem, one needs a formalized notion of “effective procedure” and Turing’s machines were intended to do exactly that

> **note 2**
数学者や数学団体は自身が発案・直面した未解決問題を公開し、研究を生み出してきた。1900年にHilbertが、パリで開催された国際数学者会議（International Congress of Mathematicians: ICM）および彼の著作で、次の世紀に研究されるべき23の主要な数学的問題が発表された[^10-1] [^10-2] [^10-3]。Entscheidungsproblemは[Hilbertの23の問題](https://ja.wikipedia.org/wiki/%E3%83%92%E3%83%AB%E3%83%99%E3%83%AB%E3%83%88%E3%81%AE23%E3%81%AE%E5%95%8F%E9%A1%8C)のうち、[Diophantine方程式](https://en.wikipedia.org/wiki/Diophantine_equation)に解があるかどうかを決定するアルゴリズムを求める第10問題に関連している。（**第2問題も？？** // Church-turing thesis）

1935年、HilbertのEntscheidungsproblemに興味を持ったAlan Turingは、任意の数学的記述の導出に必要な「形式化された手順」が必要である、として研究を開始した。すなわち、どんな数学的記述も導出できる手順が存在するということは、どんな数学的記述も証明可能であると言える、という考え方である。Turingは翌1936年に発表した論文[^10-22]で、そういう手順が可能である仮想的な機械（UTM: **Universal Turing machine**[^10-26]）を考案し、Entscheidungsproblemが成り立たたないことを証明した[^10-17] [^10-18] [^10-19] [^10-20]。したがって例えば、数学の定理を証明するためのアルゴリズム的な手法は存在せず、総当たり（Brute force）的に証明を試さなければならないということが示されたことになる[^10-54]。
Turingのアプローチで独創的だったのは、UTMを考案するにあたり、それまで発明されていた「機械」に注目するのではなく、子供が勉強で使う方眼紙や何か手順を踏むときの人間の思考など、「人間」に注目した上で、実行する手順を徹底的に曖昧さがない論理的な処理に落とし込んだことである[^10-21]。
UTMの論理性は、1943年に発表された、神経生理学者Warren McCullochと数学者Walter Pittsによるニューロンの数学モデル（MPニューロン、MCPニューロンと呼ばれる）およびそれにより構成されるニューラルネットワークモデルの考案のためのインスピレーションをもたらし[^10-23] [^10-47]、UTMの構成（**note 4**参照）は、Machineへの命令を入力データと同じ記憶領域に配置するstored-program方式と呼ばれ、1945年にアメリカの学者John von Neumannにより発表されたコンピュータの構成（ノイマン型アーキテクチャ、von Neumann model、Princeton architectureなどと呼ばれる）にも強い影響を与えるなど[^10-24] [^10-25] [^10-26]、多大な影響を与えることとなった。
ノイマン型アーキテクチャが発表された1945年末には、世界初の「プログラム可能な（命令の与え方によって様々なタスクをこなすことができる）」計算機であるENIAC（Electronic Numerical Integrator and Computer）[^10-27] [^10-28]、1948年には世界で初めてノイマン型アーキテクチャで動作するManchester Baby（SSEM: Small-Scale Experimental Machineとも呼ばれる）など[^10-29] [^10-30]、続々と電子計算機（以降、コンピュータ）が一般化し（なんでもできるようになり）、同時に高性能化していった。
さらに1951年には、Marvin MinskyとDean Edmondsが、SNARC（Stochastic Neural Analog Reinforcement Calculator）という世界で初めて人工ニューラルネットワーク（ANN: Artificial Neural Network）を実装したコンピュータを構築している。SNARCのニューラルネットワークは、MPニューロンの考え方を拡張したHebb理論に基づいており、**学習**することができるようになっている。
Hebb理論は、1949年にカナダの心理学者Donald Olding Hebの[著書](https://pure.mpg.de/rest/items/item_2346268_3/component/file_2346267/content)で提唱された[^10-48]、ニューロンの数学モデルの学習ルールとそのアルゴリズムを含む理論である。Hebbは、つながっている2つのニューロンが同時に発火すればするほど、それらの接続強度（以降、重み）は強くなるという規則を主張した（これは、後に長期記憶の理論にも影響した）[^10-52]。この規則に基づいて重みを調整すれば、ロジックが変えられる、すなわち所望のロジックを得るために重みを調整すれば、機械が改善されることになるため「学習」と呼ぶことができる（SNARCではHebb則に基づいて重みの更新を人の手で行っていた）[^10-50]。
ただし、純粋な総当たり処理をすべてのタスクに対して行う計算はこの頃のコンピュータの性能では不可能であり[^10-55]、特に探索や認識といった複雑なタスクに対しては、知性的に解を求める方法が求められていたと考えられる。さらに1949年、アメリカのコンピュータ科学者Edmund Berkeleyが著書*Giant Brains, or Machines That Think*で「A machine, therefore, can think.」と言及し[^10-32] [^10-33] [^10-34]、1950年にTuringが発表した論文を「I PROPOSE to consider the question, ‘Can machines think?’」で始めるなど[^10-35]、思考する機械への関心はさらに盛り上がりを見せていた。Turingはその論文でTuring Testという非常に重要な。。。（Turing Testについて詳細は割愛）。

> **note 3**
Turing machineとUniversal Turing Machineの違い

> **note 4**
Turing machineは自身の論文の中でcomputing machineと呼ばれ[^10-22]、無限長のテープと。詳細は割愛。

1954年にRAND（Research and Development）Corporationで、JOHNNIAC（John von Neumann Numerical Integrator and Automatic Computerの略でvon Neumannも開発に携わった）という計算機が構築され[^10-36]、翌年にかけてコンピュータ科学者・認知心理学者のAllen Newellと政治・経済・社会学者のHerbert Simonを中心にLogic Theoristと呼ばれる、IPL（Information Processing Languageというプログラミング言語）を用いたプログラムが作成された[^10-37] [^10-38] [^10-39]。Logic Theoristは、人間の数学者の頭脳の能力を模倣するように、Symbolを組み合わせて表現に組み込む「symbolic reasoning」と呼ばれる推論に基づいており[^10-41]、元になる数学定理のから新しい定理を証明することが可能である（しかもいくつかの数学定理は、人間の数学者よりも詳細な証明を示すことができた）[^10-37]。このように、基にする要素（root）から論理規則に基づいて分岐しながら目的の要素を探索するアルゴリズムは、今日でも探索木（search tree）として知られており、Logic Theoristは解ける保証がない問題に取り組むプログラムを作成した点が一つの大きな発明であると考えられる。また、Logic Theoristは実際の問題を解決するために人間の推論能力をシミュレートした世界初の人工知能プログラムと称され[^10-51]、Symbolを用いて人間の思考プロセスをプログラム化するいう思想に基づいたこのような手法は後に、**Symbolic AI**に分類される[^10-42]。Symbolic AIに対して、人間の脳をモデル化すれば人間と同じように知能をもたせることができるという思想に基づいて、ニューロンの数学モデルを用いてANNを構成する手法は**Connectionist AI**と呼ばれる[^10-49]。
Heuristics? Reasoning search?
Logic AI
https://plato.stanford.edu/entries/logic-ai/

上記のように、この頃、「考える機械（thinking machine）」に関する取り組みが非常に活発だったと言えるが、Dartmouth大学の数学助教授だったJohn McCarthyがより明確にその研究領域を発展させるために[^10-45]、DSRPAI（Dartmouth Summer Research Project on Artificial Intelligence、ダートマス会議）でRockefeller財団にセミナーのための資金提供を要請し、その研究領域を**人工知能（Artificial Intelligence）**と名付けた[^10-44]。これが、AIという用語が使われた最初の文書であり[^10-46]、これがAIという研究分野の誕生とされる（1956年にDSRPAIが開催され、Logic theoristはそこで発表された[^10-43]）。

> **note 5**
Research and Development (RAND) Corporationとは（割愛）

> **note 7**
> John McCarthyの要請原文
We propose that a 2-month, 10-man study of artificial intelligence be carried out during the summer of 1956 at Dartmouth College in Hanover, New Hampshire. The study is to proceed on the basis of the conjecture that every aspect of learning or any other feature of intelligence can in principle be so precisely described that a machine can be made to simulate it. An attempt will be made to find how to make machines use language, form abstractions and concepts, solve kinds of problems now reserved for humans, and improve themselves. We think that a significant advance can be made in one or more of these problems if a carefully selected group of scientists work on it together for a summer.

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

## 1957 ~ 1980（第一次AIブーム：決められたパターンの中から最適な方法を探索するAI）
本節以降では、AIのアルゴリズムや技術の変遷に注目するため発明者や関係者は割愛する場合がある。
### boom 1957 ~ 1974
1958年、Connectionist AIの分野では、RosenblattによりPerceptronと呼ばれる単層のニューラルネットワークが発明された。Perceptronは、MPニューロンが0または1の2つの値のみを扱うのに対して小数点以下を含んだ値を扱うようになり、加えてHebb理論で導入された重みを教師データを用いて調節する、すなわち前節のSNARC同様に機械が学習する方法（**教師あり学習**、Supervised Learning。詳細は割愛）も考案された[^20-4] [^20-5]。
このように人間がルールを作らずに機械に学習能力を与える研究分野に対して、1959年にArthur Samuelが**Machine Learning**（**機械学習**）という言葉を提唱した[^20-10]。Samuel自身も1952年に[Checkers](https://ja.wikipedia.org/wiki/%E3%83%81%E3%82%A7%E3%83%83%E3%82%AB%E3%83%BC)をプレイするプログラムを作成し[^20-8]（[Alpha-beta pruning](https://lethediana.sakura.ne.jp/tech/archives/uncategorized-ja/2134/)と呼ばれる方法で効率的に戦略を探索させた）、1955年にRot Learningと呼ばれる方式で勝者の戦略を学習可能とし[^20-11]、1959年に当時のベストプレイヤーを打ち負かしている[^20-9]。

> **note 3**
ニューロンの数学モデルのことをPerceptronと呼ぶこともあり[^10-53]、その場合、MPニューロンが最初のPerceptronとなる。

ただし、この時期のAI研究はSymbolic AIの分野がより大きな盛り上がりを見せていた。

様々な特定のタスクに対するAI（前節のLogic Theoristの場合、定理の証明というタスク）がメインだったが、1959年にAllen NewellとHerbert A. SimonによりGeneral Problem Solver（GPS）と呼ばれる、一般的なタスクに対応することを意図したAIが発明された[^20-13]。GPSは、到達したい目標へ一足飛びにたどり着けない場合に、目標との差から中間目標を作って徐々に目標に近づく[Means End Analysis](https://lethediana.sakura.ne.jp/tech/archives/summary-ja/2143/)（MEA）と呼ばれる手法を導入しており、GPS以後、MEAはAIに広く利用された[^20-14]。
*Forward searchとBackward searchを組み合わせた手法・・・*

> **note 3**
実際には、論理や幾何学の定理の証明、Chessのような明確に定義された問題にのみ適用可能だったが、他の理論的研究の基礎になっている[^20-12] 。
- SOAR（1982）[Laird, John & Rosenbloom, Paul. (1994). The Evolution of the Soar Cognitive Architecture. ]
- GOMS

このようなAI研究の成功に加え、1961年に世界初のICチップが販売[^20-15]（これまでのコンピュータ（IBM704）がメモリ不足だった[^20-16]というAI研究に対するボトルネックを克服するハードウェアの進化）、1962年にARPA（Advanced Research Projects Agency、高等研究計画局）にIPTO（Information Processing Techniques Office、情報処理技術局）の設立と[^20-17]、それによるマサチューセッツ工科大学（MIT）、スタンフォード大学（SAIL（Stanford Artificial Intelligence Laboratory）、Stanford HPP（Heuristics Programming Project）等）、カーネギーメロン大学をはじめとするAI研究への投資などにより、AI研究の規模が根本的に変わり、小規模なプロジェクトの集まりから大規模で注目度の高い分野へと推進された[^20-18]。
1965年にはHPPでDENDRAL（DENDRitic ALgorithm）と呼ばれる、化学者が未知の有機分子を特定できるように分子のスペクトル分析を行い構造を示すAIの開発が開始された[^20-19]。SAILのコンピュータPDP-6で作成されたプログラムであり、

DENDRALはルールベースで（ゲーム等ではない）現実の問題のために作られたプログラムであると言われる[^20-20]。

Dendralその後
https://dl.acm.org/doi/pdf/10.1145/89482.89484

1965 Expert systems were formally introduced around 1965[20] by the Stanford Heuristic Programming Project led by Edward Feigenbaum, who is sometimes termed the "father of expert systems";: Decision tree


1966 Joseph Weizenbaum’s ELIZA
Computer scientist Joseph Weizenbaum famously illustrated the limitations of AI 
in the 1960s with the development of the Eliza program. The program 
extracted key phrases and mimicked human dialogue in the manner of non-
directional psychotherapy. The user might enter, ``I do not feel well 
today,'' to which the program would respond, ``Why do you not feel well 
today?'' Weizenbaum later argued in Computer Power and Human Reason 
that computers would likely gain enormous computational power but 
should not replace people because they lack such human qualities and 
compassion and wisdom.
https://www.govinfo.gov/content/pkg/CHRG-114shrg24175/html/CHRG-114shrg24175.htm

https://www.lamsade.dauphine.fr/~cazenave/papers/games.pdf

1967 – Machines gained the ability to recognize patterns 
    The “nearest neighbor” algorithm was created,

1968 Shakey the robot
1971 Blocksworld planning and reasoning domain
1968 ムーアの法則


1969: Minsky and Pappert's "Perceptrons" book shows single-layer NN can't represent XOR
ただし、Perceptronは2種類かつ比較的単純な分類タスク（厳密には、線形分離可能なタスク）にしか対応できないことがわかり[^20-3]、1969年に出版されたPerceptrons: an introduction to computational geometryという書籍で単純な論理 XOR 関数を学習できないことを示されるなど[^20-6]、Connectionist AIの分野は冬の時代に。


(政府は、話し言葉の書き起こしと翻訳、および高スループットのデータ処理ができるマシンに特に関心を持っていました。)

Most of the federal support has come from the Defense Advanced Research Projects Agency (DARPA, known during certain periods as ARPA) and other units of the Department of Defense (DOD). Other funding agencies have included the National Institutes of Health, National Science Foundation, and National Aeronautics and Space Administration (NASA), which have pursued AI applications of particular relevance to their missions—health care, scientific research, and space exploration.
https://nap.nationalacademies.org/read/6323/chapter/11#204

### winter 1974 ~ 1980
問題点
- コンピューターは、十分な情報を保存したり、十分な速度で処理したりすることができませんでした
- 
- Perceptronの線形問題　しかしながら、欠陥が見つかった


[^20-1]: [人工知能用言語 Lispの今と将来](https://www.jstage.jst.go.jp/article/jjsai/24/5/24_681/_pdf)

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


[^20-20]: [AI History: the 1980s and expert systems](https://www.klondike.ai/en/ai-history-the-1980s-and-expert-systems/)


## 1980 ~ 1993
### boom 1980 ~ 1987
The first “convolutional neural networks” were used by Kunihiko Fukushima in 1979
John Hopfield and David Rumelhart Deep Learningを普及
Edward Feigenbaumのexpert system
日本政府 Fifth Generation Computer Project (FGCP)
In 1989, Yann LeCun Backpropagation

1990 Deep blue

1990
Kernel classifiers were described as early as the 1960s, with the invention of the kernel perceptron.[3] They rose to great prominence with the popularity of the support-vector machine (SVM) in the 1990s, when the SVM was found to be competitive with neural networks on tasks such as handwriting recognition.

In the late 1980s and early 1990s, there was a surge of excitement in the AI community as people realized that machine learning could solve some problems in interesting ways, with substantial advantages stemming from their ability to accept raw forms of input data, and to train algorithms to perform predictive tasks. At that time, however, computers were not powerful enough to process vast amounts of data.
https://www.whitehouse.gov/wp-content/uploads/2022/12/TTC-EC-CEA-AI-Report-12052022-1.pdf

### winter 1987 ~ 1993

## 1993 ~ 2011
### boom
In 1995, Dana Cortes and Vladimir Vapnik developed the support vector machine (a system for mapping and recognizing similar data)
LSTM (long short-term memory) for recurrent neural networks was developed in 1997
1997 Deep Blue (Game AI)

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
Foundation model

Probabilistic AI
https://hawai.tech/ia-waves-and-evolution-of-hardware/


https://softjourn.com/insights/heuristic-programming#
Game Theory: In the 1950s and 1960s, researchers like Claude Shannon and Arthur Samuel developed early heuristics to explore optimal game strategies like chess and checkers. Their work paved the way for more advanced heuristic techniques used in game theory today.
Optimization: In the 1970s, researchers began developing metaheuristic optimization algorithms, such as genetic and simulated annealing, to find near-optimal solutions to complex optimization problems.
Machine Learning: The 1980s and 1990s witnessed significant advancements in machine learning techniques, such as decision trees and neural networks, which rely on heuristic methods to learn from data and make predictions.
Human-Computer Interaction: Heuristic evaluation, a method for identifying usability issues in user interfaces, was introduced by Jakob Nielsen in the 1990s, highlighting the application of heuristics in human-computer interaction.
As computer science continues to evolve, so do heuristic techniques, with researchers constantly developing new and innovative ways to apply heuristics to tackle increasingly complex problems.

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