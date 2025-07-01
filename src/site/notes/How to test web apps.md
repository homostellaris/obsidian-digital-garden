---
{"dg-publish":true,"permalink":"/how-to-test-web-apps/","tags":["dev"]}
---

The field of software engineering is ever-evolving and there is still lots of room for debate about the best way to do certain things.

One of those things is software testing. We do have some established best practices but in my experience most companies do not follow them. One of these best practices is known as the _testing pyramid_.

![Pasted image 20250701090901.png](/img/user/Pasted%20image%2020250701090901.png)

In this article I will share with you my personal testing philosophy and in doing so convince you that it’s time to lay to rest the testing pyramid analogy. Notice that I use the word _philosophy_ not _science_. This is because what I offer is not hard proof but merely reasoned conjecture, I could very well be wrong! If so then I encourage you to express your disgust in the comments section.

Before getting into the weeds we I must define (and possible re-define) some terminology that is essential to understanding the philosophy.

---
### Terminology
#### Requirements
Some formal specification of what the software needs to do to meet its users needs. How these are decided upon is outside of the scope of this article, for now assume they are magically and perfectly given to you before you start writing the software.
#### Manual test
An employee pretends to be a user and tests a complete copy of the software using the same interface the user would use.
#### End-to-end test
A test run by a computer on a complete copy of the software using the same interface as its user’s. In most cases this is a web browser so browser automation tools are the most common. By necessity this type of testing requires that a complete copy of your software is created for the purposes of testing (hence the term end-to-end).
#### Integration test
A test run by a computer that traditionally covers multiple _units_ at once (i.e. in integration with one another). In my opinion this term is redundant so long as we are clear about what a unit test is. This term will not be used again in this article because it is not necessary! Read the definition of a unit test below and you’ll understand why.
#### Unit test
A type of automated test which covers an individual component of the software. This could be a function, a module, or even a the HTTP API of an entire service; the only thing that matters is that it is not the entire system being tested, if that’s the case then it’s a unit test. The term unit is inherently abstract and so it makes sense to argue over what a unit should be. You can (and probably should) test at many different levels of abstraction so defining a unit is pointless. In this article I will provide a concrete definition of when to use end-to-end tests and when to use unit tests but all you need to know is end-to-end testing is the whole system and unit testing is anything else!
#### Acceptance test
Acceptance tests are used to decide if an iteration of some software meets the requirements it’s supposed to. If the acceptance tests pass then you can ship it! If the acceptance test fails then the requirements are not met and these shortcomings are bugs, so you shouldn’t ship it. Acceptance tests can be any type of tests, they could be manual tests, unit tests, or end-to-end tests. It’s up to you to decide what gives you the confidence to ship! So it goes without saying that it’s really important to come up with a good definition for your acceptance tests.
#### Sanity check
A sanity check is something a human does because it doesn’t trust computers no matter how well they behave. Without getting too philosophical, sanity checks are necessary because despite what the media would believe computer intelligence is nowhere near human intelligence yet. There is no replacement for a human eye and there will not be for a long time. It is always worth getting a human to try the software so they can see it working with their own eyes for the sake of their sanity. But note that it should only take a few seconds to confirm one’s own sanity!
#### Engineering Team
The engineering team is made of software engineers. They are employed by the business to turn requirements into software. It’s not enough for the engineering team to write code, they also need to provide proof that the code satisfied the requirements.
#### The Business
The business earns money by providing solutions to their user’s problems so they get to know their user’s and the problem domain really well and then produce requirements for software that they are highly confident will solve the user’s problems. They employ an engineering team to turn these requirements into software and they want proof that this software meets those requirements.

---

### The philosophy
The testing philosophy has 3 main tenets:
- End-to-end tests are for The Business.
- Unit tests are for the Engineering Team.
- Manual tests are for sanity.
To understand the first two tenets let us compare the strengths and weaknesses of end-to-end tests and unit tests.
#### End-to-end tests are good because
- **They are unlikely to give you false positives.** They foo bar.
- …

…

…

Unit tests are for re-usable things because they cover more inputs.

Because of agile you usually don’t know if some code will be re-used when you first write it. This is a good things. Premature optimisation is not good.

Because of agile / lean refactoring is likely and good. We need end-to-end tests for this. White-box unit tests that are tightly coupled to low-level design are the enemy of adaptability so we only do that for something we now know is going to be heavily re-used.

Come up with a good analogy for end-to-end, single use code, and then refactoring and creating re-usable tools. Could be a date UI component.

Show that what may have been unit tests for the main team can become acceptance tests for the engineering team! And they will have lower level unit tests of their own, so acceptance tests really is an orthogonal concept to end-to-end / unit. 

Emphasise that failing unit tests do not necessarily block shipping.

Something about white box vs black box

Sanity checking is because automation is good