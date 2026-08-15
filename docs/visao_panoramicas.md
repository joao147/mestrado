# Visão panorâmica de escoamentos por múltiplas câmeras

## 1. Ideia central

Uma alternativa à reconstrução 3D é combinar imagens de **duas ou mais câmeras** para formar uma única imagem espacialmente estendida do escoamento.

```text
Câmera 1 + Câmera 2 + ... 
        ↓
registro geométrico
        ↓
warping / reprojeção
        ↓
blending
        ↓
imagem panorâmica do escoamento
```

A técnica pertence à área de **image stitching / image mosaicing**. O pipeline clássico envolve registro, transformação geométrica e composição das imagens. citeturn563975search1turn563975search4

A diferença para reconstrução 3D é fundamental:

**Reconstrução 3D:** imagens 2D → geometria 3D

**Visão panorâmica:** imagens 2D → imagem 2D contínua de maior extensão

---

## 2. Aplicação a escoamentos multifásicos

Imagine duas câmeras observando regiões consecutivas de um tubo:

```text
Câmera 1                    Câmera 2
┌───────────┐              ┌───────────┐
│           │              │           │
│  bolhas   │              │  bolhas   │
│           │              │           │
└─────┬─────┘              └─────┬─────┘
      └────────── overlap ───────┘
                    ↓
          ┌─────────────────────┐
          │  escoamento longo   │
          │ ○  ○   ○ ○    ○     │
          │   ○   ○      ○      │
          └─────────────────────┘
```

O objetivo não é necessariamente obter profundidade, mas **aumentar o campo de visão mantendo resolução espacial e temporal**.

Isso pode permitir observar:

- evolução das bolhas;
- coalescência e breakup;
- desenvolvimento espacial do escoamento;
- transições de regime;
- distribuição espacial das estruturas;
- correlação entre estruturas distantes;
- trajetórias em uma região muito maior.

---

## 3. Metodologia experimental

### Aquisição

- duas ou mais câmeras sincronizadas;
- campos de visão parcialmente sobrepostos;
- iluminação uniforme;
- calibração geométrica relativa;
- idealmente câmera e exposição equivalentes.

### Processamento

```text
imagens brutas
    ↓
correção óptica
    ↓
registro entre câmeras
    ↓
transformação geométrica
    ↓
alinhamento
    ↓
seam finding
    ↓
blending
    ↓
imagem panorâmica
```

Os principais problemas de mosaicing tradicional incluem variações de iluminação, distorção, ruído e objetos em movimento, que podem produzir *ghosting* e contornos duplicados. citeturn563975search1

Em multifásicos, o desafio é maior porque **as próprias bolhas se movimentam e deformam**.

---

## 4. O principal desafio científico

O stitching convencional assume que as diferentes imagens representam essencialmente a mesma cena.

No escoamento isso não é necessariamente verdade:

```text
Câmera 1          Câmera 2

bolha A ───────→
       muda de forma

bolha B ─────────→
       muda de posição
```

Assim, um método baseado exclusivamente em SIFT/ORB + homografia pode produzir artefatos quando tenta unir estruturas que mudaram entre as aquisições.

Uma possível contribuição científica seria desenvolver **stitching orientado à física do escoamento**, utilizando:

- geometria conhecida do tubo;
- calibração das câmeras;
- optical flow;
- tracking de bolhas;
- máscaras de segmentação;
- velocidade estimada;
- modelo de deformação das interfaces.

---

# 5. Possibilidades de linhas de pesquisa

## Linha 1 — Proof of concept

### *Multi-camera image stitching for extended visualization of multiphase flows*

**Pergunta:** É possível gerar uma imagem espacialmente estendida de um escoamento multifásico com qualidade suficiente para análise quantitativa?

Comparar:

**uma câmera vs. duas câmeras vs. imagem panorâmica**

Métricas:

- erro de alinhamento;
- resolução;
- artefatos na região de overlap;
- continuidade das interfaces;
- estabilidade temporal.

**Complexidade:** baixa.

---

## Linha 2 — Stitching robusto para bolhas em movimento

### *Motion-aware image stitching for visualization of bubbly flows*

Modificar o stitching convencional para considerar que as bolhas:

- deslocam-se;
- deformam-se;
- coalescem;
- desaparecem/reaparecem.

Possível arquitetura:

```text
registro geométrico
        +
segmentação das bolhas
        +
optical flow / tracking
        ↓
stitching com consciência de movimento
```

**Pergunta:** O conhecimento do movimento das estruturas reduz os artefatos de composição?

**Complexidade:** média.

---

## Linha 3 — Mosaico espaço-temporal

### *Spatiotemporal panoramic imaging of multiphase flows*

Em vez de gerar apenas uma imagem panorâmica, gerar uma **sequência panorâmica temporal**.

Isso permitiria construir:

**posição espacial × tempo**

e estudar:

- propagação de estruturas;
- velocidade;
- frequência de passagem;
- coalescência;
- evolução do regime.

A ideia é particularmente interessante porque transforma múltiplas câmeras em uma espécie de **janela espacial expandida de alta taxa temporal**.

**Complexidade:** média/alta.

---

## Linha 4 — Tracking em domínio panorâmico

### *Extended-field bubble tracking using multi-camera image mosaicing*

Pipeline:

```text
múltiplas câmeras
      ↓
panorama
      ↓
segmentação
      ↓
tracking
      ↓
trajetórias longas
```

A hipótese é que o campo de visão maior permita acompanhar uma bolha ou estrutura por mais tempo e, portanto, obter estimativas mais robustas de:

- velocidade;
- aceleração;
- trajetória;
- deformação;
- lifetime;
- coalescência/breakup.

**Complexidade:** média/alta.

---

## Linha 5 — Quantificação de desenvolvimento espacial

