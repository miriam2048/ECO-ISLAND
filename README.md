[ECO ISLAND.html](https://github.com/user-attachments/files/35408201/ECO.ISLAND.html)<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ECO ISLAND 🌱</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: "Trebuchet MS", Arial, sans-serif;
    background: #b8e8b0;
    color: #34543a;
}

header {
    background: #77c879;
    padding: 20px;
    text-align: center;
    border-bottom: 5px solid #5aa95e;
}

header h1 {
    margin: 0;
    font-size: 32px;
}

header p {
    margin: 8px 0 0;
}

.container {
    max-width: 1200px;
    margin: auto;
    padding: 15px;
}

.stats {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
    gap: 10px;
    margin-bottom: 15px;
}

.stat {
    background: #fff8df;
    border-radius: 15px;
    padding: 12px;
    text-align: center;
    border: 3px solid #d5e8a9;
}

.stat strong {
    display: block;
    font-size: 22px;
    margin-top: 5px;
}

.main {
    display: grid;
    grid-template-columns: 1fr 300px;
    gap: 15px;
}

.panel {
    background: #fff8df;
    border-radius: 20px;
    padding: 15px;
    border: 4px solid #d5e8a9;
}

.island {
    background: #71c8e4;
    border-radius: 20px;
    padding: 15px;
    min-height: 500px;
    overflow: auto;
}

.map {
    display: grid;
    grid-template-columns: repeat(10, 1fr);
    gap: 4px;
    max-width: 700px;
    margin: auto;
}

.tile {
    aspect-ratio: 1;
    background: #90d77b;
    border-radius: 9px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: clamp(18px, 3vw, 32px);
    cursor: pointer;
    border: 2px solid #79bd68;
    transition: 0.15s;
}

.tile:hover {
    transform: scale(1.08);
    background: #b0e695;
}

.water {
    background: #67bde1;
    border-color: #52a7d1;
}

.sand {
    background: #f3d48c;
    border-color: #e3c375;
}

.selected {
    outline: 4px solid #ffcf44;
}

.controls {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin: 10px 0;
}

.catalog {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(115px, 1fr));
    gap: 8px;
    margin: 12px 0;
}

.catalog button {
    background: #fff;
    color: #34543a;
    border: 2px solid #d5e8a9;
    min-height: 64px;
}

.catalog button.selected-building {
    background: #ffcf44;
    color: #34543a;
    border-color: #d6a900;
}

.catalog button small {
    display: block;
    margin-top: 4px;
}

.recipe-list {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 8px;
    margin: 12px 0;
}

.recipe-list button {
    background: #e9f5d7;
    color: #34543a;
    border: 2px solid #b9d99b;
    text-align: left;
    min-height: 76px;
}

.recipe-list button:hover {
    background: #d5e8a9;
}

button, select {
    border: none;
    border-radius: 12px;
    padding: 10px;
    background: #77c879;
    color: white;
    font-weight: bold;
    cursor: pointer;
    font-size: 14px;
}

button:hover {
    background: #54a95b;
}

button:active {
    transform: scale(0.97);
}

select {
    background: #5aa95e;
}

h2, h3 {
    margin-top: 5px;
}

.info {
    background: #e9f5d7;
    padding: 12px;
    border-radius: 12px;
    margin: 10px 0;
}

.log {
    background: white;
    border-radius: 12px;
    padding: 10px;
    height: 140px;
    overflow-y: auto;
    font-size: 14px;
}

.mission {
    background: #dff0c9;
    padding: 10px;
    border-radius: 12px;
    margin: 8px 0;
}

.footer {
    text-align: center;
    padding: 20px;
}

@media(max-width: 800px) {
    .main {
        grid-template-columns: 1fr;
    }
}
</style>
</head>

<body>

<header>
    <h1>🌴 ECO ISLAND 🌱</h1>
    <p>Construye una isla sostenible y cuida el planeta</p>
</header>

