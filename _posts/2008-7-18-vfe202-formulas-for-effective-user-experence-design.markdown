---
layout: post
title: vfe202-formulas-for-effective-user-experence-design
---
This sessions is being presented by Mark Miller from Developer Express,
and as most of you know (all 5 or 6 of my readers) I'm a big fan of
CodeRush which is a product from Developer Express.  This should be
quite an interesting presentation considering Mark's disgust for modal
dialogs!

* * * * *

Cost of Interaction
- Keystrokes
- Mouse travel distance and clicks
- Other input mechinisms
- Brain poser to drive the app
- Shifts in eye focus
 
Keystrokes
- Measured in keys press
 
Mark has created a cost of pressing keys.  Very impressive!  Letters are
a 1.0 and the more or less difficult they are to reach than letters he
raises and/or lowers the points.
 
Chorded keystrokes require more brain power to understand then finding
items in menus.
 
Showing mouse travel distance and click counts.  Showing the Exceptions
dialog box in VS.  Requires 3000 pixels in travel and 7 clicks.
 
Where are the hands?
- On the keyboard and/or mouse
      - HOme keys
      - home keys + extended navigation keys
      - home keys + numeric keypad
      - home keys + mouse
- Transitional cost
      - reaching for the mouse
      - returng hand to the keyboard
 
Brain power needed to run ui
- Distraction recover time
- emotional state / stress level caused by UI
- items that suck up valuable brain power
      - Distractions / visual noise
     - Awkward key combos
      - user mistakes
      - slideshow UI (having to recall what is behind a dialog box)
      - going to the help
      - searching for functionality
       - excessive / unnessecary steps
     - variance from the user model
     - orienterring costs
 
User Model
- It's what the user expects
- Ofthen there's a correspoinding object in the physical world to
establish precedence
- Sometimes computer history (Save buttons == floppy disk)
 
Sucking Brain power
- reduce the ability to focus
- lower productivity
- increase stress / tension
- provoke a negatve emotional response
     - Frustration -\> Rage
 
Gaze Shift
- the shift in eye angel required to spot the important information
- measured in degrees
      - a 17: monitor occupies about 28 degrees from top to bottom
      - \< 4 degrees are effortless
      - \> 8 degrees require visual scanning
      - on a 17" inch monitor running 1280 x 1024 a 6 degree cone has
diamter of about 220 pixels
 
Gaze shift problem areas
- Modal dialogs
    - meno on top, Ok at the bottom
    - Centered over app usually hides data
- Context menus
    - what happens when the most used item is on the bottom of the list?
 
Get this book
-Edward Tuft'es Visual Explainations: Images and Quantities, Evidence
and Narrative
 
Smallest Effective difference
- Don't go high contrast if you can go lower contrast
- just use what is needed
- Don't overdo it!
- Crank up the contrast a bit
     - LCD monitor quality varies significantly
     - Test on the crappiest display you can find
     - Tip: add a crappy display to your multiple monitor setup
 
Information in Parallel
- Serial
      - Evaluated over time
- Parallel
      - Evaulated instantly
      - Viewer controls pace
 
Noise
- Erodes productivity
- Hides important details
- Work to identify and suppress it
- People don't like noise and will ignore it.  If information looks like
noise people will do whatever they can to get rid of it (Close a dialog
box, find random buttons that will make it go away)
 
Contrast
- Eyes are attracted to great contrast
- Contrast should fit information relevance
    - Importan infomration should have high contrast
 
Color
- Work with a limited palette
- Pick two hues that work well together
      - Use these colors throughout the design
      - Add varations of these colors as needed
      - Don't change the hue, change saturation and lightness only
- Add a few other hues as accents
     - Use these sparingly
 
Color tips
- Use saturation like contrast
- offer users fewer color choices
      - offer preset palettes
      - Custom Controls
 
Shape
- In .NET use GraphicsPaths
      - Assign to Region, if it's a window
      - Paint, if you have a graphics object
- Opportunity to:
      - Create smaller footprints (custom forms)
      - Follow / simulate user models
      - Really screw up!!!!!!!!!!!! (just saw this on the powerpoint. 
made me laugh!! :D)
 
Opacity/Transparency
- \#1 Rule: Don't place semi-transparent text on top of text
- To break this rule:
     - Make transparent text larger
     - try rotating
- Vary transparancy over time for soft transition effects
- Adding transparency can soften high-contrast shapes with sharp edges
 
Shadow
- Great for floating UI elements
     - Set them apart from the data below
 
Size
- Just like contrast - relevant dat can be larger than less relevant
data
- Combine with low contrast
 
Motion / Animation
- Smallest effective difference rules apply here too
- Acceleration / deceleration are both good
- You can animate appearance / exit without motion (fade in / fade out)
 
 
Keybindings
- Distill commands into groups
     - Funcationally similiar commands
     - Funcationally opposite (toggle) commands
     - Focus on what the user wants to do not how
 
Use context to infer customer intent
 
Think about Key Binding on international keyboards, keys can be harder
to hit.
 
(some dude in front of me is paying his credit card bills online.  he
has quite the balance!)
 
Mouse travel
- Postion UI element \*closer\* to the mouse
- if a mouse click cause UI below it to move, move the mouse
- if you do it right, people don't even notice the mouse moved. 
 
(just showed a demo, and he's right.  You don't even notice.)
 
Mouse clicks
- Fewer is better
- Don't mess with user models
 
Where people are looking?
-Until eye gaze trackers become standard, we'll have to guess
- Eyes are focused on
   - Mouse, if moving
   - Somewhere in the selection if one exists
   - Caret, if visible
   - the keyboard, if entering text and not a touch typist
 
Directing gaze
- Motion
- Size
- Contrast
- Texture
- Depth
 
Lower brain power requirements
- Stop sucking and your customers will be happy! (lol)
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections),
[UX](http://technorati.com/tag/UX)
