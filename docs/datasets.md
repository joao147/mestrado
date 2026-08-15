# Códigos e Datasets Abertos para Visão Computacional em Escoamentos Multifásicos

## Visão geral

A disponibilidade de dados abertos é **boa para detecção, segmentação e tracking 2D**, mas ainda **mais limitada para reconstrução 3D multi-view de bolhas**.

| Objetivo                     | Disponibilidade           |
| ---------------------------- | ------------------------- |
| Detecção de bolhas         | **Muito boa**       |
| Segmentação                | **Muito boa**       |
| Tracking 2D                  | **Boa**             |
| Classificação de regime    | **Boa**             |
| Fusão imagem + sensores     | **Boa e crescente** |
| Reconstrução 3D multi-view | **Limitada**        |
| Tracking 3D de bolhas        | **Limitada**        |
| Light-field em multifásicos | **Emergente**       |

---

## Datasets e códigos de maior interesse

### 1. BubblyFlow

**Foco:** detecção e segmentação de bolhas.

- Imagens de bolhas;
- anotações/máscaras;
- dataset disponibilizado publicamente;
- código disponível no GitHub;
- associado a trabalho com SAM 2.1.

**Links:** dataset ([Kaggle](https://www.kaggle.com/datasets/semanurkk/bubblyflow)) · código ([GitHub](https://github.com/Semanur97/BubblyFlow))

**Uso recomendado:** começar com segmentação e reconhecimento de estruturas de bolhas.

---

### 2. Public Dataset of Cropped Bubble Images and Segmentation Masks

**Foco:** segmentação e geração de dados sintéticos.

Disponibilizado no **Zenodo**, contendo:

- imagens reais de bolhas;
- imagens recortadas;
- máscaras de segmentação.

**Uso recomendado:** desenvolvimento e validação de modelos de segmentação.

**Link:** [Zenodo](https://zenodo.org/records/21076241)

---

### 3. Dataset de escoamento bifásico em tubo horizontal

**Foco:** visão computacional + medição experimental + tracking.

Disponibiliza dados de:

- imagens de alta velocidade;
- pressão;
- aceleração;
- fração de vazio;
- contornos das bolhas;
- diâmetros;
- número de bolhas;
- segmentação;
- informações de tracking.

**É particularmente interessante para pesquisa experimental**, pois permite estudar:

```text
imagem
   ↓
segmentação
   ↓
tracking
   ↓
grandezas geométricas
   ↓
correlação com sensores
```

Também é uma base interessante para explorar **fusão de sensores + visão computacional**.

**Links:** dataset ([UNICAMP RedU](https://redu.unicamp.br/dataset.xhtml?persistentId=doi:10.25824/redu/ISMWP4)) · artigo associado ([DOI 10.1016/j.dib.2025.112117](https://doi.org/10.1016/j.dib.2025.112117))

---

### 4. Dataset de cavitação em óleo mineral — Zenodo

**Foco:** caracterização estatística de bolhas/cavitação.

Contém imagens e dados para estimar:

- distribuição de tamanho de bolhas;
- frações de volume/massa;
- outras características do escoamento.

O conjunto tem aproximadamente **1,5 GB**.

**Uso recomendado:** análise estatística e caracterização de populações de bolhas.

**Link:** [Zenodo](https://zenodo.org/records/14272615)

---

### 5. Light-field — dados + código

Não é especificamente um dataset de escoamento multifásico, mas é relevante para a metodologia de **reconstrução 3D por light field**.

Disponibiliza:

- dados de reconstrução volumétrica de partículas;
- código no GitHub (PIV e geração de dados sintéticos);
- software associado ao sistema light-field.

**Uso recomendado:** estudar a metodologia de reconstrução 3D antes de aplicá-la a multifásicos.

**Links:** projeto ([lightfieldpiv.github.io](https://lightfieldpiv.github.io/)) · código PIV ([GitHub](https://github.com/lightfieldpiv/LFPIV)) · geração de dados sintéticos ([GitHub](https://github.com/lightfieldpiv/ParticleGeneration/))

---

### 6. Experimental database of ultrasonic signals, void fraction and movies of bubble column

**Foco:** caracterização de coluna de bolhas por vídeo e por sinais de ultrassom.

Dataset próprio (Araújo, C. C. S.; Fileti, A. M. F., 2024), disponibilizado no **RedU — Repositório de Dados de Pesquisa da Unicamp**, contendo:

- filmes (vídeos) da coluna de bolhas (`movies.rar`);
- sinais de ultrassom em três frequências: 1 MHz, 2 MHz e 5 MHz (`US_1MHz.rar`, `US_2MHz.rar`, `US_5MHz.rar`);
- dados de fração de vazio associados;
- `readme.pdf` com instruções de uso.

Licença CC BY-NC 4.0. Conjunto grande (vídeos + sinais somam dezenas de GB).

**Uso recomendado:** fusão de visão computacional (vídeo) com sensoriamento ultrassônico para estimar fração de vazio e caracterizar o regime da coluna de bolhas — bom candidato para explorar **fusão de sensores + visão computacional** com dados próprios.

**Link:** [RedU (DOI 10.25824/redu/EZTTPJ)](https://doi.org/10.25824/redu/EZTTPJ)

---

### 7. Experimental database of Taylor bubble and spherical caps rising in a stagnant liquid

**Foco:** vídeos de bolhas de Taylor e calotas esféricas subindo em líquido estagnado.

Dataset próprio (Araújo, C. C. S.; Mazza, R. A., 2024), disponibilizado no **RedU**, contendo vídeos (`REDU_videos_bolha alongada.rar`) da ascensão de bolhas alongadas (Taylor) e calotas esféricas.

Licença CC BY-NC 4.0. Arquivo ~276 MB.

**Uso recomendado:** detecção/segmentação e medição de forma, comprimento e velocidade de bolhas alongadas — bom caso de teste para pipelines de visão computacional em bolhas individuais.

**Link:** [RedU (DOI 10.25824/redu/LVYZEJ)](https://doi.org/10.25824/redu/LVYZEJ)

---

### 8. Experimental images database of vertical to horizontal slug flow transition

**Foco:** imagens e vídeos de escoamento slug em transição vertical-horizontal.

Dataset próprio (Araújo, C. C. S.; Toledo, G. P.; Bressani, M.; Pineda, A. J. O.; Mazza, R. A., 2024), disponibilizado no **RedU**, contendo:

- imagens de uma única bolha de ar subindo em coluna de água estagnada;
- vídeos da passagem da bolha alongada em trechos vertical, horizontal e na curva entre essas orientações;
- grade de testes com velocidade superficial do líquido de 0,30 a 1,20 m/s e do gás de 0,30 a 0,90 m/s.

Licença CC BY-NC 4.0. Arquivo `Vertical_Horizontal_Transition.zip` (~3,9 GB).

**Uso recomendado:** estudo de detecção/segmentação e tracking de bolhas alongadas em geometrias com curva, útil para avaliar robustez de métodos de visão computacional frente a mudanças de orientação do escoamento.

**Link:** [RedU (DOI 10.25824/redu/OFXDRZ)](https://doi.org/10.25824/redu/OFXDRZ)

---


## Estratégia prática para reprodução

Uma sequência recomendada seria:

### Etapa 1 — Segmentação

**BubblyFlow**

```text
imagem → segmentação → máscara de bolhas
```

### Etapa 2 — Tracking e medição

**Dataset do tubo horizontal**

```text
imagem → segmentação → tracking → velocidade/diâmetro
                         ↓
                 pressão/aceleração/void fraction
```

### Etapa 3 — Reconstrução 3D

Partir para datasets/metodologias multi-view e, se necessário, construir um pequeno conjunto próprio:

```text
2+ câmeras
   ↓
calibração
   ↓
segmentação
   ↓
correspondência
   ↓
reconstrução 3D
   ↓
tracking 3D
   ↓
parâmetros hidrodinâmicos
```

---

## Oportunidade de pesquisa

A falta de benchmarks públicos completos para **reconstrução 3D de bolhas** pode ser vista como uma oportunidade.

Um possível benchmark seria:

**imagens sincronizadas multi-câmera + calibração + segmentações + ground truth geométrico + tracking + parâmetros hidrodinâmicos + incertezas.**

Isso permitiria comparar:

- stereo vision;
- multi-view reconstruction;
- virtual cameras;
- métodos iterativos;
- deep learning;
- métodos physics-informed.

E estabeleceria uma ponte natural entre:

**visão computacional → problemas inversos → reconstrução 3D → medição experimental → quantificação de incerteza.**
