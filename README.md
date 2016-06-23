# bb-theme-archive-flex
Flexbox archive layout

Working on a archive page layout (something that has popped up here lately) where I wanted a random sort of masonry layout.
Rather than writing a new php template, I decided to see if I could do it with nothing but CSS and this is what I cam up with.
This is the standard BB Theme archive layout and all CSS and 1 line of jQuery.
Lets start with the customizer
The layout is set to 1100px wide
The blog layout is set to no sidebar
The arvhive layout is set to image besides posts
The jQuery is easy and can be ommitted (or css used)
I added the class 'well' to the article.
jQuery( document ).ready( function($){
$('.home article').addClass('well');
});
Now I only wanted to target the home page so I prefixed everything with the home class. Well is a bootstrap class that gives it that sunken look with the background and border etc around each post
Now for the css
The first thing was to assign flex to the container (if you do not know what flex is, put it on your priority to learn list)
.home .fl-content {
display: -webkit-box;
display: -webkit-flex;
display: -ms-flexbox;
display: flex;
flex-direction: row;
flex-wrap: wrap;
justify-content: space-between;
}
The next is the articles, I want to set the width
.home .fl-content article {
width: 30%;
padding: 10px 20px;
margin: 5px;
flex-grow: 1;
}
As you can see I gave each article some padding and room to move with margins as well as a 30% width.
You can also see the flex-grow, this ensures the article takes up 1 column.
Now I wanted to increase some widths of random articles
.home .fl-content article:nth-child(1),
.home .fl-content article:nth-child(4),
.home .fl-content article:nth-child(6){
width: 50%;
}
So you can see I chose the 1st, 4th and 6th articles to give a width of 50%
Looking at it on mobile, 50% width posts looks squashed and awful, so lets fix that with some media queries. Everything looks ok from 768px and up, so I targeted screens below that and made them 100% width
@media screen and (max-width: 767px) {
.home .fl-content article {
width: 100%;
}
}
The final step was to make sure the next and prev posts were at the bottom of the page as these were being affected by the flex-box, so this was an easy fix
.home .fl-archive-nav {
width: 100%;
}
And that is it, the result is a nice responsive masonry style gridded layout on the home page with it set to latest posts.
