# Fume Extractor

<img src="photos/IMG_4094.JPEG?raw=true" alt="Smoke test" title="Smoke test" width=60%>

## Introduction:

I wanted to make a fume extractor for when I do soldering at my workbench. I had a few old (but unused) 40mm 12V fans lying around which I figured might make for a nice compact unit, so I went looking on Printables if someone already made something I could use. My requirements were pretty simple, to use the 2 fans I had, and to be rechargable using a lithium-ion battery from my collection.

I found a beautiful design on [Printables](https://www.printables.com/model/95088-ssak-fume-extractor) by mr Kamil Kaleta that seemed to tick all the boxes. Compact, good looking, (potentially) battery powered.

<img src="photos/OriginalDesign.png?raw=true" alt="Original Design" title="Original Design" width=75%>

However it seemed that aside from uploading the model the author had not added any instructions, interior images, specifications or anything. His own blog was offline, I found a [YouTube](https://www.youtube.com/watch?v=tM0-lobVyuU) video with some more angles of the finished product but also not much more information.

Since I liked the design so much I decided to fork this project so to speak and finish it up. This is the documentation for my interpretation of the project. All credits for the design go to [Kamil Kaleta](https://www.printables.com/@KamilKaleta), though I did make some modifications but only functional ones, nothing structural.


### Changes to original design:

It looks like the original design is meant to be used plugged in, using a barrel jack. I wanted it to be rechargable, fortunately there's a lot of free space in the interior to achieve this. Originally I wanted to use an 18650 battery but these are just slightly too long (and I had already finished printing the housing so too late to scale it up a bit). I ended up finding a compact 2000 mAh lithium cell in my collection that fit in the available space nicely.

So one of the changes was to change the existing cutout for a barrel jack connector into a cutout for a USB-C female connector. I also thinned out the back cover around this location a bit to make the particular board I used flush with the back of the unit. 

Another change was that I moved the hole for the potentiometer/on/off switch to be exactly in the center of the available space, so the potentiometer wouldn't be in the way on the inside. With the new potentiometer I ordered this was probably not necessary but during testing I was using a much bigger one.

Finally I modified the hole for the status LED. I don't know why it had such a long pipe on the original model, maybe he used a light pipe?
Anyway I changed it to make a press fit for a 3mm LED, that's just a bit below the surface when fully pressed in.

I suppose another difference is I ignored the decorative patterns. Due to printing face down they are pretty much just swirls in the flat surface in my prints, the original designer seems to have either filled them with white filament in a dual color print or used epoxy or something to fill them in, but I don't really care.


## Implementation:


### Electronics:

<img src="photos/IMG_3793.JPEG?raw=true" alt="Electronics concept" title="Electronics concept" width=75%>

See the photo for an idea of how the electronics are connected. 

Pretty simple, a TP4056 Lithium charger board with USB-C port, connected to a 18650 battery holder. (which I later changed for a lithium pouch cell due to space limitations)
This gives between 3V and 4.2V out depending on state of charge (when plugged in the output of the charger board is simply 4.2V, not 5V). This is connected (with the positive wire passing through the switch part of the potentiometer) to a MT3608 boost converter that boosts up to 12V, controlled with a potentiometer on the PCB. I desoldered this potentiometer, measured that it was 100 kilo Ohm and ordered some 5 pin (3 for the potentiometer, one for the switch at the 0 position) potentiometers, and soldered it to the boost converter with some wires. 

A 3mm red LED with a 120ohm current limiting resistor is also connected via the potentiometer switch. This ensures that it will run on battery voltage and not on the 12V. Any difference in brightness between full and empty battery is not important. I also sanded down the top of the LED for a more frosted look but this is entirely personal preference. I might add a tiny drop of epoxy in the hole to act as a light pipe the next time I'm mixing some up for something else.

The boost regulator now regulates between 4-ish volts and the full 12V boost. For proper fume extracting anything less than 10 volt doesn't really do much, it's not strong enough, especially with the filter material also in the way.

Then finally 2x 40mm 12v fans in parallel connected to the boost regulator.


### Housing:

After making the above mentioned modifications I simply printed the parts in Black PLA+ with 50% infill (infill is mostly meaningless since the entire model is almost exclusively perimeters). The orientation is pretty obvious, there's only one way to print it all without requiring supports, everything face down. See the 3mf file for easy printing. If I made it again I might have reduced the layer height for a bit more smoothness but realistically it's a functional print, not a decorative one.

<img src="photos/IMG_4081.JPEG?raw=true" alt="Housing Printed" title="Housing Printed" width=75%>


### Assembly:

Fans are screwed in with some long M2 screws and nuts and washers (since my fans had much too large mounting holes). 

<img src="photos/IMG_3843.JPEG?raw=true" alt="Fan mounting inside" title="Fan mounting inside" width=45%> <img src="photos/IMG_3844.JPEG?raw=true" alt="Fan mounting outside" title="Fan mounting outside" width=45%>

Potentiometer through the hole with nut and the knob on top. Hot glued the wires for security. The LED is pushed in the hole where it makes a friction fit. Then after connecting the wires (122ohm resistor is a 100+22ohm in series) it's also hot glued in place.

<img src="photos/Potentiometer.png?raw=true" alt="Potentiometer mounting" title="Potentiometer mounting" width=75%>

The USB-C charging board turned out to be almost perfectly sized but as I wanted it to be perfectly flush I mounted it a tiny bit away from the back wall (not really necessary, just like the look of it better this way). It's hot glued in there, since it pushed straight against the front of the main body all insertion force is directed that way. Only when unplugging the cable it might put some stress on the glue connection but then likewise it should be pulling against the back cover. Time will tell if this is strong enough.

<img src="photos/USBCBoard.png?raw=true" alt="USB-C Charging board mounting" title="USB-C Charging board mounting" width=75%>

The Boost converter has no stress on it at all so it's just hot glued to the side where it's a bit out of the way. In hindsight I could have mounted it on the other side so it's in the airflow, so it would have cooling. If the inductor gets hot it might melt the hot glue, we'll see.

<img src="photos/BoostBoard.png?raw=true" alt="Boost Converter board mounting" title="Boost Converter board mounting" width=75%>

Finally the battery was connected via a connector, pushed in wherever there was some space left and fixed with a few dots of hot glue.

<img src="photos/IMG_4077.JPEG?raw=true" alt="Final inside view" title="Final inside view" width=75%>

Then the back cover is screwed in with 5 M2 countersunk allen bolts to close it up. Next I cut up some carbon filter to size and used another 4 M2 countersunk allen bolts to fix the filter housing to the rest of the unit.

<img src="photos/IMG_4079.JPEG?raw=true" alt="Assembled no filter" title="Assembled no filter" width=45%> <img src="photos/IMG_4083.JPEG?raw=true" alt="Assembled complete" title="Fan mounting outside" width=45%>


## Bill of Materials:

- about 75 grams of PLA(+) 
- a smattering of M2 screws and possibly some nuts 
- about 1 stick of hot glue 
- 2 40mm 12VDC fans 
- TP4056 USB-C Charger 
- MT3608 Boost Converter 
- 100Kohm 5 pin potentiometer 
- 2000 mAh Lithium cell 
- some wires and a battery connector 
- red 3mm LED 
- 100 ohm resistor 
- 22 ohm resistor 
- Activated carbon filter material 

