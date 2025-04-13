# Trabalho Prático 2 – Manutenção e Evolução de Software

## Membros do grupo e curso

- **Douglas Viana Coutinho** – Pós-graduação em Ciência da Computação

## Objetivo do trabalho

Avaliar o uso de modelos de linguagem (LLMs) para **geração automática de documentação de software**, com foco em dois tipos principais: mensagens de commits e comentários de código. O objetivo é entender a efetividade, limitações e possíveis melhorias dessa aplicação no contexto da manutenção e evolução de sistemas.

## Metodologia

### Modelo de linguagem que será usado

O trabalho utilizará modelos da família **GPT** (como GPT-3.5 ou GPT-4), via API da OpenAI, e possivelmente modelos open-source como **Code LLaMA** ou **StarCoder**, para comparação.

### Datasets

Será construído (ou reutilizado) um dataset de **médio porte**, contendo algumas **dezenas de instâncias**. Cada instância conterá trechos de código-fonte (commits, funções, changelogs, etc.) e sua respectiva documentação original (mensagem de commit ou comentário), obtidos a partir de:

- Repositórios populares no GitHub, preferencialmente em projetos com boa prática de documentação.
- Seleção de repositórios será feita com base em critérios como:
  - Número de estrelas (> 500)
  - Frequência de commits e issues
  - Qualidade dos comentários e mensagens de commit
 
### Exemplos preliminares de prompts

```text
# Zero-shot
"Escreva uma mensagem de commit apropriada para o seguinte diff de código:"

# One-shot
"A seguir está um exemplo de commit e sua mensagem correspondente. Gere a mensagem para o próximo exemplo."

Exemplo:
Código:
<trecho do diff>
Mensagem:
<mensagem de commit>
Novo código:
<novo trecho>
```
## Avaliação

### Avaliação Quantitativa

A avaliação quantitativa será feita usando métricas como:

- **ROUGE** e **BLEU**: para comparar a similaridade entre a saída do modelo e a documentação original.
- **Cosine similarity** entre embeddings das mensagens geradas e originais.
- **Precision, Recall e F1** em casos onde a saída é estruturada (por exemplo, se for feita extração de changelog semântico).

### Avaliação Qualitativa

Serão analisadas manualmente instâncias representativas:

- **Bons exemplos**: onde a saída do modelo é clara, fiel e útil.
- **Maus exemplos**: onde a saída contém erros, omissões ou é redundante.
- A análise considerará aspectos como clareza, completude, fidelidade ao código e utilidade prática da documentação gerada.
