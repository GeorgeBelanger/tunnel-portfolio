# Infinite Tubes

![Infinite Tubes with Three.js](https://tympanus.net/codrops/wp-content/uploads/2017/05/InfiniteTubesWithThreeJS_Featured.jpg)

A tunnel experiment in WebGL inspired by the effect seen on the [http://www.fornasetti.com/](Fornasetti) website. By [Louis Hoebregts](http://mamboleoo.be/).

[Article on Codrops](https://tympanus.net/codrops/?p=30954)

[Demo](https://tympanus.net/Development/InfiniteTubes/)

## Credits

- [Official Three.js website](https://threejs.org/)
- Brick texture is from [maxTextures](http://www.mb3d.co.uk/mb3d/Stone_and_Rock_Seamless_and_Tileable_High_Res_Textures.html)
- Perlin noise algorithm was written by [Seph Gentle](https://github.com/josephg/noisejs)
- Modern pattern with hand drawn stripes from [Freepik.com](http://www.freepik.com/index.php?goto=74&idfoto=934482)
- Blood cell model is from [Turbosquid](https://www.turbosquid.com/3d-models/free-blood-cell-3d-model/509576)

## License
This resource can be used freely if integrated or build upon in personal or commercial projects such as websites, web apps and web templates intended for sale. It is not allowed to take the resource "as-is" and sell it, redistribute, re-publish it, or sell "pluginized" versions of it. Free plugins built using this resource should have a visible mention and link to the original work. Always consider the licenses of all included libraries, scripts and images used.

## Misc

Follow Louis: [Twitter](https://twitter.com/Mamboleoo), [Codepen](http://codepen.io/Mamboleoo/), [LinkedIn](https://be.linkedin.com/in/louis-hoebregts-734aa1a8)

Follow Codrops: [Twitter](http://www.twitter.com/codrops), [Facebook](http://www.facebook.com/codrops), [Google+](https://plus.google.com/101095823814290637419), [GitHub](https://github.com/codrops), [Pinterest](http://www.pinterest.com/codrops/), [Instagram](https://www.instagram.com/codropsss/)


[© Codrops 2017](http://www.codrops.com)


# Dev Log
  
## 2/26/19 Tuesday 3:45pm Glickman
  - Today I am going to work on getting the tunnel portfolio site working
    - First thing I am going to do is copy the codepen into a folder and make a github repo
    - Deleted all text off the page and am just left with the canvas and links
    - The focus is going to be on index 2. Things I want to change:
      - 1. Change the original particles into screenshots of my projects
        - Tried https://threejs.org/docs/#api/en/textures/CubeTexture and got a shiny object that killed my render time
        - Tried https://github.com/abemID/threejstuts/blob/master/5-material-with-image.html but it said these methods were deprecated. 
      - 2. Make the particles clickable
      - 3. Change the texture of the tunnel
  - Now I see why I should have branches for projects even if I am working solo - The commits don't have to be as big. I can add just comments and such and only save the truly notable commits for master. 

## 2/27/19 Wednesday 5:45pm glickman
  - Working on portfolio again today
  - Also thought that I should make a photography website for Shunham. $100
  - Making branches now- Starting with clickable geom's
    - Going to get the click and or hover on box to work today. 
      - Not sure if I want to keep the original design or swtich to static cubes that hyperspace when you click them.
        - Starting with this tutorial https://soledadpenades.com/articles/three-js-tutorials/object-picking/
          - Got the cubes to light up red only on click. Now to get my frames to light up red on click in demo2
          - Got my frames to light up red only on click, but had some weird errors that came up
            | If I chose this.scene.children, the tunnel itself would light up and if I filtered the results inside of render, it still lit up the tunnel
              | If I chose this.particles, it said a.raycast was not a function because this.particles only has the speed data whereas children has all physics data
                @ Inside of the add particles function, I set allParticles = this.scene.children.filter(child => child.type == "Mesh")
            | If the mouse is hovering over a frame when it spawns, it becomes red
            | Also note that the ray goes all the way through the scene and can possibly tag multiple frames.
              @ Got it to click only the closest frame by removing the iterator and choosing intersects[0]
                - Could possibly be done better by chosing intersectObject with no 's' 
            - All the particles are recycled - If I click them all red all the new ones will be red as well. This can be fine. 
            - The particles are hard to click because they move with the mouse and the tunnel. 

## 3/3/19 Sunday 7:30pm home
  - Just gonna do a quick 20 minutes(actually spent 1 hour) tonight to try and get an image as a surface for my frames.
    - The progression and branches for the next phases of development will be:
      1. Get image on surface
      2. Get click to go to a link
      3. Build my object table
      4. Get a nice hover effect
      5. Play with speed and placement of frames
      6. Get hyperspace to work
    - Used this guide https://discoverthreejs.com/book/1-first-steps/4-textures-intro/#_
    - Was able to map an image to all six sides of an object, but want to map 2 unique images to only 2 sides. 
      - The images are also sometimes upside down...

## 3/6/19 Wednesday 7:15pm home
  - Added a url change when objects are clicked. 
    - In tunnel.prototype.onclick, if the raycaster intersects something: `window.location.href='http://www.google.com/'` after 2000ms delay.