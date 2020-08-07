# 40VA-SINGLE-MOSFET-SSTC

if anyone would like to cooperate on the project or interrupt designs, have any questions or comments, feel free to contact me.

for more pictures and videos of the coil in action go to : https://www.instagram.com/waskalabs/


after posting some pictures of my completed design i have had quite a few people ask me for schematics / files / build info. the original intention of the design was to create a single pcb driver for any possible configuration of moderately low voltage transformer based tesla coils that i could use as a simple and quick platform for developing a variety of small desktop tesla coil designs and learn more about sstc operation. this design is a mixture of steve wards class e and mini sstc builds with some small modifications. for detials on the design go to (https://www.stevehv.4hv.org/sstc5.htm). i developed the v0 pcb design to be milled out at home using a pcb mill using a ~0.5mm endmill. you dont have to use a mill here - thats just what i designed the tolerances for. any method of diy pcb production should work. after developing and testing the driver i put together a small test coil, tuned everything, and had a relatively impressive mini coil in about a day. the v0 design has a well annotated schematic and pcb with descriptions and information that will hopefully be easy for the novice to understand and recreate. there are many online resources for understanding the general operation of sstcs so i will not be covering everyhting in detail here but only explaining the specs of my mini coil build here (links to more resources below).


the v1 pcb design has been made for proper pcb production and includes good high power pcb design, external interrputer pins, better wire connection points, and has been made to be configurable for use with raw mains power using an external transformer as the low voltage source. as of writing this the pcbs are currently in production and have not arrived yet. when they do i will be testing mains versions of the design.




# mini coil design specifications  (v0 pcb only):

secondary coil = ~ 5.5 inch 34awg secondary coil wound on 3.5 inch pvc ~ 430khz (also tested with a ~6.5" 395khz coil which gave even better results)

primary coil   = ~ 4.5 inch, 3 turns, 14 awg braided wire

transformer    = ul1585 24v 40va (white and black wires for 120v)

555 interrupt  = ~ 7 - 480hz

bus capacitors = 2 x 35v 22000uf caps

mosfet         = irfp460 (use for any high frequency coil)

after powering up the first coil and playing around with it a bit - it became immediately apparent that the 555 interrupter is not the way to go. i left it on the design as a simple way to get started - but i would not recommend it for continual use. the issue is the "on time" (time that the coil is powered up on each pulse) is much longer than necessary. the coil would ramp up and generate an arc, but would continue to burn away in continuous wave operation until being switched off by the low pulse of the 555. this can cause unnecessary strain on the mosfet, drains the bus caps, and also takes away from the aesthetic of the larger arcs. my solution to this was to remove the 555 chip and solder a 3 pin male to female dupont wire to the chip socket (interrupt, 12v, gnd pins) and run it into an arduino nano clone (pin 9, vin, gnd, respectively). the arduino should be programmed to give an on-time of between 1 - 5 milliseconds (i have stuck with 2 ms). i haave decided to add a potentiometer to vary the off time of the design to cycle between 2 - 1000 hz. the arduino tone library was also used successfully create audio output.

i will not be adding any more detail about the interrupter designs until the v1 pcbs are complete. once they are in and test coils are built i will be making various interrupter addons such as staccato mode, isolated audio input, multiple potentiometers for varied on and off times over a given range, etc. and will post finished developments here.



for more detailed explainations of sstc operation & design:

https://www.stevehv.4hv.org/sstcindex.htm

https://www.loneoceans.com/labs/#

http://kaizerpowerelectronics.dk/
