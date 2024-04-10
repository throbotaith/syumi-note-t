
#### はじめに
最初にサイコロの任意の単一の結果の確率を考慮する。サイコロが7つあるため、全ての可能な結果の集合は $\Omega=\{1, \ldots, 6\}^7$となる。全ての結果が等しく確率的であるため、任意の $\omega \in \Omega$ の確率は $(1 / 6)^7$となる。ゲームのペイオフが値 $v$ を取る確率は、値 $v$ をもたらす $\Omega$ 内の全ての結果 $\omega$ に割り当てられた総確率を計算することで評価できる。原則として、これは確率的なものが残りから分離されているおかげで、行うのは非常に簡単だ。集合 $\Omega$ は結果空間と呼ばれ、その要素は結果だ。図2.2はこの考え方を示している。左側でランダムな結果が生成され、右側ではさまざまなメカニズムを用いて値が導出される; これらの値の一部は観測される可能性がある。

人工的なゲームの価値をどう導き出すかについてもう少し形式的になることが多くの利点をもたらす。このため、ゲームがその価値を得るプロセスは、$\Omega$から実数への関数 $X$ 数式的には、($X: \Omega \rightarrow \mathbb{R}$）である。標本空間から実数の部分集合への関数が**確率変数**と呼ばれるのは皮肉なことである。これらはプログラミング言語の意味でランダムでも変数でもない。ランダム性は $X$ への入力、つまり標本空間の要素である**事象**にあり、ランダムに変化する結果を生み出す。後ほど確率変数にもう少し構造を加えるが、標本空間から実数へのマップとして考えるだけで十分である。

#### 一般的な確率

![[Pasted image 20240410211332.png]]


ある数値$v \in \mathbb{N}$を選ぶ。$X=v$となる確率は何か？この確率は$(1 / 6)^7$に$X^{-1}(v)=\{\omega \in \Omega: X(\omega)=v\}$のサイズを掛けたものとなる。これはつまり、確率変数の出力が$v$となるような入力$\omega$の集合を示す。$X^{-1}(v)$は、$X$の下での$v$の原像と呼ばれる。より一般的に、$X$がある集合$A \subseteq \mathbb{N}$の値を取る確率は、$(1 / 6)^7$に$X^{-1}(A)=\{\omega \in \Omega: X(\omega) \in A\}$の濃度を掛けたもので与えられる。

前段落では、$\Omega$の部分集合に割り当てられた確率のみが必要だったことに注意。これをもう少し一般化するために、$\Omega$の特定の部分集合に確率を割り当てるマップ$\mathbb{P}$を導入する。$\mathbb{P}$の直感的な意味は次のとおりである。ランダムな結果が$\Omega$で生成される。結果が集合$A \subset \Omega$となる確率は$\mathbb{P}(A)$である。$A$が$\mathbb{P}$の定義域にない場合、つまり入力制限の範囲外の場合、結果が$A$内に落ちる確率の質問に答えることはできない。しかし、$\mathbb{P}$を$\Omega$の特定の部分集合にのみ制限するべき理由についての議論は後回しにする。上記のサイコロの例では、$\mathbb{P}$の定義域内の部分集合族は制限されておらず、特に任意の部分集合$A \subseteq \Omega$に対して、$\mathbb{P}(A)=(1 / 6)^7|A|$とする。

したがって、$X$が値$v$を取る**確率**は$\mathbb{P}\left(X^{-1}(v)\right)$だ。つまり、出力が$v$となるような、確率変数への入力集合の確率となる。より読みやすい表記法でこれを$\mathrm{P}(X=v)$とする。しかし、このなじみのある形式が$\mathbb{P}\left(X^{-1}(v)\right)$の略記であることを常に心に留めておく必要がある。より一般的に、$\mathbb{P}(\operatorname{predicate}(U, V, \ldots))=\mathbb{P}(\{\omega \in \Omega: \operatorname{predicate}(U(\omega), V(\omega), \ldots)$ が真である $\})$も使用する。


#### 一般的な確率の満たすべき性質
$\mathbb{P}$はどのような性質を満たすべきか？$\Omega$が全ての可能な結果の集合であるため、$\mathbb{P}$が$\Omega$に対して定義され、

・$\mathbb{P}(\Omega)=1$であること
・$\emptyset$が結果を含まないため$\mathbb{P}(\emptyset)=0$

が期待される。さらに、確率は非負であるべきなので、

・$\mathbb{P}$が定義される任意の$A \subset \Omega$に対して$\mathbb{P}(A) \geq 0$

が成り立つべきだ。$A^c=\Omega \backslash A$を$A$の補集合とする。すると$\mathbb{P}$が$A$に対して定義される場合に限り、$A^c$にも定義され、

・$\mathbb{P}\left(A^c\right)=1-\mathbb{P}(A)$（**否定規則**）

が期待される。最後に、

・$A, B$が互いに素であるならば$A \cap B=\emptyset$
・$\mathbb{P}(A), \mathbb{P}(B)$および$\mathbb{P}(A \cup B)$が全て定義される場合、$\mathbb{P}(A \cup B)=\mathbb{P}(A)+\mathbb{P}(B)$

となる。これを**有限加法性**と呼ぶ。

#### $\sigma$-代数とその性質（測度論的確率論の基礎）

##### 集合族の定義

$\mathcal{F}$：$\mathbb{P}$が定義される$\Omega$の部分集合族

##### 性質

・$A \in \mathcal{F}$かつ$A^c \in \mathcal{F}$
　$\mathbb{P}\left(A^c\right)$は単純に$\mathbb{P}\left(A^c\right)=1-\mathbb{P}(A)$によって定義できる
・$\mathbb{P}$が互いに素な集合$A$と$B$に定義されている場合、$A \cup B \in \mathcal{F}$である
　この性質は(i)集合が互いに素でない場合でも、および(ii)可算無限に多くの集合に対しても成り立つことを要求する。
・$\left\{A_i\right\}_i$が集合のコレククションであり、全ての$i \in \mathbb{N}$に対して$A_i \in \mathcal{F}$である場合、$\cup_i A_i \in \mathcal{F}$
　これらの集合が対ごとに素である場合、$\mathbb{P}\left(\cup_i A_i\right)=\sum_i \mathbb{P}\left(A_i\right)$となる。
　
このような性質を満たす部分集合族を$\sigma$-代数と呼び、これは'sigma-algebra'と発音され、時には$\sigma$-fieldとも呼ばれる（注1を参照）。

##### $\sigma$-代数と確率測度のちゃんとした定義

##### $\mathcal{F} \subseteq 2^{\Omega}$が$\sigma$代数である場合、

・$\Omega \in \mathcal{F}$かつ全ての$A \in \mathcal{F}$に対して$A^c \in \mathcal{F}$
・全ての$\{A_i\}_i$に対して$A_i \in \mathcal{F}$である全ての$i \in \mathbb{N}$について$\cup_i A_i \in \mathcal{F}$
つまり、全体の結果空間を含み、補集合および可算合併の下で閉じているべきである。

##### 関数$\mathbb{P}: \mathcal{F} \rightarrow \mathbb{R}$が確率測度である場合

・$\mathbb{P}(\Omega)=1$
・全ての$A \in \mathcal{F}$に対して$\mathbb{P}(A) \geq 0$
・$\mathbb{P}\left(A^c\right)=1-\mathbb{P}(A)$および互いに素な集合の可算コレクション$\{A_i\}_i$について$A_i \in \mathcal{F}$である全ての$i$に対して$\mathbb{P}\left(\cup_i A_i\right)=\sum_i \mathbb{P}\left(A_i\right)$

確率測度は**確率分布**、または単に**分布**とも呼ばれる。

##### サブ$\sigma$-代数

・$\mathcal{F}$が$\sigma$-代数であり、$\mathcal{G} \subset \mathcal{F}$も$\sigma$-代数の場合、$\mathcal{G}$を$\mathcal{F}$のサブ$\sigma$-代数と言う。
　$\mathbb{P}$が$\mathcal{F}$上で定義された測度である場合、$\mathcal{G}$への$\mathbb{P}$の制限は$\mathcal{G}$上で定義された測度$\mathbb{P}_{\mid \mathcal{G}}$であり、全ての$A \in \mathcal{G}$に対して$\mathbb{P}_{\mid \mathcal{G}}(A)=\mathbb{P}(A)$と定義される。サブ$\sigma$-代数の概念を導入した理由について疑問に思うかもしれないが、その答えはすぐに明らかになる。

##### いくつかの定義

・$\mathcal{F}$の要素：**可測集合**
　$\mathbb{P}$がそれらに値を割り当てる意味で可測である。
　
・$(\Omega, \mathcal{F})$：**可測空間**

・$(\Omega, \mathcal{F}, \mathbb{P})$：**確率空間**

・$\mathbb{P}$：**測度**　
　$\mathbb{P}(\Omega)=1$という条件が取り除かれる場合
　
・$\mathbb{P}$：**符号付き測度**
　$\mathbb{P}(A) \geq 0$という条件も取り除かれる場合
　
　測度と符号付き測度に対して$\mathbb{P}$記号を使用するのは珍しい。

##### 確率変数と確率測度

確率変数は新しい確率測度を導く。特に、上記の例では$\mathbb{P}_X(A)=\mathbb{P}\left(X^{-1}(A)\right)$は、$\mathbb{P}\left(X^{-1}(A)\right)$が定義される全ての$\mathbb{R}$の部分集合$A$に対して定義される確率測度だ。より一般的に、確率変数$X$に対する確率測度$\mathbb{P}_X$は$X$の**law**、または$X$による$\mathbb{P}$の**押し出し(push forward)測度**と呼ばれる。
$\mathbb{P}_X$の重要性は、$X$に関する任意の確率的質問が$\mathbb{P}_X$の知識だけから答えられることだ。$\Omega$や$X$のマップの詳細さえ必要ない。これは、しばしば基礎となる確率空間$(\Omega, \mathcal{F}, \mathbb{P})$を言及しない言い訳として使用される。$X$を固定したまま$\mathbb{P}$を変更する（例えば、ロードされたサイコロに切り替えるなど）と、$X$によって誘導される測度が変わる。特にバンディットアルゴリズムの性能の限界に対する下限を証明する際に、このように$\mathbb{P}$を変更する議論を頻繁に使用する。洞察力のある読者は、いくつかの詳細を飛ばしたことに気づいたかもしれない。測度は$\sigma$-代数から$\mathbb{R}$への関数として定義されるので、$\mathbb{P}_X$を測度と呼びたい場合、その**定義域$\{A \subset \mathbb{R}: X^{-1}(A) \in \mathcal{F}\}$が$\sigma$-代数である必要**がある。これは非常に一般的に成り立つ。関数$X: \Omega \rightarrow \mathcal{X}$に対して、$\mathcal{X}$が任意であっても、コレクション$\{A \subset \mathcal{X}: X^{-1}(A) \in \mathcal{F}\}$が$\sigma$-代数であることを**練習問題2.3**で示す。




##### 可測写像

$X$が**実数以外の値を取ることができるように**、例を少し一般化すると有用である。例えば、範囲は**ベクトルや、シーケンスのような抽象的なオブジェクト**である可能性がある。$(\Omega, \mathcal{F})$を可測空間、$\mathcal{X}$を任意の集合、$\mathcal{G} \subseteq 2^{\mathcal{X}}$とする。
関数$X: \Omega \rightarrow \mathcal{X}$が$\mathcal{F} / \mathcal{G}$-**可測写像**であるとは、
・全ての$A \in \mathcal{G}$に対して$X^{-1}(A) \in \mathcal{F}$
であることを意味する．

##### ボレル

$\mathcal{G}$が$\sigma$-代数である必要はない。$\mathcal{F}$と$\mathcal{G}$が文脈から明らかな場合、$X$は可測集合と呼ばれる。$\mathcal{G}$の典型的な選択肢は何か？$X$が実数値の場合、通常$\mathcal{G}=\{(a, b): a<b$で$a, b \in \mathbb{R}\}$、すなわち全ての開区間の集合を選択する。$X$が$\mathcal{F} / \mathcal{G}$-可測である場合、それはまた$\mathcal{F} / \sigma(\mathcal{G})$-可測であることも確認できる。ここで$\sigma(\mathcal{G})$は$\mathcal{G}$を含む最小の$\sigma$-代数である。この最小の$\sigma$-代数は存在することが示される。さらに、それは$\mathcal{G}$を含むすべての$\sigma$-代数に含まれる集合$A$を正確に含む（**練習問題2.5**を参照）。$\mathcal{G}$が開区間の集合である場合、$\sigma(\mathcal{G})$は通常$\mathfrak{B}$または$\mathfrak{B}(\mathbb{R})$と表記され、$\mathbb{R}$の**ボレル$\sigma$-代数**と呼ばれる。この定義は、開区間を形$\prod_{i=1}^k\left(a_i, b_i\right)$の開矩形に置き換えることで$\mathbb{R}^k$に拡張される。ここで$a<b \in \mathbb{R}^k$である。$\mathcal{G}$がそのような全ての開矩形の集合である場合、$\sigma(\mathcal{G})$はボレル$\sigma$-代数：$\mathfrak{B}\left(\mathbb{R}^k\right)$である。より一般的に、位相空間$\mathcal{X}$のボレル$\sigma$-代数は、$\mathcal{X}$の開集合によって生成される$\sigma$-代数である。

##### 確率変数（確率ベクトル）のちゃんとした定義

・可測空間$(\Omega, \mathcal{F})$上の**確率変数**（**確率ベクトル**）は、
　$\mathcal{F} / \mathfrak{B}(\mathbb{R})$-可測関数$X: \Omega \rightarrow \mathbb{R}$（$\mathcal{F} / \mathfrak{B}\left(\mathbb{R}^k\right)$-可測関数$X: \Omega \rightarrow \mathbb{R}^k$）
　である。
　
・可測空間$(\Omega, \mathcal{F})$と$(\mathcal{X}, \mathcal{G})$の間の確率要素は、$\mathcal{F} / \mathcal{G}$-可測関数$X: \Omega \rightarrow \mathcal{X}$
　である。

この定義によれば、確率ベクトルは範囲空間が$(\mathbb{R}^k, \mathfrak{B}\left(\mathbb{R}^k\right))$である確率要素であり、$k=1$の場合、**確率ベクトルは確率変数である**。**確率要素**は、$\mathbb{R}^k$に値を取らない関数まで確率変数とベクトルを一般化する。まあ，一般化された確率変数だと思えば良い．任意の確率要素に対して押し出し測度（または法則）を定義できる。さらに、確率変数とベクトルはうまく連携する。もし$X_1, \ldots, X_k$が同じドメイン$(\Omega, \mathcal{F})$上の$k$個の確率変数であれば、$X(\omega)=\left(X_1(\omega), \ldots, X_k(\omega)\right)$は$\mathbb{R}^k$-値の確率ベクトルであり、その逆もまた然り（**練習問題2.2**）。

可測空間$(\Omega, \mathcal{F})$と$(\mathcal{X}, \mathcal{G})$の間の写像$X: \Omega \rightarrow \mathcal{X}$が与えられた場合、$\sigma(X)=\left\{X^{-1}(A): A \in \mathcal{G}\right\}$を$X$によって生成される$\sigma$-代数とする。マップ$X$が$\mathcal{F} / \mathcal{G}$-**可測**であるのは、$\sigma(X) \subseteq \mathcal{F}$の場合に**限られる**。定義を確認することで、$\sigma(X)$が$\mathcal{F}$のサブ$\sigma$-代数であり、実際には$X$が可測であるための最小のサブ$\sigma$-代数であることを示せる。もし$\mathcal{G}=\sigma(\mathcal{A})$が集合システム$\mathcal{A} \subset 2^{\mathcal{X}}$によって生成される場合、$X$の$\mathcal{F} / \mathcal{G}$-可測性を確認するには、$X^{-1}(\mathcal{A})=\left\{X^{-1}(A): A \in \mathcal{A}\right\}$が$\mathcal{F}$の部分集合であるかどうかを確認するだけで十分である。これが十分である理由は、$\sigma\left(X^{-1}(\mathcal{A})\right)=X^{-1}(\sigma(\mathcal{A}))$であり、定義により後者は$\sigma(X)$であるからである。マップが可測かどうかを確認するには、合成規則を使用するか、$\mathcal{A}$に対して$X^{-1}(\mathcal{A}) \subset \mathcal{F}$をチェックするかのいずれかである。$\mathcal{A}$は$\mathcal{G}$の「生成器」である。

確率要素は、**合成によって新しい確率要素を生成することができる**。$\sigma$-代数$\mathcal{F}, \mathcal{G}$および$\mathcal{H}$に対して、$f$が$\mathcal{F} / \mathcal{G}$-可測であり、$g$が$\mathcal{G} / \mathcal{H}$-可測である場合、それらの合成$g \circ f$は$\mathcal{F} / \mathcal{H}$-可測である（**練習問題2.1**）。これは特に**ボレル関数**についてよく使用される。ボレル関数は、$\mathbb{R}^m$から$\mathbb{R}^n$への$\mathfrak{B}\left(\mathbb{R}^m\right) / \mathfrak{B}\left(\mathbb{R}^n\right)$-可測関数の特別な名称であり、**ボレル可測**とも呼ばれる。すべての馴染み深い関数がボレルであることを読者は喜ぶだろう。まず第一に、すべての連続関数がボレルであり、加算や乗算などの基本的な操作が含まれる。しかし、連続性は必須ではない。実際、ボ**レルでない関数を構築するのは困難**である。これは、確率変数を扱う際に通常の操作が「安全」であることを意味する。

##### 指示関数

指示関数について述べる。任意の集合$\Omega$と$A \subseteq \Omega$が与えられたとき、$A$の指示関数は$\mathbb{I}_A: \Omega \rightarrow\{0,1\}$であり、次のように定義される：

$$
\mathbb{I}_A(\omega)= \begin{cases}1, & \text { if } \omega \in A ; \\ 0, & \text { otherwise }\end{cases}
$$


・$A$が複雑な記述を持つ場合、$\mathbb{I}_A(\omega)$の代わりに$\mathbb{I}\{\omega \in A\}$と書くことで表記を乱用することが便利になる。同様に、$\mathbb{I}\{\mathrm{predicate}(X, Y, \ldots)\}$と書くことで、述語が真である$\Omega$の部分集合の指示関数を意味することが多い。
・指示関数$\mathbb{I}_A$が$(\Omega, \mathcal{F})$上の確率変数であるのは、$A$が可測である場合、つまり$A \in \mathcal{F}$である場合に限られる。


##### $\mathcal{F}=2^{\Omega}$，つまり$\sigma$-代数を標本空間の冪集合（すべての事象がつまった集合族）として定義しない理由

多くの場合、$\mathcal{F}=2^{\Omega}$と定義することに何の問題もない。しかし、$\mathcal{F}=2^{\Omega}$にしない2つの理由がある。1つ目は技術的なもので、2つ目は概念的なものだ。

###### 技術的な理由

これは，次のような驚くべき定理によって強調される。

・$\mathcal{F}$が$\Omega$の冪集合として選ばれた場合、$\Omega=[0,1]$上に一様確率分布が存在しない（もし存在したら、任意の区間にその長さを割り当てる性質を持つだろう）

言い換えれば、一様測度を定義したい場合、$\mathcal{F}$はあまりに大きすぎてはならない。対照的に、一様測度はボレル$\sigma$-代数上で定義できるが、これを証明するのは初歩的ではない。


##### 概念的な理由

概念的な理由としては，$\sigma$-代数を使用して情報を表現できるため、$\mathcal{F}=2^{\Omega}$にしないことのである。**いきなりでかい集合族は考えない**．これは、学習者が環境と相互作用し、徐々に知識を得ていくバンディットの研究に特に有用である。これを表現する1つの便利な方法は、次のセクションで説明するように、入れ子になった$\sigma$-代数のシーケンスを使用することだ。また、ボレル$\sigma$-代数が十分な可測集合を含まないのではないかと心配するかもしれないが、これは問題ではなく、容易に非可測集合を見つけることはできない。


##### なぜ測度論的確率論を学ぶのか

技術的な理由は、このアプローチが**離散空間上の分布と連続空間上の密度を統一することを可能にする**からである。たとえば、確率$1 / 2$でゼロとなり、それ以外の場合は標準ガウス分布のように振る舞う確率変数のような、**両方の要素を組み合わせた確率変数を扱う場合に、この統一が必要になる**ことがある。このような確率変数は、いわゆる「混合連続および離散分布」を生み出し、確率を素朴に扱うアプローチでは特別な処理が必要に思えるが、測度論的アプローチではこれらの確率変数を扱うことは何ら異常ではない。



##### 確率空間と確率変数についての法則

確率論における大きな「陰謀」は、測度を定義するためには確率空間が必要にもかかわらず、定理の記述において確率空間がほとんど言及されないということである。代わりに、確率要素とそれらの結合確率に対する制約に基づいて記述される。
例えば、$X$と$Y$が確率変数であり、

$$
\mathbb{P}(X \in A, Y \in B)=\frac{|A \cap[6]|}{6} \cdot \frac{|B \cap[2]|}{2} \quad \text { for all } A, B \in \mathfrak{B}(\mathbb{R}),
$$

となる場合、これはサイコロ$(X \in[6])$とコイン$(Y \in[2])$の値の結合分布(**同時確率分布**)を表す。この公式は$X$と$Y$の出力間の確率的相互作用に関するいくつかの制約を記述するが、その**ドメインについては何も言及しない**。ある意味で、ドメインは重要な詳細ではない。それにもかかわらず、適切なドメインがそもそも存在するかどうかを尋ねる必要がある。より一般的には、ランダム変数のコレクション$X_1, \ldots, X_k$の結合法に関するいくつかの制約が与えられた場合に、**適切な確率空間が存在するかどうか**を尋ねることができる。これには、制約が相互に矛盾しないことが意味され、つまり$\mathfrak{B}\left(\mathbb{R}^k\right)$上に$\mu$という確率測度が存在し、$\mu$が想定された制約を満たすことを意味する。その場合、$\Omega=\mathbb{R}^k, \mathcal{F}=\mathfrak{B}\left(\mathbb{R}^k\right), \mathbb{P}=\mu$を選び、$X_i: \Omega \rightarrow \mathbb{R}$を$i$番目の座標マップとする：$X_i(\omega)=\omega_i$。$\mathbb{P}$の$X=\left(X_1, \ldots, X_k\right)$の下での押し出し測度は$\mu$であり、これは定義により制約と互換性がある。


##### $\sigma$-代数の直積

特定の制約を持つ集合に対して、制約と互換性がある測度$\mu$が存在するかというより具体的な問題がある。しばしば、制約は有限個の$\sigma$-代数の直積の要素に対して指定される。もし$(\Omega_1, \mathcal{F}_1), \ldots,(\Omega_n, \mathcal{F}_n)$が可測空間である場合、$\mathcal{F}_1, \ldots \mathcal{F}_n$の直積は

$$
\mathcal{F}_1 \times \cdots \times \mathcal{F}_n=\left\{A_1 \times \cdots \times A_n: A_1 \in \mathcal{F}_1, \ldots, A_n \in \mathcal{F}_n\right\} \subseteq 2^{\Omega_1 \times \cdots \times \Omega_n}
$$

となる。このセットの要素は$\Omega_1 \times \cdots \times \Omega_n$の中で可測長方形として知られている。


##### 定理2.4（カラテオドリの拡張定理）
$(\Omega_1, \mathcal{F}_1), \ldots,(\Omega_n, \mathcal{F}_n)$を可測空間とし、$\bar{\mu}: \mathcal{F}_1 \times \cdots \times \mathcal{F}_{n} \rightarrow[0,1]$を関数とする。この関数は以下の条件を満たす：

(a) $\bar{\mu}\left(\Omega_1 \times \cdots \times \Omega_n\right)=1$；及び
(b) すべての$A_k \in \mathcal{F}_1 \times \cdots \times \mathcal{F}_n$において互いに素な集合の列に対して$\bar{\mu}\left(\cup_{k=1}^{\infty} A_k\right)=\sum_{k=1}^{\infty} \bar{\mu}\left(A_k\right)$が成り立つ。

$\Omega=\Omega_1 \times \cdots \times \Omega_{n}$および$\mathcal{F}=\sigma\left(\mathcal{F}_1 \times \cdots \times \mathcal{F}_n\right)$とする。すると、
・$\mu$が$\mathcal{F}_1 \times \cdots \times \mathcal{F}_n$上の$\bar{\mu}$と一致するような、$(\Omega, \mathcal{F})$上の一意な確率測度$\mu$が存在する。


この定理は、$\Omega_k=\mathbb{R}$および$\mathcal{F}_k=\mathfrak{B}(\mathbb{R})$として適用される。その後、直積のすべての値に対する測度の値が一意に決まり、それによってどこでもその値が一意に定まる。

##### コラム
$\mathcal{F}_1 \times \mathcal{F}_2=\sigma\left(\mathcal{F}_1 \times \mathcal{F}_2\right)$とは限らない。例えば、$\mathcal{F}_1=\mathcal{F}_2=2^{\{1,2\}}$とする。その場合、$\left|\mathcal{F}_1 \times \mathcal{F}_2\right|=1+3 \times 3=10$（$\emptyset \times X=\emptyset$のため）であるが、$\mathcal{F}_1 \times \mathcal{F}_2$が$2^{\{1,2\} \times\{1,2\}}$のシングルトンを含むので、$\sigma\left(\mathcal{F}_1 \times \mathcal{F}_2\right)=2^{\{1,2\} \times\{1,2\}}$となる。したがって、$\mathcal{F}_1 \times \mathcal{F}_2$から6つの集合が欠けている。例えば、$\{(1,1),(2,2)\} \in \sigma\left(\mathcal{F}_1 \times \mathcal{F}_2\right) \backslash \mathcal{F}_1 \times \mathcal{F}_2$である。
$\sigma\left(\mathcal{F}_1 \times \cdots \times \mathcal{F}_n\right)$の$\sigma$-代数は、$\left(\mathcal{F}_k\right)_{k \in[n]}$の積$\sigma$-代数と呼ばれ、$\mathcal{F}_1 \otimes \cdots \otimes \mathcal{F}_n$とも記される。積演算は結合的であり、$\left(\mathcal{F}_1 \otimes \mathcal{F}_2\right) \otimes \mathcal{F}_3=\mathcal{F}_1 \otimes\left(\mathcal{F}_2 \otimes \mathcal{F}_3\right)$となるため、$\mathcal{F}_1 \otimes \mathcal{F}_2 \otimes \mathcal{F}_3$と書くことが正当化される。ボレル$\sigma$-代数に関しても同様にうまくいくことがわかる：$p, q \in \mathbb{N}^{+}$に対して、$\mathfrak{B}\left(\mathbb{R}^{p+q}\right)=\mathfrak{B}\left(\mathbb{R}^p\right) \otimes \mathfrak{B}\left(\mathbb{R}^q\right)$である。言うまでもなく、積に2つ以上の項がある場合も同様である。$\mathcal{F}$の$n$倍の積$\sigma$-代数は$\mathcal{F}^{\otimes n}$と表記される。

##### $\sigma$-代数と知識

測度論的確率の概念的な利点の一つは、$\sigma$-代数と「知識」という直感的なアイデアとの関係にある。この関係は有用で直感的だが、残念ながら完璧ではない。可測空間$(\Omega, \mathcal{F})$、$(\mathcal{X}, \mathcal{G})$、$(\mathcal{Y}, \mathcal{H})$が与えられ、$X: \Omega \rightarrow \mathcal{X}$と$Y: \Omega \rightarrow \mathcal{Y}$が確率要素であるとする。$X$の値を観測した（「$X^{\prime}$を知っている」）後、これが$Y$の値について何を意味するのか、さらに簡単に言うと、$X$を観測した後に$Y$の値を正確に決定できる状況はどのようなものか、ということを考えるかもしれない。この状況は図2.3で示されている。ある制約の下で、答えは$X$と$Y$によって生成される$\sigma$-代数の観点で考えることができる．

![[Pasted image 20240410211443.png]]
　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　図2.3 因数分解問題は、図が可換になるような（可測な）関数$f$が存在するかどうかを尋ねる。
　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　

$(\mathcal{Y}, \mathcal{H})$に対する技術的な仮定を除いて、以下の結果は$Y$が$X$の可測関数である場合に限り、$Y$が$\sigma(X) / \mathcal{H}$-可測であることを示している。言及された技術的仮定は$(\mathcal{Y}, \mathcal{H})$がボレル空間であることを要求し、これは本書で考慮される全ての確率空間、$(\mathbb{R}^k, \mathfrak{B}\left(\mathbb{R}^k\right))$を含む、に真である。ボレル空間の正確な定義は次の章に委ねられる。

##### 補題2.5（因数分解補題）
$(\mathcal{Y}, \mathcal{H})$がボレル空間であると仮定する。その場合、$Y$が$\sigma(X)$-可測である（$\sigma(Y) \subseteq \sigma(X)$）のは、$Y=f \circ X$となる$\mathcal{G} / \mathcal{H}$-可測な$\operatorname{map} f: \mathcal{X} \rightarrow \mathcal{Y}$が存在する場合に限られる。

この意味で$\sigma(X)$は、$X$から可測関数を通じて抽出可能な全ての情報を含んでいる。これは$Y$が$X$から導き出せる場合に限り$Y$が$\sigma(X)$-可測であると言うのと同じではない。なぜなら$\mathcal{X} \rightarrow \mathcal{Y}$への写像の集合は$\mathcal{G} / \mathcal{H}$-可測関数のセットよりもはるかに大きいかもしれないからだ。$\mathcal{G}$が粗い場合、$\mathcal{G} / \mathcal{H}$-可測関数はあまり多くなく、$\mathcal{G}=\{\mathcal{X}, \emptyset\}$の場合が極端な例である。このような場合、$\sigma(X)$が$X$について知り得る全てを捉えているという直感はもはや真ではない（**練習問題2.6**）。問題は$\sigma(X)$が$X$にのみ依存するのではなく、$(\mathcal{X}, \mathcal{G})$の$\sigma$-代数にも依存し、$\mathcal{G}$が粗い場合、$\sigma(X)$も粗くなり、多くの関数が$\sigma(X)$-可測にならないことにある。$X$が確率変数であれば、定義により$\mathcal{X}=\mathbb{R}$および$\mathcal{G}=\mathfrak{B}(\mathbb{R})$であり、これは比較的細かい粒度であり、$f$が可測である要件はそれほど制限的ではない。それにもかかわらず、最も良い設定である$\Omega=\mathcal{X}=\mathcal{Y}=\mathbb{R}$および$\mathcal{F}=\mathcal{G}=\mathcal{H}=\mathfrak{B}(\mathbb{R})$でも、$Y=f \circ X$となる非可測な$f$が存在することがある。言い換えると、$Y$に関する全ての情報は$X$に存在するが、**可測な方法で抽出することはできない**。これらの問題は、$X$が$\Omega$の可測集合を$\mathcal{X}$の非可測集合に写像する場合にのみ発生する。幸いなことに、このような確率変数は存在するが、応用では決して遭遇しないため、$\sigma(X)$が出会う可能性のある任意の確率変数$X$について知るべき全てを含んでいると考えることに最終的な正当性が与えられる。



##### 条件付き確率
条件付き確率は、ランダムな結果について部分的な知識を得たときに、確率がどのように更新されるべきかについて話すために導入される。確率空間$(\Omega, \mathcal{F}, \mathbb{P})$を考え、$\mathbb{P}(B)>0$であるような$A, B \in \mathcal{F}$が与えられたとする。$B$が与えられたときの$A$の条件付き確率$\mathbb{P}(A \mid B)$は次のように定義される：

$$
\mathbb{P}(A \mid B)=\frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)} .
$$
##### 条件付き確率の例
結果$\omega \in \Omega$を多面体のサイコロを投げた結果と考える。問われる確率は、$\omega \in B$となった状態で、サイコロが$\omega \in A$となるように着地した確率である。条件$\omega \in B$の意味は、$\omega \in B$が真のときのサイコロのロールに焦点を当てることである。$\omega \in B$が成立しないすべてのサイコロのロールは除外される。直感的に、$B$が与えられた$A$の条件付き確率において重要なのは、$B$の中に$A$のどれだけの部分があるかであり、これがまさに定義の意味するところである。