### *Large-field image-based characterization of developing multiphase flows*

Usar o mosaico para observar simultaneamente diferentes posições ao longo da tubulação.

Isso permitiria estudar:

```text
entrada → desenvolvimento → transição → regime desenvolvido
```

e medir a evolução espacial de:

- fração de vazio;
- densidade de bolhas;
- distribuição de diâmetro;
- velocidade;
- frequência de coalescência;
- regime de escoamento.

**Potencial científico:** alto.

---

## Linha 6 — Fusão entre visão panorâmica e sensores

### *Multi-camera panoramic imaging combined with pressure/ultrasound sensing for multiphase flow characterization*

Uma possibilidade particularmente alinhada com instrumentação seria combinar:

**imagem panorâmica + pressão + ultrassom + outros sensores**

Por exemplo:

```text
Imagem panorâmica ──┐
Pressão ────────────┼──→ modelo de inferência
Ultrassom ──────────┤
Aceleração ─────────┘
```

A grande vantagem seria associar **estrutura espacial observada** às respostas integradas dos sensores.

---

## Linha 7 — Visão panorâmica como benchmark para ML

### *Extended-field imaging for machine learning-based multiphase flow pattern recognition*

Comparar modelos treinados com:

- imagem individual;
- sequência temporal;
- imagem panorâmica;
- imagem panorâmica + sinais de sensores.

Pergunta:

> **O aumento do campo de visão melhora a representação aprendida do regime de escoamento?**

Isso conecta diretamente:

**computer vision → representation learning → flow-pattern recognition.**

---

## Linha 8 — Stitching físico-informado

### *Physics-informed image stitching for multiphase flow visualization*

Em vez de tratar as imagens como fotografias genéricas, incorporar restrições físicas:

- geometria do tubo;
- continuidade espacial;
- conservação da identidade das estruturas;
- velocidade máxima plausível;
- direção predominante do escoamento;
- deformação admissível das bolhas.

O problema poderia ser formulado como uma otimização:

$$
\hat{T}
=
rg\min_T
\left[
L_{image}(T)
+
\lambda L_{physics}(T)

ight]
$$

onde `L_image` mede o erro de registro e `L_physics` penaliza soluções fisicamente inconsistentes.

**Potencial:** alto e metodologicamente original.

---

# 6. Relação com reconstrução 3D

As duas linhas são complementares:

```text
                 Multi-camera imaging
                         │
             ┌───────────┴───────────┐
             ▼                       ▼
      Imagem panorâmica          Reconstrução 3D
             │                       │
        grande campo             profundidade
             │                       │
       tracking longo          geometria 3D
             │                       │
             └───────────┬───────────┘
                         ▼
                parâmetros físicos
```

A reconstrução 3D tenta resolver a **profundidade**.

O mosaico panorâmico tenta aumentar a **extensão espacial observável**.

Para muitos experimentos multifásicos, a segunda abordagem pode ser muito mais simples e ainda preservar alta resolução temporal.

---

# 7. Referências metodológicas para começar

### Image mosaicing

**Pandey, A.; Pati, U. C. — Image mosaicing: A deeper insight** (2019). *Image and Vision Computing*, 89, 236–257. [DOI: 10.1016/j.imavis.2019.07.002](https://doi.org/10.1016/j.imavis.2019.07.002)

Review geral sobre mosaicing, cobrindo registro, warping, blending e principais dificuldades, com classificação de mais de 100 algoritmos por domínio de processamento, aplicação e tipo de imagem. É uma boa referência metodológica para a base de visão computacional — inclusive discute aquisição com múltiplas câmeras fixas, não apenas uma câmera em movimento.

### Mosaicing incremental

**McLauchlan, P. F.; Jaenicke, A. — Image mosaicing using sequential bundle adjustment** (2002). *Image and Vision Computing*, 20(9–10), 751–759. [DOI: 10.1016/S0262-8856(02)00064-1](https://doi.org/10.1016/S0262-8856(02)00064-1)

Aborda a construção de mosaicos panorâmicos precisos a partir de ajuste geométrico (bundle adjustment) sequencial e autocalibração de câmera, incluindo distorção radial.

### Contexto multifásico

**Wang, H. et al. — A 3D reconstruction method of bubble flow field based on multi-view images by bi-direction filtering maximum likelihood expectation maximization algorithm** (2023). *International Journal of Multiphase Flow*, 168, 104480. [DOI: 10.1016/j.ijmultiphaseflow.2023.104480](https://doi.org/10.1016/j.ijmultiphaseflow.2023.104480)

Trabalho recente que já explora sistema multi-câmera para medir estruturas de bolhas, embora com objetivo de reconstrução 3D (não de mosaicing 2D). Mostra que **calibração multi-câmera e registro de imagens de bolhas** são tecnologicamente viáveis no contexto multifásico.

---

# 8. Linha de pesquisa recomendada

Uma progressão particularmente interessante seria:

```text
Etapa 1
Stitching geométrico básico
        ↓
Etapa 2
Stitching + segmentação
        ↓
Etapa 3
Stitching + tracking
        ↓
Etapa 4
Mosaico espaço-temporal
        ↓
Etapa 5
Inferência de parâmetros hidrodinâmicos
        ↓
Etapa 6
Fusão com pressão / ultrassom
        ↓
Etapa 7
Stitching physics-informed
```

A pergunta científica mais forte talvez não seja simplesmente **“como juntar duas imagens?”**, mas:

> **“Quanto a ampliação do campo de visão por múltiplas câmeras melhora a capacidade de observar, rastrear e inferir estruturas hidrodinâmicas em escoamentos multifásicos?”**

Isso transforma uma técnica clássica de *computer vision* — **image mosaicing** — em uma possível **técnica de medição experimental para escoamentos multifásicos**.
