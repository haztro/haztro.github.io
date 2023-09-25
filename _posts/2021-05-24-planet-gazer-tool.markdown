---
layout: post
title:  "Planet Locating Tool"
---

I stumbled across [**this**](https://stjarnhimlen.se/comp/ppcomp.html) awesome website which describes a method for computing the position of the planets in our solar system. I thought it'd be fun to make a visualiser that, given a time and location, will show you where you need to look in the sky to see a specific planet. 

The indicator on the left shows which compass direction to face (the azimuth angle) and the indicator on the right shows how high up in the sky to look (the altitude angle). In this case, if you looked west and a bit above the horizon - that's where you'd find the planet. These indicators are found in the toolbar and will display information for whatever planet is selected. 

![image tooltip here](/assets/planet-gazer/compass.png)
![image tooltip here](/assets/planet-gazer/altitude.png)

Also included in the toolbar are a date and location panel for manually entering specific times and latitudes/longitudes. I also added the option to hide and show each planet. Here's a small demo:

![image tooltip here](/assets/planet-gazer/gif1.gif)

If you'd like to know how it works, all the code for this project is on [**Github**](https://github.com/haztro/planet-finder). The file "PlanetLocator.gd" contains all the functionality for computing planet positions/viewing angles. I've included a bunch of comments that hopefully make it somewhat clear as to what's going on. I won't go into much detail here since the site mentioned before is fairly thorough. Although, I will briefly outline the steps in the computation since I think it's useful to understand what's happening conceptually. 

1. Compute heliocentric ecliptic coords of planet

2. Compute the Sun's position relative to the earth 

3. Compute geocentric position of planet by adding Sun's position to planet's position

4. Convert planet's position to Azimuth and Altitude angles. 

Below shows what's going on in steps 1 to 3 visually. 

![image tooltip here](/assets/planet-gazer/explanation.gif)

You can see that when Mars and the Sun line up in panel 3, they more or less overlap in the main view and when Earth sits between them in panel 3, the main view shows them opposite one another. 

This was a fun project to work on and I learnt heaps about planetry theory. If you'd like to use the tool yourself it's available at [**itch.io**](https://haztro.itch.io/planet-gazer) (along with source code).

<br/>
<iframe frameborder="0" src="https://itch.io/embed/1055222" width="552" height="167"><a href="https://haztro.itch.io/planet-gazer">Planet Gazer by haztro</a></iframe>
<br/>