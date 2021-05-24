# Github Pages의 Markdown과 Latex 수식(formula) 표현

깃허브 페이지에서 마크다운을 이용하여 수식(mathmatical formulas)이 포함된
블로그을 작성하는 방법 두 가지를 설명한다.
기본 아이디어는 `MathJax` 서버를 이용하여 수식이 나올 때마다 동일한 수식을
표현하는 HTML 코드로 대체해서 보여주는 것이다. 

사용하는 자바 코드는 다음과 같다.

```js
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
```

__참고:__ 위 자바코드는 주피터 노트북을 html 파일로 변환할 때 head 부분에 자동으로 
삽입되는 `MathJax` 관련 코드를 추출한 것이다.

* __방법 1__

    가장 단순하며 가장 무식한 방법으로,
    매 마크다운 파일의 최상단에 위 자바스크립트 코드를 삽입한다.


* __방법 2__

    jekyll 등 특별한 테마를 사용할 경우에 권장되는 방법으로,
    먼저 `head.html` 파일의 `head` 태그 안에 아래 html 코드를 삽입한다. 

    ```html
    {% if page.use_math %}
        {% include mathjax_support.html %}
    {% endif %}
    ```

    단, 앞서 언급된 자바스크립트 코드가 저장된 `mathjax_support.html` 파일이
    `head.html` 파일과 동일한 폴더에 위치해야 한다. 


## 수식 예제

다양한 수식 예제를 latex으로 표현하는 예제들을 살펴본다.


