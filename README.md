<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ashish Windows 11 Clone</title>
<style>
  *{margin:0;padding:0;box-sizing:border-box;}
  html,body{height:100%;font-family:"Segoe UI",sans-serif;overflow:hidden;}
  body{background:url('https://wallpapercave.com/wp/wp9628653.jpg') no-repeat center/cover;}

  #boot,#login,#desktop,#startMenu{position:absolute;width:100%;height:100%;display:none;}
  #boot{background:black;color:white;display:flex;justify-content:center;align-items:center;flex-direction:column;}
  #boot img{width:120px;animation:pulse 2s infinite alternate;}
  @keyframes pulse{0.3{opacity:.3;}100%{opacity:1;}}
  #login{background:rgba(30,30,30,0.95);display:flex;justify-content:center;align-items:center;flex-direction:column;color:white;}
  #login input,button{padding:10px 20px;margin:10px;border:none;border-radius:5px;}
  #login input{width:200px;font-size:16px;}
  #login button{background:#0078d7;color:white;cursor:pointer;font-size:16px;}

  #desktop{display:none;}
  #taskbar{position:fixed;bottom:0;width:100%;height:48px;background:rgba(255,255,255,0.8);display:flex;align-items:center;justify-content:center;box-shadow:0 -1px 5px rgba(0,0,0,0.3);}
  #taskbar img{height:32px;margin:0 10px;cursor:pointer;transition:transform .2s;}
  #taskbar img:hover{transform:scale(1.2);}
  #startMenu{display:none;bottom:48px;left:50%;transform:translateX(-50%);width:400px;height:300px;background:rgba(255,255,255,0.95);border-radius:12px;display:flex;flex-wrap:wrap;padding:20px;box-shadow:0 0 20px rgba(0,0,0,0.2);}
  .appIcon{width:80px;text-align:center;margin:10px;cursor:pointer;}
  .appIcon img{width:48px;height:48px;}
  .window{position:absolute;background:white;border-radius:10px;box-shadow:0 0 10px rgba(0,0,0,0.3);overflow:hidden;}
  .window-header{background:#0078d7;color:white;padding:8px;display:flex;justify-content:space-between;}
  .window-body{padding:10px;height:calc(100% - 32px);overflow:auto;}
</style>
</head>
<body>
<div id="boot">
  <img src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Windows_logo_-_2021.svg">
  <p style="margin-top:20px;font-size:18px;">Booting Ashish Windows...</p>
</div>
<div id="login">
  <h2>Welcome</h2>
  <input id="pw" type="password" placeholder="Password">
  <button onclick="login()">Sign in</button>
</div>
<div id="desktop"></div>
<div id="taskbar">
  <img onclick="toggleStart()" src="https://upload.wikimedia.org/wikipedia/commons/f/f8/Windows_logo_-_2021.svg">
</div>
<div id="startMenu"></div>

<script>
  const apps=[
    {id:'notepad',name:'Notepad',ico:'https://icons.iconarchive.com/icons/custom-icon-design/flatastic-1/512/notepad-icon.png',content:`<textarea style="width:100%;height:100%;border:none;"></textarea>`},
    {id:'calc',name:'Calculator',ico:'https://icons.iconarchive.com/icons/graphicloads/100-flat-2/256/calculator-icon.png',content:`<iframe src="https://www.online-calculator.com/simple-calculator/" style="width:100%;height:100%;border:none;"></iframe>`},
    {id:'paint',name:'Paint',ico:'https://icons.iconarchive.com/icons/graphicloads/colorful-long-shadow/256/Paint-icon.png',content:`<canvas id="paintCanvas" width="380" height="240" style="border:1px solid #000"></canvas><script>let c=document.getElementById('paintCanvas'),ctx=c.getContext('2d'),drawing=false;c.onmousedown=()=>drawing=true;c.onmouseup=()=>drawing=false;c.onmousemove=e=>drawing&&ctx.fillRect(e.offsetX,e.offsetY,2,2);<\/script>`},
    {id:'media',name:'Media',ico:'https://icons.iconarchive.com/icons/dtafalonso/android-lollipop/512/Video-player-icon.png',content:`<video controls autoplay style="width:100%;height:100%"><source src="https://www.w3schools.com/html/mov_bbb.mp4"></video>`},
    {id:'terminal',name:'Terminal',ico:'https://icons.iconarchive.com/icons/papirus-team/papirus-apps/512/utilities-terminal-icon.png',content:`<pre>> Ashish Terminal\\n> type help</pre>`},
    {id:'browser',name:'Browser',ico:'https://icons.iconarchive.com/icons/google/chrome/512/Google-Chrome-icon.png',content:''}
  ];
  window.onload=(()=>{document.getElementById('boot').style.display='flex';setTimeout(()=>{document.getElementById('boot').style.display='none';document.getElementById('login').style.display='flex';},2000);});
  function login(){
    if(document.getElementById('pw').value==='1234'){
      document.getElementById('login').style.display='none';
      document.getElementById('desktop').style.display='block';
      apps.forEach(a=>{
        let icon=document.createElement('img');icon.src=a.ico;
        document.getElementById('taskbar').appendChild(icon);
        let am=document.createElement('div');am.className='appIcon';am.onclick=()=>openApp(a.id);
        am.innerHTML=`<img src="${a.ico}"><div>${a.name}</div>`;
        document.getElementById('startMenu').appendChild(am);
      });
    } else alert('Wrong password');
  }
  function toggleStart(){
    let m=document.getElementById('startMenu');
    m.style.display=m.style.display==='flex'?'none':'flex';
    m.style.flexWrap='wrap';
  }
  function openApp(id){
    const a=apps.find(x=>x.id===id);
    if(id==='browser'){window.open('https://www.google.com','_blank');return;}
    const w=document.createElement('div');w.className='window';w.style.width='500px';w.style.height='350px';w.style.top='100px';w.style.left='100px';
    w.innerHTML=`
      <div class="window-header">${a.name}<button onclick="this.closest('.window').remove()">X</button></div>
      <div class="window-body">${a.content}</div>`;
    document.body.appendChild(w);
  }
</script>
</body>
</html>
