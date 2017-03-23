# cats-test
A small study project on [typelevel cats](https://github.com/typelevel/cats).

## Documentation
- [Cats documentation](http://typelevel.org/cats/)

## Book
- [Advanced Scala with Cats Book - Noel Welsh and Dave Gurnell](http://underscore.io/books/advanced-scala/)
- [Advanced Scala with Cats Book (preview) - Noel Welsh and Dave Gurnell](https://s3-us-west-2.amazonaws.com/book-sample/advanced-scala-preview-with-full-toc.pdf)

## Semigroup
A [Semigroup](http://typelevel.org/cats/typeclasses/semigroup.html) is a binary associative operation that operates
on the same type, lets call that type `A`.

What does this even mean? Well, this means that the operation has two parameters (binary) and must be of the
same type, `A`. The operation must also return an `A`.

```scala
trait Semigroup[A] {
  def combine(x: A, y: A): A
}
```

The rule is, for each instance of `A` the following must be true, and is easy to test:

```scala
combine(x, combine(y, z)) = combine(combine(x, y), z)
```

If you can implement an instance of `Semigroup` where the above rule is true for instances of `A` for x, y and z
then you have successfully implemented a mathemetical structure called a `Semigroup`.

> If a type A can form a Semigroup it has an associative binary operation.

### What is the clue
Well, its not about the Semigroup really, its about the implementation of the semigroup instance for a certain type.

Lets look at an example for the type `Int`:

```scala
def combine*(x: Int, y: Int): Int = x ??? y
```

If we look at the pseudo code above, the `???` represents an mathematical operation like eg. the `+`, `-`, `*` and so on.
These operations are all binary because they need two inputs:

```scsala
// the '+' sign needs two inputs, 1 and 2 and is
// called a 'binary operation'
1 + 2 = 3
```

Alright, are all binary operations in math associative?

```scala
scala> (1 + 2) + 3 == 1 + (2 + 3)
res0: Boolean = true

scala> (1 - 2) - 3 == 1 - (2 - 3)
res1: Boolean = false

scala> (1 * 2) * 3 == 1 * (2 * 3)
res2: Boolean = true
```

It seems like not all binary operations are associative, but the `+` and `*` are.

## Semigroup instances


## Monoid
[Monoid](http://typelevel.org/cats/typeclasses/monoid.html) extends the power of Semigroup by providing an additional empty value.

```scala
```

## Video
- [(0'18 hr) Discovering Types (from Strings) with Cats and Shapeless - Jonathan Merritt](https://www.youtube.com/watch?v=RecGZB3tclE)
- [(0'49 hr) Cats — A Fresh Look at Functional Programming in Scala - Mike Stew O'Connor](https://www.youtube.com/watch?v=hIwdaP3-U6I)

## Resources
- [Herding Cats - Eugene Yokota](http://eed3si9n.com/herding-cats/index.html)