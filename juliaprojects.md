## Julia Plots

[<kbd> <br> Earnings Plot <br> </kbd>](https://atcurry.github.io/juliaprojects/earnings) [<kbd> <br> Voters Plot <br> </kbd>](https://atcurry.github.io/juliaprojects/voters)  

---

### _1) Data Visualisation with PlotlyJS (March '23)_
##### _Below are interactive graphs made using the PlotlyJS package for Julia._

- 1 - Earnings   
A plot highlighting the disparity in wages among graduates from top US schools.  

- 2 - Voters  
A plot showing the countries with the lowest voter turnouts.  

The data is stored in the in Dataframes, and then plotted using Plotly. The plot is saved as a .html file so it remains interactive, however it can be stored as an image or pdf, but it will be static in this format.

#### _Links to plots:_

[<kbd> <br> Earnings Plot <br> </kbd>](https://atcurry.github.io/juliaprojects/earnings) [<kbd> <br> Voters Plot <br> </kbd>](https://atcurry.github.io/juliaprojects/voters)  

#### _Links to code:_

[<kbd> <br> Earnings Julia Code <br> </kbd>](https://github.com/atcurry/julia/blob/main/Plotly/earnings.jl) [<kbd> <br> Voters Julia Code <br> </kbd>](https://github.com/atcurry/julia/blob/main/Plotly/voters.jl)  

#### _Code:_
Below is the code for the first plot

```
using PlotlyJS, DataFrames

schools = ["Brown", "NYU", "Notre Dame", "Cornell", "Tufts", "Yale",
           "Dartmouth", "Chicago", "Columbia", "Duke", "Georgetown",
           "Princeton", "U.Penn", "Stanford", "MIT", "Harvard"]
n_schools = size(schools)[1]

women_salary = [72, 67, 73, 80, 76, 79, 84, 78, 86, 93, 94, 90, 92, 96, 94, 112]
men_salary = [92, 94, 100, 107, 112, 114, 114, 118, 119, 124, 131, 137, 141, 151, 152, 165]

df = DataFrame(
    school=vcat(repeat(schools, 2)),
    salary=vcat(men_salary, women_salary),
    gender=vcat(repeat(["Men"], n_schools), repeat(["Women"], n_schools))
)

# Use column names of df for the different parameters x, y, color, ...
p = plot(
    df,
    kind="scatter",
    marker=attr(size=12),
    mode="markers",
    x=:salary,
    y=:school,
    group=:gender,
    Layout(
        title="Gender Earnings Disparity",
        xaxis_title="Annual Salary (in thousands)" # customize axis label
    )
)
savefig(p, "p.html")
```

---
