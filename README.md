# ggplot Basics

## Libraries
```{r}
library(tidyverse)
library('palmerpenguins')
```

## Basic viz
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g),color="purple")

## Common summary functions
glimpse(penguins)
head(penguins)
colnames(penguins)

#documentation for geom_point
?geom_point


#basic overlay graphic
ggplot(data=penguins)+
  geom_smooth(mapping=aes(x=flipper_length_mm,y=body_mass_g,linetype=species))+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))

#jitter adds random noise to data, "easier to see points"
ggplot(data=penguins)+
  geom_jitter(mapping=aes(x=flipper_length_mm,y=body_mass_g))


#basic bar graph
ggplot(data=diamonds)+
  geom_bar(mapping=aes(x=clarity,fill=clarity))

#alternate code for overlaying graphics
ggplot(data=penguins,aes(x=flipper_length_mm,y=body_mass_g))+
  geom_point()+
  geom_smooth()


#facet wraps basics
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g, color=species))+
  facet_wrap(~species)


#diamonds facet wrap
ggplot(data=diamonds)+
  geom_bar(mapping=aes(x=color,fill=cut))+
  facet_wrap(~cut)

ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))+
  facet_grid(sex~species)

#Labels

#add title, subtitle, caption
ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))+
  labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle = "Sample of three species", caption = "Data Collected by Dr. Kristen Gorman")+
  annotate("text",x= 220, y=3500,label="The Gentoos are the largest",color="purple", fontface="bold",size=4.5,angle=25)

#store plot as a variable
p<- ggplot(data=penguins)+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))+
  labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle = "Sample of three species", caption = "Data Collected by Dr. Kristen Gorman")

p+annotate("text",x= 220, y=3500,label="The Gentoos are the largest",color="blue")

#Saving visualizations
#Use export button in the plots tab

ggsave("/R/Three Penguin Species.png")
