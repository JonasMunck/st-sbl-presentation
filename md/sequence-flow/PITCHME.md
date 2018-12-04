---?image=img/stop-trades-sequence-flow.png&postition=top&size=80% 50%

1. Message hits target machine and it generates a stop trade

---

---?image=img/stop-trades-sequence-flow.png&postition=top&size=80% 50%

2a. StopTrade Message is published on kafka
2b. Original message in stored in target services domain

---

---?image=img/stop-trades-sequence-flow.png&postition=top&size=80% 50%

3. StopTrade Message is saved in AMPS and is now available for UI

---

---?image=img/stop-trades-sequence-flow.png&postition=top&size=80% 50%

4a. Client revokes message
4b. Target service retrieves original message
4c. Merge logic is applied
4d. sync. response to client, user knows if resolving was successful
4e. StopTrade service is notified via HTTP
4f. stoptrade message is removed from AMPS

---