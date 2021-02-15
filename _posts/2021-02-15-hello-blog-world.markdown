---
layout: post
title:  "Hello Blog World!"
categories: jekyll helloworld blog
---

I created this blog using [jekyll](https://www.jekyllrb.com). I'm starting the Recurse Center Spring 2021 Batch today.

As a test, here's some [Haskell](https://www.haskell.org/) code I wrote last night, adapted from [this paper](https://www.kestrel.edu/people/meertens/publications/papers/Calculating_the_Sieve_of_Eratosthenes.pdf).

{% highlight haskell %}
-- sieve of Eratosthenes 
-- print out primes until terminated

primes :: [Integer]
primes = sieve [2..]

sieve :: [Integer] -> [Integer]
sieve (p : ns) = p : sieve (filter (notdiv p) ns)

notdiv :: Integer -> Integer -> Bool
notdiv d n = n `mod` d /= 0 

main :: IO ()
main = mapM_ print primes
{% endhighlight %}


