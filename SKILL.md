# Skill: ventura.algorithms — LOOP Skill Engine / Deterministic Replay

![MIT](https://img.shields.io/github/license/chamseddinehiddoud/ventura.algorithms)
![stars](https://img.shields.io/github/stars/chamseddinehiddoud/ventura.algorithms)
![forks](https://img.shields.io/github/forks/chamseddinehiddoud/ventura.algorithms)

Skill de resolução de problemas com algoritmos e estruturas de dados usando
**execução determinística**: explore o problema uma vez, compile o padrão,
replique em variações com ~zero tokens, regenere quando o padrão não servir.

## Trigger

Use quando o usuário quiser: resolver um problema de algoritmo, revisar
padrões (grafos, DP, guloso, retrocesso), estudar estruturas de dados,
preparar entrevista técnica, otimizar uma solução.

## Arquitetura Token-Efficient & Regenerative

| Fase | Descrição | Consumo |
|---|---|---|
| **Explore** | Modelo forte analisa o problema e escolhe o padrão (uma vez) | Alto (único) |
| **Compile** | Gera `padrao.md`: tipo, passos, complexidade, esqueleto | Baixo |
| **Replay** | Aplica o padrão a variações — sem redecidir a abordagem | Mínimo/Zero |
| **Regenerate** | Problema foge do padrão → explore de novo | Sob demanda |

## Receita determinística (Replay)

```text
1. PEDIDO   — "resolver problema X" | "variação de padrão Y"
2. RECEITA  — consulta padrao.md: tipo, passos, complexidade, esqueleto
3. EXECUTA  — 1. traduz entrada/saída | 2. aplica esqueleto | 3. valida exemplo
4. REGISTRA — padrão aplicado, dificuldade, complexidade, observações
5. STOP-YIELD — padrão não encaixa (complexidade/limite) → sinaliza regenerar
```

## Regras de engenharia

- **Token Budget** — Explore: até 6k tokens. Replay: < 200 tokens.
- **Context Firewall** — o replay só vê o padrão compilado (nunca a curadoria inteira).
- **Prefix Caching** — o sistema deste arquivo fica byte-stable.
- **Skill Distillation** — padrão validado vira receita permanente.
- **Regeneração** — problema com restrição nova → volta ao Explore.

## Como compilar o padrão (Explore → Compile)

```text
1. Analisa o problema: entrada, saída, restrições, tamanho esperado
2. Mapeia para categoria curada e escolhe o padrão (grafos/DP/guloso/etc.)
3. Compila padrao.md: passos, complexidade (tempo/espaço), esqueleto genérico
4. Valida com um exemplo e ativa o Replay
```

## Exemplo de uso

```text
Atue como ventura.algorithms (modo REPLAY). Meu padrao.md diz: "Programação
dinâmica, menor custo em grade". Aplique o esqueleto a esta variação:
[entrada aqui]. Use menos de 200 tokens e registre a complexidade.
```
