# Shapeless Tag Generator
This tool was created to generate the boilerplate code that usually accompanies using [shapeless](https://github.com/milessabin/shapeless) tagged types.

This tool is very simple and is written in Python. This functionality would make much more sense as an SBT plugin.

## Example Usage
```
shapeless-tag-generator --tags 'MovieId:String MovieName:String Rating:Double'
```

Output:
```
sealed trait MovieIdTag
type MovieId = String @@ MovieIdTag

object MovieId {
  def apply(movieId: String): MovieId =
    tag[MovieIdTag][String](movieId)
}

sealed trait MovieNameTag
type MovieName = String @@ MovieNameTag

object MovieName {
  def apply(movieName: String): MovieName =
    tag[MovieNameTag][String](movieName)
}

sealed trait RatingTag
type Rating = Double @@ RatingTag

object Rating {
  def apply(rating: Double): Rating =
    tag[RatingTag][Double](rating)
}
```

## Checks
```
mypy shapeless-tag-generator
pycodestyle shapeless-tag-generator
```
