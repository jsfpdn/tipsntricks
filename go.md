# Go Stuff

## Catch Shadowed Variables

```bash
> go install golang.org/x/tools/go/analysis/passes/shadow/cmd/shadow
> go vet -vettool=$(which shadow) <package>
```

## Compile Flags

* optimization decisions `go build -gcflags -m <package>` (inlining functions, variable escaping)