##### 条件付き確率の重要性
条件付き確率の重要性は、追加情報が与えられた中で，確率がどのように更新されるべきかの計算法を定義することにある。$\mathbb{P}(A \mid B)$は、$B$が与えられた$A$の事後確率と呼ばれる。事前確率は$\mathbb{P}(A)$である。$\mathbb{P}(B)>0$である限り、すべての$A \in \mathcal{F}$に対して$\mathbb{P}(A \mid B)$が定義される。実際、$A \mapsto \mathbb{P}(A \mid B)$は、$B$が与えられた事後確率測度と呼ばれる測度空間$(\Omega, \mathcal{F})$上の確率測度である（**練習問題2.7参照**）。言葉「事後」と「事前」に付随する時間的特性はやや誤解を招く可能性がある。確率は予測に関連している。未来のイベントに割り当てられる不確実性の度合いを表す。$B$という特定の条件が与えられた場合のランダム実験の結果の特定の性質の予測が、$A$が与えられた$B$の条件付き確率である。**すべては未来の仮定された結果に関連している**。サイコロが投げられると、$\omega$が固定され、$\omega \in A, B$かそうでないかが決まる。実験が終了した後には不確実性は残らず、予測は実験後には自明となる。

##### ベイズの定理
ベイズの定理は、$A, B \in \mathcal{F}$の両方が正の確率で発生する場合に次のように述べている：

