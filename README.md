### Project - Estimativa de Idade por Visão Computacional

**Instruções Rápidas:** As imagens estão guardadas no google-drive e precisam ser baixadas para a máquina ([Link](https://drive.google.com/drive/folders/1_52FZSsq3nWsfQbnuxd0MzQccUKT7Jrm?usp=sharing))

**Problema de Negócio:** Automatizar a verificação de taxa etária a partir de imagens faciais.

**Solução:** Aplicação de Transfer Learning com a arquitetura ResNet50 pré-treinada, utilizando ajuste fino (fine-tuning) em Python

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
