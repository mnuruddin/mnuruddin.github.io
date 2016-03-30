---
layout: post
title:  "The Basics (part 1)"
date:   2016-03-29 14:40:16
description: Yuk, kenalan dulu sama Swift! Pembahasan mengenai simple values dan control flow
---

{% highlight swift %}

/// Let's start Swift basics part 1 
let theBasics = Hello.Swift(title: "The Basics", part: 1)
theBasics.start()

{% endhighlight %}

Traditional way setiap kali kita belajar bahasa pemrograman baru kan selalu diawali dengan print "Hello, World!". Nah di Swift (latest version), this can be done in a single line:  

{% highlight swift %}

print("Hello, World!")

{% endhighlight %}

Ane mulai dari **The Basics** dulu, sehingga kalian bisa start writing code in Swift.

##### Note
<blockquote>
	Kalian bisa sekalian membuka playground di Xcode untuk coba secara live dari apa yang ane jabarin disini. Sehingga kalian bisa melakukan improvisasi. Caranya, File > New > Playground (⌥⇧⌘N)<br/><br/>Playground itu sebuah interactive Swift coding environment yang langsung menampilkan result dari code yang kalian bikin.
</blockquote>

<br/>

<h3>Simple Values</h3>
<br/>
Gunakan *let* untuk membuat sebuah constant dan *var* untuk variable. Swift secara otomatis akan menentukan type dari sebuah constant atau variable sesuai dengan value yang diberikan (implicit).

{% highlight swift %}

let myConstant = "Hello, World!"

var myVariable = "Hello, World!"
myVariable = "Hello, Swift!"

{% endhighlight %}

Kita juga bisa membuat constant atau variable dengan type yang sudah jelas ditentukan (explicit), maka bisa menambahkan colon (:) setelah variable.

{% highlight swift %}

let implicitInteger: Int = 19
var implicitDouble = 19.0
var explicitDouble: Double = 19

{% endhighlight %}

Sebuah value tidak bisa secara implisit berubah ke type lain. Jika kita ingin mengubah value ke type lain, maka kita harus secara eksplisit mengubah value tersebut dengan cara membuat sebuah instance dari type yang diinginkan  

{% highlight swift %}

let age = 19
let label = "My age is"
var myAge = label + String(age)

{% endhighlight %}

Nah, ada cara lain juga untuk membuat value tersebut menjadi string. Caranya dengan memasukkan value di dalam parentheses dengan tambahan backslash (\\) sebelum parentheses.

{% highlight swift %}

let age = 19
var myAge = "My age is \(age)"

{% endhighlight %}

Membuat array dan dictionary menggunakan brackets ([]). Untuk mengakses element-nya bisa memasukkan index ataupun key di dalam sebuah brackets.

{% highlight swift %}

let colors = ["red", "green", "blue"]
print(colors[1])

let occupations = ["John" : "Programmer",
		   "Doe" : "Designer"]
print(occupations["John"])

{% endhighlight %}

Untuk membuat empty array menggunakan ([]) dan dictionary menggunakan ([:]). Atau bisa juga secara explicit menggunakan initializar syntax. 

{% highlight swift %}

let emptyImplicitArray = []
let emptyExplicitArray = [String]()

let emptyImplicitDictionary = [:]
let emptyExplicitDictionary = [String : Double]()

{% endhighlight %}

<br/>

<h3>Control Flow</h3>
<br/>
Control flow di Swift mirip dengan control flow bahasa pemrograman pada umumnya. *if* dan *switch* untuk conditonal statement dan gunakan *for-in*, *for*, *while*, dan *repeat-while* untuk loops. Mungkin disini yang terdengar asing adalah *repeat-while*, akan tetapi sebetulnya ini sama saja dengan *do-while*

{% highlight swift %}

let planets = ["Mercury", "Venus", "Earth", "Mars", 
	       "Jupiter", "Saturn", "Uranus", "Neptune"]

