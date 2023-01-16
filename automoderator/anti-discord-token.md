## Trigger
Type: `Message matches regex`

Value: `([A-Za-z\d\-_]+)\.[A-Za-z\d\-_]+\.[A-Za-z\d\-_]+`

## Conditions
Type: `New message`

Type: `Edited message`

## Effects
Type: `Delete Message`

Type: `Send Message`

* Custom message: `Please do not send Discord Tokens`
* Delete sent message after x seconds (0 for non-deletion): `0`
* Ping user commiting the infraction: ✅
* Channel to send message in (Leave None to send message in same channel): `None`
