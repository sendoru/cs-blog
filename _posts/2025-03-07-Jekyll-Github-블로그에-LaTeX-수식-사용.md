---
Title: 2025-03-07-Jekyll-Github-블로그에-LaTeX-수식-사용
categories:
  - Others
tags:
  - Web
  - Blog
  - Jekyll
toc: true
use_math: true
---

이 글에서는 [Mathjax](https://github.com/mathjax/MathJax)를 이용해 Jekyll 블로그에 LaTex 문법을 이용한 수식을 넣는 법을 알아본다.

## 마크다운 엔진 변경

`_config.yml`에서 `# Conversion`으로 시작되는 부분을 다음과 같이 바꾼다. [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) 등 일부 템플릿에서는 기본으로 적용되어 있다.

```yml
# Conversion
markdown: kramdown
highlighter: rouge
lsi: false
excerpt_separator: "\n\n"
incremental: false
```

## 모든 문서에 적용할 경우

`_includes/head.html` 맨 끝에 아래 내용을 붙여넣으면 끝이다.

```html
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
      TeX: {
        equationNumbers: {
          autoNumber: "AMS"
        }
      },
      tex2jax: {
      inlineMath: [ ['$', '$'] ],
      displayMath: [ ['$$', '$$'], ['\\[', '\\]'] ],
      processEscapes: true,
    }
  });
</script>
<script
  type="text/javascript"
  async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"
></script>
```

## 특정 문서에만 적용할 경우

### `mathjax_support.html` 생성

`_include` 디렉토리에 `mathjax_support.html`를 생성하고 위 섹션에 있는 코드를 그대로 입력한다.

### `_layouts/default.html` 파일 수정

`<head>`에 아래 코드를 추가한다.

{% raw %}
```
{% if page.use_math %}
  {% include mathjax_support.html %}
{% endif %}
```
{% endraw %}

### YAML front-matter 설정

LaTeX 문법을 사용할 포스트의 front-matter에 `use_math: true`를 적용

```yaml
---
Title: 2025-03-07-Jekyll-Github-블로그에-LaTeX-수식-사용
categories:
  - Others
tags:
  - Web
  - Blog
  - Jekyll
toc: true
use_math: true
---
```

## MathJax 수식 예시

### 인라인 수식

```latex
오일러 공식: $e^{ix} = \cos(x) + i\sin(x)$
```

오일러 공식: $e^{ix} = \cos(x) + i\sin(x)$

### 블록 수식

```latex
$$
K(a,b) = \int \mathcal{D}x(t) \exp(2\pi i S[x]/\hbar)
$$
```

$$
K(a,b) = \int \mathcal{D}x(t) \exp(2\pi i S[x]/\hbar)
$$

---

## References
- [Jekyll Github 블로그에 MathJax로 수학식 표시하기](https://mkkim85.github.io/blog-apply-mathjax-to-jekyll-and-github-pages/)
- [MathJax, Jekyll and github pages](http://benlansdell.github.io/computing/mathjax/)