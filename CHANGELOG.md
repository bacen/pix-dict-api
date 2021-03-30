# Changelog

Mudanças relevantes na API do DICT serão documentadas aqui.

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

