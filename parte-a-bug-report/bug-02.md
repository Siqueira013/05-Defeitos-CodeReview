# Bug 02 - Campo de formulário aceita envio vazio

## Descrição
O formulário permite ser enviado mesmo quando todos os campos estão vazios, o que não deveria acontecer.

## Passos para reproduzir
1. Acesse a página do formulário
2. Não preencha nenhum campo
3. Clique no botão de envio

## Resultado esperado
O sistema deveria impedir o envio e exibir mensagens de erro solicitando o preenchimento dos campos obrigatórios.

## Resultado obtido
O formulário é enviado mesmo sem nenhuma informação preenchida.

## Severidade
Média

## Ambiente
Google Chrome, Windows 10