---
layout: post
title:  "Perspective Grid Maker"
---

I was looking for a tool to generate perspective grids that maintained the correct grid spacing throughout the whole scene. As far as I could tell there wasn't any software that made this easy to do. Below demonstrates the issue, the grid lines on the left get distorted as they move into the background, however the right grid maintains the correct spacing: 

![image tooltip here](/assets/perspective-grid-maker/comp1.png){: width="40%" }
![image tooltip here](/assets/perspective-grid-maker/comp2.png){: width="40%" }

Since I couldn't find anything that produced grids like the one on the right, I decided to make my own in Godot. I figured I'd keep an option to generate grids like the one on the left since it's nice to drag around vanishing points. After a few weeks working on it I'd come up with a handy little tool. Below shows the 2D mode.

![image tooltip here](/assets/perspective-grid-maker/2d.gif)

The easiest way to achieve consistent grid spacing was to allow the user to rotate a 3D environment. This meant that I could just take advantage of the [Godot] engine - it's already done all the math for 3D perspective. Both 2D mode and 3D mode output PNG images for each grid layer.

![image tooltip here](/assets/perspective-grid-maker/3d1.gif)

I included a feature that allows you to import a background image to use as reference: 

![image tooltip here](/assets/perspective-grid-maker/background.gif)

There's also an option to enable a fisheye lens effect. I used [**this**](https://github.com/Cykyrios/Godot360) code for the effect - it was super easy to implement.

![image tooltip here](/assets/perspective-grid-maker/3d.gif)

Here's a little demo of the tool: 

<div style="text-align: center">
<iframe style="max-width: 100%" width="560" height="315" src="https://www.youtube.com/embed/4bTAgUpmppw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div> 

Here's a drawing I did using a perspective grid generated with the app. 

![image tooltip here](/assets/perspective-grid-maker/drawing1.png)

At some point I'd like to add 4-point perspective in addition to the 2, 3 and 5-point options. Another nice feature would be to somehow work out how to convert a grid made in 2D mode to a 3D environment and vise versa since it'd be cool to just drag around vanishing points and still have non distorted grids. Anyway, for now you can try out a demo of the tool [**here**](https://haztro.itch.io/perspective-grid-maker):  enjoy :)

<iframe style="max-width: 100%" frameborder="0" src="https://itch.io/embed/795356" width="552" height="167"><a href="https://haztro.itch.io/perspective-grid-maker">Perspective Grid Maker by haztro</a></iframe>
