# Skill: ventura.algorithms — LOOP Skill Engine / Constrained Replay

![License](https://img.shields.io/github/license/venturalabs-ai/ventura.algorithms)
![Stars](https://img.shields.io/github/stars/venturalabs-ai/ventura.algorithms)

Skill de resolução de problemas com algoritmos e estruturas de dados usando **replay restrito por padrão versionado**: explore quando necessário, compile o padrão, reutilize a abordagem em variações compatíveis e regenere quando as restrições mudarem.

## Trigger

Use quando o usuário quiser resolver um problema de algoritmo, revisar padrões, estudar estruturas de dados, preparar entrevista técnica ou otimizar uma solução.

## Arquitetura de eficiência

| Fase | Descrição | Meta de contexto |
|---|---|---|
| **Explore** | Analisa problema, restrições e padrão provável | Maior |
| **Compile** | Gera `padrao.md`: tipo, passos, complexidade e esqueleto | Reduzida |
| **Constrained Replay** | Reutiliza o padrão apenas quando as restrições permanecem compatíveis | Mínima necessária |
| **Regenerate** | Reavalia quando o padrão deixa de servir | Sob demanda |

O consumo real de tokens depende do modelo, runtime e contexto. Este projeto não afirma execução com zero tokens nem determinismo de saídas LLM.

## Receita de replay

```text
1. PEDIDO   — problema ou variação
2. RECEITA  — consulta padrao.md: tipo, passos, complexidade, esqueleto
3. EXECUTA  — traduz entrada/saída | aplica esqueleto | valida exemplo
4. REGISTRA — padrão, dificuldade, complexidade e observações
5. STOP-YIELD — restrição incompatível → sinaliza regenerar
```

## Regras de engenharia

- definir token/context budget mensurável por runtime;
- limitar o replay ao padrão necessário;
- usar prefixos estáveis apenas quando houver cache suportado;
- registrar complexidade de tempo e espaço;
- voltar ao Explore quando novas restrições alterarem a escolha do algoritmo.

## Compilar o padrão

```text
1. Analise entrada, saída, restrições e escala.
2. Mapeie para uma família de algoritmos/estruturas.
3. Registre padrao.md com passos, complexidade e esqueleto genérico.
4. Valide com um exemplo e inicie Constrained Replay.
```
