---?image=img/bg/green.jpg

# Resubmit API

##### Implementations on Producer side

+++?image=img/bg/pink.jpg&position=right&size=70% 100%

@snap[west span-50]
HTTP API
@snapend

@snap[east text-white span-70]
@ol
- accept specific payload
- resolve messages according to business logic
- send reply to stop trades
@olend


+++

Resubmit payload


```json
{
  "command": "Resolve",  /* or "Ignore" */
  "sourceId": "8912",
  "editedFields": [
      {
          "name": "Volume",
          "value": 4500
      }
  ]
}
```

@[2-3](required)
@[4-9](optional in resolve flow)

Note:

FieldType is not required here, since the producer service
for sure knows what type the field in the original error message has.
