GO言語の基礎まとめ
-----------------

> 変数の名前の後ろに>typeが来る。
> 
> swap関数は二つのSTRINGを返す.
> 
> 引数がないRETURN分は与えられた値を返すこれを”NAKED　RETURN”という。
　しかし、可読性を悪くする恐れがあるので短い関数にだけ使わなければならない。
> 
> VAR分はj変数に関する目録を宣言する。－＞最後はTYPE
>
> #基本TYPE
>　bool, string, int, int8, int16, int32, int64
>　unit, unit8, unit16, unit32, unit64, uintptr

> byte // unit8 別称
> rune // ユニコードではCODE　POINTを意味する。
> float32, float64
> complex64, complex128

> #Zero values
> 明示的な初期値なしで宣言された変数はそれのZERO　VALUEが与えられる。
> 数字　TYPE　－＞　０
> BOOLEAN　TYPE ->　FALSE
> STRING　””（空文字列）
> 
