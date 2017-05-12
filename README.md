# Divvy Bike usage in Chicago at July 1st

# Summary
This visualization explores where and when people use Divvy Bike at Chicago.

Divvy Bike is a bike rental company, they have 581 bike rental stations at Chicago. Customers can rent a bike from one station, and return in another station. Divvy bike 
shared their customers trip data with trip start and end time and station. 
In this case, I would like to find when and where customers would use their bike. The visualization result would help the campany to find potential stations and prepare bicycle capacity for each station.

Their dataset was upload quarterly[1],each day they had more than 10,000 trips log. I use the quarter 3 2016 dataset for analsysis, find the top 10 paths, different users behavior in each of a day and a day of week in this dataset. In the final explorative graph, after clean the wrong and meaningless data, summarize the data in same trip at same hour, there would be over 2,000 data each day. However, the Google map I used to animate the trips would be limited to 240 for selected day. So I just picked the July 1st, the first day of Quarter 3 to visualize. The final graph help viewers take a glimpse of when and where people would use a bike in a day. I use sql query to get all summarized data mentioned above. I also use python to convert that to bunble.csv and bunble_select.json file for bundle plot.

The visualization can help viewers find the where Divvy bike users would like to ride in Chicago, find at what time a day and what day of a week would customers and subscribers use divvy bike, and also gave an animation to combine all together in the final graph. In the final graph, viewers can find the start station, end station and path on the final bundle map, find where was each path on the map canvas and use button to select specific hour trip information as they wanted. 


# Design
In the first place, I wanted plot the station and path on a map using d3 geo. Although it is capable to plot the path from one station to another use straight line, it does not make sense since the data was recorded for bicycle ride. Then I tried to use Google Map API for the animation, since it contains bicycle ride mode for simulation. I wanted to use d3.js to plot station on maps[2], load the geo information and then use google api for the path animation[3]. 
## Chart type
There are two types in final chart, map and bundle. The goal of the project is to show viewers when and where people would use divvy bike. I use iteratively animate to solve the when and map to solve the where. However, since the final graph contains too much information, I have add bar chart to help viewers find the insight before the final graph, and use bundle graph to give the literal information.
## Visual encodings
I used the iframe with d3 to help viewers view the storyline more smoothly. 
Accordint to different case, I would resize the google map in different scale to highlight the information I would like to provide.
I used drak mode with blue paths to help viewers focus more on animation.  
I also used colorful bundles graph to help viewers identify important information.
## layout
To make it neat, all the page use boostrap to assign space. 
Most of the pages I used specific css file to customize the performance.
The iframe also provide a scroll bar for some page with too much information or too huge the graph.
## legends and hierarchy
Each page has a main title and a label to show what is the purpose of the graph and what conclusion we can get from the graph.
 

# Feedback
## Feedback1
The initial plot was plot in terrain mode, the background color was bright. I tried to plot the stations on red points with black margin, and use the automative colorful paths offered by google map api. The feedback from my friends is that is too colorful to focus on specific information provided. I change the code of backgound theme into dard mode, put those stations on white points and uniform the path on light blue. It is easier to find where people go after that.

## Feedback2
Even though Google Map Api provide geo information for each path, viewers need to use a mouse to find the specific start station and end station one by one. My friend suggested me to plot another graph for those information. I used the Bundle plot to show the start and end station names, links for selected hour and the others path[4].
It looks cool and it easier to understand.

## Feedback3
Both Map and Bundle are cool, however, since I used the buttom format in d3 visualization course[5], it seemed not well format in my friends view. I then used the Boostrap to change the web framework, and made it capable for mobile use.

## Feedback4 for Udacity review
I had add 4 more graphs to make it a story and make the final graph combine insights in new graphs. The fisrt chart help viewers find which paths was the most popular, the second help viewers compare local commutors and tourists favored paths, the third and fourth help viewers compare local commutors and tourists behaviors patterns in a day and a week. Combine all information we got, it is more easier to find insights in the last graph.
For the last graph, the rental stations on the bundle plot could be selected by splited the origin data into 24 small datasets, each time selected one dataset would help. However, that would be too redundant since I need to generate 24 new json files for bundle plot. Moreover, I would like to show all the relationship using the "red line" in the bundle plot. You can mouseover to select one of the nodes and see all related nodes connected with red line in this way. Otherwise, there is no need of bundle plot since parallel coordinates[6] can do the same jobs. I have also tried to interacting between the bundle and the graph, but the two graph use different format of data: bundle graph did not allow the blank or symbol "&" or "*". The name of stations contained all those symbols and blank. To do that, I need to cover part of the bundle function and write my own. In other words, it is capable to accomplish this function if I wanted to write my own d3 package, but the project's purpose is to use the d3 but not create a new one.  The buttons design leave the past selected not return to yellow since viewers might accidently re-push the former buttons even if they had already viewed that. It did not affect other function but it is misleading, I have changed. I considered cluster graph in the first place, however, the data I got just showed me the start and end staion, in other words, their are no hierarchy in this data. In this case, I did not pick the cluster graph.




# Resource
## 1. Divvy Data - Historical trip data available to the public: https//www.divvybikes.com/system-data
## 2. Google Maps + D3:
https://bl.ocks.org/mbostock/899711
## 3. How to make animated moving marker on Google map using javascript:
http://geekonjava.blogspot.com/2014/10/how-to-make-animated-moving-marker-on.html
## 4. Edge Bundling:
http://mbostock.github.io/d3/talk/20111116/bundle.html?1491414418356
## 5. D3 visualization - Delaying The Display Of Buttons
https://classroom.udacity.com/nanodegrees/nd002/parts/00213454010/modules/318423863275460/lessons/3066258748/concepts/31058087100923
## 6. parallel coordinates:
http://mbostock.github.io/d3/talk/20111116/#13




