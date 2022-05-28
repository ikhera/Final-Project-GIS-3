# Mapping the Predominent Non-English Language in each Chicago Neighborhood


# [My StoryMap](https://uploads.knightlab.com/storymapjs/9d951daa95ba43a5949a57c4e7827f90/a-linguistic-history-of-chicago/index.html)


## Research Question 1: How does the predominant non English language change over Chicago's community areas?  


### According to 2015 Census Data, 15.7% of Chicago's population does not speak English as their predominant language - approximately 400,000 residents. I came upon a data set from the Chicago Data Portal that provides the predominent non English language spoken in each of Chicago's 77 community areas, and I knew I wanted to work with it for this project. My parents are both immigrants, and immigration history and language history are both of great personal interest to me.  

### I am currently interning for WBEZ, and I will be staying on there after college to work as a climate reporter. My work in journalism has made me absolutely fascinated by the interplay between storytelling, history and spatial data. My projects in previous quarters of this class have been very focused on data and data analysis, and this quarter, I wanted to push myself to incorporate an anecdotal aspect to my work. I was particularly impacted by our Week 4 readings on Feminist Data Visualization. I firmly believe that while spatial data analysis is incredibly powerful, we also have a responsibility to convey and embrace the socio-cultural contexts of our maps. I identified neighborhoods of interest from my map, each with unique predominenet non English languages, and did research about the history of that language and its speakers within the community area.

<img width="1437" alt="Language Map" src="https://user-images.githubusercontent.com/70248566/170409302-e4e366f9-a7db-450a-a084-f283c3f8af73.png">

### This is the map I made with tmap in R. It displays the predominant non-English language in each of Chicago's community areas.

### My data was sourced from the Chicago Data Portal, and spans the years 2008-2012. It is linked [here](https://data.cityofchicago.org/Health-Human-Services/Census-Data-Languages-spoken-in-Chicago-2008-2012/a2fk-ec6q).

### The map displays some fascinating geographic language trends. Chinese is spoken predominantly The Loop, Near South Side, Armour Square, Douglas, Bridgeport and Hyde Park. Polish is predominant on the far Northwest side of the city, in areas like Jefferson Park and O'Hare. African Languages - which are not classified more specifically than that - are predominant in Avalon Park and Burnside. Spanish is predominant across most community areas.

### Once I had identified the spatial distribution of language, I started to incorporate the narrative aspect of this project. 


## Research Question 2: What historical and immigration trends contributed to the presence of a language within a community area? 


### The second, significant goal of this project was to incorporate the historical and narrative aspects of these linguistic trends. I wanted the user to be able to click through a history of distinct immigrant groups in Chicago and learn about their languages. I was particularly eager to use StoryMap for this purpose, as it is a tool designed specifically for journalists to engage with spatial data in a storytelling context. 

<img width="1306" alt="Screen Shot 2022-05-27 at 5 56 03 PM" src="https://user-images.githubusercontent.com/70248566/170798289-0a2e274d-0002-4012-8cd0-7dd10f839e73.png">


## Methods


### I used R to clean my data and create the map which would function as my basemap throughout the project. The link to my R Markdown is here. I have also included my code here. 


*Libraries*

library(sf)
library(tmap)

*Reading in Data from the Chicago Data Portal*

*Uploading the Community Area Shapefile*
  
  areas<-st_read("/cloud/project/GIS Final/Shape File/geo_export_9a2737c4-fc5a-4162-b9c2-0048bd7d4022.shp")

*Assigning the name "geoid" to the variable "area_numbe", which represents the community area number in the shapefile (Chicago has 77)*
 
  areas$geoid <-areas$area_numbe

*Uploading the Census Language Data csv File*
 
  languages<-read.csv("/cloud/project/GIS Final/Shape File/Languages 2.csv")

*Assigning the name "geoid" to the variable "Community.Area", which represents the community area number in the language data set (Chicago has 77)*
    
   languages$geoid<-languages$Community.Area

*Merging the Census Language Data csv with the Community Area Shapefile using the shared variable "geoid"*
    
merged<-merge(areas,languages,by="geoid") *merging by geoid, shared variable*
tmap_mode("view")

*Customizing my map using tmap*

tm_shape(merged)+ tm_fill("Language", palette = "Paired", title= "Predominant Non-English Language", alpha=0.6) +tm_scale_bar(color.dark="gray60")+tm_borders("black")+ tm_layout(main.title="Predominant Non-English Language in Chicago Neighborhoods")+tm_view(view.legend.position=c("right", "top"))


