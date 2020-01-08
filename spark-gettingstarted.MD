# Getting Started with Spark

## 1. Your variable
```
val movies = sc.parallelize(
    Array(
      "Frozen,2013", 
      "Toy Story, 1995",
      "WALL-E,2008",
      "Despicable Me, 2020",
      "Shrek,2001",
      "The lego movie,2014",
      "Alice in wonderland,2010")
)
```

## 2. Display in Console
```
movies.collect().foreach(println)
```

## 3. First Transformations

### filter() : Predicated as Java8
```scala
// Option 1, extract last 4 characters
val movies2010 = movies.filter(
  m => m.substring(m.length-4, m.length).toInt == 2010
)

// Option 2, split and fetch last
movies.filter(m => m.split(",").last.trim.toInt == 2010).collect().foreach(println)
```

### map() : same as Java
```scala
val familyMovies = movies.map(
  m => (m,Set("a","b"))
)
familyMovies.collect().foreach(println)
```

### flatMap() : explode a collection
```scala
val familyGenres = familyMovies.flatMap{ case(m,g) => g}.distinct
familyGenres.collect().foreach(println)
```

### cartesian() : all combination
```scala
val diff = familyGenres.cartesian(familyGenres).filter{ case(g1,g2) => g1 != g2 }
diff.collect().foreach(println)
```


