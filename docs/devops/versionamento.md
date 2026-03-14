# Versionamento

O projeto adota o **Versionamento Semântico (SemVer)** para padronizar a evolução do software e comunicar claramente o impacto de cada alteração.

## Estrutura da Versão

A versão é composta por três números independentes seguindo o formato:

<div style="font-size: 2em; font-weight: bold; text-align: center; margin: 20px 0; color: #3f51b5;">v
  <span title="Mudanças que quebram compatibilidade" style="border: 2px solid #3f51b5; padding: 5px 15px; border-radius: 8px;">MAJOR</span> . 
  <span title="Novas funcionalidades (retrocompatíveis)" style="border: 2px solid #3f51b5; padding: 5px 15px; border-radius: 8px;">MINOR</span> . 
  <span title="Correções de bugs" style="border: 2px solid #3f51b5; padding: 5px 15px; border-radius: 8px;">PATCH</span>
</div>

---

## Definições de Incremento

| Nível     | Quando Incrementar                                                | Impacto |
| :-------- | :---------------------------------------------------------------- | :------ |
| **MAJOR** | Mudanças incompatíveis com versões anteriores (breaking changes). | Alta    |
| **MINOR** | Adição de novas funcionalidades que mantêm a compatibilidade.     | Média   |
| **PATCH** | Correções de bugs ou ajustes menores (retrocompatíveis).          | Baixa   |

---

## Ciclo de Vida das Tags no Git

No fluxo do projeto, as tags são aplicadas nos momentos de **Release** e **Hotfix**.

!!! info "Importante"
As tags devem ser sempre prefixadas com a letra `v` (ex: `v1.0.4`). Elas funcionam como "fotografias" do estado do código em um momento específico do tempo, garantindo que possamos voltar a qualquer versão estável se necessário.

### Exemplo de Fluxo:

1. Começamos em `v1.0.0`.
2. Adicionamos uma tela de login -> vira `v1.1.0` (MINOR).
3. Corrigimos um erro de digitação nessa tela -> vira `v1.1.1` (PATCH).
4. Refatoramos todo o banco de dados quebrando a API antiga -> vira `v2.0.0` (MAJOR).
