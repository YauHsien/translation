# 土地公有政策

### 非正式的列表
- ( N., 土 )
- ( N., 地 )
- ( N., 公 )
- ( Adj., 公 )
- ( Adj., 有 )
- ( V., 有 )
- ( N. 政 )
- ( N. 策 )

#### 現有詞組
- ( N.P., 土地 )
- ( N.P., 土地公 )
- ( N.P., 土地公有政策 )
- ( N.P., 地公 )
- ( Adj., 公有 )
- ( N.P., 公有土地 )
- ( N.P., 政策 )

#### 想象的剖析器
A = string("土地")
B = string("公")
C = string("公有")
D = string("有")
E = string("政策")
Parser = alt( using(then( using(then( using(then(A,B), fun appendNP/1), % 讀到「土地公」
                                      D ),
                                fun appendSV/1), % 讀到「土地公/np, 有/v」
                          E ),
                    fun appendSVO/1), % 讀到「土地公/np/s, 有/v, 政策/np/o」
              using(then( using(then(A,C), fun appendNP/1), % 讀到「土地/np, 公有/adj」
                          E ),
                    fun appendNP/1) % 讀到「土地/np, 公有/adj, 政策/np」
            )
