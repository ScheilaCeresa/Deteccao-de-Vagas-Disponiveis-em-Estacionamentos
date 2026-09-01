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


## Tecnologias Utilizadas

- Java  
- OpenCV  

Motivo: Optamos por essas tecnologias por serem de domínio do grupo, garantindo agilidade no desenvolvimento. A escolha também é compatível com a abordagem adotada, que utiliza métodos tradicionais de PDI, dispensando o uso de bibliotecas mais complexas.
