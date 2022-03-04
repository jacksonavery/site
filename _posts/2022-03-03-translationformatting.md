---
layout: post
title:  "Formatting and Translations"
date:   2022-03-03 00:00:00 -0500
editdate:
tags: english design
furigana: true
---

###### In designing a website that discusses one language (<span class="smallcaps">jp</span>) largely in another (<span class="smallcaps">en</span>), one of the inevitable problems is how to provide text in both. In this post I'll discuss the challenges involved, analyze some other site's solutions, and explain my own choice. This comes up for me mostly when quoting, but for sites looking to teach another language this will comes up any time you need to provide an example.

### パート壱：Why can't you just do it normally?

I'll forgive you your insolence, given that you, in this case, are me, and because this trope *and* the meta-variant of this trope are both overplayed.[^cringe] With that out of the way, the reason I don't want to quote inline is that「見苦しいだから」"it looks awful." It's awkward to parse for human and computer[^leftdoublequote] alike, the spacing is terrible no matter what I do, and overall it seeps unprofessionalism. 

For my audience with more knowledge of <span class="smallcaps">jp</span>, you may be asking "why not furigana?" 

[理由はこれに:This is why.]。

[This way definitely isn't any better.:この方も確かに醜い。]

I figured out while writing this that Yomichan can't (or won't) scan this furigana either, which is really the nail in the camel's back. To be clear, I'm not native-level, don't sentence mine from me, but forcing any reader to copy/paste text into [Jisho](https://jisho.org) in current-year is downright inhumane.

A better solution must be possible. Thus, let us evolve from good artists to great.

### パート弐：Other people's solutions

#### 弐点壱：[Tofugu](https://www.tofugu.com/)

![Tofugu.com Screenshot](/assets/translationformatting/tofugu1.jpg)

This is implemented with an HTML unordered list and some ::before CSS, strangely enough. Nothing wrong with that though.

