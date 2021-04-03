# onshape tutorial

This page is class notes for teaching a class on how to use OnShape CAD to make 3D objects, with a focus on making them 3D printable.


# get a free account
onshape free account for hobbyists (non-commercial): https://www.onshape.com/en/products/free

(you might need to turn off adblock for that link to work, for some reason)

NOTE: a free account cannot make private designs, only public ones. (just like github used to be)


# OnShape vs OpenSCAD
onshape is a professional cad package, whereas openscad is a toy.
* TODO make this sound a little bit less harsh to openscad


# general strategies for designing stuff
* usually you will start 2D (with a sketch) and then go 3D (with an extrude or revolve or something)
  * there are functions that can change existing 3D objects, but (unlike openscad), it is very uncommon to go directly to a 3D object.
  * E.g. there isn't a "make a cube" function, instead you would make a square in a sketch and extrude it into a cube

* if you go back and change something in a previous step, it will automatically recalculate the rest of the stuff so it is updated
  * or it might fail to do this, in which case, Ctrl-Z to undo lol
  * Also, for many functions, there is a "final" button you can click switch from looking at what you're currently editing to looking at the final product (after all the subsequent changes are applied). This is useful when e.g. you want to tweak a dimension until the final product "looks about right"

* Alt-C keyboard shortcut brings up a search box where you can search for functions (very useful)
* there's a keyboard shortcuts cheat sheet in the "?" help menu at the top right (very helpful)


# design activity: custom phone stand

## you will need
* OnShape account (see above)
  * it's probably best to have this ready before class
* phone (or similarly-sized object to put in the stand)
* ruler to measure phone (metric is preferable, millimeters is best)

## outer profile of the phone stand
* sketch on right face
* rectangle for the front
* slanted part for the back

## extrude the phone stand
* change "blind" to "symmetric" so that the stand stays in the middle of the work area (this will make things easier later)
* "Depth" should be width of phone plus a margin on either side
  * for my 80mm phone I did 100mm

## now make the phone itself
* mostly the same procedure as for the phone stand
* hide the phone stand so it's not in the way while you do this
* position the phone roughly where it should sit inside the stand
  * don't worry about tilting it back, we'll do that later
  * re-show the phone stand profile sketch (probably "Sketch 1") to make this easier
* extrude the phone as a **new** part, not as an addition to the existing thing
  * also, make it symmetric

## tilt the phone back a little
* use "transform" function to do this
  * select the phone part to transform
  * select "Rotate" from the drop-down
  * select one of the bottom edges of the phone part as the axis
* pick a good angle
  * probably like 10-40 degrees or so
  * if the angle is going the wrong direction, click the arrow next to it to reverse it

## cut out the phone from the phone stand
* use "boolean" to do this
  * select "subtract" tab
  * tool is the phone (the part that defines what shape we are cutting out)
  * target is the phone stand (what's going to be left when we are done)
* this will delete the phone part. If you want to keep that (e.g. so your CAD model looks more realistic), check the "keep tools" box

## go back and tweak the dimensions if anything doesn't look right
* if you go back and change something in a previous step, it will automatically recalculate the rest of the stuff so it is updated
  * or it might fail to do this, in which case, Ctrl-Z to undo lol

## add fillets and chamfers to make it look good
* fillet: rounded corner
* chamfer: cut off corner that is not rounded
* fillets look great in CAD pretty much everywhere
* but for 3D printing, you want to avoid fillets:
  * on the bottom edges (will mess up build plate adhesion)
  * on the top edges (won't look very good due to print resolution)
  * chamfers are good in these locations though