$$
\mathbb{P}(A \mid B)=\frac{\mathbb{P}(B \mid A) \mathbb{P}(A)}{\mathbb{P}(B)} .
$$

ベイズの定理は、右辺の量に関する情報に基づいて$\mathbb{P}(A \mid B)$を得ることを可能にするために役立つ。この単純な式が確率論と統計学において非常に重要な地位を持つ理由は、このようなケースが非常に頻繁に発生するためである。**練習問題2.8**は、この法則を確認することを読者に求めている。独立性は、知識/情報に関連する確率論の別の基本的な概念である。最も単純な形で、独立性は確率空間$(\Omega, \mathcal{F}, \mathbb{P})$上のイベント間に成り立つ関係である。2つのイベント$A, B \in \mathcal{F}$が独立である場合、

$$
\mathbb{P}(A \cap B)=\mathbb{P}(A) \mathbb{P}(B) .
$$

これは知識とどのように関連しているか？$\mathbb{P}(B)>0$と仮定して、両辺を$\mathbb{P}(B)$で割り、条件付き確率の定義を使用すると、上記は

$$
\mathbb{P}(A \mid B)=\mathbb{P}(A) .
$$

と等価であることがわかる。もちろん、$\mathbb{P}(A)>0$の場合、$(2.3)$は$\mathbb{P}(B \mid A)=\mathbb{P}(B)$と等価である。後者の両方の関係は、$A$と$B$が独立である場合、$B$（それぞれ、$A$）が発生したことが知られているかどうかにかかわらず、$A$（または$B$）に割り当てられた確率が同じままであることを表している。


