# Benner — erros e tratativas

> 📌 Esta página reúne erros, causas e tratativas ligados ao Benner, especialmente em cenários de cadastro, faturamento, documentos e rotinas financeiras.

## Como esta página deve ser usada

- Consultar falhas ligadas ao Benner
- Identificar causas já mapeadas
- Reutilizar tratativas validadas
- Direcionar corretamente para a equipe responsável

## 🔴 Falha ao autorizar operação

**Mensagem:**  
Falha ao autorizar operação. Value cannot be null. Parameter name: key

**Tratativa do suporte:**  
- Tentar reenviar
- Se o erro persistir, abrir chamado fileciteturn2file3turn3file0

## 🔴 Conta financeira não preenchida

**Mensagem:**  
FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!

**Causa conhecida:**  
CR sem conta financeira configurada no Benner.

**Direcionamento:**  
➡️ GECON fileciteturn2file3

## 🔴 Filial não habilitada para faturar

**Mensagem:**  
Impossível faturar esta filial com o produto informado.

**Leitura operacional:**  
Renan confirmou que o caminho é por e-mail, consolidando os casos com Entidade, Unidade, Filial e Produto. Não precisa abrir um chamado por item. fileciteturn3file0

**Direcionamento:**  
➡️ GECON / área responsável pelo cadastro no Benner fileciteturn2file3

## 🔴 Centro de custo inválido

**Mensagem:**  
Centro de custo inválido para a filial.

**Direcionamento:**  
➡️ GECON fileciteturn2file3turn3file0

## 🔴 Complemento com mais de 60 caracteres

**Mensagem:**  
O tamanho máximo do campo "Complemento" é 60 caracteres.

**Tratativa do suporte:**  
1. Reduzir temporariamente o complemento
2. Integrar
3. Ajustar novamente o cadastro, se necessário fileciteturn2file3

## 🔴 Boleto automático não configurado

**Mensagem:**  
Não foi possível realizar a geração automática de boleto de cobrança.

**Direcionamento:**  
➡️ GECON fileciteturn2file3turn3file0

## 🔴 Documento fora do período de abertura do financeiro

**Mensagem:**  
Documento não está dentro do período de abertura do financeiro para CRE.

**Leitura operacional:**  
Renan sinalizou que parece configuração da GECON. fileciteturn3file0

## 🔴 Erro no primeiro envio com “documento já existe”

**Leitura operacional:**  
Não confundir com duplicidade comum. Renan estava levantando esses casos para repassar à GETIC quando o erro acontece já no primeiro envio. fileciteturn3file0

## Observação prática

Muitos erros do Benner exigem primeiro distinguir:
- o SGN enviou certo?
- o dado de cadastro está correto?
- o retorno do Benner é coerente?

Essa leitura muda totalmente o destino do caso.

*Base inicial de erros do Benner estruturada a partir do histórico operacional da equipe.*
