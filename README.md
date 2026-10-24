# VGiatti Social — Repositório Oficial de Releases (OTA)

Este repositório distribui publicamente os pacotes **APK assinados** do aplicativo **VGiatti Social** e alimenta o verificador automático de atualizações Over-The-Air (OTA) integrado ao app Android.

---

## 📥 Download da Versão Atual (`v1.5.12`)

- **Última Release Oficial:** [Baixar APK mais recente (`releases/latest`)](https://github.com/murilogiatti/vgiatti_social_releases/releases/latest)
- **Pacote Android:** `com.vgiatti.social` (`versionCode 47`)

---

## ✨ Destaques da Versão `v1.5.12`

- **Motor Gráfico Canvas 2D Offscreen:** Renderização direta e determinística para **Feed 1:1 (1080×1080)** e **Stories 9:16 (1080×1920)** com fundo * Blur Cover*, vinheta cinematográfica e proteção de *safe-zones*.
- **Enquadramento da Foto (`Conter` vs `Preencher`):** Alternância rápida entre *Contain* (sem cortes) e *Cover* (preenchimento total do quadro com *rounded clip*).
- **Gerador Inteligente de Títulos (`✨ Sugerir`):** Sugestões instantâneas de *copywriting* imobiliário baseadas nos dados reais do imóvel (tipo, bairro, dormitórios e vagas).
- **Exportação Nativa Multi-Formato:**
  - **Stories (9:16):** Imagem PNG de alta definição compartilhada direto no Instagram.
  - **Feed (1:1 MP4):** Vídeo MP4 H.264 (`avc1`, 1080×1080, 30 fps) codificado via hardware Android (`MediaCodec` + `MediaMuxer`) com trilha AAC opcional.
  - **WhatsApp (GIF + Legenda):** GIF animado (480×480) + legenda completa copiada e enviada ao WhatsApp.
- **Resiliência Offline & Prefetch:** Pré-carregamento da galeria em segundo plano e catálogo de contingência offline embutido.

---

## 🔒 Segurança e Verificação OTA

O aplicativo **VGiatti Social** consulta a API deste repositório (`repos/murilogiatti/vgiatti_social_releases/releases/latest`) e realiza três validações nativas antes de acionar o instalador do Android:

1. **HTTPS Estrito:** Aceita downloads exclusivamente de `github.com` e `objects.githubusercontent.com`.
2. **Validação de Assinatura Criptográfica (SHA-256):** O APK baixado tem seu certificado confrontado com o certificado do app instalado (`UpdateInstallerPlugin.java`), bloqueando qualquer pacote adulterado.
3. **Proteção Anti-Downgrade:** O `versionCode` do APK baixado deve ser estritamente superior ao instalado no dispositivo.
