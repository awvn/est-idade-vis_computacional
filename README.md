### Project - Estimativa de Idade por Visão Computacional

**Instruções Rápidas:** As imagens estão guardadas no google-drive e precisam ser baixadas para a máquina ([Link](https://drive.google.com/drive/folders/1_52FZSsq3nWsfQbnuxd0MzQccUKT7Jrm?usp=sharing))

**Problema de Negócio:** Automatizar a verificação de taxa etária a partir de imagens faciais.

**Solução:** Aplicação de Transfer Learning com a arquitetura ResNet50 pré-treinada, utilizando ajuste fino (fine-tuning) em Python

## ⚠️ Limitações e Evolução Futura

### Limitações dos Dados e do Modelo
* **Desempenho Experimental vs. Produção:** O modelo baseado na arquitetura **ResNet50 pré-treinada** (adaptada para regressão com camada de saída linear/ReLU) atingiu a meta estabelecida do projeto, alcançando um **MAE de validação entre 6,0 e 6,5 anos** (abaixo do limite alvo de `val_mae ≤ 8`). No entanto, esse resultado refere-se a um conjunto de imagens controlado em ambiente de desenvolvimento e **não deve ser interpretado como precisão garantida em produção** (como sistemas reais de verificação etária em pontos de venda).
* **Sinais de Overfitting e Viés de Domínio:** Observou-se uma diferença relevante entre o erro de treino (**MAE entre 2,0 e 2,3 anos**) e o de validação (**6,0–6,5 anos**), indicando **overfitting** aos padrões visuais do dataset de treino. Além disso, o desempenho é sensível a variações de iluminação, ângulo facial, oclusões (óculos, máscaras, barbas), qualidade da câmera e desbalanceamento demográfico entre faixas etárias (menor volume de imagens de crianças e idosos extremos).

### Melhorias Futuras
* **Redução de Overfitting e Regularização:** Aplicar técnicas mais intensivas de **Data Augmentation** (rotação, ajuste de brilho/contraste, *random erasing* e espelhamento horizontal), além de adicionar camadas de **Dropout** e penalização L2 (*weight decay*) na cabeça de regressão, acompanhadas de ajuste fino gradual (*gradual unfreezing*) dos blocos finais da ResNet50.
* **Pré-processamento Facial e Equilíbrio de Classes:** Integrar um detector facial prévio (como *MTCNN* ou *RetinaFace*) para recortar e alinhar os rostos antes da inferência, removendo ruídos de fundo, e aplicar amostragem ponderada para equilibrar faixas etárias sub-representadas.
* **Avaliação Ética e Monitoramento em Produção:** Auditar o erro (MAE) segmentado por grupos demográficos (gênero, etnia e faixa etária) para mitigar vieses algorítmicos, definir faixas de confiança/incerteza nas previsões e implementar monitoramento de *data drift* antes de qualquer uso comercial.


**Foco Técnico:** Treino em GPU e otimização para redução do Erro Médio Absoluto (MAE).

### 🚀 Tecnologias
- Python
- Pandas
- Matplotlib
- Inspect
- Tensorflow
- Keras
- Adam
- GlobalAveragePooling2D

### 📦 Como instalar

``` bash
git clone https://github.com/awvn/est-idade-vis_computacional.git
cd est-idade-vis_computacional
pip install -r requirements.txt
