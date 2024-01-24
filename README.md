# Fume Extractor

## Introduction:

I wanted to make a fume extractor for when I do soldering at my workbench. I had a few old (but unused) 40mm 12V fans lying around which I figured might make for a nice compact unit, so I went looking on Printables if someone already made something I could use. My requirements were pretty simple, to use the 2 fans I had, and to be rechargable using a lithium-ion battery from my collection.

I found a beautiful design on [Printables](https://www.printables.com/model/95088-ssak-fume-extractor) by mr Kamil Kaleta that seemed to tick all the boxes. Compact, good looking, (potentially) battery powered. However it seemed that aside from uploading the model the author had not added any instructions, interior images, specifications or anything. His own blog was offline, I found a [YouTube](https://www.youtube.com/watch?v=tM0-lobVyuU) video with some more angles of the finished product but also not much more information.

Since I liked the design so much I decided to fork this project so to speak and finish it up. This is the documentation for my interpretation of the project. All credits for the design go to [Kamil Kaleta](https://www.printables.com/@KamilKaleta), though I did make some modifications but only functional ones, nothing structural.

### Changes to original design:

It looks like the original design is meant to be used plugged in, using a barrel jack. I wanted it to be rechargable, fortunately there's a lot of free space in the interior to achieve this. Originally I wanted to use an 18650 battery but these are just slightly too long (and I had already finished printing the housing so too late to scale it up a bit). I ended up finding a compact 2000 mAh lithium cell in my collection that fit in the available space nicely.

So one of the changes was to change the existing cutout for a barrel jack connector into a cutout for a USB-C female connector. I also thinned out the back cover around this location a bit to make the particular board I used flush with the back of the unit. 

Another change was that I moved the hole for the potentiometer/on/off switch to be exactly in the center of the available space, so the potentiometer wouldn't be in the way on the inside. With the new potentiometer I ordered this was probably not necessary but during testing I was using a much bigger one.

Finally I modified the hole for the status LED. I don't know why it had such a long pipe on the original model, maybe he used a light pipe?
Anyway I changed it to make a press fit for a 3mm LED, that's just a bit below the surface when fully pressed in.

## Implementation:

### Electronics:

See the photo for an idea of how the electronics are connected. Pretty simple, a TP4056 Lithium charger board with USB-C port, connected to a 18650 battery holder (a lithium pouch cell is also possible and would take up less space, at the expense of capacity/runtime). This gives between 3 and 4.2 volts out depending on state of charge (when plugged in output is simply 4.2, not 5V). This is connected (with the positive wire passing through the switch part of the potentiometer) to a MT3608 boost converter that boosts up to 12V, but regulated with a potentiometer on the PCB. I desoldered this potentiometer, measured that it was 100 kilo Ohm and ordered some 5 pin (3 for the potentiometer, one for the switch at the 0 position) potentiometers, and soldered it to the boost converter with some wires. 
Now it regulates between 4-ish volts and the full 12V boost. Then finally 2 40mm 12v fans in parallel connected to the boost regulator.


### Housing:

### Assembly:

## Bill of Materials:



