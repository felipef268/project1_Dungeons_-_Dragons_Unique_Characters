# D&D Characters — Análise Exploratória

Análise de um dataset com mais de 60 mil fichas de personagens de D&D criadas por jogadores reais, explorando padrões de criação de personagem, decisões de build e qualidade dos dados.

**Dataset:** `dnd_chars_unique.csv` — fichas de personagens com atributos, classe, raça, magias, equipamento, país e data de criação.

## Perguntas exploradas

1. **Atributos por classe** — Os jogadores seguem a lógica do sistema na hora de distribuir pontos? (Bárbaro com Força alta, Ladino com Destreza alta, etc.)
2. **Combinações de raça e classe** — Quais combos aparecem com mais frequência?
3. **HP, AC e progressão de nível** — Como essas variáveis se correlacionam ao longo dos níveis?
4. **Multiclasse** — Personagens multiclasse tendem a ter nível mais alto? Quais classes mais se misturam?
5. **Distribuição geográfica e temporal** — De onde vêm os registros e como a criação de fichas evoluiu no tempo?
6. **Magias mais escolhidas** — Quais truques e magias de 1º círculo são mais populares?
7. **Min-maxing** — Quais classes concentram pontos em poucos atributos (build "bitolada") e quais são mais equilibradas?
8. **Arsenal** — Qual a relação entre classe de combate e escolha de arma (arco, escudo, arma pesada)?
9. **Clustering (K-Means)** — Os atributos numéricos da ficha sozinhos são suficientes para separar arquétipos de personagem (tanque, conjurador, ágil)?
10. **Dados faltantes** — Quais colunas têm mais valores nulos, e o que isso indica sobre a qualidade do dataset?

## Principais achados

- **Fighter, Rogue, Cleric, Barbarian e Paladin** são as classes mais populares no dataset.
- A média de atributos por classe segue, em boa parte, a lógica esperada do sistema (ex: Força alta entre as classes marciais), mas com variações interessantes em classes híbridas.
- **HP e nível têm correlação forte (~0.65)**, enquanto AC cresce de forma mais discreta com o nível — sugerindo que a armadura tende a estabilizar mais rápido que os pontos de vida.
- Apenas **~5,9% dos personagens são multiclasse**, mostrando que builds de classe única ainda dominam amplamente.
- **Estados Unidos e Canadá** concentram a grande maioria dos registros do dataset.
- As magias/truques mais escolhidos incluem *Cure Wounds*, *Mage Hand* e *Healing Word* — refletindo a popularidade de builds de suporte e utilidade.
- O K-Means consegue separar parcialmente arquétipos de combate (ex: Fighter vs. Wizard) só com base em atributos numéricos, mas há sobreposição relevante entre classes com perfis estatísticos parecidos.
- Algumas colunas (como `processedSpells` e `processedAlignment`) têm proporção significativa de dados faltantes, o que é esperado já que nem todo personagem é conjurador ou preenche todos os campos da ficha.

## Estrutura do notebook

O notebook (`Projeto_Dungeons_&_Dragons_Unique_Characters.ipynb`) está organizado em 10 seções, cada uma com uma pergunta de negócio, o código de análise e uma visualização (gráfico de barras, heatmap, scatter plot, boxplot ou matriz de correlação, dependendo da pergunta).

## Tecnologias utilizadas

- **pandas** / **numpy** — manipulação e engenharia de dados
- **seaborn** / **matplotlib** — visualização
- **scikit-learn** — clustering (K-Means) e normalização (StandardScaler)
- **Google Colab** — ambiente de execução
