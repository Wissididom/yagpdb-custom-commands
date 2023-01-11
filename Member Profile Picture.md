## Trigger
Type: `Command (mention/cmd prefix)`
Value: `mpfp`

## Response
```
{{if eq (len .CmdArgs) 0}}
	{{ .Member.AvatarURL "1024" }}
{{else}}
	{{ (getMember (index .CmdArgs 0)).AvatarURL "1024" }}
{{end}}
```
