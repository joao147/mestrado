# Reconstrução 3D de Escoamentos por Visão Computacional

## 0. Quando vale a pena reconstruir em 3D

Vale a pena reconstruir em 3D quando a informação que você quer medir é intrinsecamente tridimensional. Em uma imagem 2D, a projeção mistura profundidade com tamanho, posição e sobreposição das estruturas; assim, duas configurações físicas diferentes podem gerar imagens muito parecidas. A reconstrução 3D permite recuperar, ao menos aproximadamente, posição, volume, área interfacial, forma, distância entre bolhas e trajetória espacial, além de reduzir problemas de oclusão e sobreposição. Isso é particularmente relevante em escoamentos multifásicos porque a física depende fortemente da estrutura espacial: uma fração de vazio inferida de uma única imagem pode ser afetada pela distribuição das bolhas ao longo da profundidade, enquanto em 3D pode-se estimar diretamente volume de gás e estrutura da interface. Por outro lado, 3D não é automaticamente melhor: se o objetivo for apenas classificar o regime, detectar uma bolha, estimar uma grandeza correlacionada com uma projeção 2D ou obter alta taxa temporal, a imagem 2D pode ser muito mais simples, barata e robusta. A pergunta correta, portanto, é: qual informação física está sendo perdida pela projeção 2D e essa informação perdida é importante para a variável que quero estimar?

---

## 1. O que é

Existe uma área de **visão computacional 3D aplicada a escoamentos multifásicos** que busca reconstruir a estrutura espacial do escoamento a partir de imagens de câmeras, sem necessariamente utilizar PIV ou Tomo-PIV.

O foco é reconstruir, por exemplo:

- posição 3D das bolhas;
- forma e volume;
- trajetória;
- velocidade;
- deformação;
- coalescência e breakup;
- área interfacial;
- distribuição espacial.

A ideia central é:

**câmeras → imagens 2D → reconstrução → estrutura 3D → parâmetros hidrodinâmicos**

---

## 2. Por que é um problema inverso?

Sim. Em geral, trata-se de um **problema inverso**.

A estrutura 3D real do escoamento é desconhecida, enquanto as câmeras fornecem apenas suas **projeções 2D**. A partir dessas observações, procura-se inferir a geometria 3D que melhor explica as imagens.

De forma conceitual:

**estrutura 3D desconhecida → projeções nas câmeras → imagens observadas**

No problema inverso, fazemos o caminho contrário:

**imagens observadas → estimativa da estrutura 3D**

O problema pode ser mal-posto, pois diferentes estruturas 3D podem produzir projeções semelhantes.

---

## 3. Metodologia geral

A cadeia metodológica típica é:

```text
Calibração das câmeras
        ↓
Aquisição de imagens
        ↓
Segmentação / detecção das bolhas
        ↓
Correspondência entre vistas
        ↓
Reconstrução 3D
        ↓
Rastreamento temporal
        ↓
Parâmetros hidrodinâmicos
        ↓
Incerteza da reconstrução
```

### Etapas

**1. Calibração**

Determinação da geometria das câmeras e, quando necessário, dos efeitos ópticos e de refração.

**2. Aquisição**

Imagens sincronizadas de duas ou mais vistas ou, em algumas abordagens, uma câmera light-field.

**3. Segmentação**

Identificação das bolhas/interfaces em cada imagem.

**4. Correspondência**

Determinação de quais regiões ou pontos em diferentes imagens correspondem ao mesmo objeto físico.

**5. Reconstrução**

Estimativa da posição ou superfície 3D utilizando, por exemplo:

- triangulação estereoscópica;
- multi-view reconstruction;
- métodos iterativos;
- virtual cameras;
- restrições geométricas ou físicas;
- deep learning.

**6. Tracking**

A reconstrução é repetida ao longo do tempo para obter trajetórias e velocidades.

**7. Inferência física**

A geometria 3D passa a ser utilizada para calcular grandezas como volume, área, velocidade, deformação e fração de vazio.

---

## 4. Principais abordagens

| Abordagem                           | Ideia                                                                                               |
| ----------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Stereo vision**             | Duas vistas permitem estimar profundidade por triangulação.                                       |
| **Multi-view reconstruction** | Várias câmeras fornecem diferentes projeções da mesma estrutura.                                |
| **Virtual camera**            | Cria vistas adicionais ou impõe restrições para melhorar uma reconstrução com poucas câmeras. |
| **Light-field imaging**       | Uma única aquisição fornece informação angular/de profundidade.                                |
| **Deep learning**             | A rede aprende a relacionar imagens 2D com geometria ou representação 3D.                         |

---

## 5. Diferença para PIV / Tomo-PIV

| Técnica                               | Principal objetivo                |
| -------------------------------------- | --------------------------------- |
| **PIV**                          | Campo de velocidade 2D            |
| **Tomo-PIV**                     | Campo de velocidade 3D            |
| **Reconstrução 3D de bolhas**  | Geometria/posição 3D das bolhas |
| **Stereo vision**                | Profundidade e posição 3D       |
| **Light-field**                  | Profundidade/estrutura 3D         |
| **Deep-learning reconstruction** | Inferência de estrutura 3D       |

---

## 6. Onde está o desafio científico?

Os principais problemas são:

- poucas vistas para uma estrutura 3D complexa;
- bolhas sobrepostas;
- oclusão;
- deformação das interfaces;
- correspondência entre bolhas;
- erro de calibração;
- refração na interface gás–líquido;
- iluminação;
- resolução temporal;
- propagação de incerteza.

Por isso, a reconstrução pode se beneficiar de **informação física adicional** para restringir a solução.

---


## 8. Uma visão moderna da área

A evolução conceitual pode ser vista como:

**Imagem 2D → detecção → segmentação → correspondência → reconstrução 3D → tracking → inferência física**

E uma linha moderna acrescenta:

**→ deep learning → representação latente → reconstrução/inferência com incerteza**

Isso aproxima a visão computacional 3D de:

**problemas inversos + visão computacional + aprendizado de máquina + física do escoamento + quantificação de incerteza.**
