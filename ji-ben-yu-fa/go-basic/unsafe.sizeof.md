---
description: >-
  Sizeof takes an expression x of any type and returns the size in bytes of a
  hypothetical variable v as if v was declared via var v = x. 返回在內存中的字節大小
---

# unsafe.Sizeof

#### 返回在內存中的字節byte大小

```
package main

import (
	"fmt"
	"unsafe"
)

func main() {

	var i64 int64
	fmt.Printf("int64: %d \n", unsafe.Sizeof(i64))
	var ui64 uint64
	fmt.Printf("ui64: %d \n", unsafe.Sizeof(ui64))

	var b1 bool
	fmt.Printf("b1: %d \n", unsafe.Sizeof(b1))

	var s1 string
	fmt.Printf("s1: %d \n", unsafe.Sizeof(s1))
	var f32 float32
	fmt.Printf("f32: %d \n", unsafe.Sizeof(f32))
	var f64 float64
	fmt.Printf("f64: %d \n", unsafe.Sizeof(f64))
	var c64 complex64
	fmt.Printf("c64: %d \n", unsafe.Sizeof(c64))

	var c128 complex128
	fmt.Printf("c128: %d \n", unsafe.Sizeof(c128))
}

```
