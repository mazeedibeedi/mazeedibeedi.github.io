---
layout: post
title: BlocJams
feature-img: "img/blocJams.png"
thumbnail-path: "img/blocJams.png"
short-description: Turn the music up!

---
## Summary
BlocJams is a digital music player similar to services like Spotify. It is a working music player for both desktop and mobile users, designed with responsiveness in mind.

## Explanation
BlocJams is the first front end project that I have worked on for Bloc. This project helped me to develop my HTML, CSS and Javascript skills and exposed me to technologies that many frontend developers use, such as AngularJs and JQuery. It also exposed me to the best practices that front end developers use e.g. file structure. This project has two versions; one built with JQuery, the other built with AngularJs

## Challenges faced with BlocJams

### Making the website responsive
One of the first challenges was how to make the website responsive to different kinds of devices with varying screen sizes. We had two problems to tackle:
1. How to display BlocJams in devices with small screens
2. How to display BlocJams in devices with large screens

#### Solution
Using CSS Media Queries, we were able to focus on styling for screens that were 640px and larger. For these small to medium sized devices, we used a grid system where we can set the the size of a certain HTML element to be a certain percentage of the viewport

Before
{:.center}
![]({{ site.baseurl }}/img/withoutmeta.png)

After
{:.center}
![]({{ site.baseurl }}/img/withmeta.png)

For larger devices, to prevent certain HTML elements from stretching, we introduced a max-width property of the HTML elements that would be affected by this.

Before
{:.center}
![]({{ site.baseurl }}/img/withoutmax.png)

After
{:.center}
![]({{ site.baseurl }}/img/blocJams.png)

### Going from Vanilla Javascript to JQuery
DOM Scripting was originally used for this project, and was used for providing BlocJams with it's functionalities. Features like dynamically showing the user the song list in an album and playing/pausing a song were done in Vanilla Javascript. 

{% highlight javascript %}
var setCurrentAlbum = function(album) {
     var albumTitle = document.getElementsByClassName('album-view-title')[0];
     var albumArtist = document.getElementsByClassName('album-view-artist')[0];
     var albumReleaseInfo = document.getElementsByClassName('album-view-release-info')[0];
     var albumImage = document.getElementsByClassName('album-cover-art')[0];
     var albumSongList = document.getElementsByClassName('album-view-song-list')[0];
     
     albumTitle.firstChild.nodeValue = album.title;
     albumArtist.firstChild.nodeValue = album.artist;
     albumReleaseInfo.firstChild.nodeValue = album.year + ' ' + album.label;
     albumImage.setAttribute('src', album.albumArtUrl);
     
     albumSongList.innerHTML = '';
     
    for (var i = 0; i < album.songs.length; i++) {
        albumSongList.innerHTML += createSongRow(i + 1, album.songs[i].title, album.songs[i].duration);
    }
};
{% endhighlight %}

#### Solution
Going with JQuery, it allowed for a much easier selecting of HTML elements without having to read long lines of code. Look at the example code below to see the difference between how the variable `setCurrentAlbum` when written in pure Javascript vs JQuery

{% highlight javascript %}
var setCurrentAlbum = function(album) {
    currentAlbum = album;
    var $albumTitle = $('.album-view-title');
    var $albumArtist = $('.album-view-artist');
    var $albumReleaseInfo = $('.album-view-release-info');
    var $albumImage = $('.album-cover-art');
    var $albumSongList = $('.album-view-song-list');
    
    $albumTitle.text(album.title);
    $albumArtist.text(album.artist);
    $albumReleaseInfo.text(album.year + ' ' + album.label);
    $albumImage.attr('src', album.albumArtUrl);
    
    $albumSongList.empty();
    
    for (var i = 0; i < album.songs.length; i++) {
        var $newRow = createSongRow(i + 1, album.songs[i].title, album.songs[i].duration);
        $albumSongList.append($newRow);
    }
};
{% endhighlight %}
### Going from JQuery to Angular
Moving from using JQuery to building an AngularJs project provided some interesting challenges and lessons learned. It taught me about the MVC framework that AngularJs uses, and taught me the difference between a library (JQuery) and a framework (AngularJs).

#### Solution
AngularJs provided many benefits in making developing websites simpler to read and understand. To illustrate this point, the code below shows how the next and previous buttons were designed in JQuery and in AngularJs

JQuery
{% highlight javascript %}
var $previousButton = $('.main-controls .previous');
var $nextButton = $('.main-controls .next');

$(document).ready(function() {
    setCurrentAlbum(albumPicasso);
    $previousButton.click(previousSong);
    $nextButton.click(nextSong);
});
{% endhighlight %}
AngularJs
{% highlight html %}
<div class="main-controls">
    <a class="previous" ng-click="previousSong()">
        <span class="ion-skip-backward"></span>
    </a>
    <a class="next" ng-click="nextSong()">
        <span class="ion-skip-forward"></span>
    </a>
</div>
{% endhighlight %}
The biggest difference to focus on is how AngularJs, directly provides functionality to an HTML element by being declared on the element itself in HTML. Whereas with JQuery, the element must be found first then assign functionality to it. 

## Conclusion
### What worked
The end result of the project is that BlocJams is a respsonve website, that plays music from the music files saved on the website and provides the user with the following functionalites:
1. Play/Pause song - either on the player bar or on the album view itself
1. Next/Previous song - provided on the player bar
1. Seekbar - provides the user with the ability to change at what point the song plays
1. Volume bar - provides the user with the ability to adjust the volume of a song to their liking.

### What didn't work
One of the issues I faced was being able to make sure that the volume is consistent when a new song is played. For example, if the volume is set at 60% it should be set to 60% throughout the whole time. 
Another issue I faced was being able to play a song when no song has been selected, i.e. when no song is playing or is paused

### What I learned from BlocJams
- How to make responsive websites
- How to add functionality to HTML elements e.g. play/pause
- How to structure HTML pages and style them with CSS
- How to structure a front end project
- Knowing your toolset i.e. strengths and weaknesses
- How to make dynamic websites using Javascript
- How to use Google Chrome's developer tools

### Looking forward
BlocJams taught me a lot about how websites are created. Having completed BlocJams, I have the knowledge to be able to work on my own projects for websites, and to be able to read and understand how other websites work.