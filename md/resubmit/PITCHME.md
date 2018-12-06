---?image=img/bg/green.jpg

# Resubmit API

##### Implementations on Producer side

+++?image=img/bg/pink.jpg&position=right&size=65% 100%

@snap[west span-50]
HTTP API
<br/>
or
<br/>
ASYNC CQRS
@snapend

@snap[east text-white span-50]
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

FieldType is _not_ required here, since the producer service
for sure knows what type the field in the original error message has.

+++

asp.net example

```cs
[HttpPost]
ResolveController([FromBody] ResolveDto resolveMessage)
{
    var success = _handler.ExecuteResolveCommand(resolveMessage);  // business logic here

    if (success) return Ok();

    // For some reason resolving failed.
    // We now have the opportunity to tell our user why.
    return SomeHttpError(new StopTrade.Dto.ResolveResponse {
        Message = "Human readable error message"
    });
}
```

+++

@box[bg-red text-white rounded demo-box-pad](There is currently no way to send ResolveResponse via the async resolve pattern!)

+++

Any thoughts on which resolve pattern is "prefered"?

- sync
- async
