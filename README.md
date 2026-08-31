Modelagem e Avaliação de Desempenho por Meio de Redes Neurais Recorrentes do Tipo LSTM para Evapotranspiração de Referência no Município de Bom Jesus do Itabapoana – RJ

Trabalho de Conclusão de Curso (TCC) — Instituto Federal Fluminense (IFF), Campus Bom Jesus do Itabapoana.

Autores: Gustavo Teixeira Lima, Guilherme Ribas Amaral Orientador: Dr. Roberto Luís da Silva Carvalho Ano: 2026

Sobre o projeto

Este repositório contém o código desenvolvido para o TCC que investiga o uso de redes neurais recorrentes do tipo LSTM (Long Short-Term Memory) na estimativa da evapotranspiração de referência (ETo) para o município de Bom Jesus do Itabapoana – RJ.

O desempenho da LSTM é comparado com três métodos consagrados na literatura agrometeorológica — Hargreaves-Samani (HS), Makkink (MK) e Penman-Monteith/FAO-56 (PM) — além de baselines mais simples de aprendizado de máquina (regressão linear e MLP).

Dados

Fonte: estação meteorológica do campus IFF Bom Jesus do Itabapoana
Período: janeiro de 2021 a outubro de 2025
Volume final: 1.763 dias válidos, após limpeza e tratamento (remoção de sensores duplicados via limiar físico de temperatura, substituição de interpolação spline por climatologia horária, correção de vazamento de dados no MinMaxScaler, entre outros ajustes no pipeline)
Principais achados
Nowcasting vs. forecasting: ao usar variáveis meteorológicas do mesmo dia (nowcasting), todos os modelos atingem desempenho quase perfeito (R² ≈ 0,99). Já na previsão a partir apenas de dados históricos (forecasting), o desempenho cai (R² entre 0,55 e 0,72) — cenário em que a memória temporal da LSTM passa a agregar valor real.
Benchmark com baselines (Seção 5.8): surpreendentemente, a regressão linear simples superou a LSTM na maioria dos alvos avaliados, evidência de que a relação entre ETo e variáveis meteorológicas é predominantemente linear quando dados do mesmo dia estão disponíveis.

.
├── LSTM_ETo_3Metodos_IFF_OTIMIZADO.ipynb   # notebook principal com todo o pipeline
├── data/                                    # dados de entrada (ver observação abaixo)
├── requirements.txt                         # dependências do projeto
└── README.md

git clone https://github.com/[seu-usuario]/[nome-do-repo].git
cd [nome-do-repo]
pip install -r requirements.txt
jupyter notebook LSTM_ETo_3Metodos_IFF_OTIMIZADO.ipynb

Metodologia

O notebook implementa:

Pré-processamento e limpeza dos dados meteorológicos
Cálculo de ETo pelos métodos HS, MK e PM como referência/comparação
Treinamento de modelos LSTM com alternância entre modos nowcasting/forecasting
Regularização L2, seed fixa para reprodutibilidade
Comparação com baselines (regressão linear, MLP)
Célula de projeção futura de ETo

Citação

LIMA, Gustavo Teixeira; AMARAL, Guilherme Ribas. Modelagem e avaliação de desempenho por meio de
redes neurais recorrentes do tipo LSTM para evapotranspiração de referência no município de Bom
Jesus do Itabapoana – RJ. 2026. Trabalho de Conclusão de Curso (Graduação) – Instituto Federal
Fluminense, Campus Bom Jesus do Itabapoana, Bom Jesus do Itabapoana, 2026.

MIT LICENSE
