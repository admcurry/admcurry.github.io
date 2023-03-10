[<kbd> <br>  Home  <br> </kbd>](https://atcurry.github.io)
[<kbd> <br>  About  <br> </kbd>](https://atcurry.github.io/about.html)
[<kbd> <br>  Notes  <br> </kbd>](https://atcurry.github.io/notes.html)
[<kbd> <br>  Coding  <br> </kbd>](https://atcurry.github.io/coding.html)
[<kbd> <br>  Data Analysis <br> </kbd>](https://atcurry.github.io/data.html)
[<kbd> <br>  Projects (r)  <br> </kbd>](https://atcurry.github.io/rprojects.html)
[<kbd> <br>  Projects (julia)  <br> </kbd>](https://atcurry.github.io/juliaprojects.html)
[<kbd> <br>  Projects (python)  <br> </kbd>](https://atcurry.github.io)
[<kbd> <br>  Repo's  <br> </kbd>](https://atcurry.github.io/repos.html)

---

[<kbd> <- Back to notes  <br> </kbd>](https://atcurry.github.io/notes.html)

<div align="center"> <h1> Statistics </h1> </div> <br/>

**Statistics is the practice and study of collecting and analysing data.**  
**A summary statistic is a fact or summary of some data.**

### Mean:
```
mean(data)
```

### Variance:
The average distance from each data point to the data’s mean.
```
dists <- data - mean(data)
variance <- dists^2 / count(data) - 1

var(data)
```

### Standard Deviation
```
sd(data)
```

### Quartiles
Quartiles split up data into four equal parts.
The interquartile range is the difference between the 25th and 75th percentile.
```
quantile(data)

quantile(data, 0.75) - quantile(data, 0.25)
```

### Outliers


## Probability 

### Setting a Seed
```
set.set(50)
```

### Sampling
```
dataset %>%
	sample_n(5, replace = TRUE)
```

### Summarising Probability
```
size_distribution <- restaurant_groups %>%
  count(group_size) %>%
  mutate(probability = n / sum(n))
  
 size_distribution %>%
   filter(group_size >= 4) %>%
   summarise(prob_4_or_more = sum(probability))
 ```
 
 