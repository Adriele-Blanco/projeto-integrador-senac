# Relatorio de Teste e manutencao - UC 3 (Encontro 6)
**Projeto Integrador Java Swing - Homologacao Intermodular**
---
## 1. Matriz de Casos de Teste (Peer QA)
| ID | Modulo | Cenario / Teste | Resultado Esperado | Resultado Obtido | Status |
| :---: | :--- | :--- | :--- | :--- | :---: |
| **CT-01** | `TelaLogin` | Login com e-mail e senha vazios | Bloquear o login e exibir mensagem amigavel | Bloqueou exibindo "Digite seu E-mail" | **APROVADO** |
| **CT-02** | `CriarConta` | Cadastro com campos obrigatorios vazios | Bloquear o cadastro e apresentar mensagem | Bloqueou exibindo "Digite seu nome!" | **APROVADO** |
| **CT-03** | `CriarConta` | Tentativa de cadastro com e-mail duplicado | Impedir cadastro duplicado e notificar usuario | Bloqueou exibindo "E-mail duplicado" | **APROVADO** |
| **CT-04** | `Formulario` | Avancar com o campo de descricao vazio | Impedir o avanco e solicitar preenchimento | Sistema permitiu avancar para "Endereco do problema" | **REPROVADO** |
| **CT-05** | `ExportadorCSV` | Abertura do arquivo CSV no Excel / Leitores | Gerar arquivo legivel e reconhecer acentos/caracteres | Nao reconheceu caracteres especiais (acentos/c) | **REPROVADO** |
| **CT-06** | `JanelaStatus` | Clique no botao "VOLTAR" (Navegacao) | Fechar janela atual via `dispose()` e retornar | Abriu a `TelaInicial`, mas a `JanelaStatus` nao foi encerrada (duplicou) | **REPROVADO** |
---
## 2. Bug report
CT-04 Bug
* **Modulo afetado:** `Formulario`
* **Caso de teste:** CT-04
* **Descricao:** O formulario permite avancar para a proxima etapa mesmo se a descricao estiver vazia ou com combinacao imcompleta.
* **Acao Corretiva:** Adicionar verificacao de impedimento de navegacao.
---
CT-05 Bug
* **Modulo afetivo:** `CSV`
* **Caso de teste:** CT-05
* **Descricao:** O arquivo CSV exportado nao grava a marcacao fazendo com que apps como o Excel desfigure acentos e caracteres especiais.
* **Acao corretiva:** Inserir a gravacao e padronizar o separador de colunas com `;`.
---
CT-06 Bug
* **Modulo afetivo:** `JanelaStatus`
* **Caso de teste:** CT-06
* **Descricao:** Ao clicar no botao "VOLTAR", uma nova janela da `TelaInicial` e criada sem que a `JanelaStatus` seja descartada, gerando duplicacao de janelas.
* **Acao corretiva:** Inserir a chamada `dispose();`no envento `actionPerformed` do botao "VOLTAR".