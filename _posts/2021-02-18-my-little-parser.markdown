---
layout: post
title:  "My Little Parser"
---

[^1]I just completed a [syntax analyzer](https://github.com/mnopqr1/MyNand2Tetris/tree/master/SyntaxAnalyzer) for the language "Jack" (a variant of Java with some simplifications), which was [project 10 of the Nand2Tetris course](https://www.nand2tetris.org/project10). Yay. It took me about 9 hours total start to finish[^2], a bit more than I expected, but that's normal. To make my life a little harder, I decided to do it in Python, because I am more used to writing object-oriented programs in Java, and the course project instructions seem to have been written with Java in mind. 

The way Python does classes and objects is... interesting. Let's just say I learned a lot about my`self`.

Some things I learned / struggled with during this project, in the order that they come to mind:

* Don't forget to write `self.` in front of any call to a function or variable that belongs to this class. `self` = `this` in Java, as far as I understand, but Python is much more rigid about having to say it all the time, whereas in Java you can omit `this` whenever no confusion can arise. I read a bit about it on Stackoverflow and I guess the reason comes down to the fact that omitting `self` can lead to weird scope problems.

* My instinct is to write public getters and setters all the time, but as far as I know Python doesn't really care about visibility of instance variables, so you could just as well access them directly instead of via a getter, say. This feels a bit scary to me, especially in situations like this, which could have come up in this project, but which I deliberately avoided because it felt really icky:

```python
class Tokenizer:
    current_token = "blob"
    next_token = "bleep"
    token_after_that = "meow"

    def advance(self):
        self.current_token = self.next_token
        self.next_token = self.token_after_that

tokenizer = Tokenizer()
an_interesting_token = tokenizer.current_token
tokenizer.advance()
```
The riddle here is: what's in `an_interesting_token` now? And does the answer change if current_token is not a string but an object of another class, Token? (I just tested this and the answers to these questions seem to be `blob` and "No", respectively, but don't quote me on this.)

I guess I need to learn a bit more thoroughly how objects work in Python to understand this.

But now, "[moedig voorwaarts](https://www.deepl.com/translator#nl/en/moedig%20voorwaarts)" to [project 11](https://nand2tetris.org/project11), a full compiler!

---

[^1]: Title inspired by learning last night that Billy Bob Thornton, of Fargo fame, is a [great fan of the animated TV program of the same name, modulo the last few characters](https://www.vulture.com/2016/11/billy-bob-thornton-enjoys-my-little-pony.html).[^a] 

[^a]: How do you get footnotes in a title in Markdown? And can you do footnotes of footnotes? Yes, I like [David Foster Wallace](https://fs.blog/2012/04/david-foster-wallace-this-is-water/).

[^2]: I know this because I tracked my time with [toggl](https://www.toggl.com). It works well and has a reasonably convenient desktop app, but I wouldn't mind switching to a free open source version instead of this freemium thing. Or maybe I should write one as my web dev project...? In any case tracking time helps me combat procrastination.