# custom_yang_model
```
virtualenv virtualenv
source virtualenv/bin/activate
pip install -r requirements.txt
```
- Validate a YANG model
```sh
pyang -f tree engineer.yang

module: engineer
  +--rw engineer
  |  +--rw name       string
  |  +--rw age?       types:age_type
  |  +--rw commute?   types:transportation_type
  |  +--rw project
  |     +--rw work_item* [work_item_name]
  |        +--rw work_item_name    string
  |        +--rw deadline?         string
  +--rw food* [item_name]
     +--rw item_name         string
     +--rw (food_type)?
        +--:(office)
        |  +--rw coffee
        |  |  +--rw size?   enumeration
        |  |  +--rw milk?   boolean
        |  +--rw donut?      empty
        +--:(home)
           +--rw salad?      empty
           +--rw smoothie?   empty
```
- Validate a sample XML file against a YANG model (support only YANG version 1)
```sh
yang2dsdl -v interfaces-data.xml interfaces.yang

== Generating RELAX NG schema './interfaces-data.rng'
Done.

== Generating Schematron schema './interfaces-data.sch'
Done.

== Generating DSRL schema './interfaces-data.dsrl'
Done.

== Validating grammar and datatypes ...
interfaces-data.xml validates

== Adding default values... done.

== Validating semantic constraints ...
No errors found.
```
Reference: [Understanding Yang](https://network.developer.nokia.com/sr/learn/yang/understanding-yang/)