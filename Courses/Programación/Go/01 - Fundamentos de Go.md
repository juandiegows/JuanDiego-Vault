---
tags:
  - golang
  - go
  - platzi
  - programación
---

# 01 — Fundamentos de Go

---

## 📦 Estructura de un Programa

```go
package main

import "fmt"

func main() {
    fmt.Println("Hola, Mundo!")
}
```

```bash
go run main.go      # ejecutar
go build main.go    # compilar
go mod init mi-app  # iniciar módulo
```

---

## 🔤 Variables y Tipos

```go
// Declaración explícita
var nombre string = "Juan"
var edad   int    = 25

// Inferencia de tipo (short declaration)
nombre := "Juan"
edad   := 25

// Constantes
const PI = 3.14159

// Tipos básicos
bool
int, int8, int16, int32, int64
uint, uint8, uint16, uint32, uint64
float32, float64
string
byte   // alias de uint8
rune   // alias de int32 (un caracter Unicode)
```

---

## 🔄 Funciones

```go
// Función simple
func saludar(nombre string) string {
    return "Hola, " + nombre
}

// Múltiples retornos (Go idiomático)
func dividir(a, b float64) (float64, error) {
    if b == 0 {
        return 0, fmt.Errorf("división por cero")
    }
    return a / b, nil
}

// Uso
resultado, err := dividir(10, 2)
if err != nil {
    log.Fatal(err)
}
fmt.Println(resultado) // 5
```

---

## 📦 Slices y Maps

```go
// Slice (array dinámico)
frutas := []string{"manzana", "pera", "uva"}
frutas = append(frutas, "naranja")

// Iterar
for i, fruta := range frutas {
    fmt.Printf("%d: %s\n", i, fruta)
}

// Map (diccionario)
persona := map[string]interface{}{
    "nombre": "Juan",
    "edad":   25,
}

// Verificar existencia
edad, ok := persona["edad"]
if ok {
    fmt.Println("Edad:", edad)
}
```

---

## 🏗️ Structs (como clases)

```go
type Persona struct {
    Nombre string
    Edad   int
}

// Método
func (p Persona) Saludar() string {
    return fmt.Sprintf("Hola, soy %s y tengo %d años", p.Nombre, p.Edad)
}

// Uso
juan := Persona{Nombre: "Juan", Edad: 25}
fmt.Println(juan.Saludar())
```

---

## 🔗 Siguiente
- [[02 - Concurrencia en Go]]
