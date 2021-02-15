---
layout: post
title:  "Eratosthenes animated"
tags: haskell eratosthenes prime gloss graphics
---



<img src="https://user-images.githubusercontent.com/78932387/107930818-c4e5ff00-6f7b-11eb-962c-bd0cda51764f.gif">

A number is _prime_ if it can not be divided into smaller whole pieces. The first few prime numbers are 2, 3, 5, 7, 11. For example, 4 isn't prime because it is 2 times 2, 6 isn't prime because it is 2 times 3, and 9 isn't prime because it is 3 times 3. But I can divide 5 into whole pieces, because 5 is 5 times 1, you say? Yes, but that doesn't count. I said _smaller_ whole pieces.

An ancient algorithm for finding all the prime numbers is to, well, how do I put this, remove all the non-prime numbers. For example, no even number after 2 is prime, because it can be divided into 2 and something else. No multiple of 3 (other than 3 itself) can be prime either. Now 4 has already been eliminated, so apparently the next prime is 5. But no later multiple of 5 can be prime. Continuing like this, the [sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) gives you all the primes. The first source for it is in the 3rd century BC, which makes it one of the oldest algorithms in history.


[This paper](https://www.kestrel.edu/people/meertens/publications/papers/Calculating_the_Sieve_of_Eratosthenes.pdf), gives a _very_ short functional program that performs this algorithm. In Haskell:

{% highlight haskell %}
primes :: [Integer]
primes = sieve [2..]

sieve :: [Integer] -> [Integer]
sieve (p : ns) = p : sieve (filter (notdiv p) ns)
    where notdiv d n = n `mod` d /= 0 
{% endhighlight %}
 
I was feeling inspired last night and I decided to create the above animation of how various numbers are eliminated in subsequent sieving stages. I wrote this in [Haskell](https://haskell.org) for practice and used the [Gloss](https://hackage.haskell.org/package/gloss) library for drawing and animating. Here's the [source code](https://gist.github.com/mnopqr1/edf697173bde40b5e040d89af912b4ed).


