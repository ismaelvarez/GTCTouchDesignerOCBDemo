# GTCTouchDesignerOCBDemo
A demo that uses FIWARE Notification System to get the telescope telemetry data. 

## Description
A web server node sends a subscription message to the OrionContextBroker for every entity in a list (keyIndicators.txt)

```json
{
  "description": "A touch designer subscription",
  "subject": {
    "entities": [
      {
        "id": "EndNode1"                                          # EntityID
      }
    ]
  },
  "notification": {
    "http": {
      "url": "http://192.168.0.10:9080/notification"               # URL to the Web Server node
    }
  }
}
```
When the entity is modified, the Orion Context Broker sends a notification message to all the subscriptors.
The web server node recieve that message, and parser it, saving the attribute values in a table.

Notification message:

```json
{
  "subscriptionId": "59edf55231cee478fe9fff1e",
  "data": [
    {
    "id": "EndNode1",
    "type": "EndNode",
    "PresenceSensor1": {
      "type": "Number",
      "value": 1,
      "metadata": {
        "TimeInstant": {
          "type": "DateTime",
          "value": "2022-03-31T11:10:09.307Z"
        }
      }
    },
    "PresenceSensor2": {
      "type": "Number",
      "value": 0,
      "metadata": {
        "TimeInstant": {
          "type": "DateTime",
          "value": "2022-03-31T11:10:09.307Z"
          }
        }
      }
    }
 ]
}
```
