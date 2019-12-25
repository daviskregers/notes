# Primitives

At this section we are going to look at primitive data types that are available at the go language.

There are 3 categories of types we can store data in go:

## Boolean type

- Values are `true` or `false`
- Not an alias for other types (e.g. int)
- Zero value if false

```go
var n bool = true
fmt.Printf("%v, %T\n", n, n)
n = false
fmt.Printf("%v, %T\n", n, n)
m := 1 == 1
fmt.Printf("%v, %T\n", m, m)
var o bool // default value is `0`
fmt.Printf("%v, %T\n", o, o)
```

```go
true, bool
false, bool
true, bool
false, bool
```

## Numberic types

### Integers

- Signed Integers
    - int type has varying size, but min 32 bits
    - 8 bit (int8) through 64 bit (int64)
- Unsigned integers
    - 8 bit (byte and uint8) through 32 bit (uint32)
- Arithmetic operations
    - Addition, subtraction, multiplication, division, remainder
- Bitwise operations
    - and, or, xor, and not
- Zero value is 0
- Can't mix types in same family (uint16 + uint32 = error)

```go
// Signed Integers
i := 42 // int
var i1 int8 = 42 // 8 bit integer (-128 to -127)
var i2 int16 = 42 // 16 bit integer (-32 768 to 32 767)
var i3 int32 = 42 // 32 bit integer (-2147483648 to 2147483647)
var i4 int64 = 42 // 64 bit integer (-9223372036854775808 to 9223372036854775807)

fmt.Printf("%v, %T\n", i, i)
fmt.Printf("%v, %T\n", i1, i1)
fmt.Printf("%v, %T\n", i2, i2)
fmt.Printf("%v, %T\n", i3, i3)
fmt.Printf("%v, %T\n", i4, i4)

// Unsigned Integers
var ui1 uint8  = 42 // 8  bit unsigned integer (0 to 255)
var ui2 uint16 = 42 // 16 bit unsigned integer (0 to 65535)
var ui3 uint32 = 42 // 32 bit unsigned integer (0 to 4294967295)

fmt.Printf("%v, %T\n", ui1, ui1)
fmt.Printf("%v, %T\n", ui2, ui2)
fmt.Printf("%v, %T\n", ui3, ui3)

// we don't have a 64 bit uint, but we have byte.

// basic operations
// variable types must match or do type conversion

a := 10 // 1010
b := 3  // 0011

fmt.Println(a + b)
fmt.Println(a - b)
fmt.Println(a * b)
fmt.Println(a / b)  // note that it drops reminder, since we preserve integer type
fmt.Println(a % b)  // reminder
fmt.Println(a ^ b)  // AND      -- 1010 ^  0011 = 0010
fmt.Println(a | b)  // OR       -- 1010 |  0011 = 1011
fmt.Println(a ^ b)  // XOR      -- 1010 ^  0011 = 1001
fmt.Println(a &^ b) // AND NOT  -- 1010 &^ 0011 = 0100

a = 8 // 2^3
fmt.Println(a << 3)   // bit shift 3 places left, 2^3 * 2^3 = 2^6
fmt.Println(a >> 3)   // bit shift 3 places right, 2^3 / 2^3 = 2^0
```

```go
42, int
42, int8
42, int16
42, int32
42, int64
42, uint8
42, uint16
42, uint32
13
7
30
3
1
9
11
9
8
64
1
```

### Floating point

- Follow IEEE-754 standard
- Zero value is 0
- 32 and 64 bit versions
- Literal types
    - Decimal (3.14)
    - Exponential (13e18 or 2E10)
    - Mixed (13.7e12)
- Arithmetic operations
    - addition, subtraction, multiplication, division

```go
// Floating numbers
// 32 bit float (precision from +/- 1.18E38 to +/-3.4E38)
// 64 bit float (precision from +/- 2.23E-308 to +/-1.8E308)

var f0 float32 = 3.14E12
f1 := 3.14
f2 := 13.7e72
f3 := 2.1E14

fmt.Printf("%v, %T\n", f0, f0)
fmt.Printf("%v, %T\n", f1, f1)
fmt.Printf("%v, %T\n", f2, f2)
fmt.Printf("%v, %T\n", f3, f3)

a1 := 10.2
b1 := 3.7
fmt.Println(a1 + b1)
fmt.Println(a1 + b1)
fmt.Println(a1 * b1)
fmt.Println(a1 / b1)
```

```go
3.14e+12, float32
3.14, float64
1.37e+73, float64
2.1e+14, float64
13.899999999999999
13.899999999999999
37.74
2.7567567567567566
```

### Complex numbers

- Zero value is (0+0i)
- 64 and 128 bit versions
- Built-in functions
    - complex - make complex number from 2 floats
    - real - get real part as float
    - imag - get imaginary part as float
- Arithmetic operations
    - Addition, subtraction, multiplication, division

```go
// complex numbers
// there are 2 types -
// - complex64  (float32 real + float32 imaginary parts)
// - complex128 (float64 real + float64 imaginary parts)

var c1 complex64 = 1 + 2i
var c2 complex128 = 1 + 3i

fmt.Printf("%v, %T\n", c1, c1)
fmt.Printf("%v, %T\n", c2, c2)

fmt.Printf("%v, %T\n", real(c1), real(c1))
fmt.Printf("%v, %T\n", imag(c1), imag(c1))

fmt.Printf("%v, %T\n", real(c2), real(c2))
fmt.Printf("%v, %T\n", imag(c2), imag(c2))

a2 := 1 + 2i
b2 := 2 + 5.2i

fmt.Println(a2 + b2)
fmt.Println(a2 - b2)
fmt.Println(a2 * b2)
fmt.Println(a2 / b2)
```

```go
(1+2i), complex64
(1+3i), complex128
1, float32
2, float32
1, float64
3, float64
(3+7.2i)
(-1-3.2i)
(-8.4+9.2i)
(0.3994845360824742-0.038659793814433i)
```

## Text types

- Strings
    - UTF-8
    - Immutable
    - Can be concatenated with plus (+) operator
    - Can be coverted to []byte
- Rune
    - UTF-32
    - Alias for int32
    - Special methods normally required to process
        - e.g. strings.Reader#ReadRune

```go
s  := "this is a string"
s2 := "this is also a string"

fmt.Printf("%v, %T\n", s, s)
fmt.Printf("%v, %T\n", s[2], s[2]) // 105, uint8
fmt.Printf("%v, %T\n", string(s[2]), string(s[2])) // i, string

fmt.Printf("%v, %T\n", s + s2, s + s2)

// convert to bytes
sb := []byte(s)
fmt.Printf("%v, %T\n", sb, sb)

// rune
r := 'a'
var r1 rune = 'a'
fmt.Printf("%v, %T\n", r, r) // 97, int32
fmt.Printf("%v, %T\n", r1, r1) // 97, int32
```

```go
this is a string, string
105, uint8
i, string
this is a stringthis is also a string, string
[116 104 105 115 32 105 115 32 97 32 115 116 114 105 110 103], []uint8
97, int32
97, int32
```
