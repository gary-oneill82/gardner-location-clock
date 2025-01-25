# The Gardner (Weasley) Family Clock

Happy Birthday Paul and welcome to your own version of the Weasley family clock!  The mechanism is mostly 3D printed and the STL files are available in the repository should anything break or wear out.

The Control software has been written in [ESPhome](https://esphome.io/) and provides a Web Server with [REST API](https://esphome.io/web-api/#api-rest).  Both hands are controlled by "Select" entities on the clock and the current state can be returned with a GET request to `http://<ip-address>/select/laura_location?detail=all` or `http://<ip-address>/select/paul_location?detail=all` this will return the following JSON Payload:
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
 

If you want the clock to update locations automatically you will need to work out the best way to do this for the two of you
