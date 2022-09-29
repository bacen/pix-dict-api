# Changelog

Mudanças relevantes na API do DICT serão documentadas aqui.

## [1.8.0] - 2022-09-25
### Adicionado
- Novas políticas de limitação REFUND_LIST_WITH_ROLE e REFUND_LIST_WITHOUT_ROLE para listagem de pedidos de devolução
- Novas políticas de limitação POLICIES_READ e POLICIES_LIST para o serviço de consulta de baldes
- Endpoints para consulta de baldes na seção “Política de Limitação"

### Alterado
- Política de limitação KEYS_READ renomeada para KEYS_CHECK
- Taxa de reposição e tamanho do balde da política de limitação STATISTICS_READ alterados de 100 para 500
- Texto de descrição do campo PI-RequestingParticipant do grupo HEADER PARAMETERS da seção “Consultar Vínculo”. Passa a considerar Iniciadores de pagamento
- Endpoint “Consultar Vínculo(PSP iniciador)” deprecado
- Inclusão de 3 casas decimais na precisão dos campos de data nos XML’s de exemplo de respostas na API
- Melhoria nos textos descritivos das seções “Receber Relato de Infração” e “Fechar Relato de Infração”
- Políticas de usuário final passam a descontar 20 fichas para consultas inválidas
- Baldes de consultas para participantes das categorias A e B passam a ter reposição de fichas de 12.000/min e 8.000/min
- Baldes de usuários PF passam a ter 100 fichas para cada tipo de balde e usuários PJ 1.000 fichas para cada tipo de balde

### Removido
-	Removidas políticas de limitação ENTRIES_READ_PARTICIPANT_INITIATOR e ENTRIES_READ_USER_INITIATOR;

## [1.7.2] - 2022-02-03
### Alterado
- Ajuste no texto das regras de contagem das políticas de baldes para considerar ordens de pagamento 
- Inclusão do tamanho máximo da lista de chaves no CheckKeysRequest
- Restrição no formato de chave EMAIL para não permitir caractere '%'
- Eliminação do erro 404 do endpoint de consulta de estatísticas

## [1.7.1] - 2021-11-16
### Adicionado
- Novo tipo de contador em estatísticas para transações rejeitadas: REJECTED
- Política para controle de limites de acesso no endpoint de estatísticas: STATISTICS_READ

### Alterado
- Correções pontuais de nomenclatura

### Removido
- Eliminação do motivo ENTRY_INACTIVITY para operações de deleção de chaves

## [1.7.0] - 2021-10-29
### Adicionado
- Novo fluxo de reporte de infração
- Consulta de estatísticas por CPF/CNPJ

### Alterado
- Novo formato do PayerID

## [1.6.1] - 2021-10-13
### Adicionado
- Campo refundAmount no XML de exemplo de listagem de devoluções
- Campo InfractionReportId em devoluções
- Criada estrutura Person para unificar os tipos Owner e Claimer
- Ajuste do campo Name para 120 caracteres

### Alterado
- Aumento do nome em PF e PJ para 120 caracteres

## [1.6.0] - 2021-09-20
### Adicionado
- Categorias de baldes de A a F
- Tratamento diferenciado para controle de limites de PF e PJ

### Removido
- Política ENTRIES_READ

### Alterado
- Tamanho do balde na ENTRIES_UPDATE

## [1.5.0] - 2021-07-19
### Adicionado
- ID da PACS.004 na consulta de devolução
- Parâmetro de indicação para inclusão de indiretos nas consultas de devolução e relatos de infração
- Políticas de limites para iniciadores
- Balde para controle de atualização de chaves

### Alterado
- Novo formato do PayerID (aberto e não mais psedonimizado)

## [1.4.0] - 2021-06-26
### Adicionado
- Novo tipo de conta TRAN
- Definição de políticas de limitação para Devolução, listagens de infração e checkKeys

## [1.3.0] - 2021-06-11
### Adicionado
- Fluxo de devolução

## [1.2.0] - 2021-04-01
### Adicionado
- Alteração de nome de cliente na Entry
- Consulta de existência de chaves (CheckKeys)

## [1.1.0] - 2020-12-02
### Removido
- Tipo de infração AML_CTF
- Contadores de infração para os tipos REPORTED_AML_CFT e CONFIRMED_AML_CFT

### Adicionado
- UNAVAILABLE em FileStatus
- Novas políticas de limitação de requisições
- Seção sobre versionamento da API
- Parâmetro IncludeIndirectParticipants na operação de listClaims

### Alterado
- Simplificação das expressões regulares de nomes de NaturalPerson e LegalPerson

## [1.0.1] - 2020-10-20
### Adicionado
- campos CorrelationId e ResponseTime em todos Responses

### Alterado
- Regex para nomes de pessoas físicas passou a permitir apóstrofo (U+0027)
- Definição de SyncVerifierStart, para refletir como está implementado

