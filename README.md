<div align="center">

<svg width="860" height="420" viewBox="0 0 860 420" fill="none" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <!-- Background Gradients -->
    <linearGradient id="hud-bg" x1="0" y1="0" x2="860" y2="420" gradientUnits="userSpaceOnUse">
      <stop stop-color="#050811"/>
      <stop offset="1" stop-color="#020408"/>
    </linearGradient>
    <linearGradient id="neon-cyan" x1="0" y1="0" x2="1" y2="1">
      <stop stop-color="#00f0ff"/>
      <stop offset="1" stop-color="#7000ff"/>
    </linearGradient>
    <linearGradient id="scanline" x1="0" y1="0" x2="0" y2="1">
      <stop stop-color="#00f0ff" stop-opacity="0.08"/>
      <stop offset="0.5" stop-color="#000000" stop-opacity="0.2"/>
      <stop offset="1" stop-color="#00f0ff" stop-opacity="0.08"/>
    </linearGradient>
    <!-- Grid Pattern -->
    <pattern id="hud-grid" width="20" height="20" patternUnits="userSpaceOnUse">
      <path d="M 20 0 L 0 0 0 20" fill="none" stroke="#00f0ff" stroke-width="0.5" stroke-opacity="0.07"/>
    </pattern>
  </defs>

  <style>
    .mono { font-family: 'JetBrains Mono', 'Fira Code', monospace; }
    .sans { font-family: 'Inter', -apple-system, sans-serif; }
    .neon-text { fill: #00f0ff; }
    .neon-purple { fill: #c084fc; }
    .neon-green { fill: #4ade80; }
    .dim-text { fill: #64748b; }
    .light-text { fill: #e2e8f0; font-weight: 600; }
    .header-tag { font-size: 11px; letter-spacing: 2px; fill: #38bdf8; }
    .term-title { font-size: 12px; font-weight: bold; fill: #00f0ff; letter-spacing: 1px; }
    .term-label { font-size: 11px; fill: #00f0ff; font-weight: bold; }
    .term-val { font-size: 11px; fill: #f8fafc; }
  </style>

  <!-- Main HUD Frame -->
  <rect x="2" y="2" width="856" height="416" rx="14" fill="url(#hud-bg)" stroke="#1e293b" stroke-width="1.5"/>
  <rect x="2" y="2" width="856" height="416" rx="14" fill="url(#hud-grid)"/>
  <rect x="2" y="2" width="856" height="416" rx="14" fill="url(#scanline)"/>
  
  <!-- Outer Corner Accents -->
  <path d="M 12 35 L 12 12 L 35 12" stroke="#00f0ff" stroke-width="2" fill="none"/>
  <path d="M 848 35 L 848 12 L 825 12" stroke="#00f0ff" stroke-width="2" fill="none"/>
  <path d="M 12 385 L 12 408 L 35 408" stroke="#00f0ff" stroke-width="2" fill="none"/>
  <path d="M 848 385 L 848 408 L 825 408" stroke="#00f0ff" stroke-width="2" fill="none"/>

  <!-- Top Title Bar -->
  <circle cx="28" cy="28" r="4" fill="#ef4444"/>
  <circle cx="42" cy="28" r="4" fill="#eab308"/>
  <circle cx="56" cy="28" r="4" fill="#22c55e"/>
  <text x="75" y="32" class="mono header-tag">SYSTEM.ENG // NOC_SOC_TACTICAL_TERMINAL</text>
  <text x="710" y="32" class="mono" font-size="10" fill="#22c55e">● SEC_LEVEL_01 [ARMED]</text>
  <line x1="20" y1="46" x2="840" y2="46" stroke="#1e293b" stroke-width="1"/>

  <!-- LEFT BOX: VISUAL MATRIX / CYBER HOLOGRAM -->
  <rect x="30" y="65" width="340" height="325" rx="8" fill="#030712" stroke="#00f0ff" stroke-opacity="0.3" stroke-width="1"/>
  <text x="45" y="88" class="mono" font-size="10" fill="#38bdf8" letter-spacing="1">VISUAL_MAP // SEC_TOPOLOGY_MATRIX</text>
  <line x1="45" y1="96" x2="355" y2="96" stroke="#1e293b" stroke-width="1"/>

  <!-- ASCII Hologram Core -->
  <g class="mono" font-size="9" fill="#00f0ff" opacity="0.85">
    <text x="50" y="125">     .---.       [ BORDER / EDGE CORE ]</text>
    <text x="50" y="140">    /     \      WAN ──&gt; PPPoE / BGP Peering</text>
    <text x="50" y="155">   | () () |     Status: WireGuard ACTIVE</text>
    <text x="50" y="170">    \  -  /      Throughput: 1.0 Gbps (HW-Off)</text>
    <text x="50" y="185">     '---'       Firewall: RAW + Stateful Inspection</text>
    <text x="50" y="210">  [ SECURITY TELEMETRY OVERLAY ]</text>
    <text x="50" y="225">  ├─ PORT SCAN PSD  : [ ONLINE / 0 DOWNTIME ]</text>
    <text x="50" y="240">  ├─ BRUTE FORCE BF : [ 3-STAGE MITIGATION ]</text>
    <text x="50" y="255">  ├─ THE DUDE PROBES: [ ALL SENSORS 100% UP ]</text>
    <text x="50" y="270">  └─ MSS CLAMPING   : [ AUTO PMTU ENABLED ]</text>
    <text x="50" y="300" fill="#c084fc">  &gt; SYSTEM TARGET: CELIO ASSIS // OPERATOR</text>
    <text x="50" y="318" fill="#4ade80">  &gt; CONVERGENCE : HIGH AVAILABILITY L2/L3</text>
    <text x="50" y="336" fill="#38bdf8">  &gt; LATENCY NOC : 0.8ms [JITTER 0.02ms]</text>
  </g>
  <rect x="45" y="355" width="310" height="20" rx="3" fill="#082f49" stroke="#00f0ff" stroke-width="0.5"/>
  <text x="110" y="369" class="mono" font-size="10" fill="#38bdf8">NODE ID: KIDPEACES // MT-CORE-01</text>

  <!-- RIGHT BOX: TELEMETRY & PROFILE SYSTEM DATA -->
  <g transform="translate(395, 65)">
    <!-- Section 1: Identity Info -->
    <rect x="0" y="0" width="435" height="110" rx="8" fill="#030712" stroke="#1e293b" stroke-width="1"/>
    <text x="15" y="22" class="mono term-title">// SYSTEM_INFO // OPERATOR_PROFILE</text>
    <line x1="15" y1="30" x2="420" y2="30" stroke="#1e293b" stroke-width="1"/>
    
    <text x="15" y="48" class="mono term-label">Subject:</text>
    <text x="115" y="48" class="sans term-val">Célio Assis</text>

    <text x="15" y="66" class="mono term-label">Specialty:</text>
    <text x="115" y="66" class="mono term-val neon-purple">NOC &amp; Network Infrastructure Specialist</text>

    <text x="15" y="84" class="mono term-label">Focus Area:</text>
    <text x="115" y="84" class="sans term-val">Borda IP, Roteamento BGP/OSPF, Defesa SOC</text>

    <text x="15" y="102" class="mono term-label">Status:</text>
    <text x="115" y="102" class="mono term-val neon-green">PROVISIONED &amp; OPERATIONAL [2026]</text>

    <!-- Section 2: Stack Matrix -->
    <rect x="0" y="120" width="435" height="105" rx="8" fill="#030712" stroke="#1e293b" stroke-width="1"/>
    <text x="15" y="142" class="mono term-title">// PROTOCOLS &amp; HARDWARE STACK</text>
    <line x1="15" y1="150" x2="420" y2="150" stroke="#1e293b" stroke-width="1"/>

    <text x="15" y="168" class="mono term-label">Edge &amp; Core:</text>
    <text x="115" y="168" class="mono term-val">MikroTik RouterOS v6/v7, BGP, OSPF, MPLS</text>

    <text x="15" y="186" class="mono term-label">Tunnels &amp; Sec:</text>
    <text x="115" y="186" class="mono term-val">WireGuard, L2TP/IPsec, Firewall RAW/Mangle</text>

    <text x="15" y="204" class="mono term-label">Monitoring:</text>
    <text x="115" y="204" class="mono term-val">The Dude Server, SNMP v2c/v3, Syslog NOC</text>

    <!-- Section 3: Direct Tactical Links -->
    <rect x="0" y="235" width="435" height="90" rx="8" fill="#030712" stroke="#00f0ff" stroke-opacity="0.3" stroke-width="1"/>
    <text x="15" y="255" class="mono term-title">// DIRECT_GRID_LINKS</text>
    <line x1="15" y1="262" x2="420" y2="262" stroke="#1e293b" stroke-width="1"/>

    <text x="15" y="280" class="mono term-label">Live Portal:</text>
    <text x="115" y="280" class="mono term-val neon-cyan">celiothekid.github.io</text>

    <text x="15" y="298" class="mono term-label">Instagram:</text>
    <text x="115" y="298" class="mono term-val">@kidpeaces</text>

    <text x="15" y="316" class="mono term-label">WhatsApp:</text>
    <text x="115" y="316" class="mono term-val neon-green">+55 (65) 98442-3873</text>
  </g>

  <!-- Bottom Terminal Status Bar -->
  <text x="30" y="405" class="mono" font-size="10" fill="#64748b">SYSTEM_ID: ASSIS-009 // ENCRYPTED SESSION // NOC &amp; SOC HARDENED</text>
  <text x="730" y="405" class="mono" font-size="10" fill="#00f0ff">TERM: ttyS0_OK</text>
</svg>

<br/>

<p align="center">
  <a href="https://celiothekid.github.io"><img src="https://img.shields.io/badge/🌐_LIVE_LAB-PORTAL-00f0ff?style=for-the-badge&labelColor=050811" alt="Live Lab"/></a>
  <a href="https://wa.me/5565984423873"><img src="https://img.shields.io/badge/📱_WHATSAPP-DIRECT-25d366?style=for-the-badge&labelColor=050811" alt="WhatsApp"/></a>
  <a href="https://instagram.com/kidpeaces/"><img src="https://img.shields.io/badge/📸_INSTAGRAM-@KIDPEACES-e1306c?style=for-the-badge&labelColor=050811" alt="Instagram"/></a>
</p>

</div>

---

### 🛠️ Matriz de Operações & Roteamento

```text
 [ BORDA & ROTEAMENTO ] ─────> BGP Peering, RouterOS v6/v7, OSPF Multi-Area, Failover Recursivo
 [ CRIPTOGRAFIA & VPN ] ─────> WireGuard Protocol, IKEv2 / IPsec Suite, L2TP, MSS Clamping
 [ DEFESA ATIVA & SOC ] ─────> Filtro RAW Anti-DDoS, Mitigação Brute-Force 3 Estágios, Drop Scans
 [ TELEMETRIA & NOC ]   ─────> The Dude Server, SNMP v2c/v3, Syslog Centralizado, Auto-Health Check
