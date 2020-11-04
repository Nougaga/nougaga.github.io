---
layout: post
title:  "Welcome to Jekyll!"
date:   2020-11-04 22:27:32 +0900
categories: jekyll update
---
#### 강조, 코드 조각
\`_posts\` → `_posts`

<br>


#### 포스트 저장
\`YYYY-MM-DD-title.md\` → url/폴더경로 또는 카테고리/YYYY/MM/DD/title

<br>


#### 코드 덩어리는 아래에서 {와 % 사이의 공백을 제거
\{ % highlight ruby % \}<br>
def print_hi(name)<br>
  puts "Hi, #{name}"<br>
end<br>
print_hi('Tom')<br>
#=> prints 'Hi, Tom' to STDOUT.<br>
\{ % endhighlight % \}<br>
↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓<br>
{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

#### 링크
\[라벨\]\(URL\) 또는<br>
\[라벨\]로만 쓰다가 어딘가에<br>
\[라벨\]:\(URL\)를 명시

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