First off, the font is too small. It doesn't carry exactly in screenshot, so feel free to follow the link to the specific page [here](https://www.tofugu.com/japanese/kosoado/), but it's legitimately difficult for me to read. Bonus points for the furigana. This is more of a complaint about modern website design in general, not just Tofugu, but please make the font bigger. "Just zoom in," except that that increases the size of the text field too. Now I'm leaning extra far back so I don't strain my eyes snapping back to the beginning of every extra-long line, and we're back where we started. Normal text-heavy websites are infinitely tall already, it's fine to narrow the field for the sake of legibility. [Butterick's Practical Typography](https://practicaltypography.com/line-length.html) recommends a line length of 45-90 characters; Tofugu clocks in at ~113. Anyway.

Tofugu's design is rather minimal, just indent and write the two pieces of text, <span class="smallcaps">jp</span> first. The main problem I have with this is the way the languages are stated explicitly every single time. Maybe if you've never seen either language in your life it's helpful, but the site is written *in* English. I think it's fair to assume the audience knows what that looks like. From there, it's reasonable to assume that the other language shown is the only other language the site ever talks about. It's a minor detail, but by adding the redundant labels the size of the original+translation insert is doubled for no benefit.

#### 弐点弐：[Tae Kim](https://guidetojapanese.org/learn/)

![Tae Kim Screenshot 1](/assets/translationformatting/taekim1.jpg) 

![Tae Kim Screenshot 2](/assets/translationformatting/taekim2.jpg)

The first is a list, as you'd expect, and the second is plaintext.

Specific page [here](https://guidetojapanese.org/learn/grammar/stateofbeing). The official Tae Kim website uses two different designs, one for single sentences and one for dialogues. Both are rather, well, utalitarian. However, the gothic font is thicker and more legible than Tofugu's minchō one at the same size. 

I must reiterate my rant about line length; a random line from Tae Kim was 112 characters. In general, Tae Kim's guides are fairly ugly, but they convey information as well as Tofugu's. I can't really complain much, they do the job, but I personally expect a little more for my own site. The fullwidth <span class="smallcaps">jp</span> "Ａ：" followed directly by the properly spaced <span class="smallcaps">en</span> "A:" is particularly crunchy.

The layout is vertically successive, as was Tofugu's.

#### 弐点参:[Vocaloid Lyrics Wiki](https://vocaloidlyrics.fandom.com/)

![Vocaloid Wiki Screenshot](/assets/translationformatting/vocaloidwiki1.jpg)

This uses an HTML table, as do I.

Specific page [here](https://vocaloidlyrics.fandom.com/). Finally, the other alignment style: the text and its translation aligned horizontally instead of in vertical succession. I don't need to tell you this specific site is unnatractive but there's potential here as well. 

This was my original plan, sans romaji column. However, I quickly ran into the issue that there isn't enough space for even a normal sentence without overflowing into the next line, let alone a longer one (this example only makes sense if your screen is at least 750px wide):

|では、私は仏御前様のお相手をしに行くわね。|Anyways, I must go to be with Hotoke.|

>from [heikemonogatari ep02](/2022/02/26/0001.html)

This isn't crippling, but it's really awkward when a sentence bleeds into the next line by only a word or two. I also need space to cite the speaker whenever I'm quoting more than a single line of dialogue, so I returned to vertical form.

### パート参：My solution

|Speaker|この文はちょっと長いかもまだテーブルに合います。|
||This sentence might be a little long but it still fits in the table.|
|Talker|私も言いたいことがないけど例文のためにもうちょっとベラベラした方がいい。|
||I also have nothing of meaning to express but for example's sake it's essential I go on a bit.|

At the end of the day, there's nothing incredible going on, but I honestly think it's a contender for best I've seen. Most sites of this flavor aren't really big on design, and there's a salient sense in the community that if something is too well designed it's trying to sell you something. I understand the sentiment, and I feel it myself at times,[^refold] but nowadays there's no reason why a site can't be attractive. In turn, there's no reason why it has to either.

Anyways, I battled internally a bit over whether or not to indent the text at the start of a line, but decided to go without for the marginal space gain. The color alternation comes from the theme I use, Minima, but I made minor changes to most else to get a more clean look.[^ironic] Everything else was just minor tweaking until it looked good and worked well.

In kramdown, the above table is encoded as:

```
|Speaker|この文はちょっと長いかもまだテーブルに合います。|
||This sentence might be a little long but it still fits in the table.|
|Talker|私も言いたいことがないけど例文のためにもうちょっとベラベラした方がいい。|
||I also have nothing of meaning to express but for example's sake it's essential I go on a bit.|
```

It was important to me that it was simple enough to create translations in plaintext, as is the point of markdown. I would say I suceeded. 

The CSS is as follows, although it uses a fair number of variables defined elsewhere:

```
table {
  margin-bottom: $spacing-unit;
  width: 100%;
  text-align: $table-text-align;
  color: lighten($text-color, 18%);
  border-collapse: collapse;
  tr {
    &:nth-child(odd) {
      background-color: lighten($grey-color-light, 6%);
      //border-top: 1px solid $grey-color-light;
    }
  }
  th, td {
    padding: ($spacing-unit / 3) ($spacing-unit / 3);
  }
  td+td {
    border-left: 1px solid $grey-color-light;
  }
}
```

Thanks for reading, また今度。

---

[^cringe]: The meta-meta-variant though? Hilarious.

[^leftdoublequote]: The reason for the nasty quotation mark in the middle is that the code that converts straight quotes into curly quotes recognizes '」' as a text character, and snaps quotes to it as such. This is fair enough, it's meant as a rudimentary alphabet parser, and <span class="smallcaps">jp</span> quotes are not alphabetical. Regardless, I really don't think I have it in me to copy-paste the correct quote in every time, and I'm not looking to mod kramdown at the moment.

[^refold]: Tofugu is respectable about Wanikani, but see [refold](https://refold.la). Those web transitions aren't getting me to pay for material with free greater-than-or-equivalents. In both cases, what's out there for Anki is better and free.

[^ironic]: Ironically, Minima's base table is not minimal at all.