# Data

Our [data](https://github.com/CSSEGISandData/COVID-19) is from Johns Hopkins university, and it's daily updated

---

---

# Correlation of Data

## ![Corr](correlation.png)

---

# Similarity and Dissimilarity of Data

## ![dis](distance.png)

---

# Skewness of Data

## 1- Calculating the skewness of Total Deaths for all the countries with **Rapidminer**

by plotting the number of death cases on the x axis and number of countries have the same number of cases on the y axis.

![Skewness](https://raw.githubusercontent.com/sudofix/COVID19/master/Skewness.png)
We can see that the data is positively skewed, which means that the majority of the countries have few dead cases
</br></br>

## 2- Calculating Skewness of Total Confirmed, Recovered, Deaths & Active Cases Data using **Python**

![skew](https://raw.githubusercontent.com/sudofix/COVID19/master/skew.png)

We can see that also (Total cases, Recovered cases, Active cases ) data is positivley skewed

---

---

# Progress of Infection

- Visualizing China's, Italy's, Iran's, Spain's & USA's Confirmed Cases Progress
  ![prog](https://raw.githubusercontent.com/sudofix/COVID19/master/China%2C_Iran%2C__Italy%2C_Spain_%26_USA_Progress.png)

---

---

# Data Boxplots

## ![box](Boxplots.png)

---

# Prediction

---

Tried to predict the expected number of COVID-19 ( confirmed - deaths - recovered ) cases in Egypt with two approches.

- Exponential curve equation</br>
- Logistic curve equation

The day which we will predict the number of cases on is May 25 2020.

Tools : R lang

## 1- Exponential curve fit

Here is the confirmed cases growth curve in Egypt
![Egypt_growth](https://raw.githubusercontent.com/Dodger23/EGYPT-19/master/images/25-5-2020/growth_curve.png)

We can see by just looking that the growth of number of cases in Egypt is an expoential grwoth. so we can try to find the closest exponential curve that fits into this curve and find what number will be on that curve on May 25.

Using exponential growth equation **alpha * exp(beta * t) + theta** and R model to find the optimal alpha, beta and theta to find the closest curve fits into the growth curve of Egypt.

```
#Fitting a model to find the optimum value of theta
  model.0 <- lm(log(Cases - c.0) ~ Date, data = df_t)

  # Finding optimum of alpha, beta and theta
  start <-
    list(a = exp(coef(model.0)[1]),
         b = coef(model.0)[2],
         c = c.0)
  model = nls(
    formula = Cases ~ a * exp(b * Date) + c ,
    data = df_t,
    start = start
  )

  # Storing alpha, beta and theta
  t = coef(model)

  p = t["a"] * (exp(t["b"] * x)) + t["c"]
```

The expected confirmed cases number on May 25 is about **21,000 case**

## ![fig1](https://raw.githubusercontent.com/Dodger23/EGYPT-19/master/images/25-5-2020/exponintial_confirmed_cases.png)

By trying the same on (death - recovered ) cases ...

the expected deaths cases number on May 25 is about **1000 cases**

## ![fig1](https://raw.githubusercontent.com/Dodger23/EGYPT-19/master/images/25-5-2020/exponintial_deaths_cases.png)

the expected recovered cases number on May 25 is about **4,500 cases**

## ![fig1](https://raw.githubusercontent.com/Dodger23/EGYPT-19/master/images/25-5-2020/exponintial_recovered_cases.png)

</br>
<hr>
</br>

## 2- Logistic curve equation

But there is no continuous exponential growth in real life, because eventualy we will reach a point where there will be so many infected people and less not infected people and the curve will start to slow until it falts when we reach the population,and here comes the logistic curve.

![logistic_curve](https://images.ctfassets.net/vrkkgjbn4fsk/3Bs14iW8ZG2KAGYYIC0aCa/b3c9016568775b92a1d3f91ef23e3523/8-growth-s-curve.png?q=90&w=3066)

Logistic curve equation is **N(d+1) = E * P * N(d)** where ...</br>

- **N(d+1)** : Number of cases in the next day </br>
- **E** : Average number of people someone infectedd is exposed to every day</br>
- **P = (1 - N(d) / Population)**: Probabilty of each exposure becoming an infection </br>
- **N(d)** : Number of cases in the current day</br>

and we can see the logistic curve depends mostly on the **E** and **P** which together they represent the **infection rate**, in the begining of the infection the **P** is high becuase (1- (1 / 98 420 000) ) = 0.9999</br>
We can run something like a simulation by adjusting the **E** and **P**.

So by starting from the current dat and by saying that the average number of people someone infected is exposed to every day is 7 we find that the number of confirmed cases on May 25 is about **25,000 cases**
and if it's 4 because of the quarntine the number is about \*_15,000_

![fig](https://raw.githubusercontent.com/Dodger23/EGYPT-19/master/images/25-5-2020/confirmed_infection_rate.png)

But by starting from the begining of the infection and by saying that the average number of people someone infected is exposed to each day is 7 before the quarntine and 2 after the quarntine.
The number of Actual cases on May 25 is about **150,000 cases**

![fig](https://raw.githubusercontent.com/Dodger23/EGYPT-19/master/images/25-5-2020/confirmed_infection_rate_from_start.png)

---

# Attributes Generation

---

---

# Discretization

---

---

# Text to Numerical

---

---

# Tracking Idea

---

---

# Decision Tree

---

---

# Naive Bayes Classification

---

---

# K-Means Clustering
