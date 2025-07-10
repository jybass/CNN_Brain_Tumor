# Classificação de Tumor Cerebral com CNN

![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![Keras](https://img.shields.io/badge/Keras-2.x-red.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

Este projeto consiste na construção e treinamento de uma Rede Neural Convolucional (CNN) para classificar imagens de ressonância magnética, identificando a presença ou ausência de tumores cerebrais. O objetivo principal é atingir uma acurácia de validação superior a 95%.

---

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Dataset](#-dataset)
- [Arquitetura do Modelo](#-arquitetura-do-modelo)
- [Resultados](#-resultados)

---

## 🔬 Visão Geral

O notebook `YURI-BASSO-DF-IA-VNW.ipynb` detalha o processo completo, desde o pré-processamento dos dados até a avaliação do modelo. A CNN foi desenvolvida utilizando TensorFlow e a API Keras para criar um classificador binário eficiente para as imagens médicas.

---

## 🖼️ Dataset

O conjunto de dados é composto por 3096 imagens de ressonância magnética coloridas (RGB) com dimensões de 256x256 pixels. As imagens estão divididas em duas classes:

-   **No**: Imagens sem tumor cerebral.
-   **Yes**: Imagens com tumor cerebral.

Os dados foram divididos em conjuntos de treinamento (80%) e validação (20%). Foi aplicada uma camada de `RandomContrast` para realizar data augmentation, melhorando a capacidade de generalização do modelo.

---

## 🏗️ Arquitetura do Modelo

O modelo é sequencial e sua arquitetura é detalhada abaixo:

| Camada (Tipo)              | Shape de Saída          | Parâmetros |
| -------------------------- | ----------------------- | ---------- |
| `random_contrast`          | (None, 256, 256, 3)     | 0          |
| `conv2d` (Conv2D)          | (None, 254, 254, 16)    | 448        |
| `max_pooling2d`            | (None, 84, 84, 16)      | 0          |
| `conv2d_1` (Conv2D)        | (None, 82, 82, 32)      | 4,640      |
| `max_pooling2d_1`          | (None, 27, 27, 32)      | 0          |
| `flatten` (Flatten)        | (None, 23328)           | 0          |
| `dense` (Dense)            | (None, 32)              | 746,528    |
| `dense_1` (Dense)          | (None, 1)               | 33         |

**Total de parâmetros:** 751,649

-   **Função de Ativação:** `ReLU` nas camadas convolucionais e densas, e `Sigmoid` na camada de saída para classificação binária.
-   **Otimizador:** `Adam`.
-   **Função de Perda:** `Binary Crossentropy`.

---

## 📊 Resultados

O modelo foi treinado por 50 épocas e alcançou uma **acurácia de validação de 96.28%**, superando a meta de 95%.

### Gráfico de Acurácia
![Gráfico de Acurácia](https://github.com/jybass/CNN_Brain_Tumor/blob/main/imagens/Print%20do%20gr%C3%A1fico%20de%20acur%C3%A1cia.PNG)

### Matriz de Confusão
A matriz de confusão gerada ao final do treinamento mostra o desempenho detalhado do modelo na classificação das imagens do conjunto de validação.

![Matriz de Confusão](https://github.com/jybass/CNN_Brain_Tumor/blob/main/imagens/Print%20da%20matriz%20de%20confus%C3%A3o.PNG)

---
