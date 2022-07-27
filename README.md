# Selcting-cases-and-subgroups-
### SELECTING CASES AND SUBGROUPS ###

# Load pacman, rio and tidyverse
pacman::p_load(pacman, rio, tidyverse)

### loading the data, making psychRegions as factor and renaming it as y

data <- import("StateData.xlsx") %>% as_tibble() %>% 
  select(state_code,region, psychRegions, instagram:modernDance) %>%
  mutate(psychRegions = as.factor(psychRegions)) %>% print()

View(data)

# FILTERING SINGLE VARIABLE  

### Filtering the facebook greater than 1. Remember facebook is a quantitative variable 
newdata <-data %>% filter(facebook > 1) %>% print()
view(newdata)

### Filtering all the states whose entrepreneur is less than 1. Remember entrepreneur is a quantitative variable 
newdata2 <-data %>% filter(entrepreneur < 1) %>% print()
view(newdata2)

### Filtering all states whose region is in the Northeast. Remember entrepreneur is a character variable
newdata3 <- data %>% filter(region == "Northeast") %>% print()
view(newdata3)

### Filtering all the states whose psychReion is Friendly and Conventioal 
newdata4 <- data %>% filter(psychRegions == "Friendly and Conventional")
view(newdata4)


# FILTERING MULTIPLE VARIABLES 

### Filtering all the states whose region is in the Northeast or psychRegions 
### is Friendly and Convnrtional. Remember or is a vertical pipe 

newdata5 <- data %>% filter(region == "Northeast" | psychRegions == "Friendly and Conventional")
view(newdata5)

### Filtering all the states whose region is in the South and  retweet
### is less than 1. Remember and  is the uppersand &
newdata6 <- data %>% filter(region == "South" & retweet < 1)
view(newdata6)

### Filtering all the states whose region is not in the South and PsychRegions not
### Friendly and Conventional. Remember not is an exclamation sign 
newdata7 <- data %>% filter(!region == "South" & !psychRegions == "Friendly and Conventional")
view(newdata7)