<div class="container">

    <div class="stats">
        <div class="stat">💰 Monedas<strong id="coins">5000</strong></div>
        <div class="stat">🌍 Contaminación<strong id="pollution">0</strong></div>
        <div class="stat">😊 Felicidad<strong id="happiness">70</strong></div>
        <div class="stat">📅 Día<strong id="day">1</strong></div>
        <div class="stat">🌳 Madera<strong id="wood">0</strong></div>
        <div class="stat">🪨 Piedra<strong id="stone">0</strong></div>
        <div class="stat">🍃 Hojas<strong id="leaves">0</strong></div>
        <div class="stat">🍎 Fruta<strong id="fruit">0</strong></div>
        <div class="stat">♻️ Reciclaje<strong id="recycling">0</strong></div>
    </div>

    <div class="main">

        <div class="panel">
            <h2>🏝️ Tu isla</h2>

            <div class="controls">
                <select id="action">
                    <option value="select">👆 Seleccionar</option>
                    <option value="house">🏠 Casa - 500</option>
                    <option value="factory">🏭 Fábrica - 800</option>
                    <option value="shop">🛒 Supermercado - 400</option>
                    <option value="park">🌳 Parque - 300</option>
                    <option value="solar">☀️ Panel solar - 600</option>
                    <option value="recyclingCenter">♻️ Centro reciclaje - 500</option>
                    <option value="garden">🌻 Huerto - 350</option>
                    <option value="water">💧 Tratamiento agua - 600</option>
                    <option value="wind">🌬️ Molino eólico - 700</option>
                    <option value="hospital">🏥 Hospital - 700</option>
                    <option value="school">🏫 Escuela - 500</option>
                    <option value="bike">🚲 Carril bici - 250</option>
                    <option value="beach">🏖️ Playa protegida - 400</option>
                    <option value="forest">🌲 Bosque - 300</option>
                    <option value="flower">🌷 Flores - 50</option>
                    <option value="bench">🪑 Banco - 100</option>
                    <option value="lamp">💡 Farola - 100</option>
                    <option value="fountain">⛲ Fuente - 200</option>
                    <option value="fence">🪵 Valla - 30</option>
                    <option value="path">🟫 Camino - 20</option>
                </select>

                <button onclick="moveMode()">🔄 Mover</button>
                <button onclick="removeMode()">🗑️ Retirar</button>
            </div>

            <div class="info">
                Selecciona una construcción o decoración y después pulsa una casilla de la isla.
            </div>

            <h3>🏗️ Construcciones disponibles</h3>
            <div class="info" id="buildInfo">Elige algo de la tienda y después pulsa una casilla libre de la isla.</div>
            <div class="catalog" id="buildingCatalog"></div>

            <div class="map" id="map"></div>

            <div class="controls">
                <button onclick="collectResources()">🌳 Recoger materiales</button>
                <button onclick="fish()">🎣 Pescar</button>
                <button onclick="nextDay()">🌙 Dormir / Nuevo día</button>
            </div>

            <div class="controls">
                <button onclick="sellFish()">💰 Vender peces</button>
                <button onclick="sellMaterials()">🧺 Vender materiales</button>
                <button onclick="donateFish()">🐠 Donar peces</button>
                <button onclick="releaseFish()">🌊 Liberar peces</button>
            </div>

            <h3>🛠️ Taller: fabricar objetos con recursos</h3>
            <div class="info">Fabrica objetos usando madera, piedra, hojas y reciclaje. Después selecciónalos en «Construcciones disponibles» y colócalos en la isla. Los objetos fabricados no cuestan monedas al colocarlos.</div>
            <div class="recipe-list" id="recipeList"></div>
            <div class="info" id="craftInfo">Aquí verás cuántos objetos fabricados tienes disponibles.</div>

        </div>

        <div class="panel">

            <h2>📋 Isla</h2>

            <div class="info">
                <strong>🌍 Estado ambiental</strong>
                <p id="environment">Tu isla está comenzando.</p>
            </div>

            <div class="info">
                <strong>🛠️ Mantenimiento</strong>
                <p>Repara tu isla sin pasar días.</p>
                <button onclick="repairIsland()">🔧 Reparar ahora (100 monedas)</button>
            </div>

            <div class="info">
                <strong>🏗️ Reformas</strong>
                <p>Mejora la sostenibilidad de tu isla.</p>
                <button onclick="reformIsland()">♻️ Reforma ecológica (200 monedas)</button>
            </div>

            <h3>🧑‍🤝‍🧑 Habitantes</h3>

            <div class="info">
                <strong>🐰 Mía, agricultora</strong>
                <p>¡Hola! Necesitamos más huertos para producir alimentos.</p>
                <button onclick="talk('mia')">💬 Hablar</button>
            </div>

            <div class="info">
                <strong>🦊 Tom, comerciante</strong>
                <p>¡El reciclaje es muy importante para nuestra isla!</p>
                <button onclick="talk('tom')">💬 Hablar</button>
            </div>

            <div class="info">
                <strong>🐢 Lola, protectora marina</strong>
                <p>¡Tenemos que proteger nuestras playas y el mar!</p>
                <button onclick="talk('lola')">💬 Hablar</button>
            </div>

            <h3>🎯 Misiones ODS</h3>

            <div class="mission">
                <strong>ODS 2 🌾</strong>
                <p>Construye un huerto.</p>
            </div>

            <div class="mission">
                <strong>ODS 6 💧</strong>
                <p>Construye un sistema de tratamiento de agua.</p>
            </div>

            <div class="mission">
                <strong>ODS 7 ☀️</strong>
                <p>Instala energía renovable.</p>
            </div>

            <div class="mission">
                <strong>ODS 11 🏘️</strong>
                <p>Construye una isla sostenible.</p>
            </div>

            <div class="mission">
                <strong>ODS 12 ♻️</strong>
                <p>Construye un centro de reciclaje.</p>
            </div>

            <div class="mission">
                <strong>ODS 13 🌍</strong>
                <p>Reduce la contaminación.</p>
            </div>

            <div class="mission">
                <strong>ODS 14 🐠</strong>
                <p>Protege los océanos.</p>
            </div>

            <div class="mission">
                <strong>ODS 15 🌳</strong>
                <p>Planta árboles y crea bosques.</p>
            </div>

            <h3>📜 Registro</h3>
            <div class="log" id="log"></div>

        </div>

    </div>

    <div class="footer">
        🌱 ECO ISLAND — Un futuro sostenible empieza contigo 🌱
    </div>

