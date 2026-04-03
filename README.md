# OONE-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-
fit=cover">
<title>oone</title>
<link href="https://fonts.googleapis.com/css2?
family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400;1,500&family=Cormorant:ital,w
rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{--fs-xs:clamp(9px,.75vw,11px);--fs-sm:clamp(10px,.9vw,12px);--fs-
md:clamp(13px,1.1vw,15px);--fs-lg:clamp(20px,2vw,24px);--fs-
xl:clamp(28px,3.2vw,38px);--fs-2xl:clamp(32px,4vw,52px);--fs-
display:clamp(52px,7vw,96px);--sp:clamp(10px,1.2vw,14px)}
html,body{width:100%;height:100%;overflow:hidden}
body{background:#1C1412;color:#F9F0E8}
canvas{display:block}
#cv{position:fixed;inset:0;z-index:4;pointer-events:auto}
@media(pointer:fine){body{cursor:none}}
#cur{position:fixed;pointer-events:none;z-
index:9999;transform:translate(-50%,-50%);display:none}
@media(pointer:fine){#cur{display:block}}
/* ── LOGO MARK ── */
.oo-mark{position:relative;display:inline-block;width:2ex;height:1.55ex;vertical-
align:baseline;overflow:visible}
.oo-mark .o1,.oo-mark .o2{position:absolute;left:50%;top:55%;font-
family:"Cormorant Garamond",serif;font-style:italic;line-height:1;transform-
origin:center center;user-select:none;font-size:2.6ex}
.oo-mark .o1{font-weight:400;transform:translate(-50%,-50%) skewX(-28deg)}
.oo-mark .o2{font-weight:300;transform:translate(-50%,-50%) scaleX(-1)
skewX(-28deg) scale(0.86);-webkit-text-fill-color:transparent;-webkit-text-
stroke:.8px currentColor}
.oo-word{font-family:"Cormorant Garamond",serif;font-style:italic;font-
weight:300;display:inline;line-height:1}
/* ── NAV ── */
#nav{position:fixed;top:0;left:0;right:0;z-index:600;display:flex;align-
items:center;justify-content:space-between;padding:16px 24px;pointer-events:none}
#nav.vis{pointer-events:all}
.nav-left{pointer-events:all}
.nav-brand{cursor:pointer;transition:opacity .2s;opacity:.35;display:inline-
flex;align-items:baseline}
.nav-brand:hover{opacity:.6}
.nav-links{display:flex;gap:0;pointer-events:all}
.nav-link{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.14em;text-transform:uppercase;color:rgba(255,255,255,.28);padding:6px
16px;cursor:pointer;transition:all
.2s;border:none;background:none;position:relative;-webkit-tap-highlight-
color:transparent}
.nav-link:hover{color:rgba(255,255,255,.55)}
.nav-link.on{color:rgba(255,255,255,.65)}
.nav-
link.on::after{content:'';position:absolute;bottom:2px;left:16px;right:16px;height:1px;backgrou
.nav-drop{position:relative}
.nav-drop-
menu{display:none;position:absolute;top:100%;left:0;background:rgba(4,4,3,.94);border:1px
solid rgba(255,255,255,.06);backdrop-filter:blur(12px);padding:4px 0;min-
width:120px;z-index:10}
.nav-drop.open .nav-drop-menu{display:block}
.nav-drop-item{display:block;width:100%;padding:8px
16px;background:none;border:none;font-family:"Space Mono",monospace;font-
size:var(--fs-xs);letter-spacing:.12em;text-
transform:uppercase;color:rgba(255,255,255,.32);cursor:pointer;text-
align:left;transition:color .15s}
.nav-drop-item:hover{color:rgba(255,255,255,.65)}
.nav-right{display:flex;align-items:center;gap:10px;pointer-events:all}
.tp-btn{display:flex;align-items:center;gap:6px;padding:4px
10px;background:transparent;border:1px solid
rgba(255,255,255,.06);cursor:pointer;font-family:"Space Mono",monospace;font-
size:var(--fs-xs);letter-spacing:.10em;text-
transform:uppercase;color:rgba(255,255,255,.22);transition:all .2s}
.tp-btn:hover{color:rgba(255,255,255,.55);border-color:rgba(255,255,255,.2)}
/* ── KEY PANEL ── */
#panel-key{position:fixed;bottom:max(20px,env(safe-area-inset-
bottom,12px));left:20px;z-index:200;background:rgba(4,4,3,.82);border:1px solid
rgba(255,255,255,.05);backdrop-filter:blur(12px);padding:var(--sp) calc(var(--
sp)*1.2);min-width:130px}
#panel-filter{position:fixed;bottom:max(20px,env(safe-area-inset-
bottom,12px));right:20px;z-index:200;background:rgba(4,4,3,.82);border:1px solid
rgba(255,255,255,.05);backdrop-filter:blur(12px);padding:var(--sp) calc(var(--
sp)*1.2);min-width:140px}
.pk-head{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.16em;text-transform:uppercase;color:rgba(255,255,255,.16);padding-
bottom:6px;border-bottom:1px solid rgba(255,255,255,.05);margin-
bottom:6px;animation:ooneMonoDrift 14s ease-in-out infinite}
@keyframes oonePeek{
from{opacity:0;transform:translateY(.55em) skewX(-4.5deg);letter-
spacing:.06em;filter:blur(5px)}
to{opacity:1;transform:translateY(0) skewX(0);letter-
spacing:normal;filter:blur(0)}
}
.oone-peek{opacity:0}
#dw-body.oone-stag .oone-peek{animation:oonePeek .88s cubic-bezier(.16,1,.3,1)
forwards;animation-delay:var(--od,0s)}
#dw-body.oone-stag .oone-peek.oone-serif-drift{animation:oonePeek .88s cubic-
bezier(.16,1,.3,1) forwards,ooneSerifShimmer 9s ease-in-out infinite;animation-
delay:var(--od,0s),calc(var(--od, 0s) + 0.9s)}
@keyframes ooneMonoDrift{
0%,100%{letter-spacing:.16em;opacity:1}
50%{letter-spacing:.22em;opacity:.88}
}
@keyframes ooneDwCatDrift{
0%,100%{letter-spacing:.18em}
50%{letter-spacing:.24em}
}
.pk-row{display:flex;align-items:center;gap:10px;padding:4px 0;cursor:pointer;min-
height:24px}
.pk-row:hover .pk-lbl{color:rgba(255,255,255,.7)}
.pk-lbl{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.10em;text-
transform:uppercase;color:rgba(255,255,255,.28);transition:color .15s;user-
select:none}
.pk-row.on .pk-lbl{color:rgba(255,255,255,.62)}
.pk-dot{width:6px;height:6px;border-radius:50%;flex-shrink:0;transition:opacity
.2s}
.pk-row.dim .pk-dot{opacity:.25}
.pk-row.dim .pk-lbl{color:rgba(255,255,255,.15)}
.pk-sub{padding-left:16px}
.pk-sub .pk-row{min-height:20px}
.pk-circ{width:7px;height:7px;border-radius:50%;border:1px solid
rgba(255,255,255,.22);flex-shrink:0;transition:all .15s}
.pk-toggle{position:relative;width:26px;height:14px;border-
radius:7px;background:rgba(255,255,255,.10);border:1px solid
rgba(255,255,255,.12);cursor:pointer;flex-shrink:0;transition:background .2s}
.pk-toggle.on{background:rgba(255,255,255,.20);border-color:rgba(255,255,255,.25)}
.pk-
toggle::after{content:'';position:absolute;top:2px;left:2px;width:8px;height:8px;border-
radius:50%;background:rgba(255,255,255,.35);transition:all .2s}
.pk-toggle.on::after{left:14px;background:rgba(255,255,255,.65)}
/* ── DRAWER ── */
#drawer{position:fixed;bottom:0;left:0;right:0;z-index:500;background:var(--bar-
bg,rgba(7,6,5,.97));border-top:1px solid
rgba(255,255,255,.06);transform:translateY(100%);transition:height .3s
ease;height:50vh;display:flex;flex-direction:column;overflow:hidden}
#drawer.open{transform:translateY(0)}
#drawer.expanded{height:100vh;height:100dvh}
.drawer-open #panel-key,.drawer-open #panel-filter{display:none}
.dw-head{display:flex;align-items:center;justify-content:space-
between;padding:12px 24px;padding-top:max(12px,env(safe-area-inset-
top,12px));border-bottom:1px solid rgba(255,255,255,.06);flex-shrink:0}
.dw-cat{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.18em;text-
transform:uppercase;color:rgba(255,255,255,.28);animation:ooneDwCatDrift 12s ease-
in-out infinite}
.dw-acts{display:flex;gap:10px;align-items:center}
.dw-btn{background:none;border:none;cursor:pointer;font-family:"Space
Mono",monospace;font-size:var(--fs-xs);letter-spacing:.12em;text-
transform:uppercase;color:rgba(255,255,255,.28);padding:4px 8px;transition:color
.15s;-webkit-tap-highlight-color:transparent}
.dw-btn:hover{color:rgba(255,255,255,.7)}
.dw-body{flex:1;overflow-y:auto;padding:20px 24px 28px;padding-
bottom:max(28px,env(safe-area-inset-bottom,28px));-webkit-overflow-
scrolling:touch}
/* ── SHARED ── */
.dw-facts{border-top:1px solid rgba(255,255,255,.06);margin-bottom:14px}
.dw-fact{display:flex;gap:12px;padding:6px 0;border-bottom:1px solid
rgba(255,255,255,.05)}
.dw-fk{width:80px;flex-shrink:0;font-family:"Space Mono",monospace;font-size:var(-
-fs-xs);text-transform:uppercase;letter-spacing:.06em;color:rgba(255,255,255,.22)}
.dw-fv{font-family:"Space Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.50)}
.about-wrap{display:grid;grid-template-columns:1.1fr .9fr;gap:28px}
@media(max-width:640px){.about-wrap{grid-template-columns:1fr}}
.about-name{font-family:"Cormorant",serif;font-style:italic;font-
size:clamp(36px,5vw,56px);color:rgba(255,255,255,.88);margin-bottom:14px}
@keyframes ooneSerifShimmer{
0%,100%{opacity:1;transform:translateY(0)}
50%{opacity:.94;transform:translateY(-.04em)}
}
.about-bio{font-family:"Cormorant",serif;font-size:var(--fs-md);line-
height:1.75;color:rgba(255,255,255,.42);margin-bottom:10px}
.about-bio strong{color:rgba(255,255,255,.68);font-weight:400}
.stat-n{font-family:"Cormorant",serif;font-size:clamp(24px,3.5vw,32px);line-
height:1}
.stat-l{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.12em;text-transform:uppercase;color:rgba(255,255,255,.20);margin-
bottom:14px}
.cv-toggle{background:none;border:1px solid
rgba(255,255,255,.08);cursor:pointer;font-family:"IBM Plex Mono",monospace;font-
size:var(--fs-xs);letter-spacing:.10em;text-
transform:uppercase;color:rgba(255,255,255,.28);padding:6px 12px;margin-
top:10px;transition:all .15s}
.cv-toggle:hover{color:rgba(255,255,255,.62)}
.cv-panel{max-height:0;overflow:hidden;transition:max-height .4s ease}
.cv-panel.open{max-height:2000px}
.cv-sec-title{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.14em;text-transform:uppercase;color:rgba(255,255,255,.18);padding-
bottom:5px;border-bottom:1px solid rgba(255,255,255,.05);margin:16px 0 8px}
.cv-role-title{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
md);color:rgba(255,255,255,.65)}
.cv-role-date{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.18);float:right}
.cv-role-org{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.30);margin-bottom:4px}
.cv-role-desc{font-family:"Cormorant",serif;font-size:var(--fs-sm);line-
height:1.7;color:rgba(255,255,255,.26)}
.skills{display:flex;gap:4px;flex-wrap:wrap;margin-top:6px}
.skill{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-xs);padding:3px
7px;border:1px solid rgba(255,255,255,.06);color:rgba(255,255,255,.20)}
.dw-divider{border:none;border-top:1px solid rgba(255,255,255,.05);margin:18px 0}
.brand-lbl{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.16em;text-transform:uppercase;color:rgba(255,255,255,.12);margin-
bottom:8px}
.brand-name{font-family:"Cormorant Garamond",serif;font-style:italic;font-
size:var(--fs-lg);color:rgba(255,255,255,.45);margin-bottom:8px}
.brand-p{font-family:"Cormorant",serif;font-size:var(--fs-md);line-
height:1.75;color:rgba(255,255,255,.26);margin-bottom:6px}
/* ── SERVICES ── */
.svc-grid{display:grid;gap:12px}
.svc{padding:14px 16px;border:1px solid
rgba(255,255,255,.05);background:rgba(255,255,255,.01)}
.svc-name{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
lg);color:rgba(255,255,255,.65);margin-bottom:6px}
.svc-desc{font-family:"Cormorant",serif;font-size:var(--fs-md);line-
height:1.7;color:rgba(255,255,255,.30);margin-bottom:8px}
.svc-rate{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.20)}
.svc-ex{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.14);margin-top:4px}
.contact{margin-top:16px;padding-top:14px;border-top:1px solid
rgba(255,255,255,.05)}
.contact-title{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
lg);color:rgba(255,255,255,.45);margin-bottom:12px}
.dw-input{width:100%;background:none;border:none;border-bottom:1px solid
rgba(255,255,255,.08);font-family:"Cormorant",serif;font-size:var(--fs-
md);color:rgba(255,255,255,.65);outline:none;padding:6px 0;margin-bottom:10px}
.dw-input::placeholder{color:rgba(255,255,255,.16);font-style:italic}
.dw-textarea{width:100%;background:none;border:none;border-bottom:1px solid
rgba(255,255,255,.08);font-family:"Cormorant",serif;font-size:var(--fs-
md);color:rgba(255,255,255,.65);outline:none;padding:6px 0;margin-bottom:10px;min-
height:60px;resize:vertical}
.dw-textarea::placeholder{color:rgba(255,255,255,.16);font-style:italic}
.dw-send{padding:6px 14px;background:none;border:1px solid
rgba(255,255,255,.12);font-family:"Space Mono",monospace;font-size:var(--fs-
xs);letter-spacing:.14em;text-
transform:uppercase;color:rgba(255,255,255,.35);cursor:pointer;transition:all
.15s}
.dw-send:hover{background:rgba(255,255,255,.04);color:rgba(255,255,255,.75)}
/* ── LOG ── */
.log-tabs{display:flex;border-bottom:1px solid rgba(255,255,255,.06);margin-
bottom:14px}
.log-tab{padding:6px 16px;background:none;border:none;border-bottom:1.5px solid
transparent;margin-bottom:-1px;font-family:"Space Mono",monospace;font-size:var(--
fs-xs);letter-spacing:.12em;text-
transform:uppercase;color:rgba(255,255,255,.25);cursor:pointer;transition:color
.15s}
.log-tab.on{color:rgba(255,255,255,.65);border-bottom-color:rgba(255,255,255,.30)}
.log-panel{display:none}.log-panel.on{display:block}
.log-inner{display:flex;flex-direction:column;gap:10px}
.btn-row{display:flex;gap:5px;flex-wrap:wrap}
.lcbt{padding:5px 11px;background:none;border:1px solid
rgba(255,255,255,.08);font-family:"Space Mono",monospace;font-size:var(--fs-
xs);letter-spacing:.08em;text-
transform:lowercase;color:rgba(255,255,255,.24);cursor:pointer;transition:all
.15s}
.lcbt.on{background:rgba(255,255,255,.04);border-
color:rgba(255,255,255,.25);color:rgba(255,255,255,.75)}
.log-input{background:none;border:none;border-bottom:1px solid
rgba(255,255,255,.08);font-family:"Cormorant",serif;font-size:var(--fs-
lg);color:rgba(255,255,255,.65);outline:none;padding:5px 0;width:100%}
.log-input::placeholder{color:rgba(255,255,255,.16);font-style:italic}
.log-sub{display:flex;gap:8px;align-items:flex-end}
.log-lis{flex:1;background:none;border:none;border-bottom:1px solid
rgba(255,255,255,.06);font-family:"Space Mono",monospace;font-size:var(--fs-
sm);color:rgba(255,255,255,.45);outline:none;padding:5px 0}
.log-lis::placeholder{color:rgba(255,255,255,.14);font-style:italic}
.log-go{padding:5px 14px;background:none;border:1px solid
rgba(255,255,255,.15);font-family:"Space Mono",monospace;font-size:var(--fs-
xs);letter-spacing:.12em;text-
transform:uppercase;color:rgba(255,255,255,.35);cursor:pointer;flex-shrink:0}
.recent{display:flex;flex-direction:column;gap:2px;margin-top:6px}
.re-c{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.10em;text-transform:uppercase;width:auto;flex-shrink:0}
.re-t{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
md);color:rgba(255,255,255,.60);overflow:hidden;text-overflow:ellipsis;white-
space:nowrap;line-height:1.2}
.re-a{font-family:"Space Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.16);flex-shrink:0}
/* ── FEED ── */
.feed-grid{columns:2;column-gap:8px}
@media(min-width:800px){.feed-grid{columns:3}}
.feed-card{break-inside:avoid;margin-bottom:8px;border:1px solid
rgba(255,255,255,.05);background:rgba(255,255,255,.015);overflow:hidden}
.feed-card img{width:100%;display:block}
.feed-card-body{padding:8px 10px}
.feed-card-title{font-family:"Cormorant",serif;font-style:italic;font-size:var(--
fs-md);color:rgba(255,255,255,.55);line-height:1.3;margin-bottom:4px}
.feed-card-meta{font-family:"Space Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.18);letter-spacing:.06em}
.feed-card-text{font-family:"Cormorant",serif;font-size:var(--fs-
sm);color:rgba(255,255,255,.32);line-height:1.6;margin-bottom:4px}
.feed-card a{color:rgba(255,255,255,.35);text-decoration:none;border-bottom:1px
solid rgba(255,255,255,.08)}
.feed-card a:hover{color:rgba(255,255,255,.6)}
.feed-src{display:flex;gap:10px;margin-bottom:12px}
.feed-src-btn{padding:5px 11px;background:none;border:1px solid
rgba(255,255,255,.08);font-family:"Space Mono",monospace;font-size:var(--fs-
xs);letter-spacing:.08em;text-
transform:lowercase;color:rgba(255,255,255,.24);cursor:pointer;transition:all
.15s}
.feed-src-btn.on{background:rgba(255,255,255,.04);border-
color:rgba(255,255,255,.25);color:rgba(255,255,255,.70)}
.feed-loading{font-family:"Space Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.18);padding:20px 0;text-align:center;letter-
spacing:.12em;text-transform:uppercase}
.feed-empty{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
md);color:rgba(255,255,255,.22);padding:20px 0;text-align:center}
/* ── ARENA ── */
.arena-src-row{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:14px}
.arena-src-btn{padding:5px 11px;background:none;border:1px solid
rgba(255,255,255,.08);font-family:"Space Mono",monospace;font-size:var(--fs-
xs);letter-spacing:.08em;text-
transform:lowercase;color:rgba(255,255,255,.24);cursor:pointer;transition:all
.15s}
.arena-src-btn.on{background:rgba(255,255,255,.04);border-
color:rgba(255,255,255,.25);color:rgba(255,255,255,.70)}
.arena-grid-wrap{overflow-y:auto}
.arena-grid{columns:2;column-gap:6px}
@media(min-width:600px){.arena-grid{columns:3}}
@media(min-width:900px){.arena-grid{columns:4}}
.arena-card{break-inside:avoid;margin-
bottom:6px;cursor:pointer;overflow:hidden;position:relative}
.arena-card img{width:100%;height:auto;display:block;transition:opacity .3s}
.arena-card:hover img{opacity:.75}
.arena-cap{position:absolute;bottom:0;left:0;right:0;padding:6px
8px;background:linear-gradient(transparent,rgba(0,0,0,.7));font-
family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
sm);color:rgba(255,255,255,.65);line-height:1.3;opacity:0;transition:opacity .25s}
.arena-card:hover .arena-cap{opacity:1}
/* ── GALLERY ── */
.gal-filters{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:16px}
.gal-grid{columns:2;column-gap:9px}
@media(min-width:520px){.gal-grid{columns:3}}
@media(min-width:820px){.gal-grid{columns:4}}
@media(min-width:1100px){.gal-grid{columns:5}}
.gal-item{position:relative;break-inside:avoid;margin-
bottom:9px;overflow:hidden;cursor:pointer;background:rgba(255,255,255,.012);transition:transfor
.28s cubic-bezier(.16,1,.3,1),box-shadow .28s ease;will-change:transform}
.gal-item:hover{transform:translateY(-3px);box-shadow:0 10px 32px rgba(0,0,0,.5)}
.gal-item img{width:100%;height:auto;display:block;position:relative;z-
index:1;filter:grayscale(100%) brightness(.88);transition:filter .55s ease}
.gal-item canvas{display:none}
.gal-mode-multi .gal-item:hover img{filter:grayscale(25%) brightness(1)}
.gal-mode-multi .gal-item.proj-open img{filter:grayscale(0%) brightness(1)}
.gal-mode-mono .gal-item img{filter:grayscale(100%) brightness(.88)}
.gal-mode-mono .gal-item:hover img{filter:grayscale(100%) brightness(1)}
.gal-mode-duo .gal-item img{filter:grayscale(100%) sepia(60%) brightness(.88)}
.gal-mode-duo .gal-item:hover img{filter:grayscale(20%) sepia(40%) brightness(1)}
.gal-label{position:absolute;bottom:0;left:0;right:0;padding:20px 10px 8px;z-
index:3;font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
sm);color:rgba(255,255,255,.75);pointer-events:none;transition:opacity
.3s;background:linear-gradient(transparent,rgba(0,0,0,.65))}
.gal-item:hover .gal-label{opacity:0}
#image-view{position:fixed;inset:0;z-index:3;background:var(--
bg,#1C1412);overflow-y:auto;-webkit-overflow-
scrolling:touch;display:none;padding:56px 20px 60px}
#image-view.on{display:block}
#image-view .gal-grid{columns:2;column-gap:9px}
@media(min-width:520px){#image-view .gal-grid{columns:3}}
@media(min-width:820px){#image-view .gal-grid{columns:4}}
.iv-head{position:fixed;top:0;left:0;right:0;z-index:4;display:flex;align-
items:center;justify-content:space-between;padding:16px
24px;background:rgba(7,6,5,.92);backdrop-filter:blur(10px)}
.iv-title{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.18em;text-
transform:uppercase;color:rgba(255,255,255,.28);animation:ooneMonoDrift 14s ease-
in-out infinite;animation-delay:-3s}
.iv-log-bub{background:none;border:1px solid rgba(255,255,255,.12);border-
radius:50%;width:52px;height:52px;display:flex;align-items:center;justify-
content:center;font-family:"Space Mono",monospace;font-size:8px;letter-
spacing:.18em;text-
transform:uppercase;color:rgba(255,255,255,.38);cursor:pointer;transition:all .3s
cubic-bezier(.16,1,.3,1);position:relative;overflow:hidden}
.iv-log-bub::before{content:'';position:absolute;inset:0;border-
radius:50%;background:radial-gradient(circle at 38%
30%,rgba(255,255,255,.08),transparent 65%);pointer-events:none}
.iv-log-bub:hover{color:rgba(255,255,255,.75);border-
color:rgba(255,255,255,.30);transform:scale(1.08);box-shadow:0 0 20px
rgba(255,255,255,.06)}
/* ── FEED OVERLAY ── */
#feed-overlay{position:fixed;inset:0;z-index:2;pointer-
events:none;display:none;overflow:hidden}
#feed-overlay.on{display:block}
.feed-ticker-
wrap{position:absolute;bottom:0;left:0;right:0;height:100%;display:flex;flex-
direction:column;justify-content:center}
.feed-ticker{display:flex;gap:12px;animation:feedScroll 80s linear
infinite;width:max-content;padding:0 12px}
.feed-ticker img{height:32vh;width:auto;opacity:.22;display:block;flex-
shrink:0;pointer-events:auto;cursor:pointer;transition:opacity .4s}
.feed-ticker img:hover{opacity:.55}
@keyframes feedScroll{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}
/* ── TOOLTIP ── */
#tip{position:fixed;z-index:800;background:rgba(10,10,8,.97);border:1px solid
rgba(255,255,255,.08);padding:10px 14px;pointer-
events:none;opacity:0;transition:opacity .12s;max-width:240px}
#tip.on{opacity:1}
.t-cat{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.16em;text-transform:uppercase;margin-bottom:5px}
.t-title{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
md);letter-spacing:.03em;color:rgba(255,255,255,.70);margin-bottom:3px;line-
height:1.1}
.t-sub{font-family:"Cormorant",serif;font-size:var(--fs-
sm);color:rgba(255,255,255,.40)}
.t-time{font-family:"Space Mono",monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.20);margin-top:4px}
/* ── THEME ── */
#theme-chooser{position:fixed;inset:0;z-
index:700;background:rgba(0,0,0,.6);display:flex;align-items:flex-end;justify-
content:flex-end;padding:20px;pointer-events:none;opacity:0;transition:opacity
.2s}
#theme-chooser.on{opacity:1;pointer-events:all}
.tc-panel{background:rgba(6,5,4,.97);border:1px solid
rgba(255,255,255,.05);padding:14px 16px 12px;position:relative}
.tc-close{position:absolute;top:-8px;right:-8px;width:18px;height:18px;border-
radius:50%;background:rgba(20,18,16,1);border:1px solid
rgba(255,255,255,.10);cursor:pointer;font-family:"Space Mono",monospace;font-
size:10px;color:rgba(255,255,255,.30);display:flex;align-items:center;justify-
content:center;transition:all .15s}
.tc-close:hover{color:rgba(255,255,255,.7)}
.tc-grid{display:flex;flex-direction:column;gap:5px}
.tc-row{display:flex;gap:5px}
.tc-bub{width:20px;height:20px;border-radius:50%;cursor:pointer;border:1.5px solid
transparent;transition:transform .18s;flex-
shrink:0;position:relative;overflow:hidden}
.tc-
bub::after{content:"";position:absolute;top:10%;left:14%;width:32%;height:18%;border-
radius:50%;background:rgba(255,255,255,.38);filter:blur(1px);transform:rotate(-20deg)}
.tc-bub:hover{transform:scale(1.35);border-color:rgba(255,255,255,.25)}
.tc-bub.sel{border-color:rgba(255,255,255,.75);transform:scale(1.15)}
/* ── TUTORIAL ── */
#tut{position:fixed;inset:0;z-index:8000;pointer-
events:none;opacity:0;transition:opacity .5s}
#tut.on{opacity:1;pointer-events:all}
.tut-dim{position:absolute;inset:0;background:rgba(0,0,0,.58)}
.tut-card{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);max-
width:420px;width:90%;padding:36px 36px
28px;background:rgba(12,11,9,.97);border:1px solid rgba(255,255,255,.05);backdrop-
filter:blur(14px);min-height:240px;display:flex;flex-direction:column}
.tut-step{font-family:"IBM Plex Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.18em;text-transform:uppercase;color:rgba(255,255,255,.14);margin-
bottom:12px;min-height:14px}
.tut-title{font-family:"Cormorant",serif;font-style:italic;font-size:var(--fs-
lg);color:rgba(255,255,255,.70);line-height:1.15;margin-bottom:12px;min-
height:28px;animation:ooneSerifShimmer 9s ease-in-out infinite;animation-
delay:-1.5s}
.tut-body{font-family:"Cormorant",serif;font-size:var(--fs-md);line-
height:1.72;color:rgba(255,255,255,.35);margin-bottom:20px;flex:1;min-height:48px}
.tut-body em{color:rgba(255,255,255,.50);font-style:italic}
.tut-nav{display:flex;align-items:center;justify-content:space-between;min-
height:28px}
.tut-dots{display:flex;gap:6px}
.tut-dot{width:5px;height:5px;border-
radius:50%;background:rgba(255,255,255,.10);transition:all .2s}
.tut-dot.on{background:rgba(255,255,255,.40)}
.tut-btn{background:none;border:1px solid rgba(255,255,255,.10);font-family:"IBM
Plex Mono",monospace;font-size:var(--fs-xs);letter-spacing:.12em;text-
transform:uppercase;color:rgba(255,255,255,.30);padding:6px
14px;cursor:pointer;transition:all .15s}
.tut-btn:hover{color:rgba(255,255,255,.68);border-color:rgba(255,255,255,.22)}
.tut-skip{background:none;border:none;font-family:"IBM Plex Mono",monospace;font-
size:var(--fs-xs);letter-spacing:.10em;text-
transform:uppercase;color:rgba(255,255,255,.14);cursor:pointer;transition:color
.15s}
.tut-skip:hover{color:rgba(255,255,255,.35)}
/* ── PROJECT ── */
.proj-wrap{display:grid;grid-template-columns:1fr 1fr;gap:20px}
@media(max-width:640px){.proj-wrap{grid-template-columns:1fr}}
.proj-title{font-family:"Cormorant",serif;font-style:italic;font-
size:clamp(32px,4vw,54px);letter-spacing:-.01em;line-
height:.95;color:rgba(255,255,255,.92);margin-bottom:12px}
.proj-tag{font-family:"Cormorant",serif;font-size:var(--fs-md);line-
height:1.6;color:rgba(255,255,255,.38);margin-bottom:20px;padding-
bottom:20px;border-bottom:1px solid rgba(255,255,255,.06)}
.proj-desc{font-family:"Cormorant",serif;font-size:clamp(15px,1.3vw,18px);line-
height:1.78;color:rgba(255,255,255,.42);flex:1}
/* ── PROJECT LAYOUT ── */
.proj-layout{display:grid;grid-template-columns:52% 48%;gap:0;min-height:70vh}
@media(max-width:640px){.proj-layout{grid-template-columns:1fr;min-height:auto}}
.proj-img-col{position:relative;overflow:hidden;background:#0a0a08;min-
height:320px}
.proj-img-col img{width:100%;height:100%;object-
fit:cover;display:block;transition:transform .8s cubic-bezier(.16,1,.3,1)}
.proj-img-col:hover img{transform:scale(1.03)}
.proj-img-
expand{position:absolute;bottom:12px;right:12px;background:rgba(0,0,0,.72);border:1px
solid rgba(255,255,255,.14);color:rgba(255,255,255,.5);font-family:"Space
Mono",monospace;font-size:9px;letter-spacing:.14em;text-
transform:uppercase;padding:5px 10px;cursor:pointer;transition:all .2s;backdrop-
filter:blur(4px)}
.proj-img-expand:hover{color:rgba(255,255,255,.9);background:rgba(0,0,0,.9)}
.proj-info-col{padding:32px 28px 24px;display:flex;flex-direction:column;border-
left:1px solid rgba(255,255,255,.05)}
.proj-eyebrow{font-family:"Space Mono",monospace;font-size:var(--fs-xs);letter-
spacing:.22em;text-transform:uppercase;color:rgba(255,255,255,.22);margin-
bottom:16px}
.proj-extra-imgs{display:none;margin-top:12px;flex-direction:column;gap:6px}
.proj-extra-imgs.open{display:flex}
.proj-extra-img{width:100%;display:block}
.proj-facts{margin-top:20px;padding-top:16px;border-top:1px solid
rgba(255,255,255,.06)}
.proj-fact{display:flex;gap:16px;padding:5px 0;border-bottom:1px solid
rgba(255,255,255,.03)}
.proj-fk{width:76px;flex-shrink:0;font-family:"Space Mono",monospace;font-
size:9px;text-transform:uppercase;letter-
spacing:.10em;color:rgba(255,255,255,.18)}
.proj-fv{font-family:"Space Mono",monospace;font-
size:9px;color:rgba(255,255,255,.40);letter-spacing:.04em}
/* ── LOG ENTRY WITH THUMB ── */
.re{display:flex;gap:12px;align-items:flex-start;padding:8px 0;border-bottom:1px
solid rgba(255,255,255,.04);cursor:pointer;transition:background .15s}
.re:hover{background:rgba(255,255,255,.025);margin:0 -8px;padding:8px}
.re-thumb{width:52px;height:52px;flex-
shrink:0;overflow:hidden;background:rgba(255,255,255,.04)}
.re-thumb img{width:100%;height:100%;object-fit:cover;display:block}
.re-body{display:flex;flex-direction:column;justify-
content:center;flex:1;overflow:hidden;gap:3px}
.re-meta{display:flex;align-items:center;justify-content:space-between;gap:8px}
</style>
</head>
<body>
<div id="cur"><svg width="14" height="14" viewBox="0 0 14 14"><circle cx="7"
cy="7" r="5.5" fill="none" stroke="rgba(240,232,216,.30)" stroke-width=".5"/>
<circle cx="7" cy="7" r="1.1" fill="#C8944A" id="cur-dot"/></svg></div>
<canvas id="cv"></canvas>
<div id="nav" class="vis">
<div class="nav-left"><span class="nav-brand" onclick="goHome()"><span
class="oo-word" style="font-size:20px;color:rgba(255,255,255,.30)"><span
class="oo-mark"><span class="o1">O</span><span class="o2">O</span></span>ne</span>
</span></div>
<div class="nav-links">
<button class="nav-link" onclick="navTo('about')">About</button>
<button class="nav-link" onclick="navTo('services')">Services</button>
<div class="nav-drop" id="nav-log-drop">
<button class="nav-link" onclick="toggleLogDrop(event)">View</button>
<div class="nav-drop-menu">
<button class="nav-drop-item"
onclick="setMainView('log');closeLogDrop()">Log</button>
<button class="nav-drop-item"
onclick="setMainView('gallery');closeLogDrop()">Gallery</button>
<button class="nav-drop-item"
onclick="setMainView('feed');closeLogDrop()">Feed</button>
</div>
</div>
</div>
<div class="nav-right"><button class="tp-btn" onclick="openThemeChooser()"><div
id="tp-dot" style="width:7px;height:7px;border-radius:50%;background:#C8944A;flex-
shrink:0"></div><span id="tp-label">F.2</span></button></div>
</div>
<div id="panel-key">
<div class="pk-head">view</div>
<div class="pk-row on" id="pk-log" onclick="setMainView('log')"><div class="pk-
dot" style="background:rgba(255,255,255,.50)"></div><span class="pk-
lbl">log</span></div>
<div class="pk-row" id="pk-gallery" onclick="setMainView('gallery')"><div
class="pk-dot" style="background:rgba(255,255,255,.30)"></div><span class="pk-
lbl">gallery</span></div>
<div class="pk-row" id="pk-feed" onclick="setMainView('feed')"><div class="pk-
dot" style="background:rgba(255,255,255,.20)"></div><span class="pk-
lbl">feed</span></div>
<div class="pk-head" style="margin-top:8px">show</div>
<div class="pk-row on" id="pk-practice" onclick="toggleShowFilter('practice')">
<div class="pk-circ" id="prac-circ"></div><span class="pk-lbl">practice</span>
</div>
<div class="pk-row on" id="pk-play" onclick="toggleShowFilter('play')"><div
class="pk-circ" id="play-circ"></div><span class="pk-lbl">play</span></div>
<div class="pk-row" style="margin-top:6px;gap:8px"><span class="pk-lbl"
style="font-size:var(--fs-xs);opacity:.5">time</span><div class="pk-toggle on"
id="pk-timespace" onclick="toggleTimeSpace()"></div><span class="pk-lbl"
style="font-size:var(--fs-xs);opacity:.5">space</span></div>
</div>
<div id="panel-filter">
<div class="pk-head" id="pf-head">log</div>
<div id="pf-rows"></div>
</div>
<div id="image-view"></div>
<div id="feed-overlay"><div class="feed-ticker-wrap"><div class="feed-ticker"
id="feed-ticker"></div></div></div>
<div id="drawer"><div class="dw-head"><span class="dw-cat" id="dw-cat"></span><div
class="dw-acts"><button class="dw-btn" id="dw-expand-btn"
onclick="toggleDrawerExpand()">expand</button><button class="dw-btn"
onclick="closeDrawer()">&times;</button></div></div><div class="dw-body" id="dw-
body"></div></div>
<div id="tip"><div class="t-cat" id="tip-cat"></div><div class="t-title" id="tip-
title"></div><div class="t-sub" id="tip-sub"></div><div class="t-time" id="tip-
time"></div></div>
<div id="theme-chooser" onclick="if(event.target===this)closeThemeChooser()"><div
class="tc-panel"><button class="tc-close" onclick="closeThemeChooser()">&times;
</button><div id="tc-grid"></div></div></div>
<div id="tut"><div class="tut-dim" onclick="closeTut()"></div><div class="tut-
card" id="tut-card"></div></div>
<div style="position:fixed;bottom:8px;right:20px;z-index:150;pointer-events:none">
<span class="oo-word" style="font-size:14px;color:rgba(255,255,255,.10)"><span
class="oo-mark"><span class="o1">O</span><span class="o2">O</span></span>ne</span>
</div>
<script>
var KEY='oone_v27',DAY=86400000,NOW=Date.now();
function load(){try{var r=localStorage.getItem(KEY);if(r)return
JSON.parse(r);}catch(e){}return{entries:[]};}
function save(){try{localStorage.setItem(KEY,JSON.stringify(ARCH));}catch(e){}}
var ARCH=load();
var COSMOS_GQL='https://api.cosmos.so/graphql';
var COSMOS_BOARDS=[
{id:780860256,tags:['architecture','interiors']},
{id:191788568,tags:['print + digital']}
];
var _cosmosCache={};
var _cosmosCatFilter='';
function fetchCosmos(boardId,cb){
if(_cosmosCache[boardId])return cb(_cosmosCache[boardId]);
fetch(COSMOS_GQL,{method:'POST',headers:{'Content-Type':'application/json'},
body:JSON.stringify({query:'{ cluster(id:'+boardId+') { elements { items { id
type image { url width height } } } } }'})
}).then(function(r){return r.json();})
.then(function(d){
var items=((d.data||{}).cluster||{}).elements||{};
var imgs=(items.items||[]).filter(function(b){return
b.image&&b.image.url;});
_cosmosCache[boardId]=imgs;cb(imgs);
}).catch(function(){cb([]);});
}
function renderCosmosGrid(){
var grid=document.getElementById('arena-grid');
if(!grid)return;
var allImgs=[];
COSMOS_BOARDS.forEach(function(board){
var show=!_cosmosCatFilter||board.tags.indexOf(_cosmosCatFilter)>=0;
if(show)(_cosmosCache[board.id]||[]).forEach(function(img)
{allImgs.push(img);});
});
grid.innerHTML='';
if(!allImgs.length){grid.innerHTML='<div class="feed-empty">nothing
here</div>';return;}
allImgs.forEach(function(b){
var card=document.createElement('div');card.className='arena-card';
card.innerHTML='<img src="'+b.image.url+'?w=600" alt="" loading="lazy">';
grid.appendChild(card);
});
}
function setCosmosCat(cat){
_cosmosCatFilter=(_cosmosCatFilter===cat)?'':cat;
document.querySelectorAll('.cosmos-cat-btn').forEach(function(b)
{b.classList.toggle('on',b.getAttribute('data-cat')===_cosmosCatFilter);});
renderCosmosGrid();
}
function loadAllCosmos(){
var loaded=0;
COSMOS_BOARDS.forEach(function(board){
fetchCosmos(board.id,function()
{loaded++;if(loaded===COSMOS_BOARDS.length)renderCosmosGrid();});
});
}
var PROJECTS={
spa:{id:'spa',title:'Cellar Spa',tag:'Cellar floor lap pool and spa, Upper East
Side.',facts:[['Location','New York, NY'],['Client','Wesley Moon Inc'],
['Scope','SD to DD'],['Program','Lap pool, sauna, steam, spa'],['Year','2024–26'],
['Role','Designer']],desc:'Reworked the schematic design. Composed wood flooring
pattern, modeled carved stone sink, developed pool mosaic
language.',galCat:'practice',galSub:'interiors'},
bigsky:{id:'bigsky',title:'Stargazer Compound',tag:'Ski compound spa
reconfiguration, Big Sky, Montana.',facts:[['Location','Big Sky, MT'],
['Client','Hart Howerton'],['Scope','SD to DD'],['Program','Compound, spa,
suites'],['Year','2024–26'],['Role','Designer']],desc:'SD to DD for two
residential ski compounds. Spa ceiling reveals constellations through aperiodic
paneling.',galCat:'practice',galSub:'architecture'},
troub:{id:'troub',title:'Troubadour Club',tag:'Community fitness center, College
Grove, Tennessee.',facts:[['Location','College Grove, TN'],['Client','Hart
Howerton'],['Scope','DD to CD'],['Area','34,200 SF'],['Year','2023'],
['Role','Designer']],desc:'DD to CD drawing set. Reflected ceiling plans, interior
elevations, millwork details.',galCat:'practice',galSub:'architecture'},
ranch:{id:'ranch',title:'Covert Ranch',tag:'Private working ranch, Texas Hill
Country.',facts:[['Location','Austin, TX'],['Client','Hart Howerton'],['Scope','SD
Package'],['Program','Kitchen, bar, dining'],['Year','2023'],
['Role','Designer']],desc:'Material palette: blackened steel, Corten cladding,
board-formed concrete, woven leather.',galCat:'practice',galSub:'interiors'},
twins:{id:'twins',title:'Housing Dual Neighbors',tag:'Two residential towers
negotiating the urban grid.',facts:[['Location','New York, NY'],['Client','M.Arch
UVA'],['Scope','Schematic Design'],['Program','Mixed-use residential'],
['Year','2021'],['Role','Designer']],desc:'Mediates city grid vs. true north,
elevated vs. at-grade. Two towers share a podium but diverge in
section.',galCat:'practice',galSub:'urban design'}
};
var GAL_META=[
{projId:null,cat:'photography',sub:'photography'},
{projId:null,cat:'photography',sub:'photography'},
{projId:null,cat:'photography',sub:'photography'},
{projId:null,cat:'photography',sub:'photography'},
{projId:'spa',cat:'practice',sub:'interiors'},
{projId:'spa',cat:'practice',sub:'interiors'},
{projId:'spa',cat:'practice',sub:'interiors'},
{projId:'spa',cat:'practice',sub:'interiors'},
{projId:'bigsky',cat:'practice',sub:'architecture'},
{projId:'bigsky',cat:'practice',sub:'architecture'},
{projId:'bigsky',cat:'practice',sub:'architecture'},
{projId:'troub',cat:'practice',sub:'architecture'},
{projId:'troub',cat:'practice',sub:'architecture'},
{projId:'troub',cat:'practice',sub:'architecture'},
{projId:'ranch',cat:'practice',sub:'interiors'},
{projId:'ranch',cat:'practice',sub:'interiors'},
{projId:'ranch',cat:'practice',sub:'interiors'},
{projId:'twins',cat:'practice',sub:'urban design'},
{projId:'twins',cat:'practice',sub:'urban design'},
{projId:null,cat:'photography',sub:'photography'},
{projId:null,cat:'photography',sub:'photography'},
{projId:null,cat:'photography',sub:'photography'}
];
if(!ARCH.entries.length){ARCH.entries=[
{cat:'artifacts',rel:'itself',title:'Cellar Spa',sub:'Wesley Moon Inc',place:'New
York',lat:40.7736,lng:-73.9566,t:NOW-42*DAY,id:'spa'},
{cat:'artifacts',rel:'itself',title:'Stargazer Compound',sub:'Hart
Howerton',place:'Big Sky MT',lat:45.2836,lng:-111.4010,t:NOW-38*DAY,id:'bigsky'},
{cat:'artifacts',rel:'itself',title:'Troubadour Club',sub:'Hart
Howerton',place:'College Grove TN',lat:35.7731,lng:-86.8930,t:NOW-
32*DAY,id:'troub'},
{cat:'artifacts',rel:'itself',title:'Covert Ranch',sub:'Hart
Howerton',place:'Austin TX',lat:30.2672,lng:-97.7431,t:NOW-28*DAY,id:'ranch'},
{cat:'artifacts',rel:'itself',title:'Housing Dual Neighbors',sub:'M.Arch
UVA',place:'New York',lat:40.7282,lng:-73.9942,t:NOW-200*DAY,id:'twins'},
{cat:'sensations',rel:'itself',title:'Palladium NYC',sub:'14th St',place:'New
York',lat:40.7340,lng:-73.9893,t:NOW-20*DAY},
{cat:'sensations',rel:'orbit',title:'Circles',sub:'Mac
Miller',place:'Nashville',lat:36.1627,lng:-86.7816,t:NOW-28*DAY},
{cat:'sensations',rel:'orbit',title:'Purple
Rain',sub:'Prince',place:'Nashville',lat:36.1580,lng:-86.7780,t:NOW-3*DAY},
{cat:'artifacts',rel:'orbit',title:'Learning from Las Vegas',sub:'Venturi Scott
Brown',place:'Nashville',lat:36.1580,lng:-86.7890,t:NOW-24*DAY},
{cat:'artifacts',rel:'orbit',title:'RSVP Cycles',sub:'Lawrence
Halprin',place:'Nashville',lat:36.1630,lng:-86.7850,t:NOW-12*DAY},
{cat:'ideas',rel:'itself',title:'narrative integrity at every
scale',place:'Nashville',lat:36.1560,lng:-86.7870,t:NOW-18*DAY},
{cat:'ideas',rel:'itself',title:'the body as the
measure',place:'Nashville',lat:36.1590,lng:-86.7840,t:NOW-5*DAY},
{cat:'ideas',rel:'itself',title:'systems thinking and
hospitality',place:'Nashville',lat:36.1600,lng:-86.7860,t:NOW-9*DAY}
];save();}
var GAL_IMGS=[
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
{src:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAA0JCgsKCA0LCgsODg0PEyAVExISEyccHh
];
var SCHEMES=[{id:'s-fal',num:'F',word:'FERRO',acc:[228,68,28],vars:[{v:'v1',acc:
[205,52,20],bg:'#180A05'},{v:'v2',acc:[228,68,28],bg:'#1A0C06'},{v:'v3',acc:
[252,95,42],bg:'#1C0E07'}]},{id:'s-win',num:'W',word:'COBALT',acc:
[58,102,252],vars:[{v:'v1',acc:[38,78,228],bg:'#070918'},{v:'v2',acc:
[58,102,252],bg:'#090B1C'},{v:'v3',acc:[88,130,255],bg:'#0B0D20'}]},{id:'s-
spr',num:'S',word:'PATINA',acc:[32,198,148],vars:[{v:'v1',acc:
[20,172,128],bg:'#071210'},{v:'v2',acc:[32,198,148],bg:'#081412'},{v:'v3',acc:
[50,218,165],bg:'#0A1614'}]},{id:'s-sum',num:'U',word:'AMBER',acc:
[238,162,28],vars:[{v:'v1',acc:[215,140,16],bg:'#130F05'},{v:'v2',acc:
[238,162,28],bg:'#150F06'},{v:'v3',acc:[255,182,46],bg:'#171108'}]},{id:'s-
stn',num:'T',word:'BONE',acc:[210,188,155],vars:[{v:'v1',acc:
[185,162,128],bg:'#0D0C0B'},{v:'v2',acc:[210,188,155],bg:'#0F0E0D'},{v:'v3',acc:
[232,210,178],bg:'#111010'}]}];
var SVARS={'s-fal|v1':{'--bg':'#180A05','--ink':'#FAF0E8','--
ink2':'rgba(250,240,232,.35)','--acc':'#CD341480','--bar-
bg':'rgba(24,10,5,.97)'},'s-fal|v2':{'--bg':'#1A0C06','--ink':'#FAF0E8','--
ink2':'rgba(250,240,232,.35)','--acc':'#E4441C','--bar-
bg':'rgba(26,12,6,.97)'},'s-fal|v3':{'--bg':'#1C0E07','--ink':'#FAF0E8','--
ink2':'rgba(250,240,232,.35)','--acc':'#FC5F2A','--bar-
bg':'rgba(28,14,7,.97)'},'s-win|v1':{'--bg':'#070918','--ink':'#EAF0FF','--
ink2':'rgba(234,240,255,.35)','--acc':'#264EE4','--bar-bg':'rgba(7,9,24,.97)'},'s-
win|v2':{'--bg':'#090B1C','--ink':'#EAF0FF','--ink2':'rgba(234,240,255,.35)','--
acc':'#3A66FC','--bar-bg':'rgba(9,11,28,.97)'},'s-win|v3':{'--bg':'#0B0D20','--
ink':'#EAF0FF','--ink2':'rgba(234,240,255,.35)','--acc':'#5882FF','--bar-
bg':'rgba(11,13,32,.97)'},'s-spr|v1':{'--bg':'#071210','--ink':'#E8F8F2','--
ink2':'rgba(232,248,242,.35)','--acc':'#14AC80','--bar-
bg':'rgba(7,18,16,.97)'},'s-spr|v2':{'--bg':'#081412','--ink':'#E8F8F2','--
ink2':'rgba(232,248,242,.35)','--acc':'#20C694','--bar-
bg':'rgba(8,20,18,.97)'},'s-spr|v3':{'--bg':'#0A1614','--ink':'#E8F8F2','--
ink2':'rgba(232,248,242,.35)','--acc':'#32DAA5','--bar-
bg':'rgba(10,22,20,.97)'},'s-sum|v1':{'--bg':'#130F05','--ink':'#FAF4E5','--
ink2':'rgba(250,244,229,.35)','--acc':'#D78C10','--bar-
bg':'rgba(19,15,5,.97)'},'s-sum|v2':{'--bg':'#150F06','--ink':'#FAF4E5','--
ink2':'rgba(250,244,229,.35)','--acc':'#EEA21C','--bar-
bg':'rgba(21,15,6,.97)'},'s-sum|v3':{'--bg':'#171108','--ink':'#FAF4E5','--
ink2':'rgba(250,244,229,.35)','--acc':'#FFB62E','--bar-
bg':'rgba(23,17,8,.97)'},'s-stn|v1':{'--bg':'#0D0C0B','--ink':'#EDE6DA','--
ink2':'rgba(237,230,218,.35)','--acc':'#B9A280','--bar-
bg':'rgba(13,12,11,.97)'},'s-stn|v2':{'--bg':'#0F0E0D','--ink':'#EDE6DA','--
ink2':'rgba(237,230,218,.35)','--acc':'#D2BC9B','--bar-
bg':'rgba(15,14,13,.97)'},'s-stn|v3':{'--bg':'#111010','--ink':'#EDE6DA','--
ink2':'rgba(237,230,218,.35)','--acc':'#E8D2B2','--bar-bg':'rgba(17,16,16,.97)'}};
var RAMPS={'s-fal|v2':{base:[26,12,6],stops:[[0,[26,12,6]],[.10,[68,18,5]],[.24,
[125,32,8]],[.40,[192,50,14]],[.56,[228,68,28]],[.68,[245,108,55]],[.80,
[255,152,95]],[.91,[255,205,158]],[1,[250,240,225]]]},'s-win|v2':{base:
[9,11,28],stops:[[0,[9,11,28]],[.10,[16,20,68]],[.25,[25,38,132]],[.42,
[36,64,202]],[.57,[58,102,252]],[.70,[98,138,255]],[.82,[145,175,255]],[.92,
[192,212,255]],[1,[232,242,255]]]},'s-spr|v2':{base:[8,20,18],stops:[[0,
[8,20,18]],[.10,[8,45,30]],[.26,[9,82,52]],[.43,[14,138,92]],[.58,[32,198,148]],
[.70,[68,220,170]],[.82,[112,238,192]],[.92,[165,248,215]],[1,[220,252,238]]]},'s-
sum|v2':{base:[21,15,6],stops:[[0,[21,15,6]],[.10,[52,35,5]],[.25,[92,60,7]],[.42,
[158,108,10]],[.57,[238,162,28]],[.70,[252,190,60]],[.82,[255,215,105]],[.92,
[255,235,162]],[1,[252,248,225]]]},'s-stn|v2':{base:[15,14,13],stops:[[0,
[15,14,13]],[.12,[38,32,22]],[.28,[66,52,36]],[.44,[112,88,60]],[.58,
[210,188,155]],[.70,[228,208,175]],[.82,[240,224,198]],[.92,[248,238,218]],[1,
[252,246,236]]]}};
// Fallback ramps for v1/v3 just reference v2
Object.keys(RAMPS).forEach(function(k){var sid=k.split('|')
[0];if(!RAMPS[sid+'|v1'])RAMPS[sid+'|v1']=RAMPS[k];if(!RAMPS[sid+'|v3'])RAMPS[sid+'|v3']=RAMPS
var SCHEME_CATS={'s-fal':{ideas:[248,192,52],artifacts:[228,68,28],sensations:
[255,142,92]},'s-win':{ideas:[112,168,255],artifacts:[58,102,252],sensations:
[172,118,255]},'s-spr':{ideas:[32,198,148],artifacts:[245,82,158],sensations:
[252,198,58]},'s-sum':{ideas:[238,162,28],artifacts:[255,102,52],sensations:
[142,222,95]},'s-stn':{ideas:[232,210,172],artifacts:[198,168,128],sensations:
[238,168,148]}};
var currentScheme='s-
fal',currentVariation='v2',currentView='time',currentPage='log';
var activeLayers={ideas:true,artifacts:true,sensations:true},activeRels=
{itself:true,orbit:true};
var CAT_COLORS=SCHEME_CATS['s-fal'];function updateCatColors()
{CAT_COLORS=SCHEME_CATS[currentScheme]||SCHEME_CATS['s-fal'];}
var CV=document.getElementById('cv'),CTX;try{CTX=CV.getContext('2d');}catch(e)
{CTX=null;}
var
VW=0,VH=0,MX=0,MY=0,T=0,hovBubble=-1,hovNode=-1,thermalCache=null,lastCacheKey='',mouseTrail=
[],drawerMode='';
var GRAIN;try{var
_s=512,_c=document.createElement('canvas');_c.width=_c.height=_s;var
_x=_c.getContext('2d');if(_x){var _d=_x.createImageData(_s,_s);for(var
_i=0;_i<_d.data.length;_i+=4){var
_v=Math.random()*255;_d.data[_i]=_d.data[_i+1]=_d.data[_i+2]=_v;_d.data[_i+3]=255;}_x.putImageD
{GRAIN=null;}
var geoReady=false,userLat=0,userLng=0;
function timeAgo(t){var d=(Date.now()-
t)/DAY;if(d<1)return'today';if(d<2)return'yesterday';if(d<7)return
Math.floor(d)+'d ago';if(d<30)return Math.floor(d/7)+'w ago';if(d<365)return
Math.floor(d/30)+'mo ago';return Math.floor(d/365)+'y ago';}
function hashStr(s){var h=0;for(var i=0;i<s.length;i++){h=((h<<5)-
h)+s.charCodeAt(i);h|=0;}return h;}
function getAccRGB(){for(var i=0;i<SCHEMES.length;i++)
{if(SCHEMES[i].id===currentScheme){for(var j=0;j<SCHEMES[i].vars.length;j++)
{if(SCHEMES[i].vars[j].v===currentVariation)return
SCHEMES[i].vars[j].acc;}}}return[192,38,26];}
function getInkRGB(){var v=SVARS[currentScheme+'|'+currentVariation];if(v&&v['--
ink']&&v['--ink'][0]==='#'){var n=parseInt(v['--
ink'].slice(1),16);return[(n>>16)&255,(n>>8)&255,n&255];}return[240,232,216];}
function getRamp(){return RAMPS[currentScheme+'|'+currentVariation]||RAMPS['s-
fal|v2'];}
function thermalColor(t){var s=getRamp().stops;for(var i=0;i<s.length-1;i++)
{if(t<=s[i+1][0]){var f=(t-s[i][0])/(s[i+1][0]-s[i][0]);return[Math.round(s[i][1]
[0]+(s[i+1][1][0]-s[i][1][0])*f),Math.round(s[i][1][1]+(s[i+1][1][1]-s[i][1]
[1])*f),Math.round(s[i][1][2]+(s[i+1][1][2]-s[i][1][2])*f)];}}return s[s.length-1]
[1];}
var BAYER4=[[0,8,2,10],[12,4,14,6],[3,11,1,9],[15,7,13,5]],DITHER_CACHE={};
function getDitherPalette(){var b=getRamp().base;function g(v)
{return[v,v,v];}return[g(b[0]*.5+b[1]*.3+b[2]*.2|0),g(40),g(72),g(110),g(155),g(210)];}
function buildDither(img,w,h){
// Render at 2× then downscale — gives anti-aliased source for crisper dither
var ow=Math.min(w,300),oh=Math.round(h*ow/w);
var src=document.createElement('canvas');src.width=ow;src.height=oh;
var sc=src.getContext('2d');if(!sc)return null;
// Slight contrast/saturation boost before dithering for vivid palette mapping
sc.filter='contrast(1.08) saturate(1.12)';
sc.drawImage(img,0,0,ow,oh);
sc.filter='none';
var id=sc.getImageData(0,0,ow,oh),d=id.data,p=getDitherPalette(),n=p.length;
// 6-color palette uses threshold strength 0.68 (scaled down from 0.78 for 4-
color)
var str=0.68;
for(var y=0;y<oh;y++)for(var x=0;x<ow;x++){
var i=(y*ow+x)*4;
var lm=(d[i]*.299+d[i+1]*.587+d[i+2]*.114)/255;
var th=(BAYER4[y%4][x%4]+.5)/16-.5;
var ix=Math.max(0,Math.min(n-1,Math.round((lm+th*str)*(n-1))));
d[i]=p[ix][0];d[i+1]=p[ix][1];d[i+2]=p[ix][2];d[i+3]=255;
}
sc.putImageData(id,0,0);
return src;
}
function applyScheme(sid,v){currentScheme=sid;currentVariation=v;var
vars=SVARS[sid+'|'+v];if(vars){Object.keys(vars).forEach(function(k)
{document.body.style.setProperty(k,vars[k]);});document.body.style.background=vars['-
-bg'];document.body.style.color=vars['--ink'];var d=document.getElementById('tp-
dot');if(d)d.style.background=vars['--acc'];var cd=document.getElementById('cur-
dot');if(cd)cd.setAttribute('fill',vars['--acc']);var
cr=document.querySelector('#cur circle');if(cr)cr.setAttribute('stroke',vars['--
ink2']);}updateCatColors();thermalCache=null;lastCacheKey='';DITHER_CACHE={};var
sc;SCHEMES.forEach(function(s){if(s.id===sid)sc=s;});var
lbl=document.getElementById('tp-label');if(lbl&&sc)lbl.textContent=sc.num+'.'+
(['v1','v2','v3'].indexOf(v)+1);try{localStorage.setItem('oone_scheme',JSON.stringify({id:sid,v
{}renderThemeGrid();}
function openThemeChooser(){document.getElementById('theme-
chooser').classList.add('on');renderThemeGrid();}
function closeThemeChooser(){document.getElementById('theme-
chooser').classList.remove('on');}
function renderThemeGrid(){
var g=document.getElementById('tc-grid');if(!g)return;
var acc=getAccRGB();
var schRow='<div style="display:flex;gap:10px;justify-content:center;margin-
bottom:14px">'+
SCHEMES.map(function(s){
var sel=(s.id===currentScheme);var rep=s.vars[1]||s.vars[0];
return '<div class="tc-bub'+(sel?' sel':'')+'"
style="background:rgb('+rep.acc+');width:28px;height:28px"
onclick="applyScheme(\''+s.id+'\',\''+rep.v+'\');refreshThemeGridModes()"></div>';
}).join('')+'</div>';
var modeDefs=[{m:'mono',pct:'0%',lbl:'mono'},{m:'duo',pct:'40%',lbl:'duo'},
{m:'multi',pct:'100%',lbl:'multi'}];
var modeRow='<div style="display:flex;gap:16px;justify-content:center">'+
modeDefs.map(function(mo){
var on=galColorMode===mo.m;
var bgStr=mo.m==='mono'?'rgb(88,88,82)':mo.m==='duo'?'linear-
gradient(135deg,rgb('+acc+'),rgb(88,88,82))':multiCircleBg();
return '<div onclick="applyGalMode(\''+mo.m+'\');refreshThemeGridModes()"
style="text-align:center;cursor:pointer;user-select:none">'
+'<div id="tc-mode-circ-'+mo.m+'" style="width:28px;height:28px;border-
radius:50%;background:'+bgStr+';margin:0 auto 5px;border:2px solid
rgba(255,255,255,'+(on?'.65':'.12')+');box-sizing:border-box;transition:border-
color .2s"></div>'
+'<div id="tc-mode-lbl-'+mo.m+'" style="font-family:Space
Mono,monospace;font-size:8px;letter-spacing:.06em;text-
transform:uppercase;color:rgba(255,255,255,'+(on?'.55':'.18')+');line-
height:1.5">'
+'<div>'+mo.pct+'</div><div>'+mo.lbl+'</div></div></div>';
}).join('')+'</div>';
g.innerHTML=schRow+modeRow;
}
function refreshThemeGridModes(){
var acc=getAccRGB();
[{m:'mono'},{m:'duo'},{m:'multi'}].forEach(function(mo){
var c=document.getElementById('tc-mode-circ-
'+mo.m),l=document.getElementById('tc-mode-lbl-'+mo.m);
if(!c)return;
c.style.background=mo.m==='mono'?'rgb(88,88,82)':mo.m==='duo'?'linear-
gradient(135deg,rgb('+acc+'),rgb(88,88,82))':multiCircleBg();
var on=galColorMode===mo.m;
c.style.borderColor=on?'rgba(255,255,255,.65)':'rgba(255,255,255,.12)';
if(l)l.style.color=on?'rgba(255,255,255,.55)':'rgba(255,255,255,.18)';
});
}
function visibleEntries(){return ARCH.entries.filter(function(e){return
activeLayers[e.cat]&&activeRels[e.rel||'itself'];});}
// ── KEY ───────────────────────────────────────────────────────────────────────
var galColorMode='multi';
function applyGalMode(m){galColorMode=m;var iv=document.getElementById('image-
view');if(iv){iv.classList.remove('gal-mode-multi','gal-mode-mono','gal-mode-
duo');iv.classList.add('gal-mode-'+m);}try{var
s=JSON.parse(localStorage.getItem('oone_scheme')||'{}');s.galMode=m;localStorage.setItem('oone_
{}refreshTutModes();refreshThemeGridModes();}
var showFilters={practice:true,play:true};
var galSubFilters={architecture:true,interiors:true,'urban design':true,'print +
digital':true,photography:true};
function setMainView(v){
closeDrawer();
currentPage=v;
document.getElementById('pk-log').classList.toggle('on',v==='log');
document.getElementById('pk-gallery').classList.toggle('on',v==='gallery');
document.getElementById('pk-feed').classList.toggle('on',v==='feed');
var feedMode=v==='feed';
['pk-practice','pk-play'].forEach(function(id){
var row=document.getElementById(id);
if(row)
{row.classList.toggle('dim',feedMode);row.style.pointerEvents=feedMode?'none':'';}
});
if(v==='gallery'){
document.getElementById('image-view').classList.add('on');
document.getElementById('feed-overlay').classList.remove('on');
buildImageView();
CV.style.pointerEvents='none';
} else {
document.getElementById('image-view').classList.remove('on');
}
if(v==='feed'){
document.getElementById('feed-overlay').classList.add('on');
buildFeedOverlay();
CV.style.pointerEvents='none';
} else {
document.getElementById('feed-overlay').classList.remove('on');
}
if(v==='log'){CV.style.pointerEvents='auto';}
updateNav();
renderFilterPanel();
}
function toggleShowFilter(cat){
showFilters[cat]=!showFilters[cat];
document.getElementById('pk-
practice').classList.toggle('on',showFilters.practice);
document.getElementById('pk-play').classList.toggle('on',showFilters.play);
document.getElementById('pk-
practice').classList.toggle('dim',!showFilters.practice);
document.getElementById('pk-play').classList.toggle('dim',!showFilters.play);
thermalCache=null;lastCacheKey='';
if(currentPage==='gallery')rebuildImageView();
}
function toggleTimeSpace(){
var tgl=document.getElementById('pk-timespace');
var isTime=tgl.classList.contains('on');
if(isTime){tgl.classList.remove('on');currentView='space';
if(!geoReady&&navigator.geolocation)navigator.geolocation.getCurrentPosition(function(p)
{userLat=p.coords.latitude;userLng=p.coords.longitude;geoReady=true;},{},{});
}else{tgl.classList.add('on');currentView='time';}
thermalCache=null;lastCacheKey='';
}
function renderFilterPanel(){
var head=document.getElementById('pf-head'),rows=document.getElementById('pf-
rows');
var cc=CAT_COLORS;
if(currentPage==='gallery'){
head.textContent='category';
var cats=['architecture','interiors','urban design','print +
digital','photography'];
rows.innerHTML=cats.map(function(c){var on=galSubFilters[c];return'<div
class="pk-row'+(on?' on':'')+'" onclick="toggleGalSub(\''+c+'\',this)"><div
class="pk-circ" style="'+(on?'background:rgba(255,255,255,.45);border-
color:rgba(255,255,255,.45)':'')+'"></div><span class="pk-lbl">'+c+'</span>
</div>';}).join('');
}else if(currentPage==='feed'){
head.textContent='category';
var fcats=['architecture','interiors','urban design','print +
digital','photography'];
rows.innerHTML=fcats.map(function(c){var
on=!_cosmosCatFilter||_cosmosCatFilter===c;return'<div class="pk-row'+(on?'
on':'')+'" onclick="setCosmosCatPanel(\''+c+'\',this)"><div class="pk-circ"
style="'+(on?'background:rgba(255,255,255,.45);border-
color:rgba(255,255,255,.45)':'')+'"></div><span class="pk-lbl">'+c+'</span>
</div>';}).join('');
}else{
head.textContent='type';
var cats2=[['ideas',cc.ideas],['artifacts',cc.artifacts],
['sensations',cc.sensations]];
rows.innerHTML=cats2.map(function(p){var
c=p[0],rgb=p[1],on=activeLayers[c];return'<div class="pk-row'+(on?' on':'')+'"
onclick="toggleLogCat(\''+c+'\',this)"><div class="pk-circ" style="border-
color:rgb('+rgb+');'+(on?'background:rgb('+rgb+')':'')+'"></div><span class="pk-
lbl">'+c+'</span></div>';}).join('');
}
}
function setCosmosCatPanel(cat,row){
setCosmosCat(cat);
// sync panel row highlights
document.querySelectorAll('#pf-rows .pk-row').forEach(function(r){
var isOn=!_cosmosCatFilter||r.querySelector('.pk-
lbl').textContent===_cosmosCatFilter;
r.classList.toggle('on',isOn);
var circ=r.querySelector('.pk-circ');
if(circ)
{circ.style.background=isOn?'rgba(255,255,255,.45)':'';circ.style.borderColor=isOn?'rgba(255,25
});
}
function toggleLogCat(c,row)
{activeLayers[c]=!activeLayers[c];row.classList.toggle('on');var
circ=row.querySelector('.pk-circ');if(circ){var
rgb=CAT_COLORS[c];if(activeLayers[c])
{circ.style.background='rgb('+rgb+')';circ.style.borderColor='rgb('+rgb+')';}else{circ.style.ba
function toggleGalSub(c,row)
{galSubFilters[c]=!galSubFilters[c];row.classList.toggle('on');var
circ=row.querySelector('.pk-circ');if(circ){if(galSubFilters[c])
{circ.style.background='rgba(255,255,255,.45)';circ.style.borderColor='rgba(255,255,255,.45)';}
// ── BUBBLE POP (water spray + ripple, no accent confetti) ───────────────────
var popParticles=[],popRings=[];
function popBubble(idx){
var a=bubAnim[idx],br=bubR(),cx=a.px,cy=a.py;
popRings.push({x:cx,y:cy,r:0,rMax:br*2.85,life:1});
for(var i=0;i<36;i++){
var ang=(i/36)*Math.PI*2+
(Math.random()-.5)*.55,spd=1.8+Math.random()*5.2,mist=Math.random()<.38;
popParticles.push({
x:cx+(Math.random()-.5)*br*.25,y:cy+(Math.random()-.5)*br*.25,
vx:Math.cos(ang)*spd*(mist?0.65:1),vy:Math.sin(ang)*spd*(mist?0.55:1)-(mist?
0:1.1),
sz:mist?
0.9+Math.random()*1.1:1.3+Math.random()*2.6,life:1,ay:.2+Math.random()*.14,drag:mist?
0.982:0.972,mist:mist
});
}
bubAnim[idx].scaleT=0;
setTimeout(function(){if(bubAnim[idx])bubAnim[idx].scaleT=1;},560);
}
function buildImageView(){var iv=document.getElementById('image-
view');iv.classList.remove('gal-mode-multi','gal-mode-mono','gal-mode-
duo');iv.classList.add('gal-mode-'+galColorMode);var
existing=iv.querySelector('.gal-grid');if(!existing){iv.innerHTML='<div class="iv-
head"><span class="iv-title">gallery</span><button class="iv-log-bub"
onclick="setMainView(\'log\')">LOG</button></div>';var
g=document.createElement('div');g.className='gal-grid';g.id='iv-
grid';iv.appendChild(g);}else{existing.innerHTML='';}var
g2=document.getElementById('iv-
grid');if(g2)fillImageGrid(g2,galSubFilters,showFilters);}
function rebuildImageView(){var g=document.getElementById('iv-
grid');if(g)fillImageGrid(g,galSubFilters,showFilters);}
function fillImageGrid(container,subFilters,showFilters){
container.innerHTML='';
GAL_IMGS.forEach(function(img,idx){
var meta=GAL_META[idx]||{projId:null,cat:'photography',sub:'photography'};
var catOk=!showFilters||(meta.cat==='practice'?
showFilters.practice:showFilters.play);
var subOk=!subFilters||subFilters[meta.sub];
if(!catOk||!subOk)return;
var div=document.createElement('div');
div.className='gal-item';
div.setAttribute('data-idx',idx);
var im=document.createElement('img');
im.src=img.src;
im.alt=img.name||'';
im.loading='lazy';
div.appendChild(im);
var cv=document.createElement('canvas');
div.appendChild(cv);
var lbl=document.createElement('div');
lbl.className='gal-label';
lbl.textContent=meta.projId?PROJECTS[meta.projId].title:(img.name||meta.sub);
div.appendChild(lbl);
div.addEventListener('click',function(){
if(meta.projId)openProject(meta.projId);
});
function applyDither(imgEl,cvEl){try{var ck=
(imgEl.src||'')+'|'+currentScheme+'|'+currentVariation,d=DITHER_CACHE[ck];if(!d)
{d=buildDither(imgEl,imgEl.naturalWidth||imgEl.width,imgEl.naturalHeight||imgEl.height);if(d)DI
{cvEl.width=d.width;cvEl.height=d.height;var
cx=cvEl.getContext('2d');if(cx)cx.drawImage(d,0,0);}}catch(e){}}
im.onload=function(){applyDither(im,cv);};
if(im.complete&&im.naturalWidth)applyDither(im,cv);
container.appendChild(div);
});
}
function findProjectForPhoto(idx){var k=Object.keys(PROJECTS);return idx<k.length?
k[idx]:null;}
// ── POSITIONING ───────────────────────────────────────────────────────────────
function entryPos(e,vis){if(currentView==='space'&&e.lat&&e.lng)return
geoProject(e.lat,e.lng,vis);if(!vis||!vis.length)return[VW*.5,VH*.5];var
mn=vis[0].t,mx=vis[0].t;for(var i=1;i<vis.length;i++)
{if(vis[i].t<mn)mn=vis[i].t;if(vis[i].t>mx)mx=vis[i].t;}mn-=DAY;mx+=DAY;var
xn=.06+((e.t-mn)/(mx-mn))*.88,h=hashStr(e.title||''),yB=
{ideas:.28,artifacts:.52,sensations:.75}[e.cat]||.5,yJ=((h%200)-100)/100*.08,xJ=
((h%300)-150)/300*.025;return[Math.max(.04,Math.min(.96,xn+xJ))*VW,Math.max(.06,Math.min(.94,yB
function geoProject(lat,lng,vis){if(!vis||!vis.length)return[VW*.5,VH*.5];var
mnLa=90,mxLa=-90,mnLn=180,mxLn=-180;vis.forEach(function(e){if(e.lat&&e.lng)
{if(e.lat<mnLa)mnLa=e.lat;if(e.lat>mxLa)mxLa=e.lat;if(e.lng<mnLn)mnLn=e.lng;if(e.lng>mxLn)mxLn=
{mnLa=Math.min(mnLa,userLat);mxLa=Math.max(mxLa,userLat);mnLn=Math.min(mnLn,userLng);mxLn=Math.
dLa=(mxLa-mnLa)||1,dLn=(mxLn-mnLn)||1;mnLa-=dLa*.15;mxLa+=dLa*.15;mnLn-
=dLn*.15;mxLn+=dLn*.15;var x=(.07+((lng-mnLn)/(mxLn-mnLn))*.86)*VW,y=(.07+((mxLa-
lat)/(mxLa-mnLa))*.78)*VH,h=hashStr((lat+'|'+lng).toString());return[x+
((h%60)-30)*.5,y+((h%40)-20)*.5];}
function nodeR(){return Math.max(4,Math.max(VW,VH)/120);}
// ── CANVAS ────────────────────────────────────────────────────────────────────
var bubAnim=[],BUBBLE_DEF=[{label:'ABOUT',cx:.28,cy:.50,phase:0,sub:'who this
is'},{label:'SERVICES',cx:.50,cy:.52,phase:2.1,sub:'what i do'},
{label:'GALLERY',cx:.72,cy:.49,phase:4.2,sub:'the work'}];
var bubIntroEnd=0;
function initBubs(){if(!bubAnim.length)BUBBLE_DEF.forEach(function(b)
{bubAnim.push({px:b.cx*VW,py:b.cy*VH,ox:b.cx*VW,oy:b.cy*VH,phase:b.phase,scale:1,scaleT:1});});
BUBBLE_DEF.forEach(function(b,i){bubAnim[i].ox=b.cx*VW;bubAnim[i].oy=b.cy*VH;});}
function bubR(){return Math.min(VW,VH)*.072;}
function drawBubble(ctx,bx,by,r,acc,iP,hot,mx,my){
// ── Layer 0: Deep ambient scatter ──
ctx.globalCompositeOperation='screen';
var sc=ctx.createRadialGradient(bx,by,r*.1,bx,by,r*3.2);
sc.addColorStop(0,'rgba('+acc+','+(hot?.10:.035)+')');
sc.addColorStop(.5,'rgba('+acc+','+(hot?.028:.008)+')');
sc.addColorStop(1,'rgba('+acc+',0)');
ctx.beginPath();ctx.arc(bx,by,r*3.2,0,Math.PI*2);ctx.fillStyle=sc;ctx.fill();
// ── Layer 1: Glass body interior volume ──
ctx.globalCompositeOperation='screen';
var gv=ctx.createRadialGradient(bx-r*.08,by-r*.06,r*.05,bx,by,r);
gv.addColorStop(0,'rgba(255,255,255,'+(hot?.028:.010)+')');
gv.addColorStop(.55,'rgba(255,255,255,.003)');
gv.addColorStop(1,'rgba(0,0,0,0)');
ctx.beginPath();ctx.arc(bx,by,r,0,Math.PI*2);ctx.fillStyle=gv;ctx.fill();
// ── Layer 2: Caustic glints (glass / water — cool white, not rainbow) ──
ctx.globalCompositeOperation='screen';
for(var si=0;si<12;si++){
var a0=si/12*Math.PI*2+iP*.14,a1=(si+.28)/12*Math.PI*2+iP*.14;
var pulse=(.045+.04*Math.sin(iP*1.35+si*.85))*(hot?1.15:1);
var sg=ctx.createRadialGradient(bx,by,r*.8,bx,by,r);
sg.addColorStop(0,'rgba(255,255,255,0)');
sg.addColorStop(.52,'rgba(255,255,255,'+(pulse*
(hot?.11:.042)).toFixed(4)+')');
sg.addColorStop(.68,'rgba(218,236,255,'+(pulse*
(hot?.055:.022)).toFixed(4)+')');
sg.addColorStop(1,'rgba(255,255,255,0)');
ctx.beginPath();ctx.arc(bx,by,r,a0,a1);ctx.arc(bx,by,r*.8,a1,a0,true);ctx.closePath();
ctx.fillStyle=sg;ctx.fill();
}
// ── Layer 3: Mouse-reactive specular (treats cursor as light source) ──
var dx=mx-bx,dy=my-by,dist=Math.sqrt(dx*dx+dy*dy);
var nx=dist>0?dx/dist:-0.62,ny=dist>0?dy/dist:-0.72;
var falloff=Math.max(0,1-dist/(r*5));
var spX=bx-nx*r*.28,spY=by-ny*r*.32;
var spIntensity=hot?(0.72+falloff*.28):(0.42+falloff*.18);
ctx.globalCompositeOperation='screen';
var sp=ctx.createRadialGradient(spX,spY,0,spX,spY,r*.26);
sp.addColorStop(0,'rgba(255,255,255,'+spIntensity.toFixed(3)+')');
sp.addColorStop(.38,'rgba(255,255,255,'+(spIntensity*.22).toFixed(3)+')');
sp.addColorStop(1,'rgba(255,255,255,0)');
var spAngle=Math.atan2(-ny,-nx);
ctx.beginPath();ctx.ellipse(spX,spY,r*.20,r*.12,spAngle-.5,0,Math.PI*2);
ctx.fillStyle=sp;ctx.fill();
// Secondary micro-highlight (fixed upper-left, always visible)
var sk2=ctx.createRadialGradient(bx-r*.38,by-r*.42,0,bx-r*.38,by-r*.42,r*.10);
sk2.addColorStop(0,'rgba(255,255,255,'+(hot?.36:.18)+')');
sk2.addColorStop(1,'rgba(255,255,255,0)');
ctx.beginPath();ctx.ellipse(bx-r*.38,by-r*.42,r*.08,r*.05,-.4,0,Math.PI*2);
ctx.fillStyle=sk2;ctx.fill();
// ── Layer 4: Bottom caustic (refraction glow beneath sphere) ──
ctx.globalCompositeOperation='screen';
var caus=ctx.createRadialGradient(bx+r*.08,by+r*.6,0,bx,by+r*.5,r*.9);
caus.addColorStop(0,'rgba('+acc+','+(hot?.07:.025)+')');
caus.addColorStop(1,'rgba('+acc+',0)');
ctx.beginPath();ctx.ellipse(bx,by+r*.5,r*.9,r*.35,0,0,Math.PI*2);
ctx.fillStyle=caus;ctx.fill();
// ── Layer 5: Fresnel rim (neutral glass + faint accent echo) ──
ctx.globalCompositeOperation='source-over';
var rimR=hot?(0.34+falloff*.2):(0.15+falloff*.09);
var rimW=hot?1.65:.72;
ctx.beginPath();ctx.arc(bx,by,r,0,Math.PI*2);
var rimGrad=ctx.createLinearGradient(bx-r*.9,by-r*.9,bx+r*.9,by+r*.9);
rimGrad.addColorStop(0,'rgba(255,255,255,'+(rimR*.92).toFixed(3)+')');
rimGrad.addColorStop(.38,'rgba(228,242,255,'+(rimR*.42).toFixed(3)+')');
rimGrad.addColorStop(.55,'rgba('+acc+','+(rimR*.28).toFixed(3)+')');
rimGrad.addColorStop(1,'rgba(255,255,255,'+(rimR*.72).toFixed(3)+')');
ctx.strokeStyle=rimGrad;ctx.lineWidth=rimW;ctx.stroke();
// ── Layer 6: Inner dark ring (depth / thickness of glass) ──
ctx.beginPath();ctx.arc(bx,by,r*.96,0,Math.PI*2);
ctx.strokeStyle='rgba(0,0,0,'+
(hot?.06:.03)+')';ctx.lineWidth=r*.04;ctx.stroke();
ctx.globalCompositeOperation='source-over';
}
function drawBubbles(){
var br=bubR(),acc=getAccRGB(),ink=getInkRGB();
bubAnim.forEach(function(a,i){
// Smooth float — layered sine for organic feel
var fx=Math.sin(T*.13+a.phase)*.5+Math.sin(T*.07+a.phase*1.3)*.22;
var fy=Math.cos(T*.10+a.phase*.8)*.4+Math.cos(T*.06+a.phase*1.1)*.18;
a.px+=fx; a.py+=fy;
// Magnetic cursor pull when nearby
var cdx=MX-a.ox,cdy=MY-a.oy,cd=Math.sqrt(cdx*cdx+cdy*cdy);
var pull=Math.max(0,1-cd/(br*4.5));
a.px+=cdx*pull*.018; a.py+=cdy*pull*.018;
// Spring back to origin
a.px=a.px*.9978+a.ox*.0022; a.py=a.py*.9978+a.oy*.0022;
// Scale spring — quicker ease when collapsing, softer reinflate
var spr=a.scaleT===0?0.12:(a.scale<0.25?0.045:0.058);
a.scale+=(a.scaleT-a.scale)*spr;
var hot=(hovBubble===i);
if(a.scaleT!==0)a.scaleT=hot?1.12:1;
var r=br*a.scale,bx=a.px,by=a.py,iP=T*.28+a.phase;
CTX.save();
if(r>0.8)drawBubble(CTX,bx,by,r,acc,iP,hot,MX,MY);
// Label
var fSz=Math.round(r*.21);
CTX.font='300 italic '+fSz+'px "Cormorant Garamond",serif';
CTX.textAlign='center';CTX.textBaseline='middle';
CTX.globalCompositeOperation='source-over';
// Subtle text shadow for depth
CTX.shadowColor='rgba(0,0,0,.55)';CTX.shadowBlur=hot?12:6;
CTX.globalAlpha=hot?.78:.38;
CTX.fillStyle='rgb('+ink+')';
CTX.fillText(BUBBLE_DEF[i].label,bx,by);
CTX.shadowBlur=0;
CTX.restore();
});
}
function buildThermal(){if(!CTX)return null;var
vis=visibleEntries(),now=Date.now(),SC=4,SW=Math.ceil(VW/SC),SH=Math.ceil(VH/SC);var
o=document.createElement('canvas');o.width=SW;o.height=SH;var
ox=o.getContext('2d');if(!ox)return
null;ox.clearRect(0,0,SW,SH);ox.globalCompositeOperation='screen';vis.forEach(function(e)
{var pos=entryPos(e,vis),ex=pos[0]/SC,ey=pos[1]/SC,nr=nodeR()/SC,age=(now-
e.t)/DAY,rec=Math.exp(-age/22);var c0=thermalColor(.12);var
g0=ox.createRadialGradient(ex,ey,0,ex,ey,nr*36);g0.addColorStop(0,'rgba('+c0+','+
(.11+rec*.09)+')');g0.addColorStop(.45,'rgba('+c0+','+
((.11+rec*.09)*.3)+')');g0.addColorStop(1,'rgba('+c0+',0)');ox.beginPath();ox.arc(ex,ey,nr*36,0
c1=thermalColor(.45);var
g1=ox.createRadialGradient(ex,ey,0,ex,ey,nr*18);g1.addColorStop(0,'rgba('+c1+','+
(.26+rec*.2)+')');g1.addColorStop(.4,'rgba('+c1+','+
((.26+rec*.2)*.28)+')');g1.addColorStop(1,'rgba('+c1+',0)');ox.beginPath();ox.arc(ex,ey,nr*18,0
o;}
function drawField(){
if(!CTX)return;
if(currentPage!=='log'){CTX.clearRect(0,0,VW,VH);return;}
var
ck=currentScheme+'|'+currentVariation+'|'+currentView+'|'+JSON.stringify(activeLayers)+JSON.str
if(ck!==lastCacheKey){thermalCache=buildThermal();lastCacheKey=ck;}
CTX.clearRect(0,0,VW,VH);
// Atmospheric thermal — soft blur makes it feel organic, not computed
if(thermalCache){
CTX.save();
CTX.filter='blur(7px)';
CTX.globalAlpha=.88;
CTX.drawImage(thermalCache,0,0,VW,VH);
CTX.filter='none';
CTX.restore();
}
// ── Velocity-based mouse trail ──
var acc=getAccRGB();
if(mouseTrail.length>1){
// Glow circles (radius scales with speed)
CTX.globalCompositeOperation='screen';
mouseTrail.forEach(function(mt){
var spd=mt[3]||0, r=Math.max(44,Math.min(115,50+spd*3.8));
var mg=CTX.createRadialGradient(mt[0],mt[1],0,mt[0],mt[1],r);
mg.addColorStop(0,'rgba('+acc+','+(mt[2]*(0.042+spd*.0008)).toFixed(4)+')');
mg.addColorStop(.38,'rgba('+acc+','+(mt[2]*0.010).toFixed(4)+')');
mg.addColorStop(1,'rgba('+acc+',0)');
CTX.beginPath();CTX.arc(mt[0],mt[1],r,0,Math.PI*2);
CTX.fillStyle=mg;CTX.fill();
});
// Bézier spine through trail points for silky thread
CTX.globalCompositeOperation='lighter';
CTX.beginPath();
CTX.moveTo(mouseTrail[0][0],mouseTrail[0][1]);
for(var ti=1;ti<mouseTrail.length-1;ti++){
var mx2=(mouseTrail[ti][0]+mouseTrail[ti+1][0])*.5;
var my2=(mouseTrail[ti][1]+mouseTrail[ti+1][1])*.5;
CTX.quadraticCurveTo(mouseTrail[ti][0],mouseTrail[ti][1],mx2,my2);
}
var lt=mouseTrail[mouseTrail.length-1];
CTX.lineTo(lt[0],lt[1]);
CTX.strokeStyle='rgba('+acc+',.055)';
CTX.lineWidth=1.2;
CTX.stroke();
CTX.globalCompositeOperation='source-over';
}
// Film grain overlay
if(GRAIN)
{CTX.save();CTX.globalAlpha=.010;CTX.globalCompositeOperation='overlay';CTX.drawImage(GRAIN,0,0
// Entry nodes
var vis=visibleEntries();
ARCH.entries.forEach(function(e,ei){
if(!activeLayers[e.cat]||!activeRels[e.rel||'itself'])return;
var pos=entryPos(e,vis),ex=pos[0],ey=pos[1],nr=nodeR(),hot=
(hovNode===ei),cc=CAT_COLORS[e.cat]||[192,98,42],cs='rgb('+cc+')';
CTX.save();
if(hot){
// Hovered node glow
var ng=CTX.createRadialGradient(ex,ey,0,ex,ey,nr*3.5);
ng.addColorStop(0,'rgba('+cc+',.22)');ng.addColorStop(1,'rgba('+cc+',0)');
CTX.globalCompositeOperation='screen';
CTX.beginPath();CTX.arc(ex,ey,nr*3.5,0,Math.PI*2);CTX.fillStyle=ng;CTX.fill();
CTX.globalCompositeOperation='source-over';
}
if((e.rel||'itself')==='itself'){
CTX.globalAlpha=hot?.88:.40;CTX.fillStyle=cs;
CTX.beginPath();CTX.arc(ex,ey,hot?5:3,0,Math.PI*2);CTX.fill();
}else{
CTX.globalAlpha=hot?.60:.22;CTX.strokeStyle=cs;CTX.lineWidth=hot?.9:.4;
CTX.beginPath();CTX.arc(ex,ey,nr*1.2,0,Math.PI*2);CTX.stroke();
CTX.globalAlpha=hot?.70:.30;CTX.fillStyle=cs;
CTX.beginPath();CTX.arc(ex,ey,hot?3:1.8,0,Math.PI*2);CTX.fill();
}
});
CTX.restore();
}
function resize(){if(!CV||!CTX)return;var
dpr=window.devicePixelRatio||1;VW=window.innerWidth;VH=window.innerHeight;CV.width=Math.round(V
window.addEventListener('resize',resize);
// ── INTERACTION ───────────────────────────────────────────────────────────────
function hitBubble(mx,my){var br=bubR();for(var i=0;i<bubAnim.length;i++){var
dx=mx-bubAnim[i].px,dy=my-bubAnim[i].py;if(Math.sqrt(dx*dx+dy*dy)<br*1.1)return
i;}return-1;}
function hitNode(mx,my){var
vis=visibleEntries(),best=-1,bestD=28;ARCH.entries.forEach(function(e,i)
{if(!activeLayers[e.cat]||!activeRels[e.rel||'itself'])return;var
pos=entryPos(e,vis),dx=mx-pos[0],dy=my-pos[1],d=Math.sqrt(dx*dx+dy*dy);if(d<bestD)
{bestD=d;best=i;}});return best;}
var _pMX=0,_pMY=0,_MVX=0,_MVY=0;
CV.addEventListener('mousemove',function(ev){
_MVX=ev.clientX-_pMX;_MVY=ev.clientY-_pMY;
_pMX=MX=ev.clientX;_pMY=MY=ev.clientY;
var spd=Math.sqrt(_MVX*_MVX+_MVY*_MVY);
// Magnetic cursor snap toward nearest bubble
var cur=document.getElementById('cur');
if(cur){
var br=bubR(),magX=MX,magY=MY;
bubAnim.forEach(function(a){
var dx=MX-a.px,dy=MY-a.py,d=Math.sqrt(dx*dx+dy*dy);
var pull=Math.max(0,1-d/(br*3.2))*.14;
magX+=( a.px-MX)*pull;magY+=(a.py-MY)*pull;
});
cur.style.left=magX+'px';cur.style.top=magY+'px';
}
mouseTrail.push([MX,MY,1,spd]);if(mouseTrail.length>38)mouseTrail.shift();hovBubble=hitBubble(M
tip=document.getElementById('tip');if(hovNode>=0){var
e=ARCH.entries[hovNode],vis=visibleEntries(),pos=entryPos(e,vis),cc=CAT_COLORS[e.cat]||
[192,38,26];document.getElementById('tip-
cat').textContent=e.cat;document.getElementById('tip-
cat').style.color='rgb('+cc+')';document.getElementById('tip-
title').textContent=e.title;document.getElementById('tip-
sub').textContent=e.sub||'';document.getElementById('tip-
time').textContent=timeAgo(e.t)+(e.place?' \u00b7
'+e.place:'');tip.classList.add('on');tip.style.left=Math.min(pos[0]+14,VW-
250)+'px';tip.style.top=(pos[1]-65)+'px';}else
tip.classList.remove('on');bubAnim.forEach(function(a,i){if(a.scaleT!==0)a.scaleT=
(hovBubble===i)?1.1:1;});});
CV.addEventListener('click',function(){if(hovBubble>=0)
{popBubble(hovBubble);if(hovBubble===0)setTimeout(function()
{navTo('about');},200);else if(hovBubble===1)setTimeout(function()
{navTo('services');},200);else if(hovBubble===2)setTimeout(function()
{setMainView('gallery');},200);}else if(hovNode>=0){var
e=ARCH.entries[hovNode];if(e.id&&PROJECTS[e.id])openProject(e.id);else
openEntryDrawer(hovNode);}});
CV.addEventListener('touchstart',function(ev){var
t=ev.touches[0];MX=t.clientX;MY=t.clientY;hovBubble=hitBubble(MX,MY);hovNode=hitNode(MX,MY);if
{ev.preventDefault();popBubble(hovBubble);var hb=hovBubble;setTimeout(function()
{[function(){navTo('about');},function(){navTo('services');},function()
{setMainView('gallery');}][hb]();},200);}else if(hovNode>=0)
{ev.preventDefault();var
e=ARCH.entries[hovNode];if(e.id&&PROJECTS[e.id])openProject(e.id);else
openEntryDrawer(hovNode);}},{passive:false});
// ── NAV ───────────────────────────────────────────────────────────────────────
function goHome(){closeDrawer();setMainView('log');}
function navTo(page){
// Toggle: clicking the active tab closes the drawer
if(drawerMode && currentPage===page)
{closeDrawer();currentPage='';updateNav();return;}
currentPage=page;updateNav();
document.getElementById('image-view').classList.remove('on');
if(page==='about')openAbout();else if(page==='services')openServices();else
if(page==='log')openLog();
}
function updateNav(){
document.querySelectorAll('#nav .nav-link').forEach(function(l)
{l.classList.remove('on');});
var links=document.querySelectorAll('#nav .nav-links > .nav-link, #nav .nav-drop
.nav-link');
if(currentPage==='about'&&links[0])links[0].classList.add('on');
if(currentPage==='services'&&links[1])links[1].classList.add('on');
// "View" dropdown (links[2]) highlights for log, gallery, feed
if((currentPage==='log'||currentPage==='gallery'||currentPage==='feed')&&links[2])links[2].clas
}
function toggleLogDrop(ev){ev.stopPropagation();document.getElementById('nav-log-
drop').classList.toggle('open');}
function closeLogDrop(){document.getElementById('nav-log-
drop').classList.remove('open');}
document.addEventListener('click',function(){closeLogDrop();});
// ── DRAWERS ───────────────────────────────────────────────────────────────────
function primeDwBodyAnim(){
var b=document.getElementById('dw-body');
if(!b)return;
b.querySelectorAll('.oone-peek').forEach(function(n){n.classList.remove('oone-
peek','oone-serif-drift');n.style.removeProperty('--od');});
var pick=[],seen=new Set();
function add(n){if(n&&n.nodeType===1&&!seen.has(n)){seen.add(n);pick.push(n);}}
b.querySelectorAll(':scope > *').forEach(add);
b.querySelectorAll('.about-wrap > *').forEach(add);
b.querySelectorAll('.about-wrap > div:first-child > *').forEach(add);
b.querySelectorAll('.about-wrap > div:last-child > *').forEach(add);
b.querySelectorAll('.svc-grid > .svc').forEach(add);
b.querySelectorAll('.contact').forEach(add);
b.querySelectorAll('.proj-eyebrow, .proj-title, .proj-tag, .proj-desc, .proj-
facts, .proj-img-col').forEach(add);
b.querySelectorAll('.log-tabs').forEach(add);
b.querySelectorAll('.log-panel.on > *').forEach(add);
pick.forEach(function(n,i){
n.classList.add('oone-peek');
if(n.matches&&n.matches('.about-name, .svc-name, .contact-title, .proj-
title'))n.classList.add('oone-serif-drift');
n.style.setProperty('--od',(0.02+Math.min(i,16)*0.048)+'s');
});
b.classList.remove('oone-stag');
void b.offsetWidth;
b.classList.add('oone-stag');
}
function openDrawer(label,fn){
var d=document.getElementById('drawer');
var alreadyOpen=d.classList.contains('open');
document.getElementById('dw-cat').textContent=label;
var b=document.getElementById('dw-body');b.innerHTML='';
document.getElementById('dw-expand-btn').textContent='expand';
d.classList.remove('expanded');
if(typeof fn==='function')fn(b);else b.innerHTML=fn;
d.classList.add('open');document.body.classList.add('drawer-
open');drawerMode=label;
requestAnimationFrame(function(){requestAnimationFrame(primeDwBodyAnim);});
if(window._fm){
if(!alreadyOpen){
// Slide up from bottom
window._fm.animate(d,{y:['100%','0%']},
{type:'spring',stiffness:320,damping:32,mass:.9});
} else {
// Already open — crossfade content only, no slide
window._fm.animate(b,{opacity:[0,1]},{duration:.22,ease:[.16,1,.3,1]});
}
}
}
function toggleDrawerExpand(){var
d=document.getElementById('drawer');if(d.classList.contains('expanded'))
{closeDrawer();}else{d.classList.add('expanded');document.getElementById('dw-
expand-btn').textContent='return';if(window._fm){window._fm.animate(d,{height:
['50vh','100dvh']},{type:'spring',stiffness:260,damping:30,mass:.9});}}}
function closeDrawer(){var
d=document.getElementById('drawer');document.body.classList.remove('drawer-
open');drawerMode='';updateNav();if(window._fm){window._fm.animate(d,{y:
['0%','100%']},
{type:'spring',stiffness:380,damping:36,mass:.8,onComplete:function()
{d.classList.remove('open','expanded');}});}else{d.classList.remove('open','expanded');}}
function openProject(id){var p=PROJECTS[id];if(!p)return;
var projImgs=GAL_META.map(function(m,i){return m.projId===id?
i:-1;}).filter(function(i){return i>=0;});
openDrawer(p.title,function(b){
var w=document.createElement('div');
var firstImg=projImgs.length>0?'<img src="'+GAL_IMGS[projImgs[0]].src+'"
alt="'+p.title+'">' :'<div style="width:100%;height:100%;display:flex;align-
items:center;justify-content:center;color:rgba(255,255,255,.12);font-family:Space
Mono,monospace;font-size:9px;letter-spacing:.12em">NO IMAGE</div>';
var expandBtn=projImgs.length>1?'<button class="proj-img-expand"
onclick="toggleProjImgs(this)">+'+( projImgs.length-1)+' more</button>':'';
var extraImgs=projImgs.slice(1).map(function(i){return'<img class="proj-extra-
img" src="'+GAL_IMGS[i].src+'" alt="">';}).join('');
var extraSection=projImgs.length>1?'<div class="proj-extra-imgs" id="proj-
extra-'+id+'">'+extraImgs+'</div>':'';
w.innerHTML='<div class="proj-layout"><div class="proj-img-
col">'+firstImg+expandBtn+'</div>'
+'<div class="proj-info-col"><div class="proj-eyebrow">'+
(p.galSub||p.galCat||'')+'</div><div class="proj-title">'+p.title+'</div><div
class="proj-tag">'+p.tag+'</div>'
+'<div class="proj-desc">'+p.desc+'</div>'
+'<div class="proj-facts">'+p.facts.map(function(f){return'<div class="proj-
fact"><span class="proj-fk">'+f[0]+'</span><span class="proj-fv">'+f[1]+'</span>
</div>';}).join('')+'</div>'
+'</div></div>'+extraSection;
b.appendChild(w);
setTimeout(function(){
var dw=document.getElementById('drawer');
if(dw&&!dw.classList.contains('expanded'))dw.classList.add('expanded');
},350);
});
}
function toggleProjImgs(btn){var id=btn.closest('.dw-body').querySelector('.proj-
extra-
imgs');if(!id)return;id.classList.toggle('open');btn.textContent=id.classList.contains('open')?
collapse':btn.textContent;}
function openEntryDrawer(idx){var
e=ARCH.entries[idx];if(!e)return;openDrawer(e.cat,function(b){b.innerHTML='<div
style="font-family:Cormorant,serif;font-style:italic;font-size:var(--fs-
xl);color:rgba(255,255,255,.85);margin-bottom:10px">'+e.title+'</div>'+
(e.sub?'<div style="font-family:Cormorant,serif;font-size:var(--fs-
md);color:rgba(255,255,255,.38);margin-bottom:10px">'+e.sub+'</div>':'')+'<div
style="font-family:Space Mono,monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.20)">'+timeAgo(e.t)+(e.place?' \u00b7 '+e.place:'')+'
\u00b7 '+(e.rel||'itself')+'</div>';});}
function openAbout(){openDrawer('about',function(b){var
w=document.createElement('div');w.className='about-wrap';var
left=document.createElement('div');left.innerHTML='<div class="about-name">Josh
Harrison</div><p class="about-bio"><strong>Designer at Wesley Moon Inc.</strong>
Based in Brooklyn. I care about edges, thresholds, and the moment a room becomes a
feeling.</p><p class="about-bio">My work moves between scales \u2014 development
strategy down to mosaic detailing \u2014 but the question is always the same: how
does this shape attention?</p>';var
tb=document.createElement('button');tb.className='cv-toggle';tb.textContent='see
full cv';var cp=document.createElement('div');cp.className='cv-
panel';tb.onclick=function(){var
o=cp.classList.toggle('open');tb.textContent=o?'collapse cv':'see full
cv';};left.appendChild(tb);var
ci=document.createElement('div');ci.style.paddingTop='14px';ci.innerHTML='<div
class="cv-sec-title">experience</div><div style="margin-bottom:10px"><span
class="cv-role-title">Designer</span><span class="cv-role-
date">2024\u2013present</span><div class="cv-role-org">Wesley Moon Inc. \u00b7 New
York, NY</div><div class="cv-role-desc">100% DD for ski compound interiors, cellar
floor spa, Upper East Side. Custom millwork and mosaic detailing.</div></div><div
style="margin-bottom:10px"><span class="cv-role-title">Designer</span><span
class="cv-role-date">2022\u20132024</span><div class="cv-role-org">Hart Howerton
\u00b7 New York, NY</div><div class="cv-role-desc">High-end residential and
hospitality as Design Architect and AOR.</div></div><div style="margin-
bottom:10px"><span class="cv-role-title">Architecture Coordinator</span><span
class="cv-role-date">2017\u20132020</span><div class="cv-role-org">Bedrock \u00b7
Detroit, MI</div></div><div style="margin-bottom:10px"><span class="cv-role-
title">Fellowship</span><span class="cv-role-date">2017\u20132019</span><div
class="cv-role-org">Venture for America</div></div><div class="cv-sec-
title">education</div><div style="margin-bottom:10px"><span class="cv-role-
title">Master of Architecture</span><span class="cv-role-
date">2020\u20132022</span><div class="cv-role-org">University of Virginia</div>
</div><div style="margin-bottom:10px"><span class="cv-role-title">B.S.
Architecture + B.A. American Studies</span><span class="cv-role-
date">2013\u20132017</span><div class="cv-role-org">University of Virginia</div>
</div><div class="cv-sec-title">tools</div><div class="skills"><span
class="skill">AutoCAD</span><span class="skill">Rhino</span><span
class="skill">Revit</span><span class="skill">SketchUp</span><span
class="skill">Adobe CS</span><span class="skill">Bluebeam</span><span
class="skill">VRay</span><span class="skill">Grasshopper</span>
</div>';cp.appendChild(ci);left.appendChild(cp);var
div=document.createElement('hr');div.className='dw-
divider';left.appendChild(div);var
brand=document.createElement('div');brand.innerHTML='<div class="brand-lbl">about
this site</div><div class="brand-name"><span class="oo-word" style="font-
size:inherit;color:inherit"><span class="oo-mark"><span class="o1">O</span><span
class="o2">O</span></span>ne</span></div><p class="brand-p"><em>In itself, in
orbit.</em></p><p class="brand-p"><em>Itself</em> is work I\u2019m putting into
the world \u2014 built, proposed, projected. A solid dot marks it.</p><p
class="brand-p"><em>Orbit</em> is work that inspires \u2014 books half-read, rooms
half-remembered, songs that keep coming back. A target ring marks them.
</p>';left.appendChild(brand);var
right=document.createElement('div');right.innerHTML='<div class="stat-n">05</div>
<div class="stat-l">built works 2017\u2013present</div><div class="stat-
n">04</div><div class="stat-l">cities of practice</div><div class="dw-facts"
style="margin-top:16px"><div class="dw-fact"><span class="dw-fk">current</span>
<span class="dw-fv">Wesley Moon Inc.</span></div><div class="dw-fact"><span
class="dw-fk">previous</span><span class="dw-fv">Hart Howerton \u00b7
Bedrock</span></div><div class="dw-fact"><span class="dw-fk">education</span><span
class="dw-fv">M.Arch, UVA</span></div><div class="dw-fact"><span class="dw-
fk">based</span><span class="dw-fv">Brooklyn, NY</span></div><div class="dw-fact">
<span class="dw-fk">email</span><span class="dw-fv">harrisonjt95@gmail.com</span>
</div></div>';w.appendChild(left);w.appendChild(right);b.appendChild(w);var
acc=SVARS[currentScheme+'|'+currentVariation];if(acc)w.querySelectorAll('.stat-
n').forEach(function(el){el.style.color=acc['--acc'];});});}
function openServices(){openDrawer('services',function(b){var
g=document.createElement('div');g.className='svc-grid';g.innerHTML='<div
class="svc"><div class="svc-name">Architecture</div><div class="svc-
desc">Schematic design, massing studies, space planning, and design development
for residential and hospitality projects.</div><div class="svc-rate">Pricing
available on request</div><div class="svc-ex">e.g. Stargazer Compound \u00b7
Troubadour Club</div></div><div class="svc"><div class="svc-name">Interiors</div>
<div class="svc-desc">Full-scope interior design from concept through construction
documentation. Material palettes, custom millwork, finish integration.</div><div
class="svc-rate">Pricing available on request</div><div class="svc-ex">e.g. Cellar
Spa \u00b7 Covert Ranch</div></div><div class="svc"><div class="svc-name">Urban
Design</div><div class="svc-desc">Development strategy, entitlement support,
consultant coordination, and owner\u2019s representation at the district scale.
</div><div class="svc-rate">Pricing available on request</div><div class="svc-
ex">e.g. Bedrock Detroit \u00b7 Housing Dual Neighbors</div></div><div
class="svc"><div class="svc-name">Print + Digital Media</div><div class="svc-
desc">Design identity, spatial storytelling, creative direction, and visual
communication across print and digital formats.</div><div class="svc-rate">Pricing
available on request</div></div><div class="svc"><div class="svc-
name">Photography</div><div class="svc-desc">Architectural, spatial, and
documentary photography. Film and digital.</div><div class="svc-rate">Pricing
available on request</div></div>';b.appendChild(g);var
c=document.createElement('div');c.className='contact';c.innerHTML='<div
class="contact-title">Get in touch</div><input class="dw-input" id="sn"
placeholder="name"><input class="dw-input" id="se" placeholder="email"><textarea
class="dw-textarea" id="sm" placeholder="tell me about your project">
</textarea>';var send=document.createElement('button');send.className='dw-
send';send.textContent='send';send.onclick=function(){var
n=document.getElementById('sn').value.trim(),e2=document.getElementById('se').value.trim(),m=do
{send.textContent='fill all fields';setTimeout(function()
{send.textContent='send';},1500);return;}window.location.href='mailto:harrisonjt95@gmail.com?
subject='+encodeURIComponent('Inquiry from
'+n)+'&body='+encodeURIComponent(m+'\n\n\u2014
'+n+'\n'+e2);};c.appendChild(send);b.appendChild(c);});}
function makeLogTabs(b,activeTab){
var tabs=document.createElement('div');tabs.className='log-tabs';
var tL=document.createElement('button');tL.className='log-tab'+
(activeTab==='entries'?' on':'');tL.textContent='entries';
var tG=document.createElement('button');tG.className='log-tab'+
(activeTab==='gallery'?' on':'');tG.textContent='gallery';
var tF=document.createElement('button');tF.className='log-tab'+
(activeTab==='feed'?' on':'');tF.textContent='feed';
var pL=document.createElement('div');pL.className='log-panel'+
(activeTab==='entries'?' on':'');
var pG=document.createElement('div');pG.className='log-panel'+
(activeTab==='gallery'?' on':'');
var pF=document.createElement('div');pF.className='log-panel'+
(activeTab==='feed'?' on':'');
function activate(t){[tL,tG,tF].forEach(function(x)
{x.classList.remove('on');});t.classList.add('on');[pL,pG,pF].forEach(function(x)
{x.classList.remove('on');});}
tL.onclick=function(){activate(tL);pL.classList.add('on');};
tG.onclick=function(){activate(tG);pG.classList.add('on');buildLogGallery(pG);};
tF.onclick=function(){activate(tF);pF.classList.add('on');buildFeed(pF);};
tabs.appendChild(tL);tabs.appendChild(tG);tabs.appendChild(tF);
buildLogPanel(pL);
if(activeTab==='gallery')buildLogGallery(pG);
if(activeTab==='feed')buildFeed(pF);
b.appendChild(tabs);b.appendChild(pL);b.appendChild(pG);b.appendChild(pF);
}
function openLog(){openDrawer('log',function(b)
{makeLogTabs(b,'entries');});currentPage='log';updateNav();}
function openLogGallery(){openDrawer('log',function(b)
{makeLogTabs(b,'gallery');});currentPage='log';updateNav();}
// ── FEED ──────────────────────────────────────────────────────────────────────
function buildFeed(wrap){
if(wrap.querySelector('.cosmos-feed'))return;
wrap.innerHTML='';
var filterRow=document.createElement('div');filterRow.className='gal-filters';
['architecture','interiors','urban design','print +
digital','photography'].forEach(function(c){
var btn=document.createElement('button');
btn.className='lcbt cosmos-cat-btn';
btn.setAttribute('data-cat',c);
btn.textContent=c;
btn.onclick=function(){setCosmosCat(c);};
filterRow.appendChild(btn);
});
wrap.appendChild(filterRow);
var gridWrap=document.createElement('div');gridWrap.className='arena-grid-wrap
cosmos-feed';
var grid=document.createElement('div');grid.className='arena-
grid';grid.id='arena-grid';
grid.innerHTML='<div class="feed-loading">loading\u2026</div>';
gridWrap.appendChild(grid);
wrap.appendChild(gridWrap);
_cosmosCatFilter='';
loadAllCosmos();
}
function buildFeedOverlay(){
var ticker=document.getElementById('feed-ticker');
if(!ticker)return;
if(ticker.childElementCount>0)return;
ticker.innerHTML='<span style="font-family:Space Mono,monospace;font-
size:9px;letter-spacing:.14em;color:rgba(255,255,255,.18);align-
self:center;padding:0 20px">loading\u2026</span>';
var allImgs=[];
var loaded=0;
COSMOS_BOARDS.forEach(function(board){
fetchCosmos(board.id,function(imgs){
imgs.forEach(function(img){allImgs.push(img);});
loaded++;
if(loaded===COSMOS_BOARDS.length){
if(!allImgs.length){ticker.innerHTML='';return;}
var doubled=allImgs.concat(allImgs);
ticker.innerHTML='';
doubled.forEach(function(b){
var imgEl=document.createElement('img');
imgEl.src=b.image.url+'?w=600';
imgEl.loading='lazy';
imgEl.alt='';
ticker.appendChild(imgEl);
});
}
});
});
}
function loadFeed(grid){
grid.innerHTML='<div class="feed-loading">loading\u2026</div>';
if(feedSource==='arena'){
if(feedCache){renderArenaFeed(grid,feedCache);return;}
fetch(ARENA_API+'/users/'+ARENA_USER+'/channels?per=8')
.then(function(r){if(!r.ok)throw new Error(r.status);return r.json();})
.then(function(data){
var channels=data.channels||data||[];
if(!channels.length){
grid.innerHTML='<div class="feed-empty">No public channels found.<br><span
style="font-family:Space Mono,monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.18);display:block;margin-top:8px">Make sure your
Are.na channels are set to "public" visibility.</span></div>';
return;
}
var loaded=0,allBlocks=[];
channels.slice(0,6).forEach(function(ch){
fetch(ARENA_API+'/channels/'+ch.slug+'/contents?per=12')
.then(function(r){return r.ok?r.json():null;})
.then(function(d){
if(d){var blocks=d.contents||d||[];blocks.forEach(function(bl)
{bl._channel=ch.title;allBlocks.push(bl);});}
loaded++;
if(loaded>=Math.min(channels.length,6)){
allBlocks.sort(function(a,b){return new
Date(b.updated_at||b.created_at)-new Date(a.updated_at||a.created_at);});
feedCache=allBlocks;
renderArenaFeed(grid,allBlocks);
}
}).catch(function()
{loaded++;if(loaded>=Math.min(channels.length,6)&&allBlocks.length)
{feedCache=allBlocks;renderArenaFeed(grid,allBlocks);}});
});
})
.catch(function(err){
grid.innerHTML='<div class="feed-empty">Could not load Are.na<br><span
style="font-family:Space Mono,monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.18);display:block;margin-top:8px">Error:
'+err.message+'<br>Your channels may be set to "closed" or "private".<br>Change
them to "public" in Are.na settings.</span><br><a
href="https://www.are.na/'+ARENA_USER+'" target="_blank" rel="noopener"
style="font-family:Space Mono,monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.30);border-bottom:1px solid
rgba(255,255,255,.10);margin-top:12px;display:inline-block">view profile on are.na
\u2192</a></div>';
});
}else{
grid.innerHTML='<div class="feed-empty" style="padding:30px 0"><div
style="margin-bottom:10px">Pinterest doesn\u2019t offer a public API.</div><a
href="https://pin.it/JzITXV9ok" target="_blank" rel="noopener" style="font-
family:Space Mono,monospace;font-size:var(--fs-
xs);color:rgba(255,255,255,.35);border-bottom:1px solid
rgba(255,255,255,.10)">view board on pinterest \u2192</a></div>';
}
}
function renderArenaFeed(grid,blocks){
grid.innerHTML='';
blocks.forEach(function(bl){
var card=document.createElement('div');card.className='feed-card';
if(bl.image&&bl.image.display&&bl.image.display.url){
var
img=document.createElement('img');img.src=bl.image.display.url;img.loading='lazy';img.alt=bl.ti
}
var body=document.createElement('div');body.className='feed-card-body';
if(bl.title&&bl.title!==bl.source&&bl.title!==''){var
t=document.createElement('div');t.className='feed-card-
title';t.textContent=bl.title;body.appendChild(t);}
if(bl.content_html&&bl.class==='Text'){var
tx=document.createElement('div');tx.className='feed-card-
text';tx.innerHTML=bl.content_html.substring(0,200);body.appendChild(tx);}
if(bl.source&&bl.source.url){var
a=document.createElement('a');a.href=bl.source.url;a.target='_blank';a.rel='noopener';a.textCon
var meta=document.createElement('div');meta.className='feed-card-
meta';meta.textContent=bl._channel||'';body.appendChild(meta);
card.appendChild(body);grid.appendChild(card);
});
if(!blocks.length)grid.innerHTML='<div class="feed-empty">no blocks
found</div>';
}
function buildLogPanel(w){var
inner=document.createElement('div');inner.className='log-inner';var aC='ideas';var
rd=document.createElement('div');rd.className='btn-row';
['ideas','artifacts','sensations'].forEach(function(c){var
btn=document.createElement('button');btn.className='lcbt'+(c==='ideas'?'
on':'');btn.textContent=c;btn.onclick=function()
{rd.querySelectorAll('.lcbt').forEach(function(x)
{x.classList.remove('on');});btn.classList.add('on');aC=c;};rd.appendChild(btn);});var
ti=document.createElement('input');ti.className='log-input';ti.placeholder='what
did you notice?';var subRow=document.createElement('div');subRow.className='log-
sub';var sub=document.createElement('input');sub.className='log-
lis';sub.placeholder='subtitle / source';var
go=document.createElement('button');go.className='log-
go';go.textContent='log';go.onclick=function()
{if(!ti.value.trim())return;ARCH.entries.push({cat:aC,rel:'itself',title:ti.value.trim(),sub:su
recent=document.createElement('div');recent.className='recent';renderRecent(recent);
[rd,ti,subRow,recent].forEach(function(el)
{inner.appendChild(el);});w.appendChild(inner);}
function renderRecent(el){el.innerHTML='';ARCH.entries.slice().sort(function(a,b)
{return b.t-a.t;}).slice(0,10).forEach(function(e){var cc=CAT_COLORS[e.cat]||
[192,38,26];var
d=document.createElement('div');d.className='re';d.style.display='flex';d.style.gap='10px';d.st
0';d.style.borderBottom='1px solid
rgba(255,255,255,.03)';d.style.cursor='pointer';
var projImg='';
if(e.id&&PROJECTS[e.id]){
var projImgIdx=GAL_META.findIndex(function(m){return m.projId===e.id;});
if(projImgIdx>=0)projImg='<div class="re-thumb"><img
src="'+GAL_IMGS[projImgIdx].src+'" alt=""></div>';
}
d.innerHTML=projImg+'<div class="re-body"><div class="re-meta"><span class="re-
c" style="color:rgb('+cc+')">'+e.cat+'</span><span class="re-
a">'+timeAgo(e.t)+'</span></div><div class="re-t">'+e.title+(e.sub?' —
'+e.sub:'')+'</div></div>';
if(e.id&&PROJECTS[e.id])d.addEventListener('click',function()
{openProject(e.id);});
el.appendChild(d);});}
function buildLogGallery(wrap){if(wrap.querySelector('.gal-
filters'))return;wrap.innerHTML='';var
filters=document.createElement('div');filters.className='gal-filters';
['architecture','interiors','urban design','print +
digital','photography'].forEach(function(c){var
btn=document.createElement('button');btn.className='lcbt
on';btn.textContent=c;btn.setAttribute('data-gf',c);btn.onclick=function()
{btn.classList.toggle('on');rebuildLogGalGrid();};filters.appendChild(btn);});wrap.appendChild
grid=document.createElement('div');grid.className='gal-grid';grid.id='log-gal-
grid';wrap.appendChild(grid);fillLogGalGrid();}
function rebuildLogGalGrid(){var g=document.getElementById('log-gal-grid');if(g)
{g.innerHTML='';fillLogGalGrid();}}
function fillLogGalGrid(){var g=document.getElementById('log-gal-
grid');if(!g)return;var af={};document.querySelectorAll('.gal-filters
.lcbt.on').forEach(function(b){af[b.getAttribute('data-
gf')]=true;});fillImageGrid(g,af,showFilters);}
// ── TICK ──────────────────────────────────────────────────────────────────────
function tick(){T+=.012;for(var i=mouseTrail.length-1;i>=0;i--){mouseTrail[i][2]-
=.018;if(mouseTrail[i][2]<=0)mouseTrail.splice(i,1);}for(var k=popRings.length-
1;k>=0;k--){var pr=popRings[k];pr.r+=(pr.rMax-pr.r)*.26;pr.life-
=.032;if(pr.life<=0)popRings.splice(k,1);}for(var j=popParticles.length-1;j>=0;j--
){var
pp=popParticles[j];pp.vy+=pp.ay;pp.x+=pp.vx;pp.y+=pp.vy;pp.vx*=pp.drag;pp.vy*=pp.drag;pp.life-
=pp.mist?0.016:0.021;if(pp.life<=0)popParticles.splice(j,1);}if(CTX)
{drawField();drawBubbles();drawPopRings();drawPopParticles();}requestAnimationFrame(tick);}
function drawPopRings()
{if(!popRings.length)return;CTX.save();CTX.globalCompositeOperation='screen';popRings.forEach(f
{var t=pr.life;if(t<=0)return;CTX.strokeStyle='rgba(255,255,255,'+
(t*.42).toFixed(3)+')';CTX.lineWidth=2.2*t;CTX.beginPath();CTX.arc(pr.x,pr.y,pr.r,0,Math.PI*2);
(t*.22).toFixed(3)+')';CTX.lineWidth=.9*t;CTX.stroke();});CTX.restore();}
function drawPopParticles()
{if(!popParticles.length)return;CTX.save();CTX.globalCompositeOperation='screen';popParticles.f
{var t=p.life;if(t<=0)return;var rad=p.sz*t,al=t*(p.mist?0.32:0.52);var
g=CTX.createRadialGradient(p.x,p.y,0,p.x,p.y,rad*1.35);g.addColorStop(0,'rgba(255,255,255,'+
(al*.92).toFixed(3)+')');g.addColorStop(.45,'rgba(232,248,255,'+
(al*.45).toFixed(3)+')');g.addColorStop(1,'rgba(210,235,255,0)');CTX.fillStyle=g;CTX.beginPath
resize();try{var saved=JSON.parse(localStorage.getItem('oone_scheme'));if(saved)
{applyScheme(saved.id,saved.v);if(saved.galMode)applyGalMode(saved.galMode);}}catch(e)
{}applyScheme(currentScheme,currentVariation);applyGalMode(galColorMode);tick();renderFilterPan
function buildProjStrip(){
var strip=document.getElementById('proj-strip');
if(!strip)return;
var keys=Object.keys(PROJECTS);
var projImgMap={};
GAL_META.forEach(function(m,i)
{if(m.projId&&!projImgMap[m.projId])projImgMap[m.projId]=i;});
keys.forEach(function(k){
var p=PROJECTS[k];
var imgIdx=projImgMap[k];
if(imgIdx==null)return;
var card=document.createElement('div');
card.style.cssText='width:clamp(90px,10vw,130px);flex-
shrink:0;cursor:pointer;pointer-events:all;margin-
right:8px;opacity:0.55;transition:opacity .3s,transform .3s';
card.innerHTML='<img src="'+GAL_IMGS[imgIdx].src+'"
style="width:100%;height:clamp(60px,8vw,90px);object-
fit:cover;display:block;filter:saturate(0.5) brightness(0.7)">'
+'<div style="font-family:\'Space Mono\',monospace;font-size:8px;letter-
spacing:.10em;text-transform:uppercase;color:rgba(255,255,255,.25);margin-
top:4px;white-space:nowrap;overflow:hidden;text-
overflow:ellipsis">'+p.title+'</div>';
card.addEventListener('mouseenter',function()
{card.style.opacity='1';card.style.transform='translateY(-4px)';});
card.addEventListener('mouseleave',function()
{card.style.opacity='0.55';card.style.transform='';});
card.addEventListener('click',function(){openProject(k);});
strip.appendChild(card);
});
requestAnimationFrame(function(){requestAnimationFrame(function()
{strip.style.opacity='1';});});
}
window.addEventListener('load',function(){maybeShowTut();});
var TUT_STEPS=[{t:'The field',b:'Each dot is something noticed, made, or felt. The
field warms where attention accumulates. Brighter means more recent.'},{t:'Itself
and orbit',b:'Solid dots are <em>itself</em> \u2014 from me. Target rings are
<em>orbit</em> \u2014 influences, inspirations, references.'},{t:'Navigate',b:'Use
the top bar to open <em>About</em>, <em>Services</em>, or <em>Log</em>. Use the
bottom-left key to switch between <em>field</em> and <em>gallery</em> views.'},
{t:'Gallery',b:'The gallery organizes work by <em>practice</em> and <em>play</em>.
Everything gets dithered to your color story. Hover to reveal.'}];
var
tutStep=0,tutEl=document.getElementById('tut'),tutCard=document.getElementById('tut-
card');
function multiCircleBg(){
var cols=SCHEMES.map(function(s){return'rgb('+(s.vars[1]||s.vars[0]).acc+')';});
return'linear-gradient(135deg,'+cols.join(',')+')';
}
function buildTutPalette(){
var acc=getAccRGB();
var schHtml='<div style="display:flex;gap:10px;justify-
content:center;margin:18px 0 20px">'+SCHEMES.map(function(s){
var sel=(s.id===currentScheme);
var rep=s.vars[1]||s.vars[0];
return '<div class="tc-bub'+(sel?' sel':'')+'"
style="background:rgb('+rep.acc+');width:28px;height:28px"
onclick="applyScheme(\''+s.id+'\',\''+rep.v+'\');document.querySelectorAll(\'#tut-
card .tc-bub\').forEach(function(b)
{b.classList.remove(\'sel\')});this.classList.add(\'sel\');refreshTutModes()">
</div>';
}).join('')+'</div>';
var modeDefs=[{m:'mono',label:'monochrome'},{m:'duo',label:'duotone'},
{m:'multi',label:'multicolor'}];
var modeHtml='<div style="display:flex;gap:20px;justify-content:center;margin-
top:4px">'+modeDefs.map(function(mo){
var on=galColorMode===mo.m;
var bg,pct;
if(mo.m==='mono'){bg='rgb(88,88,82)';pct='0%';}
else if(mo.m==='duo'){bg='linear-
gradient(135deg,rgb('+acc+'),rgb(88,88,82))';pct='40%';}
else{bg=multiCircleBg();pct='100%';}
return '<div onclick="applyGalMode(\''+mo.m+'\');refreshTutModes()"
style="text-align:center;cursor:pointer;user-select:none">'
+'<div id="tut-mode-circ-'+mo.m+'" style="width:28px;height:28px;border-
radius:50%;background:'+bg+';margin:0 auto 6px;border:2px solid
rgba(255,255,255,'+(on?'.65':'.12')+');transition:border-color .2s;box-
sizing:border-box"></div>'
+'<div style="font-family:Space Mono,monospace;font-size:8px;letter-
spacing:.06em;text-transform:uppercase;color:rgba(255,255,255,'+
(on?'.55':'.18')+');line-height:1.5" id="tut-mode-lbl-'+mo.m+'">'
+'<div>'+pct+'</div><div>'+mo.label+'</div>'
+'</div></div>';
}).join('')+'</div>';
return schHtml+modeHtml;
}
function refreshTutModes(){
var acc=getAccRGB();
[{m:'mono'},{m:'duo'},{m:'multi'}].forEach(function(mo){
var circ=document.getElementById('tut-mode-circ-'+mo.m);
var lbl=document.getElementById('tut-mode-lbl-'+mo.m);
if(!circ)return;
if(mo.m==='mono')circ.style.background='rgb(88,88,82)';
else if(mo.m==='duo')circ.style.background='linear-
gradient(135deg,rgb('+acc+'),rgb(88,88,82))';
else circ.style.background=multiCircleBg();
var on=galColorMode===mo.m;
circ.style.borderColor=on?'rgba(255,255,255,.65)':'rgba(255,255,255,.12)';
if(lbl)lbl.style.color=on?'rgba(255,255,255,.55)':'rgba(255,255,255,.18)';
});
}
function renderTutStep(){if(tutStep===-1){tutCard.innerHTML='<div style="text-
align:center;margin-bottom:14px"><span class="oo-mark" style="font-
size:36px;color:rgba(255,255,255,.25)"><span class="o1">O</span><span
class="o2">O</span></span></div><div class="tut-title">Before we begin.</div><div
class="tut-body" style="font-size:var(--fs-sm)"><div style="margin-
bottom:6px;color:rgba(255,255,255,.30)">Choose a palette:
</div>'+buildTutPalette()+'<div style="margin-
top:14px;color:rgba(255,255,255,.22)">You can change this anytime.</div></div><div
class="tut-nav" style="margin-top:16px"><div></div><div
style="display:flex;gap:8px;align-items:center"><button class="tut-skip"
onclick="closeTut()">skip tour</button><button class="tut-btn"
onclick="nextTut()">show me around</button></div></div>';return;}var
s=TUT_STEPS[tutStep],dots='',isLast=(tutStep===TUT_STEPS.length-1);for(var
i=0;i<TUT_STEPS.length;i++)dots+='<div class="tut-dot'+(i===tutStep?' on':'')+'">
</div>';tutCard.innerHTML='<div class="tut-step">'+(tutStep+1)+' /
'+TUT_STEPS.length+'</div><div class="tut-title">'+s.t+'</div><div class="tut-
body">'+s.b+'</div><div class="tut-nav"><div class="tut-dots">'+dots+'</div><div
style="display:flex;gap:8px;align-items:center">'+(isLast?'':'<button class="tut-
skip" onclick="closeTut()">skip</button>')+'<button class="tut-btn" onclick="'+
(isLast?'closeTut()':'nextTut()')+'">'+(isLast?'let&#39;s go':'next')+'</button>
</div></div>';}
function nextTut(){tutStep++;if(tutStep>=TUT_STEPS.length)
{closeTut();return;}renderTutStep();}
function closeTut(){if(window._fm){window._fm.animate(tutEl,{opacity:[1,0]},
{duration:.35,ease:[.4,0,1,1],onComplete:function()
{tutEl.classList.remove('on');tutEl.style.opacity='';}});}else{tutEl.classList.remove('on');}}
function maybeShowTut(){tutStep=-1;renderTutStep();setTimeout(function()
{tutEl.classList.add('on');tutEl.style.opacity='0';if(window._fm)
{window._fm.animate(tutEl,{opacity:[0,1]},{duration:.5,ease:
[.16,1,.3,1]});}else{tutEl.style.opacity='';}},600);}
document.addEventListener('keydown',function(ev){if(ev.key==='Escape')
{if(tutEl.classList.contains('on'))closeTut();else
if(drawerMode)closeDrawer();else if(document.getElementById('image-
view').classList.contains('on')||document.getElementById('feed-
overlay').classList.contains('on')){setMainView('log');}else
closeThemeChooser();}});
</script>
<script type="module">
import("https://esm.sh/framer-motion@11").then(function(fm){
window._fm={animate:fm.animate,stagger:fm.stagger};
document.dispatchEvent(new CustomEvent('fm:ready'));
}).catch(function(){
document.dispatchEvent(new CustomEvent('fm:ready'));
});
</script>
</body>
</html>
