配列のスライド和
=

Problem Statement
-

数値配列の隣り合う要素同士の和を全て足したものを、配列の「スライド和」と呼ぶことにする。
たとえば、配列 [1, 2, 3, 4] のスライド和は、(1+2) + (2+3) + (3+4) = 15 となる。

N個の異なる数値からなる配列が与えられるので、そのスライド和がK以上になるように要素を並び替えたい。
そのような順列は何通りあるか出力せよ。

答えはとても大きな数値になることがあるので、答えを 10009 で割った余りを出力せよ。

Note
-
答えを計算する際、余りを取る操作は積と和に対して自由に行えることに注意せよ。
たとえば、N!(Nの階乗)を 10009 で割った余りを求める場合、以下二つは数学的に結果が同じになる。

* 全部の積をとってから 10009 の余りを求める
* 積ごとに 10009 の余りを求める

プログラムでは数値のオーバーフローを防ぐため、積ごとに余りを計算しよう。すなわち、

    int fact = 1;
    for (int i = 1 ; i <= N ; i++) {
        fact = (fact * i) % 10009;
    }

とすることで求められる。大きな数同士の足し算についても同様である。

Input
-

入力は複数のデータセットで構成され、1つのデータセットは以下の形式で表される。

> N K<br>
> a<sub>1</sub> a<sub>2</sub> ... a<sub>N</sub>

ここでNは配列の要素数、Kはスライド和の基準、a<sub>i</sub>は配列の各要素である。

入力の終わりは、データセットの代わりに2つの0が入力される。

Constraints
-

入力は、以下の条件をすべて満たす。

* 1 <= N <= 50
* 1 <= K <= 5000
* 1 <= a<sub>i</sub> <= 100
* 1 <= (i,j) <= N なる全てのi,jに対して、 i != j ならば a<sub>i</sub> != a<sub>j</sub>

Sample Input 1
-

    3 8
    1 2 3
    0 0

Sample Output 1
-

    4
答えは、[1,2,3], [1,3,2], [2,3,1], [3,2,1]の4通りである。

Sample Input 2
-

    5 15
    1 2 3 4 5
    3 18
    1 2 9
    0 0
    
Sample Output 2
--

    120
    2