# `private` vs. `protected` methods

This seems to be a widely discussed and never-ending story within the PHP community. We think that there are good reasons to use both of them.

As a general rule of thumb you may refer to this:

Start by declaring your class methods to be `private`. A lot of your code should be easily replaceable by using proper Dependency Injection principles. If you, however, realize there's a real use case for a third party developer to override a given method, declare it `protected`. Moreover, note that `public` methods do not necessarily imply that they represent a public API.

Blog posts worth reading:

- [Pragmatism over Theory: Protected vs Private, Fabien Potencier](http://fabien.potencier.org/article/47/pragmatism-over-theory-protected-vs-private)
- [PRIVATE VS PROTECTED: LET’S COMBINE THEM!, Vitor Baum](http://phpandme.tumblr.com/post/4391869601/private-vs-protected-lets-combine-them
)
