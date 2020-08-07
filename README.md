# 40VA-SINGLE-MOSFET-SSTC

If anyone would like to cooperate on the project or interrupt designs, have any questions or comments, feel free to contact me.

For more pictures and videos of the coil in action go to : https://www.instagram.com/waskalabs/


After posting some pictures of my completed design I have had quite a few people ask me for schematics / files / build info. The original intention of the design was to create a single pcb driver for any possible configuration of moderately low voltage transformer based tesla coils that I could use as a simple and quick platform for developing a variety of small desktop tesla coil designs and learn more about sstc operation. This design is a mixture of steve wards class e and mini sstc builds with some small modifications. For detials on the design go to (https://www.stevehv.4hv.org/sstc5.htm).I developed the V0 pcb design to be milled out at home using a pcb mill using a ~0.5mm endmill. You dont have to use a mill here - thats just what I designed the tolerances for. Any method of diy pcb production should work. After developing and testing the driver I put together a small test coil, tuned everything, and had a relatively impressive mini coil in about a day. The V0 design has a well annotated schematic and pcb with descriptions and information that will hopefully be easy for the novice to understand and recreate. There are many online resources for understanding the general operation of SSTCs so I will not be covering everything in detail here but only explaining the specs of my mini coil build here (links to more general resources below).


The V1 pcb design has been designed for proper pcb production and includes good high power design, external interrputer pins, better wire connection points, and has been made to be configurable for use with raw mains power using an external transformer as the low voltage source. As of writing this the pcbs are currently in production and have not arrived yet. When they do I will be testing mains versions of the design as well as some modular addons I have come up with and will post the designs here.




# mini coil design specifications  (V0 pcb):

Secondary coil = ~ 5.5 inch 34awg secondary coil wound on 3.5 inch pvc ~ 430khz (also tested with a ~6.5" 395khz coil which gave even better results)

Primary coil   = ~ 4.5 inch, 3 turns, 14 awg braided wire

Transformer    = UL1585 24v 40va (white and black wires for 120v)

555 interrupt  = ~ 7 - 480hz

Bus capacitors = 2 x 35v 22000uf caps

Mosfet         = IRFP460 (use for any high frequency coil)

After powering up the first coil and playing around with it a bit - it became immediately apparent that the 555 interrupter is not the way to go. I left it on the design as a simple way to get started - but I would not recommend it for continual use. The issue is the "On time" (time that the coil is powered up on each pulse) is much longer than necessary. The coil would ramp up and generate an arc, but would continue to burn away in continuous wave operation until being switched off by the low pulse of the 555. This can cause unnecessary strain on the mosfet, drains the bus caps, and also takes away from the aesthetic of the larger arcs. My solution to this was to remove the 555 chip and solder a 3 pin male to female dupont wire to the chip socket (interrupt, 12v, gnd pins) and run it into an arduino nano clone (pin 9, vin, gnd, respectively). The arduino should be programmed to give an on-time of between 1 - 5 milliseconds (I have stuck with 2 ms). I haave decided to add a potentiometer to vary the off time of the design to cycle between 2 - 1000 hz. The arduino tone library was also used successfully create audio output.

I will not be adding any more detail about the interrupter designs until the V1 pcbs are complete. Once they are in and test coils are built I will be making various interrupter addons such as staccato mode, isolated audio input, multiple potentiometers for varied on and off times over a given range, etc. And will post finished developments here.

If you decided to use an atx power supply as a case like I did. Be sure to keep the primary coil atleast 1-2 inches away from the metal surface of the case as the steel will interfere with the coil and significantly reduce performance. I 3D printed a coil standoff for this


For more detailed explainations of sstc operation & design:

https://www.stevehv.4hv.org/sstcindex.htm

https://www.loneoceans.com/labs/#

http://kaizerpowerelectronics.dk/
