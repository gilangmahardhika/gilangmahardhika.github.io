---
layout: post
title:  "Metaprogramming : class_eval dan instance_eval"
date:   2013-06-15 17:03:00
categories: metaprogramming
---

`class_eval` dan `instance_eval` pada ruby memungkinkan anda untuk mengevaluasi kode atau objek tertentu. Dengan menggunakan `class_eval` kita dapat membuat sebuah instance method baru diluar kelas tersebut.

contohnya :
{% highlight ruby %}
class Car
end

Car.class_eval do
	def steer(direction)
		"Steering #{direction}"
	end
end

car = Car.new
car.steer("left")

# Hasilnya
"Steering left"
{% endhighlight %}

Dari kode tersebut bisa disimpulkan bahwa kita bisa membuat sebuah `instance method` baru dari `class Car` diluar dari kelas tersebut.

Sedangkan `instance_eval` memungkinkan kita untuk membuat `class method` diluar kelas tersebut. Sama halnya dengan kode diatas, misalkan kita akan membuat class method dari `class Car`, berikut contohnya :

{% highlight ruby %}
class Car
end

Car.instance_eval do
	def print_name(name)
		"Car name is #{name}"
	end
end

Car.print_name("Rubicon")

# Hasilnya
"Car name is Rubicon"
{% endhighlight %}