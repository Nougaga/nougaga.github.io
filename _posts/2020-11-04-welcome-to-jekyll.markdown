---
layout: post
title:  "How to Make GitHub Pages with MARKDOWN"
date:   2020-11-04 22:27:32 +0900
categories: howto
---
#### 강조, 코드 조각
\`_posts\` → `_posts`

<br>


#### 포스트 저장
\`YYYY-MM-DD-title.md\` → url/폴더경로 또는 카테고리/YYYY/MM/DD/title

<br>

#### 코드 덩어리는 아래에서 {와 % 사이의 공백을 제거
```
{ % highlight ruby % }
def print_hi(name)
  puts "Hi, #{name}"
end<br>
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{ % endhighlight % }
```
↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓<br>
{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

#### 링크
1. \[라벨\]\(URL\) 또는<br>
2. \[라벨\]로만 쓰다가 어딘가에<br>
\[라벨\]:\(URL\)의 형태로 명시<br>

[jekyll-docs](https://jekyllrb.com/docs/home)<br>
[jekyll-gh]<br>
[jekyll-talk]

[jekyll-gh]:(https://github.com/jekyll/jekyll)
[jekyll-talk]:(https://talk.jekyllrb.com/)
