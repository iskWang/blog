---
layout: post
title:  "關於 rails n+1 問題"
date:   2016-03-10 16:42:40 +0800
---

## 關於

因為連續兩次面試都被問到這問題( Orz )，想用這機會整理

當前端需要一整串資料
{% highlight ruby %}
  @books = Book.limit(10)
{% endhighlight %}
{% highlight erb %}
  <% @books.each | book | %>
    <p> <%= book.name  %></p>
    <p> <%= book.author %></p>
    <p> <%= book.company.name %></p>
  <% end %>
{% endhighlight %}

```Book.limit(10)``` 第一次會先撈前 10 筆 ```book``` 紀錄，但因為 ```book.company.name``` 會造成需要多額外十次 ```company``` 查詢

## 解決

因此用 ```includes```，確保資料表關聯
{% highlight ruby %}
 @books = Book.includes(:company).limit(10)
{% endhighlight %}
{% highlight sql %}
 SELECT * FROM books LIMIT 10
 SELECT companies.* FROM companies WHERE (companies.book_id IN (1,2,3,4,5,6,7,8,9,10))
{% endhighlight %}

## 參考

[RailsGuides- Active Record 查詢](http://rails.ruby.tw/active_record_querying.html)

[Rails 3 種做到 eager loading 方法](http://blog.hothero.org/posts/2015/07/17/rails-3-do-eager-loading-method)

[Rails 使用 include 和 join 避免 N+1 query](http://motion-express.com/blog/20141028-rails-include-join-avoid-n-1-query)
