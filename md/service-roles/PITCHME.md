@snap[north-east]
@size[1.5em](Overview)
@snapend

@snap[east high-level bullets]

#### Producer

@ul[](false)
 - produces stop trade messages, dispatches on kafka
 - Implements HTTP API to let stop trade client send commands to resolve stop trades. Replies if resolving was successful or not
 @ulend

@snapend

@snap[west high-level]
![](img/stopped-trades-high-level.png)
@snapend

---

@snap[west]
![](img/stopped-trades-high-level.png)
@snapend

@snap[east]
StopTrade Service

- Consumes from kafka
- Stores messages in AMPS
- Has HTTP API so that client can list, query and delete stop trade messages
@snapend

---

@snap[west]
![](img/stopped-trades-high-level.png)
@snapend

@snap[east fragment]
StopTrade Client

- Display stop trade messages in a "good way"
- Allows user to edit and resolve stop trade messages
@snapend

