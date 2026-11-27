<div align="center">
  <img src="assets/logo.png" width="130" alt="OSSYNC Logo" style="border-radius: 24px;" />

  # OSSYNC

  <p align="center">
    <b>Sincronização Inteligente de Ordens de Serviço de Engenharia (Rauzee + SIOPI Caixa)</b>
  </p>

  <p align="center">
    <a href="#-download">Download</a> •
    <a href="#-como-usar">Como usar</a> •
    <a href="#-atualizações">Atualizações</a> •
    <a href="docs/PRIVACIDADE.md">Privacidade</a> •
    <a href="docs/TERMOS_DE_USO.md">Termos de uso</a>
  </p>

  <p align="center">
    <a href="https://github.com/Nickolas-Costa/OSSYNC/releases/latest"><img src="https://img.shields.io/github/v/release/Nickolas-Costa/OSSYNC?style=for-the-badge&label=Vers%C3%A3o&color=0066FF" alt="Última versão" /></a>
    <img src="https://img.shields.io/badge/Windows-10%20%7C%2011%20(64%20bits)-0078D4?style=for-the-badge&logo=windows&logoColor=white" alt="Windows 10 e 11, 64 bits" />
    <img src="https://img.shields.io/badge/LGPD-PII%20Masked-00C853?style=for-the-badge&logo=shield&logoColor=white" alt="LGPD" />
  </p>
</div>

---

## ⚡ O que é

O **OSSYNC** faz sozinho o trabalho repetitivo das OSs de engenharia: pega as
engenharias pendentes na **Rauzee**, consulta cada uma no **SIOPI da Caixa**,
atualiza a posição de volta na Rauzee e entrega um **relatório pronto** (HTML,
CSV e e-mail) com o que mudou, o que precisa de ação e os laudos baixados.

> **O sistema não substitui os portais corporativos.
> Ele reduz o trabalho necessário para usá-los.**

## ⏱️ Quanto tempo economiza

| O que acontece | Trabalho manual | Com o OSSYNC |
| :--- | :---: | :---: |
| Lote de **10 OSs** (sincronização completa) | ~5–6 min antes de paralelizar | **2–3 min** (com 2–3 abas do SIOPI) |
| Lote de **11 OSs** com 6 laudos, 1 PEPT e 4 análises | **~13 min** (estimativa: 90 s por laudo, 60 s por PEPT, 45 s por análise) | **2–3 min** |

**Resultado:** a sincronização com várias abas do SIOPI ficou **cerca de 50% mais rápida**
(de 5–6 min para 2–3 min nas OSs do teste), e cada lote como o do exemplo poupa
**cerca de 10 a 11 minutos (~80%)** de trabalho de consulta e atualização item por item.
Os tempos manuais são estimativas e podem ser ajustados em Configurações → Execução.
O próprio relatório mostra a economia de cada execução.

## 🛡️ Seus dados ficam no seu computador

- **Nada sai da sua máquina sem você mandar.** Não há conta, nuvem, servidor do OSSYNC nem telemetria.
  Os dados só saem para a Rauzee e o SIOPI (os próprios portais) e para o e-mail que você configurar.
- **Senhas e tokens** ficam no Gerenciador de Credenciais do Windows, cofre criptografado do seu usuário,
  e não em arquivo de texto.
- **Dados pessoais mascarados nos logs** (CPF, nomes e telefones) — LGPD.
- **Relatórios, laudos e histórico** ficam em `%LOCALAPPDATA%\OSSYNC`, com retenção configurável.
  Os laudos PDF são guardados como evidência.

Detalhes em [Privacidade](docs/PRIVACIDADE.md).

## 🧩 Principais funções

- Sincronização automática pela Rauzee e pelo SIOPI, em lote ou por OS/CPF, com várias abas do SIOPI ao mesmo tempo.
- Atualização da Rauzee com a posição do SIOPI, PEPT e engenharia (valor, validade e garantia).
- Relatório em HTML e CSV com o que precisa de ação, o tipo de cada OS (imóvel pronto, construção…) e o contato para vistoria, e envio por e-mail.
- Guia Resultados com o panorama do período: laudos, atrasadas, tipos de serviço e motivos de PEPT.
- Agendamento por horário e dias, rodando mesmo com o app fechado, e reagendamento automático das falhas.
- Link de WhatsApp pronto para cada OS com alteração.
- Busca rápida por OS, CPF (com ou sem pontuação) ou parte do nome do cliente, com o histórico de cada item.
- Laudos baixados e organizados, com busca, e abertos direto do relatório no app.

## 📥 Download

<p align="center">
  <a href="https://github.com/Nickolas-Costa/OSSYNC/releases/latest"><img src="assets/download.png" height="60" alt="Baixar o OSSYNC"></a>
</p>

Na página da versão mais recente, baixe o **`OSSYNC-Setup-<versão>-x64.exe`**
(instalador para Windows 10/11 64 bits). Não precisa de administrador.

Também há o **`OSSYNC-<versão>-win64.zip`** (versão portátil) com o arquivo `.sha256` para conferência.

## 🚀 Como usar

1. **Instale:** abra o instalador baixado e siga as telas. Um atalho do OSSYNC
   fica na Área de Trabalho.
2. **Siga os primeiros passos:** na primeira abertura, a Visão geral mostra o que
   falta: informar os logins da Rauzee e do SIOPI, testar as conexões, instalar o
   navegador automatizado (download único) e fazer a primeira sincronização.
   O guia pode ser revisto a qualquer momento em **Ajuda e diagnóstico**.
3. **Execute:** clique em **Sincronizar agora** e acompanhe o progresso. Ao final, o
   relatório abre no próprio app, com as OSs que pedem ação no topo e as
   ocorrências resumidas no final.

Se alguma OS falhar, o OSSYNC **reagenda sozinho** uma nova tentativa só para ela.

## 🔄 Atualizações

A partir da versão 2.17.1, vá em **Configurações → Dados e retenção → Buscar atualizações**.
O app baixa a versão nova desta página, confere a impressão digital (SHA-256) do
instalador publicada pelo GitHub e instala sozinho, preservando seus dados e
configurações. Se algo der errado, o aviso aparece na tela.

Em versões anteriores, baixe e instale a versão nova por cima.

## 📄 Documentos

- [Privacidade](docs/PRIVACIDADE.md): o que fica gravado, por quanto tempo e o que é mascarado.
- [Termos de uso](docs/TERMOS_DE_USO.md).
- [Créditos de terceiros](docs/THIRD_PARTY_NOTICES.md): componentes de código aberto e suas licenças.

O OSSYNC não tem vínculo com a Caixa Econômica Federal nem com a Rauzee. Rauzee e
SIOPI são sistemas e marcas de terceiros; o app só os acessa com as suas credenciais.
O código-fonte é privado; este repositório guarda os instaladores e a documentação para quem usa.
