# Stuck electronic parking brake
During our cross country ski vacation in Åre Sweden, the temperature dropped to between -25 to -30 degrees C but I still wanted to ski. So after pre heating the car I started driving to the tracks, then I suddenly realized I had forgot my glasses. I turned around, drove back to the cabin that sits in a slight slope, put the car in idle and engaged the electronic parking brake. 3 minutes later I tried to release the parking brake and it started to complain that the parking brake had not fully disengaged. I tried multiple times to engage and disengage without any luck.

When engaging the parking brake I would get a yellow warning, saying that parking brake service is required. And when disengaging I would get a red warning light and the message parking brake not fully released.

I drove the car 50m to the nernst flat parking spot, and I could see in the snow that there were skidding marks on the left tire, so it was indeed locked up. The right tire hade released properly.

My hypothesis here was that there could have been moisture either in the parking brake motor or the caliper that had frozen due to the cold wether that locked the parking brake mechanism.

## Defrosting the caliper
Going 100% on the hypothesis that the parking brake mechanism is frozen i brought out the heat gun on 170 degrees C and pointed it to the back of the caliper and the park brake motor, but the heat gun had a really hard time even getting up to 70 degrees C. Then I increase to 300 with the same result. Then I maxed it out on 600 degrees C which was a really bad idea, now it got up to temperature and it quickly started to melt and deform the plastics of the park brake motor. 

After applying heat a bit more cautiously, I got the the temperature up on the entire caliper to around 10 degrees C. I tried releasing the park brake one more time, but with disappointing result. At this point I thought that I might have damaged the motor with the heat gun.

## Removing the motor from the caliper
Now using the included emergency scissor lift and 19mm socket tool I removed the tire and then started to unscrew the hex bolts that holds the motor in place. To my disappointment it is mor or less impossible the fit a hex bit, and wrench (even low profile once) to one of the screws without first removing the caliper. It is also not possible to remove the caliper when the park brake is engaged (stupid design). I had a hacksaw blade in my toolbox, so I decided to cut through one of the ears of the motor instead, then i could remove the motor and unwind the spindle and pressure nut releasing the park brake.

Now I have a drivable car, but the car still thinks that the park brake is engaged and gives me a really annoying beep sound when driving that becomes even more frequent like once a second when driving faster than 30km/h. Driving home to Gothenburg in this state (around 11h) with partner and two small kids was not an option.

## Ordering a new motor
I ordered a new motor from Vparts which I had in less than 24h later which I think is insane, I am really impressed with both Vparts and PostNord being able to deliver parts this quickly. Unfortunately it did not fix the problem, which meant that the original motor was probably working. It would have been smart to test the old one using the cars 12v battery and two wires, but I did not have any wires available at the time and for some reason I was very confident that the motors was bad so I did not think clearly.

## Diagnosis
At this point I did not really know what the problem could be but i was thinking that it could be one of:
- Need of motor calibration, removing error codes
- Cables that are snapped or short to ground
- Blown fuses
- Bad PBM (Park brake module)

I ordered an icarsoft from Vparts, again super impressed, had it the day after. Then I found a really friendly local in Åre that were willing to lend me a multimeter. I also found all the wiring schematics for my V60 on [scribd.com](https://www.scribd.com/document/490826169/2011-S60-V60-39262202#page=1)

### OBD diagnosis
The I car soft gave me the following codes:
```
Code: C200801
State: None
Left Motor. General Failure Information. General Electronic Failure.
```
and
```
Code: C200811
State: None
Left Motor. General Electrical Failure. Circuit Short To Ground.
```
### Electronic diagnosis
Starting with the easiest thing, checking that the fuses to the left motor was not blown. According to the wiring diagram this would be one of 11D/A1 or 11D/A2 which are 30A fuses, but they were both ok.

Checking continuity for both wires from the PBM connector to the park break motor connector using a multimeter. This would be wire 29(Blue with green stripes) and 14(Violet with black stripes). However to find which pin in the connector that actually is you would need to unwind parts of the harness, so i just tested all the large pins that can carry high current until I found two that corresponded the pins in the motor connector.
![](multimeter.png)
I also tested continuity to ground for these two pins, and they were not short to ground.

If I would not have seen continuity or if any of the wires was short to ground I would have done the same test but in connector 74/514. Then I would have a better understanding where the short or broken wire would be. Most likely close to to the swing arm, which is the only moving part that transfers movement to the cable harness.

The tests shows that there is no problem with the wires that can cause a short to ground, this makes me believe that there is a short to ground inside the PBM module, and it would need to be replaced.

![](wiring.png)
![](fuses.png)
![](cable_harness_pbm.png)
![](cable_harness_motor.png)
<table>
  <tr>
    <td><img src="connector_74_514.png" alt="Connector 74_514" width="400"/></td>
    <td><img src="connector_74_514_explain.png" alt="Connector 74_514 explanation" width="400"/></td>
  </tr>
</table>

## Replacing PBM (Park brake module)
When ever replacing a data module you might need to do a software download, especially if it is a new module, this can only be done by authorized Volvo repair shops with a valid online vida license. Closest place for this would be Östersund, which is quite far and they would probably not have new spare parts on the shelf.

The best thing would then be to order a second hand unit. And hope that it would not require a software download. A software download is not necessary new software it is rather car configuration, e.g a awd vehicle might need different parameters on when to release than a FWD vehicle, but that is just a guess. 

I found a second han unit that had belong to a V60 of the same model year, same engine and gearbox which to me would be the only important parameters for a good fit that would not require a software download

2 days later I received a PBM from Jönköpings bildemontering which worked out grate without any software download, and an obd diagnostics showed no errors for the PBM.

Removing the old PBM is quick but a bit tricky to find/reach one of the plastics clips before you can bend it out of its mount.
![](pbm_mount.png)