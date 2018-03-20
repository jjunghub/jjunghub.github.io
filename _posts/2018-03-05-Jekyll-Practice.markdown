---
layout: post
title:  "Jekyll이랑 친해지기"
date:   2018-03-05 15:41 +0900
categories: jekyll update
---
> Jekyll 의 핵심 역할은 텍스트 변환 엔진입니다. 시스템 배경 컨셉은 이렇습니다: Markdown 이나 Textile 또는 일반 HTML 등 자신이 즐겨 사용하는 마크업 언어로 문서를 작성하면, Jekyll 은 이 문서들을 다양한 레이아웃으로 포장합니다. 당신은 사이트 URL 구성 방식이나 데이터가 레이아웃에 배치되는 방식 등, 변환 과정에 포함된 다양한 동작들을 원하는대로 조정할 수 있습니다. 단지 텍스트 파일을 수정하는 것만으로 이 모든 일들이 가능하며, 그 결과로 정적 웹 사이트가 만들어집니다.  
>Jekyll website

Jekyll에서 제공되는 유용한 문서, [한국어](https://jekyllrb-ko.github.io/docs/usage/) [영어](https://jekyllrb.com/docs/usage/)

### 기본 사용법
`_config.yml`에 build 시 참고할 환경변수 들을 설정 해놓으면 편함. 자동 재생성(`--watch`) 중에 새로 읽어 들이지 않으니 주의하자.

{% highlight ruby %}
$ jekyll serve
# => 개발용 서버가 http://localhost:4000/ 에서 구동
# 자동-재생성이 자동으로 활성화됨. 비활성화 하려면 '--no-watch' 를 뒤에 붙임.

$ jekyll serve --detach
# => 백그라운드에서 돌아감. 종료하려면
# 'ps aux | grep jekyll' 로 PID 검색 후
# 'kill -9 [PID]'
{% endhighlight %}
{% highlight ruby %}
$ jekyll build
{% endhighlight %}

### 구조

| `_posts` | ***한마디로 말하면, 당신의 컨텐츠*** 다. 중요한 것은 파일들의 명명규칙인데, **반드시 다음 형식을 따라야 한다: `YEAR-MONTH-DAY-title.MARKUP.`** 고유주소는 포스트 별로 각각 정의할 수 있지만, 날짜와 마크업 언어 종류는 오로지 파일명에 의해 결정된다.  예를 들어, 이 포스트의 파일명은 `2018-03-05-Jekyll-Practice.markdown` 이다! |
| `_data` | ***사이트에 사용할 데이터*** 를 적절한 포맷으로 정리하여 보관하는 디렉토리. Jekyll 엔진은 이 디렉토리에 있는 (확장자와 포맷이 `.yml` 또는 `.yaml`, `.json`, `.csv` 인) 모든 YAML 파일을 자동으로 읽어들여 `site.data` 로 사용할 수 있도록 만든다. 만약 이 디렉토리에 `members.yml` 라는 파일이 있다면, `site.data.members` 라고 입력하여 그 컨텐츠를 사용할 수 있다. |


<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
