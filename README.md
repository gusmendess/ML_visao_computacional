# Treinamento de Máquina - Visão Computacional

Trabalho de conclusão de fim de curso (TCC), onde apliquei meus conhecimentos de treinamento de máquina para melhorar um banco de imagens e treinar a i.a para reconhecer o uso correto de equipamentos de segurança de trabalho. Ferramentas: Python, OpenCV, Pytorch.

https://github.com/gusmendess/PPE_detection/assets/140565605/b2dba393-431e-442f-bb18-d5ebfdace772

## 1. Definição de projeto e banco de imagens

Para o projeto em questão foi definido que seria necessário desenvolver uma máquina de modo que possa identificar se um trabalhador está utilizando ou não o capacete de segurança do trabalho corretamente atráves de um banco de imagens conhecido. Utilizei o banco de imagens YOLO helmet/head disponível no Kaggle. 

![Texto alternativo](https://static.wixstatic.com/media/bf35e2_93d8654020e74efb89ee62c7632f3715~mv2.png/v1/fill/w_490,h_385,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/bf35e2_93d8654020e74efb89ee62c7632f3715~mv2.png)

## 2. Tratamento e Limpeza de Dados

A separação de um banco de imagens em pastas de treinamento, validação e teste é uma prática fundamental no treinamento de modelos de visão computacional, especialmente para máquinas de aprendizado profundo, como redes neurais convolucionais (CNNs). Foi adotado uma separação de 70% dos dados para treinamento, 20% dos dados para validação e 10% para teste. Essa abordagem é crucial para garantir que o modelo seja treinado de maneira robusta e evitar:

1.Avaliação da Generalização: Ao separar os dados em conjuntos de treinamento, validação e teste, cria-se ambientes distintos para treinar, ajustar hiperparâmetros e avaliar o modelo. Isso evita overfitting, garantindo que o modelo generalize bem para novos dados.

2.Prevenção de Overfitting: A validação e o conjunto de teste atuam como benchmarks para verificar se o modelo está generalizando ou apenas memorizando padrões específicos dos dados de treinamento, prevenindo o overfitting.

3.Ajuste de Hiperparâmetros: Durante o treinamento, ajustar os hiperparâmetros é comum. A validação fornece um conjunto independente para avaliar diferentes configurações, sem contaminar os dados de teste.

4.Simulação do Ambiente de Produção: O conjunto de teste simula o ambiente de produção, representando dados do mundo real e fornecendo uma estimativa realista do desempenho do modelo.

5.Aprimoramento Contínuo: A divisão adequada dos conjuntos permite um ciclo contínuo de treinamento, avaliação, ajuste e iteração, resultando em modelos mais robustos.

![Texto alternativo](https://static.wixstatic.com/media/bf35e2_4a57faf77dc641acab667e99cdc34abd~mv2.png/v1/fill/w_600,h_385,al_c,q_85,enc_auto/bf35e2_4a57faf77dc641acab667e99cdc34abd~mv2.png)

## 3. Treinamento de Máquina

Após organizado o banco de imagens, foi feito o treinamento de máquina a partir do modelo do yolov5, que utiliza o Pytorch para criar uma arquitetura de rede neural convolucional (CNN) profunda para realizar a detecção de objetos. A estrutura da rede neural é otimizada para processar imagens e gerar previsões em tempo real. Todo o treinamento encontra-se no notebook feito no google collab com seu devido passo a passo no notebook do repositório.

![Texto alternativo](https://static.wixstatic.com/media/bf35e2_371e822576c3445fa2abf5a80b695d3d~mv2.png/v1/fill/w_600,h_460,al_c,lg_1,q_85,enc_auto/bf35e2_371e822576c3445fa2abf5a80b695d3d~mv2.png)

## 4. Análise de eficácia e ajustes de hiperparâmetros

Com o treinamento finalizado, utilizei a biblioteca de monitoramento de machine learning wand.b (Weights and Biases).

1. Visualização em Tempo Real: Acompanha o progresso do treinamento em tempo real, fornecendo gráficos interativos e visualizações.

2. Integração com Diversos Frameworks: Pode ser integrado com frameworks populares, como TensorFlow e PyTorch.

3.Registro de Experimentos: Registra métricas, parâmetros, gráficos, imagens e outros artefatos para uma análise aprofundada dos experimentos.

Neste projeto, consegui identificar que o banco de imagens não era capaz de ensinar para a inteligência artificial a reconhecer as classes de objetos em ambientes com baixa iluminação, chuva, etc.. Então aproveitei para inserir uma amostra de dados própria e comparei o resultado entre elas.

![Texto alternativo](https://static.wixstatic.com/media/bf35e2_222f7c7625e44bb8944a501a79e46463~mv2.png/v1/fill/w_720,h_354,al_c,lg_1,q_85,enc_auto/bf35e2_222f7c7625e44bb8944a501a79e46463~mv2.png)

## 5. Identificação de objetos

Depois de tudo isso, o modelo finalmente está pronto para a inferência.

https://github.com/gusmendess/PPE_detection/assets/140565605/39b04837-4ed4-4129-80df-5b938398b27c

A aplicação da visão computacional na gestão de empresas pode proporcionar diversos insights valiosos para a tomada de decisões estratégicas. 

1. Análise de Dados Visuais: Utilize câmeras para rastrear padrões de movimento de clientes em lojas físicas, otimizando o layout e melhorando a experiência do cliente.

2. Segurança e Vigilância: Detecção de Intrusões: Utilize sistemas de visão computacional para identificar comportamentos suspeitos ou intrusões em áreas restritas.

3. Manutenção Preditiva: ​Utilize visão computacional para identificar sinais de desgaste ou danos em equipamentos, permitindo a manutenção antes de falhas críticas.

4. Segurança do trabalho: Utilize visão computacional para prevenir acidentes com falta de uso de EPI's.

