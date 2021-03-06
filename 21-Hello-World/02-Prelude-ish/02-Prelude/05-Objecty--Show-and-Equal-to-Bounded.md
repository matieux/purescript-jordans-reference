# Objecty

In Java, every object has 3 functions:
- toString
- equals
- hashCode

However, some types do not need these functions (e.g. singletons, lambda functions, etc.). Furthermore, `equals` should only work between objects of the same type (i.e. `4 == "4"` shouldn't compile).

## Show, Equal, Ord, Bounded

Since the documentation for these type classes are clear, we will redirect you to them instead of repeating them here:
- [Show](https://pursuit.purescript.org/packages/purescript-prelude/4.1.0/docs/Data.Show). Note: see hdgarrood's [Down With Show](https://harry.garrood.me/blog/down-with-show-part-1/) 3-part series as to why he thinks we should replace `Show` with something that better suits the purposes for which it is normally used.
- [Equal](https://pursuit.purescript.org/packages/purescript-prelude/4.1.0/docs/Data.Eq) determines whether two values of the same type are equal. In this way, it avoids the problem that Java has above.
- [Ordering](https://pursuit.purescript.org/packages/purescript-prelude/4.1.0/docs/Data.Ordering) is a data type for specifying whether something is less than (LT), equal to (EQ), or greater than (GT) something else.  [Ord](https://pursuit.purescript.org/packages/purescript-prelude/4.1.0/docs/Data.Ord) takes two values of type, `a`, and returns an Ordering. Ord uses `total ordering`. There are a different kinds of ordering that require a different number and type of laws:
    - **Preorder**: reflexive and transitive laws
    - **Parital order**: reflexive, transitive, and antisymmetric
    - **Total order**: reflexive, transitive, antisymmetric, and total (e.g. it can order every value of a given type)
- [Bounded](https://pursuit.purescript.org/packages/purescript-prelude/4.1.0/docs/Data.Bounded) just adds an upper and lower bound to Ord.

## Useful Derived Functions

Most of these come from `Ord`:
- min/max - self-explanatory
- clamp - `clamp lowerBound upperBound value`
- between - `between lowerBound upperBound value`
