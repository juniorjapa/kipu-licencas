# Licenças do Kipu

O agente Kipu de cada empresa lê o `licencas.json` a cada 5 minutos.

## Como liberar um aparelho

1. O aparelho novo mostra **"Aparelho aguardando liberação"** com um código (ex.: `Q7F2-9XA3`).
2. Abra o `licencas.json`, encontre a empresa e adicione o código em `aparelhos`:

```json
"aparelhos": {
  "Q7F2-9XA3": { "status": "liberado", "obs": "Tablet do João" }
}
```

3. Salve (commit). Em até 5 minutos o aparelho entra.

## Campos de cada empresa

| Campo | O que é |
|---|---|
| chave (ex.: `5AYS7Z6S`) | Código da licença, gravado no agente com `kipu-agente licenca 5AYS7Z6S` |
| `nome` | Só para você saber de quem é |
| `status` | `liberado` ou `bloqueado` (bloqueia a empresa toda na hora) |
| `validade` | Até quando está pago (AAAA-MM-DD). Renovou → mude a data |
| `max_aparelhos` | Quantos aparelhos podem estar liberados |
| `aparelhos` | Código → `status` (`liberado` / `bloqueado`) e `obs` livre |

- Para tirar um aparelho: mude o `status` para `bloqueado` ou apague a linha.
- Se houver mais aparelhos liberados que o limite, valem os primeiros da lista.
- Sem internet, o agente usa a última leitura por até 7 dias.
- Este repositório é público: não coloque senhas nem dados sensíveis.
