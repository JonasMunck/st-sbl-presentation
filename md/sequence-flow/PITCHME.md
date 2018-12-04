@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south]

1. Message hits target machine and it generates a stop trade

@snapend

---

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south]

- StopTrade Message is published on kafka
- Original message in stored in target services domain

@snapend

---

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south]

3. StopTrade Message is saved in AMPS and is now available for UI

@snapend

---

@snap[north seq-flow]
![seq-flow](img/stop-trades-sequence-flow.png)
@snapend

@snap[south]

4a. Client revokes message
4b. Target service retrieves original message
4c. Merge logic is applied
4d. sync. response to client, user knows if resolving was successful
4e. StopTrade service is notified via HTTP
4f. stoptrade message is removed from AMPS

@snapend

---