</div>

<script>

// =================================
// VARIABLES DEL JUEGO
// =================================

let coins = 5000;
let day = 1;
let happiness = 70;

let resources = {
    wood: 0,
    stone: 0,
    leaves: 0,
    fruit: 0,
    recycling: 0
};

let fishCount = 0;
let donatedFish = 0;

let buildings = [];
let craftedItems = {};

let selectedAction = "select";
let movingBuilding = null;
let removing = false;

const size = 10;
const tiles = [];

const buildingData = {

    house: {
        emoji: "🏠",
        cost: 500,
        pollution: 1,
        happiness: 5
    },

    factory: {
        emoji: "🏭",
        cost: 800,
        pollution: 20,
        happiness: -5
    },

    shop: {
        emoji: "🛒",
        cost: 400,
        pollution: 3,
        happiness: 3
    },

    park: {
        emoji: "🌳",
        cost: 300,
        pollution: -8,
        happiness: 10
    },

    solar: {
        emoji: "☀️",
        cost: 600,
        pollution: -10,
        happiness: 4
    },

    recyclingCenter: {
        emoji: "♻️",
        cost: 500,
        pollution: -15,
        happiness: 5
    },

    garden: {
        emoji: "🌻",
        cost: 350,
        pollution: -5,
        happiness: 8
    },

    water: {
        emoji: "💧",
        cost: 600,
        pollution: -10,
        happiness: 4
    },

    wind: {
        emoji: "🌬️",
        cost: 700,
        pollution: -12,
        happiness: 5
    },

    hospital: {
        emoji: "🏥",
        cost: 700,
        pollution: 1,
        happiness: 8
    },

    school: {
        emoji: "🏫",
        cost: 500,
        pollution: 1,
        happiness: 8
    },

    bike: {
        emoji: "🚲",
        cost: 250,
        pollution: -4,
        happiness: 5
    },

    beach: {
        emoji: "🏖️",
        cost: 400,
        pollution: -10,
        happiness: 7
    },

    forest: {
        emoji: "🌲",
        cost: 300,
        pollution: -8,
        happiness: 8
    },

    flower: {
        emoji: "🌷",
        cost: 50,
        pollution: -1,
        happiness: 2
    },

    bench: {
        emoji: "🪑",
        cost: 100,
        pollution: 0,
        happiness: 3
    },

    lamp: {
        emoji: "💡",
        cost: 100,
        pollution: 0,
        happiness: 2
    },

    fountain: {
        emoji: "⛲",
        cost: 200,
        pollution: 0,
        happiness: 5
    },

    fence: {
        emoji: "🪵",
        cost: 30,
        pollution: 0,
        happiness: 1
    },

    path: {
        emoji: "🟫",
        cost: 20,
        pollution: 0,
        happiness: 1
    }
};

