# Markov Chains Project

Um projeto educativo e utilitário para construir, treinar e gerar sequência(s) usando cadeias de Markov. Este repositório contém código e exemplos para entender como cadeias de Markov funcionam e como usá-las para tarefas simples de geração de texto, modelagem de sequência e experimentos exploratórios.

> Idioma: Português  
> Objetivo: demonstrar construção e uso de modelos de Cadeia de Markov de ordem variável para geração e análise de sequências.

---

## Conteúdo principal

- Descrição do projeto e motivação
- Requisitos e instalação
- Como preparar dados
- Uso rápido (exemplos)
- Arquitetura / estrutura de pastas
- Como contribuir
- Licença e contatos

---

## O que é este projeto?

Cadeias de Markov são modelos probabilísticos que representam transições entre estados onde a próxima saída depende (apenas) do estado atual — ou dos N estados anteriores no caso de cadeias de ordem superior. Este projeto implementa versões simples e extensíveis de cadeias de Markov com:

- Modelos de ordem 1 e ordem N
- Treinamento a partir de textos/sequências
- Geração de novas sequências/textos condicionada a um estado semente (seed)
- Ferramentas para salvar/carregar modelos e inspecionar probabilidades de transição

É ideal para fins didáticos, prototipagem rápida e experimentos em geração de texto simples.

---

## Requisitos

- Python 3.8+
- Pip

Recomenda-se criar um ambiente virtual:

```bash
python -m venv .venv
source .venv/bin/activate   # macOS / Linux
.venv\Scripts\activate      # Windows
```

Instale dependências (exemplo):

```bash
pip install -r requirements.txt
```

Se não houver requirements.txt, as dependências mínimas são (exemplos):
- numpy
- pandas (opcional, para análise)
- matplotlib (opcional, para visualizações)

Instale via:

```bash
pip install numpy pandas matplotlib
```

---

## Como usar — Quickstart

1. Prepare um corpus de texto (arquivo .txt) contendo as sequências que você quer modelar.
2. Treine um modelo de Markov a partir desse corpus.
3. Gere novas sequências.

Exemplo mínimo em Python (exemplo ilustrativo — adapte ao código do repositório):

```python
from markov import MarkovChain  # nome hipotético do módulo

# Carregar texto (cada linha considerada como sequência)
with open("data/corpus.txt", "r", encoding="utf-8") as f:
    lines = [line.strip() for line in f if line.strip()]

# Treinar cadeia de ordem 2
mc = MarkovChain(order=2)
mc.train(lines)

# Gerar sequência com seed e comprimento desejado
seed = ("eu", "gosto")
generated = mc.generate(seed=seed, length=30)
print(" ".join(generated))

# Salvar modelo
mc.save("models/markov_order2.pkl")
# Carregar modelo
# mc = MarkovChain.load("models/markov_order2.pkl")
```

(Se o seu repositório tiver scripts, notebooks ou uma CLI, substitua por: `python scripts/train.py --input data/corpus.txt --order 2 --out models/` e `python scripts/generate.py --model models/markov_order2.pkl --seed "eu gosto" --length 30`.)

---

## Recomendações para preparação de dados

- Limpeza básica: remover linhas vazias, normalizar espaços, tratamento de pontuação conforme necessário.
- Tokenização: escolha tokens por palavra, por caractere, ou por n-grama, dependendo da aplicação.
- Para textos em português, considerar normalização (lowercase), remoção de acentos apenas se fizer sentido para o seu uso.

---

## Avaliação e análise

- Verifique distribuição de probabilidades de transição para detectar estados dominantes.
- Compare amostras geradas com o corpus original qualitativamente.
- Para experimentos repetíveis, fixe a semente aleatória para geração.

Sugestões de métricas:
- Perplexity aproximada em cadeias simples (comparação entre probabilidade média das sequências).
- Diversidade lexical (número de tokens únicos / comprimento).

---

## Estrutura sugerida de pastas

(Adapte conforme seu repositório — esta é uma estrutura típica.)

- data/                — corpus e dados brutos
- notebooks/           — notebooks exploratórios e demos
- src/                 — implementação (MarkovChain, utilitários)
- scripts/             — scripts de treino, geração e avaliação
- models/              — modelos salvos
- tests/               — testes unitários
- README.md

---

## Boas práticas e extensões possíveis

- Implementar suavização (smoothing) para evitar probabilidades zero em cadeias de maior ordem.
- Implementar geração condicionada por temas (por exemplo: prefixos ou tópicos).
- Explorar cadeias com estados contínuos (ex.: embedding discretizado).
- Comparar com modelos baseados em n-grams e RNNs para tarefas de geração de texto.

---

## Contribuição

Contribuições são bem-vindas! Para contribuir:

1. Abra uma issue descrevendo o problema ou a feature.
2. Faça um fork e crie uma branch com um nome descritivo: feature/nova-funcionalidade
3. Abra um Pull Request com descrição clara das mudanças.
4. Inclua testes e atualize a documentação se necessário.

Se quiser sugestões de tarefas para iniciantes, crie uma issue com a label "help wanted".

---

## Licença

Escolha uma licença apropriada para o seu projeto (por exemplo MIT, Apache-2.0). Se não houver um arquivo LICENSE no repositório, adicione um e referencie-o aqui.

Exemplo:

Licensed under the MIT License — veja o arquivo LICENSE para detalhes.

---

## Contato / Créditos

Autores:

Grupo 2 da capacitação da Fea Dev
