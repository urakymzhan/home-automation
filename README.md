```
We will have 2 endpoints

collection: //devices
    * GET - view collection
    * POST - create new resource

Resource: /device/<identifier>
    * GET - view resource
    * DELETE - delete resource
```

# Device registry service

## Usage

All responses will have the form

```json
{
    "data": "Mixed type holding the content of the response",
    "message": "Description of what happend"
}
```

Subsequent responses definitons will only detail the expected value of the 'data field'

### List all devices

**Definition**
`GET /devices`

**Response**

- `200 OK' on success

```json
[
    {
        "identifier": "floor-lamp",
        "name": "Floor Lamp",
        "device-type": "switch",
        "control-gateway": "192.1.68.0.2"
    },
    {
        "identifier": "samsung-tv",
        "name": "Living Room TV",
        "device-type": "tv",
        "control-gateway": "192.1.68.0.9"
    }
]
```
### Registerting a new device

**Definiton**
`POST /devices`

**Arguments**
- `"identifier":string` a globally unique identifier for this device
- `"name":string` a friendly name for this device
- `"device-type":string` the type of the device as understood by the client
- `"controller_gateway":string` the IP address of the device's controller

**Response**

- `201 Created` on success

```json
    {
        "identifier": "floor-lamp",
        "name": "Floor Lamp",
        "device-type": "switch",
        "control-gateway": "192.1.68.0.2"
    }
```
## lookup device details

`GET /device/<identifier>

**Response**
- `404 Not Found` if the device does not exist
- `200 OK` on success

```json
    {
        "identifier": "floor-lamp",
        "name": "Floor Lamp",
        "device-type": "switch",
        "control-gateway": "192.1.68.0.2"
    }
```

## Delete a device

**Definition**

`DELETE /devices/<identifier>`

**Response**

- `404 Not Found` if the device does not exist
- `204 No Content` success and no content has returned