##### 独立性
「影響の欠如」という観点での独立性の定義を、読者が合理的であると感じることを願っている。$(2.4)$を定義として使用しない理由は主に便宜上である。$(2.4)$から始めた場合、$\mathbb{P}(B)=0$のケースを別途議論する必要があり、それは面倒である。2つ目の理由は、$(2.4)$は非対称な関係を示唆しているが、直感的には独立性が対称であることを期待するからである。不確定な結果はしばしば部分的に生成され、プロセス間の相互作用がないことが自然に独立性の構造につながる（複数のサイコロをロールし、ロール間に相互作用がない場合を考えてみる）。独立性の構造を発見すると、確率の計算が大幅に簡素化される。実際、独立性はしばしば関心のある確率測度を構築する方法として使用される（$(2.1)$式、**定理2.4**および**練習問題2.9**を参照）。独立性は、構築から想定されるよりも多くの独立イベントを確率空間が持っているという意味で偶然にも現れることがある（**練習問題2.10**）。独立性に関する仮定が本当に正当化されているかどうかを常に慎重に判断するべきである。これはモデリングの一部であり、その性質は数学的ではない。代わりに、モデル化されている物理的プロセスについて考える必要がある。


##### 互いに独立，相互に独立
・イベントのコレクション$\mathcal{G} \subset \mathcal{F}$が、$\mathcal{G}$の任意の2つの異なる要素が互いに独立している場合、対で独立していると言われる。
・$\mathcal{G}$内のイベントが相互に独立しているとは、任意の$n>0$の整数と$\mathcal{G}$の異なる要素$A_1, \ldots, A_n$に対して、$\mathbb{P}\left(A_1 \cap \cdots \cap A_n\right)=\prod_{i=1}^n \mathbb{P}\left(A_i\right)$であることを意味する。

これは対での独立性よりも強い制約である。相互に独立したイベントの場合、コレクションから任意の有限個のイベントの共同発生の知識は、コレクション内の他のイベントが起こるかどうかの予測を変えない。しかし、イベントが対でのみ独立している場合、このようなことはないかもしれない（**練習問題2.10**）。

2つのイベントコレクション$\mathcal{G}_1, \mathcal{G}_2$が互いに独立しているとは、
・$\mathcal{G}_1$の任意の$A$と$\mathcal{G}_2$の任意の$B$に対して、$A$と$B$が独立していることを意味する。

この定義はしばしば$\sigma$-代数に適用される。

$\sigma$-代数が確率変数によって誘導される場合、これは確率変数間の独立性の定義につながる。
・2つの確率変数$X$と$Y$が独立している場合、$\sigma(X)$と$\sigma(Y)$は互いに独立している。

対の独立性と相互の独立性の概念は自然に確率変数のコレクションに適用されるように拡張することができる。これらのすべての概念は実際に確率要素にまで拡張される。

複数のイベントや確率変数が関与する場合の独立性のデフォルトの意味は、相互の独立性である。
・$X_1, \ldots, X_n$が独立した確率変数であると言うとき、それらが相互に独立していることを意味する。

独立性は常にある確率測度に対して相対的であり、確率測度が明示的に言及されていない場合でもそうである。そのような場合、確率測度のアイデンティティは文脈から明らかであるべきである。


##### 期待値
確率論における重要な量の一つが確率変数の期待値である。確率空間$(\Omega, \mathcal{F}, \mathbb{P})$と確率変数$X: \Omega \rightarrow \mathbb{R}$を固定する。$X$の期待値はしばしば$\mathbb{E}[X]$と表される。**この表記は残念ながら$\mathbb{P}$に依存することを隠してしまう**。基礎となる測度が文脈から明らかでない場合は、$\mathbb{P}$に関して期待値を示すために$\mathbb{E}_{\mathbb{P}}$と書く。数学的には、**$X$の期待値を$\mathbb{P}$に関する$X$のルベーグ積分**として定義する：

$$
\mathbb{E}[X]=\int_{\Omega} X(\omega) \mathrm{d} \mathbb{P}(\omega) .
$$

右辺は$\int X \mathrm{~d} \mathbb{P}$とも短縮して書かれることがよくある。右辺の積分は、以下の2つの主要な性質を満たすように構築される：
(a) 指示関数の積分は、基礎となるイベントの確率である。$X(\omega)=$ $\mathbb{I}\{\omega \in A\}$がある$A \in \mathcal{F}$の指示関数である場合、$\int X \mathrm{~d} \mathbb{P}=\mathbb{P}(A)$である。
(b) 積分は線形である。$\int X_1 \mathrm{dP}$および$\int X_2 \mathrm{dP}$が定義されたすべての確率変数$X_1, X_2$と実数$\alpha_1, \alpha_2$に対して、$\int\left(\alpha_1 X_1+\alpha_2 X_2\right) \mathrm{dP}$は定義され、次の式を満たす：

$$
\int_{\Omega}\left(\alpha_1 X_1+\alpha_2 X_2\right) \mathrm{d} \mathbb{P}=\alpha_1 \int_{\Omega} X_1 \mathrm{dP}+\alpha_2 \int_{\Omega} X_2 \mathrm{dP} .
$$

これら2つの性質を合わせると、$X(\omega)=\sum_{i=1}^n \alpha_i \mathbb{I}\left\{\omega \in A_i\right\}$であるような$n, \alpha_i \in \mathbb{R}$および$A_i \in \mathcal{F}, i=1, \ldots, n$の場合、次のようになる：

$$
\int_{\Omega} X \mathrm{~d} \mathbb{P}=\sum_i \alpha_i \mathbb{P}\left(A_i\right) .
$$

この形の関数を単関数と呼ぶ。
確率変数$X$のルベーグ積分を定義する際には、$X$が単関数である場合の積分の定義として(2.6)を使用する。次のステップは、非負の確率変数へ定義を拡張することである。$X: \Omega \rightarrow[0, \infty)$が可測であるとする。アイデアは、**$X$を単関数を使用して下から近似し、この方法で得られる最大値を取ることである**：

$$
\int_{\Omega} X \mathrm{dP}=\sup \left\{\int_{\Omega} h \mathrm{dP}: h \text { が単関数で } 0 \leq h \leq X\right\} .
$$

確率変数$U, V$に対して$U \leq V$の意味は、全ての$\omega \in \Omega$に対して$U(\omega) \leq V(\omega)$であることである。右辺の上限が無限である場合、$X$の積分は定義されないと言われる。$X$の積分が定義されている場合、**$X$は可積分**である、または$\mathbb{P}$のアイデンティティが不明瞭な場合は、**$\mathbb{P}$に関して$X$が可積分**であると言われる。非負の値の上限を取っているため、$\int_{\Omega} X d P \geq 0$であることに注意。

##### 任意の確率変数に対するルベーグ積分
任意の確率変数に対する積分は、確率変数を正および負の部分に分解することによって定義される。$X: \Omega \rightarrow \mathbb{R}$が任意の可測関数であるとする。その後、$X^{+}(\omega)=X(\omega) \mathbb{I}\{X(\omega)>0\}$および$X^{-}(\omega)=$ $-X(\omega) \mathbb{I}\{X(\omega)<0\}$と定義し、$X(\omega)=X^{+}(\omega)-X^{-}(\omega)$とする。今、$X^{+}$および$X^{-}$はどちらも非負の確率変数であり、$X$の正および負の部分と呼ばれる。$X^{+}$および$X^{-}$がともに可積分である場合、次のように定義する：

$$
\int_{\Omega} X \mathrm{dP}=\int_{\Omega} X^{+} \mathrm{d} \mathbb{P}-\int_{\Omega} X^{-} \mathrm{d} \mathbb{P}
$$

そして$X$が可積分であると言う。**確率変数$X$が可積分であるのは、非負値の確率変数$|X|$が可積分である場合に限る**（**練習問題2.13**）。

特に興味深いケースは、$\Omega=\mathbb{R}$が実数直線であり、$\mathcal{F}=\mathfrak{B}(\mathbb{R})$がボレル$\sigma$-代数であり、**測度が任意の$a \leq b$に対して$\lambda((a, b))=b-a$であるような$\mathfrak{B}(\mathbb{R})$上の唯一の測度であるルベーグ測度$\lambda$である場合**である。このシナリオでは、$f: \mathbb{R} \rightarrow \mathbb{R}$がボレル可測関数である場合、ルベーグ測度に関する$f$のルベーグ積分を

$$
\int_{\mathbb{R}} f d \lambda .
$$

と書くことができる。おそらく驚くことではないが、これはほとんどの場合、$f$の不適切なリーマン積分、通常は$\int_{-\infty}^{\infty} f(x) d x$として書かれるものと一致する。正確には、**$|f|$がルベーグ可積分かつリーマン可積分である場合、積分は等しい**。

##### リーマン積分とルベーグ積分
リーマン可積分であってルベーグ可積分でない関数が存在し、その逆もまた真である（ただし、前者の例の方が後者よりも珍しい）。ルベーグ測度とそのリーマン積分との関係が言及されるのは、期待値や積分の値を実際に計算する場合、これがしばしば**ルベーグ測度に関して実数直線上での積分を計算することに帰着する**ためである。その後、リーマン積分を評価することにより、多くの基本関数の積分を再導出する必要性を回避しながら計算が実行される。

##### ルベーグ積分，期待値の性質
積分（そして期待値）には多くの重要な特性がある。最も重要なのはその**線形性**であり、期待値を使った表記を練習するために、この性質の前半を再述する。実際には、積分に対して上で要求したものよりもわずかに一般的な主張である。

##### 命題2.6
同じ確率空間上の（無限に可能性のある）確率変数の列$\left(X_i\right)_i$について、全ての$i$に対して$\mathbb{E}\left[X_i\right]$が存在し、さらに$X=\sum_i X_i$および$\mathbb{E}\left[\sum_i\left|X_i\right|\right]$も存在すると仮定する。その場合、

$$
\mathbb{E}[X]=\sum_i \mathbb{E}\left[X_i\right] .
$$
##### 期待値と和の交換
期待値と和の交換は、確率論において多くの魔法の源であり、$X_i$が独立でない場合でも成り立つ。これは（確率とは異なり）**依存する確率変数の期待値を非常にしばしば分離できる**ことを意味し、これはしばしば非常に有用である（一連の確率変数が依存している場合、それらは独立ではない）。命題2.6は**練習問題2.15**で証明される。
線形性のもう一つの要件は、**$c \in \mathbb{R}$が定数である場合、$\mathbb{E}[c X]=c \mathbb{E}[X]$である**（**練習問題2.16**）。

独立した確率変数に関する別の重要な性質もある。


##### 命題2.7
もし$X$と$Y$が独立で、$\mathbb{E}[|X|], \mathbb{E}[|Y|]<\infty$のどちらか、または$\mathbb{E}[|X Y|]<\infty$であるならば、$\mathbb{E}[X Y]=\mathbb{E}[X] \mathbb{E}[Y]$である。一般に$\mathbb{E}[X Y] \neq \mathbb{E}[X] \mathbb{E}[Y]$である（**練習問題2.19**）。

##### 命題2.8.
もし$X \geq 0$が非負の確率変数であるならば、

$$
\mathbb{E}[X]=\int_0^{\infty} \mathbb{P}(X>x) d x .
$$

