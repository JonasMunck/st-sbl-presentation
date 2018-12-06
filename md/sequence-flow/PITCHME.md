---

The Lifecycle of a StopTrade Message
+++

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south fragment]
@box[bg-orange text-white](1#Message hits target machine and it generates a stop trade)
@snapend

+++

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south-west span-45]
@box[bg-pink text-white](2a#StopTrade Message is published on kafka)
@snapend

@snap[south-east span-45 fragment]
@box[bg-orange text-white](2b#Original message in stored in target services domain)
@snapend

+++

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south]
@box[bg-green text-white](3#StopTrade Message is saved in AMPS and is now available for UI)
@snapend

+++

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend


@snap[south-west span-30 fragment]
@box[bg-orange text-white](4a#Client tries to resolve message)
@snapend

@snap[south span-30 fragment]
@box[bg-orange text-white](4b#Producer service retrieves original message)
@snapend

@snap[south-east span-30 fragment]
@box[bg-orange text-white](4c#edit logic is applied)
@snapend

+++

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[north-east]
Sync pattern
@snapend


@snap[south-west span-30]
@box[bg-pink text-white](5a#sync. response to client, user knows if resolving was successful)
@snapend

@snap[south span-30 fragment]
@box[bg-pink text-white](5b#StopTrade service is notified via HTTP)
@snapend

@snap[south-east span-30 fragment]
@box[bg-pink text-white](5c#stoptrade message is removed from AMPS)
@snapend

+++

@snap[north-east]
**Async** pattern
@snapend

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south-west span-30]
@box[bg-green text-white](2a#async. dispatch on queue, user does not know status yet)
@snapend

@snap[south span-30 fragment]
@box[bg-green text-white](5b#StopTrade UI is notified via WebSocket)
@snapend

@snap[south-east span-30 fragment]
@box[bg-green text-white](5c#stoptrade message is removed from AMPS)
@snapend

