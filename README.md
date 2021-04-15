# General

Default camera address (http://IP_ADDRESS)
```
http://192.168.0.1
```


# Camera / File settings

## Endpoint
```
http://IP_ADDRESS:80
```

## Messages (POST requests)
```bash
curl -H "Content-Type: application/json" --request POST --data '{"msg_id" : MSG_ID}' http://IP_ADDRESS:80
```

### MSG_ID 0: Help
```javascript
{
  "msg_id": 0
}
```

### MSG_ID 200 : Total file count on SD card
```javascript
{
  "msg_id": 200
}
```

### MSG_ID 201 : Total file count on SD card
```javascript
{
  "msg_id": 201,
  "SeekType": 1,
  "PosOffset": 1,
  "FileCount": 6
}
```

### MSG_ID 202 : Get file list
```javascript
{
  "msg_id": 202,
  "MainFile": "/app/sd/DCIM/100HSCAM/L0010019.MP4",
  "FileCount": 20
}
```
### MSG_ID 203 : Delete all files
```javascript
{
  "msg_id": 203
}
```

### MSG_ID 204 : Delete file
```javascript
{
  "msg_id" : 204,
  "flie_list" : [ // possible typo in help message?
    {
      "path": "/app/sd/DCIM/100HSCAM/NORM0001.MP4"
    }, {
      "path": "/app/sd/DCIM/100HSCAM/NORM0002.MP4"
    }
  }
}
```

### MSG_ID 300 : Get record status
```javascript
{
  "msg_id" : 300,
}
```

### MSG_ID 301 : Start record
```javascript
{
  "msg_id" : 301,
}
```

### MSG_ID 302 : Stop record
```javascript
{
  "msg_id" : 302,
}
```

### MSG_ID 303 : Set record type
```javascript
{
  "msg_id" : 303,
  "type" : 1
}
```

### MSG_ID 304 : Set record interval
```javascript
{
  "msg_id" : 304,
  "type" : 1
}
```

### MSG_ID 305 : Set record auto split
```javascript
{
  "msg_id" : 305,
  "type" : 1,
  "len" : 60
}
```

### MSG_ID 306 : Set record manual split
```javascript
{
  "msg_id" : 306,
  "type" : 1,
  "len" : 60
}
```

### MSG_ID 307 : Get record duration
```javascript
{
  "msg_id" : 307
}
```

### MSG_ID 308 : Record audio switch
```javascript
{
  "msg_id" : 308,
  "on" : 1
}
```

### MSG_ID 400 : Format SD card, size[param] uint KB
```javascript
{
  "msg_id" : 400,
  "size" : 32
}
```

### MSG_ID 401 : Get SD card info
```javascript
{
  "msg_id" : 401
}
```

### MSG_ID 402 : Get SD card status
```javascript
{
  "msg_id" : 402
}
```

### MSG_ID 403 : Get SD card error
```javascript
{
  "msg_id" : 403
}
```

### MSG_ID 404 : Get record error
```javascript
{
  "msg_id" : 404
}
```

### MSG_ID 500 : Get WIFI MAC address
```javascript
{
  "msg_id" : 500
}
```

### MSG_ID 800 : Close protomsg print
```javascript
{
  "msg_id" : 800,
  "type" : 1
}
```

# Gimbal settings

## Endpoint

Notice the different port!

```
http://IP_ADDRESS:27739/obsbot/tail/ai/gimbal
```

## Messages (GET requests)

Retrieve current gimbal status
```
curl --request GET IP_ADDRESS:27739/obsbot/tail/ai/gimbal
```

```javascript
{
  "BaseStatus": 0,
  "Calibrate": 0,
  "Degree": [
    0.05000000074505806,
    -12.010000228881836,
    43.599998474121094
  ],
  "Error": 0,
  "EscRollVer": "2.1.1.0",
  "Lock": false,
  "MainVer": "2.21.1.0",
  "PitchRollVer": "2.1.1.0",
  "RollBias": [
    0,
    0
  ],
  "SystemStatus": 0,
  "Velocity": [
    -0.41999998688697815,
    0.009999999776482582,
    -0.07999999821186066
  ],
  "View": "HOR",
  "YawRange": 0,
  "YawRollVer": "2.1.1.0"
}
```

## Messages (POST requests)
```
curl -H "Content-Type: application/json" --request POST --data '{"cmd" : CMD_ID}' IP_ADDRESS:27739/obsbot/tail/ai/gimbal
```

### CMD setAbsDegree :
```javascript
{
  "cmd" : "setAbsDegree",
  "rollDegree" : -1000,
  "pitchDegree" : -1000,
  "yawDegree" : -1000
}
```

### CMD_ID lock :
```javascript
{
  "cmd" : "lock",
  "mode" : 0
}
```

# AI settings

## Endpoint
```
http://IP_ADDRESS:27739/obsbot/tail/ai
```
