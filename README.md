# Chrome-Dino-Bot
A simple Python bot to automatically play the Chrome Dino game; made using OpenCV and PyAutoGui

Created in Ubuntu 20.04, but should be cross-compatible across most operating systems.

More so a proof-of-concept project to test OpenCV and template matching.

---

The script first reads the entire screen searching for the game's location.  
If the game location can't be found, the script stops.  
If it is found, the game starts two threads; the screen reading thread and the actions thread, giving the screen reading thread the x,y pos of the game location.

In the screen reading thread, the script reads in all the images under the `assets` folder and applies the Canny algorithm to each image for later template matching.  
With the templates and x, y pos of the game location, the screen is read in live and also converted to Canny.  
When the screen detects the read-in images under `assets` (aka the cacti and birds), it draws a border around the objects for visual purposes and sends a request to either Jump or Duck to the actions thread.  
The distance at which the dino jumps from the oncoming object is dependent on the time passed - as the game speeds up as time passes.