for planet in planets {
   if planet == "Earth" {
      print("I live on \(planet)")
   } else {
      print("There aliens living on \(planet)")
   }
}

{% endhighlight %}

*for-in* juga bisa digunakan to iterate over items in a dictionary. Dikarenakan dictionary itu merupakan unordered collection, maka element yang muncul dari iterasi akan ditampilkan secara acak.

{% highlight swift %}

let occupations = ["John" : "Programmer",
		   "Doe" : "Designer",
		   "Fulan" : "QA"]

for (name, occupation) in occupations {
   print("\(name) is a \(occupation)")
}

{% endhighlight %}

Dalam sebuah *if* statement, conditional value haruslah boolean expression --artinya code seperti *if planet { ... }* bakalan error. Nah, untuk mengatasi hal ini kita bisa menggunakan *if-let* statement. Value yang bisa ditangkap oleh statement ini adalah optional value, artinya bahwa value ini pasti bisa *nil* yang menyatakan bahwa value is missing. Untuk mengindikasikan bahwa value itu optional maka ditambahkan question mark (?).

{% highlight swift %}

var optionalName: String? = "Fulan"
var greeting = "Hello!"

if let name = optionalName {
   greeting = "Hello, \(name)"
}

{% endhighlight %} 

Cara lain untuk mengetahui bahwa value itu optional. Bisa lakukan *print(value)*. Maka di log akan tampil *Optional(value)*. Nah, *if-let* statement digunakan untuk mengambil nilai asli dari value itu sendiri.

##### Note
<blockquote>
	Jadi best practice-nya untuk menggunakan optional value adalah ketika kalian benar2 yakin bahwa variable tersebut akan menghasilkan nil value. Jika variable tersebut ga ada kemungkinan untuk menghasilkan nil value, maka ga perlu lah untuk dijadikan sebagai optional value.
</blockquote>

Swift *switch* statement support berbagai macam data type dan comparison operations. Setelah code di dalam *case* tereksekusi, maka program akan otomatis exit dari *switch* statement tanpa perlu ada *break* secara explisit. Kecuali jika tidak ada code yang akan dieksekusi, maka diperlukan *break* secara explisit.

{% highlight swift %}

let snack = "Spicy Potatoes"
let snackComment: String

switch snack {
   case "French Frice":
      snackComment = "Add some salt, please!"
   case let snack where snack.hasPreffix("Spicy"):
      snackComment = "Is it spicy \(snack)?"
   default:
      snackComment = "Everything tastes good."
}

print(snackComment)

{% endhighlight %} 

Selain itu case dari *switch* statement juga bisa menerima range dari sebuah angka. Operator yang bisa digunakan adalah ...< (sampai kurang dari) dan ... (sampai dengan). Selain bisa digunakan dalam *switch*, operator ini berlaku untuk loops statement *for*, *for-in*, *while*, dan *repeat-while*.

{% highlight swift %}

let myAge = 19

switch myAge {
   case 1...2:
      print("Toddler")
   case 2..<19:
      print("Kid")
   case 19...25:
      print("Adult")
   default:
      break
}

{% endhighlight %}

Untuk pattern dari syntax *while* dan *repeat-while* statement sama saja dengan bahasa pemrograman pada umumnya.

{% highlight swift %}

var n = 2
while n < 100 {
   n = n * 2
}
n
 
var m = 2
do {
   m = m * 2
} while m < 100
m

{% endhighlight %}

Nah, pembahasan mengenai **The Basics** dari Swift ini memang sengaja ane potong2 menjadi beberapa part. Bukan lain bukan apa, supaya ga terlalu banyak yang dibahas dalam satu waktu dan supaya jadi lebih nyaman aja memahaminya. Ane juga sengaja untuk membahas bener2 dari awal supaya kalian yang (baru) ingin memahami Swift akan lebih mudah untuk paham. For the next part akan dibahas mengenai **Functions and Closures**.

See you on the next part guys..

<br/>
<p class="center">Happy coding. Cheers! 🤓<br/>. . .</p> 




