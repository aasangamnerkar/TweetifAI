# TweetifAI

Video: https://youtu.be/zfL9YdV8gfo

Other Files needed that were too big for github: https://drive.google.com/drive/folders/151fX9UDSpahmyh74wLXaZuOSQcxyfZUN?usp=sharing

Note: I said I used a custom algorithm in the video, but I reverted back to tweepy for the final version.

I am applying to the following categories at HackTheLib 2021:
- Best Overall
- Most Practical/Scalable
- Best Impact
- Best Original
- Best Design

## Inspiration
I got the main inspiration for this project from two catastrophes: the car crashing in Woodfield Mall and the Parkland Shooting in 2017. In both of these incidents, social media was much faster and more detailed in reports regarding what is happening inside the building than traditional authorities. While the police and news were reporting with vague, broad terms, platforms such as Snapchat and Twitter were posting live, real footage of the incidents. This got me thinking. If social media is such a valuable resource, why is it so underutilized for informing the general public? There are two reasons: the first is that it is hard to keep track of everything on social media by location. The second is that a lot of people just don’t have social media. I decided to try to solve these issues with my project.

## What it does 
I designed a bot that can tell you if your local area is having a disaster scenario based on Social Media activity. My app reads your location, takes tweets off of Twitter by your location with a custom filtering algorithm, and runs it through a State of the Art AI to determine the subject matter of the tweets. After isolating tweets identified as talking about some sort of disaster (earthquake, mass shooting, etc) with this method, the bot will post all your local disaster-related tweets to your phone/PC. If a threshold of x disaster-related tweets has been reached in a certain amount of time, it will send out a text notification with several keywords prevalent in these tweets to notify people that there is a disaster scenario going on.
 
## How I built it
The first step to build this project was creating the AI on Kaggle.com. I used the “Natural Language Processing with Disasters” competition and created a Recurrent Neural Network (LSTM) that was able to get 86% accuracy on the validation dataset. Some of the techniques utilized to create this model included GloVe vectorization, Tensorflow, Pandas, Keras, and Numpy. Next, I set up a script that could get tweets from Twitter via Tweepy. This script used a custom location filtering algorithm to filter tweets so that it is not loading hundreds of tweets at once. Next, I developed the website. I first created a static website template with HTML in notepad++, then created a flask server that I could deploy it with. After that, I made a few functions that could integrate the AI as a filter for tweets the bot is receiving. Next, I set Flask up to use the IP address the user logs in from as their location for the filter. After that, I added a function that utilizes Twilio for the bot to push text notifications to users. All that was left now was combining everything together. I incorporated all of the functions into one script and configured the app to run on the cloud with ngrok.

## Challenges I ran into
I ran into several challenges while developing this project. The most prevalent one, by far, was designing the code in a way that made it look good on both mobile phones and desktops. As you may have imagined, this was very difficult to do due to the large difference in resolution between a small phone screen and a large laptop screen. I had to take a lot of time to format the website correctly. Another major challenge I ran into was setting up the text notification system. Most APIs available on the internet cost money to send text messages, so I had to create a trial number on a very small library called Twilio that took a lot of digging to find. Since it was not very popular, whenever I ran into a bug I had to figure out how to resolve it by myself instead of trying to Google it, as there were sometimes no options on Google that discussed the bug I had encountered. Another thing I struggled with was the optimization process for the AI. I kept switching between optimizers such as Stochastic Gradient Descent, Nesterov, and other optimization functions for my model in order to achieve the best Accuracy. After waffling a little bit, I found Adam gave me the best accuracy in the shortest amount of time.

## Accomplishments that I'm proud of
One particular accomplishment I am proud of is the integration of state of the art AI. Separately, the AI, while sophisticated, can’t really do much. I was able to find a practical use for it that can aid people in their everyday lives. Another accomplishment I am proud of is the text integration. Due to my integration of text messages as notifications, people no longer have to constantly check a webpage/web app for updates. They can just keep their phone on them and, if it notifies them of a message, check it. This is more convenient for most people because they likely already do this. Furthermore, for those who don’t have social media, it is an effective way of keeping tabs on emergencies in their areas.

## What I learned
I learned a lot from this project. I learned how to use a computer to text your phone, how to use Recurrent Neural Networks to do Natural Language Processing, and how to use Flask as a frontend to make my own HTML pages work live. One particular skill I learned that stood out was using ngrok to run my flask server. With ngrok, I can run the server off of the cloud, making it easier for me to do testing on the same computer as it is not being flooded with requests. When I ran the server off my PC, it was difficult to debug the website because it was being incredibly slow every time I tried to open my IDE. It was sending requests incredibly fast, but I was unable to do anything but use it as a server. When I switched to running it off of the cloud, I was able to do these tasks simultaneously, thereby speeding up the process significantly. I was able to create a fully functioning website, web app, and text notification system within 3 days with these new skills. 

## What's next for TweetifAI
There are several features I wanted to add to this app that I didn’t get to. I wanted to add an email push notification option to this app, as I imagined it would work similarly to the texting system. However, when I looked it up, it looked like I would have to configure another server for email integration. I would also like to see if I could incorporate multiprocessing into the AI so that it can do predictions while simultaneously texting users at the same time. This type of multitasking could potentially speed up response times and, while the server responds fast right now, faster response times are always better.