### A basic summary of my code: I merged the community areas shapefile with the languages csv by their shared variable of community area number (renamed as geoid). I then used the object "merged" to create a map. 

### Although cleaning my data in R was relatively straightforward, I ran into some significant troubles when I tried to extract the OSM Network and when I tried to upload my basemap. At this point in my methods section, I want to do a deep dive into my troubleshooting process and think about what I could have done differently. 

### My first challenge was to extract the OSM Network for Chicago and overlay it onto my map. The reason I wanted to do this was to basically ensure that when a viewer looked at my map, they didn't just zoom into a blob of color and could instead see actual streets! I closely followed the tutorial from class on extracting OSM networks, and was easily able to download the data for Chicago. However, every time I got to the next step of viewing/refining the data, I would get a fatal error message from R. 

### I switched my project over to RStudio Cloud in order to avoid running into this problem, but I still got the same message. I tried adjusting the amount of RAM used in my workspace and spent a good amount of time on RStudio Community, but couldn't figure out my problem. 

### As a second approach, I tried to use a shapefile of Building Footprints, because I figured that would be a little easier for me than using the OSM Networks directly. However, I also ran into significnat hurdles there. The .dbf portion of the shapefile would not upload into R Studio Cloud (I think the file was broken). 

### Finally, in order to make up for these shortcomings in a way I knew how, I decreased the alpha levels on my map so the basemap could be seen through the map. 


<img width="1151" alt="Screen Shot 2022-05-27 at 3 00 43 PM" src="https://user-images.githubusercontent.com/70248566/170798241-0d143883-403f-415f-b2b2-50bb64199e0a.png">


### In an ideal world, I would absolutely love to push myself to make a more challenging technical interactive map. I feel pretty silly I wasn't able to do this, and would love to continue working on this project in a capacity where I can dedicate time to it to troubleshoot more on the streets.

### My second big point of frustration in my project was working to upload my basemap into Knight Labs StoryMap. At first, I used Imgur to link a published image of my basemap into StoryMap. However, this gave me a series of blank tiles. I then decided to use Zoomify and Photoshop. Although Zoomify didn't work, I was ultimately able to download a Zoomable plug in for Photoshop that allowed me to create a "zoomable" version of my image. The idea here is to basically have a zoomable image your user can easily interact with. 

### Once I had my Zoomable image via photoshop, I downloaded Github onto my desktop, uploaded the folder into a new GitHub Repository, and then published the page to the web. Finally, I used the GitHub link to link my Zoomable Image into StoryMap. Frustratingly, however, my results looked like the screenshot below. There was absolutely a basemap of some type, it just wasn't displaying any of my work. 


<img width="1312" alt="Screen Shot 2022-05-27 at 4 47 20 PM" src="https://user-images.githubusercontent.com/70248566/170798308-00b68cee-5dfa-4717-8c1c-2d2ae6ce0465.png">


### If I had more time with this project, I would absolutely have worked to get my basemap to work on StoryMap. I felt so frustrated it didn't, and this is one of the biggest shortcomings of my project in my opinion. I ended up using one of StoryMap's own basemaps, which worked well, but I still wanted to use my own work. 

### There are several other places for improvement in this project. Firstly, I was frustrated by how old the data I was working with was. The set spans the four years between 2008 - 2012 - over 10 years ago. The age of the data means the map, although interesting, is not a current snapshot of languages in Chicago. I would love to entirely redo this project with an updated and recent data set, and would be curious to see whether it captured any recent migration trends. 

### Another source of frustration in this project was the lack of specificity around African Languages in the census data coupled with a lack of historical information on African immigrants in Chicago. This lead me to explore gaps in census data around particular immigrant groups and different organizations working to ensure the voices of African immigrants in Chicago are heard. 

### I would also love to replicate this project was the SECOND predominant non-English language in each neighborhood to try and grasp how different immigrant and ethnic groups are sharing the same geographic space. 


## StoryMap Highlights and Results

### I really enjoyed my experience of working with StoryMap. My map results followed anticipated historical trends based on my research. I was particularly excited by the two neighborhoods of African Languages which I was able to identify, since that move into the South Side has been relatively recent and many African immigrants still reside on the North Side. 