## [1.0.0] - 2020-09-16
### Adicionado
- Seção com recomendações de desempenho
- URL de produção
- Possibilidade de cancelar reivindicação de posse pelo reivindicador com razão DEFAULT_OPERATION
- Tipo de erro InfractionReportTransactionNotSettled

### Alterado
- Atualizadas referências para manual de segurança

### Removido
- Tipo de erro RequestOnBehalfUnauthorized

## [1.0.0-RC6] - 2020-08-24
### Adicionado
- _Endpoints_ de InfractionReport
- Campo OpeningDate em Entry.Account e Claim.ClaimerAccount
- Campo OpenClaimCreationDate em ExtendedEntry
- Campos CancelReason, CancelledBy, ConfirmReason em Claim
- Campos EntryCreationDate e KeyOwnershipDate em CompleteClaimResponse
- Campo RequestId em GetEntryByCidResponse

### Alterado
- Parâmetro ClaimStatus no _Endpoint_ listClaims passou a ser multi-valor (array)
- A fórmula que calcula o erro de EntryLimitExceeded considerava Participant+Branch+AccountNumber,
  passou a considerar Participant+Branch+AccountNumber+*AccountType*.

### Removido
- _Endpoints_ de Disputas (substituído por InfractionReport)

## [1.0.0-RC5] - 2020-07-22
### Adicionado
- Contadores para avaliação de risco de fraude em GetEntryResponse
- Campo obrigatório OpeningDate em BrazilianAccount
- Campo HasMoreElements em ListClaimsResponse, ListCidSetEventsResponse
- Header obrigatório PI-RequestingParticipant para operações getEntry, getClaim e getCidSetFile
- Possibilidade de remover vínculo com razão FRAUD (correção da spec)
- _Endpoints_ de disputas

### Alterado
- Campos CreationDate e KeyOwnershipDate de ExtendedEntry passaram do formato date para date-time
- Colocada restrição de caracteres para nomes de NaturalPerson e LegalPerson

### Removido
- Header PI-PayerAccountServicer para operação getEntry

## [1.0.0-RC4] - 2020-06-24
### Adicionado
- Campo Reason em ConfirmClaimRequest (correção da spec)
- Campo Participant em AcknowledgeClaimRequest, CancelClaimRequest, ConfirmClaimRequest, CompleteClaimRequest e DeleteEntryRequest
- Erro InternalServerError (spec omitia)
- Definições de idempotência para operações de acknowledgeClaim, confirmClaim e cancelClaim

### Alterado
- Campo SyncVerifier tornou-se ParticipantSyncVerifier em SyncVerification

### Removido
- Campo Reason de CompleteClaimRequest (correção da spec)
- Campo SyncVerifierLastModified de ExtendedSyncVerification

## [1.0.0-RC3] - 2020-05-29
### Adicionado
- Campo opcional correlationId a Problem
- Erro InvalidReason
- Possibilidade de confirmar reivindicação com razão USER_REQUESTED
- Parâmetro Id na operação getCidSetFile (correção da spec)

### Alterado
- Campo CompletionPeriodEnd deixou de ser preenchido para portabilidade

### Removido
- Campo SyncVerifierLastModified de CreateSyncVerificationRequest

## [1.0.0-RC2] - 2020-05-08
### Adicionado
- _Endpoints_ para reconciliação
- Campo obrigatório _RequestId_ em CreateEntryRequest e CompleteClaimResponse
- Erro RequestIdAlreadyUsed

### Alterado
- Tamanho válido do campo _AccountNumber_, de 4 a 10 para 1 a 20
- Tamanho válido do campo _Branch_, de 4 para 1 a 4
- Campo _Branch_ tornou-se opcional
- Erro EntryLimitExceededForOwner substituído por EntryLimitExceeded

### Removido
- Campos _CreatedEntryCid_ e _DeleteEntryCid_
  - Dos componentes CreateEntryResponse, DeleteEntryResponse, UpdateEntryResponse, ConfirmClaimResponse e CompleteClaimResponse

## [1.RC1] - 2020-04-01
### Adicionado
- _Endpoints_ para reivindicação de posse e portabilidade
- Novo tipo de chave EVP - Endereço Virtual de Pagamento
- Campo obrigatório _Reason_ em CreateEntryRequest e DeleteEntryRequest
- Campo _CreatedEntryCid_ em CreateEntryResponse
- _Endpoint_ updateEntry

### Alterado
- Tamanho máximo de chave alterado de 72 para 77 caracteres
- Código de sucesso da remoção de vínculo mudou para 200, inclui agora DeleteEntryResponse no corpo
- Atualizada referência para versão 2.0 do Manual de Segurança PIX

## [1.RC0] - 2020-02-18

Primeiro _release candidate_ da versão 1 da API.

