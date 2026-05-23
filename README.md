cat > /tmp/part1.html << 'HTMLEOF'
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>RTS COMMAND CENTER — 1949</title>
<script src="env-config.js"></script>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --bg:#090b08;--bg2:#0e100d;--bg3:#131613;--bg4:#181c17;
  --panel:#0c0f0b;--b1:#1a2019;--b2:#253024;
  --g1:#2d6630;--g2:#3d8a40;--g3:#6bbf6e;
  --a1:#8a5a08;--a2:#c08010;--a3:#e8b030;
  --r1:#6a1010;--r2:#a82020;--r3:#d84040;
  --bl1:#0d2840;--bl2:#1a5080;
  --cy1:#0a4040;--cy2:#208080;
  --pu1:#3a1060;--pu2:#8050c0;
  --tx1:#bfcfbc;--tx2:#7a9a78;--tx3:#3a5038;
  --gold:#c8a020;
}
html,body{height:100%;overflow:hidden;background:var(--bg);color:var(--tx1);font-family:'Segoe UI',system-ui,sans-serif;font-size:13px;}
::-webkit-scrollbar{width:4px;height:4px;}
::-webkit-scrollbar-track{background:var(--bg);}
::-webkit-scrollbar-thumb{background:var(--b2);}

/* ── TYPOGRAPHY ── */
.mono{font-family:'Courier New',monospace;}
.lbl{font-size:8px;letter-spacing:2px;color:var(--tx3);text-transform:uppercase;display:block;margin-bottom:3px;}

/* ── SCREEN SYSTEM ── */
.screen{display:none;width:100%;height:100%;}
.screen.active{display:flex;flex-direction:column;}

/* ── LOGIN ── */
#sc-login{align-items:center;justify-content:center;background:radial-gradient(ellipse at 30% 40%,rgba(45,102,48,.09),transparent 60%),var(--bg);}
.lbox{background:var(--bg2);border:1px solid var(--b2);padding:38px 40px;width:380px;box-shadow:0 24px 70px rgba(0,0,0,.97);}
.lbox-logo{font-size:9px;letter-spacing:6px;color:var(--g2);text-align:center;margin-bottom:5px;}
.lbox-title{font-size:20px;font-weight:700;letter-spacing:3px;text-align:center;margin-bottom:3px;}
.lbox-sub{font-size:8px;letter-spacing:2px;color:var(--tx3);text-align:center;margin-bottom:22px;}
.ltabs{display:flex;border:1px solid var(--b2);margin-bottom:16px;}
.ltab{flex:1;padding:8px;text-align:center;font-size:9px;letter-spacing:1.5px;cursor:pointer;color:var(--tx3);background:none;border:none;transition:all .15s;}
.ltab.active{background:var(--g1);color:#fff;}
.lerr{font-size:10px;color:var(--r3);text-align:center;margin-top:6px;min-height:14px;}

/* ── FORMS ── */
input,select,textarea{background:var(--bg);border:1px solid var(--b2);color:var(--tx1);font-family:inherit;font-size:12px;padding:7px 10px;width:100%;outline:none;transition:border-color .2s;}
input:focus,select:focus,textarea:focus{border-color:var(--g2);}
select option{background:var(--bg2);}
.fg{margin-bottom:10px;}
.fg:last-of-type{margin-bottom:0;}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.frow3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;}

