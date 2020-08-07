# 40VA-SINGLE-MOSFET-SSTC

# IF ANYONE WOULD LIKE TO COOPERATE ON THE PROJECT OR INTERRUPT DESIGNS, HAVE ANY QUESTIONS OR COMMENTS, FEEL FREE TO CONTACT ME.

# FOR MORE PICTURES AND VIDEOS OF THE COIL IN ACTION GO TO : https://www.instagram.com/waskalabs/


AFTER POSTING SOME PICTURES OF MY COMPLETED DESIGN I HAVE HAD QUITE A FEW PEOPLE ASK ME FOR SCHEMATICS / FILES / BUILD INFO. THE ORIGINAL INTENTION OF THE DESIGN WAS TO CREATE A SINGLE PCB DRIVER FOR ANY POSSIBLE CONFIGURATION OF MODERATELY LOW VOLTAGE TRANSFORMER BASED TESLA COILS THAT I COULD USE AS A SIMPLE AND QUICK PLATFORM FOR DEVELOPING A VARIETY OF SMALL DESKTOP TESLA COIL DESIGNS AND LEARN MORE ABOUT SSTC OPERATION. THIS DESIGN IS A MIXTURE OF STEVE WARDS CLASS E AND MINI SSTC BUILDS WITH SOME SMALL MODIFICATIONS. FOR DETIALS ON THE DESIGN GO TO (https://www.stevehv.4hv.org/SSTC5.htm). I DEVELOPED THE V0 PCB DESIGN TO BE MILLED OUT AT HOME USING A PCB MILL USING A ~0.5MM ENDMILL. YOU DONT HAVE TO USE A MILL HERE - THATS JUST WHAT I DESIGNED THE TOLERANCES FOR. ANY METHOD OF DIY PCB PRODUCTION SHOULD WORK. AFTER DEVELOPING AND TESTING THE DRIVER I PUT TOGETHER A SMALL TEST COIL, TUNED EVERYTHING, AND HAD A RELATIVELY IMPRESSIVE MINI COIL IN ABOUT A DAY. THE V0 DESIGN HAS A WELL ANNOTATED SCHEMATIC AND PCB WITH DESCRIPTIONS AND INFORMATION THAT WILL HOPEFULLY BE EASY FOR THE NOVICE TO UNDERSTAND AND RECREATE. THERE ARE MANY ONLINE RESOURCES FOR UNDERSTANDING THE GENERAL OPERATION OF SSTCS SO I WILL NOT BE COVERING EVERYHTING IN DETAIL HERE BUT ONLY EXPLAINING THE SPECS OF MY MINI COIL BUILD HERE (LINKS TO MORE RESOURCES BELOW).

THE V1 PCB DESIGN HAS BEEN MADE FOR PROPER PCB PRODUCTION AND INCLUDES GOOD HIGH POWER PCB DESIGN, EXTERNAL INTERRPUTER PINS, BETTER WIRE CONNECTION POINTS, AND HAS BEEN MADE TO BE CONFIGURABLE FOR USE WITH RAW MAINS POWER USING AN EXTERNAL TRANSFORMER AS THE LOW VOLTAGE SOURCE. AS OF WRITING THIS THE PCBS ARE CURRENTLY IN PRODUCTION AND HAVE NOT ARRIVED YET. WHEN THEY DO I WILL BE TESTING MAINS VERSIONS OF THE DESIGN.




# MINI COIL DESIGN SPECIFICATIONS  (V0 PCB ONLY):

SECONDARY COIL = ~ 5.5 INCH 34AWG SECONDARY COIL WOUND ON 3.5 INCH PVC ~ 430KHZ (ALSO TESTED WITH A ~6.5" 395KHZ COIL WHICH GAVE EVEN BETTER RESULTS)
PRIMARY COIL   = ~ 4.5 INCH, 3 TURNS, 14 AWG BRAIDED WIRE
TRANSFORMER    = UL1585 24V 40VA (WHITE AND BLACK WIRES FOR 120V)
555 INTERRUPT  = ~ 7 - 480HZ
BUS CAPACITORS = 2 X 35V 22000UF CAPS
MOSFET         = IRFP460 (USE FOR ANY HIGH FREQUENCY COIL)

AFTER POWERING UP THE FIRST COIL AND PLAYING AROUND WITH IT A BIT - IT BECAME IMMEDIATELY APPARENT THAT THE 555 INTERRUPTER IS NOT THE WAY TO GO. I LEFT IT ON THE DESIGN AS A SIMPLE WAY TO GET STARTED - BUT I WOULD NOT RECOMMEND IT FOR CONTINUAL USE. THE ISSUE IS THE "ON TIME" (TIME THAT THE COIL IS POWERED UP ON EACH PULSE) IS MUCH LONGER THAN NECESSARY. THE COIL WOULD RAMP UP AND GENERATE AN ARC, BUT WOULD CONTINUE TO BURN AWAY IN CONTINUOUS WAVE OPERATION UNTIL BEING SWITCHED OFF BY THE LOW PULSE OF THE 555. THIS CAN CAUSE UNNECESSARY STRAIN ON THE MOSFET, DRAINS THE BUS CAPS, AND ALSO TAKES AWAY FROM THE AESTHETIC OF THE LARGER ARCS. MY SOLUTION TO THIS WAS TO REMOVE THE 555 CHIP AND SOLDER A 3 PIN MALE TO FEMALE DUPONT WIRE TO THE CHIP SOCKET (INTERRUPT, 12V, GND PINS) AND RUN IT INTO AN ARDUINO NANO CLONE (PIN 9, VIN, GND, RESPECTIVELY). THE ARDUINO SHOULD BE PROGRAMMED TO GIVE AN ON-TIME OF BETWEEN 1 - 5 MILLISECONDS (I HAVE STUCK WITH 2 MS). I HAAVE DECIDED TO ADD A POTENTIOMETER TO VARY THE OFF TIME OF THE DESIGN TO CYCLE BETWEEN 2 - 1000 HZ. THE ARDUINO TONE LIBRARY WAS ALSO USED SUCCESSFULLY CREATE AUDIO OUTPUT.

I WILL NOT BE ADDING ANY MORE DETAIL ABOUT THE INTERRUPTER DESIGNS UNTIL THE V1 PCBS ARE COMPLETE. ONCE THEY ARE IN AND TEST COILS ARE BUILT I WILL BE MAKING VARIOUS INTERRUPTER ADDONS SUCH AS STACCATO MODE, ISOLATED AUDIO INPUT, MULTIPLE POTENTIOMETERS FOR VARIED ON AND OFF TIMES OVER A GIVEN RANGE, ETC. AND WILL POST FINISHED DEVELOPMENTS HERE.



# FOR MORE DETAILED EXPLAINATIONS OF SSTC OPERATION & DESIGN:

https://www.stevehv.4hv.org/SSTCindex.htm
https://www.loneoceans.com/labs/#
http://kaizerpowerelectronics.dk/
