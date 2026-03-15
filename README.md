# Projeto COINS - NES 2026.1

Repositório destinado à documentação técnica e acompanhamento do sistema.

## Link da Documentação

https://nes-contabilidade-integrada.github.io/doc-coins2026.1/

## 🚀 Como Executar Localmente

1. **Clonar o Repositório:**
   ```bash
   git clone https://github.com/NES-Contabilidade-Integrada/doc-coins2026.1
   cd doc-coins2026.1
   ```

2. **Criar e Ativar o Ambiente:**
   - **No Ubuntu / Linux:**
     ```bash
     python3 -m venv .venv
     source .venv/bin/activate
     ```
   - **No Windows (PowerShell):**
     ```powershell
     python -m venv .venv
     .\.venv\Scripts\Activate.ps1
     ```

3. **Instalar Dependências e Rodar:**
   ```bash
   pip install -r requirements.txt
   mkdocs serve
   ```