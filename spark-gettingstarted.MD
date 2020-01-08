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

## 3. Filter
```java
// 
val movies2010 = movies.filter(
  m => m.substring(m.length-4, m.length).toInt == 2010
)
```

# --------------------
# Filter avec les 4 derniers caracteres
# --------------------

val movies2010 = movies.filter(m => m.substring(m.length-4, m.length).toInt == 2010)

