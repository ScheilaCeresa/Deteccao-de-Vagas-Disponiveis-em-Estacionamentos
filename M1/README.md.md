# Detecção de Vagas Disponíveis em Estacionamentos por Processamento Digital de Imagens

## Sobre o Projeto

Este projeto tem como objetivo investigar e desenvolver uma solução baseada em **Processamento Digital de Imagens (PDI)** para identificar automaticamente se vagas de estacionamento estão **livres ou ocupadas**, a partir de imagens capturadas por câmeras.

A proposta surge da necessidade de otimizar a busca por vagas em estacionamentos de grande porte, reduzindo o tempo de espera e melhorando a experiência do usuário, além de auxiliar na gestão do espaço.

---

## Integrantes

- João Matheus  
- Maria Eduarda de Melo Honorato  
- Scheila Carolini da Silva Ceresa  

---

## Definição do Problema

Em estacionamentos com grande quantidade de vagas, a identificação visual da disponibilidade é frequentemente ineficiente, especialmente em horários de pico. A movimentação constante de veículos torna o processo ainda mais desafiador.

Diante disso, propomos responder à seguinte pergunta:

> **Como utilizar técnicas de Processamento Digital de Imagens para identificar automaticamente vagas de estacionamento livres e ocupadas a partir de uma imagem capturada por uma câmera?**

---

## Delimitacao de Escopo

Inerente a Imagem:

### Desafios contornados:
- Diversidade cromática dos veículos  
- Sombras moderadas  
- Reflexos superficiais  
- Variações globais de iluminação  
- Sujeira no chão  

### Limitações conhecidas:
- Não identifica o tipo de objeto ocupante (veículo, cone, lixeira, etc.)  
- Não trata sobreposição parcial de objetos  
- Não considera diferentes posições ou tamanhos de veículos  
- Não é aplicável em ambientes não estruturados (vagas sem demarcação, formatos irregulares, perspectivas distorcidas)

## Entrada e Saída

| Tipo       | Descrição                                                                 |
|------------|---------------------------------------------------------------------------|
| **Entrada** | Imagens no formato **PNG**, capturadas em ambiente controlado (vagas delimitadas e padronizadas) |
| **Saída**   | Valor booleano: `1` (ocupada) ou `0` (vazia) para cada vaga analisada     |


---

## Solucao

## Arquitetura do Sistema

O sistema é dividido em três fases principais:

### FASE 1: Detecção e Delimitação das Vagas

**Objetivo:** Identificar na imagem quais regiões correspondem a vagas de estacionamento.

#### Pré-processamento da Imagem
- Conversão para escala de cinza (`Imgproc.cvtColor()`)
- Aplicação de filtro Gaussiano (`Imgproc.GaussianBlur()`) ou mediana (`Imgproc.medianBlur()`)
- Detecção de bordas com Canny (`Imgproc.Canny()`) ou Sobel (`Imgproc.Sobel()`)

#### Detecção de Contornos e Formas Retangulares
- Uso de `Imgproc.findContours()` para extração de contornos
- Filtragem por polígono aproximado (`Imgproc.approxPolyDP()`)
- Manutenção apenas de contornos com 4 vértices (retângulos/paralelogramos)

#### Filtragem por Padrões de Tamanho
- Cálculo de área, largura e altura de cada retângulo candidato usando `Imgproc.boundingRect()`
- Comparação com padrões pré-definidos (ex: comprimento entre 150-250px, largura entre 60-100px)
- Valores calibrados conforme a perspectiva da câmera
- Aplicação de relação de aspecto característica de vagas

#### Organização Espacial
- Ordenação dos retângulos em linhas/colunas (grid)
- Atribuição de ID único para cada vaga (ex: Vaga_01, Vaga_02...)
- Armazenamento das coordenadas em `HashMap<Integer, Rect>`

### FASE 2: Extração das Vagas e Pré-processamento

**Objetivo:** Isolar cada vaga e prepará-la para análise de ocupação.

#### Recorte das Regiões de Interesse (ROI)
- Para cada vaga detectada, recortar a subimagem correspondente usando `new Mat(image, rect)`
- Imagem em escala de cinza para processamento

#### Normalização
- Redimensionamento para tamanho padrão (ex: 100x50 px) com `Imgproc.resize()`
- Aplicação de equalização de histograma com `Imgproc.equalizeHist()`

### FASE 3: Classificação Ocupado vs Vazio

**Objetivo:** Determinar se a vaga está ocupada baseado em análise de textura.

#### Métrica de "Sujeira/Ocupação"
- **Desvio Padrão dos Pixels:**
  - Vagas vazias → baixa variação (superfície uniforme do asfalto)
  - Vagas ocupadas → alta variação (texturas, sombras, cores do veículo)
- Implementação usando `Core.meanStdDev()` para cálculo eficiente

#### Métricas Complementares (Opcionais)
- Análise de energia ou entropia (matriz de co-ocorrência - GLCM)
- Contagem de bordas internas (mais bordas = ocupado)

#### Limiarização Dinâmica
- Cálculo do desvio padrão médio das vagas vazias em imagem de referência
- Definição de limiar adaptativo: se desvio > limiar → ocupado

---

## Tecnologias Utilizadas

| Tecnologia | Descrição |
|------------|-----------|
| **Java 11+** | Linguagem de programação principal |
| **OpenCV 4.5+** | Processamento de imagem e visão computacional |
| **Maven/Gradle** | Gerenciamento de dependências |

Optamos por essas tecnologias por serem de domínio do grupo, garantindo agilidade no desenvolvimento. A escolha também é compatível com a abordagem adotada, que utiliza métodos tradicionais de PDI, dispensando o uso de bibliotecas mais complexas.

---

## Estado Atual do Projeto

O projeto ainda não foi iniciado; estamos apenas na fase de ideação da solução.

---

## Link do Video

Link