命題2.8の被積分関数は$X$のしっぽ確率関数$x \mapsto \mathbb{P}(X>x)$と呼ばれる。これは$X$の補完累積分布関数としても知られている。$X$の**累積分布関数**（**CDF**）は$x \mapsto \mathbb{P}(X \leq x)$として定義され、通常$F_X$と表記される。これらの関数は非負のものだけでなく、すべての確率変数に定義される。$F_X: \mathbb{R} \rightarrow[0,1]$が増加し、右連続であり、$\lim _{x \rightarrow-\infty} F_X(x)=0$および$\lim _{x \rightarrow \infty} F_X(x)=1$であることが確認できる。確率変数の**CDF**は$X$によって誘導される確率測度$\mathbb{P}_X$のすべての側面を捉えるが、それでも実数直線上の関数に過ぎず、これは$\mathbb{P}_X$よりも少し人間にとってフレンドリーな性質である。**CDF**を確率ベクトルに一般化することもできる：もし$X$が$\mathbb{R}^k$-値の確率ベクトルである場合、そのCDFは$F_X: \mathbb{R}^k \rightarrow[0,1]$関数として定義され、$F_X(x)=\mathbb{P}(X \leq x)$を満たす。ここで、慣例に従って、$X \leq x$は$X$のすべての成分が$x$の対応する成分以下であることを意味する。

確率要素の押し出し測度$\mathbb{P}_X$は$X$の分布を要約する別の方法である。特に、任意の実数値の、$f: \mathcal{X} \rightarrow \mathbb{R}$可測関数に対して、

$$
\mathbb{E}[f(X)]=\int_{\mathcal{X}} f(x) \mathrm{d}^X(x)
$$

は、右辺または左辺が存在する場合に成り立つ。これは「無意識の統計学者の法則」、またはLOTUSとして知られている。なぜなら、これが頻繁に使用されるからである。

##### 条件付き期待値
条件付き期待値は、別の確率変数の値、あるいはより一般的にはある$\sigma$-代数が与えられた場合の確率変数の期待値について話すことを可能にする。

例2.9. $(\Omega, \mathcal{F}, \mathbb{P})$が不均等なサイコロの結果をモデル化するとする：$\Omega=[6]$、$\mathcal{F}=2^{\Omega}$、$\mathbb{P}(A)=|A| / 6$である。2つの確率変数$X$と$Y$を$Y(\omega)=\mathbb{I}\{\omega>3\}$および$X(\omega)=\omega$によって定義する。特定の$Y$の値が与えられたときの$X$の期待値に興味があると仮定する。直感的に考えると、$Y=1$は観測されていない$X$が4、5、または6のいずれかであり、これらの結果が同様に可能性があることを意味し、したがって$Y=1$が与えられた$X$の期待値は$(4+5+6) / 3=5$であるべきである。同様に、$Y=0$が与えられた$X$の期待値は$(1+2+3) / 3=2$であるべきである。簡潔な要約を求めるならば、単に「$Y^{\prime}$が与えられた$X$の期待値は$5Y+2(1-Y)$である」と書くことができる。これが自体が確率変数であることに注意。

この条件付き期待値の表記は$\mathbb{E}[X \mid Y]$である。この表記を使用して、例2.9では$\mathbb{E}[X \mid Y]=5Y+2(1-Y)$と簡潔に書くことができる。もう少し一般的には、$X: \Omega \rightarrow \mathcal{X}$および$Y: \Omega \rightarrow \mathcal{Y}$で$\mathcal{X}, \mathcal{Y} \subset \mathbb{R}$および$|\mathcal{X}|,|\mathcal{Y}|<\infty$の場合、$\mathbb{E}[X \mid Y]: \Omega \rightarrow \mathbb{R}$は$\mathbb{E}[X \mid Y](\omega)=\mathbb{E}[X \mid Y=Y(\omega)]$によって与えられる確率変数である。ここで、

$$
\mathbb{E}[X \mid Y=y]=\sum_{x \in \mathcal{X}} x \mathbb{P}(X=x \mid Y=y)=\sum_{x \in \mathcal{X}} \frac{x \mathbb{P}(X=x, Y=y)}{\mathbb{P}(Y=y)} .
$$

これは$\mathbb{P}(Y=y)=0$の場合に未定義であるため、$\mathbb{E}[X \mid Y](\omega)$は測度ゼロの集合$\{\omega: \mathbb{P}(Y=Y(\omega))=0\}$上で未定義である。

式(2.8)は、分母の$\mathbb{P}(Y=y)$が全ての$y$に対してゼロになる可能性があるため、連続確率変数に一般化することはできない。例えば、$Y$が一様分布に従って$[0,1]$の値を取る確率変数であり、$X \in\{0,1\}$がバイアス$Y$でベルヌーイ分布であるとする。これは、$X$と$Y$の結合測度が$\mathbb{P}(X=1, Y \in[p, q])=\int_p^q x d x$で$0 \leq p<q \leq 1$であることを意味する。直感的には、$\mathbb{E}[X \mid Y]$は$Y$に等しいべきであるが、どのように定義すればよいか？ベルヌーイ確率変数の平均はそのバイアスに等しいので、条件付き確率の定義は$0 \leq p<q \leq 1$の場合、

$$
\begin{aligned}
\mathbb{E}[X=1 \mid Y \in[p, q]] & =\mathbb{P}(X=1 \mid Y \in[p, q]) \\
& =\frac{\mathbb{P}(X=1, Y \in[p, q])}{\mathbb{P}(Y \in[p, q])} \\
& =\frac{q^2-p^2}{2(q-p)} \\
& =\frac{p+q}{2} .
\end{aligned}
$$

$p=q$の場合、この計算は$\mathbb{P}(Y \in[p, p])=0$であるため、適切に定義されていない。それでも、$q=p+\varepsilon$で$\varepsilon>0$として$\varepsilon$がゼロに近づく限りを取るのは、$\mathbb{P}(X=1 \mid Y=p)=p$であると主張する合理的な方法のように思える。残念ながら、このアプローチは測度ゼロの集合に向けて極限を取る正準的な方法がなく、異なる選択が異なる答えにつながるため、抽象的な空間に一般化することはできない。


代わりに、式(2.8)を条件付き期待値の抽象的な定義の出発点として使用し、2つの要件を満たす確率変数として定義する。まず、式(2.8)から$\mathbb{E}[X \mid Y](\omega)$は$Y(\omega)$にのみ依存すべきであり、したがって$\sigma(Y)$に関して可測であるべきであることがわかる。2番目の要件は「平均化性質」と呼ばれる。可測な$A \subseteq \mathcal{Y}$に対して、式(2.8)は以下を示している：

$$
\begin{aligned}
& \mathbb{E}\left[\mathbb{I}_{Y-1}(A) \mathbb{E}[X \mid Y]\right]=\sum_{y \in A} \mathbb{P}(Y=y) \mathbb{E}[X \mid Y=y] \\
& =\sum_{y \in A} \sum_{x \in \mathcal{X}} x \mathbb{P}(X=x, Y=y) \\
& =\mathbb{E}\left[\mathbb{I}_{Y-1(A)} X\right]。 \\
&
\end{aligned}
$$

これは、可測な$A \subseteq \mathcal{Y}$ごとに1つの制約を持つ一連の線形制約を$\mathbb{E}[X \mid Y]$に課すと見なすことができる。$\mathbb{E}[X \mid Y]$を未知の$\sigma(Y)$-可測確率変数として扱い、この線形システムを解こうと試みることができる。実際、これは常に可能である：線形制約と$\mathbb{E}[X \mid Y]$に対する可測性の制限は、測度ゼロの集合を除いて$\mathbb{E}[X \mid Y]$を完全に決定する。両方の条件は$\sigma(Y) \subseteq \mathcal{F}$にのみ依存することに注意。条件付き期待値の抽象的な定義はこれらの特性を定義として取り、$Y$の役割を部分$\sigma$-代数に置き換える。

##### 定義2.10（条件付き期待値）

確率空間$(\Omega, \mathcal{F}, \mathbb{P})$と確率変数$X: \Omega \rightarrow \mathbb{R}$および$\mathcal{F}$の部分$\sigma$-代数である$\mathcal{H}$が与えられたとき、$X$の$\mathcal{H}$に対する条件付き期待値は$\mathbb{E}[X \mid \mathcal{H}]$と記され、全ての$H \in \mathcal{H}$に対して

$$
\int_H \mathbb{E}[X \mid \mathcal{H}] \mathrm{d} \mathbb{P}=\int_H X \mathrm{dP} .
$$

が成り立つような$\Omega$上の$\mathcal{H}$-可測確率変数として定義される。確率変数$Y$が与えられた場合、$X$の$Y$に対する条件付き期待値は$\mathbb{E}[X \mid Y]=\mathbb{E}[X \mid \sigma(Y)]$である。


##### 定理2.11
任意の確率空間$(\Omega, \mathcal{F}, \mathbb{P})$、$\mathcal{F}$の部分$\sigma$-代数$\mathcal{H}$、および$\mathbb{P}$-可積分な確率変数$X: \Omega \rightarrow \mathbb{R}$が与えられた場合、
(2.9)を満たす$\mathcal{H}$-可測関数$f: \Omega \rightarrow \mathbb{R}$が存在する。さらに、(2.9)を満たす任意の2つの$\mathcal{H}$-可測関数$f_1, f_2: \Omega \rightarrow \mathbb{R}$は確率1で等しい：$\mathbb{P}\left(f_1=f_2\right)=1$。


##### a.s.
確率変数$X$と$Y$が$\mathbb{P}$-確率1で一致する場合、それらは$\mathbb{P}$-ほとんど確実に等しい(almost surely)と言われ、これはしばしば'$X=Y \mathbb{P}$-a.s.'、または測度が文脈から明らかな場合は'$X=Y$ a.s.'と略される。関連する有用な概念は、無視できる集合の概念である：$U \in \mathcal{F}$が$\mathbb{P}$の無視できる集合、または$\mathbb{P}$-無視できる集合である場合は、$\mathbb{P}(U)=0$である。したがって、$X=Y \mathbb{P}$-a.s.である場合は、$X=Y$が$\mathbb{P}$-無視できる集合を除いて一致する場合に限る。




$\mathbb{E}[X \mid Y]$が$Y$の範囲ではなく$\Omega$上の確率変数であるという事実は、読者にとって奇妙に思えるかもしれない。補題2.5と$\mathbb{E}[X \mid \sigma(Y)]$が$\sigma(Y)$-可測であるという事実は、$\mathbb{E}[X \mid \sigma(Y)](\omega)=(f \circ Y)(\omega)$であるような可測関数$f:(\mathbb{R}, \mathfrak{B}(\mathbb{R})) \rightarrow$ $(\mathbb{R}, \mathfrak{B}(\mathbb{R}))$が存在することを示している（**図2.4参照**）。この意味で$\mathbb{E}[X \mid Y](\omega)$は$Y(\omega)$にのみ依存し、時々$\mathbb{E}[X \mid Y](y)$と書く。

![[Pasted image 20240410224924.png]]



例2.9に戻ると、$\mathbb{E}[X \mid Y]=\mathbb{E}[X \mid \sigma(Y)]$であり、$\sigma(Y)=\{\{1,2,3\},\{4,5,6\}, \emptyset, \Omega\}$である。簡潔にするためにこの集合系を$\mathcal{H}$と表記する。$\mathbb{E}[X \mid \mathcal{H}]$が$\mathcal{H}$-可測である条件は、$\mathbb{E}[X \mid \mathcal{H}](\omega)$が$\{1,2,3\}$および$\{4,5,6\}$上で定数である場合にのみ満たされる。そして(2.9)は直ちに

$$
\mathbb{E}[X \mid \mathcal{H}](\omega)= \begin{cases}2, & \text { if } \omega \in\{1,2,3\} ; \\ 5, & \text { if } \omega \in\{4,5,6\} .\end{cases}
$$

