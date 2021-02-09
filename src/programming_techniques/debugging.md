# Debugging

I've got a particular way I go about debugging systems, less about tools and
more about process. I'm not totally sure how to go about explaining it, that
said, hence this note.

## What Debugging Is

Debugging is the process of repairing your mental model of a software
system. That is, you might _believe_ that your piece of software behaves some
way for some inputs but can _observe_ that it does not. Coming to an
understanding of exactly how and why your mental model differs is the end goal
of debugging. You may, also, want to come up with a way of adjusting the
software to match your incorrect model, but that's a secondary goal. Implicit in
this are some assumptions:

* Software and the computers they run on are _machines_ and can be understood as
  such. They have no self-animation and, while not deterministic, obey a limited
  set of rules in their operation.

* Software and the computers they run on are _human artifacts_ and were meant to
  be understood by humans.

* _Empiricism_ is the name of the game. Your reasoning -- the mental model --
  has to be informed by experimental data. Your reasoning is faulty and can't be
  trusted in isolation. Your experiments are also faulty but in a different
  degree.

* _Magical thinking_ is a curse and we all participate in it. While computers
  are simply machines following rules their complexity is staggering and
  everyone, at some point, has to cut an abstraction line and consider
  everything past that line a magical black box with behaviors that may or may
  not be reflective of the function of that part of things. If your mental model
  of one of these black box areas is wildly wrong but involved in your mental
  model for the component under discussion you're going to have a bad time.

* Debugging is best done as a _social activity_. My areas of magical thinking are
  not yours; my mental model is not yours. Involving other people in debugging
  work -- especially if they are familiar with but not close to the problem --
  almost always bears fruit.

* Mental models are good, testable models are better. In so far as is practical
  if you're investing in testing try to invest in randomized model approaches,
  like QuickCheck. Done right you'll be able to translate your mental model into
  code and lean on the computer to find defects in it.

## How I Debug

I debug following this rough process.

0. Get a statement from people familiar with the system about how things are
   going wrong, ideally something you can reproduce the issue with but, if not,
   at least something to point you in the general direction of things being
   goofy.

1. Isolate known good areas of the program from known bad. Add tests, telemetry
   or drop into a live debugger to find seams in your program where your model
   for the program holds versus where it does not. If you're lucky the resulting
   deviant bit is pretty small, but more often than not it isn't. At this point
   you should have the ability to reproduce an issue -- maybe not _the_ issue --
   against the isolated part of the program, preferably in an automated way.

2. Talk with people that wrote the deviant bit of the program, if it isn't
   you. Are they surprised by its behavior? If not, they may have intentionally
   programmed the isolated chunk to act this way intentionally. Why? If they're
   surprised, see if they have ideas for how to isolate parts of the chunk
   further. Ask for a tour by them of the chunk. Authors have a lot of deep
   insight into a program.

3. Read the source code for the program chunk, taking special care to note how
   your inputs from your reproducible issue are flowed through the code. This,
   hopefully, will give you rough ideas on where the program can be further
   subdivided.

4. If you found areas to subdivide, go back to step 1. Some of your new
   sub-chunk programs will work perfectly in accord with your mental model for
   them, others will not. Ideally, only one will not, in which case there is
   only one deviance, but more often that not you'll find several working in
   concern. Be _sure_ to work only one avenue of exploration at a time. Have the
   discipline to change only one thing at a time to keep your experiments clean.

5. If you're stuck, take a walk. Take a nap. Pack it away for the day. Our minds
   need time to rest and there's only so much that can be done in one continuous
   marathon, however much we mythologize the lone, sleepless hacker. If these
   things don't work, explain your results so far to someone else. The
   "confessional method" of debugging will often trigger new ideas and, more,
   the person you're talking with will have fresh notions.

6. If you've subdivided the program into fine parts and have a reliable, ideally
   automated ways of demonstrating how your mental model is off,
   congratulations, you've debugged the program. If you find that the "leaves"
   of this subdivision process are perfectly fine but it's some integration of
   them together that's dodgy also congratulations. Software faults often occur
   at interfaces and you should, at this point, have some method for
   demonstrating how these combined components don't quite fit right together.

7. Tell folks about your findings. It may be that the program is actually
   behaving correctly and the sense of what the program should do is off, it
   might be that it's just buggy and needs to be repaired. Usually by
   demonstrating an issue you've also demonstrated some kind of avenue for
   fixing it, but laying out your results to other people will often bear fruit
   in this regard that you, now very close to the program, will not have
   considered.

## Some Stray Thoughts

I cannot emphasize enough how important it is in this process to do only one
thing at a time. Explore one chunk of the program at once, change only one thing
at a time, keep as many of the conditions in which failure is first described as
intact as possible until you can _demonstrate_ they're co-incident and not
essential features of the problem. It's often tempting to change multiple things
at once because you "know" that the program won't be affected, but it's just
plain wrong to assume that, sure, my model of how the program work is wrong over
here but over there it's accurate. I can't tell you how many debugging sessions
I've entered into with people and requested, just for giggles, to probe
something they "know" is reliable to find that it's actually the thing that's
goofed. I can't tell you how many times I've done this to myself.

Because we're dealing with rule bound machines it might happen that you need to
unbox the mechanism in one of your black box areas, especially if you don't have
access to a domain expert to talk with.

Things take the time they take. In a world infected with Taylorism there is a
strong sense in this kind of exploration work that the "clock is ticking" and
they better get results fast. May be that there's time pressure but that's an
independent and uncontrollable concern from the time you need to reason and
perform experiments, chat with colleagues. If you're under no external time
pressure but still feel an urgent need to get results, maybe think on that. We
are not, ourselves, repeatable mechanisms.
