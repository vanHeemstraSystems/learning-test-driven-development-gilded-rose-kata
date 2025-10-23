# 100 - Instructions

Based on [Gilded Rose Refactoring Kata on GitHub](https://github.com/emilybache/GildedRose-Refactoring-Kata/blob/main/README.md).

You can find out more about this exercise in Emily Bache's YouTube video [Why Developers LOVE The Gilded Rose Kata](https://youtu.be/Mt4XpGxigT4). Emily Bache also have a video of a worked solution in Java - [Gilded Rose Kata, Hands-on](https://youtu.be/OdnV8hc9L7I)

Emily Bache uses this kata as part of her work as a technical coach. She wrote a lot about the coaching method she uses in this book [Technical Agile Coaching with the Samman method](https://leanpub.com/techagilecoach). A while back she wrote this article ["Writing Good Tests for the Gilded Rose Kata"](http://coding-is-like-cooking.info/2013/03/writing-good-tests-for-the-gilded-rose-kata/) about how you could use this kata in a [coding dojo](https://leanpub.com/codingdojohandbook).

## How to use this Kata

The simplest way is to just clone the code and start hacking away improving the design. You'll want to look at the ["Gilded Rose Requirements"](https://github.com/emilybache/GildedRose-Refactoring-Kata/blob/main/GildedRoseRequirements.md) which explains what the code is for. She strongly advises you that you'll also need some tests if you want to make sure you don't break the code while you refactor.

You could write some unit tests yourself, using the requirements to identify suitable test cases. She has provided a failing unit test in a popular test framework as a starting point for most languages.

Alternatively, use the Approval tests provided in this repository. (Read more about that in the section "Text-based Approval Testing").

The idea of the exercise is to do some deliberate practice, and improve your skills at designing test cases and refactoring. The idea is not to re-write the code from scratch, but rather to practice taking small steps, running the tests often, and incrementally improving the design. 

### Gilded Rose Requirements in other languages 

See [Gilded Rose Requirements in other languages](https://github.com/emilybache/GildedRose-Refactoring-Kata/blob/main/README.md)

## Text-Based Approval Testing

Most language versions of this code have a [TextTest](https://texttest.org) fixture for Approval testing. For information about this, see the [TextTests README](https://github.com/emilybache/GildedRose-Refactoring-Kata/tree/main/texttests)

## History of the exercise

This Kata was originally created by Terry Hughes (http://twitter.com/TerryHughes). It is already on GitHub [here](https://github.com/NotMyself/GildedRose). Bobby Johnson described the kata in an article titled "Refactor This: The Gilded Rose Kata", but unfortunately it is no longer on the internet. Emily Bache found it on the Wayback Machine [here](https://web.archive.org/web/20240525015111/https://iamnotmyself.com/refactor-this-the-gilded-rose-kata/).

She translated the original C# into a few other languages, (with a little help from her friends!), and slightly changed the starting position. This means she has actually done a small amount of refactoring already compared with the original form of the kata, and made it easier to get going with writing tests by giving you one failing unit test to start with. She also added test fixtures for Text-Based approval testing with TextTest (see [the TextTests](https://github.com/emilybache/GildedRose-Refactoring-Kata/tree/main/texttests))

As Bobby Johnson points out in his article "Why Most Solutions to Gilded Rose Miss The Bigger Picture" (on the Wayback Machine [here](https://web.archive.org/web/20230530152324/https://iamnotmyself.com/why-most-solutions-to-gilded-rose-miss-the-bigger-picture/)), it'll actually give you better practice at handling a legacy code situation if you do this Kata in the original C#. However, Emily thinks this kata
is also really useful for practicing writing good tests using different frameworks and approaches, and the small changes she has made help with that. She thinks it's also interesting to compare what the refactored code and tests look like in different programming languages.