となることを示唆する。上記の条件付き期待値の定義は非構成的であり、$\mathbb{E}[X \mid \mathcal{H}]$は$\mathbb{P}$-測度ゼロのイベントに対してのみ一意に定義されるが、これが重要な問題になることはない。まず、条件付き期待値の閉じた形式の表現が必要とされることはほとんどなく、他の期待値、条件付きかそうでないかに関連する方法が必要である。条件付き期待値がゼロ確率のイベントに対してのみ決定されるという事実が問題ではない理由もこれである：通常、条件付き期待値は他の期待値や、あるイベントがどれだけ起こりやすいかに関する声明に現れ、条件付き期待値の異なる「バージョン」間の違いを消す。


##### 条件付き期待値の性質
このセクションを締めくくるために、条件付き期待値のいくつかの追加の重要な特性をまとめます。これらは定義から直接導かれるものであり、読者には練習問題2.21でそれらを証明することを勧めます。

##### 定理2.12. 
確率空間$(\Omega, \mathcal{F}, \mathbb{P})$と$\mathcal{F}$の部分$\sigma$代数である$\mathcal{G}, \mathcal{G}_1, \mathcal{G}_2 \subset \mathcal{F}$、および$(\Omega, \mathcal{F}, \mathbb{P})$上の可積分な確率変数$X, Y$が与えられた場合、以下が成り立つ：

1. $X \geq 0$の場合、$\mathbb{E}[X \mid \mathcal{G}] \geq 0$がほぼ確実に成り立つ。
2. $\mathbb{E}[1 \mid \mathcal{G}]=1$がほぼ確実に成り立つ。
3. $\mathbb{E}[X+Y \mid \mathcal{G}]=\mathbb{E}[X \mid \mathcal{G}]+\mathbb{E}[Y \mid \mathcal{G}]$がほぼ確実に成り立つ。
4. $\mathbb{E}[X Y \mid \mathcal{G}]=Y \mathbb{E}[X \mid \mathcal{G}]$がほぼ確実に成り立つ場合、$\mathbb{E}[X Y]$が存在し、かつ$Y$が$\mathcal{G}$-可測である。
5. $\mathcal{G}_1 \subset \mathcal{G}_2$の場合、$\mathbb{E}\left[X \mid \mathcal{G}_1\right]=\mathbb{E}\left[\mathbb{E}\left[X \mid \mathcal{G}_2\right] \mid \mathcal{G}_1\right]$がほぼ確実に成り立つ。
6. $\sigma(X)$が$\mathcal{G}_1$に対して$\mathcal{G}_2$と与えられた条件下で独立である場合、$\mathbb{E}\left[X \mid \sigma\left(\mathcal{G}_1 \cup \mathcal{G}_2\right)\right]=\mathbb{E}\left[X \mid \mathcal{G}_1\right]$がほぼ確実に成り立つ。
7. $\mathcal{G}=\{\emptyset, \Omega\}$が自明な$\sigma$-代数である場合、$\mathbb{E}[X \mid \mathcal{G}]=\mathbb{E}[X]$がほぼ確実に成り立つ。

**特性1と2**は自明である。
**特性3**は期待値の線形性を一般化する。
**特性4**は、可測な量が条件付き期待値の外側に引き出されることを示し、定数$c$に対して$\mathbb{E}[c X]=c \mathbb{E}[X]$という性質に対応する。
**特性5**はタワールールまたは全期待値の法則と呼ばれ、$\mathbb{E}\left[X \mid \mathcal{G}_2\right]$の細かさが$\mathcal{G}_1$に関する条件付き期待値を取るときに無くなることを言う。
**特性6**は独立性と条件付き期待値との関係を示し、独立した量に基づく条件付き期待値は期待値に関するさらなる情報を与えないことを言う。
**特性7**は、情報に基づく条件付き期待値が全く条件付きでない期待値と同じであることを示す。

以上の抽象的な特性は何度も使用される。読者にはこのリストを注意深く学び、すべての項目が直感的であることを自分自身で確信することを勧める。離散確率変数で遊ぶことは、これを理解するのに非常に価値がある。やがてそれはすべて第二の性質となる。



##### 確率密度

密度について言及していないことに驚くかもしれない。連続空間上の確率に初めて触れるのは、正規分布とその密度

$$
p(x)=\frac{1}{\sqrt{2 \pi}} \exp \left(-x^2 / 2\right),
$$

を学んだ時であり、これを区間上で積分することで、ガウス確率変数がその区間における値を取る確率を得ることができる。読者は$p: \mathbb{R} \rightarrow \mathbb{R}$がボレル可測であり、この密度に関連するガウス測度は$(\mathbb{R}, \mathfrak{B}(\mathbb{R}))$上の$\mathbb{P}$で定義されることに注意すべきである．

$$
\mathbb{P}(A)=\int_A p d \lambda .
$$

ここでの積分は$(\mathbb{R}, \mathfrak{B}(\mathbb{R}))$上のルベーグ測度$\lambda$に関して行われる。この密度の概念は、このシンプルな設定を超えて一般化することができる。任意の可測空間$(\Omega, \mathcal{F})$上の測度（必ずしも確率測度である必要はない）である$P$と$Q$を考える。$P$に対する$Q$のラドン・ニコディム微分は、以下のような$\mathcal{F}$-可測確率変数$\frac{d P}{d Q}: \Omega \rightarrow[0, \infty)$であり、

$$
P(A)=\int_A \frac{d P}{d Q} d Q \quad \text { for all } A \in \mathcal{F} .
$$

であることが示される。この変更測度公式とも呼ばれる式は、任意の$X P$-可積分確率変数に対して、$\int X d P=\int X \frac{d P}{d Q} d Q$もまた成り立たなければならないことを意味する。ラドン・ニコディム微分$\frac{d P}{d Q}$は、$P$に対する$Q$の密度とも呼ばれる。密度が存在しない例を見つけるのは難しくない。$Q(A)=0 \Longrightarrow P(A)=0$となる全ての$A \in \mathcal{F}$に対して$P$が$Q$に対して絶対連続であると言う。$\frac{d P}{d Q}$が存在するとき、式(2.11)によって直ちに$P$が$Q$に対して絶対連続であることが導かれる。いくつかの病的なケースを除いて、これは$d P / d Q$の存在に必要かつ十分であることがわかる。測度$Q$が$\sigma$-有限であるとは、$\mathcal{F}$-可測集合である$\left\{A_i\right\}$の可算被覆が存在し、各$i$に対して$Q\left(A_i\right)<\infty$となることを意味する。

##### 定理2.13
共通の可測空間$(\Omega, \mathcal{F})$上の測度である$P, Q$を考え、$Q$が$\sigma$-有限であると仮定すると，
．$P$が$Q$に対して絶対連続である場合に限り、$P$に対する$Q$の密度、$\frac{d P}{d Q}$が存在する
・さらに、$\frac{d P}{d Q}$は$Q$-無視できる集合に対して一意に定義されるため、(2.11)を満たす任意の$f_1, f_2$に対して、$f_1=f_2$が$Q$-ほぼ確実に成り立つ

密度は期待通りに機能する。$Z$が標準ガウス確率変数であると仮定する。通常、式(2.10)に示された密度を書きますが、これはガウス測度のルベーグ測度に対するラドン・ニコディム微分であることがわかる。'古典的'な連続分布の密度は、ほぼ常にルベーグ測度に対して定義される。



#### ノート

1. ギリシャ文字の$\sigma$は、数学者によって可算無限に関連して頻繁に使用される。したがって、$\sigma$-代数（および$\sigma$-フィールド）という用語がある。可算加法性はしばしば$\sigma$-加法性と呼ばれる。加法性が可算無限の集合系に対して成立すべきであるという要求は、（興味深い）極限イベントの確率が存在することを保証するために設けられている。

2. 測度論は、可測空間、測度、およびそれらの特性に関係している。確率論と測度論の明らかな違いは、確率論では（主に）確率測度に関心があることだ。しかし、ここでの区別はそれだけではない。確率論では、確率測度とそれらの相互関係に焦点を当てている。可測空間は背景にあるが、主要な関心事のトピックというよりは、技術的なツールキットの一部と見なされる。また、確率論では、独立性がしばしば注目の中心にあるが、独立性は測度論者が特に関心を持つ性質ではない。

3. 私たちのおもちゃの例では、$\Omega=[6]^7$の代わりに$\Omega=[6]^8$（7つではなく8つのサイコロを振ることを考える、1つのサイコロは使用されない）を選ぶことができた。他にも多くの可能性がある。サイコロの振り代わりにコインフリップを考えることができる（これがどのように行われるか考えてみる）。これを簡単にするために、重み付けされたコイン（例えば、1/6の確率で表になるコイン）を使用することができるが、実際には重み付けされたコインを必要としない（これを見るのは少し難しいかもしれない）。主なポイントは、別のランダマイゼーションデバイスを使用して一つをエミュレートする方法が多数あるということだ。これらの違いは$\Omega$のセットだ。$\Omega$の選択が実行可能であるかどうかは、最終的に特定の値が見られる確率が同じままであるように、$\Omega$の上にゲームメカニズムをエミュレートできるかどうかにかかっている。しかし、主なポイントは、$\Omega$の選択は決して一意ではないということだ。ゲームの値の計算方法についても同じことが言える！例えば、最初の構成に留まる場合、サイコロは並べ替えられるかもしれない。これはすでに指摘されたが、確率の中で最大の陰謀が十分に頻繁に繰り返されることはない。

4. 有界領域上のすべてのリーマン可積分関数はルベーグ可積分である。問題は不適切な積分を取るときにのみ発生する。標準的な例は$\int_0^{\infty} \frac{\sin (x) d x}{x}$で、これは不適切なリーマン可積分関数だが、$\int_{(0, \infty)}|\sin (x) / x| d x=\infty$であるためルベーグ可積分ではない。この状況は、条件付き収束と絶対収束の系列との違いに類似しており、ルベーグ積分は後者の場合にのみ定義される。

5. ボレル可測でない集合について考えることができるか？そのような集合は存在するが、実際のアプリケーションでは自然には現れない。古典的な例はヴィタリ集合で、商群$G=\mathbb{R} / \mathbb{Q}$を取り、選択公理を適用して$G$の各同値類から$[0,1]$の代表元を選び出すことで形成される。非可測関数は非常に珍しいため、$X: \mathbb{R} \rightarrow \mathbb{R}$の関数が可測かどうかをあまり心配する必要はない。ほとんどの場合、この本で生じる可測性の問題は、ボレル$\sigma$-代数の微妙な詳細に関連しているわけではない。より頻繁には、フィルトレーションや特定の確率要素を観察した後に利用可能な知識の概念に関連している。

6. 確率変数の和や積がまた確率変数である理由、または$\inf _n X_n, \sup _n X_n, \lim \inf _n X_n, \limsup _n X_n$が$X_n$がそうである場合に測定可能である理由について多くのことが言える。重要なポイントは、測定可能な写像の合成が測定可能な写像であり、連続写像が測定可能であることを示し、その結果を適用することだ（練習問題2.1）。$\limsup _n X_n$の場合、$\lim _{m \rightarrow \infty} \sup _{n \geq m} X_n$として書き直すことができる。$\sup _{n \geq m} X_n$は減少していることに注意する（$m$が増加するにつれてより小さな集合の上限を取るため）、したがって$\limsup _n X_n=\inf _m \sup _{n \geq m} X_n$で、問題は$\inf _n X_n$と$\sup X_n$の研究に簡素化される。最後に、$\inf _n X_n$の場合、任意の実数$t$に対して$\{\omega: \inf _n X_n \geq t\}$が測定可能であれば十分だ。$\inf _n X_n \geq t$は、全ての$n$に対して$X_n \geq t$である場合にのみ成立する。したがって、$\{\omega: \inf _n X_n \geq t\}=\cap_n\{\omega: X_n \geq t\}$であり、これは可測集合の可算交差であるため測定可能である（この後者は$\left.\left(\cap_i A_i\right)^c=\cup_i A_i^c\right)$の初等的な同一性によって導かれる）。

