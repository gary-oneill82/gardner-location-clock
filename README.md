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

If you want the clock to update locations automatically you will need to work out the best way to do this for the two of you but there are a few options:

1. We run our Smart house on [Home Assistant](https://www.home-assistant.io/) which integrates directly with ESPHome devices and can be programmed with automations
2. 
