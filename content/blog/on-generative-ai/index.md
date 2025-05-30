+++
title = "On GenAI"
date = "2025-05-27T16:06:37-04:00"
tags = ["genai", "society", "ethics"]
audio = []
images = []
videos = []
draft = "true"
summary = "Nobody should use GenAI. Software engineers should not build GenAI systems.  Companies should not sell GenAI products."
+++

I have been having many thoughts about GenAI tools lately.  They keep bouncing
around inside my head, and I need to get them out.

I do not like these tools.  I think they are hurting the people who use them and
hurting our society at large.  And I want all that to stop, but I don't know to
make a difference.

The best I think I can do is explain why I feel this way and ask you to not use
GenAI tools any more.

## Terminology

Before I get into the weeds, I want to make sure everyone reading this knows
what specifically I'm talking about.  Over the last several decades, there have
been many technological advances called "AI."  Up until recently, these advances
have been useful for people and beneficial to society as a whole.  These are
things like [better noise cancellation for video calls][rnnoise], [recognizing
handwritten addresses on pieces of mail to sort it
automatically][handwriting-recognition], and even [computers with graphical
interfaces][gui] and [web search tools like Google][web-search].

[rnnoise]: https://jmvalin.ca/demo/rnnoise/
[handwriting-recognition]: https://dl.acm.org/doi/10.5555/646270.685138
[gui]: https://crm.org/articles/xerox-parc-and-the-origins-of-gui
[web-search]: https://en.wikipedia.org/wiki/PageRank

However, the latest generation of tools are significantly different.  Rather
than reducing busy-work, connecting people, or making computing more accessible
to everyone, these new tools---ChatGPT, Gemini, Claude, DALL-E, Stable
Diffusion, Sora, and anything like that---are given a prompt and _generate_ a
response of some kind (an image, an essay, a video, computer code). So, to make
it clear what I'm talking about, I will use the term "GenAI" to refer to this
new generation of tools.

## Why is GenAI Bad?

If you just want the TL;DR: it's bad because

1. it doesn't help you learn, and
2. it has been designed for the explicit purpose of replacing valuable human
   culture activities with a robot that can be controlled and doesn't require
   fair pay for its work.

But that skips all the reasoning to get to the answer, which is an important
part of evaluating whether the answer is any good.  I'll begin by laying out why
I think individual people should not use these tools.

### It's Bad for Each of Us

In early 2025, [Microsoft studied how "knowledge workers" (people whose job is
to think, like doctors, lawyers, and programmers) used GenAI
tools][ms-criticalthinking], and how it affected their thought processes. They
analyzed 936 examples of real-world usage of GenAI tools and concluded: "[W]hile
GenAI can improve worker efficiency, it can inhibit critical engagement with
work and can potentially lead to long-term overreliance on the tool and
diminished skill for independent problem-solving."  To translate this from
academic-speak, people who use GenAI tools tend to stop thinking critically
about what they use the tools for, and it reduces their capacity to solve
problems on their own.

[ms-criticalthinking]: https://www.microsoft.com/en-us/research/wp-content/uploads/2025/01/lee_2025_ai_critical_thinking_survey.pdf

This result may at first feel like the same kind of argument that elementary
school teachers were fond of making, which usually went something like, "You
have to learn your times tables because it's not like you're going to have a
calculator on you every day for the rest of your life."  This is unconvincing to
me personally, because I have a calculator strapped to my wrist (smart watch),
and a slightly larger calculator in arm's reach (smart phone) every moment of
every day.  It also echoes similar arguments made back through history, all the
way back to "all this written language is going to ruin our ability to remember
things." If we're all going to have access to these tools all the time, what
does it matter if we're not as good at some skill?  

I think that decreasing our ability to engage in critical thinking is
fundamentally different from any of the concerns brought up about prior
technological advancements.  One of the distinguishing features of being human
is our ability to learn, grow, explore, and come up with new ideas.  If we
choose to outsource those traits to a GenAI tool, what is the point of being
human?  And this is especially damaging if people use GenAI instead of learning
new skills.  Beginning computer programmers who uses a GenAI tool to write code
are depriving themselves of opportunities to learn about new aspects of
programming---and to develop the experience necessary to identify subtle bugs.
Students who use GenAI to write essays are depriving themselves of the
opportunity to learn how to communicate their ideas more effectively.  (And it's
doubly silly to use GenAI in college, because you have to pay to be there!)   A
growing artist who uses GenAI to replace phases of the artistic process throws
away opportunities to improve their understanding of anatomy, shading, posing,
or any of a dozen other techniques that are crucial to visual communication.

