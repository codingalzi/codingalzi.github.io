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

## 자바 코드 삽입 방법

크게 두 가지로 나눈다. 하나는 수식이 포함된 모든 마크다운 파일에 언급한 자바스크립트
코드를 삽입하는 것이고, 다른 하나는 모든 파일에 일괄적으로 적용하는 것이다.

* __방법 1__

    가장 단순하며 가장 무식한 방법으로,
    매 마크다운 파일의 최상단에 위 자바스크립트 코드를 삽입한다.

* __방법 2__

    jekyll 등 특별한 테마를 사용할 경우에 권장되는 방법으로,
    먼저 `head.html` 파일의 `head` 태그 안에 아래 html 코드를 삽입한다. 

    <div class="language-html highlighter-rouge"><div class="highlight"><pre class="highlight"><code>{% if page.use_math %}
    {% include mathjax_support.html %}
    {% endif %}
    </code></pre></div></div>

    단, 앞서 언급된 자바스크립트 코드가 저장된 `mathjax_support.html` 파일이
    `head.html` 파일과 동일한 폴더에 위치해야 한다. [mathjax_support.txt](./scripts/mathjax_support.txt) 파일을 다운로드한 후에 확장자를 `.html`로 변경해서 적절한
    디렉토리에 저장하면 된다.


## 수식 예제

다양한 수식 예제를 latex으로 표현하는 예제들을 살펴본다.

---

### 예제 1

$\mathbf{x}$를 원시 데이터(raw data) 벡터라고 하고 $\mathbf{z}$를 표준화된 벡터이라 할 때 다음 관계가 성립한다.

$$
\mathbf{z} = \frac{\mathbf{x}-\mu}{\sigma} \tag{*}
$$

### 예제 2


