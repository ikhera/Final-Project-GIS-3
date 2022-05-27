# Mapping the Predominent Non-English Language in each Chicago Neighborhood**


### According to 2015 Census Data, 15.7% of Chicago's population does not speak English as their predominant language - approximately 400,000 residents. Spanish is the largest non English predomminant language spoken in the city, followed by Mandarin and Polish. I wanted to use the skills I gained this quarter to explore the distribution of these non English languages spatially, across Chicago. I used a data set from the Chicago Data Portal that provides the predominent non English language spoken in each of Chicago's 77 community areas. 


## Research Question 1: How does the predominant non English change over Chicago's community areas?  


### I am currently interning for WBEZ, and I will be staying on there after college to work as a climate reporter. My work in journalism has made me absolutely fascinated by the interplay between storytelling, history and spatial data. My projects in previous quarters of this class have been very focused on data and data analysis, and this quarter, I wanted to push myself to incorporate an anecdotal aspect to my work. I was particularly impacted by our Week 4 readings on Feminist Data Visualization. I firmly believe that while spatial data analysis is incredibly powerful, we also have a responsibility to convey and embrace the socio-cultural contexts of our maps. I identified neighborhoods of interest from my map, each with unique predominenet non English languages, and did research about the history of that language and its speakers within the community area.

<img width="1437" alt="Language Map" src="https://user-images.githubusercontent.com/70248566/170409302-e4e366f9-a7db-450a-a084-f283c3f8af73.png">

### This is the map I made with tmap in R. It displays the predominant non-English language in each of Chicago's community areas.

### My data was sourced from the Chicago Data Portal, and spans the years 2008-2012. It is linked [here](https://data.cityofchicago.org/Health-Human-Services/Census-Data-Languages-spoken-in-Chicago-2008-2012/a2fk-ec6q).

### The map displays some fascinating geographic language trends. Chinese is spoken predominantly The Loop, Near South Side, Armour Square, Douglas, Bridgeport and Hyde Park. Polish is predominant on the far Northwest side of the city, in areas like Jefferson Park and O'Hare. African Languages - which are not classified more specifically than that - are predominant in Avalon Park and Burnside. Spanish is predominant across most community areas.


## Research Question 2: What historical and immigration trends contributed to the presence of a language within a community area? 


### The second, significant goal of this project was to incorporate the historical and narrative aspects of these linguistic trends. I wanted the user to be able to click through a history of distinct immigrant groups in Chicago and learn about their languages. I was particularly eager to use StoryMap for this purpose, as it is a tool designed specifically for journalists to engage with spatial data in a storytelling context. 

###IMAGE OF STOYRMAPSCREENSHOT

## MEHODS

### I used R to clean my data and create the map which would function as my basemap throughout the project. The link to my R Markdown is here. I have also included a screenshot of my code here. 


### Although cleaning my data in R was relatively straightforward, I ran into some significant troubles when I tried to extract the OSM Network and when I tried to upload my basemap. At this point, I figured the best thing to do would be a deep dive of my troubleshooting process. 

### My first challenge was to extract the OSM Network for Chicago and overlay it onto my map. The reason I wanted to do this was to basically ensure that when a viewer looked at my map, they didn't just zoom into a blob of color and could instead see actual streets! I closely followed the tutorial from class on extracting OSM networks, and was easily able to download the data for Chicago. However, every time I got to the next step of viewing/refining the data, I would get a fatal error message from R. 

### I switched my project over to RStudio Cloud in order to avoid running into this problem, but I still got the same message. In an ideal world, I would have loved to pull in these road networks to enhance my map and make it more interactive and accessible. 

### I then tried to use a shapefile of Building Footprints, because I figured that would be a little easier for me than using the OSM Networks directly. However, I also ran into significnat hurdles there. The .dbf portion of the shapefile would not upload into R Studio Cloud (I think the file was broken). 

### In order to make up for this in a way I knew how, I decreased the alpha levels on my map so the basemap could be seen through the map. 

### In an ideal world, I would absolutely love to push myself to make a more challenging technical interactive map. I feel pretty silly I wasn't able to do this. 

!(https://65d97f8628714969b21691d28b1dc164.app.rstudio.cloud/file_show?path=%2Fcloud%2Fproject%2Fmmm.html)


### My second big point of frustration in my project was working to upload my basemap into Knight Labs StoryMap. At first, I used Imgur to link a published image of my basemap into StoryMap. However, this gave me a series of blank tiles. I then decided to use Zoomify and Photoshop. Although Zoomify didn't work, I was able to download a Zoomable plug in for Photoshop that allowed me to create a "zoomable" version of my image. The idea here is to basically have a zoomable image your user can easily interact with. 

### Once I had my Zoomable image via photoshop, I downloaded Github onto my desktop, uploaded the folder into a new GitHub Repository, and then published the page to the web. Finally, I used the GitHub link to link my Zoomable Image into StoryMap. Frustratingly, however, my results looked like the screenshot below. There was absolutely a basemap of some type, it just wasn't displaying any of my work. 

## Code Screenshot

### If I had more time with this project, I would absolutely have gotten my basemap to work on StoryMap. I felt so frustrated it didn't, and this is one of the biggest shortcomings of my project in my opinion. 

### There are several other places for improvement in this project. I was frustrated by how old the data I was working with was. The set spans the four years between 2008 - 2012 - over 10 years ago. The age of the data means the map, although interesting, is not a current snapshot of languages in Chicago. I would love to entirely redo this project with an updated and recent data set, and would be curious to see whether it captured any recent migration trends. If I had more time, I would also love to explor the OTHER non-English languages spoken in each neighborhood and see how their distribution might shed insight on different communities. 

### I explore this more in my StoryMap file, but another source of frustration in this project was the lack of specificity around African Languages in the census data, coupled with a lack of historical information on African immigrants in Chicago. This lead me to explore gaps in census data and different organizations working to ensure the voices of African immigrants in Chicago are heard. 

### I would also love to replicate this project was the SECOND predominant non-English language in each neighborhood to try and grasp how different immigrant and ethnic groups are sharing the same geographic space. 


### In order to maximize the accessibility of this project, I have included all my data sources + research sources in the Data Folder. Feel free to dig around there if you want to see the data set OR learn more about Chicago's many languages and communities! 

