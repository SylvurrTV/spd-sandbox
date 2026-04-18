# Social Democracy: Sandbox
## Original Game
[Social Democracy](https://red-autumn.itch.io/social-democracy/)

## How To Use With Other Mods
---
(This tutorial will assume you know how to use Github Desktop and Github Pages, and also very basic html/js structure)

1. Find the repository of the mod you want to use, for example [Redux](https://github.com/CuttleCraft/social_democracy_redux/) and download it to your computer.
   
2. In those local files, go to /out/html/index.html and add the following at the end of the header-links div (use ctrl + f to find it):
```
<a onclick="window.showSandbox();" href="#">Sandbox</a>
```
  Feel free to change the page title or credit yourself (and also me) as mod authors if you know how to!

3. Go to /out/html/game.js, and after the "library" section, add this:
```
  window.showSandbox = function() {
      if (window.dendryUI.dendryEngine.state.sceneId.startsWith('sandbox')) {
          window.dendryUI.dendryEngine.goToScene('backSpecialScene');
      } else {
          window.dendryUI.dendryEngine.goToScene('sandbox');
      }
  };
```
4. Take /source/scenes/sandbox.scene.dry from this repository and add it to the same location in your local repo.
5. If you want to use the disable end date function, there are several .dry files that will need to be edited to make sure they check to see if the `end_disabled` variable is set to true (1) or false (0). In the following files, at the end of the "view-if:" row, add `and end_disabled != 1`. The files you must do this to are:
   * /source/scenes/events/1934_end.scene.dry
   * /source/scenes/events/death_of_hindenburg_normal.scene.dry

It's been a while since I added this, so if you find any files that I also added that to, please send a pull request to edit these docs!

7. If the mod you are using this with has different parties or completely different variables/scenes, you will have to edit the sandbox.scene.dry file to ensure it works correctly. I cannot you with that in this tutorial, it is up to you to learn.
8. When all of that is done, publish the entire local repository on github. You may need to link the Github workflow .yaml file to the Github Actions service, which will build a website for you. But first, in the repository settings, go to Pages and select your source as Github Actions. When all is done, it should work as a website!
