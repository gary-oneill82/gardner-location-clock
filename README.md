# The Gardner (Weasley) Family Clock

Happy Birthday Paul and welcome to your own version of the Weasley family clock!  The mechanism is mostly 3D printed and the STL files are available in the repository should anything break or wear out.

## First Start

When you first plug the clock in it will run a demonstration mode to move the hands to various locations before returning to home.  The Clock will present an Access Point with an SSID of "Location-Clock", I have given Laura the password.  Connect to the AP and connect to your own Wifi, the clock will now be available at http://weasley-clock.local, Laura has the Log in details for this also.

## Basic Controls

The Control software has been written in [ESPHome](https://esphome.io/) and provides a Web Server with [REST API](https://esphome.io/web-api/#api-rest).  Both hands are controlled by "Select" entities on the clock and the current state can be returned with a GET request to `http://weasley-clock.local/select/laura_location?detail=all` or `http://weasley-clock.local/select/paul_location?detail=all` this will return the following JSON Payload:
```
{
  "id":"select-laura_location",
  "name":"Laura Location",
  "icon":"",
  "entity_category":0,
  "value":"Home",
  "state":"Home",
  "option":["Home","Hogwarts","Work","Hogsmede","Quiddich","Holiday","Crieff Hydro","In Transit","Mortal Peril","Lost"],
  "sorting_weight":2,
  "sorting_group":"Controls"
}
```
To Control the hands simply send a POST request, for example `http://weasley-clock.local/select/laura_location/set?option=Hogwarts`

## Automation

If you want the clock to update locations automatically you will need to work out the best way to do this for the two of you but there are a few options:

1. We run our Smart house on [Home Assistant](https://www.home-assistant.io/) which integrates directly with ESPHome devices, has iOS and Android apps that can report location back to the server and can be programmed with automations, this is pretty much an all in one solution.
2. OwnTracks is open source and requires a phone app and server at home (can be a Rapberry Pi) as used in [this project](https://github.com/WhereslyClock/MyWhereslyClock), you then just have to work out the bridge to send the POST request to the Clock
3. Any other loction tracking service with an API should work as well so long as you write a middle-man programme to report to the clock where you each are!

## Calibration

While the hands are glued to the shafts there may still be some drift over time, if the hands stop consistently pointing to the correct location I have built in a Calibration option.  To access this go to [http://weasley-clock.local](http://weasley-clock.local) while connected to your home network and switch the "Access Calibration" switch (you will need to refresh the web page after changing the switch.  Once this is done you should see some additional options:

