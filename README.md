<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Casa GIBA · Bem-vindo!</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: #F9F8F7;
    color: #2C2C2B;
    min-height: 100vh;
  }
  .hero {
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
    color: white;
    padding: 44px 20px 36px;
    text-align: center;
  }
  .hero-icon { font-size: 44px; margin-bottom: 10px; }
  .hero h1 { font-size: 28px; font-weight: 700; margin-bottom: 6px; }
  .hero p { font-size: 15px; opacity: 0.85; }

  .container {
    max-width: 480px;
    margin: 0 auto;
    padding: 20px 16px 48px;
  }
  .card {
    background: #fff;
    border-radius: 16px;
    border: 1px solid #E6E5E3;
    padding: 20px;
    margin-bottom: 16px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.03);
  }
  .card-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 16px;
  }
  .card-icon {
    width: 40px;
    height: 40px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    flex-shrink: 0;
  }
  .icon-wifi { background: #E5F2FC; }
  .icon-clock { background: #E8F1EC; }
  .icon-phone { background: #E8F1EC; }
  .icon-rules { background: #FDE8E8; }
  .icon-map { background: #FBEBDE; }

  .card-title { font-size: 16px; font-weight: 700; color: #2C2C2B; }
  .card-subtitle { font-size: 13px; color: #7D7A75; margin-top: 2px; }

  /* Wi-Fi */
  .wifi-name { font-size: 19px; font-weight: 700; color: #2783DE; margin-bottom: 8px; }
  .wifi-pass {
    font-size: 17px;
    font-weight: 600;
    background: #F0EFED;
    border-radius: 8px;
    padding: 10px 14px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .copy-btn {
    background: #2783DE;
    color: white;
    border: none;
    border-radius: 6px;
    padding: 6px 14px;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
  }
  .copy-btn:active { opacity: 0.8; }
  .wifi-qr-box {
    margin-top: 14px;
    padding-top: 14px;
    border-top: 1px dashed #E6E5E3;
    text-align: center;
  }
  .wifi-qr-box img {
    border-radius: 8px;
    border: 1px solid #E6E5E3;
    margin-top: 8px;
  }

  /* Horários */
  .times-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .time-box {
    background: #F9F8F7;
    border-radius: 10px;
    padding: 14px;
    text-align: center;
  }
  .time-label { font-size: 12px; color: #7D7A75; margin-bottom: 4px; }
  .time-value { font-size: 22px; font-weight: 700; color: #2C2C2B; }
  .time-sub { font-size: 11px; color: #7D7A75; margin-top: 2px; }

  /* Botões de Ação */
  .btn-stack { display: flex; flex-direction: column; gap: 10px; }
  .action-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    text-decoration: none;
    border-radius: 12px;
    padding: 14px;
    font-size: 15px;
    font-weight: 700;
    cursor: pointer;
    border: none;
    width: 100%;
  }
  .whatsapp-btn { background: #25D366; color: white; }
  .vcard-btn { background: #2C2C2B; color: white; }
  .action-btn:active { opacity: 0.85; }

  /* Regras e Passeios */
  .rule-item, .spot-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 10px 0;
    border-bottom: 1px solid #F0EFED;
  }
  .rule-item:last-child, .spot-item:last-child { border-bottom: none; padding-bottom: 0; }
  .item-emoji { font-size: 22px; flex-shrink: 0; }
  .item-title { font-size: 14px; font-weight: 600; margin-bottom: 2px; }
  .item-desc { font-size: 13px; color: #7D7A75; }

  .footer {
    text-align: center;
    font-size: 12px;
    color: #7D7A75;
    margin-top: 12px;
    line-height: 1.5;
  }
  .toast {
    position: fixed;
    bottom: 24px;
    left: 50%;
    transform: translateX(-50%);
    background: #2C2C2B;
    color: white;
    padding: 10px 20px;
    border-radius: 100px;
    font-size: 14px;
    font-weight: 500;
    opacity: 0;
    transition: opacity 0.3s;
    pointer-events: none;
    white-space: nowrap;
    z-index: 1000;
  }
  .toast.show { opacity: 1; }
</style>
</head>
<body>

<div class="hero">
  <div class="hero-icon">🏡</div>
  <h1 id="prop-name">Casa GIBA</h1>
  <p>Seja muito bem-vindo! Aproveite a sua estadia ✨</p>
</div>

<div class="container">

  <!-- Wi-Fi com Copiar e QR Code -->
  <div class="card">
    <div class="card-header">
      <div class="card-icon icon-wifi">📶</div>
      <div>
        <div class="card-title">Wi-Fi da Casa</div>
        <div class="card-subtitle">Ligue-se à rede sem fios</div>
      </div>
    </div>
    <div style="font-size:12px; color:#7D7A75; margin-bottom:4px;">Nome da Rede</div>
    <div class="wifi-name" id="wifi-ssid">GIBA</div>
    
    <div style="font-size:12px; color:#7D7A75; margin-bottom:4px;">Palavra-passe</div>
    <div class="wifi-pass">
      <span id="wifi-password-display">Gilberto</span>
      <button class="copy-btn" onclick="copyWifi()">Copiar</button>
    </div>

    <!-- QR Code de ligação rápida -->
    <div class="wifi-qr-box">
      <div style="font-size:12px; color:#7D7A75; margin-bottom:4px;">Acompanhante? Aponte a câmara para ligar:</div>
      <img id="wifi-qr-img" width="140" height="140" alt="QR Code Wi-Fi" />
    </div>
  </div>

  <!-- Check-in e Check-out -->
  <div class="card">
    <div class="card-header">
      <div class="card-icon icon-clock">🕐</div>
      <div>
        <div class="card-title">Horários de Estadia</div>
        <div class="card-subtitle">Entrada e saída</div>
      </div>
    </div>
    <div class="times-grid">
      <div class="time-box">
        <div class="time-label">Check-in</div>
        <div class="time-value">14:00</div>
        <div class="time-sub">a partir das 14h</div>
      </div>
      <div class="time-box">
        <div class="time-label">Check-out</div>
        <div class="time-value">12:00</div>
        <div class="time-sub">até às 12h</div>
      </div>
    </div>
  </div>

  <!-- Contacto do Anfitrião e Salvar na Agenda -->
  <div class="card">
    <div class="card-header">
      <div class="card-icon icon-phone">💬</div>
      <div>
        <div class="card-title">Suporte e Contacto</div>
        <div class="card-subtitle">Fale com o anfitrião a qualquer hora</div>
      </div>
    </div>
    <div class="btn-stack">
      <a class="action-btn whatsapp-btn" href="https://wa.me/5511996011227" target="_blank">
        Falar no WhatsApp
      </a>
      <button class="action-btn vcard-btn" onclick="downloadVCard()">
        📲 Guardar Contacto no Telemóvel
      </button>
    </div>
  </div>

  <!-- Regras da Casa -->
  <div class="card">
    <div class="card-header">
      <div class="card-icon icon-rules">📋</div>
      <div>
        <div class="card-title">Regras da Casa</div>
        <div class="card-subtitle">Para uma estadia tranquila</div>
      </div>
    </div>
    <div class="rule-item">
      <span class="item-emoji">🤫</span>
      <div>
        <div class="item-title">Horário de Silêncio</div>
        <div class="item-desc">Das 22:00 às 08:00 respeite o descanso dos vizinhos.</div>
      </div>
    </div>
    <div class="rule-item">
      <span class="item-emoji">🚭</span>
      <div>
        <div class="item-title">Proibido Fumar</div>
        <div class="item-desc">Não é permitido fumar dentro da acomodação.</div>
      </div>
    </div>
    <div class="rule-item">
      <span class="item-emoji">🗑️</span>
      <div>
        <div class="item-title">Descarte do Lixo</div>
        <div class="item-desc">Coloque os sacos fechados na lixeira externa ao sair.</div>
      </div>
    </div>
    <div class="rule-item">
      <span class="item-emoji">🚫</span>
      <div>
        <div class="item-title">Festas e Visitas</div>
        <div class="item-desc">Eventos e hóspedes não registados não são permitidos.</div>
      </div>
    </div>
  </div>

  <!-- Sugestões de Passeios -->
  <div class="card">
    <div class="card-header">
      <div class="card-icon icon-map">🗺️</div>
      <div>
        <div class="card-title">Dicas e Passeios</div>
        <div class="card-subtitle">O melhor da região ao seu alcance</div>
      </div>
    </div>
    <div class="spot-item">
      <span class="item-emoji">🍽️</span>
      <div>
        <div class="item-title">Gastronomia Local</div>
        <div class="item-desc">Consulte o anfitrião para recomendações dos melhores pratos da zona.</div>
      </div>
    </div>
    <div class="spot-item">
      <span class="item-emoji">🛒</span>
      <div>
        <div class="item-title">Supermercados e Farmácias</div>
        <div class="item-desc">Comércio local a poucos minutos de distância.</div>
      </div>
    </div>
    <div class="spot-item">
      <span class="item-emoji">🌿</span>
      <div>
        <div class="item-title">Pontos Turísticos e Natureza</div>
        <div class="item-desc">Praias, parques e trilhos próximos para visitar durante o dia.</div>
      </div>
    </div>
  </div>

</div>

<div class="footer">
  🏡 Casa GIBA · Desejamos-lhe uma excelente estadia!<br>
  Criado para leitura por aproximação NFC & QR Code.
</div>

<div class="toast" id="toast">✅ Palavra-passe copiada!</div>

<script>
  // DADOS DA CASA (Fácil de alterar para cada cliente)
  const CONFIG = {
    nomeCasa: "Casa GIBA",
    wifiSsid: "GIBA",
    wifiPass: "Gilberto",
    telefone: "+55 11 99601-1227",
    whatsappClean: "5511996011227"
  };

  // Gerador automático do QR Code Wi-Fi compatível com câmaras
  window.addEventListener('DOMContentLoaded', () => {
    const wifiQrPayload = `WIFI:T:WPA;S:${CONFIG.wifiSsid};P:${CONFIG.wifiPass};;`;
    const qrUrl = `https://api.qrserver.com/v1/create-qr-code/?size=160x160&data=${encodeURIComponent(wifiQrPayload)}`;
    document.getElementById('wifi-qr-img').src = qrUrl;
  });

  // Copiar senha com aviso
  function copyWifi() {
    navigator.clipboard.writeText(CONFIG.wifiPass).then(() => {
      const t = document.getElementById('toast');
      t.classList.add('show');
      setTimeout(() => t.classList.remove('show'), 2000);
    });
  }

  // Gera e descarrega o ficheiro de contacto (.vcf)
  function downloadVCard() {
    const vcardData = 
`BEGIN:VCARD
VERSION:3.0
FN:Anfitrião - ${CONFIG.nomeCasa}
ORG:${CONFIG.nomeCasa}
TEL;TYPE=CELL:${CONFIG.telefone}
NOTE:Wi-Fi: ${CONFIG.wifiSsid} | Senha: ${CONFIG.wifiPass}
END:VCARD`;

    const blob = new Blob([vcardData], { type: 'text/vcard;charset=utf-8;' });
    const link = document.createElement('a');
    link.href = URL.createObjectURL(blob);
    link.download = `Contacto_${CONFIG.nomeCasa.replace(/\s+/g, '_')}.vcf`;
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  }
</script>

</body>
</html>
