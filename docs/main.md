# Visão Computacional Aplicada a Escoamentos Multifásicos

## Objetivo

Construir uma visão inicial da área que conecta:

**escoamento multifásico → aquisição de imagens → processamento de imagem → visão computacional → deep learning → inferência de parâmetros hidrodinâmicos.**

A literatura é relativamente fragmentada. Por isso, a leitura pode ser organizada em duas camadas.

---

## 1. Dez reviews para começar

| #  | Review                                                                                                                                             |  Ano | DOI                                                                                                 | Foco principal                                                                                                                                             |
| -- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ---: | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | **A review of deep learning-based bubble recognition methods** — Ren et al.                                                                 | 2026 | [10.1016/j.flowmeasinst.2026.103204](https://doi.org/10.1016/j.flowmeasinst.2026.103204)             | Detecção, segmentação semântica/por instância, reconstrução e caracterização de bolhas com deep learning.                                        |
| 2  | **Experimental techniques for multiphase flow investigation in energy applications: Advances and recent developments** — Tabrizi & Madejski | 2026 | [10.1016/j.icheatmasstransfer.2026.111576](https://doi.org/10.1016/j.icheatmasstransfer.2026.111576) | Técnicas de visualização e medição: high-speed imaging, shadowgraphy, PIV/PTV, LIF, X-ray, CT, MRI e técnicas multimodais.                           |
| 3  | **Review of Machine Learning for Hydrodynamics, Transport, and Reactions in Multiphase Flows and Reactors** — Zhu et al.                    | 2022 | [10.1021/acs.iecr.2c01036](https://doi.org/10.1021/acs.iecr.2c01036)                                 | Aplicações de ML em multifásicos: reconstrução de imagens, identificação de regimes, previsão de parâmetros e modelos híbridos/physics-informed. |
| 4  | **Particle Image Velocimetry investigations on multiphase flow in fluidized beds: A review** — Neogi et al.                                 | 2023 | [10.1016/j.flowmeasinst.2023.102309](https://doi.org/10.1016/j.flowmeasinst.2023.102309)             | PIV e processamento digital de imagens para caracterização hidrodinâmica de escoamentos multifásicos.                                                  |
| 5  | **Experimental Techniques for Bubble Dynamics Analysis in Microchannels: A Review** — Mohammadi & Sharp                                     | 2013 | [10.1115/1.4023450](https://doi.org/10.1115/1.4023450)                                               | Fundamentos experimentais de imaging, tracking e análise da dinâmica de bolhas.                                                                          |
| 6  | **Application of artificial neural network to multiphase flow metering: A review** — Bahrami et al.                                         | 2024 | [10.1016/j.flowmeasinst.2024.102601](https://doi.org/10.1016/j.flowmeasinst.2024.102601)             | ML aplicado à medição de multifásicos, incluindo regime, fração de vazio e vazão.                                                                   |
| 7  | **Integrating Machine Learning With Sensor Technology for Multiphase Flow Measurement: A Review** — Bao et al.                              | 2024 | [10.1109/jsen.2024.3437292](https://doi.org/10.1109/jsen.2024.3437292)                               | Integração de ML com diferentes sensores e técnicas de medição.                                                                                       |
| 8  | **Application of artificial intelligence technology in the recognition of multiphase flow patterns: A review** — Yang et al.                | 2026 | [10.1016/j.flowmeasinst.2026.103484](https://doi.org/10.1016/j.flowmeasinst.2026.103484)             | Revisão sobre aplicações de IA na identificação de padrões de escoamento multifásico (regimes, estruturas e classificação).                       |
| 9  | **Mechanisms and modeling of bubble dynamic behaviors and mass transfer under gravity: A review** — Yan et al.                              | 2023 | [10.1016/j.ces.2023.118854](https://doi.org/10.1016/j.ces.2023.118854)                               | Revisão sobre dinâmica de bolhas, coalescência/breakup e transferência de massa sob gravidade.                                                         |
| 10 | **Bubble identification from images with machine learning methods** — Hessenkemper et al.                                                   | 2022 | [10.1016/j.ijmultiphaseflow.2022.104169](https://doi.org/10.1016/j.ijmultiphaseflow.2022.104169)     | Avaliação de métodos de machine learning para identificação e classificação de bolhas a partir de imagens.                                          |
| 11 | **Bubble recognizing and tracking in a plate heat exchanger by using image processing and convolutional neural network** — Wang et al.      | 2021 | [10.1016/j.ijmultiphaseflow.2021.103593](https://doi.org/10.1016/j.ijmultiphaseflow.2021.103593)     | Aplicação prática de processamento de imagens e CNN para detectar e rastrear bolhas em trocadores de calor.                                             |

---

## 2. Ordem de leitura sugerida

### Nível 1 — Visão computacional e visualização

1. **Ren et al. (2026)** — bubble recognition
2. **Tabrizi & Madejski (2026)** — técnicas de visualização
3. **Mohammadi & Sharp (2013)** — fundamentos experimentais de imaging
4. **PIV review (2023)** — processamento de imagens para grandezas hidrodinâmicas

### Nível 2 — IA aplicada aos dados e imagens

5. **Review of Machine Learning for Hydrodynamics... (2022)**
6. **ANN for multiphase flow metering (2024)**
7. **ML + Sensor Technology (2024)**

## 3. Elabore perguntas a medida que for lendo os documentos

Exemplo:

> **"Como transformar uma imagem em variáveis físicas mensuráveis?"**

Entre as grandezas de interesse estão:

- diâmetro de bolha;
- distribuição de tamanho;
- velocidade;
- trajetória;
- deformação;
- aspect ratio;
- área interfacial;
- número de bolhas;
- coalescência e breakup;
- fração de vazio;
- estrutura espacial;
- regime de escoamento.

---

## 4. Segunda linha: imagem → representação → inferência física

Depois de compreender a detecção e caracterização de bolhas, o próximo passo é estudar como uma imagem pode ser usada para **inferir propriedades físicas do escoamento**.

A cadeia conceitual é:

**imagem → representação → inferência física**

Isso conecta:

**CNN → embeddings → representação latente → regressão → incerteza → physics-informed ML → fusão de sensores**

O review de ML em multifásicos de 2022 é particularmente útil nessa etapa, pois aborda aplicações como reconstrução de imagens, identificação de regimes e previsão de parâmetros relevantes.

---

## 5. Termos de busca

### 5.1 Bubble / image analysis

```text
"bubble detection" + "two-phase flow"
"bubble segmentation" + "two-phase flow"
"bubble tracking" + "multiphase flow"
```

### 5.2 Flow visualization

```text
"flow visualization" + "multiphase flow"
"high-speed imaging" + "multiphase flow"
"image-based measurement" + "two-phase flow"
```

### 5.3 Computer vision / deep learning

```text
"computer vision" + "multiphase flow"
"deep learning" + "bubble detection"
"deep learning" + "bubble segmentation"
```

### 5.4 Physical inference

```text
"image-based measurement" + "void fraction"
"image-based measurement" + "flow regime"
"vision-based" + "multiphase flow measurement"
```

A quarta família é especialmente importante porque desloca o foco de **processamento de imagens** para **medição experimental baseada em visão computacional**.

---

## 6. Mapa conceitual da área

```text
                    ESCOAMENTO MULTIFÁSICO
                            │
                            ▼
                    AQUISIÇÃO DE IMAGEM
                            │
             ┌──────────────┴──────────────┐
             ▼                             ▼
     Processamento clássico          Deep Learning
             │                             │
     ┌───────┼────────┐             ┌──────┼────────┐
     ▼       ▼        ▼             ▼      ▼        ▼
 threshold  edges  watershed       CNN   U-Net   YOLO
             │                             │
             └──────────────┬──────────────┘
                            ▼
                    DETECÇÃO / SEGMENTAÇÃO
                            │
                            ▼
                  CARACTERIZAÇÃO DA FASE
                            │
       ┌────────────┬───────┼───────────┐
       ▼            ▼       ▼           ▼
   tamanho       posição  velocidade  forma
       │            │       │           │
       └────────────┴───────┴───────────┘
                            ▼
                  INFERÊNCIA HIDRODINÂMICA
                            │
       ┌────────────────────┼────────────────────┐
       ▼                    ▼                    ▼
   void fraction       flow regime          vazão
       │                    │                    │
       └────────────────────┼────────────────────┘
                            ▼
                    REPRESENTAÇÃO LATENTE
                            │
                            ▼
                 INFERÊNCIA FÍSICA + ML
                            │
             ┌──────────────┼──────────────┐
             ▼              ▼              ▼
          incerteza    physics-informed   sensor fusion
```

## 7. O que é possível obter a partir da análise de imagens

Além do mapa conceitual resumido acima, a partir de imagens (single-view ou multi-view) e técnicas de visão computacional é possível extrair / estimar diretamente as seguintes grandezas e informações:

- Contagem de bolhas e número de objetos presentes (bubble count).
- Distribuição de tamanhos (histograma de diâmetros, D32, D10, etc.).
- Trajetórias e velocidades 2D/3D (tracking, PTV, PIV/Tomo-PIV para campos de velocidade).
- Forma e deformação (aspect ratio, esfericidade, modos de forma, curvatura local).
- Eventos dinâmicos: coalescência, breakup, separação e colisões.
- Área interfacial e concentração de área específica (IAC, interfacial area concentration) quando reconstruído volumetricamente.
- Fração de vazio local e volumétrica (area- or volume-based void fraction).
- Estimativas de transferência de massa/fluxos locais (a partir de correlações imagem→k_La ou modelos híbridos ML+PFM).
- Campos vetoriais de velocidade e gradientes (via PIV/PTV/Tomo-PIV) que permitem calcular tensões, esforços de cisalhamento e dispersão.
- Características estatísticas e espaciais (funções de correlação, estrutura espacial, clustering de bolhas).
- Mapas 3D de concentração/fase quando se usa reconstrução multi-view ou tomográfica.

Essas quantidades podem ser extraídas de forma direta (via processamento de imagem clássico), por aprendizado profundo (detecção/segmetação/tracking com redes) ou por combinações híbridas (p.ex. CNN para segmentação + PTV para tracking + modelos físicos para inferência de massa/energia).

## 8. Reconstrução 3D a partir de múltiplas câmeras — leituras recomendadas

A reconstrução 3D de escoamentos multifásicos por visão computacional busca recuperar a estrutura espacial do escoamento (posição, forma, volume, trajetória, área interfacial) a partir de imagens 2D de múltiplas câmeras, sem depender necessariamente de PIV/Tomo-PIV. Trata-se, em essência, de um **problema inverso**: a estrutura 3D é desconhecida e as câmeras fornecem apenas suas projeções 2D, de modo que se busca estimar $\hat{\mathbf{x}} = \mathcal{F}^{-1}(\mathbf{y})$ — muitas vezes mal-posto, exigindo regularização ou restrições físicas.

A cadeia metodológica típica é: **calibração das câmeras → aquisição → segmentação/detecção → correspondência entre vistas → reconstrução 3D → rastreamento temporal → inferência de parâmetros hidrodinâmicos**, com quantificação de incerteza ao longo do processo. As principais abordagens de reconstrução são stereo vision, multi-view reconstruction, virtual cameras, light-field imaging e deep learning. Os desafios centrais incluem poucas vistas, oclusão/sobreposição de bolhas, correspondência entre vistas, erro de calibração, refração gás–líquido e propagação de incerteza — daí o interesse em incorporar informação física para restringir a solução.

(Detalhamento completo em [reconstrucao_3d_escoamentos.md](reconstrucao_3d_escoamentos.md).)

Uma alternativa à reconstrução 3D — combinar imagens de múltiplas câmeras para formar uma única imagem espacialmente estendida do escoamento, sem buscar profundidade — é discutida em [visao_panoramicas.md](visao_panoramicas.md).

---

## 9. Linhas de pesquisa e possibilidades

### 1. Optical flow aplicado diretamente ao escoamento

Em vez de identificar cada bolha e rastreá-la individualmente, você estima o campo de movimento aparente diretamente dos pixels. Optical flow é justamente uma das linhas clássicas de visão computacional para estimar movimento, e hoje existem métodos baseados em deep learning bastante sofisticados.

Para multifásicos, isso abre:

**imagem → optical flow → campo de movimento → grandezas hidrodinâmicas**

É diferente de PIV porque não precisa necessariamente de partículas traçadoras e poderia trabalhar diretamente com interfaces/estruturas das bolhas.

Uma extensão ainda mais interessante seria:

**optical flow + física do escoamento → physics-informed optical flow.**

---

### 2. Scene flow 3D

É uma evolução natural do optical flow.

Optical flow fornece:

**deslocamento aparente 2D.**

Scene flow tenta obter:

**movimento 3D dos objetos.**

Assim você poderia estudar:

**multi-camera → geometria 3D → scene flow → trajetória/velocidade 3D das bolhas.**

Há inclusive reviews que tratam conjuntamente optical flow e scene flow como uma área consolidada de visão computacional.

Isso seria uma alternativa interessante ao PTV/Tomo-PIV.

---

### 3. Segmentação + rastreamento + identidade da bolha

Um problema mais difícil do que o tracking convencional é:

manter a identidade individual das bolhas durante nascimento, deformação, coalescência e breakup.

Isso é essencialmente um problema de multi-object tracking com eventos topológicos.

Exemplo:

```text
bolha A + bolha B
       ↓
   coalescência
       ↓
    bolha C
```

ou:

```text
bolha A
   ↓
breakup
   ↓
A1 + A2 + A3
```

Isso poderia ser uma área inteira de pesquisa: **topology-aware bubble tracking**.

---

### 4. Inferência de grandezas 3D sem reconstruir explicitamente o 3D

Essa talvez seja uma das mais interessantes.

Em vez de fazer:

**imagem → reconstrução 3D → volume**

poderíamos fazer diretamente:

**imagem 2D → volume estimado**

ou

**sequência 2D → fração de vazio 3D estimada.**

Isso é um problema inverso aprendido por deep learning.

A vantagem é que o modelo pode aprender relações estatísticas que tornam a reconstrução explícita desnecessária.

E isso conecta diretamente com medição indireta:

**medição indireta + modelo físico/ML + incerteza**

---

### 7. Benchmarking físico de modelos de visão

Outra lacuna interessante: em vez de perguntar apenas

> **"Qual rede segmenta melhor?"**

perguntar:

> **"Qual rede produz a melhor medição física?"**

Por exemplo, comparar modelos por:

- IoU;
- Dice;

mas também:

- erro no diâmetro;
- erro no volume;
- erro na fração de vazio;
- erro na velocidade;
- viés estatístico;
- propagação de incerteza.

Isso muda completamente o critério de avaliação.

---

### 8. Imagem + conhecimento físico

Existe uma linha crescente de physics-data fusion para reconhecimento de padrões multifásicos. Um review de 2026 sobre IA em reconhecimento de regimes destaca justamente a direção de combinar modelos de dados com informação física para melhorar interpretabilidade e generalização.

Isso poderia significar:

```text
CNN → características visuais

Reynolds, Weber, Froude, propriedades físicas, geometria

→

modelo generalizável entre diferentes fluidos e condições.
```

Isso seria particularmente interessante para superar um problema comum: um modelo treinado em água-ar não necessariamente funciona em óleo-ar.

---

### Mapa completo da área

```text
             VISÃO COMPUTACIONAL EM MULTIFÁSICOS
                            │
       ┌────────────────────┼────────────────────┐
       │                    │                    │
       ▼                    ▼                    ▼
   DETECÇÃO             MOVIMENTO            RECONSTRUÇÃO
       │                    │                    │
   segmentação        optical flow          3D multi-view
   classificação      tracking              light-field
   regime             scene flow            stereo
       │                    │                    │
       └───────────────┬────┴────────────────────┘
                       ▼
                  REPRESENTAÇÃO
                       │
             CNN / embeddings / ViT
                       │
       ┌───────────────┼────────────────┐
       ▼               ▼                ▼
  INFERÊNCIA       SENSOR FUSION    INCERTEZA
       │               │                │
       └───────────────┼────────────────┘
                       ▼
              MEDIÇÃO HIDRODINÂMICA
                       │
       void fraction / velocity / regime
       bubble size / interface / flow rate
```

---

## 10. Datasets e códigos abertos

Um levantamento de datasets e códigos abertos relevantes para as linhas descritas acima (detecção/segmentação de bolhas, tracking, reconstrução 3D, light-field), incluindo os datasets próprios de coluna de bolhas e de bolha de Taylor, está em [datasets.md](datasets.md).