8. 因数分解補題、補題2.5は、Joseph DoobとEugene Dynkinに帰属される。この補題は、実数の性質を巧みに使用している（なぜか考えてみる）。これが$\sigma$-代数が全ての情報を含むと言ったことが完全に真実ではない別の理由だ。この補題には、より一般的な確率要素に対する拡張がある[Taraldsen, 2018など]。ある意味での主要な要件は、$Y$の値域に関連する$\sigma$-代数が十分に豊かであることだ。

9. Lebesgueの支配的/単調収束定理、Fatouの補題、またはJensenの不等式などの基本的な結果には触れなかった。これらの最後のものは、凸性に関する専用の章（第26章）で説明される。他の結果は、引用したテキストで見つけることができる。これらは、無限数列のランダム変数と、それらの極限がルベーグ積分と交換できる条件に関連している。この本では、そのような数列に関連する問題にほとんど遭遇しないが、それらが必要な数回の場合には我々を許してほしい（その理由は、主に有限時間の結果に焦点を当てるか、漸近的な扱いにおいて極限を取る前に期待値を取るためだ）。

10. 文献に沿って、$P \ll Q$を$P$が$Q$に対して絶対連続であることを示すために使用する。$P$が$Q$に対して絶対連続である場合、$Q$が$P$を支配するとも言う。

11. ラドン・ニコディム微分の有用な結果は連鎖律であり、これは$P \ll Q \ll S$の場合、$\frac{d P}{d Q} \frac{d Q}{d S}=\frac{d P}{d S}$となることを述べている。この結果の証明は、任意の$Q$-可積分$f$に対して$\int f d Q=\int f \frac{d Q}{d S} d S$であるという私たちの以前の観察から導かれる。実際、この連鎖律は、$f=\mathbb{I}_A \frac{d P}{d Q}$（ここで$A \in \mathcal{F}$）を取ることにより、これが実際には$Q$-可積分であり、$\int \mathbb{I}_A \frac{d P}{d Q} d Q=\int \mathbb{I}_A d P$であることに注意して得られる。連鎖律は、密度の計算を既知の密度に関する計算に簡素化するためによく使用される。

12. ラドン・ニコディム微分は、分布（離散空間の場合）と密度（連続空間の場合）の概念を統一する。$\Omega$が離散的（有限または可算）であり、$\rho$が$\left(\Omega, 2^{\Omega}\right)$上のカウント測度である場合（これは$\rho(A)=|A|$によって定義される）、任意の$(\Omega, \mathcal{F})$上の$P$に対して$P \ll \rho$であり、$\frac{d P}{d \rho}(i)=P(\{i\})$であることが簡単にわかる。これは時々$P$の分布関数と呼ばれる。

13. ラドン・ニコディム微分は、条件付き期待値を定義する別の方法を提供する。$(\Omega, \mathcal{F}, \mathbb{P})$上の可積分確率変数$X$と$\mathcal{F}$の部分$\sigma$-代数である$\mathcal{H}$および$\left.\mathbb{P}\right|_{\mathcal{H}}$が$(\Omega, \mathcal{H})$への$\mathbb{P}$の制限である場合、測度$\mu$を$\mu(A)=\left.\int_A X d \mathbb{P}\right|_{\mathcal{H}}$によって$(\Omega, \mathcal{H})$上に定義する。$\left.\mu \ll \mathbb{P}\right|_{\mathcal{H}}$であり、$\mathbb{E}[X \mid \mathcal{H}]=\frac{d_\mu}{\left.\mathrm{dP}\right|_{\mathcal{H}}}$が式(2.9)を満たすことは簡単に確認できる。ラドン・ニコディム定理の証明は単純ではなく、条件付き期待値の存在は関数解析を使用した「初等的」だが抽象的な議論により容易に保証されることに注意する。

14. フビニ-トネリの定理（フビニの定理とも呼ぶ）は、積分の順序を交換できる強力な結果である。この結果は、例えば命題2.8の証明（練習問題2.20）に必要だ。これを述べるために、積測度を導入する必要がある。これは予想通りに機能する：二つの確率空間$\left(\Omega_1, \mathcal{F_1}, \mathbb{P}_1\right)$と$\left(\Omega_2, \mathcal{F}_2, \mathbb{P}_2\right)$が与えられた場合、$\mathbb{P}_1$と$\mathbb{P}_2$の積測度$\mathbb{P}$は、すべての$\left(A_1, A_2\right) \in \mathcal{F}_1 \times \mathcal{F}_2$に対して$\mathbb{P}\left(A_1, A_2\right)=$ $\mathbb{P}_1\left(A_1\right) \mathbb{P}_2\left(A_2\right)$を満たす$\left(\Omega_1 \times \Omega_2, \mathcal{F}_1 \otimes \mathcal{F}_2\right)$上の任意の測度として定義される（$\mathcal{F}_1 \otimes \mathcal{F}_2=\sigma\left(\mathcal{F}_1 \times \mathcal{F}_2\right)$が$\mathcal{F}_1$と$\mathcal{F}_2$の積$\sigma$-代数であることを思い出せ）。定理2.4は、この積測度（しばしば$\mathbb{P}_1 \times \mathbb{P}_2$（または$\mathbb{P}_1 \otimes \mathbb{P}_2$）と表記される）が一意に定義されることを意味する（この積測度が独立性と何の関係があるか考えてみよ）。フビニ-トネリの定理（しばしば単に「フビニ」と呼ばれる）は次のように述べている：二つの確率空間$\left(\Omega_1, \mathcal{F}_1, \mathbb{P}_1\right)$と$\left(\Omega_2, \mathcal{F}_2, \mathbb{P}_2\right)$を考え、積確率空間$(\Omega, \mathcal{F}, \mathbb{P})=\left(\Omega_1 \times \Omega_2, \mathcal{F}_1 \otimes \mathcal{F_2}, \mathbb{P}_1 \times \mathbb{P}_2\right)$上の確率変数$X$を考えると、三つの積分$\int|X(\omega)| \mathrm{d} \mathbb{P}(\omega), \int\left(\int\left|X\left(\omega_1, \omega_2\right)\right| d \mathbb{P}_1\left(\omega_1\right)\right) \mathrm{d} \mathbb{P}_2\left(\omega_2\right)$、$\int\left(\int\left|X\left(\omega_1, \omega_2\right)\right| d \mathbb{P}_2\left(\omega_2\right)\right) d \mathbb{P}_1\left(\omega_1\right)$のいずれかが有限である場合、以下が成立する。

$$
\begin{aligned}
\int X(\omega) \mathrm{d} \mathbb{P}(\omega) & =\int\left(\int X\left(\omega_1, \omega_2\right) \mathrm{d} \mathbb{P}_1\left(\omega_1\right)\right) \mathrm{d} \mathbb{P}_2\left(\omega_2\right) \\
& =

\int\left(\int X\left(\omega_1, \omega_2\right) \mathrm{dP}_2\left(\omega_2\right)\right) \mathrm{d} \mathbb{P}_1\left(\omega_1\right) .
\end{aligned}
$$



#### 参考文献

この章の多くはDavid Pollardの「A user's guide to measure theoretic probability」[Pollard, 2002]からインスピレーションを得ている。この本が好きな理由は、著者が厳密なアプローチを取りながらも、「なぜ」と「どのように」を非常に丁寧に説明しているからだ。この本はかなり早く高度になり、詳細に迷うことなく大局に集中している。他の役立つ参考文献にはBillingsley [2008]の本があり、多くの良い演習問題があり、「基本」のカバー範囲が非常に広い。これらの本はどちらもかなり詳細だ。測度論的確率への優れた短い導入については、Williams [1991]の本を参照してほしい。この本は熱心なスタイルと、マルチンゲールに対する楽しいバイアスがある。また、基本を既によく理解している数学的志向の読者に推奨されるKallenberg [2002]の本も好きだ。著者は冗長性を最小限に抑え、一般性を最大化するように素材を整理するために大きな努力をした。この再編成により、かなりの数のオリジナルの証明が生まれ、本は包括的になった。因子分解補題（補題2.5）はKallenberg [2002]（そこでは補題1.13）の本で述べられている。Kallenbergはこの補題を「機能的表現」補題と呼び、それをJoseph Doobに帰属している。定理2.4はCarathéodoryの拡張定理の系であり、集合の半環上で定義された確率測度には生成された$\sigma$-代数への一意の拡張があると言っている。残りの結果は上記のいずれかの三冊の本で見つけることができる。定理2.14はBogachev [2007]の二巻の本の定理8.9.3として現れる。最後に、古くて技術的でないものとして、Pierre Laplaceによる確率に関する哲学的エッセイを推奨する。これは最近再版された[Laplace, 2012]だ。

#### 問題集

### 2.1 (確率要素の合成)
$\mathcal{F} / \mathcal{G}$-可測な関数 $f$ と $\mathcal{G} / \mathcal{H}$-可測な関数 $g$ が与えられたとき（ここで $\mathcal{F}, \mathcal{G}, \mathcal{H}$ は適切な空間上の $\sigma$-代数）、それらの合成 $g \circ f$（通常の方法で定義される：$(g \circ f)(\omega) = g(f(\omega)), \omega \in \Omega$）が $\mathcal{F} / \mathcal{H}$-可測であることを示せ。

### 2.2
$(\Omega, \mathcal{F})$ 上のランダム変数 $X_1, \ldots, X_n$ が与えられたとき、$(X_1, \ldots, X_n)$ がランダムベクトルであることを証明せよ。

### 2.3 (ランダム変数によって誘導される $\sigma$-代数)
任意の集合 $\mathcal{U}$ と可測空間 $(\mathcal{V}, \Sigma)$ と任意の関数 $X: \mathcal{U} \rightarrow \mathcal{V}$ が与えられたとき、$\Sigma_X = \{X^{-1}(A) : A \in \Sigma\}$ が $\mathcal{U}$ 上の $\sigma$-代数であることを示せ。

### 2.4
可測空間 $(\Omega, \mathcal{F})$ と $A \subseteq \Omega$ および $\mathcal{F}_{\mid A} = \{A \cap B : B \in \mathcal{F}\}$ が与えられたとき、
(a) $(A, \mathcal{F}_{\mid A})$ が可測空間であることを示せ。
(b) $A \in \mathcal{F}$ の場合、$\mathcal{F}_{\mid A} = \{B : B \in \mathcal{F}, B \subseteq A\}$ であることを示せ。

### 2.5
$\mathcal{G} \subseteq 2^{\Omega}$ を空でない集合のコレクションとし、$\sigma(\mathcal{G})$ を $\mathcal{G}$ を含む最小の $\sigma$-代数と定義する。「最小」とは、$\mathcal{F} \subset \mathcal{F}^{\prime}$ の場合に $\mathcal{F} \in 2^{\Omega}$ が $\mathcal{F}^{\prime} \in 2^{\Omega}$ より小さいという意味である。
(a) $\sigma(\mathcal{G})$ が存在し、$\mathcal{G}$ を含むすべての $\sigma$-代数に含まれる集合 $A$ だけを正確に含むことを示せ。
(b) $(\Omega^{\prime}, \mathcal{F})$ を可測空間とし、$X: \Omega^{\prime} \rightarrow \Omega$ が $\mathcal{F} / \mathcal{G}$-可測であるとする。$X$ がまた $\mathcal{F} / \sigma(\mathcal{G})$-可測であることを示せ。（この結果は、ランダム変数がある可測性の性質を満たすかどうかをチェックする仕事を簡素化するためによく使用される。）
(c) $A \in \mathcal{F}$ であり、$\mathcal{F}$ が $\sigma$-代数の場合、$\mathbb{I}\{A\}$ が $\mathcal{F}$-可測であることを証明せよ。