// =================================
// TIENDA / SELECCIÓN DE CONSTRUCCIONES
// =================================

function createBuildingCatalog() {
    const catalog = document.getElementById("buildingCatalog");
    catalog.innerHTML = "";

    Object.keys(buildingData).forEach(type => {
        const data = buildingData[type];
        const button = document.createElement("button");
        button.type = "button";
        button.dataset.type = type;
        button.innerHTML = `${data.emoji}<small>${buildingNames[type] || type}</small><small>${data.cost} monedas</small>`;
        button.onclick = () => {
            document.getElementById("action").value = type;
            selectedAction = type;
            document.getElementById("buildInfo").textContent = `Has elegido ${data.emoji} ${buildingNames[type] || type}. Pulsa una casilla libre para construir.`;
            catalog.querySelectorAll("button").forEach(b => b.classList.remove("selected-building"));
            button.classList.add("selected-building");
        };
        catalog.appendChild(button);
    });
}

const buildingNames = {
    house: "Casa", factory: "Fábrica", shop: "Supermercado", park: "Parque",
    solar: "Panel solar", recyclingCenter: "Centro reciclaje", garden: "Huerto",
    water: "Tratamiento agua", wind: "Molino eólico", hospital: "Hospital",
    school: "Escuela", bike: "Carril bici", beach: "Playa protegida",
    forest: "Bosque", flower: "Flores", bench: "Banco", lamp: "Farola",
    fountain: "Fuente", fence: "Valla", path: "Camino"
};

// =================================
// TALLER: RECETAS DE FABRICACIÓN
// =================================

const craftRecipes = {
    bench: { name: "Banco", emoji: "🪑", materials: { wood: 2, stone: 1 } },
    fence: { name: "Valla", emoji: "🪵", materials: { wood: 3 } },
    path: { name: "Camino", emoji: "🟫", materials: { stone: 2 } },
    fountain: { name: "Fuente", emoji: "⛲", materials: { stone: 4, recycling: 1 } },
    flower: { name: "Flores", emoji: "🌷", materials: { leaves: 3 } },
    garden: { name: "Huerto", emoji: "🌻", materials: { wood: 2, leaves: 3, recycling: 1 } }
};

const materialNames = {
    wood: "madera", stone: "piedra", leaves: "hojas",
    fruit: "fruta", recycling: "reciclaje"
};

function createCraftingWorkshop() {
    const list = document.getElementById("recipeList");
    list.innerHTML = "";

    Object.entries(craftRecipes).forEach(([type, recipe]) => {
        const button = document.createElement("button");
        const costText = Object.entries(recipe.materials)
            .map(([key, amount]) => `${amount} ${materialNames[key]}`).join(" + ");
        button.type = "button";
        button.innerHTML = `${recipe.emoji} <strong>${recipe.name}</strong><br><small>${costText}</small><br><small>En inventario: ${craftedItems[type] || 0}</small>`;
        button.onclick = () => craftItem(type);
        list.appendChild(button);
    });
    updateCraftInfo();
}

