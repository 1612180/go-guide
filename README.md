# Naming

## Rule of thumb

**Longer** the **distance** between name's declaration and its use, **longer** the name

## Use Mixed Case

Don't use _

Acronyms should all be capital
```
ServerHTTP
FindID
```

## Local variables

Keep them **short**

```
Prefer i to index
Prefer r to reader
Prefer b to buffer
```

Prefer `ok` to keyInMap

```
v, ok := m[k]
```

Avoid redundant name, use `count` inside `AppleCount` function not `appleCount`

```
func AppleCount() int {
    count := 0
    ...
}
```

## Parameters

When types are **clear**, name should be short

```
func AfterFunc(d Duration, f func()) *Timer
func Echo(w io.Writer)
```

When types are **not clear**, name should provide documentation

```
func Unix(sec, nsec int64) Time
func HasPrefix(s, prefix []byte) bool
```

## Return values

Return values on **exported** functions should only be named for documentation purposes

```
func Copy(dst Writer, src Reader) (written int64, err error)
```

## Receivers

**Short** name that reflect the receiver type

```
func (b *Buffer) Read(p []byte) (n int, err error)

func (sh serverHandler) ServeHTTP(rw ResponseWriter, req *Request)
```

Should be **consistent** across a type's methods

Don't use `r` in one method and `rd` in another method

## Exported package-level names

Exported names are qualified by their **package names**

`bytes.Buffer` not `bytes.ByteBuffer`

`strings.Reader` not `strings.StringReader`

## Interface Types

Usually function name with 'er'

```
type Reader interface {
    Read(p []byte) (n int, err error)
}
```

When an interface includes **multiple methods**, choose a name that accurately describes its **purpose**

```
net.Conn
http.ResponseWriter
io.ReadWriter
```

## Errors

Error types should be `FooError`

```
type ExitError struct {
    ...
}
```

Error values should be `ErrFoo`

```
var ErrFormat = errors.New("image: unknown format")
```