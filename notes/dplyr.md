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

<div align="center"> <h1> dplyr Functions </h1> </div> <br/>


**Selecting specific columns:**
```
counties %>%
	select(state, county, population, unemployment)
 
 ```
 
 **Selecting data:**
 ```
 counties %>%
	arrange(population)

#or

counties %>%
	arrange(desc(population))
 ```
 
** Filter:**
 ```
 counties %>%
	arrange(desc(population)) %>%
	filter(state == 'New York')

	filter(state %in% c('New York', 'California'))
 ```
 
 **Changing:**
 ```
 counties %>%
	transmute(state, county, fraction_men = men / population
  
 counties %>%
	mutate(unemployed_pop = population * unemployment /100)
 ```
 
 **Aggregating:**
 ```
 counties %>%
	count(state, wt = population, sort = TRUE)
  
 counties %>%
	group_by(state) %>%
	slice_max(population, n=1)
 ```
 
 **Common functions:**
 ```
 contains()
starts_with()
ends_with()
last_col()
matches()
```
