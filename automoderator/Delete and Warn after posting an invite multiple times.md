## Trigger
Type: `Regex`
Value: `(?:https?:\/\/)?(?:www\.)?(?:discord\.(?:gg|io|me|li)|discord(?:app)?\.com\/invite)\/[^\s/]+`

## Response
```
{{$logChannel := 943966812096319518}}
{{$timeoutDuration := "6h"}}
{{$timeoutReason := "Automated Anti Discord Spam CC"}}
{{$expireInSeconds := 43200}}
{{$allowedViolations := 3}}
{{$dbViolations := (dbGet .User.ID "inviteViolations")}}
{{$violations := 0}}
{{$dmMessage := "You have sent an Discord-Invite 3 times! You probably were hacked! If you were hacked, please consider changing your password and logout everyone that currently has access to your account by doing that."}}
{{if $dbViolations}}
    {{$violations = (toInt64 $dbViolations.Value)}}
{{end}}
{{$violations = toInt64 (add $violations 1)}}
{{if gt $violations $allowedViolations}}
    {{deleteTrigger 0}}
    {{sendDM $dmMessage}}
    {{dbDel .User.ID "inviteViolations"}}
    {{execAdmin "timeout" .User.ID $timeoutDuration $timeoutReason }}
    {{sendMessage $logChannel (joinStr "" .User.String " was timed out")}}
{{else}}
    {{$violations = (dbSetExpire .User.ID "inviteViolations" $violations $expireInSeconds)}}
{{end}}
```
