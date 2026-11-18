# Privacidade — OSSYNC

> Resumo: o OSSYNC lida com dados pessoais (nomes, CPFs) e credenciais de
> portais. O projeto aplica minimização, mascaramento e retenção limitada
> em conformidade com a LGPD (Lei nº 13.709/2018).

## 1. Mascaramento de PII (LGPD)

Todos os logs (arquivo e terminal) passam por filtro automático
(`src/utils/logger.py`):

- **CPFs**: `123.456.789-00` → `123.***.***-00`.
- **Nomes**: reduzidos às iniciais (`M. O. D. C.`).
- **Telefones**: `mascarar_telefone()` exibe `(11) ***-9999`; o link
  `wa.me` carrega os dígitos reais só no href (nunca no texto visível).

Relatórios HTML/CSV **mantêm os dados reais** (são o produto do trabalho)
— trate-os como documento interno e não os encaminhe para fora dos
destinatários configurados em `EMAIL_TO`.

## 2. Segredos

- Senhas e tokens (Rauzee web, token da API Rauzee, SIOPI e SMTP) ficam no
  **Gerenciador de Credenciais do Windows** (cofre do usuário, criptografado pelo
  sistema), entradas `OSSYNC/<chave>`. Não ficam em arquivo do projeto. A primeira
  execução da 2.15.0 migra os valores antigos do `.env` e tira as linhas do `.env` e
  do `.env.bak`. Usuário e logins não sensíveis continuam no `.env`, que nunca é
  commitado (`.gitignore`). O modelo documentado é `.env.example`.
- Em outro computador ou usuário do Windows é preciso digitar as senhas de novo.
- Tokens inválidos nunca são impressos: o diagnóstico informa endpoint,
  código e dica, sem expor o segredo.

## 3. O que fica gravado — e por quanto tempo

| Dado | Onde | Retenção |
|---|---|---|
| Relatórios HTML/CSV, retry JSON/BAT | `reports/` | `RELATORIOS_RETENCAO_DIAS` (padrão 30) |
| Andamento do lote interrompido (`lote_em_andamento.json`, mesmos dados do CSV) | `reports/` | Apagado ao fim do lote; ignorado após 12 h |
| Arquivo de configuração exportado (`ossync-config-*.json`) | onde você salvar | Seu controle: leva usuários dos portais e e-mails de destino, **nunca** senhas ou tokens |
| Debug (HTML, screenshots, trace) | `reports/debug` | `DEBUG_RETENCAO_DIAS` (padrão 7), só com `--debug-artifacts` |
| Logs operacionais | `logs/` | limpeza manual |
| Laudos PDF do SIOPI | `downloads/laudos` | **permanente (evidência)** — nunca expurgado |
| Cache de sem-dados | `reports/sem_dados_cache.json` | permanente até limpeza manual |
| Histórico por item (aba Resultados) | `history/AAAA-MM.jsonl` + `history/state.json` | `HISTORICO_RETENCAO_DIAS` (padrão 90); apagável na UI |

O histórico por item é **livre de PII** (ADR-027): guarda só o
identificador (dígitos da OS ou hash salgado do CPF quando não há OS),
o tipo do evento, o status `de → para` (truncado) e contadores — nunca
nome, CPF cru, telefone ou endereço.

## 4. Compartilhamento

Relatórios e laudos só saem da máquina via **e-mail configurado por você**
ou cópia manual. Não envie banco, logs ou debug para serviços públicos de
análise sem antes remover dados sensíveis. Debug artifacts **podem conter
dados exibidos pelos portais** — ative só quando precisar diagnosticar.

## 5. WhatsApp quick-send (wa.me)

- **Origem do número:** `contato_vistoria_telefone` extraído da ficha SIOPI
  (escopo `CONTATO PARA VISTORIA`); só se vazio usa
  `WHATSAPP_TELEFONE_PADRAO` (`.env`, editável em Configurações → Execução).
  Se ambos vazios, o link abre o seletor manual (`wa.me/?text=`).
- **O que trafega:** só texto pré-formatado (motivo/situação/justificativa da
  PEPT ou valores+aprovado do laudo). **Nenhum laudo/PDF é enviado** e não há
  integração com API WhatsApp Business — é só um link `wa.me/55…` aberto no
  navegador, sem custo e sem webhook.
- **Retenção:** nenhum número é persistido fora do relatório/CSV da execução
  (retenção padrão 30 dias, mesma dos relatórios).

## Consulta de atualização

O app consulta a release mais recente em `api.github.com` no máximo uma vez por dia. Nenhum dado seu é enviado. Desligue com `VERIFICAR_ATUALIZACAO=false` no `.env`.
