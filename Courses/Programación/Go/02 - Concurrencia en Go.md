---
tags:
  - golang
  - go
  - concurrencia
  - goroutines
  - channels
---

# 02 — Concurrencia en Go: Goroutines y Channels

---

## 🚀 Goroutines

Una goroutine es una función que corre **concurrentemente** con otras. Es muy ligera (~2KB de stack inicial vs ~1MB de un thread de OS).

```go
package main

import (
    "fmt"
    "time"
)

func saludar(nombre string) {
    fmt.Printf("Hola, %s!\n", nombre)
}

func main() {
    go saludar("Juan")   // goroutine
    go saludar("María")  // goroutine

    time.Sleep(100 * time.Millisecond) // esperar
    fmt.Println("Fin del programa")
}
```

---

## 📡 Channels

Los channels permiten que las goroutines se comuniquen de forma segura.

```go
func suma(a, b int, resultado chan int) {
    resultado <- a + b // enviar al channel
}

func main() {
    resultado := make(chan int)

    go suma(5, 3, resultado)

    valor := <-resultado // recibir del channel
    fmt.Println("Resultado:", valor) // 8
}
```

---

## 🔒 WaitGroup (Sincronización)

```go
import "sync"

func main() {
    var wg sync.WaitGroup

    for i := 0; i < 5; i++ {
        wg.Add(1)
        go func(id int) {
            defer wg.Done()
            fmt.Printf("Goroutine %d terminó\n", id)
        }(i)
    }

    wg.Wait() // espera a que todas terminen
    fmt.Println("Todas las goroutines terminaron")
}
```

---

## 🔗 Volver al Índice
- [[Index]]
- [[../../Index|Todos los Cursos]]
