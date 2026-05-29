<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ticker Phonetic</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: monospace;
    background: #fff;
    color: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
  }
  .row {
    display: flex;
    align-items: flex-start;
    gap: 40px;
  }
  .col label {
    display: block;
    font-size: 11px;
    font-weight: bold;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 6px;
    color: #999;
  }
  input {
    font-family: monospace;
    font-size: 22px;
    font-weight: bold;
    border: none;
    border-bottom: 2px solid #000;
    outline: none;
    width: 90px;
    padding: 2px 0;
    text-transform: uppercase;
  }
  #output {
    font-size: 22px;
    font-weight: bold;
    padding: 2px 0;
    border-bottom: 2px solid #000;
    min-width: 280px;
    color: #000;
    white-space: nowrap;
  }
  #output.empty { color: #ccc; }
</style>
</head>
<body>
<div class="row">
  <div class="col">
    <label>Ticker</label>
    <input id="ticker" maxlength="5" placeholder="NVDA" autocomplete="off" spellcheck="false">
  </div>
  <div class="col">
    <label>Phonetic</label>
    <div id="output" class="empty">—</div>
  </div>
</div>
<script>
  const N = {A:'Alpha',B:'Bravo',C:'Charlie',D:'Delta',E:'Echo',F:'Foxtrot',G:'Golf',H:'Hotel',I:'India',J:'Juliett',K:'Kilo',L:'Lima',M:'Mike',N:'November',O:'Oscar',P:'Papa',Q:'Quebec',R:'Romeo',S:'Sierra',T:'Tango',U:'Uniform',V:'Victor',W:'Whiskey',X:'X-ray',Y:'Yankee',Z:'Zulu'};
  const inp = document.getElementById('ticker');
  const out = document.getElementById('output');
  inp.addEventListener('input', () => {
    const v = inp.value.toUpperCase().replace(/[^A-Z]/g,'');
    inp.value = v;
    if (!v) { out.textContent = '—'; out.className = 'empty'; return; }
    out.textContent = [...v].map(l => N[l]||l).join(' · ');
    out.className = '';
  });
  inp.focus();
</script>
</body>
</html>
