# ❓ How to vision: "Status quo" stories

We want to make sure all Async Rust users and their experiences are reflected in the async vision doc, so please help us by writing 'status quo' stories about your experiences or the experiences of others! Remember, **status quo stories are not "real", but neither are they fiction.** They are constructed from the real experiences of people using Async Rust (often multiple people). 

[sq]: ../status_quo.md
[character]: ../characters.md
[comment]: ./comment.md

## Goals of a status quo PR

When writing a [status quo][sq] narrative, your goal is to present what you see as a major challenge for Async Rust. You want to draw upon people's experiences (sometimes multiple people) to show all the aspects of the problem in an engaging and entertaining way.

Each story is always presented from the POV of a particular [character]. Stories should be detailed, not abstract -- it's better to give specifics than generalities. Don't say "Grace visited a website to find the answer to her question", tell us whether she went to stackoverflow, asked on reddit, or found the answer on some random blog post. Ideally you should get this detail from whatever your "source" of the story is -- but if you are using multiple sources and they disagree, you can pick one and use the FAQ to convey some of the other alternatives.

## The role of the FAQ

Every status quo PR includes a FAQ. This FAQ should always include answers to some standard questions:

* What are the morals of the story?
    * Talk about the major takeaways-- what do you see as the biggest problems.
* What are the sources for this story?
    * Talk about what the story is based on, ideally with links to blog posts, tweets, or other evidence.
* Why did you choose *NAME* to tell this story?
    * Talk about the character you used for the story and why.
* How would this story have played out differently for the other characters?
    * In some cases, there are problems that only occur for people from specific backgrounds, or which play out differently. This question can be used to highlight that.

You can feel free to add whatever other FAQs seem appropriate. You should also expect to grow the FAQ in response to questions that come up on the PR.

## The review process

When you opan a status quo PR, people will start to [comment] on it. These comments should always be constructive, with the goal not of negating the story but of making it more precise or more persuasive. Ideally, you should respond to every comment in one of two ways:

* Adjust the story with more details or to correct factual errors.
* Add something to the story's FAQ to explain the confusion.
    * If the question is already covered by a FAQ, you can just refer the commenter to that.

The goal is that, at the end of the review process, the status quo story has a lot more details that address the major questions people had.

## 🤔 Frequently Asked Questions

* What is the process to propose a status quo story?
    * Just open a PR!
* What if my story applies to multiple characters?
    * Look at the "morals" of your story and decide which character will let you get those across the best.
    * Use the FAQ to talk about how other characters might have been impacted.
    * If the story would play out really differently for other characters, maybe write it more than once!
* How much detail should I give? How specific should I be?
    * Detailed is generally better, but only if those details are helpful for understanding the morals of your story.
    * Specific is generally better, since an abstract story doesn't feel as real.
* What should I do when I'm trying to be specific but I have to make an arbitrary choice?
    * Add a FAQ with some of the other alterantives, or just acknowledging that you made an arbitrary choice there.
* None of the characters are a fit for my story.
    * It doesn't have to be perfect. Pick the one that seems like the closest fit. If you really feel stuck, though, come talk to us on [Zulip] about it!
* How should I describe the "evidence" for my status quo story?
    * The more specific you can get, the better. If you can link to tweets or blog posts, that's ideal. You can also add notes into the [conversations] folder and link to those. Of course, you should be sure people are ok with that.
