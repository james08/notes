# NO GENERICS!!
# Go Presentation


[Gophercon 2015 Slides](https://talks.golang.org/2015/gophercon-goevolution.slide#1)

>Most ideas come from previous ideas.
>(Alan Kay)
>
>Or, as some critics would say: There's nothing new in Go!
>
>They are missing the point:
>
>The task of the programming language designer " is consolidation not innovation ".
>(Hoare, 1973).


https://code.tutsplus.com/tutorials/lets-go-object-oriented-programming-in-golang--cms-26540  
<br>

https://thenewstack.io/understanding-golang-packages/


There is no type hierarchy in Go

Go has no classes, but it has types. In particular, it has structs. Structs are user-defined types. Struct types (with methods) serve similar purposes to classes in other languages.

## structs

A struct defines state. Structs hold only state and no behavior.  
```go
type Creature struct {

  Name string

  Real bool

}
```

### Embedding  
You can embed anonymous types inside each other. If you embed a nameless struct then the embedded struct provides its state (and methods) to the embedding struct directly.  
```go
type FlyingCreature struct {
  Creature
  WingSpan int
}
```

## methods
Methods are functions that operate on particular types. They have a receiver clause that mandates what type they operate on.
```go
func (c Creature) Dump() {
  fmt.Printf("Name: '%s', Real: %t\n", c.Name, c.Real)
}
```

You can embed anonymous types inside each other. If you embed a nameless struct then the embedded struct provides its state (and methods) to the embedding struct directly.

## Interfaces  
Interfaces are the hallmark of Go's object-oriented support. Interfaces are types that declare sets of methods. Like interfaces in other languages, they have no implementation.

Objects that implement all the interface methods automatically implement the interface. There is no inheritance or subclassing or "implements" keyword. In the following code snippet, type Foo implements the Fooer interface (by convention, Go interface names end with "er").
```go
type Fooer interface {
  Foo1()
  Foo2()
  Foo3()
}

type Foo struct {
}

func (f Foo) Foo1() {
    fmt.Println("Foo1() here")
}

func (f Foo) Foo2() {
    fmt.Println("Foo2() here")
}

func (f Foo) Foo3() {
    fmt.Println("Foo3() here")
}
```

## Go Routine