function craftItem(type) {
    const recipe = craftRecipes[type];
    if (!recipe) return;

    const missing = Object.entries(recipe.materials)
        .filter(([material, amount]) => (resources[material] || 0) < amount);

    if (missing.length) {
        log("❌ No tienes suficientes materiales para fabricar " + recipe.name + ".");
        return;
    }

    Object.entries(recipe.materials).forEach(([material, amount]) => {
        resources[material] -= amount;
    });

    craftedItems[type] = (craftedItems[type] || 0) + 1;
    log(`🛠️ Fabricaste ${recipe.emoji} ${recipe.name}. Ya tienes ${craftedItems[type]}.`);
    updateStats();
    createCraftingWorkshop();
    saveGame();
}

function updateCraftInfo() {
    const available = Object.entries(craftedItems)
        .filter(([, amount]) => amount > 0)
        .map(([type, amount]) => `${craftRecipes[type]?.name || buildingNames[type] || type}: ${amount}`)
        .join(" · ");
    document.getElementById("craftInfo").textContent =
        available ? "Objetos fabricados disponibles: " + available : "Todavía no has fabricado ningún objeto.";
}

// =================================
// CREAR MAPA
// =================================

function createMap() {

    const map = document.getElementById("map");

    map.innerHTML = "";

    for (let i = 0; i < size * size; i++) {

        const tile = document.createElement("div");

        tile.className = "tile";

        // Crear zonas de agua y playa
        if (i < size || i >= size * 9) {
            tile.classList.add("water");
        }

        if (i >= size * 2 && i < size * 3) {
            tile.classList.add("sand");
        }

        tile.onclick = () => clickTile(i);

        map.appendChild(tile);

        tiles.push(tile);
    }

    updateMap();
}

// =================================
// INTERACCIÓN CON MAPA
// =================================

function clickTile(index) {

    if (movingBuilding !== null) {

        if (buildings.some((b, i) => b.position === index && i !== movingBuilding)) {
            log("❌ Esa casilla ya está ocupada.");
            return;
        }

        buildings[movingBuilding].position = index;

        movingBuilding = null;

        log("🏗️ Edificio movido.");

        updateMap();
        saveGame();

        return;
    }

    if (removing) {

        const building = buildings.find(b => b.position === index);

        if (building) {

            buildings = buildings.filter(b => b.position !== index);

            log("🗑️ Elemento retirado.");

            removing = false;

            updateMap();
            calculatePollution();
            saveGame();
        }

        return;
    }

    const action = document.getElementById("action").value;

    if (action === "select") {

        const building = buildings.find(b => b.position === index);

        if (building) {

            log("Seleccionaste " + buildingData[building.type].emoji);

        } else {

            log("Esta casilla está libre.");
        }

        return;
    }

    build(action, index);
}

// =================================
// CONSTRUIR
// =================================

function build(type, position) {

    if (buildings.some(b => b.position === position)) {

        log("❌ Esta casilla está ocupada.");

        return;
    }

    const data = buildingData[type];

    if (!data) return;

    const hasCraftedItem = (craftedItems[type] || 0) > 0;

    if (!hasCraftedItem && coins < data.cost) {
        log("❌ No tienes suficientes monedas ni un objeto fabricado de este tipo.");
        return;
    }

    if (hasCraftedItem) {
        craftedItems[type]--;
        log("🏗️ Colocaste un objeto fabricado: " + data.emoji);
        createCraftingWorkshop();
    } else {
        coins -= data.cost;
        log("🏗️ Construiste " + data.emoji);
    }

    buildings.push({
        type: type,
        position: position
    });

    updateMap();
    calculatePollution();
    saveGame();
}

// =================================
// MOVER EDIFICIOS
// =================================

function moveMode() {

    removing = false;

    const position = prompt("¿Qué casilla ocupa el edificio que quieres mover? (0-99)");

    if (position === null) return;

    const index = Number(position);

    if (index < 0 || index >= 100) return;

    const building = buildings.find(b => b.position === index);

    if (!building) {

        log("No hay ningún edificio en esa casilla.");

        return;
    }

    movingBuilding = buildings.indexOf(building);

    log("Selecciona una nueva casilla para moverlo.");

}

function removeMode() {

    movingBuilding = null;

    removing = true;

    log("Selecciona el elemento que quieres retirar.");
}

