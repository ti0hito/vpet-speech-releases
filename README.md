# 🐾 VPet Speech

> Sincronização e animação de pets virtuais em tempo real a partir da voz para **VTube Studio** e **Warudo**.

[![Windows](https://img.shields.io/badge/Plataforma-Windows%2010%20%7C%2011-0078D6?logo=windows&logoColor=white)](#)
[![Status](https://img.shields.io/badge/Código-Privado%20%2F%20Proprietário-red)](#)
[![Autor](https://img.shields.io/badge/Criador-Hito-blue?logo=github)](https://github.com/ti0hito)

---

## 📖 O que é o VPet Speech?

O **VPet Speech** é um aplicativo desktop projetado especificamente para VTubers, streamers e criadores de conteúdo que utilizam pets, mascotes ou avatares secundários em suas transmissões.

Ele monitora a entrada de áudio (seja o seu microfone principal ou um cabo virtual com alertas do Livepix/Twitch) e transforma a voz em movimentos expressivos e naturais para o seu pet, sem sobrecarregar o modelo principal e sem a necessidade de plugins pesados.

---

## ✨ Como ele funciona?

O aplicativo atua como uma ponte de comunicação em tempo real entre o áudio da sua live e o software do seu modelo:

1. **Processamento Digital de Sinal (DSP de Voz):**
   * **Filtros Passa-Banda (85 Hz – 3.6 kHz):** Isola a faixa fundamental da voz humana, ignorando ruídos graves de teclado e chiados agudos.
   * **Noise Gate com Histerese:** Corta respirações, estalos e ruídos de fundo quando ninguém estiver falando.
   * **Modulador de Articulação Labial:** Destaca a abertura e fechamento natural da boca entre sílabas faladas.
   * **Compressor Soft-Knee (Anti-Grito):** Evita que risadas altas ou gritos estourem a boca ou a animação do seu modelo.

2. **Integração com VTube Studio:**
   * Conecta-se via WebSocket oficial da API de Plugins do VTube Studio.
   * Cria e injeta os parâmetros Live2D `PetVolume` (0–100) e `PetFrequency` (0–100), permitindo abrir a boca, pular ou alterar expressões de acordo com a voz.

3. **Integração com Warudo:**
   * Envia eventos e dados de precisão via WebSocket para os nós de **Blueprint** do Warudo.
   * Permite controlar nós como `Set Character BlendShape`, `Set Prop BlendShape` ou fazer o pet pular e esticar com `Lerp Vector3`.
   * Suporta eventos sem float (`PetSpeechStart` / `PetSpeechStop`) para troca automática de poses.

4. **Fila Inteligente com Speaker.bot:**
   * Pausa automaticamente a fila de leitura de mensagens por voz (TTS) do Speaker.bot assim que o áudio de um alerta ou doação do Livepix começa a tocar, retomando logo após o silêncio para que duas vozes nunca se atropelem.

5. **Modo Silencioso na Bandeja (System Tray):**
   * O aplicativo roda discretamente na área de notificação do Windows com suporte a atalhos rápidos de conexão com um clique.

---

## 📥 Download e Instalação

Você pode baixar a versão instalável mais recente na aba de [**Releases**](https://github.com/ti0hito/vpet-speech-releases/releases).

* O instalador cuida de tudo automaticamente e adiciona os atalhos no seu computador.
* **Atualizações Automáticas:** O VPet Speech possui sistema de auto-update integrado. Assim que novas funcionalidades e correções forem lançadas, o próprio app notifica e atualiza para você.

---

## 🔒 Licença e Propriedade do Código

O **VPet Speech** é um projeto de **código-fonte privado e proprietário**.

* O código-fonte deste software não é público e permanece de propriedade exclusiva do seu desenvolvedor.
* Os instaladores e executáveis oficiais disponibilizados aqui são livres para uso pessoal em suas lives e transmissões.
* É proibida a engenharia reversa, redistribuição não autorizada ou comercialização do software sem permissão prévia do autor.

---

## ⚙️ Requisitos do Sistema

* **Sistema Operacional:** Windows 10 ou Windows 11 (64-bit).
* **Softwares suportados:** VTube Studio (com API de plugins ativada) ou Warudo (versão Steam).
* **Para separar áudio de alertas/doações (Opcional):**
  * [VB-Audio Virtual Cable](https://vb-audio.com/Cable/) (Gratuito).
  * Plugin [Audio Monitor para OBS Studio](https://obsproject.com/forum/resources/audio-monitor.1186/).

---

## 📄 Licença & Créditos

Distribuído sob a licença **MIT**. Veja `LICENSE` para mais informações.

### Créditos & Reconhecimentos:
- **Desenvolvimento & Manutenção:** Desenvolvido com carinho por **[Hito](https://github.com/ti0hito)**.
- **Inspiração Conceitual:** Agradecimento especial a **[komoririck](https://github.com/komoririck)**, criador do projeto original que serviu de faísca e inspiração para a concepção do VPet Speech. Embora o projeto atual tenha sido 100% reescrito do zero (em TypeScript, Node.js e Electron) e não utilize mais nenhuma linha da base original em C#, a ideia conceitual foi brilhante e merece total reconhecimento!  
- Dúvidas, sugestões ou relatórios de bugs podem ser enviados abrindo uma [Issue](https://github.com/ti0hito/vpet-speech-releases/issues).

