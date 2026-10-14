# Perrier-74100

<!DOCTYPE html>

<html lang="fr">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>PERRIER 74 — Univers CBD</title>

<script src="https://telegram.org/js/telegram-web-app.js"></script>

<style>

:root {

  --green:#244d38;

  --light:#edf3ec;

  --text:#23352a;

}

* { box-sizing:border-box; }

body {

  margin:0;

  font-family:Arial,sans-serif;

  background:#fff;

  color:var(--text);

}

header { padding:24px 20px 12px; }

.logo { font-size:25px;font-weight:800;letter-spacing:3px; }

.sub { color:#748578;font-size:11px;letter-spacing:3px;margin-top:6px; }

.hero {

  margin:12px 16px 22px;padding:28px 20px;

  border-radius:20px;background:var(--light);

}

.hero small { color:var(--green);letter-spacing:2px; }

h1 { font-size:30px;line-height:1.15;margin:12px 0; }

p { line-height:1.6;color:#66746a; }

.categories {

  display:flex;gap:8px;overflow-x:auto;

  padding:0 16px 20px;

}

.chip {

  border:1px solid #dce5dc;border-radius:30px;

  padding:10px 15px;background:white;

  white-space:nowrap;color:var(--green);

}

.chip.active { background:var(--green);color:white; }

h2 { margin:8px 16px 16px;font-size:20px; }

.grid {

  display:grid;grid-template-columns:1fr 1fr;

  gap:12px;padding:0 16px 24px;

}

.product {

  border:1px solid #e8eee8;border-radius:16px;

  overflow:hidden;background:white;

}

.product img {

  width:100%;height:140px;object-fit:cover;

  background:var(--light);display:block;

}

.info { padding:12px; }

.info h3 { font-size:15px;margin:0 0 7px; }

.info p { font-size:12px;margin:0 0 12px; }

.details {

  border:0;background:var(--light);color:var(--green);

  padding:10px;border-radius:9px;width:100%;

}

.contact {

  display:block;margin:0 16px 28px;padding:16px;

  border-radius:14px;background:var(--green);

  color:white;text-decoration:none;text-align:center;

  font-weight:bold;

}

footer { text-align:center;color:#89958c;font-size:11px;padding:0 20px 25px; }

[hidden] { display:none !important; }

</style>

</head>

<body>

<header>

  <div class="logo">PERRIER 74</div>

  <div class="sub">L'UNIVERS DU CBD</div>

</header>

<section class="hero">

  <small>NOTRE SÉLECTION</small>

  <h1>La nature,<br>tout simplement.</h1>

  <p>Découvrez notre univers et explorez notre sélection de produits.</p>

</section>

<nav class="categories" id="categories"></nav>

<h2>Notre catalogue</h2>

<main class="grid" id="products"></main>

<a class="contact" id="contact" href="https://t.me/TON_PSEUDO">

  ✉ Nous contacter sur Telegram

</a>

<footer> PERRIER 74 · Présentation des produits<br>

Informations réglementaires à vérifier selon chaque produit.</footer>

<script>

const items = [

 {name:"Huile CBD",cat:"Huiles",

  desc:"Découvrez notre gamme d'huiles.",

  img:"https://placehold.co/500x400/edf3ec/244d38?text=Huile+CBD"},

 {name:"Fleurs de CBD",cat:"Fleurs",

  desc:"Explorez notre sélection de fleurs.",

  img:"https://placehold.co/500x400/edf3ec/244d38?text=Fleurs"},

 {name:"Résines de CBD",cat:"Résines",

  desc:"Découvrez notre sélection de résines.",

  img:"https://placehold.co/500x400/edf3ec/244d38?text=Resines"},

 {name:"Infusions",cat:"Infusions",

  desc:"Une sélection d'infusions.",

  img:"https://placehold.co/500x400/edf3ec/244d38?text=Infusions"}

];

const categories = ["Tout", ...new Set(items.map(x=>x.cat))];

let selected = "Tout";

const nav = document.querySelector("#categories");

const grid = document.querySelector("#products");

function render() {

  nav.innerHTML = "";

  categories.forEach(cat => {

    const b = document.createElement("button");

    b.className = "chip" + (cat===selected ? " active":"");

    b.textContent = cat;

    b.onclick = () => { selected=cat;render(); };

    nav.appendChild(b);

  });

  grid.innerHTML = "";

  items.filter(x=>selected==="Tout"||x.cat===selected)

  .forEach(item => {

    const card = document.createElement("article");

    card.className = "product";

    const img = document.createElement("img");

    img.src = item.img;

    img.alt = item.name;

    const info = document.createElement("div");

    info.className = "info";

    const title = document.createElement("h3");

    title.textContent = item.name;

    const desc = document.createElement("p");

    desc.textContent = item.desc;

    const button = document.createElement("button");

    button.className = "details";

    button.textContent = "En savoir plus";

    button.onclick = () => alert(item.name+"\n\n"+item.desc);

    info.append(title,desc,button);

    card.append(img,info);

    grid.appendChild(card);

  });

}

render();

const tg = window.Telegram?.WebApp;

if(tg) { tg.ready(); tg.expand(); }

</script>

</body>

</html>
