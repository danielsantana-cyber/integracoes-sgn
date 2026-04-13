# Modelo de novo caso

> 📌 Use este modelo sempre que a equipe precisar registrar um novo erro, processo ou tratativa.

## Template padrão

```markdown
## Título do caso

**Contexto**  
Descreva em que cenário o erro acontece.

**Causa**  
Explique a causa identificada.  
Se ainda não estiver validada, escreva:  
"Causa em análise — padrão ainda não confirmado."

**Solução passo a passo**  
1. Primeiro passo  
2. Segundo passo  
3. Terceiro passo

**Atenção**  
Inclua alertas, limitações ou erros comuns.

**Escalonamento**  
Indique quando escalar e para qual área ou fluxo interno.
```

## Exemplo preenchido

## Erro ao integrar a pessoa

**Contexto**  
Ocorre quando a cobrança tenta integrar, mas a pessoa não está reconhecida como integrada no Benner.

**Causa**  
Último protocolo da integração de pessoa ficou sem retorno ou com erro antigo.

**Solução passo a passo**  
1. Acessar a integração de pessoa
2. Buscar pelo CPF ou nome
3. Verificar o último protocolo
4. Se necessário, abrir o cadastro da pessoa no SGN e salvar novamente

**Atenção**  
Não olhar só protocolo antigo sem conferir o último. Isso gerou dúvida na prática do suporte. fileciteturn3file0

**Escalonamento**  
Se persistir mesmo após novo envio da pessoa, abrir chamado técnico.
