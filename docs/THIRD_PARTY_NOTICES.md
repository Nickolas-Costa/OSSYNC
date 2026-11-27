# Créditos de Terceiros — OSSYNC

O OSSYNC é construído sobre software de código aberto. Pins exatos em
`requirements.txt` (validados) e `scripts/build/requirements-build.txt`.

## Runtime

| Componente | Requisito | Licença | Uso |
|---|---|---|---|
| Playwright | `>=1.40.0` | Apache-2.0 | Automação Chromium (Rauzee + SIOPI) |
| python-dotenv | `>=1.0.0` | BSD-3-Clause | Leitura do `.env` |
| requests | `>=2.31.0` | Apache-2.0 | HTTP síncrono (API Rauzee) |
| rich | `>=13.7.0` | MIT | Tabelas e painéis no terminal |
| Jinja2 | `>=3.1.2` | BSD-3-Clause | Renderização do relatório HTML |
| FastAPI | `>=0.110.0` | MIT | Microserviço REST |
| uvicorn | `>=0.28.0` | BSD-3-Clause | Servidor ASGI |
| pydantic | `>=2.6.0` | MIT | Schemas da API |
| httpx | `==0.28.1` | BSD-3-Clause | Cliente HTTP da API |
| pywebview | `==6.2.1` | BSD-3-Clause | Janela desktop nativa (WebView2) |
| pythonnet / clr_loader / bottle / proxy_tools | `==3.1.0` / `==0.3.1` / `==0.13.4` / `==0.1.0` | MIT | Ponte .NET do pywebview |

## Build / empacotamento (não vão para o usuário final)

| Componente | Versão | Licença |
|---|---|---|
| PyInstaller | `==6.21.0` | GPL-2.0-or-later **com exceção** para bundles |
| pyinstaller-hooks-contrib | `==2026.6` | Apache-2.0 |
| Inno Setup 6 | 6.x | Licença própria (gratuita) |
| Microsoft Edge WebView2 Runtime | Evergreen (sistema) | Microsoft (proprietário) |

## Portais e marcas

Rauzee e SIOPI/Caixa Econômica Federal são sistemas e marcas de terceiros;
o OSSYNC apenas os acessa com as credenciais do usuário. Nenhum vínculo
institucional.
