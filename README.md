# ggplot Basics

## Libraries
```{r}
library(tidyverse)
library('palmerpenguins')
```

## Basic viz
```{r save your plot}
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g),color="purple")
```

## Common summary functions
```{r save your plot}
glimpse(penguins)
head(penguins)
colnames(penguins)
```

## documentation for geom_point
```{r save your plot}
?geom_point
```


## basic overlay graphic
```{r save your plot}
ggplot(data=penguins)+
  geom_smooth(mapping=aes(x=flipper_length_mm,y=body_mass_g,linetype=species))+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))
```

## jitter adds random noise to data, "easier to see points"
```{r save your plot}
ggplot(data=penguins)+
  geom_jitter(mapping=aes(x=flipper_length_mm,y=body_mass_g))
```


## basic bar graph
```{r save your plot}
ggplot(data=diamonds)+
  geom_bar(mapping=aes(x=clarity,fill=clarity))
```

## alternate code for overlaying graphics
```{r save your plot}
ggplot(data=penguins,aes(x=flipper_length_mm,y=body_mass_g))+
  geom_point()+
  geom_smooth()
```


## facet wraps basics
```{r save your plot}
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g, color=species))+
  facet_wrap(~species)
```


## diamonds facet wrap
```{r save your plot}
ggplot(data=diamonds)+
  geom_bar(mapping=aes(x=color,fill=cut))+
  facet_wrap(~cut)

ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))+
  facet_grid(sex~species)
```

# Labels

## add title, subtitle, caption
```{r save your plot}
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))+
  labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle = "Sample of three species", caption = "Data Collected by Dr. Kristen Gorman")+
  annotate("text",x= 220, y=3500,label="The Gentoos are the largest",color="purple", fontface="bold",size=4.5,angle=25)
```

## store plot as a variable
```{r save your plot}
p<- ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))+
  labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle = "Sample of three species", caption = "Data Collected by Dr. Kristen Gorman")

p+annotate("text",x= 220, y=3500,label="The Gentoos are the largest",color="blue")

```

# Saving visualizations
## Use export button in the plots tab
```{r save your plot}
ggsave("/R/Three Penguin Species.png")
```
