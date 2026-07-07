# Proyecto 2 — PageRank sobre redes reales
### IMT2230 — Álgebra Lineal Avanzada y Modelamiento, PUC

**Grupo:** Bastián Pérez, Martín Pérez, Felipe Serrano

## Descripción

Implementación desde cero (sin `networkx.pagerank()` ni funciones automáticas)
del algoritmo PageRank sobre una red real dirigida: *Wikipedia links (csb)*,
la red de hipervínculos de la Wikipedia en kashubio, obtenida de
[KONECT](http://konect.cc/networks/wikipedia_link_csb/).

Se construyen explícitamente la matriz de hipervínculos $H$, su versión
columna-estocástica $S$ y la Matriz de Google $G$, y se calcula PageRank
mediante iteración de potencias implementada manualmente.

## Resultados principales

- Red: 5.561 nodos, 191.255 aristas, densidad 0.62%, 99 nodos colgantes.
- Convergencia en 105 iteraciones (ε = 1e-10), con decaimiento geométrico
  de razón ≈ 0.85 (= α), como predice la teoría.
- Correlación de Pearson entre PageRank e in-degree: 0.38 (moderada).
- El nodo 516 concentra el mayor PageRank (1.8% de la masa total),
  seguido del nodo 2646.

Detalle completo del análisis (P1–P8) en [`informe.pdf`](informe.pdf).

## Cómo ejecutar

1. Clonar este repositorio:
```bash
   git clone https://github.com/Fsli1822/IMT2230-Proyecto-2.git
   cd <IMT2230-Proyecto-2>
```

2. Instalar las dependencias:
```bash
   pip install -r requirements.txt
```

3. Abrir y ejecutar `proyecto_pagerank_csb.ipynb` (Jupyter Notebook o
   JupyterLab). El notebook descarga automáticamente los datos desde
   KONECT en la primera celda de código — no requiere ningún paso manual.

```bash
   jupyter notebook proyecto_pagerank_csb.ipynb
```

## Datos

Fuente: [KONECT — Wikipedia links (csb)](http://konect.cc/networks/wikipedia_link_csb/)
Descarga directa: `http://konect.cc/files/download.tsv.wikipedia_link_csb.tar.bz2`

El notebook descarga y descomprime este archivo automáticamente la primera
vez que se ejecuta; no es necesario hacerlo a mano.

## Estructura del repositorio
.
├── README.md
├── requirements.txt
├── proyecto_pagerank_csb.ipynb   # código completo, P1-P8
├── informe.pdf                  # informe final del proyecto
└── .gitignore

## Notación y convenciones

Se usa la convención columna-estocástica vista en clase:
$G\mathbf{r} = \mathbf{r}$, con $\mathbf{r}$ vector columna y
$G = \alpha S + \frac{1-\alpha}{n}\mathbf{1}\mathbf{1}^T$, $\alpha=0.85$.
