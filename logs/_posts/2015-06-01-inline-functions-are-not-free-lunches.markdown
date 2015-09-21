---
layout:     post
title:      "Inline functions aren't free lunches"
subtitle:   "Think thoroughly before using inline functions."
date:       2015-06-01 21:01:00
author:     "Joshua Zhang"
header-img: "img/post-bg-02.jpg"
---

<p>When you start thinking about optimization, the world gets twisted. The first glance at inline semantic in C/C++ should always be a fantastic encounter. </p>

<p>By replacing a code block in-place, we save a function call which is quite precious when enormous functions are executed frequently. Besides, compliers can apply more optimization mechanisms on inline functions than you could think of underneath. I was stunned by this brilliant idea and started to keep optimization in mind.
The only drawback seems to be the the flexibility. Once you declared the inline function, any modification requires re-compilation of all functions including it. But if you don't care, we can enjoy the free lunches to make our programs faster. Or really?</p>

<p>The answer is NO.</p>


<h3>Inlining functions may increases object code</h3>
<p>I don't have a diploma in Statistics, but I can imagine the compiled object code might inflate if you declare many normal functions as inline. Memory size is limited, so as code segment. 
Increased size in object code will trigger paging actions, thus decrease instruction cache hit rate. In other words, the program may runs slower than before, the opposite way you could expect.</p>


<h3>Inlining makes debugger unhappy</h3>
<p>Most debuggers could do nothing to inline functions. Step inside inline functions? No way.</p>
<p>Probably the best walkaround for compilers is to build an non-inlined version and set break points in debug environment. It may not be convincing, but sometimes inline functions are nasty if you want to set break points</p>


<h3>Inlining implicitly happens</h3>

<p>Even if you don't explicitly declare inline, implicit inline functions lie everywhere, including the bad ones.</p>
{% highlight c%}
class Base{
public:
...
}
class Derived: public Base {
public:
	Derived() {...} // inline implicitly happens here.
}
{% endhighlight %}
<p>The constructor in Derived class is implicitly declared as inline. It seems like a good inline candidate. However, if you consider the Base class, you would expect a lot of things will happen in the Derived class constructor.
Indeed, complier will do lots of work here, filling it with a huge bulk of codes, which means, the bad thing happens without even a notice.</p>

<h2>Conclusion</h2>
<p>The conclusion is quite obvious, inlining is not the elixir for speeding up. Improper use will lead you to the opposite direction.
However, don't be scared, inline functions are useful, as long as we think thoroughly before declare it.</p>
<p>Simple guildline to inlining</p>
<ul>
<li>Do not declare inline functions when you start writing functions.</li>
<li>Replace macros you would instead use with template inline functions.</li>
<li>Check which functions are frequently called and less than 10 lines <a target="_blank" href="https://google-styleguide.googlecode.com/svn/trunk/cppguide.html">(according to Google C++ style guide)</a>, inline them if you think necessary.</li> 
</ul>