Beyond that, GenAI systems do not have an understanding of how well they know
any particular topic.  For example, I know that I know a great deal about
computers, I half-remember my high school chemistry classes, and I know
basically nothing about
[pharmacology](https://en.wikipedia.org/wiki/Pharmacology).  If you ask me a
question about computers, I can talk your ear off about it!  But if you ask me a
question about pharmacology, I'd be a charlatan if I said anything other than
"Oh I'm the wrong person to ask about that." Because of fundamental limitations
of their design, these generative tools are not able to judge their own
knowledge the way a human can.  If someone asks one of these tools about a
subject that is well-represented in the training data, it will respond
confidently with an answer that is usually correct.  If someone asks it about a
subject that is largely _absent_ in the training data, _it will still respond
confidently,_ but it will _make up random crap for an answer!_  None of these
tools will reliably respond with "I don't know."  They simply do not have the
capability to understand their own understanding.  Google got in trouble for
this shortly before the time of writing this essay because [their Gemini tool
would confidently make up an explanation for whatever idiom you asked
about][gemini-idioms], even if it was a completely made-up idiom like "you can't
lick a badger twice."  So someone trying to use a GenAI system for research---or
just to answer a question they're curious about---can't know whether the tool
answered the prompt truthfully, or confidently made up nonsense!

[gemini-idioms]: https://www.wired.com/story/google-ai-overviews-meaning/

### It's Bad for Society

GenAI tools don't just deprive people of opportunities to learn and
confidently [bullshit][chatgpt-bullshit] about things they don't know, they are
also terrible for society at large.  When Generative Pre-trained Transformers
(the GPT in ChatGPT) were an academic curiosity 5 years ago, nobody had
thoroughly considered what problems might arise if suddenly everyone was using
them. However, there is a certain kind of person who is constantly on the
lookout for opportunities to make money, no matter the cost. This time, it
happened to be Elon Musk and Sam Altman.  They realized that these academic
papers about GPTs and diffusion networks could be the key to a new world.

[chatgpt-bullshit]: https://link.springer.com/article/10.1007/s10676-024-09775-5

In their new world, nobody has an office job.  ChatGPT can write emails, develop
software, write marketing copy, design advertisements, coordinate projects,
answer phone calls, and do everything else that you might expect a human in an
office to do (except spin in the office chairs).  But you know what ChatGPT
won't do?  Say 'no' or demand fair pay for work done.  And that means they can
sell ChatGPT to companies and make _boatloads_ of money.  Who cares if companies
buy access to ChatGPT and then fire everyone whose job can't be automated?

Because these rich, greedy ghouls are exclusively focused on money, they do not
care how GenAI affects real people.  The technology that backs these tools does
not work unless it is trained on _gigantic_ volumes of data.  How do you get
that much data if you have no morals?  [You pirate every book you can get your
hands on][meta-libgen] without licensing them from the authors, [do the
same][midjourney-marvel] with every movie, [download every piece of text you can
find on the internet][google-ignore-robotstxt] even when people ask you not to,
and [download everything on popular art-sharing website
ArtStation][artstation-trending-prompt] (note that all of these prompts include
"trending on artstation").  And just to make it explicitly clear, the executives
at these companies know that what they're doing is immoral, _and they're
choosing to do it anyway._

* [Nick Clegg, Facebook][clegg]: "I just don't know how you go around, asking
  everyone first. I just don't see how that would work. And by the way, if you
  did it in Britain and no one else did it, you would basically kill the AI
  industry in this country overnight."
* [OpenAI][openai-houseoflords]: "Because copyright today covers virtually every
  sort of human expression---including blog posts, photographs, forum posts,
  scraps of software code, and government documents---it would be impossible to
  train today's leading AI models without using copyrighted materials."

[meta-libgen]: https://www.tomshardware.com/tech-industry/artificial-intelligence/meta-staff-torrented-nearly-82tb-of-pirated-books-for-ai-training-court-records-reveal-copyright-violations
[midjourney-marvel]: https://www.nytimes.com/interactive/2024/01/25/business/ai-image-generators-openai-microsoft-midjourney-copyright.html
[google-ignore-robotstxt]: https://futurism.com/googles-ai-scraping-sites-opt-out
[artstation-trending-prompt]: https://promptden.com/inspiration/artstation+all
[clegg]: https://www.businessinsider.com/ex-meta-exec-ai-doomed-tech-firms-ask-artists-permission-2025-5
[openai-houseoflords]: https://committees.parliament.uk/writtenevidence/126981/pdf/


After harvesting all of this data and training their GenAI models on it, the
models can produce shockingly good approximations of human writing and human
art.  And they can do it many orders of magnitude faster than a human can write
or create.  The same artists whose works were harvested without consent or
compensation have then [discovered that you can prompt various GenAI tools to
generate images _in their style,_][style-copy] and get reasonable facsimiles of
their work. That makes it very difficult for them to continue to be paid for
their artwork.  Multiply that by the number of working artists across the world,
and it is clear that these tools will cause irreparable harm to folks whose
living depends on their art or writing.

[style-copy]: https://www.trails.umd.edu/news/ai-imitating-artist-style-drives-call-to-rethink-copyright-law

This has an even more insidious knock-on effect.  Writers, artists, and
journalists whose names we all learned in school did not spring into the world
fully formed with an unchanging level of skill.  Leonardo da Vinci studied under
Andrea del Verrocchio for years before earning his reputation. Bob Woodward
started out working at the Montgomery Sentinel before he could make it at the
Washington Post.  Ursula K. Le Guin wrote five whole novels roundly rejected by
publishers, pivoted to science fiction and wrote a dozen short stories, and then
finally hit her stride with the _Earthsea_ series.  Nobody can be a good artist
without first being a mediocre one.  GenAI tools erase the market for
mediocre artists, writers, and journalists.  Small news organizations won't hire
journalists fresh out of school if they can have someone prompt a GenAI for
whatever they need, and then there won't be any stellar journalists. Artists
won't be able to practice their skills in order to rise to a world-changing
level if they can't find work to pay their bills.  Writers will not be able to
afford to devote the time required to write books that shift culture if they
can't make ends meet.

(An aside: do I think the situation from ~5 years ago was good?  No!  It sucks
for writers to have to fight with publishers to get their works accepted, even
when they _are_ that good.  It's humiliating for artists to beg for commissions
on Twitter so that they can afford rent for the month.  Nobody should have to
live like that.  But GenAI tools aren't going to make that situation any
better!)

## Don't Use GenAI

I hope I've made it clear that GenAI tools are at best useless and at worst
actively harmful to society.  If you use any GenAI tools, please stop!  I
promise that whatever you're using it for, you can either do yourself or pay
someone to do for you, and the results will be so much better.

If you're a software engineer working on GenAI tools, just say no!  Tell
your manager that what you're being asked to do [violates the ACM code of
ethics][acm-code] and it would be a violation of your responsibilities as a
professional to make these tools or allow them to be made.  Specifically, GenAI
tools regularly fail to "acknowledge that all people are stakeholders in
computing," (1.1) _including_ the ones whose jobs are getting destroyed by these
tools. GenAI tools also regularly fail to "avoid harm," (1.2) especially harm
caused to the livelihoods of people who contribute the most to human culture.
Finally, almost every GenAI training data set fails to "respect the work
required to produce new ideas, inventions, creative works, and computing
artifacts," (1.5) because they do not explicitly seek consent for creative works
to be included in the data set.

