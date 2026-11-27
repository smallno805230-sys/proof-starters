# 看到題目，怎麼選機率分配？

這份 Wiki 給學過基本機率、但常常不知道該選哪個分配的同學。
每個條目先說題目在數什麼，再列出適用條件、公式和例題。

## S1 二項分配（Binomial Distribution）

來源：[Penn State STAT 414 — The Binomial Distribution](https://online.stat.psu.edu/stat414/Lesson10)

### 什麼時候用？

1. 事先固定試驗次數 n。
2. 每次只有成功和失敗兩種結果。
3. 各次試驗互相獨立。
4. 每次成功的機率都是 p。

令 X 為 n 次試驗中的成功次數。X 可以是 0 到 n 的整數。

### 公式

$$
P(X=k)=\binom{n}{k}p^k(1-p)^{n-k}
$$

其中 $\binom{n}{k}$ 代表從 n 次試驗中選出哪 k 次成功。

### 自編例題

假設每次投籃互相獨立，命中率固定為 0.6。投 10 球，恰好進 3 球的機率是多少？

因為一開始就決定投 10 球，而且 X 數的是命中的球數，所以用二項分配。

$$
P(X=3)=\binom{10}{3}(0.6)^3(0.4)^7\approx 0.0425
$$

## S2 幾何分配（Geometric Distribution）

來源：[OpenStax《Introductory Statistics 2e》4.4 Geometric Distribution](https://openstax.org/books/introductory-statistics-2e/pages/4-4-geometric-distribution)

### 什麼時候用？

每次試驗只有成功和失敗兩種結果，各次互相獨立，成功機率固定為 p。一直做，直到第一次成功就停下來。

令 X 為第一次成功時的總試驗次數，包含最後成功的那一次，所以 X 可以是 1、2、3、……。

### 公式

$$
P(X=k)=(1-p)^{k-1}p
$$

第 k 次才首次成功，表示前 k−1 次都失敗，第 k 次成功。

### 自編例題

假設每球獨立，命中率固定為 0.6。第 4 球才第一次命中的機率是多少？

$$
P(X=4)=(0.4)^3(0.6)=0.0384
$$

如果題目改問「第一次命中前失敗幾次」，可以令 Y = X − 1。這題投了 4 球，命中前失敗了 3 球。

## S3 負二項分配（Negative Binomial Distribution）

來源：[Penn State STAT 414 第 11 課，11.4 Negative Binomial Distributions](https://online.stat.psu.edu/stat414/Lesson11#negative-binomial-distributions)

### 什麼時候用？

每次試驗只有成功和失敗兩種結果，各次互相獨立，成功機率固定為 p。一直做，直到第 r 次成功就停下來。

令 X 為第 r 次成功時的總試驗次數。至少要做 r 次才可能成功 r 次，所以 X 可以是 r、r+1、r+2、……。

### 公式

$$
P(X=k)=\binom{k-1}{r-1}p^r(1-p)^{k-r}
$$

第 k 次一定要成功，前 k−1 次則剛好成功 r−1 次。因此，只需要從前 k−1 次中選出 r−1 次成功的位置。

### 自編例題

假設每球獨立，命中率固定為 0.6。一直投到第 3 球命中，恰好投了 10 球的機率是多少？

$$
P(X=10)=\binom{9}{2}(0.6)^3(0.4)^7\approx 0.0127
$$

如果令 Y 為第 r 次成功前的失敗次數，因為總試驗次數等於成功次數加失敗次數，所以 Y = X − r。這題投了 10 球、命中 3 球，因此失敗 7 球。

當 r = 1 時，負二項分配就變成幾何分配。
