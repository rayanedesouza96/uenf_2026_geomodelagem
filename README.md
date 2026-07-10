# 🌱 Estudo Integrado: Clima, Produção de Açaí e Detecção do Barbeiro (Doença de Chagas)

Repositório com o desenvolvimento completo de um projeto que une geoprocessamento, dados climáticos e visão computacional para analisar a cadeia produtiva do açaí no Pará, incluindo o risco fitossanitário associado ao inseto vetor da Doença de Chagas.

## 🎓 Dados do Projeto

| Item | Descrição |
| :--- | :--- |
| **Instituição** | Universidade Estadual do Norte Fluminense Darcy Ribeiro (UENF) |
| **Laboratório** | LAMET – Laboratório de Meteorologia |
| **Programa** | Mestrado em Clima e Energia |
| **Disciplina** | GeoModelagem do Potencial Energético e do Microclima Urbano |
| **Docente responsável** | Dra. Raquel Jahara Lobosco |
| **Autoras** | Ana Flávia Rodrigues Barcelos Cordeiro & Rayane Pereira de Souza |

---

## 1️⃣ Etapa Climática — Mapeamento do Pará

🚀 [Clique aqui para abrir o Notebook da Etapa 1 (Mapas_acai_Rayane.ipynb)](https://github.com/rayanedesouza96/uenf_2026_geomodelagem/blob/main/Mapas_acai_Rayane.ipynb)

Nesta fase foram construídos os mapas sazonais do estado, com destaque para o principal polo produtor de açaí (Igarapé-Miri, Cametá, Abaetetuba e municípios vizinhos), usando a biblioteca **Cartopy**.

### Localização e Cobertura do Solo

<p align="center">
  <img src="./Regiao_produtora.jpeg" width="45%" alt="Região Produtora"/>
  <img src="./Mapa_usoecobertura.jpeg" width="45%" alt="Uso e Cobertura da Terra"/>
</p>

Os dados atmosféricos utilizados vêm da base **Copernicus (ERA5/ERA5-Land)**, referentes a 2024, no horário das 15h. As variáveis abaixo foram mapeadas para as quatro estações do ano:

**Precipitação (mm/dia)**
<img width="1600" height="1333" alt="Precipitacao_4_estacoes" src="https://github.com/user-attachments/assets/8b524ed6-4505-4eaf-992b-6c697917175f" />

**Temperatura do Ar (°C)**
<img width="1600" height="1333" alt="Temperatura_4_estacoes" src="https://github.com/user-attachments/assets/a9596f08-561b-4f80-b523-d4a8de806cff" />

**Velocidade do Vento (m/s)**
<img width="1600" height="1333" alt="Vento_4_estacoes" src="https://github.com/user-attachments/assets/ef97590b-bfe5-4ae7-9c34-0e976b6e4d82" />

**Umidade Relativa do Ar (%)**
<img width="1600" height="1333" alt="Umidade_4_estacoes" src="https://github.com/user-attachments/assets/c9c8124d-2007-4c37-813e-e7b3db4de977" />

---

## 2️⃣ Etapa de Visão Computacional — Modelos YOLO

Duas frentes de treinamento foram conduzidas com redes de segmentação de instâncias para reconhecer estruturas do açaí e o inseto barbeiro (triatomíneo), vetor da Doença de Chagas.

### 🟣 Modelo A — Segmentação Exclusiva do Açaí
Voltado ao reconhecimento detalhado dos frutos e cachos em cenários de campo.
- **Arquitetura:** YOLO11l-seg (Large)
- 🚀 [Clique aqui para abrir o Notebook do Modelo A (Acai_Rayane.ipynb)](https://github.com/rayanedesouza96/uenf_2026_geomodelagem/blob/main/Acai_Rayane.ipynb)

### 🪲 Modelo B — Detecção Conjunta (Açaí + Barbeiro)
Ampliação do modelo anterior para reconhecer, ao mesmo tempo, o fruto e o inseto vetor em cenas com fundo complexo, com ajuste na função de perda para compensar o desbalanceamento entre as classes.
- **Arquitetura:** YOLO11m-seg (Medium)
- 🚀 [Clique aqui para abrir o Notebook do Modelo B (Acai+barbeiro_Rayane.ipynb)](https://github.com/rayanedesouza96/uenf_2026_geomodelagem/blob/main/Acai%2Bbarbeiro_Rayane.ipynb)


---

## 3️⃣ Cruzamento entre Clima e Produtividade

Comparação entre as variáveis meteorológicas do Copernicus e os padrões produtivos observados na região de Igarapé-Miri, Abaetetuba e Cametá.

### Resumo Sazonal (ERA5-Land, 2024)

| Estação | Precipitação (mm/dia) | Temperatura (°C) | Umidade (%) | Vento (m/s) | Produtividade |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Verão** | 4.48 | 30.06 | 68.22 | 2.03 | Baixa |
| **Outono** | 12.25 | 29.29 | 76.66 | 1.34 | Muito Baixa |
| **Inverno** | 1.31 | 32.54 | 50.11 | 2.00 | Média |
| **Primavera** | 0.32 | 35.11 | 39.63 | 2.38 | Alta |

### Correlação Clima x Produção

<img width="989" height="690" alt="grafico_clima_x_indice_de_producao" src="https://github.com/user-attachments/assets/36b4c580-171d-473e-9a1a-cc6be94983c0" />

---

## 📄 Documento Final

A fundamentação teórica completa, a metodologia aplicada e a discussão dos resultados estão reunidas no relatório em PDF:

👉 **[Clique aqui para acessar o Relatório Final Completo (Ana Flávia Rodrigues e Rayane Souza - Relatório de Geomodelagem.pdf)](https://github.com/rayanedesouza96/uenf_2026_geomodelagem/blob/main/Ana%20Fl%C3%A1via%20Rodrigues%20e%20Rayane%20Souza%20-%20Relat%C3%B3rio%20de%20Geomodelagem.pdf)**

---

## ⚙️ Passo a Passo para Executar

Todo o projeto roda no **Google Colab**, com aceleração por GPU (T4):

1. **Mapeamento climático:** abra `Mapas_acai_Rayane.ipynb` e instale as dependências de geoprocessamento antes de rodar:
   ```
   pip install cartopy xarray netcdf4 h5netcdf cdsapi
   ```
   É necessário configurar previamente o token de acesso à API do Copernicus no arquivo `.cdsapirc`.

2. **Visão computacional:** os notebooks `Acai_Rayane.ipynb` e `Acai+barbeiro_Rayane.ipynb` já cuidam sozinhos da instalação da biblioteca `ultralytics` e do download das imagens hospedadas no Roboflow — basta rodar as células em sequência.

## 🗂️ Sobre o Dataset

As imagens anotadas e as respectivas máscaras de segmentação estão hospedadas publicamente no **Roboflow**. Os notebooks da etapa de visão computacional já trazem o identificador do projeto (`açai-2`) configurado, baixando e extraindo o conjunto de dados automaticamente para a pasta de treinamento — garantindo que os experimentos possam ser reproduzidos sem ajustes manuais.
