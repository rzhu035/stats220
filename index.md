# This is the meme I made by using [{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html#Installing_magick) package in R
![my_meme](https://user-images.githubusercontent.com/90770644/158389832-b55438eb-8116-4771-b950-aa7fb0f774ed.png)

*This bear on the left hand is the character from the geme "Genshin Impact" called "Guoba"*

## Here is the R code

```r

library(magick)

#get memes
happy_guoba <- image_read("https://i.pinimg.com/736x/fc/8a/f5/fc8af55a8765bf210af540f9a7f62deb.jpg")%>%
  image_scale("200")

shock_guoba <- image_read("https://static.wikia.nocookie.net/d820d769-61ed-4e73-9a90-4bb41db7ab5b/scale-to-width/755") %>%
  image_scale("200")
  
knife_guoba <- image_read("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSKVsIHN7UxuxlU6NyRREOtyZJ_7OVruvHeZQ&usqp=CAU") %>%
  image_scale("200") %>%
  image_noise()


#add text to memes
happy_text = image_blank(width = 200,
                         height = 200,
                         color = "#ffffff") %>%
  image_annotate(text = "First year in Compsci\nLearning python",
                 color = "#000000",
                 size = 16,
                 font = "Times",
                 gravity = "center")

shock_text = image_blank(width = 200,
                         height = 200,
                         color = "#ffffff") %>%
  image_annotate(text = "Second year in Compsci\nstaring at Java",
                 color = "#000000",
                 size = 16,
                 font = "Times",
                 gravity = "center")
knife_text = image_blank(width = 200,
                         height = 200,
                         color = "#ffffff") %>%
  image_annotate(text = "Third year in Compsci",
                 color = "#000000",
                 size = 16,
                 font = "Times",
                 location = "+20") %>%
  image_annotate(text = "Team programming", color = "red",size = 14, degrees = 15, location = "+50+110") %>%
  image_annotate(text = "Operating System", color = "red",size = 16, degrees = -15, location = "+75+90") %>%
  image_annotate(text = "Cycber security", color = "red",size = 15, degrees = -5, location = "+40+50")


first_row <- c(happy_guoba, happy_text) %>%
  image_append()
second_row <- c(shock_guoba, shock_text) %>%
  image_append()
third_row <- c(knife_guoba, knife_text) %>%
  image_append()

meme <- c(first_row, second_row, third_row) %>%
  image_append(stack = TRUE) %>%
  image_border("#000000", "10x10")

image_write(meme, "my_meme.png")

```
### Inspriation of my meme
1. This meme shows my 3 years study about compsci in UoA
    - The first year is very fun! We did a lot of interesting programs with Python which is chilllll 🙌
    - The second year became a little hard than previous year, java synatx is difficult than python 😱
    - Now I am in third year, these courses really freak me out! 😭
2. I really like the character "Guoba" from genshin, So I decided Let him express my feelings in this meme'
3. I add the noise effect and let the color of the text be red in third row to show my panic and irritable feelings. 


### The original meme
![](https://i.pinimg.com/736x/fc/8a/f5/fc8af55a8765bf210af540f9a7f62deb.jpg)
![](https://static.wikia.nocookie.net/d820d769-61ed-4e73-9a90-4bb41db7ab5b/scale-to-width/755)

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSKVsIHN7UxuxlU6NyRREOtyZJ_7OVruvHeZQ&usqp=CAU)
