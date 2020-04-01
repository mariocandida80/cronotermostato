<img src="https://img.shields.io/badge/Version-1.3.6-green">  <a href="https://forum.hassiohelp.eu/d/503-package-cronotermostato"><img src="https://img.shields.io/badge/Forum-hassiohelp-blue"> </a>
<img src="https://img.shields.io/badge/Update-yes-orange"> <a href="https://www.buymeacoffee.com/mariocandida80"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" width="90" alt="Buy Me A Coffee"> </a>
<br> 
If you want the weekly version, you can find it  <a href="https://github.com/mariocandida80/addon_settimanale">here</a>.

<p align="center"/> <b>Cronothermostat Package for Home Assistant.</b> <br> </p>

<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/principale.png" alt="Immagine cronotermostato"></p>
This package creates a series of entities and automations to make sure that the thermostat works in various modes that can be selected by the user and that it is possible to turn it on at certain times and whether or not you are at home.
Let's see how to install it. <br>
<br>
<a href="#Prerequisiti">Prerequisites</a><br>
<a href=“#Installazione1">Installation with climate entity no pre installated</a><br>
<a href="#Installazione2">Installation with climate entity installated</a><br>
<a href=“#Confcard">Card configuration</a><br>
<a href=“#Funzionamento">How it work</a><br>
<a name="Prerequisiti"><p align="center"/> <b>Prerequisites</b> <br> </p>
To operate, it needs an already installed climate entity or 2 entities: a switch that activates and deactivates the thermostat and a temperature sensor. <br>
To install this package you will need:<br>
1. have configured the packages <br>
2. install  <a href="https://github.com/custom-cards/button-card">button-card</a>, <a href="https://github.com/thomasloven/lovelace-card-mod"> card-mod</a>,  <a href="https://github.com/thomasloven/lovelace-state-switch">state-switch</a> and <a href="https://github.com/pilotak/homeassistant-attributes"> attributes </a> (from HACS)<br><br>

<a name="Installazione1"><p align="center"/><p align="center"/> <b>Installation with climate entity not pre-installed</b> <br> </p>
Download the chronothermostat-master.zip file (clone or download at the top right and then download zip) and unzip the files. <br>
Copy the files in this way:<br>
Pkg_cronotermostato_v1_3_6.yaml in the packages folder<br>
blue.jpg, impostazioni.jpg and fiamma.gif in the folder www/images/lovelace /<br>

Open the file Pkg_cronotermostato_v1_3_6.yaml and make the following changes:<br>
1. replace switch.sonoff_10004b541f with the switch that turns on the thermostat (line 33))<br>
2. replace sensor.sonoff_10004b541f_temperature with the temperature sensor (line 34)<br>
3. replace device_tracker.iphone7 with your device_tracker (line 35)<br>
4. replace the home zone with your own zone if it is different (line 36)<br>
5. replace the notification service with your own (line 37)<br>
6. if you already have the sensor.time, comment it (lines from 156 to 158)<br>
7. if you want a hysteresis, i.e. that the thermostat switches off at a higher temperature or that it switches on again at a lower temperature than the one set, you will have to change hot_tolerance and cold_tolerance. Example: setting the temperature to 23 and setting cold_tolerance to 2 and hot_tollerance to 0, the thermostat will turn off when it reaches 23 degrees and will turn back on at 21. By default, cold_tolerance: 0.5 and hot_tolerance: 0.<br>
Restart home assistant<br><br>

<a name="Installazione2"><p align="center"/> <b>Installation with climate entity already installed</b> <br> </p>
Download the chronothermostat-master.zip file (clone or download at the top right and then download zip) and unzip the files<br>
Copy the files in this way:<br>
Pkg_cronotermostato_v1_3_6_no_climate.yaml in the packages folder <br>
blu.jpg e fiamma.gif in the folder  www/immagini/lovelace/<br>

Open the file Pkg_cronotermostato_v1_3_6_no_climate.yaml and make the following changes:<br>
1. replace device_tracker.device with your device_tracker (line 32)<br>
2. replace the home zone with your own zone if it is different (line 33)<br>
3. replace the notification service with your own (line 34)<br>
4. replace climate thermostat with your own (line 35)<br>
5. if you already have the sensor.time, comment it (lines from 138 to 140)<br>
Restart home assistant<br><br>
<a name="Confcard"><p align="center"/> <b>For card configuration:</b><br> </p>
For those who use raw mode, create a new card and copy the contents of lovelace_raw.yaml.<br>
For those who use the yaml mode, open the lovelace_yaml.yaml file and copy the content into your lovelace file.<br>
<br>
<a name="Funzionamento"><p align="center"/> <b>How it work</b><br> </p>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/principale.png" alt="Immagine cronotermostato"></p>
In the main card you will find a button at the top right to open the settings of the on and off times for the AUTO and PREHEATING mode, below you will find a leaf that opens the settings for the ECO mode, at the top left a gear to open the settings. In the center on the left there is the temperature of your sensor while on the right the set temperature that you can change with the 2 arrows that are positioned above and below of it; in the center it is indicated by a flame if the thermostat is currently on or off; below are the 5 operating modes; the selected mode will be highlighted in yellow.<br><br>
<p align="center"/> <b>Operating mode</b><br> </p>
The thermostat is configured to operate in 5 modes:<br>

OFF: thermostat off.<br>

MANUAL: thermostat on, does not take into account times and position.<br>

AUTO:  the thermostat switches on only if you are at home and if the time is between the set time intervals.<br>

PRE: the thermostat turns on at the set time even if you are away from home.<br>

ECO:  set a lower temperature, ideal for the night or if you want to leave a lower temperature when you are not at home.<br><br>

When the thermostat is on, in any mode except OFF, it will remain on until it reaches the set temperature and will turn on again if the temperature drops again.<br>
ECO mode is automatically activated at the set time and then returns to the previous mode and the previous temperature once it arrives at the set time to switch off the ECO mode. You can also activate it manually by clicking on the ECO button. To deactivate it, simply choose a different mode and the previously set temperature will also return. If you want to deactivate ECO mode with the times set, you can do it from the settings menu.<br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/eco.png"> </p>
From the home page, clicking on the leaf at the top right, the eco mode settings menu will open.<br>
Here you can enter the on and off times of the mode and the temperature to be set when this mode is activated.<br>
By clicking on the arrow at the top right you will return to the home page.<br><br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/orari.png"> </p>
From the home page, by clicking on the icon at the top right, the settings menu will open for switching on in AUTO and PREHEATING mode.<br>
Here you can set the time for switching the thermostat on and off. There are 3 time bands with the possibility of disabling the last 2 in case you want to operate the thermostat with a mono-hourly or bi-hourly band; just click on/off above the band.<br>
By clicking on the arrow at the top right you will return to the home page.<br>
<p align="center"/><img src="https://github.com/mariocandida80/cronotermostato/blob/master/esempi/nuova_impostazioni.png" alt="nuova impostazioni"></p>
From the home page, clicking on the gear at the top left, the thermostat settings menu will open.<br>
From here you can choose whether or not to activate the ECO mode with the times set.<br>
You can select the exit mode, when you are in AUTO mode and leave the house; there are 2 modes: OFF and ECO. The first turns off the thermostat to turn it back on when you return; the second leaves the thermostat on by lowering the temperature to the ECO temperature and then restoring the temperature before returning.<br>
L'ultima ozione serve per scegliere se ricevere o meno un messaggio all'accensione del termostato. <br>
For any problem write on the <a href="https://forum.hassiohelp.eu/showthread.php?tid=503">forum.</a><br>
