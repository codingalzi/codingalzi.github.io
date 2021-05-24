<script>
    MathJax.Hub.Config({
        "HTML-CSS": {
            /*preferredFont: "TeX",*/
            /*availableFonts: ["TeX", "STIX"],*/
            styles: {
                scale: 100,
                ".MathJax_Display": {
                    "font-size": "100%",
                }
            }
        }
    });
</script>
    
<!-- Load mathjax -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-MML-AM_CHTML-full,Safe"> </script>
<!-- MathJax configuration -->
<script type="text/x-mathjax-config">
init_mathjax = function() {
    if (window.MathJax) {
    // MathJax loaded
        MathJax.Hub.Config({
            TeX: {
                equationNumbers: {
                autoNumber: "AMS",
                useLabelIds: true
                }
            },
            tex2jax: {
                inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                processEscapes: true,
                processEnvironments: true
            },
            displayAlign: 'center',
            CommonHTML: {
                linebreaks: { 
                automatic: true 
                }
            },
            "HTML-CSS": {
                linebreaks: { 
                automatic: true 
                }
            }
        });
    
        MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
    }
}
init_mathjax();
</script>
<!-- End of mathjax configuration -->

# Github Pages의 Markdown과 Latex 수식

깃허브 페이지에서 마크다운을 이용하여 수식(mathmatical formulas)이 포함된
블로그을 작성하는 방법 두 가지를 설명한다.
기본 아이디어는 `MathJax` 서버를 이용하여 수식이 나올 때마다 동일한 수식을
표현하는 HTML 코드로 대체해서 보여주는 것이다. 

이를 위해 [mathjax_support.txt](./scripts/mathjax_support.txt) 파일에 담겨 
있는 자바스크립트 코드를 사용한다. 
참고로, 언급된 자바스크립트 코드는 주피터 노트북을 html 파일로 변환할 때 head 부분에 자동으로 
삽입되는 `MathJax` 관련 코드를 추출한 것이다.

## 자바스크립트  코드 삽입 방법

크게 두 가지로 나눈다. 하나는 수식이 포함된 모든 마크다운 파일에 언급한 자바스크립트
코드를 삽입하는 것이고, 다른 하나는 모든 파일에 일괄적으로 적용하는 것이다.

* __방법 1__

    가장 단순하며 가장 무식한 방법으로,
    매 마크다운 파일의 최상단에 위 자바스크립트 코드를 삽입한다.

* __방법 2__

    jekyll 테마를 사용하는 경우엔 
    [Jekyll Github 블로그에 MathJax로 수학식 표시하기](https://mkkim85.github.io/blog-apply-mathjax-to-jekyll-and-github-pages/)를
    참조한다.

## 수식 예제

다양한 수식 예제를 latex으로 표현하는 예제들을 살펴본다.

### 예제 1

```
$\mathbf{x}$를 원시 데이터(raw data) 벡터라고 하고 $\mathbf{z}$를 표준화된 벡터이라 할 때 다음 관계가 성립한다.

$$
\mathbf{z} = \frac{\mathbf{x}-\mu}{\sigma} \tag{*}
$$
```

$\mathbf{x}$를 원시 데이터(raw data) 벡터라고 하고 $\mathbf{z}$를 표준화된 벡터이라 할 때 다음 관계가 성립한다.

$$
\mathbf{z} = \frac{\mathbf{x}-\mu}{\sigma} \tag{*}
$$

### 예제 2

```
결론적으로, 원시 데이터의 각 특성 $x_i$에 대한 파라미터 $w'_i$와 편항 $b'$은 아래와 같다.

$$
\begin{align*}
w'_i & = w_i/\sigma \\[1ex]
b' & = h (-\mu / \sigma)
\end{align*}
$$

$$
\begin{align}
w''_i & = w'_i/\sigma \\[1ex]
b'' & = h' (-\mu / \sigma)
\end{align}
$$
```

결론적으로, 원시 데이터의 각 특성 $x_i$에 대한 파라미터 $w'_i$와 편항 $b'$은 아래와 같다.

$$
\begin{align*}
w'_i & = w_i/\sigma \\[1ex]
b' & = h (-\mu / \sigma)
\end{align*}
$$

$$
\begin{align}
w''_i & = w'_i/\sigma \\[1ex]
b'' & = h' (-\mu / \sigma)
\end{align}
$$

### 예제 3

```
$$
{\displaystyle \phi_{\gamma}(\mathbf{x}, \boldsymbol{\ell})} = {\displaystyle \exp({\displaystyle -\gamma \left\| \mathbf{x} - \boldsymbol{\ell} \right\|^2})}
$$
```

$$
{\displaystyle \phi_{\gamma}(\mathbf{x}, \boldsymbol{\ell})} = {\displaystyle \exp({\displaystyle -\gamma \left\| \mathbf{x} - \boldsymbol{\ell} \right\|^2})}
$$

### 예제 4

```
\begin{equation}
\frac{1}{\text{특성 수} \cdot \text{특성의 분산}}
\end{equation}
```

\begin{equation}
\frac{1}{\text{특성 수} \cdot \text{특성의 분산}}
\end{equation}

### 예제 5

```
비용함수는 책 227쪽, 식 5-13에서 소개한 아래 함수이다.

\begin{equation}
J(\mathbf{w}, b) = \dfrac{1}{2} \mathbf{w}^T \mathbf{w} \,+\, C {\displaystyle \sum_{i=1}^{m}\max\left(0, 1 - t^{(i)} (\mathbf{w}^T \mathbf{x}^{(i)} + b) \right)}
\end{equation}
```

비용함수는 책 227쪽, 식 5-13에서 소개한 아래 함수이다.

\begin{equation}
J(\mathbf{w}, b) = \dfrac{1}{2} \mathbf{w}^T \mathbf{w} \,+\, C {\displaystyle \sum_{i=1}^{m}\max\left(0, 1 - t^{(i)} (\mathbf{w}^T \mathbf{x}^{(i)} + b) \right)}
\end{equation}
