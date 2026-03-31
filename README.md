<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>OSH — Cruz de Segurança</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow:wght@400;500;600;700;800&family=Barlow+Condensed:wght@400;600;700;800&display=swap');
*{box-sizing:border-box;margin:0;padding:0;}
:root{
  --bg:#0c1520;--hbg:#0a1118;--panel:#111d28;--card:#0e1822;--border:#1e2f3e;
  --acc:#F47B20;
  --tv:#d8e0e8;--ts:#6e8898;--tm:#3a5060;
  --g:#EAF3DE;--gb:#639922;--gt:#27500A;
  --tl:#E1F5EE;--tlb:#1D9E75;--tlt:#085041;
  --bl:#E6F1FB;--blb:#185FA5;--blt:#0C447C;
  --rb:#A32D2D;--rt:#791F1F;--rf:#FCEBEB;
  --amb:#BA7517;--amt:#633806;--amf:#FAEEDA;
  --orb:#D85A30;--ort:#712B13;--orf:#FAECE7;
  --pb:#185FA5;--pt:#0C447C;--pf:#E6F1FB;
}
html,body{width:100%;min-height:100vh;background:var(--bg);color:var(--tv);font-family:'Barlow',sans-serif;font-size:14px;}
.sync-bar{display:flex;align-items:center;gap:6px;padding:3px 10px;border-radius:99px;font-size:9px;font-weight:600;letter-spacing:.06em;transition:all .4s;}
.sync-bar.ok{background:#071510;color:#1D9E75;border:1px solid #1D9E75;}
.sync-bar.saving{background:#1c140a;color:#BA7517;border:1px solid #BA7517;}
.sync-bar.err{background:#160b0b;color:#F09595;border:1px solid #A32D2D;}
.sync-dot{width:6px;height:6px;border-radius:50%;background:currentColor;}
.hdr{display:flex;align-items:center;justify-content:space-between;padding:10px 24px;background:var(--hbg);border-bottom:2px solid var(--acc);}
.hdr-l{display:flex;align-items:center;gap:14px;}
.hdr-title .ht{font-family:'Barlow Condensed',sans-serif;font-size:18px;font-weight:800;color:var(--tv);letter-spacing:.5px;}
.hdr-title .hs{font-size:10px;color:var(--acc);letter-spacing:.1em;text-transform:uppercase;margin-top:1px;}
.hdr-r{display:flex;gap:12px;align-items:center;}
.hf{display:flex;flex-direction:column;align-items:flex-end;gap:2px;}
.hf label{font-size:8px;color:var(--acc);letter-spacing:.1em;text-transform:uppercase;}
.hf input{background:transparent;border:none;border-bottom:1.5px solid var(--acc);color:var(--tv);font-size:13px;font-weight:600;font-family:'Barlow',sans-serif;outline:none;text-align:right;width:130px;padding:2px 3px;}
.hf input::placeholder{color:#253545;font-weight:400;}
.clk{font-family:'Barlow Condensed',sans-serif;font-size:22px;font-weight:800;color:var(--acc);}
.tabs{display:flex;gap:2px;padding:8px 24px 0;background:var(--hbg);}
.tab{padding:7px 22px;font-family:'Barlow Condensed',sans-serif;font-size:12px;font-weight:700;color:var(--tm);border-radius:6px 6px 0 0;cursor:pointer;border:1px solid var(--border);border-bottom:none;background:var(--panel);letter-spacing:.1em;text-transform:uppercase;transition:all .2s;}
.tab:hover{color:var(--ts);}
.tab.on{background:var(--bg);color:var(--tv);border-color:var(--acc);border-bottom:1px solid var(--bg);}
.tb{display:none;padding:20px 24px 16px;}
.tb.on{display:block;}
.sec{font-family:'Barlow Condensed',sans-serif;font-size:10px;font-weight:700;color:var(--acc);letter-spacing:.15em;text-transform:uppercase;padding-bottom:6px;border-bottom:1px solid var(--border);margin-bottom:14px;}
/* TAB 1 */
.field-group{display:flex;flex-direction:column;gap:6px;}
.field-label{font-family:'Barlow Condensed',sans-serif;font-size:11px;font-weight:700;color:var(--ts);letter-spacing:.12em;text-transform:uppercase;}
.field-input{background:var(--panel);border:1px solid var(--border);border-radius:6px;color:var(--tv);font-family:'Barlow',sans-serif;font-size:22px;font-weight:500;padding:12px 16px;outline:none;width:100%;transition:border-color .2s;}
.field-input:focus{border-color:var(--acc);}
.field-input:hover{border-color:var(--ts);}
/* TAB 2 */
.painel-layout{display:grid;grid-template-columns:1fr 1.55fr;gap:20px;}
.ind-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:16px;}
.icard{border-radius:9px;padding:12px 14px;display:flex;flex-direction:column;gap:4px;}
.ic-g{background:#0c1c0e;border:1.5px solid var(--gb);}
.ic-tl{background:#071510;border:1.5px solid var(--tlb);}
.ic-bl{background:#060f1c;border:1.5px solid var(--blb);}
.icard-lbl{font-family:'Barlow Condensed',sans-serif;font-size:9px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;opacity:.75;}
.icard-val{font-family:'Barlow Condensed',sans-serif;font-size:38px;font-weight:800;line-height:1;}
.icard-sub{font-size:9px;opacity:.55;margin-top:1px;}
/* Calendário */
.cal-sec{display:flex;flex-direction:column;gap:0;}
.cal-leg{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:8px;}
.leg{display:flex;align-items:center;gap:4px;font-size:9px;font-weight:600;padding:3px 8px;border-radius:99px;cursor:pointer;border:1.5px solid transparent;transition:all .15s;}
.leg.on{border-color:currentColor;box-shadow:0 0 0 2px rgba(255,255,255,.04);}
.leg:hover{opacity:.85;}
.ld{width:8px;height:8px;border-radius:50%;flex-shrink:0;}
.lv{background:var(--g);color:var(--gt);} .lv .ld{background:var(--gb);}
.la{background:var(--amf);color:var(--amt);} .la .ld{background:var(--amb);}
.lr{background:var(--rf);color:var(--rt);} .lr .ld{background:var(--rb);}
.dhr{display:grid;grid-template-columns:repeat(7,1fr);gap:3px;margin-bottom:3px;}
.dh{text-align:center;font-family:'Barlow Condensed',sans-serif;font-size:10px;font-weight:700;color:var(--acc);padding:3px 0;letter-spacing:.05em;}
.dg{display:grid;grid-template-columns:repeat(7,1fr);gap:3px;}
.dc{border-radius:7px;border:1px solid var(--border);background:var(--panel);cursor:pointer;transition:transform .1s,border-color .15s;min-height:42px;padding:3px;display:flex;flex-direction:column;align-items:center;}
.dc:hover{transform:scale(1.07);border-color:var(--acc);}
.dc.em{background:transparent;border:none;cursor:default;} .dc.em:hover{transform:none;}
.dn{font-family:'Barlow Condensed',sans-serif;font-size:12px;font-weight:700;color:var(--ts);line-height:1.5;}
.dd{display:flex;flex-wrap:wrap;gap:2px;justify-content:center;padding:1px 0;}
.dot{width:7px;height:7px;border-radius:50%;}
/* Cores dos pontos: v=verde, a=amarelo, o=AZUL(PS), p=LARANJA(s/afas), r=vermelho */
.dv{background:var(--gb);} .da{background:var(--amb);} .do2{background:var(--pb);} .dp2{background:var(--orb);} .dr2{background:var(--rb);}
.ddet{background:#060d16;border:2px solid var(--acc);border-radius:10px;padding:10px 14px;margin-top:8px;}
.ddt{font-family:'Barlow Condensed',sans-serif;font-size:11px;font-weight:700;color:var(--acc);margin-bottom:8px;letter-spacing:.05em;}
.ddtg{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:4px;}
.dtag{font-size:10px;font-weight:600;padding:4px 10px;border-radius:99px;cursor:pointer;border:1.5px solid transparent;transition:all .15s;}
.dtag.on{border-color:currentColor;box-shadow:0 0 0 1.5px currentColor;}
.dtag:hover{opacity:.8;}
.dtv{background:var(--g);color:var(--gt);}
.dta{background:var(--amf);color:var(--amt);}
.dto{background:var(--pf);color:var(--pt);}   /* PS = azul */
.dtp{background:var(--orf);color:var(--ort);}  /* s/afas = laranja */
.dtr{background:var(--rf);color:var(--rt);}
.dclose{font-size:9px;color:var(--tm);cursor:pointer;float:right;padding:0 0 0 8px;}
.dclose:hover{color:var(--tv);}
.right-panel{display:flex;flex-direction:column;gap:14px;}
.og{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.oc{border-radius:11px;padding:13px 16px;display:flex;flex-direction:column;gap:4px;transition:transform .15s;}
.oc:hover{transform:scale(1.02);}
.ov{background:#0c1c0e;border:1.5px solid var(--gb);}
.oa{background:#1c140a;border:1.5px solid var(--amb);}
.ops{background:#060f1c;border:1.5px solid var(--pb);}   /* PS = azul */
.osa{background:#1c0f08;border:1.5px solid var(--orb);}  /* s/afas = laranja */
.or2{background:#1c0b0b;border:1.5px solid var(--rb);}
.otop{display:flex;align-items:center;gap:7px;}
.odot{width:10px;height:10px;border-radius:50%;flex-shrink:0;}
.on2{font-size:12px;font-weight:600;}
.onum{font-family:'Barlow Condensed',sans-serif;font-size:50px;font-weight:800;line-height:1;text-align:right;}
.pb2{height:4px;border-radius:2px;background:#1a2632;overflow:hidden;}
.pf2{height:100%;border-radius:2px;transition:width .6s cubic-bezier(.4,0,.2,1);}
.od{font-size:9px;opacity:.55;margin-top:2px;}
.meta-card{background:#060d18;border:1.5px solid var(--blb);border-radius:10px;padding:12px 16px;display:flex;justify-content:space-between;align-items:center;}
.meta-l{display:flex;flex-direction:column;gap:3px;}
.meta-title{font-family:'Barlow Condensed',sans-serif;font-size:12px;font-weight:700;color:#85B7EB;letter-spacing:.08em;text-transform:uppercase;}
.meta-sub{font-size:10px;color:var(--tm);}
.meta-vals{display:flex;gap:20px;}
.mv{display:flex;flex-direction:column;align-items:center;gap:2px;}
.mvn{font-family:'Barlow Condensed',sans-serif;font-size:30px;font-weight:800;color:#378ADD;}
.mvl{font-size:8px;color:var(--tm);text-transform:uppercase;letter-spacing:.05em;}
/* TAB 3 - ATIVIDADES */
.ativ-layout{display:grid;grid-template-columns:1fr 1fr;gap:20px;}
.ativ-form{display:flex;flex-direction:column;gap:14px;}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.fg{display:flex;flex-direction:column;gap:5px;}
.fl{font-family:'Barlow Condensed',sans-serif;font-size:10px;font-weight:700;color:var(--ts);letter-spacing:.1em;text-transform:uppercase;}
.fi{background:var(--panel);border:1px solid var(--border);border-radius:6px;color:var(--tv);font-family:'Barlow',sans-serif;font-size:13px;padding:9px 12px;outline:none;width:100%;transition:border-color .2s;}
.fi:focus{border-color:var(--acc);}
.fi::placeholder{color:var(--tm);}
.tipo-grid{display:grid;grid-template-columns:1fr 1fr;gap:6px;}
.tipo-btn{background:var(--panel);border:1px solid var(--border);border-radius:7px;color:var(--ts);font-family:'Barlow',sans-serif;font-size:11px;font-weight:500;padding:8px 10px;cursor:pointer;display:flex;align-items:center;gap:7px;transition:all .2s;}
.tipo-btn:hover{border-color:var(--ts);color:var(--tv);}
.tipo-btn.on.t-quente{background:#1c0f08;border-color:var(--orb);color:var(--tv);}
.tipo-btn.on.t-elet{background:#060f1c;border-color:var(--blb);color:var(--tv);}
.tipo-btn.on.t-altura{background:#0c1c0e;border-color:var(--gb);color:var(--tv);}
.tipo-btn.on.t-ica{background:#160b0b;border-color:var(--rb);color:var(--tv);}
.tipo-btn.on.t-espc{background:#1c140a;border-color:var(--amb);color:var(--tv);}
.tipo-btn.on.t-outr{background:#111d28;border-color:var(--ts);color:var(--tv);}
.tipo-icon{font-size:15px;flex-shrink:0;}
.tec-grid{display:grid;grid-template-columns:1fr 1fr;gap:6px;}
.tec-btn{background:var(--panel);border:1px solid var(--border);border-radius:7px;color:var(--ts);font-family:'Barlow',sans-serif;font-size:12px;font-weight:600;padding:8px 12px;cursor:pointer;transition:all .2s;text-align:center;}
.tec-btn:hover{border-color:var(--ts);color:var(--tv);}
.tec-btn.on{background:#0d1a2a;border-color:var(--blb);color:#85B7EB;}
.add-btn{background:var(--acc);border:none;border-radius:7px;color:#fff;font-family:'Barlow Condensed',sans-serif;font-size:13px;font-weight:700;padding:11px 20px;cursor:pointer;letter-spacing:.08em;text-transform:uppercase;transition:background .2s;width:100%;}
.add-btn:hover{background:#d46a18;}
.ativ-lista{display:flex;flex-direction:column;gap:8px;overflow-y:auto;max-height:calc(100vh - 220px);}
.ativ-card{background:var(--panel);border:1px solid var(--border);border-radius:10px;padding:12px 14px;display:flex;flex-direction:column;gap:8px;}
.ativ-card:hover{border-color:var(--ts);}
.ativ-card-top{display:flex;align-items:flex-start;justify-content:space-between;gap:8px;}
.ativ-tipo-tags{display:flex;gap:4px;flex-wrap:wrap;}
.atag{font-size:9px;font-weight:700;padding:2px 7px;border-radius:99px;font-family:'Barlow Condensed',sans-serif;letter-spacing:.05em;}
.atag-quente{background:#1c0f08;color:#F0997B;border:1px solid var(--orb);}
.atag-elet{background:#060f1c;color:#85B7EB;border:1px solid var(--blb);}
.atag-altura{background:#0c1c0e;color:#5DCAA5;border:1px solid var(--gb);}
.atag-ica{background:#160b0b;color:#F09595;border:1px solid var(--rb);}
.atag-espc{background:#1c140a;color:#EF9F27;border:1px solid var(--amb);}
.atag-outr{background:#111d28;color:var(--ts);border:1px solid var(--border);}
.ativ-del{background:none;border:none;color:var(--tm);cursor:pointer;font-size:14px;padding:0 2px;line-height:1;transition:color .15s;flex-shrink:0;}
.ativ-del:hover{color:#F09595;}
.ativ-nums{display:flex;gap:14px;}
.ativ-num-item{display:flex;flex-direction:column;align-items:center;gap:1px;}
.ativ-num-val{font-family:'Barlow Condensed',sans-serif;font-size:26px;font-weight:800;color:var(--acc);line-height:1;}
.ativ-num-lbl{font-size:8px;color:var(--tm);text-transform:uppercase;letter-spacing:.07em;}
.ativ-info-row{display:flex;gap:14px;flex-wrap:wrap;align-items:center;}
.ativ-info-item{display:flex;align-items:center;gap:5px;font-size:10px;color:var(--ts);}
.ativ-info-dot{width:6px;height:6px;border-radius:50%;background:var(--acc);flex-shrink:0;}
.ativ-tec-tags{display:flex;gap:4px;flex-wrap:wrap;}
.ttag{font-size:9px;font-weight:600;padding:2px 8px;border-radius:99px;background:#0d1a2a;color:#85B7EB;border:1px solid var(--blb);}
.lista-vazia{text-align:center;color:var(--tm);font-size:12px;padding:40px 20px;}
.lista-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px;}
.resumo-bar{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px;}
.res-card{background:var(--panel);border:1px solid var(--border);border-radius:8px;padding:8px 12px;display:flex;flex-direction:column;gap:2px;}
.res-val{font-family:'Barlow Condensed',sans-serif;font-size:30px;font-weight:800;color:var(--acc);}
.res-lbl{font-size:9px;color:var(--tm);text-transform:uppercase;letter-spacing:.07em;}
.ftr{display:flex;align-items:center;justify-content:space-between;padding:6px 24px;background:var(--hbg);border-top:1px solid var(--border);}
.fh{font-size:9px;color:#1e3040;}
.fb{font-size:9px;color:#1e3040;cursor:pointer;background:none;border:none;font-family:'Barlow',sans-serif;transition:color .15s;padding:4px 8px;border-radius:4px;}
.fb:hover{color:var(--ts);background:var(--border);}
</style>
</head>
<body>

<div class="hdr">
  <div class="hdr-l">
    <img src="data:image/jpeg;base64,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" alt="TKE" style="height:36px;width:auto;border-radius:4px;">
    <div class="hdr-title">
      <div class="ht">OSH</div>
    </div>
  </div>
  <div class="hdr-r">
    <div class="sync-bar saving" id="sync-bar"><span class="sync-dot"></span><span id="sync-txt">Conectando...</span></div>
    <div class="hf"><label>Mês vigente</label><input id="hmes" type="text" placeholder="Ex: Março 2026" maxlength="18" oninput="syncMes()"></div>
    <div class="clk" id="clk">--:--</div>
  </div>
</div>

<div class="tabs">
  <div class="tab on" onclick="shtab('ind',this)">Indicadores</div>
  <div class="tab" onclick="shtab('painel',this)">Painel do Mês</div>
  <div class="tab" onclick="shtab('ativ',this)">Atividades do Dia</div>
</div>

<!-- TAB 1: só 1 campo -->
<div class="tb on" id="tab-ind">
  <div class="sec">Atualização diária</div>
  <div style="max-width:420px;">
    <div class="field-group">
      <div class="field-label">Dias sem ocorrências</div>
      <input class="field-input" id="v1" type="number" min="0" value="0" oninput="saveInd()">
    </div>
  </div>
</div>

<!-- TAB 2: Painel do Mês -->
<div class="tb" id="tab-painel">
  <div class="ind-cards" style="grid-template-columns:1fr 1fr;">
    <div class="icard ic-g">
      <div class="icard-lbl" style="color:#5DCAA5">Dias sem ocorrências</div>
      <div class="icard-val" style="color:#5DCAA5" id="ic1">0</div>
      <div class="icard-sub" style="color:#5DCAA5">dias</div>
    </div>
    <div class="icard ic-bl">
      <div class="icard-lbl" style="color:#85B7EB">Recorde</div>
      <div class="icard-val" style="color:#378ADD" id="ic3">—</div>
      <div class="icard-sub" style="color:#378ADD">dias</div>
    </div>
  </div>
  <div class="painel-layout">
    <div class="cal-sec">
      <div class="sec">Calendário — <span id="cml" style="color:var(--acc);font-weight:400;">—</span></div>
      <div class="cal-leg">
        <div class="leg lv" data-c="v" onclick="selc('v')"><span class="ld"></span>Sem ocorrência</div>
        <div class="leg la" data-c="a" onclick="selc('a')"><span class="ld"></span>Incidente</div>
        <div class="leg" style="background:var(--pf);color:var(--pt);" data-c="o" onclick="selc('o')"><span class="ld" style="background:var(--pb);"></span>Primeiros socorros</div>
        <div class="leg" style="background:var(--orf);color:var(--ort);" data-c="p" onclick="selc('p')"><span class="ld" style="background:var(--orb);"></span>Acid. s/ afastamento</div>
        <div class="leg lr" data-c="r" onclick="selc('r')"><span class="ld"></span>Acid. c/ afastamento</div>
      </div>
      <div class="dhr" id="dhr"></div>
      <div class="dg" id="dg"></div>
      <div id="ddw"></div>
      <div style="margin-top:10px;">
        <button class="fb" onclick="rcal()" style="border:1px solid var(--border);">Limpar calendário</button>
      </div>
    </div>
    <div class="right-panel">
      <div>
        <div class="sec">Ocorrências do mês — detalhamento</div>
        <div class="og" style="grid-template-columns:1fr 1fr 1fr;">
          <div class="oc ov">
            <div class="otop"><div class="odot" style="background:var(--gb)"></div><div class="on2" style="color:#5DCAA5">Sem ocorrência</div></div>
            <div class="onum" style="color:#5DCAA5" id="oc1">0</div>
            <div class="pb2"><div class="pf2" style="background:var(--gb)" id="op1"></div></div>
            <div class="od" style="color:#5DCAA5" id="od1">0 registros</div>
          </div>
          <div class="oc oa">
            <div class="otop"><div class="odot" style="background:var(--amb)"></div><div class="on2" style="color:#EF9F27">Incidentes</div></div>
            <div class="onum" style="color:#EF9F27" id="oc2">0</div>
            <div class="pb2"><div class="pf2" style="background:var(--amb)" id="op2"></div></div>
            <div class="od" style="color:#EF9F27" id="od2">0 registros</div>
          </div>
          <div class="oc ops">
            <div class="otop"><div class="odot" style="background:var(--pb)"></div><div class="on2" style="color:#85B7EB">Primeiros socorros</div></div>
            <div class="onum" style="color:#85B7EB" id="oc3">0</div>
            <div class="pb2"><div class="pf2" style="background:var(--pb)" id="op3"></div></div>
            <div class="od" style="color:#85B7EB" id="od3">0 registros</div>
          </div>
          <div class="oc osa">
            <div class="otop"><div class="odot" style="background:var(--orb)"></div><div class="on2" style="color:#F0997B">Acid. s/ afastamento</div></div>
            <div class="onum" style="color:#F0997B" id="oc5">0</div>
            <div class="pb2"><div class="pf2" style="background:var(--orb)" id="op5"></div></div>
            <div class="od" style="color:#F0997B" id="od5">0 registros</div>
          </div>
          <div class="oc or2">
            <div class="otop"><div class="odot" style="background:var(--rb)"></div><div class="on2" style="color:#F09595">Acid. c/ afastamento</div></div>
            <div class="onum" style="color:#F09595" id="oc4">0</div>
            <div class="pb2"><div class="pf2" style="background:var(--rb)" id="op4"></div></div>
            <div class="od" style="color:#F09595" id="od4">0 registros</div>
          </div>
        </div>
      </div>
      <div>
        <div class="sec">Meta</div>
        <div class="meta-card">
          <div class="meta-l">
            <div class="meta-title">Superar o recorde</div>
            <div class="meta-sub" id="mtxt">—</div>
          </div>
          <div class="meta-vals">
            <div class="mv"><div class="mvn" id="mva">0</div><div class="mvl">dias atual</div></div>
            <div style="width:1px;background:var(--border);align-self:stretch;"></div>
            <div class="mv"><div class="mvn" id="mvr">—</div><div class="mvl">recorde</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- TAB 3: Atividades do Dia -->
<div class="tb" id="tab-ativ">
  <div class="resumo-bar">
    <div class="res-card"><div class="res-val" id="res-pt">0</div><div class="res-lbl">PTs em aberto</div></div>
    <div class="res-card"><div class="res-val" id="res-apr">0</div><div class="res-lbl">APRs liberadas</div></div>
    <div class="res-card"><div class="res-val" id="res-ativ">0</div><div class="res-lbl">Atividades registradas</div></div>
  </div>
  <div class="ativ-layout">
    <div class="ativ-form">
      <div class="sec">Nova atividade</div>
      <div class="form-row">
        <div class="fg"><div class="fl">Nº PT</div><input class="fi" id="f-pt" type="text" placeholder="Ex: PT-2026-041"></div>
        <div class="fg"><div class="fl">Nº APR</div><input class="fi" id="f-apr" type="text" placeholder="Ex: APR-041"></div>
      </div>
      <div class="fg"><div class="fl">Descrição da atividade</div><input class="fi" id="f-desc" type="text" placeholder="Ex: Soldagem em tubulação de vapor"></div>
      <div class="fg">
        <div class="fl">Tipo de atividade</div>
        <div class="tipo-grid">
          <button type="button" class="tipo-btn t-quente" data-tipo="quente" onclick="toggleTipo(this)"><span class="tipo-icon">🔥</span>Trabalho a quente</button>
          <button type="button" class="tipo-btn t-elet" data-tipo="elet" onclick="toggleTipo(this)"><span class="tipo-icon">⚡</span>Trabalho c/ eletricidade</button>
          <button type="button" class="tipo-btn t-altura" data-tipo="altura" onclick="toggleTipo(this)"><span class="tipo-icon">🏗</span>Trabalho em altura</button>
          <button type="button" class="tipo-btn t-ica" data-tipo="ica" onclick="toggleTipo(this)"><span class="tipo-icon">🏋</span>Içamento de carga</button>
          <button type="button" class="tipo-btn t-espc" data-tipo="espc" onclick="toggleTipo(this)"><span class="tipo-icon">⬛</span>Espaço confinado</button>
          <button type="button" class="tipo-btn t-outr" data-tipo="outr" onclick="toggleTipo(this)"><span class="tipo-icon">📋</span>Outro</button>
        </div>
      </div>
      <div class="fg">
        <div class="fl">Técnico(s) responsável(is)</div>
        <div class="tec-grid">
          <button type="button" class="tec-btn" data-tec="Fernanda" onclick="toggleTec(this)">Fernanda</button>
          <button type="button" class="tec-btn" data-tec="Jéssica" onclick="toggleTec(this)">Jéssica</button>
          <button type="button" class="tec-btn" data-tec="Jonathan" onclick="toggleTec(this)">Jonathan</button>
          <button type="button" class="tec-btn" data-tec="Juliana" onclick="toggleTec(this)">Juliana</button>
        </div>
      </div>
      <div class="form-row">
        <div class="fg"><div class="fl">Data de início</div><input class="fi" id="f-data" type="date"></div>
        <div class="fg"><div class="fl">Previsão de término</div><input class="fi" id="f-fim" type="date"></div>
      </div>
      <button class="add-btn" onclick="addAtiv()">+ Registrar atividade</button>
      <div id="f-erro" style="font-size:10px;color:#F09595;min-height:16px;"></div>
    </div>
    <div>
      <div class="lista-header">
        <div class="sec" style="margin-bottom:0;border-bottom:none;padding-bottom:0;">Atividades registradas</div>
        <button class="fb" onclick="limparAtiv()" style="font-size:10px;border:1px solid var(--border);color:var(--tm);">Limpar tudo</button>
      </div>
      <div class="ativ-lista" id="ativ-lista">
        <div class="lista-vazia">Nenhuma atividade registrada ainda.</div>
      </div>
    </div>
  </div>
</div>

<div class="ftr">
  <div class="fh" id="fh">Selecione uma cor na legenda e clique nos dias — múltiplas ocorrências por dia são permitidas</div>
  <button class="fb" onclick="rcal()" style="border:1px solid var(--border);">Limpar calendário</button>
</div>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
import { getDatabase, ref, set, onValue, remove } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-database.js";

const firebaseConfig = {
  apiKey: "AIzaSyDx_o35V45LmPe0q2sCUHuCdwsWTTPfy24",
  authDomain: "painel-osh.firebaseapp.com",
  databaseURL: "https://painel-osh-default-rtdb.firebaseio.com",
  projectId: "painel-osh",
  storageBucket: "painel-osh.firebasestorage.app",
  messagingSenderId: "260850861591",
  appId: "1:260850861591:web:a38504123dd7d26f0bbe52"
};
const app = initializeApp(firebaseConfig);
const db  = getDatabase(app);

// ── STATUS ──
let saveTimer = null;
function setSyncStatus(s) {
  const bar = document.getElementById('sync-bar');
  const txt = document.getElementById('sync-txt');
  bar.className = 'sync-bar ' + s;
  txt.textContent = s==='ok'?'Sincronizado':s==='saving'?'Salvando...':'Erro de conexão';
}
function scheduleSave(fn) {
  setSyncStatus('saving');
  clearTimeout(saveTimer);
  saveTimer = setTimeout(() => { fn(); setSyncStatus('ok'); }, 700);
}

// ── RELÓGIO ──
function tk() {
  const n = new Date();
  document.getElementById('clk').textContent =
    String(n.getHours()).padStart(2,'0')+':'+String(n.getMinutes()).padStart(2,'0');
}
tk(); setInterval(tk, 10000);

// ── TABS ──
window.shtab = (id, el) => {
  document.querySelectorAll('.tb').forEach(t => t.classList.remove('on'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('on'));
  document.getElementById('tab-'+id).classList.add('on');
  el.classList.add('on');
};

// ── MÊS ──
const mesesPT = {
  'janeiro':0,'fevereiro':1,'março':2,'marco':2,'abril':3,'maio':4,'junho':5,
  'julho':6,'agosto':7,'setembro':8,'outubro':9,'novembro':10,'dezembro':11
};
function parseMes(str) {
  str = (str||'').trim().toLowerCase();
  let month=-1, year=-1;
  for (const [n,i] of Object.entries(mesesPT)) { if (str.includes(n)) { month=i; break; } }
  const nums = str.match(/\d+/g)||[];
  if (month===-1) { for (const n of nums) { const v=parseInt(n); if(v>=1&&v<=12&&n.length<=2){month=v-1;break;} } }
  for (const n of nums) { if(n.length===4){year=parseInt(n);break;} }
  return (month===-1||year===-1) ? null : {month,year};
}
function applyMes(raw) {
  document.getElementById('hmes').value = raw;
  document.getElementById('cml').textContent = raw||'—';
  const p = parseMes(raw);
  const h = new Date();
  bCal(p?p.month:h.getMonth(), p?p.year:h.getFullYear());
}
window.syncMes = () => {
  const raw = document.getElementById('hmes').value||'';
  document.getElementById('cml').textContent = raw||'—';
  const p = parseMes(raw);
  const h = new Date();
  bCal(p?p.month:h.getMonth(), p?p.year:h.getFullYear());
  scheduleSave(() => set(ref(db,'mes'), raw));
};
onValue(ref(db,'mes'), snap => {
  const v = snap.val()||'';
  if (document.getElementById('hmes').value !== v) applyMes(v);
});

// ── INDICADORES ──
// Apenas v1 (dias sem ocorrências) é editável pelo utilizador
// ic2 e ic3 são placeholders — podem ser usados futuramente
function applyInd(v1) {
  document.getElementById('v1').value = v1;
  document.getElementById('ic1').textContent = v1;
  document.getElementById('mva').textContent = v1;
  // Meta: sem recorde definido por agora
  document.getElementById('mtxt').textContent = 'Dias sem ocorrências: ' + v1;
}
window.saveInd = () => {
  const v1 = +document.getElementById('v1').value||0;
  applyInd(v1);
  scheduleSave(() => set(ref(db,'ind'), {v1}));
};
onValue(ref(db,'ind'), snap => {
  const d = snap.val();
  if (d) applyInd(d.v1||0);
});

// ── CALENDÁRIO ──
let selC=null, calDays=31;
const dm={};

function bCal(month, year) {
  calDays = new Date(year,month+1,0).getDate();
  Object.keys(dm).forEach(k => { if(+k>calDays) delete dm[k]; });
  const firstDay = new Date(year,month,1).getDay();
  document.getElementById('dhr').innerHTML =
    ['DOM','SEG','TER','QUA','QUI','SEX','SÁB'].map(d=>'<div class="dh">'+d+'</div>').join('');
  const g = document.getElementById('dg'); g.innerHTML='';
  for (let i=0;i<firstDay;i++) {
    const e=document.createElement('div');e.className='dc em';g.appendChild(e);
  }
  for (let d=1;d<=calDays;d++) {
    const c=document.createElement('div');c.className='dc';c.id='dc-'+d;
    const n=document.createElement('div');n.className='dn';n.textContent=d;
    const dots=document.createElement('div');dots.className='dd';dots.id='dd-'+d;
    c.appendChild(n);c.appendChild(dots);
    c.onclick=(()=>{const day=d;return()=>hday(day);})();
    g.appendChild(c); rdots(d);
  }
  const total=firstDay+calDays, resto=total%7===0?0:7-(total%7);
  for (let i=0;i<resto;i++) {
    const e=document.createElement('div');e.className='dc em';g.appendChild(e);
  }
  ups();
}

// Mapa de código → classe CSS do ponto
// v=verde, a=amarelo, o=AZUL(PS), p=LARANJA(s/afas), r=vermelho
const dotClass = {v:'dv', a:'da', o:'do2', p:'dp2', r:'dr2'};

function rdots(d) {
  const w=document.getElementById('dd-'+d); if(!w)return;
  const s=dm[d]||new Set(); w.innerHTML='';
  ['v','a','o','p','r'].forEach(c => {
    if (s.has(c)) {
      const dot=document.createElement('div');
      dot.className='dot '+dotClass[c];
      w.appendChild(dot);
    }
  });
}

function hday(d) {
  if (selC) {
    if (!dm[d]) dm[d]=new Set();
    if (dm[d].has(selC)) dm[d].delete(selC); else dm[d].add(selC);
    if (dm[d].size===0) delete dm[d];
    rdots(d); ups(); saveCal();
  } else {
    showDet(d);
  }
}

function showDet(d) {
  const s=dm[d]||new Set();
  const nm={v:'Sem ocorrência',a:'Incidente',o:'Primeiros socorros',p:'Acid. s/ afastamento',r:'Acid. c/ afastamento'};
  const cs={v:'dtv',a:'dta',o:'dto',p:'dtp',r:'dtr'};
  document.getElementById('ddw').innerHTML=
    '<div class="ddet">'+
    '<span class="dclose" onclick="document.getElementById(\'ddw\').innerHTML=\'\'">✕ fechar</span>'+
    '<div class="ddt">Dia '+d+' — marque as ocorrências:</div>'+
    '<div class="ddtg">'+
    ['v','a','o','p','r'].map(c=>
      '<span class="dtag '+cs[c]+' '+(s.has(c)?'on':'')+'" onclick="td('+d+',\''+c+'\')">'+nm[c]+'</span>'
    ).join('')+
    '</div></div>';
}

window.td = (d,c) => {
  if (!dm[d]) dm[d]=new Set();
  if (dm[d].has(c)) dm[d].delete(c); else dm[d].add(c);
  if (dm[d].size===0) delete dm[d];
  rdots(d); ups(); showDet(d); saveCal();
};

window.selc = c => {
  selC = selC===c?null:c;
  document.querySelectorAll('.leg').forEach(el => el.classList.toggle('on',el.dataset.c===selC));
  const L={v:'Sem ocorrência',a:'Incidente',o:'Primeiros socorros',p:'Acid. s/ afastamento',r:'Acid. c/ afastamento'};
  document.getElementById('fh').textContent = selC ?
    'Cor: '+L[selC]+' — clique nos dias para pintar' :
    'Clique num dia sem cor selecionada para editar detalhes';
};

// v=oc1, a=oc2, o=oc3(azul/PS), p=oc5(laranja/s-afas), r=oc4
const ocMap = [['v','1'],['a','2'],['o','3'],['p','5'],['r','4']];

function ups() {
  const cnt={v:0,a:0,o:0,p:0,r:0}; let tot=0;
  Object.values(dm).forEach(s=>{s.forEach(c=>{if(cnt[c]!==undefined)cnt[c]++;});tot++;});
  const mx=Math.max(1,...Object.values(cnt));
  ocMap.forEach(([k,i])=>{
    const v=cnt[k];
    document.getElementById('oc'+i).textContent=v;
    document.getElementById('op'+i).style.width=Math.round(v/mx*100)+'%';
    document.getElementById('od'+i).textContent=v+' registro'+(v!==1?'s':'');
  });
}

function calToObj() {
  const o={};
  Object.entries(dm).forEach(([d,s])=>{o[d]=[...s].join(',');});
  return o;
}
function objToCal(o) {
  Object.keys(dm).forEach(k=>delete dm[k]);
  if(o) Object.entries(o).forEach(([d,v])=>{dm[d]=new Set(v.split(',').filter(Boolean));});
}
function saveCal() { scheduleSave(()=>set(ref(db,'cal'),calToObj())); }

onValue(ref(db,'cal'), snap => {
  objToCal(snap.val());
  for(let d=1;d<=calDays;d++) rdots(d);
  ups();
});

window.rcal = () => {
  Object.keys(dm).forEach(k=>delete dm[k]);
  for(let d=1;d<=calDays;d++) rdots(d);
  document.getElementById('ddw').innerHTML='';
  ups();
  scheduleSave(()=>set(ref(db,'cal'),{}));
};

// ── ATIVIDADES ──
const tipoLabels = {
  quente:'Trabalho a quente', elet:'Trabalho c/ eletricidade',
  altura:'Trabalho em altura', ica:'Içamento de carga',
  espc:'Espaço confinado', outr:'Outro'
};
const tipoTagClass = {
  quente:'atag-quente', elet:'atag-elet', altura:'atag-altura',
  ica:'atag-ica', espc:'atag-espc', outr:'atag-outr'
};

window.toggleTipo = btn => btn.classList.toggle('on');
window.toggleTec  = btn => btn.classList.toggle('on');

window.addAtiv = () => {
  const pt   = document.getElementById('f-pt').value.trim();
  const apr  = document.getElementById('f-apr').value.trim();
  const desc = document.getElementById('f-desc').value.trim();
  const data = document.getElementById('f-data').value;
  const fim  = document.getElementById('f-fim').value;
  const erro = document.getElementById('f-erro');
  const tipos = [...document.querySelectorAll('.tipo-btn.on')].map(b=>b.dataset.tipo);
  const tecs  = [...document.querySelectorAll('.tec-btn.on')].map(b=>b.dataset.tec);
  if(!pt&&!apr) { erro.textContent='Informe ao menos o número da PT ou APR.'; return; }
  if(!desc)     { erro.textContent='Informe a descrição.'; return; }
  if(!tipos.length) { erro.textContent='Selecione ao menos um tipo.'; return; }
  if(!tecs.length)  { erro.textContent='Selecione ao menos um técnico.'; return; }
  if(!data)     { erro.textContent='Informe a data de início.'; return; }
  erro.textContent='';
  const id = Date.now();
  setSyncStatus('saving');
  set(ref(db,'ativ/'+id), {id,pt,apr,desc,tipos,tecs,data,fim}).then(()=>setSyncStatus('ok'));
  ['f-pt','f-apr','f-desc','f-fim'].forEach(fid=>document.getElementById(fid).value='');
  document.querySelectorAll('.tipo-btn.on,.tec-btn.on').forEach(b=>b.classList.remove('on'));
  const h=new Date();
  document.getElementById('f-data').value =
    h.getFullYear()+'-'+String(h.getMonth()+1).padStart(2,'0')+'-'+String(h.getDate()).padStart(2,'0');
};

window.delAtiv = id => {
  setSyncStatus('saving');
  remove(ref(db,'ativ/'+id)).then(()=>setSyncStatus('ok'));
};
window.limparAtiv = () => {
  setSyncStatus('saving');
  set(ref(db,'ativ'),{}).then(()=>setSyncStatus('ok'));
};

function fmtData(d) {
  if(!d) return '—';
  const [y,m,day]=d.split('-');
  return day+'/'+m+'/'+y;
}

onValue(ref(db,'ativ'), snap => {
  const data  = snap.val()||{};
  const lista = Object.values(data).sort((a,b)=>b.id-a.id);
  document.getElementById('res-pt').textContent   = lista.filter(a=>a.pt).length;
  document.getElementById('res-apr').textContent  = lista.filter(a=>a.apr).length;
  document.getElementById('res-ativ').textContent = lista.length;
  const el = document.getElementById('ativ-lista');
  if(!lista.length) {
    el.innerHTML='<div class="lista-vazia">Nenhuma atividade registrada ainda.</div>';
    return;
  }
  el.innerHTML = lista.map(a=>`
    <div class="ativ-card">
      <div class="ativ-card-top">
        <div class="ativ-tipo-tags">
          ${(a.tipos||[]).map(t=>`<span class="atag ${tipoTagClass[t]}">${tipoLabels[t]}</span>`).join('')}
        </div>
        <button class="ativ-del" onclick="delAtiv(${a.id})" title="Remover">✕</button>
      </div>
      <div style="font-size:13px;font-weight:600;color:var(--tv);">${a.desc}</div>
      <div class="ativ-nums">
        ${a.pt  ? `<div class="ativ-num-item"><div class="ativ-num-val">${a.pt}</div><div class="ativ-num-lbl">Nº PT</div></div>`  : ''}
        ${a.apr ? `<div class="ativ-num-item"><div class="ativ-num-val">${a.apr}</div><div class="ativ-num-lbl">Nº APR</div></div>` : ''}
      </div>
      <div class="ativ-info-row">
        <div class="ativ-info-item"><span class="ativ-info-dot"></span><span>Início: ${fmtData(a.data)}</span></div>
        ${a.fim ? `<div class="ativ-info-item"><span class="ativ-info-dot" style="background:var(--ts)"></span><span>Término: ${fmtData(a.fim)}</span></div>` : ''}
      </div>
      <div class="ativ-tec-tags">
        ${(a.tecs||[]).map(t=>`<span class="ttag">${t}</span>`).join('')}
      </div>
    </div>`).join('');
});

// ── INICIALIZAÇÃO ──
(()=>{
  const h = new Date();
  // Data de hoje no campo de início
  document.getElementById('f-data').value =
    h.getFullYear()+'-'+String(h.getMonth()+1).padStart(2,'0')+'-'+String(h.getDate()).padStart(2,'0');
  // Calendário com mês atual
  const nomes=['Janeiro','Fevereiro','Março','Abril','Maio','Junho',
               'Julho','Agosto','Setembro','Outubro','Novembro','Dezembro'];
  const mesAtual = nomes[h.getMonth()]+' '+h.getFullYear();
  document.getElementById('hmes').value = mesAtual;
  document.getElementById('cml').textContent = mesAtual;
  bCal(h.getMonth(), h.getFullYear());
  setSyncStatus('ok');
})();
</script>
</body>
</html>
