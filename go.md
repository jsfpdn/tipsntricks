# Go Stuff

## Catch Shadowed variables

```bash
go install golang.org/x/tools/go/analysis/passes/shadow/cmd/shadow
```

```bash
go vet -vettool=$(which shadow) <package>
```

