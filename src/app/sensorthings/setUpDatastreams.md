# Create SensorThings instances

for each using the POST method

## Thing

http://il060:8082/v1.0/Things

```
{
   "name": "Prusa i3",
   "description": "3D Printer Prusa i3 MK3 in the Iot Lab Salzburg on the central desk",
   "properties": {
      "kafka": {
         "hosts": [
            "il081:9093",
            "il082:9094",
            "il083:9095"
         ],
         "topics": {
            "logs": "dtz-logging",
            "metrics": "dtz-sensorthings"
         },
      "specification": "https://www.prusa3d.com/downloads/manual/prusa3d_manual_175_en.pdf"
      }
}
```

## Location

for each Thing:

http://il061:8082/v1.0/Things(1)/Locations

http://il061:8082/v1.0/Things(2)/Locations

```
{
  "name": "IoT Labor Salzburg",
  "description": "IoT Labor of Salzburg Research",
  "encodingType": "application/vnd.geo+json",
  "location": {
    "type": "Point",
    "coordinates": [13.040670, 47.822784]
  }
}
```



## Sensor

http://il061:8082/v1.0/Sensors
```
{
  "name": "operator input on the operator dashboard for the Ultimaker 2.",
  "description": "Input from the Ultimaker 2 3D Printer's operator Dashboard is streamed.",
  "encodingType": "application/pdf",
  "metadata": "https://github.com/iot-salzburg/dtz_operator-dashboard"
}
```


## Datastreams with Observed Properties

http://il061:8082/v1.0/Datastreams


```
{
  "name": "Filament Change",
  "description": "New Filament inserted into the Ultimaker 2 3D printer will be logged.",
  "observationType": "http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Observation",
  "unitOfMeasurement": {
    "name": "filament",
    "symbol": "srfg.ultimaker2.filament",
    "definition": "string"
      },
  "Thing":{"@iot.id":1},
  "ObservedProperty":
      {
      "name": "Ultimaker 2 Filament Change",
      "description": "The Filament color and type of the Ultimaker 2 3D printer",
      "definition": "http://il081:6789/edit_filaments"
        },
  "Sensor":{"@iot.id":10}
}


{
  "name": "3D Print Annotations",
  "description": "Annotations of the print and printing process",
  "observationType": "http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Observation",
  "unitOfMeasurement": {
    "name": "print annotation",
    "symbol": "srfg.ultimaker2.annotation",
    "definition": "string"
  },
  "Thing":{"@iot.id":1},
  "ObservedProperty":
    {
      "name": "Ultimaker2 print annotation",
      "description": "Observations of the printing result of the Ultimaker2.",
      "definition": "srfg.ultimaker2.annotaion"
    },
  "Sensor":{"@iot.id":10}
}

{
  "name": "3D Print Nozzle Cleaning",
  "description": "Nozzle cleaning event of the Ultimaker2",
  "observationType": "http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Observation",
  "unitOfMeasurement": {
    "name": "nozzle cleaning",
    "symbol": "srfg.ultimaker2.nozzle-cleaning",
    "definition": "string"
  },
  "Thing":{"@iot.id":1},
  "ObservedProperty":
    {
      "name": "Ultimaker2 nozzle cleaning event",
      "description": "Reported nozzle cleaning of the Ultimaker2.",
      "definition": "srfg.ultimaker2.nozzle-cleaning"
    },
  "Sensor":{"@iot.id":10}
}
```



# Getting corresponding datastreams:

http://il061:8082/v1.0/Datastreams(10)?$expand=ObservedProperty