[acm-code]: https://www.acm.org/code-of-ethics

If you're in charge of products at any of these companies, please tell your
superiors that nobody wants more GenAI features, and that the company would be
better served by focusing on helping people instead.  When appropriate, it may
also be helpful to remind them that [outputs from GenAI are not
copyrightable][nlr-nocopyright].

[nlr-nocopyright]: https://natlawreview.com/article/copyright-offices-latest-guidance-ai-and-copyrightability

And if you're an executive or board member at one of these companies?  I've
heard that the latest health fad among your peers is to take one of those
expensive NVIDIA data center GPUs, remove the heat sink, break the card itself
up into lots of pointy shards, and then take the shards as a suppository.

---

I've immersed myself in computing since age 12.  I wanted to learn how to write
software because I saw [Jérémie][jeremie] develop the [Skidbladnir][skid] in my
favorite cartoon, and thought "that's the coolest thing I've ever seen, I wanna
do _that!_"  So I taught myself how to program, learned everything I could about
computers, tried every operating system I could get my paws on (to the detriment
of the family computer and also my first laptop), and went to college to become
a professional software developer.  I love computers.  They're probably the most
powerful tool that humanity has built to date.  They have the capability to do
so much good in the world, and I've devoted my life to learning about them,
advancing the field, and making the world a better place for everyone through
the medium of software.

[jeremie]: https://en.codelyoko.fr/personnages/jeremie.cl 
[skid]: https://www.codelyoko-leguide.fr/en/70

But computers can also be used to cause terrible harm.  I am distraught by the
rapid rise of GenAI.  I am anguished by my industry's decision to abandon the
goal of bringing computing to everyone, and instead choose to replace everyone
with computers. It hurts me endlessly to watch these companies shovel every
aspect of human culture into an industrial macerator, so that they can extrude
billions upon billions of pieces of polite nonsense that all have the same
veneer of congeniality over an utter lack of meaning.  This isn't what computing
is supposed to be about.  The only people who this helps are rich assholes like
Sam Altman, Mark Zuckerberg, Elon Musk, and Jeff Bezos.  And the only thing it
helps do is take money that the rest of us are owed and funnel it into their
various investment schemes.

I don't know what to do any more.  I want to use my passion for computing to
help regular people, but the rest of the industry seems to have decided that
helping people isn't profitable.  And every regulatory process meant to prevent
this kind of thing from happening has been gutted by the very same ghouls who
are benefiting from it.

Maybe I should pivot to the trades and settle for computing as a hobby.

---

If you have thoughts, feedback, or corrections about this essay, you can find my
email on the home page of this website.  Please be kind---I understand if you're
angry or upset too, but taking it out on me doesn't help make anything better.