### StoryMap allowed for me to use images and text to tell the stories of each of these different places around the city. To make up for my lack of personalized basemap, I made sure to include my map as much as possible and to refer back to it often. 


<img width="1310" alt="Screen Shot 2022-05-28 at 10 05 27 AM" src="https://user-images.githubusercontent.com/70248566/170831411-1806d741-a9d0-4477-8eb1-2ef1d6b6c583.png">

<img width="1436" alt="Screen Shot 2022-05-28 at 9 48 01 AM" src="https://user-images.githubusercontent.com/70248566/170831227-6c0fe171-add7-4006-9cc7-82cab207fc0d.png">

<img width="1312" alt="Screen Shot 2022-05-28 at 10 04 57 AM" src="https://user-images.githubusercontent.com/70248566/170831237-91d5c3c0-926c-4bc1-a709-c67be5cda6ac.png">

<img width="1310" alt="Screen Shot 2022-05-28 at 10 05 19 AM" src="https://user-images.githubusercontent.com/70248566/170831425-09eb8c3e-e9d2-4b7f-9abc-ec039a4a47b8.png">


### I also really liked StoryMap's ability to zoom in closer to a specific neighborhood / to adjust the zoom. This let me pull in to specific landmarks across the city, like the Pui Tak Center.

<img width="1309" alt="Screen Shot 2022-05-28 at 10 15 29 AM" src="https://user-images.githubusercontent.com/70248566/170831458-8ff34860-d473-4af1-bc40-985ed8c54b16.png">

### Overall, I thought the Knight Lab's StoryMap was a great choice for this lab. That being said, I think I would like to transition over to using ArcGIS StoryMap for the rest of my work and career, primarily because of all the difficulty I had with the image compatability. It would be great if StoryMap could exist within the same platform I was designing my map, instead of having to go through the frustrating process of image conversion. 

## Data and Sources


### In order to maximize the accessibility of this project, I have included all my data sources + research sources below. Feel free to dig around there if you want to see the data set OR learn more about Chicago's many languages and communities! 

[LVEJO](http://www.lvejo.org/)

[The Story of Little Village](https://interactive.wttw.com/chicago-by-l/neighborhoods/little-village)

[The Face of the Mexican Chicago](https://scalar.usc.edu/works/latino-metropolis-a-brief-urban-cultural-history-of-us-latinos---1/the-face-of-the-mexican-chicago)

[On Leong Merchant's Association Building](https://www.chicago.gov/content/dam/city/depts/zlup/Historic_Preservation/Publications/On_Leong_Merchants_Association_Building.pdf)

[Chicago's Historic Polish Language Newspapers](https://www.library.illinois.edu/illinoisnewspaperproject/chicagos-historic-polish-language-newspapers/)

[United African Organization](https://uniteafricans.org/about-uao/who-we-are)

[A Taste of West Africa on the South Side](https://southsideweekly.com/taste-west-africa-south-side/)

[Chicago Groups Preparing African Immigrants for the Census](https://www.wbez.org/stories/chicago-groups-preparing-african-immigrants-for-the-census/9a63f665-cfa9-4137-8a50-b11624a6a50a)

[Little Village Arch, Gateway To ‘The Mexican Capital Of The Midwest,’ Is Now An Official City Landmark](https://blockclubchicago.org/2022/01/26/little-village-arch-gateway-to-the-mexican-capital-of-the-midwest-is-now-an-official-city-landmark/)

[Creating a New Chinatown](https://americanhistory.si.edu/many-voices-exhibition/creating-community-chicago-and-los-angeles-1900%E2%80%931965/chicago/chinatown#:~:text=Chinese%20immigrants%20first%20settled%20in,the%20South%20Side%20in%201912.)

[African immigrants hope for a Chicago community of their own](https://www.chicagotribune.com/news/ct-xpm-2013-01-14-ct-met-african-immigration-20130114-story.html)

[The Story of Chicago’s Rise as a Distinctly Polish American City](https://news.wttw.com/2019/11/18/story-chicago-s-rise-distinctly-polish-american-city)

[Chicago Languages](https://www.chicago.gov/city/en/depts/mayor/supp_info/office-of-new-americans/language-access.html)

[Census Language Data Set](https://data.cityofchicago.org/Health-Human-Services/Census-Data-Languages-spoken-in-Chicago-2008-2012/a2fk-ec6q)

[Building Footprints Data Set](https://data.cityofchicago.org/Buildings/Building-Footprints-current-/hz9b-7nh8)









