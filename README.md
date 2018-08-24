
# My talk on Phaser
(My slides)[https://slides.com/jimb0b/deck-1]  
Delivered at the (First Time Speakers Event)[https://www.codecraftuk.org/events/2018/08/FirstTimeSpeakers] by CodeCraft at Skyscanner on 16/8/18  

Resources:  
The Phaser core can be forked (on GitHub)[https://github.com/photonstorm/phaser] and modified  
And (Phaser 2)[https://github.com/photonstorm/phaser-ce]   
http://phaser.io/
Phaser on (Wikipedia)[https://en.wikipedia.org/wiki/Phaser_(game_framework)]  
A little bit of (history)[http://phaser.io/phaser3/history]  
Steve Jobs’ (‘Thoughts On Flash’)[https://www.apple.com/hotnews/thoughts-on-flash/] blog post  
And (thoughts on those Thoughts)[https://www.kirupa.com/kirupa_dot_com_not_dead_simply_napping.htm] from Kirupa (a once-popular site for Flash tutorials)  

(ImageMagick)[http://www.imagemagick.org/] a command line image editing tool  
My (brief guide)[https://github.com/L3gomancer/ImageMagickQuickGuide] to ImageMagick  
(Tiled)[https://www.mapeditor.org/] lets you ‘draw’ with repeating tiles and spits out JSON  

Phaser Games:  
(Road Of Fury: Desert Strike)[http://gamedistribution.com/games/road-of-fury-desert-strike]  
(Meiji)[https://l3gomancer.github.io/meije/]  
My fork of the (Mario demo)[https://l3gomancer.github.io/PhaserDudeMarioExample/]  
And the (particle demo)[https://l3gomancer.github.io/PhasParticle/]  

Some Non-Phaser Web Games I Like:  
(A Grain Of Truth)[http://www.rudowscy.com/agot/] adventure  
(Browser Quest)[https://browserquest.mozilla.org] 2D mutliplayer with WebSockets  
(A Dark Room)[https://adarkroom.doublespeakgames.com]  
(slither.io)[https://slither.io]  
(agar.io)[https://agar.io]  


Talk Content:
[slide 1]
Hello I'm the last speaker of this event so I'll talk quickly so we can all head to the bar.
I’m Ed, a student of computer science 
[GCC plug]
and organiser of a computer meetup the Glasgow Coder Collective, a welcoming array of technology enthusiasts of various backgrounds that help each other with projects or motivation with courses. We also host tech talks. Recently we were lucky enough to have a workshop on Heroku with the developers of Heroku.

[phaser]
So what’s phaser?
[a phaser]
A phaser is a Starfleet-issued side-arm for repelling boarding parties ...ok ok, you came for a technical talk so here it is
[a phaser’s innards]
...sorry I’m a Trekkie.
[a guilty Cptn Picard]

[Real Phaser logo]
Phaser is actually a JavaScript framework for making web games
It uses the <canvas> HTML5 tag. It can also use WebGL to take advantage of GPU acceleration but it will gracefully fall back to canvas if the browser doesn’t support it.

[A Brief History Of Wasting Time]
[screenshot the first browser]
The internet was never really intended as a platform for games. When the first HTML browser was made by a particle physicist it was intended for transferring academic documents between scientific institutions and universities.
[Java Runtime Environment loading...]
So if HTML wasn’t enough for rich media what do you do? One answer was plugins like Java. The problem was it was slow to load, had limited capabilities, and if it crashed you had to reload the page. It wasn’t really a web page anyway, it was like a window onto an application already installed on your machine. If you want to experience what it was like back then just stare at this slide for 5mins.
[Flash and Flash Player]
Flash arrived, it was another plugin but had better compression and an accessible tool. Adobe bundled the Flash editor in the Creative Suite family. Animators liked the keyframes feature. Programmers liked ActionScript which was a lot like JavaScript. In fact you can port Flash games to Phaser. If you were in school around early 2000s you probably had a favourite toon or game. Anyone remember these?
[some popular Flash games and their hosting websites]
The reason I’m bothering to tell you this is to show there is a market and there are some established approaches to profit out of it either as a solo indie or a studio. Host on your own or join an aggregator etc.
But there’s still the problem of rampant plagiarism and copying which are the same problems of websites in general
[Jobs’s blog]
Steve Jobs blogged about his security concerns about Flash and then discontinued support on iOS which removed a popular device for web games

[Phaser logo]
And then there was Phaser! Phaser is a free JavaScript framework for making web games for desktop and mobile. Created by Photon Storm, made mostly in JavaScript and TypeScript.
Let's dive into the code!
[Code boilerplate]
3 main functions
Preload, to load assets
Create, to spawn and position sprites in the game scene or room or world
Update, to detect input and trigger behavior accordingly, or AI
In this example it's just preload and create since its a non-interactive demo for particles.
Often the JS would be in a file but here it's in a <script> tag.
Note the canvas dimensions at top. Site designers can get creative with matching the background to the game
[Czechoslovakian A Grain Of Truth]
Phaser tries to use WebGL or it happily falls back to Canvas based on browser support. The creator seems rather enamoured with the canvas element as there’s a quote hidden in the Phaser2 core
[Commented quote]
[blue text about particles]
A particle system is built-in, for explosions, streams, or attach an Emitter to a Sprite for a trail to follow it around. Let’s see a demo of that
[Code pre+create]
Just to point out at the top, you link it in in the head of your index.html or bundle it.
At the bottom in preload are the folder paths to our assets
And below the canvas dimensions is the physics engine, this one built in is Arcade Physics for common collision detection between sprites. The gravity value is the acceleration in pixels per second per second. The code is quite readable, right?
Other built in ones are Impact Physics for advanced tile support and Matter.js for polygon and 3d. There are more via plugins or add-ons. In fact the plugin market, along with support materials, is how the creator makes money.
[Particle demo in Chrome]
The final example demo on a local server in Chrome. It’s a sprite experiencing realtime physics, it bounces forever because it hits the ceiling.

[sprites]
That was a non-interactive example but you came here for games!
If you’re unfamiliar with games, this is a sprite sheet of the controllable character, one image holding all different poses and frames and picked out as needed. The green bar will be a platform, given a hitbox for collision
[Code]
Now we include the “update” function for the controls
Web devs will notice we override the browser vendor’s margins to 0, it’s still a normal website.
[more code]
In Preload the character is declared with frameWidth dimensions, this chops the spritesheet into chunks so that down here in Create we can loop through the frames and set a frame rate for the walk cycle
We also give collision to the boundaries of the world to keep the player inbounds
[yet more code]
This gives the item sprites physics, and makes them despawn when its hitbox overlaps with the player’s, and it is called with the “disableBody” function below. Clearly this could be for collectables.
Update is for frequently updated behaviours like the player’s jump mechanics. It instantly assigns the player with an upward vector and then just lets gravity bring it down. ‘Proper’ Mario jumping would have a ‘sideways gravity’ instead of instantly changing direction mid-air. You can set it to a keyboard key press, mouse, peripheral for gamepads, or touch for mobile devices.
[finished game]

[list of game frameworks]
There are a lot of game frameworks out there, So why Phaser?
You’re probably thinking “Wow Edward, you must have a comprehensive process to compare the every framework and weigh up the advantages, right?” You would be correct.
[bulleted list]
Here’s a list of things I consider when picking a new tool: the name
...that’s it
[tools]
Other tools I chose with this methodology:
Firefox sounds like a flaming fox
Cyberduck is an FTP client
Kraken is a Git client. I shout “release the Kraken” every time push to GH. It’s in the docs.

[Tut list]
Phaser has plenty of tutorials and resources online
[the dev’s account]
And a nice community in the forums. In fact sometimes the creator Richard Davey shows up and personally answers the questions of random 12yos.

[The Witcher]
In conclusion I hope you can use this to make something you are proud of. Almost proud as Poland, for example! Poland is so proud of their game industry that when then-president Obama went on a state visit he was given a copy of The Witcher 3 for Xbox 360.
Which is daft if you ask me. Everybody knows he’s a PC gamer

[Another GCC plug. You’re welcome ;) ]
