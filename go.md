# Go Stuff

## Catch Shadowed Variables

```bash
> go install golang.org/x/tools/go/analysis/passes/shadow/cmd/shadow
> go vet -vettool=$(which shadow) <package>
```

## Code Optimalization/Introspection

* `GODEBUG=inittrace=1` go run main.go - print work (execution time & allocs) caused by `init` functions

## Compile Flags

* optimization decisions `go build -gcflags -m <package>` (inlining functions, variable escaping)

