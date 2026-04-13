# Problemas recorrentes

> 📌 Casos repetidos que merecem olhar de problema, e não só de chamado isolado.

## 🔁 Padrões conhecidos do sistema

### Quando usar “Aprovar retorno”

Use quando:
- já foi integrado
- erro é duplicado
- sistema retornou erro, mas já processou
- existe protocolo anterior com sucesso

### Quando usar “Reenviar”

Use quando:
- erro transitório
- falha momentânea
- janela de atualização do Benner gerou inconsistência
- reprocessamento é a ação orientada

### Quando usar “Forçar reenvio”

Use quando:
- item aparece em destaque e tentativa normal não resolve
- a própria tratativa já foi consolidada assim para aquele erro

### Quando abrir chamado

- não existe tratativa
- erro persiste após reenvio
- há indício de problema técnico
- o caso precisa de causa raiz

## Casos recorrentes já reconhecidos

### DependenciasPAISES
Erro recorrente que gerou vários chamados e exigiu tratamento de causa raiz, não só reprocessamento. fileciteturn3file0turn2file5

### Out of memory
Erro que voltou a aparecer em várias partes do fluxo e mereceu acompanhamento especial. fileciteturn3file0

### Duplicação de desconto / parcela liquidada
Quando o sistema enviou certo do lado do SGN, mas o Benner integrou desconto duplicado, gerando erro de parcela já liquidada. Isso é forte candidato a causa raiz do outro lado. fileciteturn3file0

### Erro no primeiro envio com “documento já existe”
Renan pediu para separar esses casos porque não são iguais à duplicidade normal de segundo envio. fileciteturn3file0

*Esta página deve crescer sempre que um erro deixar de ser isolado e passar a se repetir.*
