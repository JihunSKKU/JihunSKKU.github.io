---
title: "Lattigo bfv functions and parameters"
date: 2023-07-18
excerpt: "Lattigo에 있는 각 function들과 parameter들 분석"
toc: true
toc_sticky: true
use_math: true

header:
  teaser: /assets/images/encryption.jpg

categories:
  - 학부연구생
tags:
  - homomorphic encryption
  - Lattigo
  - Go

last_modified_at: 2023-07-18
---

# `NewPlaintext`

`NewPlaintext`는 rlwe/plaintext.go에 정의되어 있는 function이다.

```Go
// NewPlaintext creates a new Plaintext at level `level` from the parameters.
func NewPlaintext(params Parameters, level int) (pt *Plaintext) {
	return &Plaintext{Value: ring.NewPoly(params.N(), level), 
      MetaData: MetaData{Scale: params.defaultScale, IsNTT: params.defaultNTTFlag}}
}
```

## `Plaintext`

`Plaintext`는 같은 directory에 정의되어 있는 struct이다.

```Go
// Plaintext is a common base type for RLWE plaintexts.
type Plaintext struct {
	MetaData
	Value *ring.Poly
}
```

### `ring.NewPoly`

`ring.NewPoly`는 ring/poly.go에 정의되어 있는 function이다.

```Go
// NewPoly creates a new polynomial with N coefficients set to zero and Level+1 moduli.
func NewPoly(N, Level int) (pol *Poly) {
	pol = new(Poly)

	pol.Buff = make([]uint64, N*(Level+1))
	pol.Coeffs = make([][]uint64, Level+1)
	for i := 0; i < Level+1; i++ {
		pol.Coeffs[i] = pol.Buff[i*N : (i+1)*N]
	}

	return
}
```

### `Poly`

`Poly`는 ring/poly.go에 정의되어 있는 struct이다.

```Go
// Poly is the structure that contains the coefficients of a polynomial.
type Poly struct {
	Coeffs [][]uint64 // Dimension-2 slice of coefficients (re-slice of Buff)
	Buff   []uint64   // Dimension-1 slice of coefficient
}
```

## `MetaData`

`MetaData`는 rlwe/metadata.go에 정의되어 있는 struct이다.

```Go
// MetaData is a struct storing metadata.
type MetaData struct {
	Scale
	IsNTT        bool
	IsMontgomery bool
}
```

### `Scale`

`Scale`은 rlwe/scale.go에 정의되어 있는 struct이다.

```Go
// Scale is a struct used to track the scaling factor
// of Plaintext and Ciphertext structs.
// The scale is managed as an 128-bit precision real and can
// be either a floating point value or a mod T
// prime integer, which is determined at instantiation.
type Scale struct {
	Value big.Float
	Mod   *big.Int
}
```


