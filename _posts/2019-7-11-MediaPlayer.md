---
layout: post
title: (Under contruction) MediaPlayer
tags : [Nugets, Xamarin.Forms]
---
## A cross platform media player lib ...       
Based on ideas and code of [martijn00](https://github.com/martijn00) ( https://github.com/martijn00/XamarinMediaManager )

MediaPlayer is basically a clone of martijn00s XamarinMediaManager. It started all when I tried to contribute to this project.    
  
Any media player is a quite complex project and martijn00 is a quite sophisticated developer. Whereas my first steps went well, I was quickly struggling with the project structure and implementation. When I saw that I took more time analyzing the project than developing features I started thinking about this re-implementation…    

Doing so I finally I understand many of the tricks hidden in martijn00s project.  
   
So, I didn’t reinvent the wheel, I disassembled and reassembled it 😉
  
It started as an experiment, but it got a real project with its own new constraints ... Once again I struggle not only with the multi-platform MediaPlayer part, but managing the MSBuild.Sdk.Extras (one project - N platforms - one Nuget) exasperates me ...

[Continue on Github ...](https://github.com/ZeProgFactory/MediaPlayer)
