# Criando Relatórios Dinâmicos com Parâmetros no Power BI

Projeto desenvolvido como desafio final da Formação Power BI Analyst da DIO.

## Objetivo

Aprimorar o relatório financeiro produzido no desafio anterior, adicionando uma página de análise dinâmica com pelo menos dois visuais controlados por parâmetros de campos. O foco é permitir que o usuário explore os dados e construa uma leitura do desempenho comercial sem precisar editar os gráficos.

## Página: Visão Dinâmica

A página apresenta duas perguntas de negócio complementares:

1. **Onde as vendas estão concentradas?** Um gráfico de barras permite alternar a dimensão da análise entre **Produto**, **Segmento** e **País**.
2. **Como os resultados evoluem ao longo do tempo?** Um gráfico de linhas permite selecionar e comparar **Vendas**, **Lucro**, **Unidades Vendidas** e **Descontos**, por mês.

Os segmentadores são exibidos acima de seus respectivos visuais. O layout reutiliza a identidade visual azul e branca do relatório e inclui navegação para as demais páginas.

## Parâmetro de categorias

Nome: `Analisar por`

Campos utilizados da tabela `financials`:
- `Product`
- `Segment`
- `Country`

O parâmetro controla o eixo de categorias de um gráfico de barras com soma de vendas.

## Parâmetro de indicadores

Nome: `Indicador Dinâmico`

Foram criadas medidas DAX para os valores selecionáveis:

```dax
Total Sales = SUM(financials[ Sales])
```

> Nota: no arquivo de origem, o nome da coluna de vendas inclui um espaço antes de `Sales`.

```dax
Total Profit = SUM(financials[Profit])
```

```dax
Total Units Sold = SUM(financials[Units Sold])
```

```dax
Total Discounts = SUM(financials[Discounts])
```

O parâmetro usa essas medidas e controla o eixo Y do gráfico de linhas. O eixo X utiliza `Month Name`, ordenado por `Month Number` para respeitar a sequência cronológica.

## Storytelling

**Onde vendemos mais e como os resultados evoluem?** A análise começa pela distribuição das vendas entre categorias. Em seguida, o usuário pode observar a evolução mensal dos principais indicadores e comparar vendas e lucro. Assim, é possível explorar concentrações, variações mensais e diferenças entre faturamento e resultado, sempre a partir dos filtros selecionados.

## Recursos utilizados

- Microsoft Power BI Desktop
- Parâmetros de campos
- Medidas DAX
- Segmentadores de dados
- Gráfico de barras
- Gráfico de linhas
- Classificação cronológica de meses
- Navegação entre páginas

## Entrega

O repositório inclui o arquivo `.pbix` com o relatório atualizado, uma captura de tela da página **Visão Dinâmica** e este README.

## Contexto

Projeto educacional desenvolvido para a DIO a partir do relatório do desafio anterior, preservando as páginas existentes e adicionando a página **Visão Dinâmica**.
