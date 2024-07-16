# Segmentação de Perfil de Investidores

## Resumo

Este estudo utiliza técnicas de Análise de Correspondência Simples (ANACOR) e Análise de Correspondência Múltipla (ACM) para investigar a relação entre o perfil de investidores e suas preferências de aplicação financeira. Os dados foram analisados usando a linguagem R e os pacotes FactoMineR e sjPlot, explorando tabelas de contingência, resíduos padronizados, mapas perceptuais e percentuais de inércia explicada.

## Introdução

A Análise de Correspondência é uma técnica multivariada amplamente utilizada para explorar relações entre variáveis categóricas em estudos de mercado e comportamento do consumidor. Neste estudo, aplicamos ANACOR e ACM para segmentar e entender o comportamento de investidores com base em seu perfil e escolhas de aplicação financeira.

## Metodologia

### Preparação dos Dados

- **Carregamento dos dados**: Dados de perfil de investidores.
- **Visualização inicial e sumário estatístico**: Análise descritiva dos dados.

### Análise de Correspondência Simples (ANACOR)

1. **Construção de tabelas de contingência**.
2. **Cálculo de estatísticas qui-quadrado**.
3. **Análise de resíduos padronizados**.
4. **Construção de mapas perceptuais**: Visualização dos resultados.

### Análise de Correspondência Múltipla (ACM)

1. **Preparação dos dados**:
   - Matrizes binárias.
   - Matriz de Burt.
2. **Implementação da ACM**: Utilização do pacote FactoMineR.
3. **Visualização das coordenadas-padrão das categorias das variáveis**.
4. **Mapas perceptuais**: Representação das dimensões principais explicadas pela ACM.

## Resultados

### ANACOR

- **Identificação de padrões significativos**: Entre perfis de investidores e suas preferências de aplicação financeira.
- **Mapas perceptuais**: Revelam clusters distintos de investidores com comportamentos semelhantes.

### ACM

- **Segmentação adicional**: Baseada em perfil demográfico e estado civil.
- **Variáveis significativas**: Identificação das variáveis que mais contribuem para as dimensões explicadas.

## Discussão

Os resultados indicam que as técnicas de ANACOR e ACM são eficazes na segmentação e compreensão do comportamento de investidores, fornecendo insights valiosos para estratégias de marketing e desenvolvimento de produtos financeiros personalizados.

## Conclusão

Este estudo demonstra a aplicação prática e os benefícios das técnicas de Análise de Correspondência na análise de dados financeiros. A utilização do R e dos pacotes especializados permitiu uma análise detalhada e interpretativa, essencial para a tomada de decisões estratégicas no setor financeiro.

## Aprendizados e Aplicações Futuras

Futuras pesquisas podem explorar a combinação de técnicas de análise multivariada com modelos de machine learning para melhorar a precisão das previsões de comportamento de investidores e personalização de serviços financeiros.

## Implementação

### Instalação e Carregamento dos Pacotes


install.packages("FactoMineR")
install.packages("sjPlot")
install.packages("readr")
install.packages("dplyr")
install.packages("ggplot2")

library(FactoMineR)
library(sjPlot)
library(readr)
library(dplyr)
library(ggplot2)


### Carregamento e Visualização dos Dados


# Carregar dados
dados <- read_csv("perfil_investidores.csv")

# Visualização inicial
summary(dados)


### Análise de Correspondência Simples (ANACOR)


# Tabela de contingência
tabela_contingencia <- table(dados$perfil, dados$preferencia)

# Estatísticas qui-quadrado
chisq.test(tabela_contingencia)

# Resíduos padronizados
residuos <- chisq.test(tabela_contingencia)$residuals

# Mapas perceptuais
acm <- CA(tabela_contingencia)
plot(acm)


### Análise de Correspondência Múltipla (ACM)


# Preparação dos dados
dados_binarios <- dummy_cols(dados, select_columns = c("perfil", "preferencia"))
matriz_burt <- burt(dados_binarios)

# Implementação da ACM
acm <- MCA(matriz_burt, graph = TRUE)

# Coordenadas-padrão
acm$var$coord

# Mapas perceptuais
plot(acm)

### Pontos Importantes

1. **Resumo**: Breve descrição do objetivo e técnicas utilizadas.
2. **Introdução**: Explicação do contexto e importância da análise.
3. **Metodologia**: Passos detalhados para a preparação dos dados, ANACOR e ACM.
4. **Resultados**: Principais achados das análises.
5. **Discussão**: Interpretação dos resultados.
6. **Conclusão**: Sumário dos benefícios e aplicação das técnicas.
7. **Aprendizados e Aplicações Futuras**: Direções para pesquisas futuras.
8. **Implementação**: Código detalhado para replicação do estudo.