/* ── BUTTONS ── */
.btn{display:inline-flex;align-items:center;justify-content:center;gap:5px;padding:7px 14px;border:1px solid var(--b2);background:var(--bg3);color:var(--tx2);font-size:11px;cursor:pointer;transition:all .15s;white-space:nowrap;font-family:inherit;}
.btn:hover{border-color:var(--tx3);color:var(--tx1);}
.btn:disabled{opacity:.35;cursor:not-allowed;}
.btn.g{background:var(--g1);border-color:var(--g1);color:#fff;}
.btn.g:hover{background:#225228;}
.btn.r{background:var(--r1);border-color:var(--r1);color:#fff;}
.btn.r:hover{background:#500a0a;}
.btn.a{background:rgba(138,90,8,.18);border-color:var(--a2);color:var(--a3);}
.btn.a:hover{background:rgba(138,90,8,.3);}
.btn.ghost{background:transparent;border-color:var(--b2);color:var(--tx3);}
.btn.ghost:hover{border-color:var(--tx3);color:var(--tx1);}
.btn.sm{padding:4px 9px;font-size:10px;}
.btn.xs{padding:2px 6px;font-size:9px;}
.btn-red-big{padding:11px 22px;background:var(--r2);border:2px solid var(--r3);color:#fff;font-size:14px;font-weight:700;letter-spacing:2px;cursor:pointer;transition:all .2s;font-family:inherit;}
.btn-red-big:hover{background:#8a1818;box-shadow:0 0 18px rgba(168,32,32,.5);}
.brow{display:flex;gap:6px;flex-wrap:wrap;}

/* ── PANELS ── */
.panel{background:var(--panel);border:1px solid var(--b1);padding:12px;position:relative;}
.panel::after{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--b2),transparent);}
.ph{display:flex;align-items:center;justify-content:space-between;margin-bottom:9px;padding-bottom:7px;border-bottom:1px solid var(--b1);}
.pt{font-size:8px;letter-spacing:2px;color:var(--tx3);text-transform:uppercase;display:flex;align-items:center;gap:5px;}
.pt::before{content:'';width:3px;height:3px;border-radius:50%;background:var(--g2);box-shadow:0 0 5px var(--g2);display:inline-block;}
.pt.a::before{background:var(--a2);box-shadow:0 0 5px var(--a2);}
.pt.r::before{background:var(--r3);box-shadow:0 0 5px var(--r3);}

/* ── GRIDS ── */
.g2{display:grid;grid-template-columns:1fr 1fr;gap:12px;}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;}
.sp2{grid-column:span 2;}
.sp3{grid-column:span 3;}
.sp4{grid-column:span 4;}

/* ── BADGES ── */
.badge{display:inline-block;padding:2px 6px;font-size:8px;letter-spacing:1px;text-transform:uppercase;border:1px solid;}
.bc{color:#ef5350;border-color:#4a1010;background:rgba(106,16,16,.15);}
.bcap{color:#42a5f5;border-color:#0d2840;background:rgba(13,40,64,.2);}
.bf{color:#bdbdbd;border-color:#303030;background:rgba(40,40,40,.25);}
.bm{color:#ffb300;border-color:#4a3000;background:rgba(138,90,8,.15);}

/* ── STAT ROW ── */
.sr{display:flex;justify-content:space-between;align-items:center;padding:4px 0;border-bottom:1px solid var(--b1);font-size:11px;}
.sr:last-child{border-bottom:none;}

/* ── MODAL ── */
.moverlay{display:none;position:fixed;inset:0;z-index:900;background:rgba(0,0,0,.78);backdrop-filter:blur(2px);align-items:center;justify-content:center;}
.moverlay.open{display:flex;}
.modal{background:var(--bg2);border:1px solid var(--b2);padding:18px;min-width:340px;max-width:620px;width:93%;max-height:90vh;overflow-y:auto;box-shadow:0 24px 70px rgba(0,0,0,.97);}
.modal-title{font-size:13px;font-weight:600;letter-spacing:1px;margin-bottom:13px;padding-bottom:9px;border-bottom:1px solid var(--b1);}
.modal-foot{display:flex;gap:7px;justify-content:flex-end;margin-top:13px;padding-top:10px;border-top:1px solid var(--b1);}

/* ── NOTIF ── */
.notif{position:fixed;top:54px;right:12px;z-index:9999;padding:8px 13px;font-size:11px;border:1px solid var(--b2);background:var(--bg3);box-shadow:0 4px 20px rgba(0,0,0,.8);animation:sldin .2s ease-out;max-width:300px;pointer-events:none;}
.notif.ok{border-color:var(--g1);color:var(--g3);}
.notif.err{border-color:var(--r1);color:var(--r3);}
.notif.info{border-color:var(--a1);color:var(--a3);}
@keyframes sldin{from{opacity:0;transform:translateX(14px);}to{opacity:1;transform:translateX(0);}}

/* ── TABLES ── */
.tbl{width:100%;border-collapse:collapse;font-size:10px;}
.tbl th{text-align:left;padding:5px 8px;font-size:8px;letter-spacing:1.5px;color:var(--tx3);border-bottom:1px solid var(--b2);background:var(--bg2);text-transform:uppercase;}
.tbl td{padding:5px 8px;border-bottom:1px solid var(--b1);vertical-align:middle;}
.tbl tr:last-child td{border-bottom:none;}
.tbl tr:hover td{background:rgba(255,255,255,.018);}

/* ── TOOLTIP ── */
#global-tip{position:fixed;z-index:9998;background:var(--bg2);border:1px solid var(--a2);padding:8px 12px;font-size:10px;pointer-events:none;display:none;box-shadow:3px 3px 12px rgba(0,0,0,.9);max-width:260px;line-height:1.6;}

/* ─────────────────────────────────────────────
   APP HEADER
───────────────────────────────────────────── */
.app-hdr{height:46px;display:flex;align-items:center;background:var(--bg2);border-bottom:1px solid var(--b2);padding:0 13px;gap:13px;flex-shrink:0;box-shadow:0 2px 12px rgba(0,0,0,.6);}
.app-logo{font-size:13px;font-weight:700;letter-spacing:3px;color:var(--g3);white-space:nowrap;}
.app-logo span{color:var(--tx3);}
.hsep{width:1px;height:26px;background:var(--b2);}
.hitem{display:flex;flex-direction:column;align-items:center;}
.hitem .lbl{margin:0;}
.hval{font-size:11px;font-weight:700;color:var(--a2);}
.rts-clock{font-family:'Courier New',monospace;font-size:10px;color:var(--g3);letter-spacing:.8px;}
.huser{margin-left:auto;display:flex;align-items:center;gap:7px;}
.uav{width:26px;height:26px;border-radius:50%;border:2px solid;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0;}
.admin-badge{font-size:7px;letter-spacing:2px;padding:2px 7px;background:rgba(138,90,8,.2);border:1px solid var(--a2);color:var(--a3);}

/* ─────────────────────────────────────────────
   APP NAV
───────────────────────────────────────────── */
.app-nav{display:flex;background:var(--bg2);border-bottom:1px solid var(--b2);padding:0 13px;flex-shrink:0;overflow-x:auto;scrollbar-width:none;}
.app-nav::-webkit-scrollbar{display:none;}
.ntab{font-size:9px;letter-spacing:1.5px;padding:8px 14px;cursor:pointer;color:var(--tx3);background:none;border:none;border-bottom:2px solid transparent;outline:none;transition:all .15s;white-space:nowrap;text-transform:uppercase;}
.ntab:hover{color:var(--tx2);}
.ntab.active{color:var(--g3);border-bottom-color:var(--g2);}
.ntab.adm{color:var(--a2);}
.ntab.adm.active{color:var(--a3);border-bottom-color:var(--a2);}

/* ─────────────────────────────────────────────
   PAGES
───────────────────────────────────────────── */
.app-pages{flex:1;overflow:hidden;position:relative;}
.pg{display:none;height:100%;overflow:hidden;}
.pg.active{display:flex;flex-direction:column;}
.pscroll{flex:1;overflow-y:auto;padding:13px;}

/* ─────────────────────────────────────────────
   MAP PAGE
───────────────────────────────────────────── */
#pg-map{flex-direction:row;}
.map-wrap{flex:1;position:relative;overflow:hidden;background:#020a03;cursor:grab;user-select:none;}
.map-wrap.grabbing{cursor:grabbing;}
.map-wrap.placing{cursor:crosshair;}
#map-img{position:absolute;transform-origin:0 0;filter:saturate(.68) brightness(.72) contrast(1.12);pointer-events:none;user-select:none;}
.map-grid-svg{position:absolute;inset:0;pointer-events:none;}
.map-tile-layer,.map-unit-layer,.map-battle-layer{position:absolute;inset:0;}
.map-ctrl{position:absolute;top:9px;left:9px;display:flex;flex-direction:column;gap:4px;z-index:20;}
.mzb{width:25px;height:25px;background:rgba(9,11,8,.92);border:1px solid var(--b2);color:var(--tx2);font-size:13px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .15s;}
.mzb:hover{border-color:var(--g2);color:var(--g3);}
.map-info{position:absolute;bottom:5px;left:9px;font-size:8px;letter-spacing:1px;color:rgba(107,191,110,.3);}

/* tile marker */
.tm{position:absolute;transform:translate(-50%,-50%);pointer-events:auto;z-index:5;cursor:pointer;text-align:center;}
.tm-i{width:22px;height:22px;border:2px solid;display:flex;align-items:center;justify-content:center;font-size:10px;background:rgba(2,10,3,.88);transition:transform .15s;}
.tm:hover .tm-i{transform:scale(1.3);}
.tm-l{font-size:7px;text-align:center;margin-top:1px;white-space:nowrap;text-shadow:0 1px 4px #000;max-width:64px;overflow:hidden;text-overflow:ellipsis;}

/* unit marker */
.um{position:absolute;transform:translate(-50%,-50%);pointer-events:auto;z-index:8;cursor:pointer;text-align:center;transition:left 1.2s ease,top 1.2s ease;}
.um-s{width:26px;height:17px;border:2px solid;display:flex;align-items:center;justify-content:center;font-size:7px;font-weight:700;font-family:'Courier New',monospace;background:rgba(0,0,0,.92);}
.um-l{font-size:7px;text-align:center;white-space:nowrap;margin-top:1px;}
.um-c{font-size:7px;text-align:center;color:rgba(180,180,180,.7);}
.um.moving .um-s{border-style:dashed;}
.um.sel .um-s{box-shadow:0 0 8px currentColor;}
.fuel-ring{width:30px;height:30px;border-radius:50%;border:1px solid rgba(255,183,48,.4);position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);pointer-events:none;}

/* battle icon */
.battle-icon{position:absolute;transform:translate(-50%,-50%);z-index:15;pointer-events:auto;cursor:pointer;text-align:center;}
.bi-inner{background:rgba(106,16,16,.94);border:2px solid var(--r3);padding:4px 9px;font-size:8px;font-weight:700;letter-spacing:1px;color:var(--r3);white-space:nowrap;animation:bpulse 1.5s infinite;}
@keyframes bpulse{0%,100%{opacity:1;}50%{opacity:.55;}}

/* map sidebar */
.map-sb{width:248px;flex-shrink:0;border-left:1px solid var(--b2);background:var(--bg2);overflow-y:auto;display:flex;flex-direction:column;}
.msb-sec{padding:9px;border-bottom:1px solid var(--b1);}
.msb-t{font-size:8px;letter-spacing:2px;color:var(--tx3);margin-bottom:7px;text-transform:uppercase;}
.fli{display:flex;align-items:center;gap:5px;padding:5px 6px;border:1px solid var(--b1);margin-bottom:3px;background:var(--bg);cursor:pointer;transition:all .12s;}
.fli:hover{border-color:var(--b2);}
.fli-bar{width:3px;align-self:stretch;flex-shrink:0;}
.fli-dot{width:9px;height:9px;border-radius:50%;flex-shrink:0;}
.fli-name{flex:1;font-size:9px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;}

/* movement panel */
.move-panel{background:rgba(10,64,40,.15);border:1px solid var(--cy1);padding:9px;margin:9px;}
.mp-title{font-size:8px;letter-spacing:2px;color:var(--cy2);margin-bottom:7px;}

/* ─────────────────────────────────────────────
   OPS PAGE
───────────────────────────────────────────── */
#pg-ops{flex-direction:row;}
.ops-roster{width:192px;flex-shrink:0;border-right:1px solid var(--b2);background:var(--bg2);overflow-y:auto;padding:8px;}
.ops-center{flex:1;display:flex;flex-direction:column;overflow:hidden;}
.ops-tb{display:flex;align-items:stretch;background:var(--bg2);border-bottom:1px solid var(--b2);flex-shrink:0;overflow-x:auto;scrollbar-width:none;}
.ops-tb::-webkit-scrollbar{display:none;}
.otb{font-size:9px;letter-spacing:1px;padding:7px 11px;border:none;border-right:1px solid var(--b1);background:transparent;color:var(--tx3);cursor:pointer;transition:all .12s;white-space:nowrap;text-transform:uppercase;font-family:inherit;}
.otb:hover{color:var(--tx2);background:rgba(255,255,255,.02);}
.otb.active{color:var(--a3);background:rgba(138,90,8,.08);box-shadow:inset 0 -2px 0 var(--a2);}
.tl-bar{display:flex;align-items:center;gap:7px;padding:4px 9px;background:rgba(0,0,0,.32);border-bottom:1px solid var(--b1);flex-shrink:0;}
.tl-track{flex:1;height:4px;background:var(--bg);border:1px solid var(--b2);position:relative;cursor:pointer;border-radius:2px;}
.tl-fill{height:100%;background:var(--a2);border-radius:2px;transition:width .3s;}
.tl-dot{position:absolute;top:50%;transform:translate(-50%,-50%);width:9px;height:9px;border-radius:50%;border:1.5px solid var(--bg2);cursor:pointer;transition:transform .1s;}
.tl-dot:hover{transform:translate(-50%,-50%) scale(1.35);}
.tlc{width:19px;height:19px;border:1px solid var(--b2);background:var(--bg);color:var(--tx2);cursor:pointer;font-size:10px;display:flex;align-items:center;justify-content:center;border-radius:1px;}
#ops-canvas{flex:1;display:block;cursor:crosshair;}
.ops-right{width:238px;flex-shrink:0;border-left:1px solid var(--b2);background:var(--bg2);overflow-y:auto;padding:9px;display:flex;flex-direction:column;gap:9px;}

/* unit roster item */
.uri{padding:5px 7px;background:var(--bg);border:1px solid var(--b1);cursor:grab;margin-bottom:3px;transition:border-color .12s;}
.uri:hover{border-color:var(--b2);}
.uri:active{cursor:grabbing;opacity:.45;}
.uri-top{display:flex;align-items:center;gap:5px;margin-bottom:3px;}
.nato{width:21px;height:13px;border:1.5px solid;display:flex;align-items:center;justify-content:center;font-size:6px;font-weight:700;font-family:'Courier New',monospace;flex-shrink:0;}
.nl{border-color:var(--g1);color:var(--g3);}
.nm{border-color:var(--a1);color:var(--a2);}
.nh{border-color:var(--r1);color:var(--r3);}
.ns{border-color:var(--pu1);color:var(--pu2);}
.nspg{border-color:var(--cy1);color:var(--cy2);}
.nu{border-color:#37474f;color:#8aaa86;}
.uri-cnts{display:flex;align-items:center;gap:3px;flex-wrap:wrap;}
.cg{display:flex;align-items:center;gap:2px;}
.cntb{width:12px;height:12px;border:1px solid var(--b2);background:var(--bg2);color:var(--tx2);cursor:pointer;font-size:10px;display:flex;align-items:center;justify-content:center;}
.cntn{font-size:9px;min-width:14px;text-align:center;font-weight:600;}

/* placed unit on canvas */
.pu{position:absolute;user-select:none;cursor:move;z-index:10;}
.pu-s{width:23px;height:15px;border:1.5px solid;display:flex;align-items:center;justify-content:center;font-size:6px;font-weight:700;font-family:'Courier New',monospace;background:rgba(0,0,0,.92);}
.pu-l{font-size:7px;text-align:center;margin-top:1px;white-space:nowrap;}
.pu.sa .pu-s{border-color:var(--g1);color:var(--g3);}
.pu.sa .pu-l{color:var(--g3);}
.pu.sd .pu-s{border-color:var(--r1);color:var(--r3);}
.pu.sd .pu-l{color:var(--r3);}

/* ─────────────────────────────────────────────
   TECH TREE
───────────────────────────────────────────── */
.tt-tabs{display:flex;background:var(--bg2);border-bottom:1px solid var(--b2);padding:0 13px;flex-shrink:0;}
.tt-tab{font-size:9px;letter-spacing:1.5px;padding:8px 15px;cursor:pointer;color:var(--tx3);background:none;border:none;border-bottom:2px solid transparent;outline:none;transition:all .15s;text-transform:uppercase;}
.tt-tab.active{border-bottom-color:currentColor;}
.tt-content{flex:1;overflow-y:auto;padding:13px;}
.tt-era{margin-bottom:18px;}
.tt-era-title{font-size:9px;letter-spacing:3px;color:var(--tx3);border-bottom:1px solid var(--b2);padding-bottom:6px;margin-bottom:10px;text-transform:uppercase;}
.tech-cards{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:8px;}
.tech-card{background:var(--bg);border:1px solid var(--b2);padding:10px;position:relative;transition:border-color .15s;}
.tech-card:hover{border-color:var(--b2);}
.tech-card.unlocked{border-color:var(--g1);background:rgba(45,102,48,.06);}
.tc-top{display:flex;align-items:flex-start;gap:6px;margin-bottom:5px;}
.tc-name{font-size:11px;font-weight:600;flex:1;line-height:1.3;}
.tc-tier{font-size:7px;letter-spacing:1px;padding:1px 5px;border:1px solid;text-transform:uppercase;flex-shrink:0;}
.t1{color:#66bb6a;border-color:var(--g1);}
.t2{color:#42a5f5;border-color:var(--bl1);}
.t3{color:#ffb300;border-color:var(--a1);}
.t4{color:#ef5350;border-color:var(--r1);}
.tc-cost{font-size:9px;color:var(--tx3);margin-bottom:4px;}
.tc-desc{font-size:9px;color:var(--tx2);line-height:1.65;}
.tc-origin{font-size:8px;color:var(--a2);margin-top:4px;font-style:italic;}
.tc-special-btn{display:flex;align-items:center;gap:4px;font-size:8px;color:var(--a2);margin-top:5px;cursor:pointer;background:none;border:none;padding:0;font-family:inherit;}
.tc-special-btn:hover{color:var(--a3);}
.tc-special-body{display:none;font-size:9px;color:var(--a3);margin-top:5px;padding:5px 7px;background:rgba(138,90,8,.1);border-left:2px solid var(--a1);line-height:1.7;}
.tc-special-body.open{display:block;}
.tc-actions{display:flex;gap:5px;margin-top:8px;}

/* admin tech editor */
.te-card{background:var(--bg);border:1px solid var(--b2);padding:10px;margin-bottom:8px;position:relative;}
.te-card-hdr{display:flex;align-items:center;gap:7px;margin-bottom:8px;}
.te-drag{cursor:grab;color:var(--tx3);font-size:16px;user-select:none;}
.te-del{margin-left:auto;background:none;border:none;color:var(--r2);cursor:pointer;font-size:15px;padding:0;}

/* gun column presets */
.gun-columns{display:grid;grid-template-columns:repeat(5,1fr);gap:8px;margin-top:10px;}
.gun-col{background:var(--bg2);border:1px solid var(--b1);padding:8px;}
.gun-col-title{font-size:8px;letter-spacing:1.5px;color:var(--tx3);margin-bottom:6px;text-transform:uppercase;border-bottom:1px solid var(--b1);padding-bottom:4px;}
.gun-item{padding:5px 6px;border:1px solid var(--b1);margin-bottom:4px;font-size:9px;cursor:pointer;transition:border-color .12s;}
.gun-item:hover{border-color:var(--b2);}

/* ─────────────────────────────────────────────
   POLITICS
───────────────────────────────────────────── */
#pg-politics{flex-direction:row;}
.pol-feed{flex:1;overflow-y:auto;padding:13px;display:flex;flex-direction:column;gap:8px;}
.pol-post{padding:10px 12px;border:1px solid var(--b1);background:var(--bg2);}
.pol-post.ann{border-left:3px solid var(--a2);background:rgba(138,90,8,.05);}
.pol-post.war{border-left:3px solid var(--r2);}
.pol-post.diplomatic{border-left:3px solid var(--bl2);}
.pol-post.lore{border-left:3px solid var(--g2);}
.pol-hdr{display:flex;align-items:center;gap:7px;margin-bottom:6px;}
.pol-body{font-size:11px;line-height:1.75;}
.pol-sb{width:260px;flex-shrink:0;border-left:1px solid var(--b2);background:var(--bg2);overflow-y:auto;padding:11px;}

/* ─────────────────────────────────────────────
   AI
───────────────────────────────────────────── */
#pg-ai{flex-direction:row;}
.ai-chat{flex:1;display:flex;flex-direction:column;overflow:hidden;}
.ai-hdr{padding:8px 12px;border-bottom:1px solid var(--b2);background:var(--bg2);display:flex;align-items:center;gap:9px;flex-shrink:0;}
.ai-dot{width:7px;height:7px;background:var(--g3);border-radius:50%;animation:apulse 2s infinite;}
@keyframes apulse{0%,100%{box-shadow:0 0 4px rgba(107,191,110,.3);}50%{box-shadow:0 0 10px rgba(107,191,110,.7);}}
.ai-msgs{flex:1;overflow-y:auto;padding:11px;display:flex;flex-direction:column;gap:8px;}
.cmsg{max-width:87%;}
.cmsg.user{align-self:flex-end;}
.cmsg.ai{align-self:flex-start;}
.cmsg-lbl{font-size:7px;letter-spacing:2px;color:var(--tx3);margin-bottom:2px;text-transform:uppercase;}
.cmsg-bub{padding:7px 11px;font-size:10px;line-height:1.75;border:1px solid var(--b1);}
.cmsg.user .cmsg-bub{background:rgba(45,102,48,.12);border-color:var(--g1);}
.cmsg.ai .cmsg-bub{background:var(--bg2);}
.typing{display:none;align-self:flex-start;}
.typing.show{display:flex;}
.typing-b{padding:7px 11px;background:var(--bg2);border:1px solid var(--b1);display:flex;gap:4px;align-items:center;}
.td{width:5px;height:5px;background:var(--tx3);border-radius:50%;animation:tda 1.2s infinite;}
.td:nth-child(2){animation-delay:.2s;}.td:nth-child(3){animation-delay:.4s;}
@keyframes tda{0%,60%,100%{opacity:.3;transform:translateY(0);}30%{opacity:1;transform:translateY(-3px);}}
.ai-inp{padding:8px 11px;border-top:1px solid var(--b2);background:var(--bg2);display:flex;gap:6px;flex-shrink:0;}
#chat-input{flex:1;resize:none;height:38px;background:var(--bg);border:1px solid var(--b2);color:var(--tx1);font-size:10px;padding:6px 9px;outline:none;font-family:inherit;}
#chat-input:focus{border-color:var(--g2);}
#send-btn{font-size:10px;letter-spacing:1px;padding:0 12px;background:rgba(45,102,48,.18);border:1px solid var(--g1);color:var(--g3);cursor:pointer;flex-shrink:0;font-family:inherit;}
.ai-sb{width:240px;flex-shrink:0;border-left:1px solid var(--b2);background:var(--bg2);overflow-y:auto;padding:9px;}
.qbtn{width:100%;text-align:left;padding:5px 7px;font-size:9px;background:var(--bg);border:1px solid var(--b1);color:var(--tx3);cursor:pointer;margin-bottom:3px;font-family:inherit;transition:all .12s;line-height:1.4;}
.qbtn:hover{border-color:var(--b2);color:var(--tx2);}

/* ─────────────────────────────────────────────
   ADMIN
───────────────────────────────────────────── */
.adm-layout{display:grid;grid-template-columns:170px 1fr;height:100%;overflow:hidden;}
.adm-nav{background:var(--bg);border-right:1px solid var(--b2);overflow-y:auto;}
.adm-ni{display:block;width:100%;text-align:left;padding:8px 13px;font-size:9px;letter-spacing:1px;cursor:pointer;color:var(--tx3);background:transparent;border:none;border-left:2px solid transparent;transition:all .12s;font-family:inherit;text-transform:uppercase;}
.adm-ni:hover{color:var(--tx2);background:var(--bg2);}
.adm-ni.active{color:var(--a3);background:var(--bg2);border-left-color:var(--a2);}
.adm-content{overflow-y:auto;padding:13px;}
.adm-sec{display:none;}
.adm-sec.active{display:block;}

/* morale */
.morale-big{font-size:48px;font-weight:700;text-align:center;line-height:1;margin:6px 0;}
.mbar-t{height:5px;background:var(--bg);overflow:hidden;border:1px solid var(--b1);border-radius:2px;}
.mbar-f{height:100%;transition:width .35s,background .35s;border-radius:2px;}
.mfx{max-height:170px;overflow-y:auto;display:flex;flex-direction:column;gap:3px;margin-top:7px;}
.mfxr{padding:3px 7px;font-size:9px;border-left:2px solid var(--b1);}
.mfxr.neg{border-left-color:var(--r2);color:var(--tx2);}
.mfxr.pos{border-left-color:var(--g1);color:var(--g3);}

/* fuel badge */
.fuel-badge{display:inline-flex;align-items:center;gap:3px;padding:1px 6px;font-size:8px;border:1px solid #37474f;color:#90a4ae;background:rgba(55,71,79,.15);}

@media(max-width:820px){#pg-map,#pg-ops,#pg-ai,#pg-politics{flex-direction:column;}.map-sb,.ops-roster,.ops-right,.ai-sb,.pol-sb{width:100%;max-height:180px;}.adm-layout{grid-template-columns:1fr;}}
</style>
</head>
<body>
<div id="global-tip"></div>
<div id="notif-container" style="position:fixed;top:54px;right:12px;z-index:9999;display:flex;flex-direction:column;gap:5px;"></div>

<!-- MODALS -->
<div class="moverlay" id="mod-tile"><div class="modal" id="mod-tile-c"></div></div>
<div class="moverlay" id="mod-unit"><div class="modal" id="mod-unit-c"></div></div>
<div class="moverlay" id="mod-move"><div class="modal" id="mod-move-c"></div></div>
<div class="moverlay" id="mod-battle"><div class="modal" id="mod-battle-c"></div></div>
<div class="moverlay" id="mod-player"><div class="modal" id="mod-player-c"></div></div>
<div class="moverlay" id="mod-tech-edit"><div class="modal" id="mod-tech-edit-c" style="max-width:720px;width:96%;"></div></div>
<div class="moverlay" id="mod-div"><div class="modal" id="mod-div-c"></div></div>

<!-- LOGIN -->
<div class="screen active" id="sc-login">
  <div class="lbox">
    <div class="lbox-logo">RTS COMMAND CENTER</div>
    <div class="lbox-title">OPERATIONS — 1949</div>
    <div class="lbox-sub">CLASSIFIED ACCESS ONLY</div>
    <div class="ltabs">
      <button class="ltab active" id="ltab-in" onclick="switchLTab('in')">LOG IN</button>
      <button class="ltab" id="ltab-reg" onclick="switchLTab('reg')">REGISTER</button>
    </div>
    <div id="lf-in">
      <div class="fg"><span class="lbl">Username</span><input id="l-u" type="text" placeholder="callsign" autocomplete="username"></div>
      <div class="fg"><span class="lbl">Password</span><input id="l-p" type="password" placeholder="••••••••" onkeydown="if(event.key==='Enter')doLogin()"></div>
      <button class="btn g" style="width:100%;margin-top:4px;" onclick="doLogin()">ENTER COMMAND CENTER</button>
      <div class="lerr" id="l-err"></div>
    </div>
    <div id="lf-reg" style="display:none">
      <div class="fg"><span class="lbl">Username (callsign)</span><input id="r-u" placeholder="your_callsign"></div>
      <div class="fg"><span class="lbl">Password</span><input id="r-p" type="password" placeholder="min 4 chars"></div>
      <div class="fg"><span class="lbl">Preferred Nation</span>
        <select id="r-n">
          <option value="">— No preference —</option>
          <option value="serbia">Kingdom of Serbia</option><option value="yugoslavia">Greater Yugoslav Empire</option>
          <option value="ukraine">Kingdom of Ukraine</option><option value="japan">Japan (Allied Occ. Zone)</option>
          <option value="ussr">Reformed USSR</option><option value="china">China</option>
          <option value="nkorea">North Korea (DPRK)</option><option value="morocco">Socialist Rep. Morocco</option>
          <option value="usa">USA</option><option value="egypt">Egypt (Islamist)</option>
          <option value="burgundy">Burgundy</option><option value="rome">Roman Empire</option>
          <option value="poland">Third Rep. Poland</option><option value="israel">Israel</option>
          <option value="ussn">USSN</option><option value="baltic">Baltic Protection Force</option>
          <option value="norway">Norway</option><option value="phuceld">Former Rep. PhúcEld</option>
        </select>
      </div>
      <button class="btn g" style="width:100%;margin-top:4px;" onclick="doRegister()">CREATE ACCOUNT</button>
      <div class="lerr" id="r-err"></div>
    </div>
    <div style="margin-top:13px;font-size:8px;color:var(--tx3);text-align:center">Sessions Wed &amp; Sat · July 1949 · Sprocket RTS</div>
  </div>
</div>

<!-- MAIN APP -->
<div class="screen" id="sc-app">
  <div class="app-hdr" id="app-hdr"></div>
  <div class="app-nav" id="app-nav"></div>
  <div class="app-pages" id="app-pages">
    <div class="pg active" id="pg-map" style="flex-direction:row;"></div>
    <div class="pg" id="pg-ops" style="flex-direction:row;"></div>
    <div class="pg" id="pg-vehicles" style="flex-direction:column;"></div>
    <div class="pg" id="pg-techtree" style="flex-direction:column;"></div>
    <div class="pg" id="pg-divisions"><div class="pscroll" id="div-scroll"></div></div>
    <div class="pg" id="pg-market"><div class="pscroll" id="mkt-scroll"></div></div>
    <div class="pg" id="pg-politics" style="flex-direction:row;"></div>
    <div class="pg" id="pg-nations"><div class="pscroll" id="nat-scroll"></div></div>
    <div class="pg" id="pg-profile"><div class="pscroll" id="prof-scroll"></div></div>
    <div class="pg" id="pg-timeline" style="display:none;overflow:hidden;grid-template-columns:1fr 240px;"></div>
    <div class="pg" id="pg-calc"><div class="pscroll" id="calc-scroll"></div></div>
    <div class="pg" id="pg-ai" style="flex-direction:row;"></div>
    <div class="pg" id="pg-admin"><div class="adm-layout" id="adm-layout"></div></div>
  </div>
</div>

<script>
// ════════════════════════════════════════════
// IMAGES (injected by build script)
// ════════════════════════════════════════════
HTMLEOF
echo "part1 written"
