---
layout: post
title:  "Metaprogramming : define_method"
date:   2013-06-15 17:03:00
categories: metaprogramming
---

Dengan menggunekan `define_method` memungkinkan untuk membuat suatu method baru secara dinamis.

{% highlight ruby %}
class Foo
 define_method("bar") do
  "bar"
 end
end

Foo.new.bar #return "bar"
{% endhighlight %}

`define_method` juga memungkinkan kita membuat suatu method baru dengan argumen

{% highlight ruby %}
class Foo
 define_method("bar") do |argument|
  "bar and #{argument}"
 end
end

Foo.new.bar("foo") #return "bar and foo"
{% endhighlight %}

Juga memungkinkan membuat method yang lebih dinamis dengan array
{% highlight ruby %}
class Foo
 ["one", "two", "three"].each do |number|
  define_method("print_#{number}") do |name|
   "This is number #{number}, #{name}"
  end
 end
end

Foo.new.print_one("John") #return "This is number one, John"
Foo.new.print_two("John") #return "This is number two, John"
Foo.new.print_three("John") #return "This is number three, John"
{% endhighlight %}