// =================================
// MAPA
// =================================

function updateMap() {

    tiles.forEach(tile => {

        tile.innerHTML = "";

        tile.classList.remove("selected");

    });

    buildings.forEach(building => {

        const tile = tiles[building.position];

        if (tile) {

            tile.innerHTML = buildingData[building.type].emoji;

        }
    });
}

// =================================
// RECURSOS
// =================================

function collectResources() {

    const woodAmount = Math.floor(Math.random() * 4) + 2;
    const stoneAmount = Math.floor(Math.random() * 3) + 1;
    const leafAmount = Math.floor(Math.random() * 5) + 2;
    const fruitAmount = Math.floor(Math.random() * 3) + 1;
    const recyclingAmount = Math.floor(Math.random() * 3) + 1;

    resources.wood += woodAmount;
    resources.stone += stoneAmount;
    resources.leaves += leafAmount;
    resources.fruit += fruitAmount;
    resources.recycling += recyclingAmount;

    log("🌳 Recogiste materiales.");

    updateStats();
    saveGame();
}

// =================================
// PESCA
// =================================

function fish() {

    if (Math.random() < 0.75) {

        fishCount++;

        log("🎣 ¡Has pescado un pez!");

    } else {

        log("🐠 No has pescado nada esta vez.");
    }

    updateStats();
    saveGame();
}

function sellFish() {

    if (fishCount <= 0) {

        log("No tienes peces para vender.");

        return;
    }

    coins += fishCount * 50;

    log("💰 Vendiste " + fishCount + " peces.");

    fishCount = 0;

    updateStats();
    saveGame();
}

// VENDER MATERIALES
function sellMaterials() {
    const prices = { wood: 10, stone: 8, leaves: 5, fruit: 15, recycling: 20 };
    const names = { wood: "madera", stone: "piedra", leaves: "hojas", fruit: "fruta", recycling: "material reciclado" };
    let earned = 0;
    let sold = [];

    for (const material in prices) {
        const amount = resources[material] || 0;
        if (amount > 0) {
            earned += amount * prices[material];
            sold.push(amount + " " + names[material]);
            resources[material] = 0;
        }
    }

    if (earned === 0) {
        log("🧺 No tienes materiales para vender.");
        return;
    }

    coins += earned;
    log("💰 Vendiste " + sold.join(", ") + " y ganaste " + earned + " monedas.");
    updateStats();
    saveGame();
}

function donateFish() {

    if (fishCount <= 0) {

        log("No tienes peces para donar.");

        return;
    }

    donatedFish += fishCount;

    log("🐠 Donaste peces para la colección marina.");

    fishCount = 0;

    happiness += 5;

    updateStats();
    saveGame();
}

function releaseFish() {

    if (fishCount <= 0) {

        log("No tienes peces que liberar.");

        return;
    }

    log("🌊 Liberaste los peces al mar.");

    fishCount = 0;

    happiness += 3;

    updateStats();
    saveGame();
}

// =================================
// HABITANTES
// =================================

function talk(person) {

    if (person === "mia") {

        if (buildings.some(b => b.type === "garden")) {

            coins += 100;

            log("🐰 Mía: ¡Gracias por construir un huerto! +100 monedas.");

        } else {

            log("🐰 Mía: ¿Podrías construir un huerto para nuestra comunidad?");
        }
    }

    if (person === "tom") {

        if (buildings.some(b => b.type === "recyclingCenter")) {

            coins += 100;

            log("🦊 Tom: ¡Gracias por ayudar a reciclar! +100 monedas.");

        } else {

            log("🦊 Tom: Necesitamos un centro de reciclaje.");
        }
    }

    if (person === "lola") {

        if (buildings.some(b => b.type === "beach")) {

            coins += 100;

            happiness += 5;

            log("🐢 Lola: ¡La playa está protegida! +100 monedas.");

        } else {

            log("🐢 Lola: Ayúdame a proteger nuestra playa.");
        }
    }

    updateStats();
    saveGame();
}

// =================================
// CONTAMINACIÓN
// =================================