これらの問題をただ翻訳します。

### 2.6 (知識と $\sigma$-代数: 病的な例)
補題2.5の文脈で、$Y=X$ でありながら $Y$ が $\sigma(X)$ 可測でない例を示せ。

**ヒント:** 補題の後で示唆されているように、$\Omega=\mathcal{Y}=\mathcal{X}=\mathbb{R}$、$X(\omega)=Y(\omega)=\omega$、$\mathcal{F}=\mathcal{H}=\mathfrak{B}(\mathbb{R})$ および $\mathcal{G}=\{\emptyset, \mathbb{R}\}$ をトリビアルな $\sigma$-代数として選ぶことで、この状況を整えることができる。

### 2.7
$(\Omega, \mathcal{F}, \mathbb{P})$ を確率空間とし、$\mathbb{P}(B)>0$ であるような $B \in \mathcal{F}$ をとる。$A \mapsto \mathbb{P}(A | B)$ が $(\Omega, \mathcal{F})$ 上の確率測度であることを証明せよ。

### 2.8 (ベイズの法則)
(2.2) を検証せよ。

### 2.9
2つの標準的な、偏りのない六面のサイコロを独立に投げることによって生成される標準的な確率空間 $(\Omega, \mathcal{F}, \mathbb{P})$ を考える。したがって、$\Omega=\{1, \ldots, 6\}^2$、$\mathcal{F}=2^{\Omega}$ および任意の $A \in \mathcal{F}$ に対して $\mathbb{P}(A)=|A| / 6^2$ であるので、$X_i(\omega)=\omega_i$ はサイコロ $i \in\{1,2\}$ の投げ結果を表す。
(a) ' $X_1<2$ ' と ' $X_2$ が偶数' のイベントが互いに独立であることを示せ。
(b) より一般的に、任意の2つのイベント、$A \in \sigma(X_1)$ および $B \in \sigma(X_2)$ が互いに独立であることを示せ。

### 2.10 (偶発的な独立性)
この問題のポイントは独立性をより深く理解することである。以下の問題を解決せよ：
(a) $(\Omega, \mathcal{F}, \mathbb{P})$ を確率空間とし、$\emptyset$ と $\Omega$（これらはイベントである）が他のどのイベントとも独立であることを示せ。これの直感的な意味は何か？
(b) 前述のパートを続けて、$\mathbb{P}(A) \in\{0,1\}$ であるような任意のイベント $A \in \mathcal{F}$ が他のどのイベントとも独立であることを示せ。
(c) その補集合 $A^c=\Omega \backslash A$ に対して独立であるイベント $A \in \mathcal{F}$ について何が結論づけられるか？直感的に意味があるか？
(d) 自身に対して独立であるイベント $A \in \mathcal{F}$ について何

が結論づけられるか？直感的に意味があるか？
(e) 最小限の $\sigma$-代数で偏りのないコインの2回の独立なフリップによって生成される確率空間を考える。$A$ と $B$ が互いに独立であるようなイベントのペア $A, B$ をすべて列挙せよ。
(f) 偏りのない3面のサイコロの独立なロールによって生成される確率空間を考える。個々のサイコロのロールの可能な結果を1、2、3とする。$i$ 番目のサイコロロールの結果に対応するランダム変数を $X_i$ とし（$i \in\{1,2\}$）、イベント $\{X_1 \leq 2\}$ と $\{X_1=X_2\}$ が互いに独立であることを示せ。
(g) 前述の例の確率空間は、有限の結果空間上で確率測度が一様である（プロダクト構造を持っている）ときの例である。任意の $n$-要素の有限結果空間で一様測度を考える。$A$ と $B$ が互いに独立であるためには、$|A|、|B|、|A \cap B|$ の基数が $n|A \cap B|=|A| \cdot |B|$ を満たすことが必要かつ十分であることを示せ。
(h) $n$ が素数である場合、非自明なイベントが独立であることはないことを示せ（イベント $A$ が自明であるとは、$\mathbb{P}(A) \in\{0,1\}$ であることを意味する）。
(i) 二者間独立が必ずしも相互独立を意味しないことを示す例を構築せよ。
(j) $A, B, C$ が互いに独立であるための必要十分条件は、$\mathbb{P}(A \cap B \cap C)=\mathbb{P}(A) \mathbb{P}(B) \mathbb{P}(C)$ であるか？自分の主張を証明せよ。

これらの問題をただ翻訳します。

### 2.11 (独立と確率要素)
以下の問題を解け：
(a) $X$ を定数確率要素（つまり、定義された結果空間上の任意の $\omega \in \Omega$ に対して $X(\omega)=x$）とする。$X$ が他の任意のランダム変数と独立であることを示せ。
(b) $X$ がほとんど確実に定数（つまり、適切な値 $x$ に対して $\mathbb{P}(X=x)=1$）である場合も上記が成り立つことを示せ。
(c) 2つのイベントが独立であるための必要十分条件は、それらの指示ランダム変数が独立であることである（つまり、$A, B$ が独立である場合、そしてその場合に限り、$X(\omega)=\mathbb{I}\{\omega \in A\}$ と $Y(\omega)=\mathbb{I}\{\omega \in B\}$ が互いに独立である）。
(d) イベントのコレクションとそれらの指示ランダム変数に対する二者間および相互独立の結果を前項の結果に一般化せよ。

### 2.12
$X \leq Y$ かつ $X \geq 0$ の場合、$\mathbb{E}[X] \leq \mathbb{E}[Y]$ である。さらに、$X$ が正および負の値を取ることが許され、両方の $X$ と $Y$ が可積分である場合でも、この命題は成立する。

### 2.13
この演習の目的は、ランダム変数 $X$ が可積分である場合、そしてその場合に限り、$|X|$ が可積分であることを示すことである。これは複数のステップに分かれている。最初の問題は $|X|$ の可測性に対処することである。直接計算でもこれを示すことができるが、より一般的な方法を追求する価値があるかもしれない：
(a) 任意の $f: \mathbb{R} \rightarrow \mathbb{R}$ 連続関数はボレル可測である。
(b) 任意のランダム変数 $X$ に対して、$|X|$ もランダム変数であることを結論づけよ。
(c) 任意のランダム変数 $X$ に対して、$X$ が可積分である場合、そしてその場合に限り、$|X|$ が可積分であることを証明せよ（$|X|$ は $X$ がランダム変数である場合に限りランダム変数であるので、この命題は意味を成す）。

**ヒント:** (b)については演習2.1を思い出せ。 (c)については、$|X|$ と $(X)^{+}$ および $(X)^{-}$ の関係を調べよ。

### 2.14 (無限値の積分)
非負のランダム変数に対して積分を一貫して定義し、積分が常に定義される（無限大であっても良い）ことを可能にすることはできる

か？反対論者である場合は例を構築することによって、または積分に対して持つべき要件と一致する定義を証明することによって、自分の意見を擁護せよ。

### 2.15
命題2.6を証明せよ。

命題2.6. 同じ確率空間上の（無限に可能性のある）確率変数の列$\left(X_i\right)_i$について、全ての$i$に対して$\mathbb{E}\left[X_i\right]$が存在し、さらに$X=\sum_i X_i$および$\mathbb{E}\left[\sum_i\left|X_i\right|\right]$も存在すると仮定する。その場合、
$$
\mathbb{E}[X]=\sum_i \mathbb{E}\left[X_i\right] .
$$

**ヒント:** ルベーグの優収束定理/単調収束定理を使用すると便利かもしれない。

### 2.16
$c \in \mathbb{R}$ が定数である場合、$X$ が可積分である限り、$\mathbb{E}[c X]=c \mathbb{E}[X]$ であることを証明せよ。

### 2.17
命題2.7を証明せよ。

命題2.7. もし$X$と$Y$が独立で、$\mathbb{E}[|X|], \mathbb{E}[|Y|]<\infty$のどちらか、または$\mathbb{E}[|X Y|]<\infty$であるならば、$\mathbb{E}[X Y]=\mathbb{E}[X] \mathbb{E}[Y]$である。一般に$\mathbb{E}[X Y] \neq \mathbb{E}[X] \mathbb{E}[Y]$である

**ヒント:** ルベーグ積分の「帰納的」定義から始め、単純関数、次に非負の関数、最後に任意の独立ランダム変数について考えよ。終了するには、ルベーグの優収束定理を使用すると良いかもしれない。

### 2.18
$\mathcal{G}_1 \subset \mathcal{G}_2$ の場合、$\mathbb{E}\left[X \mid \mathcal{G}_1\right]=\mathbb{E}\left[\mathbb{E}\left[X \mid \mathcal{G}_1\right] \mid \mathcal{G}_2\right]$ がほぼ確実に成立することを証明せよ。

### 2.19
一般に、依存するランダム変数に対して、$\mathbb{E}[X Y]=\mathbb{E}[X] \mathbb{E}[Y]$ が成立しないことを示す例を提供せよ。

### 2.20
命題2.8を証明せよ。

命題2.8. もし$X \geq 0$が非負の確率変数であるならば、

$$
\mathbb{E}[X]=\int_0^{\infty} \mathbb{P}(X>x) d x .
$$

**ヒント:** $X(\omega)=\int_{[0, \infty)} \mathbb{I}\{[0, X(\omega)]\}(x) d x$ として議論し、積分を交換せよ。フビニ・トネリの定理を使用して積分の交換を正当化せよ。

### 2.21
定理2.12を証明せよ。

定理2.12. 確率空間$(\Omega, \mathcal{F}, \mathbb{P})$と$\mathcal{F}$の部分$\sigma$代数である$\mathcal{G}, \mathcal{G}_1, \mathcal{G}_2 \subset \mathcal{F}$、および$(\Omega, \mathcal{F}, \mathbb{P})$上の可積分な確率変数$X, Y$が与えられた場合、以下が成り立つ：

1. $X \geq 0$の場合、$\mathbb{E}[X \mid \mathcal{G}] \geq 0$がほぼ確実に成り立つ。
2. $\mathbb{E}[1 \mid \mathcal{G}]=1$がほぼ確実に成り立つ。
3. $\mathbb{E}[X+Y \mid \mathcal{G}]=\mathbb{E}[X \mid \mathcal{G}]+\mathbb{E}[Y \mid \mathcal{G}]$がほぼ確実に成り立つ。
4. $\mathbb{E}[X Y \mid \mathcal{G}]=Y \mathbb{E}[X \mid \mathcal{G}]$がほぼ確実に成り立つ場合、$\mathbb{E}[X Y]$が存在し、かつ$Y$が$\mathcal{G}$-可測である。
5. $\mathcal{G}_1 \subset \mathcal{G}_2$の場合、$\mathbb{E}\left[X \mid \mathcal{G}_1\right]=\mathbb{E}\left[\mathbb{E}\left[X \mid \mathcal{G}_2\right] \mid \mathcal{G}_1\right]$がほぼ確実に成り立つ。
6. $\sigma(X)$が$\mathcal{G}_1$に対して$\mathcal{G}_2$と与えられた条件下で独立である場合、$\mathbb{E}\left[X \mid \sigma\left(\mathcal{G}_1 \cup \mathcal{G}_2\right)\right]=\mathbb{E}\left[X \mid \mathcal{G}_1\right]$がほぼ確実に成り立つ。
7. $\mathcal{G}=\{\emptyset, \Omega\}$が自明な$\sigma$-代数である場合、$\mathbb{E}[X \mid \mathcal{G}]=\mathbb{E}[X]$がほぼ確実に成り立つ。
8. 