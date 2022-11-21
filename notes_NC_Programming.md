# NC Programming Notes

## Számolási Kéépletek

```
Vc = D * Pi * n / 1000
Peff = nü * Pm
Psz = Peff = f * ap * Vc * kc
Fc = A * kc = ap * f * kc
Q = ap * f * Vc
h = sinK * f
Kc = Kc1 * h^-mc
A = ap * f
```

## Transzformációk

### Forgatás

G68 p q R
G69
p q - forgatás középpontja
R - forgatás szöge
Ha p q valmelyike nem kap értéket akkor a forgatás középpontjának a pillanatnyi tengely-pozíciót vesszük.

### Léptékezés

G51 v P
G50
v - léptékezés középpontja
P - léptékezés arányszáma

### Tükrözés

G51.1 v
G50.1 v
v - a tengely címe melyen a tükrözést végezni kívánjuk

## Sample kódok egyes megoldásokhoz

### Körzseb marása spirállal

G0 X0 Y0 Z2
G1 X[D/2] G41
G3 I-[D/2] Z-12 L7
I-[D/2]
G1 X0 Y0 G40

### Körzseb letörése

G10 P[T] L12 R1 (letöréshez átmérő módosítása)

G1 Z-1.5
G1 X[D/2] G41
G3 I-[D/2]
G1 X0 Y0 G40

G10 P[T] L12 R5

### Szögletes zseb marása

P9999 X[hossz] Y[szélesség] Z[mélység] R[lekerekítés] K[Zráállás]

### Nagyoláshoz Automatikus Javítás bekapcsolása [Paraméter Módosítása]

G10 L52
N1403 Q0 R1
N1403 Q1 R1
G11

## G10 Paramétermódosítás:

G10 L52
N1503 Q3 R1 (N a paraméter száma, Q a bit száma 0-7, R a bit új értéke)
G11

### Használt paraméter gyűjtemény:

#### I J ABS KOORDINÁTA: EXECUTION CONFIG 2ES BIT 1-BE

#### m98 p9000 = m140 ha át van írva a paraméter
