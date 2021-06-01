# Devide-Registration
Building a REST API in Python

## Usage

All resopnses will have the form

```json
{
  "data":"Mixed type holding the content of response",
  "message":"Description of what happened"
}
```

Subsequent response definitions will only details the xpected value of the `data field`

## List All the devices

**Definition**
`GET /devices`

**Response**
-`200 ok` on success
```json
[
  {
    "identifier":"florr_lamp",
    "name":"Floor Lamp",
    "device_type":"switch",
    "controller_gateway":"192.1.68.0.2"
  },
  {
    "identifier":"samsung-tv",
    "name":"Living Room TV",
    "device_type":"tv",
    "controller_gateway":"192.1.68.0.9"
  }
]
```
## Registering New Device

**Definition**
`POST /device`

**Arguments**
-`"identifier":string` a globally unique identifier for the device
-`"name":string` a friendly name given for the device
-`"device_type":string` a type of device understood by client
-`"controller_gateway":string` a IP address for the decive's controller

IF the device with identier is already exists, the existing device will be overwritten. 
**Response**
-`200 Created` on success

```json
{
  "identifier":"florr_lamp",
  "name":"Floor Lamp",
  "device_type":"switch",
  "controller_gateway":"192.1.68.0.2"
}
```

## Lookup device details
`GET /device/<identifier>`

**Response**
-`400 Not Found` if device which is not exists
-`200 OK` on success

```json
{
  "identifier":"florr_lamp",
  "name":"Floor Lamp",
  "device_type":"switch",
  "controller_gateway":"192.1.68.0.2"
}
```

## Delete a device
`DELETE /device/<identifier>`

**Response**

-`400 Not Found` if device which is not exists
-`204 No Content` on success
