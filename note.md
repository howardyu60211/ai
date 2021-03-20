先備知識
===

## 微分

- ### 意義

    函數經過微分後就變為導數。
    
    ![wiki](https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/Derivative_-_geometric_meaning.svg/300px-Derivative_-_geometric_meaning.svg.png)

    $$
    割線斜率 = { \frac {\Delta y}{\Delta x} } = { \frac {f(x+\Delta x)-f(x)}{\Delta x} }
    $$
    $$
    切線斜率 = {\lim_{\Delta x \to 0}{ \frac {f(x+\Delta x)-f(x)}{\Delta x} }}= \lim_{ x \to {x_0}}{ \frac {f(x)-f(x_0)}{x-{x_0}} }
    $$
    
- ### 表示法
    

    |        | 微分一次 | 微分兩次 | 微分三次 | 微分四次 |
    | ------ | ------- | ------- | ------ | ------ |
    | 牛頓    | $$f'(x)$$ | $$f''(x)$$ | $$f'''(x)$$ | $$f^{(4)}(x)$$ |
    |萊布尼茲| $$\frac {df(x)}{dx} $$ | $$\frac {d^2f(x)}{dx^2} $$ | $$\frac {d^3f(x)}{dx^3} $$ | $$\frac {df(x)^4}{dx^4} $$ |

- ### 公式
    1. #### $f(x)=k ,{d \over dx}f(x) = 0, k \in \mathbb R$
        > 證明 :
            任一水平線上兩點斜率為零

    ---

    2. #### $f(x)=x^k, {d \over dx}f(x) = kx^{k-1}, k \in \mathbb R$
        > 證明 :
            p.f.$\exists n \in \mathbb R, f(x) = x^n, f'(x) = nx^{n-1}$
            $$f'(x) = { \lim_ { \Delta x \to 0 } { \frac {f (x + \Delta x) - f(x)}{\Delta x} }}$$
            $$= { \lim_ { \Delta x \to 0 } { \frac{(x + \Delta x)^n - x^n}{\Delta x} }}$$
            $$= { \lim_ { \Delta x \to 0 } { \frac {\sum_{i=0}^n C_i^n x^{n-i} \Delta x^i - x^n}{\Delta x} }}$$
            $$= { \lim_ { \Delta x \to 0 } { \frac {\sum_{i=1}^n C_i^n x^{n-i} \Delta x^i}{\Delta x} }}$$
            $$= { \lim_ { \Delta x \to 0 } {\sum_{i=0}^n C_i^n x^{n-i-1 } \Delta x^i} }$$
            $$= x^{n-1} + \lim_ { \Delta x \to 0 } \Delta x { ( {\sum_{i=1}^n C_i^n x^{n-i-1} \Delta x^i } ) }$$
            $$=  x^{n-1} $$
    3. #### ${df(x)g(x) \over dx} = f(x)g'(x) + g(x)f'(x)$
        > 證明 :
            $$
            {df(x)g(x) \over dx} = \lim_ { \Delta x \to 0 } { \frac {f (x + \Delta x)g(x+\Delta x) - f(x)g(x)}{\Delta x} }
            $$
            $$
            ={ \lim_ { \Delta x \to 0 } { \frac {f (x + \Delta x)g(x+\Delta x) - f(x+\Delta x)g(x)}{\Delta x} + { \lim_ { \Delta x \to 0 } { \frac  {f(x+ \Delta x)g(x) - f(x)g(x)}{\Delta x} }}}}
            $$
            $$
            =\lim_ { \Delta x \to 0 } {f(x+\Delta x) \frac {g(x+\Delta x) - g(x)}{\Delta x} + { \lim_ { \Delta x \to 0 } { g(x) \frac  {f(x+ \Delta x) - f(x)}{\Delta x} }}}
            $$
            $$ = f(x)g'(x) + g(x)f'(x) $$
            
機器學習
===
- ## 方式
    1. 監督式學習
        有標籤（答案）像選擇題  找資料與標籤關係
    2. 非監督式學習
        無標籤  像申論題  找資料之間結構
    3. 增強式學習
        有環境回饋  找最佳動作
- ## 流程
    ```mermaid
        flowchart TD
            A[假設集合] -->|挑選假設| B[學習演算法]
            
            subgraph 比較
                C(function g) <==> D(function f)
            end
            B -->|預測模型| D
            比較 --> E[(訓練資料)]
            E --> B
    ```
- ## 特徵轉換 (*feature transform*): $\phi$
*     把非線性轉為線性

- ## 過適 (*overfitting*)
    ![image alt](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR_ZLkva1yaLO7v-JANBVMV7p31gfw-WXsuOw&usqp=CAU)
    |                | overfitting      | optimal |
    | -------------- | ---------------- | ------- |
    | 訓練資料相似度 | 極高(100%)       | 普通    |
    | 真實模型相似度 | 極低             | 普通    |
    | 敘述           | 過度相信訓練資料 |         |
    | 輸出           | 不穩定           | 穩定    |
    * 模型易受訓練資料影響?
    > 解決方法: 簡單模型優先
    * 資料噪音、變異大?
    > 解決方法: 清除預處理資料
    * 如何避免學習到過於複雜的假設?
    > 解決方法: regularization
        限縮假設空間能挑選之範圍。
        $\Rightarrow ||x|| < y$