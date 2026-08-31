# **Projeto Aplicado Longitudinal — M1**





### Detecção de Vagas Disponíveis em Estacionamentos por Processamento Digital de Imagens



Integrantes

- João Matheus
- Maria Eduarda de Melo Honorato
- Scheila Carolini da Silva Ceresa
---





###### 1\. Definição do problema



Estacionamentos possuem um número limitado de vagas que podem estar livres ou ocupadas em diferentes momentos. A identificação da disponibilidade das vagas normalmente depende da observação visual realizada pelos próprios motoristas ou por funcionários do estacionamento.



Em estacionamentos com grande quantidade de vagas, essa identificação pode se tornar demorada e pouco eficiente, principalmente quando há movimentação constante de veículos.



Diante desse cenário, este projeto propõe investigar a utilização de técnicas de Processamento Digital de Imagens (PDI) para identificar automaticamente se determinadas vagas de estacionamento estão livres ou ocupadas a partir de imagens digitais.



O problema central do projeto pode ser definido pela seguinte questão:



Como utilizar técnicas de Processamento Digital de Imagens para identificar automaticamente vagas de estacionamento livres e ocupadas a partir de uma imagem capturada por uma câmera?



###### 2\. Problemática

- Inerente a Imagem


Uma imagem de estacionamento apresenta diferentes características que podem dificultar essa identificação, como:
diferentes cores de veículos;
sombras; variações de iluminação;
reflexos; diferentes tamanhos e formatos de veículos;
diferentes posições dos veículos; obstáculos;
E sobreposição parcial de objetos.
A solução proposta irá contornar os desafios relacionados à diversidade cromática dos veículos, sombras moderadas, reflexos superficiais, variações globais de iluminação e a presença de sujeira no chão, uma vez que a análise baseada no desvio padrão dos pixels captura qualquer alteração textural na superfície da vaga. Entretanto, essa solução terá uma saída delimitada, sendo capaz apenas de classificar a vaga como ocupada ou vazia, não sendo capaz de identificar o que está ocupando a vaga. Dessa forma, questões relacionadas a obstáculos, cones e lixeiras não serão contornadas, pois todos serão tratados da mesma forma que um veículo. Da mesma forma, desafios ligados a diferentes posições dos veículos, diferentes tamanhos e formatos de veículos, e sobreposição parcial de objetos também não serão abordados.

- Saida

- Entrada









