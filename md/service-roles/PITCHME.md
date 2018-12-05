
### Involved services and their roles

+++?image=img/stopped-trades-high-level.png&position=center&size=60%

Note:

Stop trade as implemented in SBL, the async / sync strategy.
async / async would not involve http response check after resolving stop trade message.

+++

@snap[north-east]
@size[1.2em](Producer)
@snapend

@snap[east high-level bullets]

@ul[](false)
 - Produces stop trade messages, dispatches on kafka
 - Implements HTTP API to let stop trade client send commands to resolve stop trades.
 - Mechanism to indicate if resolving was successful or not
 @ulend

@snapend

@snap[west high-level]
![](img/stopped-trades-high-level.png)
@snapend

Note: Don't go into details, just explain the components here to get an overview.

+++

@snap[north-east]
@size[1.2em](StopTrade Service)
@snapend

@snap[east high-level bullets]

@ul[](false)
- Consumes from kafka
- Stores messages in AMPS
- Has HTTP API so that client can list, query and delete stop trade messages
 @ulend

@snapend

@snap[west high-level]
![](img/stopped-trades-high-level.png)
@snapend

+++

@snap[north-east]
@size[1.2em](StopTrade Client)
@snapend

@snap[east high-level bullets]

@ul[](false)
- Display stop trade messages in a "good way"
- Allows user to edit and resolve stop trade messages
 @ulend

@snapend

@snap[west high-level]
![](img/stopped-trades-high-level.png)
@snapend

Note:

Client could implement SuperUser interface with even more power.