function calculatePollution() {

    let total = 0;

    buildings.forEach(building => {

        total += buildingData[building.type].pollution;

    });

    total = Math.max(0, total);

    document.getElementById("pollution").innerText = total;

    if (total < 20) {

        document.getElementById("environment").innerText =
        "🌱 ¡Tu isla está muy limpia!";

    } else if (total < 50) {

        document.getElementById("environment").innerText =
        "🌿 La contaminación está controlada.";

    } else {

        document.getElementById("environment").innerText =
        "⚠️ ¡Hay demasiada contaminación!";
    }

    happiness = Math.max(0, 100 - total);

    updateStats();
}

// =================================
// MANTENIMIENTO
// =================================

function repairIsland() {

    if (coins < 100) {

        log("❌ No tienes suficientes monedas.");

        return;
    }

    coins -= 100;

    happiness = Math.min(100, happiness + 10);

    log("🔧 ¡Isla reparada! No pasó ningún día.");

    calculatePollution();
    updateStats();
    saveGame();
}

// =================================
// REFORMAS
// =================================

function reformIsland() {

    if (coins < 200) {

        log("❌ No tienes suficientes monedas.");

        return;
    }

    coins -= 200;

    const factories = buildings.filter(b => b.type === "factory");

    if (factories.length > 0) {

        factories.forEach(f => {

            f.type = "solar";

        });

        log("♻️ Reformaste una fábrica convirtiéndola en energía solar.");

    } else {

        buildings.push({
            type: "park",
            position: findFreeTile()
        });

        log("🌳 Reforma ecológica: añadiste un parque.");
    }

    calculatePollution();
    updateMap();
    updateStats();
    saveGame();
}

// =================================
// NUEVO DÍA
// =================================

function nextDay() {

    day++;

    coins += 100;

    buildings.forEach(building => {

        if (building.type === "shop") coins += 50;

        if (building.type === "garden") {

            resources.fruit += 2;
        }

        if (building.type === "house") {

            happiness += 1;
        }

    });

    log("🌙 ¡Comienza el día " + day + "! Recibiste 100 monedas.");

    updateStats();
    calculatePollution();
    saveGame();
}

// =================================
// CASILLAS LIBRES
// =================================

function findFreeTile() {

    for (let i = 0; i < 100; i++) {

        if (!buildings.some(b => b.position === i)) {

            return i;
        }
    }

    return 0;
}

// =================================
// ESTADÍSTICAS
// =================================

function updateStats() {

    document.getElementById("coins").innerText = coins;

    document.getElementById("day").innerText = day;

    document.getElementById("happiness").innerText =
    Math.min(100, happiness);

    document.getElementById("wood").innerText =
    resources.wood;

    document.getElementById("stone").innerText =
    resources.stone;

    document.getElementById("leaves").innerText =
    resources.leaves;

    document.getElementById("fruit").innerText =
    resources.fruit;

    document.getElementById("recycling").innerText =
    resources.recycling;
}

// =================================
// REGISTRO
// =================================

function log(message) {

    const logBox = document.getElementById("log");

    logBox.innerHTML =
    message + "<br>" + logBox.innerHTML;
}

// =================================
// GUARDAR
// =================================

function saveGame() {

    const data = {
        coins,
        day,
        happiness,
        resources,
        fish: fishCount,
        donatedFish,
        buildings,
        craftedItems
    };

    localStorage.setItem("ecoIslandSave", JSON.stringify(data));
}

// =================================
// CARGAR
// =================================

function loadGame() {

    const saved = localStorage.getItem("ecoIslandSave");

    if (!saved) return;

    const data = JSON.parse(saved);

    coins = data.coins ?? coins;

    day = data.day ?? day;

    happiness = data.happiness ?? happiness;

    resources = data.resources ?? resources;

    fishCount = data.fish ?? 0;

    donatedFish = data.donatedFish ?? 0;

    buildings = data.buildings ?? [];
    craftedItems = data.craftedItems ?? {};
}

// =================================
// INICIAR JUEGO
// =================================

loadGame();

createBuildingCatalog();
createCraftingWorkshop();

createMap();

updateStats();

calculatePollution();

</script>

</body>
</html>

# ECO-ISLAND
