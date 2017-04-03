---
layout: post
title: BlocChat
feature-img: "img/username.png"
thumbnail-path: "img/blocChat.png"
short-description: BlocChat - Chat with your friends

---
## Summary
BlocChat is a simple real-time chat application built with AngularJs and Firebase

## Explanation
BlocChat is the first project I worked on for Bloc with little guidance, except for the wireframes and occassional lines of code. This is also the first project where I worked with Firebase and Bootstrap.

## Challenges faced with BlocChat
### Setting a username
Once a user enters the website, they are prompted to enter their username. If they return to the website using the same browser, their username will stay. Angular Cookies was used to save the username in a cookie given to a browser

{:.center}
![]({{ site.baseurl }}/img/username.png)

### Creating and selecting a chat room
A user can create a new chat room, where other users can send messages. Selecting the chat room will only display the messages for that chat. 

{:.center}
![]({{ site.baseurl }}/img/newchat.png)

{:.center}
![]({{ site.baseurl }}/img/chat.png)

### Creating a new message
A user can send messages to a chat room that they are currently in. The message will show the user that the message belongs to, and the timestamp of when the message was entered.

{:.center}
![]({{ site.baseurl }}/img/message.png)

{:.center}
![]({{ site.baseurl }}/img/realtime.png)

### Displaying it all in real-time
For this real-time chat to work all the information displayed to the user has to be shown in... well, real-time. We retrieved all the data saved on Firebase using the AngularFire module, which is then displayed on the browser using the ngRepeat directive on AngularJs. This was done for rooms and messages in rooms.

{:.center}
![]({{ site.baseurl }}/img/blocChat.png)

## Conclusion
### What worked
The results? BlocChat works as a real-time chat application where users can send messages to each other in the chat room there are in. It also remembers the user's username. Bootstrap modal works for letting the user enter their username and creating a new chat room.

### What didn't work
- The design and style of the website was rushed. It displays the correct information, but the website itself does not look user friendly. 
- Not having unique usernames
- Not having unique chat room names
### What I learned from BlocJams
- How to use Firebase with AngularJs projects
- How to use Bootstrap
- How to display messages and chats in real-time using ngRepeat
- Know the difference between Services and Controllers and when to use which

### Looking forward
With the BlocChat application finished, I can now use the knowledge learned to develop Angular projects with Firebase. I also have been exposed to Bootstrap and would be using it a lot more with my newer projects.