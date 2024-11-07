# CornDiseaseClassifier- Classificador de Doenças do Milho 

Classificador de doenças em folhas de milho usando Redes Neurais Convolucionais (CNNs) para auxiliar no monitoramento da saúde das plantas. Este projeto identifica quatro classes específicas: Mancha de Cercospora (Gray Leaf Spot), Ferrugem Comum, Saudável, e Queima das Folhas do Norte.

## Índice

* [Visão Geral](#Visão-Geral)
* [Estrutura do Projeto](#Estrutura-do-Projeto)
* [Pré-requisitos](#Pré-requisitos)
* [Como Executar](#Como-Executar)
* [Usando o Modelo Treinado](#Usando-o-Modelo-Treinado)
* [Dataset](#Dataset)
* [Resultados](#Resultados)
* [Contribuições](#Contribuições)
  
# Visão Geral

Esse projeto utiliza uma CNN para a classificação automática de doenças nas folhas de milho. A partir de imagens das folhas, o modelo consegue identificar se a planta está saudável ou se apresenta alguma doença. Isso pode auxiliar pequenos agricultores e profissionais da agricultura a monitorar a saúde das plantações e tomar decisões preventivas.

# Estrutura do Projeto 

```bash 
CornDiseaseClassifier/
│
├── README.md                    # Explicação do projeto e instruções de uso
├── Modelo_treinado.h5           # Arquivo do modelo treinado
├── requirements.txt             # Dependências do projeto
├── train_model.ipynb            # Notebook com o código de treinamento e avaliação
├── test/                        # Diretório de teste (com subpastas para cada classe de doença)
├── train/                       # Diretório de treino (com subpastas para cada classe de doença)
└── validation/                  # Diretório de validação (com subpastas para cada classe de doença)
```
# Pré-requisitos

- Python 3.x
- Bibliotecas listadas em requirements.txt

Para instalar as dependências, use:
 - pip install -r requirements.txt

Para instalar as dependências, use:
```console 
pip install -r requirements.txt
```

# Como Executar

Clone este repositório:
```console 
git clone https://github.com/seu-usuario/CornDiseaseClassifier.git
```
Instale as dependências:
```console 
pip install -r requirements.txt
```

Abra o Jupyter Notebook:
```console 
train_model.ipynb
```

No notebook, execute as células para treinar o modelo ou carregue o modelo treinado (Modelo_treinado.h5) para fazer previsões.

Usando o Modelo Treinado
O modelo treinado está salvo como Modelo_treinado.h5. Para usá-lo em novas imagens:
```console 
from tensorflow.keras.models import load_model
from tensorflow.keras.preprocessing import image
import numpy as np

# Carregar o modelo

model = load_model('Modelo_treinado.h5')

# Carregar e pré-processar uma imagem
img = image.load_img('caminho_para_imagem.jpg', target_size=(256, 256))
img_array = image.img_to_array(img)
img_array = np.expand_dims(img_array, axis=0) / 255.0

# Fazer uma previsão

pred = model.predict(img_array)
classes = ['Mancha de Cercospora', 'Ferrugem Comum', 'Saudável', 'Queima das Folhas do Norte']
print("Classe prevista:", classes[np.argmax(pred)])
```

# Dataset
O projeto utiliza imagens de folhas de milho divididas em quatro classes:

- Corn___Cercospora_leaf_spot Gray_leaf_spot (Mancha de Cercospora)
- Corn___Common_rust (Ferrugem Comum)
- Corn___healthy (Saudável)
- Corn___Northern_Leaf_Blight (Queima das Folhas do Norte)

Os dados estão organizados em diretórios para treino (train), validação (validation), e teste (test), com subpastas para cada classe de doença.

# Resultados
Durante o treinamento, o modelo alcançou uma acurácia satisfatória nas imagens de validação e teste. Os gráficos de acurácia e perda podem ser visualizados no notebook train_model.ipynb.

# Contribuições
Contribuições são bem-vindas! Para sugerir melhorias, faça um fork do repositório e abra uma pull request.

