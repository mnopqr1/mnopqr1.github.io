---
layout: post
title:  "Hello, World Wide Web"
---

This week, I'm trying to build from the ground up an online multiplayer game [like this one](https://codenames.game). I did learn to write some very vanilla and static HTML and CSS at one point in my life, but have always been a little scared of the web, graphics, user interactions. I tend to feel much safer in the homely surroundings of my own terminal and IDE, with some formulas and abstract concepts flying around, instead of having to think about things like [app deployment](https://devcenter.heroku.com/articles/github-integration), user [sessions](https://flask.palletsprojects.com/en/1.1.x/quickstart/#sessions), and [column](https://getbootstrap.com/docs/5.0/layout/columns/) styles. So this project seems like a good way to get out of my comfort zone.

As a first step, I went through [Freecodecamp's front end development](https://www.freecodecamp.org/learn/front-end-libraries/) courses, up until half way through the React course, where it all started to feel a bit theoretical, and I decided I'd be better off trying to build a small prototype of a game and try to learn as I went along. Inspired by [this lecture](https://cs50.harvard.edu/beyond/2019/days/2/), I decided Tic Tac Toe would serve just fine as an online-game equivalent of "hello world".

So I installed myself some Flask, got an [Heroku](https://www.heroku.com) account, and a few hours later, I had this text-based version of Tic Tac Toe that looks like it is from around the year I was born:

![Tic Tac Toe in the past](/assets/tictactoetext.png)

Then, applying what I learned on Freecodecamp about the front end, CSS and Bootstrap, and an hour of a lot of Googling later, it looked like this:

![Tic Tac Toe a little later](/assets/tictactoebootstr.png)

I'm clearly not a graphic designer but at least it now looks like something that was made in the current millennium. It also took a bit of time to get the deployment on Heroku to work (who'd have thought that I'd need to use an application called `gunicorn` for that!), but there is now a **[live version](https://sam-tictactoe.herokuapp.com)** available. The [github repo is here](https://github.com/mnopqr1/tictactoe/). 

It isn't multi-player yet, in other words, you can only play with someone who is physically sitting next to you, which is very 90s but not at all in line with the current state of the world. So that's next, but I think I'm ready to implement the multi-player idea directly for my own game, instead of for tic-tac-toe, which is, after all, not a super exciting game. This will probably involve learning something about how to store sessions server-side, and more React, perhaps? Stay tuned.