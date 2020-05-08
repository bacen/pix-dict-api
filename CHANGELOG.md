# Changelog

Mudanças relevantes na API do DICT serão documentadas aqui.

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

