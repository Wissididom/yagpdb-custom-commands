## Trigger
Type: `Command (mention/cmd prefix)`
Value: `upfp`

## Response
```
{{if eq (len .CmdArgs) 0}}
	{{ .User.AvatarURL "1024" }}
{{else}}
	{{ (getMember (index .CmdArgs 0)).User.AvatarURL "1024" }}
{{end}}
```
