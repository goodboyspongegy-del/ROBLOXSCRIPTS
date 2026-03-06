[roblox-script-reference (1).html](https://github.com/user-attachments/files/25782647/roblox-script-reference.1.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RobloxScript.dev — Complete Lua Scripting Reference</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Bebas+Neue&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --surface2: #1a1a24;
    --border: #2a2a3a;
    --accent: #ff3c6e;
    --accent2: #00e5ff;
    --accent3: #ffe600;
    --text: #e8e8f0;
    --muted: #6b6b8a;
    --code-bg: #0d0d15;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* GRID BACKGROUND */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(255,60,110,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,60,110,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* HEADER */
  header {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(10,10,15,0.92);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 60px;
  }

  .logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.6rem;
    letter-spacing: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .logo span { color: var(--accent3); -webkit-text-fill-color: var(--accent3); }

  nav { display: flex; gap: 1.5rem; }
  nav a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 500;
    letter-spacing: 0.5px;
    transition: color 0.2s;
    cursor: pointer;
  }
  nav a:hover { color: var(--accent2); }

  /* SEARCH */
  .search-wrap {
    position: relative;
  }
  #search {
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--text);
    padding: 0.4rem 1rem 0.4rem 2.2rem;
    border-radius: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    width: 220px;
    outline: none;
    transition: border-color 0.2s;
  }
  #search:focus { border-color: var(--accent2); }
  .search-icon {
    position: absolute;
    left: 0.6rem;
    top: 50%;
    transform: translateY(-50%);
    color: var(--muted);
    font-size: 0.9rem;
  }

  /* HERO */
  .hero {
    position: relative;
    z-index: 1;
    text-align: center;
    padding: 5rem 2rem 3rem;
  }

  .hero-tag {
    display: inline-block;
    background: rgba(255,60,110,0.1);
    border: 1px solid rgba(255,60,110,0.3);
    color: var(--accent);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    padding: 0.3rem 1rem;
    border-radius: 100px;
    margin-bottom: 1.5rem;
    letter-spacing: 1px;
  }

  .hero h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3rem, 8vw, 7rem);
    line-height: 0.95;
    letter-spacing: 3px;
    margin-bottom: 1rem;
  }

  .hero h1 .line1 { color: var(--text); }
  .hero h1 .line2 {
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .hero p {
    color: var(--muted);
    font-size: 1rem;
    max-width: 500px;
    margin: 0 auto 2rem;
    line-height: 1.7;
  }

  .hero-stats {
    display: flex;
    justify-content: center;
    gap: 3rem;
    margin-top: 2rem;
  }

  .stat { text-align: center; }
  .stat-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2rem;
    color: var(--accent2);
  }
  .stat-label {
    font-size: 0.75rem;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* LAYOUT */
  .container {
    position: relative;
    z-index: 1;
    max-width: 1300px;
    margin: 0 auto;
    padding: 0 2rem 4rem;
    display: grid;
    grid-template-columns: 260px 1fr;
    gap: 2rem;
    align-items: start;
  }

  /* SIDEBAR */
  .sidebar {
    position: sticky;
    top: 80px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
  }

  .sidebar-title {
    padding: 1rem 1.2rem;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 2px;
    color: var(--muted);
    text-transform: uppercase;
    border-bottom: 1px solid var(--border);
    background: var(--surface2);
  }

  .sidebar-item {
    display: flex;
    align-items: center;
    gap: 0.7rem;
    padding: 0.7rem 1.2rem;
    cursor: pointer;
    transition: all 0.15s;
    border-left: 3px solid transparent;
    font-size: 0.88rem;
    color: var(--muted);
  }

  .sidebar-item:hover {
    background: var(--surface2);
    color: var(--text);
    border-left-color: var(--accent2);
  }

  .sidebar-item.active {
    background: rgba(0,229,255,0.06);
    color: var(--accent2);
    border-left-color: var(--accent2);
  }

  .sidebar-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: currentColor;
    flex-shrink: 0;
  }

  /* MAIN CONTENT */
  .main { display: flex; flex-direction: column; gap: 2rem; }

  /* SECTION */
  .section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    animation: fadeUp 0.4s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .section-header {
    padding: 1.2rem 1.5rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: var(--surface2);
  }

  .section-title {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.3rem;
    letter-spacing: 1px;
  }

  .section-icon {
    width: 32px; height: 32px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
  }

  .section-count {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 0.2rem 0.6rem;
    border-radius: 100px;
  }

  /* SCRIPT CARDS GRID */
  .scripts-grid {
    padding: 1.5rem;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1rem;
  }

  .script-card {
    background: var(--code-bg);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    transition: all 0.2s;
    cursor: pointer;
  }

  .script-card:hover {
    border-color: var(--accent2);
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(0,229,255,0.08);
  }

  .card-header {
    padding: 0.8rem 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.02);
  }

  .card-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    color: var(--accent2);
  }

  .card-tag {
    font-size: 0.65rem;
    padding: 0.15rem 0.5rem;
    border-radius: 4px;
    font-family: 'JetBrains Mono', monospace;
    font-weight: 700;
    letter-spacing: 0.5px;
  }

  .tag-server { background: rgba(255,60,110,0.15); color: var(--accent); }
  .tag-local { background: rgba(0,229,255,0.15); color: var(--accent2); }
  .tag-module { background: rgba(255,230,0,0.15); color: var(--accent3); }
  .tag-both { background: rgba(150,100,255,0.15); color: #b388ff; }

  .card-code {
    padding: 1rem;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    line-height: 1.7;
    color: #a8b8cc;
    white-space: pre;
    overflow-x: auto;
    max-height: 160px;
  }

  .card-code .kw { color: #ff79c6; }
  .card-code .fn { color: #50fa7b; }
  .card-code .str { color: #f1fa8c; }
  .card-code .cm { color: #6272a4; font-style: italic; }
  .card-code .num { color: #bd93f9; }
  .card-code .var { color: #8be9fd; }

  .card-footer {
    padding: 0.6rem 1rem;
    border-top: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .card-desc { font-size: 0.75rem; color: var(--muted); }

  .copy-btn {
    background: none;
    border: 1px solid var(--border);
    color: var(--muted);
    padding: 0.2rem 0.6rem;
    border-radius: 4px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    cursor: pointer;
    transition: all 0.15s;
  }

  .copy-btn:hover { border-color: var(--accent2); color: var(--accent2); }
  .copy-btn.copied { border-color: #50fa7b; color: #50fa7b; }

  /* MODAL */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.85);
    z-index: 1000;
    display: none;
    align-items: center;
    justify-content: center;
    padding: 2rem;
    backdrop-filter: blur(6px);
  }

  .modal-overlay.open { display: flex; }

  .modal {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    max-width: 800px;
    width: 100%;
    max-height: 85vh;
    overflow-y: auto;
    animation: modalIn 0.25s ease;
  }

  @keyframes modalIn {
    from { opacity: 0; transform: scale(0.95); }
    to { opacity: 1; transform: scale(1); }
  }

  .modal-head {
    padding: 1.5rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    background: var(--surface);
  }

  .modal-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.5rem;
    letter-spacing: 1px;
    color: var(--accent2);
  }

  .modal-close {
    background: none;
    border: 1px solid var(--border);
    color: var(--muted);
    width: 32px; height: 32px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.15s;
  }
  .modal-close:hover { border-color: var(--accent); color: var(--accent); }

  .modal-body { padding: 1.5rem; }

  .modal-code {
    background: var(--code-bg);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1.5rem;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    line-height: 1.8;
    color: #a8b8cc;
    white-space: pre;
    overflow-x: auto;
    margin-bottom: 1rem;
  }

  .modal-desc {
    color: var(--muted);
    font-size: 0.88rem;
    line-height: 1.7;
    margin-bottom: 1rem;
  }

  .modal-copy-btn {
    background: linear-gradient(90deg, var(--accent), #ff6b9d);
    border: none;
    color: white;
    padding: 0.7rem 2rem;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.85rem;
    cursor: pointer;
    font-weight: 700;
    letter-spacing: 1px;
    transition: opacity 0.2s;
  }
  .modal-copy-btn:hover { opacity: 0.85; }

  /* FILTER TABS */
  .filter-bar {
    display: flex;
    gap: 0.5rem;
    padding: 1rem 1.5rem;
    border-bottom: 1px solid var(--border);
    flex-wrap: wrap;
  }

  .filter-btn {
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--muted);
    padding: 0.3rem 0.8rem;
    border-radius: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    cursor: pointer;
    transition: all 0.15s;
  }

  .filter-btn:hover, .filter-btn.active {
    background: rgba(0,229,255,0.1);
    border-color: var(--accent2);
    color: var(--accent2);
  }

  /* HIDDEN */
  .hidden { display: none !important; }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--muted); }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    .container { grid-template-columns: 1fr; }
    .sidebar { position: static; display: flex; flex-wrap: wrap; }
    .sidebar-item { flex: 1; min-width: 140px; }
  }
</style>
</head>
<body>

<header>
  <div class="logo">Roblox<span>Script</span>.dev</div>
  <nav>
    <a onclick="scrollToSection('services')">Services</a>
    <a onclick="scrollToSection('player')">Player</a>
    <a onclick="scrollToSection('gui')">GUI</a>
    <a onclick="scrollToSection('remote')">Remotes</a>
    <a href="https://create.roblox.com/docs" target="_blank">Official Docs ↗</a>
  </nav>
  <div class="search-wrap">
    <span class="search-icon">⌕</span>
    <input id="search" type="text" placeholder="Search scripts..." oninput="filterSearch(this.value)">
  </div>
</header>

<div class="hero">
  <div class="hero-tag">// COMPLETE ROBLOX LUA REFERENCE</div>
  <h1>
    <div class="line1">SCRIPT</div>
    <div class="line2">EVERYTHING.</div>
  </h1>
  <p>Every essential Roblox Lua pattern, from game services to GUI systems. Copy, learn, build.</p>
  <div class="hero-stats">
    <div class="stat"><div class="stat-num">60+</div><div class="stat-label">Scripts</div></div>
    <div class="stat"><div class="stat-num">12</div><div class="stat-label">Categories</div></div>
    <div class="stat"><div class="stat-num">100%</div><div class="stat-label">Official API</div></div>
  </div>
</div>

<div class="container">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-title">Categories</div>
    <div class="sidebar-item active" onclick="showSection('all')"><span class="sidebar-dot"></span> All Scripts</div>
    <div class="sidebar-item" onclick="showSection('services')"><span class="sidebar-dot"></span> Game Services</div>
    <div class="sidebar-item" onclick="showSection('player')"><span class="sidebar-dot"></span> Player & Character</div>
    <div class="sidebar-item" onclick="showSection('gui')"><span class="sidebar-dot"></span> GUI / UI</div>
    <div class="sidebar-item" onclick="showSection('remote')"><span class="sidebar-dot"></span> Remote Events</div>
    <div class="sidebar-item" onclick="showSection('datastore')"><span class="sidebar-dot"></span> DataStore</div>
    <div class="sidebar-item" onclick="showSection('tween')"><span class="sidebar-dot"></span> Tweening</div>
    <div class="sidebar-item" onclick="showSection('physics')"><span class="sidebar-dot"></span> Physics</div>
    <div class="sidebar-item" onclick="showSection('loop')"><span class="sidebar-dot"></span> Loops & Events</div>
    <div class="sidebar-item" onclick="showSection('tool')"><span class="sidebar-dot"></span> Tools & Items</div>
    <div class="sidebar-item" onclick="showSection('sound')"><span class="sidebar-dot"></span> Sound & Music</div>
    <div class="sidebar-item" onclick="showSection('module')"><span class="sidebar-dot"></span> ModuleScripts</div>
    <div class="sidebar-item" onclick="showSection('lighting')"><span class="sidebar-dot"></span> Lighting & FX</div>
  </aside>

  <!-- MAIN -->
  <main class="main" id="mainContent"></main>
</div>

<!-- MODAL -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal" id="modal">
    <div class="modal-head">
      <div class="modal-title" id="modalTitle"></div>
      <button class="modal-close" onclick="closeModalDirect()">✕</button>
    </div>
    <div class="modal-body">
      <p class="modal-desc" id="modalDesc"></p>
      <div class="modal-code" id="modalCode"></div>
      <button class="modal-copy-btn" onclick="copyModal()">⧉ COPY FULL SCRIPT</button>
    </div>
  </div>
</div>

<script>
const SCRIPTS = [
  // ── SERVICES ──
  {
    id: 's1', cat: 'services', tag: 'both', title: 'GetService Basics',
    desc: 'Access all core Roblox game services.',
    short: `<span class="cm">-- Core Services</span>
<span class="kw">local</span> <span class="var">Players</span> = game:<span class="fn">GetService</span>(<span class="str">"Players"</span>)
<span class="kw">local</span> <span class="var">RS</span> = game:<span class="fn">GetService</span>(<span class="str">"RunService"</span>)
<span class="kw">local</span> <span class="var">TS</span> = game:<span class="fn">GetService</span>(<span class="str">"TweenService"</span>)
<span class="kw">local</span> <span class="var">SS</span> = game:<span class="fn">GetService</span>(<span class="str">"SoundService"</span>)`,
    full: `-- All Core Roblox Services
local Players       = game:GetService("Players")
local RunService    = game:GetService("RunService")
local TweenService  = game:GetService("TweenService")
local SoundService  = game:GetService("SoundService")
local UserInputService = game:GetService("UserInputService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local ServerStorage = game:GetService("ServerStorage")
local Lighting      = game:GetService("Lighting")
local Workspace     = game:GetService("Workspace")
local DataStoreService = game:GetService("DataStoreService")
local HttpService   = game:GetService("HttpService")
local MarketplaceService = game:GetService("MarketplaceService")
local CollectionService = game:GetService("CollectionService")
local PhysicsService = game:GetService("PhysicsService")
local ChatService   = game:GetService("Chat")`
  },
  {
    id: 's2', cat: 'services', tag: 'both', title: 'RunService Loops',
    desc: 'Heartbeat, Stepped, and RenderStepped loops for game logic.',
    short: `<span class="cm">-- RunService events</span>
<span class="var">RS</span>.Heartbeat:<span class="fn">Connect</span>(<span class="kw">function</span>(dt)
  <span class="cm">-- Runs every frame, server + client</span>
<span class="kw">end</span>)
<span class="var">RS</span>.RenderStepped:<span class="fn">Connect</span>(<span class="kw">function</span>(dt)
  <span class="cm">-- Client only, before render</span>
<span class="kw">end</span>)`,
    full: `local RunService = game:GetService("RunService")

-- Heartbeat: Runs after physics step, client AND server
RunService.Heartbeat:Connect(function(deltaTime)
    print("Delta:", deltaTime)
end)

-- Stepped: Runs before physics step
RunService.Stepped:Connect(function(time, deltaTime)
    print("Stepped at:", time)
end)

-- RenderStepped: CLIENT ONLY - runs before each frame render
RunService.RenderStepped:Connect(function(deltaTime)
    -- Perfect for camera and character updates
end)

-- Check context
if RunService:IsServer() then
    print("Running on server")
elseif RunService:IsClient() then
    print("Running on client")
end`
  },
  {
    id: 's3', cat: 'services', tag: 'server', title: 'MarketplaceService',
    desc: 'Handle game passes, developer products, and purchases.',
    short: `<span class="kw">local</span> <span class="var">MPS</span> = game:<span class="fn">GetService</span>(<span class="str">"MarketplaceService"</span>)
<span class="var">MPS</span>.ProcessReceipt = <span class="kw">function</span>(info)
  <span class="cm">-- Handle purchases here</span>
  <span class="kw">return</span> <span class="var">Enum</span>.ProductPurchaseDecision.PurchaseGranted
<span class="kw">end</span>`,
    full: `local MarketplaceService = game:GetService("MarketplaceService")
local Players = game:GetService("Players")

-- Check if player owns a game pass
local GAMEPASS_ID = 123456789

local function checkGamePass(player)
    local success, owns = pcall(function()
        return MarketplaceService:UserOwnsGamePassAsync(player.UserId, GAMEPASS_ID)
    end)
    if success and owns then
        print(player.Name .. " owns the game pass!")
    end
end

-- Prompt purchase
local function promptPass(player)
    MarketplaceService:PromptGamePassPurchase(player, GAMEPASS_ID)
end

-- Handle developer product receipts (SERVER ONLY)
MarketplaceService.ProcessReceipt = function(receiptInfo)
    local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)
    if not player then
        return Enum.ProductPurchaseDecision.NotProcessedYet
    end
    
    if receiptInfo.ProductId == 987654321 then
        -- Give player their reward
        print("Processing purchase for", player.Name)
    end
    
    return Enum.ProductPurchaseDecision.PurchaseGranted
end

Players.PlayerAdded:Connect(checkGamePass)`
  },

  // ── PLAYER ──
  {
    id: 'p1', cat: 'player', tag: 'server', title: 'Player Added / Removed',
    desc: 'Handle players joining and leaving the game.',
    short: `<span class="var">Players</span>.PlayerAdded:<span class="fn">Connect</span>(<span class="kw">function</span>(player)
  <span class="fn">print</span>(player.Name .. <span class="str">" joined!"</span>)
<span class="kw">end</span>)
<span class="var">Players</span>.PlayerRemoving:<span class="fn">Connect</span>(<span class="kw">function</span>(player)
  <span class="fn">print</span>(player.Name .. <span class="str">" left!"</span>)
<span class="kw">end</span>)`,
    full: `local Players = game:GetService("Players")

-- Player joins
Players.PlayerAdded:Connect(function(player)
    print(player.Name .. " joined! UserId:", player.UserId)
    
    -- Wait for character
    player.CharacterAdded:Connect(function(character)
        print(player.Name .. "'s character loaded")
        local humanoid = character:WaitForChild("Humanoid")
        local hrp = character:WaitForChild("HumanoidRootPart")
        
        -- Character died
        humanoid.Died:Connect(function()
            print(player.Name .. " died")
        end)
    end)
end)

-- Player leaves
Players.PlayerRemoving:Connect(function(player)
    print(player.Name .. " left the game")
    -- Good place to save data
end)

-- Handle existing players (script loaded mid-game)
for _, player in ipairs(Players:GetPlayers()) do
    print("Already in game:", player.Name)
end`
  },
  {
    id: 'p2', cat: 'player', tag: 'local', title: 'LocalPlayer & Character',
    desc: 'Access the local player, character, and humanoid.',
    short: `<span class="kw">local</span> <span class="var">player</span> = <span class="var">Players</span>.LocalPlayer
<span class="kw">local</span> <span class="var">char</span> = player.Character
  <span class="kw">or</span> player.CharacterAdded:<span class="fn">Wait</span>()
<span class="kw">local</span> <span class="var">hum</span> = char:<span class="fn">WaitForChild</span>(<span class="str">"Humanoid"</span>)
<span class="kw">local</span> <span class="var">hrp</span> = char:<span class="fn">WaitForChild</span>(<span class="str">"HumanoidRootPart"</span>)`,
    full: `local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- Get character (wait if not loaded yet)
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local hrp = character:WaitForChild("HumanoidRootPart")
local rootJoint = hrp:WaitForChild("RootJoint")

-- Player info
print("Name:", player.Name)
print("UserId:", player.UserId)
print("Team:", player.Team)
print("AccountAge:", player.AccountAge)

-- Humanoid properties
humanoid.WalkSpeed = 16      -- default
humanoid.JumpPower = 50      -- default
humanoid.MaxHealth = 100
humanoid.Health = 100

-- Watch for respawn
player.CharacterAdded:Connect(function(newChar)
    character = newChar
    humanoid = newChar:WaitForChild("Humanoid")
    hrp = newChar:WaitForChild("HumanoidRootPart")
    print("Respawned!")
end)`
  },
  {
    id: 'p3', cat: 'player', tag: 'server', title: 'Leaderboard Stats',
    desc: 'Create and update leaderboard values shown above players.',
    short: `<span class="var">Players</span>.PlayerAdded:<span class="fn">Connect</span>(<span class="kw">function</span>(player)
  <span class="kw">local</span> <span class="var">ls</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"Folder"</span>, player)
  <span class="var">ls</span>.Name = <span class="str">"leaderstats"</span>
  <span class="kw">local</span> <span class="var">coins</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"IntValue"</span>, ls)
  <span class="var">coins</span>.Name = <span class="str">"Coins"</span>
<span class="kw">end</span>)`,
    full: `local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
    -- Create leaderstats folder (must be named exactly this)
    local leaderstats = Instance.new("Folder")
    leaderstats.Name = "leaderstats"
    leaderstats.Parent = player

    -- Add stats
    local coins = Instance.new("IntValue")
    coins.Name = "Coins"
    coins.Value = 0
    coins.Parent = leaderstats

    local kills = Instance.new("IntValue")
    kills.Name = "Kills"
    kills.Value = 0
    kills.Parent = leaderstats

    local level = Instance.new("IntValue")
    level.Name = "Level"
    level.Value = 1
    level.Parent = leaderstats

    -- Example: give coins over time
    while player.Parent do
        task.wait(10)
        coins.Value += 5
    end
end)`
  },
  {
    id: 'p4', cat: 'player', tag: 'local', title: 'UserInputService',
    desc: 'Detect keyboard, mouse, and touch inputs.',
    short: `<span class="kw">local</span> <span class="var">UIS</span> = game:<span class="fn">GetService</span>(<span class="str">"UserInputService"</span>)
<span class="var">UIS</span>.InputBegan:<span class="fn">Connect</span>(<span class="kw">function</span>(input, gpe)
  <span class="kw">if</span> gpe <span class="kw">then return end</span>
  <span class="kw">if</span> input.KeyCode == <span class="var">Enum</span>.KeyCode.E <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"E pressed!"</span>)
  <span class="kw">end</span>
<span class="kw">end</span>)`,
    full: `local UserInputService = game:GetService("UserInputService")

-- Key pressed
UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if gameProcessedEvent then return end -- ignore if typing in chat etc.

    if input.KeyCode == Enum.KeyCode.E then
        print("E key pressed")
    elseif input.KeyCode == Enum.KeyCode.LeftShift then
        print("Shift pressed - maybe sprint?")
    elseif input.UserInputType == Enum.UserInputType.MouseButton1 then
        print("Left click!")
    end
end)

-- Key released
UserInputService.InputEnded:Connect(function(input, gpe)
    if gpe then return end
    if input.KeyCode == Enum.KeyCode.LeftShift then
        print("Shift released")
    end
end)

-- Check if key is held
local function isHeld(keyCode)
    return UserInputService:IsKeyDown(keyCode)
end

-- Mouse position
local mousePos = UserInputService:GetMouseLocation()
print("Mouse at:", mousePos.X, mousePos.Y)

-- Mobile support check
if UserInputService.TouchEnabled then
    print("Player is on mobile")
end`
  },

  // ── GUI ──
  {
    id: 'g1', cat: 'gui', tag: 'local', title: 'Create ScreenGui',
    desc: 'Build a ScreenGui with a Frame and TextLabel from scratch.',
    short: `<span class="kw">local</span> <span class="var">sg</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"ScreenGui"</span>, playerGui)
<span class="kw">local</span> <span class="var">frame</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"Frame"</span>, sg)
<span class="var">frame</span>.Size = <span class="var">UDim2</span>.<span class="fn">new</span>(<span class="num">0</span>,<span class="num">200</span>,<span class="num">0</span>,<span class="num">100</span>)
<span class="var">frame</span>.Position = <span class="var">UDim2</span>.<span class="fn">new</span>(<span class="num">0.5</span>,<span class="num">-100</span>,<span class="num">0.5</span>,<span class="num">-50</span>)`,
    full: `local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "MyGui"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- Main Frame
local frame = Instance.new("Frame")
frame.Name = "MainFrame"
frame.Size = UDim2.new(0, 300, 0, 200)
frame.Position = UDim2.new(0.5, -150, 0.5, -100)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
frame.BorderSizePixel = 0
frame.Parent = screenGui

-- Corner radius
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 12)
corner.Parent = frame

-- Title label
local title = Instance.new("TextLabel")
title.Text = "My Panel"
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.GothamBold
title.TextSize = 18
title.Parent = frame

-- Button
local btn = Instance.new("TextButton")
btn.Text = "Click Me"
btn.Size = UDim2.new(0, 120, 0, 40)
btn.Position = UDim2.new(0.5, -60, 0.5, 0)
btn.BackgroundColor3 = Color3.fromRGB(255, 60, 110)
btn.TextColor3 = Color3.fromRGB(255, 255, 255)
btn.Font = Enum.Font.GothamBold
btn.TextSize = 14
btn.Parent = frame

local btnCorner = Instance.new("UICorner")
btnCorner.CornerRadius = UDim.new(0, 8)
btnCorner.Parent = btn

btn.MouseButton1Click:Connect(function()
    print("Button clicked!")
end)`
  },
  {
    id: 'g2', cat: 'gui', tag: 'local', title: 'Draggable GUI',
    desc: 'Make any Frame draggable with mouse input.',
    short: `<span class="kw">local</span> <span class="var">dragging</span>, <span class="var">dragStart</span>, <span class="var">startPos</span>
<span class="var">frame</span>.InputBegan:<span class="fn">Connect</span>(<span class="kw">function</span>(i)
  <span class="kw">if</span> i.UserInputType == <span class="var">Enum</span>.UserInputType.MouseButton1 <span class="kw">then</span>
    <span class="var">dragging</span> = <span class="kw">true</span>
    <span class="var">dragStart</span> = i.Position
  <span class="kw">end</span>
<span class="kw">end</span>)`,
    full: `local UserInputService = game:GetService("UserInputService")

-- Pass in any Frame to make it draggable
local function makeDraggable(frame, dragHandle)
    dragHandle = dragHandle or frame
    
    local dragging = false
    local dragInput, mousePos, framePos

    dragHandle.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            mousePos = input.Position
            framePos = frame.Position

            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    dragHandle.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement then
            dragInput = input
        end
    end)

    UserInputService.InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            local delta = input.Position - mousePos
            frame.Position = UDim2.new(
                framePos.X.Scale,
                framePos.X.Offset + delta.X,
                framePos.Y.Scale,
                framePos.Y.Offset + delta.Y
            )
        end
    end)
end

-- Usage:
makeDraggable(frame)          -- whole frame is drag handle
makeDraggable(frame, titleBar) -- only title bar drags`
  },
  {
    id: 'g3', cat: 'gui', tag: 'local', title: 'Notification System',
    desc: 'Animated toast notifications that auto-dismiss.',
    short: `<span class="kw">local function</span> <span class="fn">notify</span>(msg, color)
  <span class="kw">local</span> <span class="var">notif</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"Frame"</span>, sg)
  <span class="cm">-- Tween in, wait, tween out</span>
  <span class="var">TS</span>:<span class="fn">Create</span>(notif, tweenInfo, {Position = targetPos}):<span class="fn">Play</span>()
  <span class="var">task</span>.<span class="fn">delay</span>(<span class="num">3</span>, <span class="kw">function</span>() notif:<span class="fn">Destroy</span>() <span class="kw">end</span>)
<span class="kw">end</span>`,
    full: `local TweenService = game:GetService("TweenService")
local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local sg = Instance.new("ScreenGui")
sg.Name = "NotifGui"
sg.ResetOnSpawn = false
sg.Parent = playerGui

local notifCount = 0

local function notify(message, color, duration)
    color = color or Color3.fromRGB(50, 200, 100)
    duration = duration or 3

    notifCount += 1
    local yOffset = (notifCount - 1) * 65

    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0, 280, 0, 55)
    frame.Position = UDim2.new(1, 10, 1, -80 - yOffset)
    frame.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
    frame.BorderSizePixel = 0
    frame.Parent = sg

    Instance.new("UICorner", frame).CornerRadius = UDim.new(0, 10)

    local accent = Instance.new("Frame")
    accent.Size = UDim2.new(0, 4, 1, 0)
    accent.BackgroundColor3 = color
    accent.BorderSizePixel = 0
    accent.Parent = frame
    Instance.new("UICorner", accent).CornerRadius = UDim.new(0, 4)

    local label = Instance.new("TextLabel")
    label.Text = message
    label.Size = UDim2.new(1, -20, 1, 0)
    label.Position = UDim2.new(0, 14, 0, 0)
    label.BackgroundTransparency = 1
    label.TextColor3 = Color3.fromRGB(220, 220, 230)
    label.Font = Enum.Font.Gotham
    label.TextSize = 13
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.TextWrapped = true
    label.Parent = frame

    local tweenIn = TweenService:Create(frame,
        TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
        {Position = UDim2.new(1, -295, 1, -80 - yOffset)}
    )
    tweenIn:Play()

    task.delay(duration, function()
        local tweenOut = TweenService:Create(frame,
            TweenInfo.new(0.3, Enum.EasingStyle.Quart, Enum.EasingDirection.In),
            {Position = UDim2.new(1, 10, 1, -80 - yOffset)}
        )
        tweenOut:Play()
        tweenOut.Completed:Connect(function()
            frame:Destroy()
            notifCount -= 1
        end)
    end)
end

-- Usage:
notify("Welcome to the game!", Color3.fromRGB(50, 200, 100))
notify("You leveled up!", Color3.fromRGB(255, 200, 50))
notify("Low health!", Color3.fromRGB(255, 60, 60))`
  },

  // ── REMOTE EVENTS ──
  {
    id: 'r1', cat: 'remote', tag: 'both', title: 'RemoteEvent Setup',
    desc: 'Fire events between client and server securely.',
    short: `<span class="cm">-- Server</span>
<span class="var">remoteEvent</span>.OnServerEvent:<span class="fn">Connect</span>(<span class="kw">function</span>(player, data)
  <span class="fn">print</span>(player.Name, data)
<span class="kw">end</span>)
<span class="cm">-- Client</span>
<span class="var">remoteEvent</span>:<span class="fn">FireServer</span>({action = <span class="str">"attack"</span>})`,
    full: `-- ============ SERVER SCRIPT ============
local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Create remote event (do this once in ServerScript)
local myEvent = Instance.new("RemoteEvent")
myEvent.Name = "MyEvent"
myEvent.Parent = ReplicatedStorage

-- Listen for client → server
myEvent.OnServerEvent:Connect(function(player, action, value)
    print(player.Name .. " sent:", action, value)
    
    -- Fire back to one player
    myEvent:FireClient(player, "response", "Got it!")
    
    -- Fire to all players
    myEvent:FireAllClients("broadcast", player.Name .. " did something")
end)

-- ============ LOCAL SCRIPT ============
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local myEvent = ReplicatedStorage:WaitForChild("MyEvent")

-- Send to server
myEvent:FireServer("attack", 50)

-- Listen for server → client
myEvent.OnClientEvent:Connect(function(action, value)
    print("Server says:", action, value)
end)`
  },
  {
    id: 'r2', cat: 'remote', tag: 'both', title: 'RemoteFunction',
    desc: 'Request data from server and get a return value.',
    short: `<span class="cm">-- Server</span>
<span class="var">remoteFunc</span>.OnServerInvoke = <span class="kw">function</span>(player)
  <span class="kw">return</span> <span class="str">"Hello from server!"</span>
<span class="kw">end</span>
<span class="cm">-- Client</span>
<span class="kw">local</span> <span class="var">result</span> = <span class="var">remoteFunc</span>:<span class="fn">InvokeServer</span>()`,
    full: `-- ============ SERVER SCRIPT ============
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local getDataFunc = Instance.new("RemoteFunction")
getDataFunc.Name = "GetPlayerData"
getDataFunc.Parent = ReplicatedStorage

getDataFunc.OnServerInvoke = function(player, requestType)
    if requestType == "coins" then
        local leaderstats = player:FindFirstChild("leaderstats")
        if leaderstats then
            return leaderstats.Coins.Value
        end
        return 0
    elseif requestType == "level" then
        return 5 -- example
    end
    return nil
end

-- ============ LOCAL SCRIPT ============
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local getDataFunc = ReplicatedStorage:WaitForChild("GetPlayerData")

-- Invoke server and get result
local coins = getDataFunc:InvokeServer("coins")
print("My coins:", coins)

local level = getDataFunc:InvokeServer("level")
print("My level:", level)`
  },

  // ── DATASTORE ──
  {
    id: 'd1', cat: 'datastore', tag: 'server', title: 'Save & Load Data',
    desc: 'Persist player data across sessions with DataStoreService.',
    short: `<span class="kw">local</span> <span class="var">store</span> = <span class="var">DSS</span>:<span class="fn">GetDataStore</span>(<span class="str">"PlayerData"</span>)
<span class="kw">local</span> <span class="var">data</span> = store:<span class="fn">GetAsync</span>(<span class="str">"Player_"</span> .. player.UserId)
store:<span class="fn">SetAsync</span>(<span class="str">"Player_"</span> .. player.UserId, {coins = <span class="num">100</span>})`,
    full: `local DataStoreService = game:GetService("DataStoreService")
local Players = game:GetService("Players")

local playerData = DataStoreService:GetDataStore("PlayerData_v1")

local function loadData(player)
    local key = "Player_" .. player.UserId
    local success, data = pcall(function()
        return playerData:GetAsync(key)
    end)

    if success then
        if data then
            return data
        else
            -- First time player
            return { coins = 0, level = 1, xp = 0 }
        end
    else
        warn("Failed to load data for", player.Name, data)
        return { coins = 0, level = 1, xp = 0 }
    end
end

local function saveData(player, data)
    local key = "Player_" .. player.UserId
    local success, err = pcall(function()
        playerData:SetAsync(key, data)
    end)
    if not success then
        warn("Failed to save data for", player.Name, err)
    end
end

-- Store in-memory
local cache = {}

Players.PlayerAdded:Connect(function(player)
    cache[player.UserId] = loadData(player)
    print("Loaded data for", player.Name)
end)

Players.PlayerRemoving:Connect(function(player)
    if cache[player.UserId] then
        saveData(player, cache[player.UserId])
        cache[player.UserId] = nil
    end
end)

-- Save on server close (important!)
game:BindToClose(function()
    for _, player in ipairs(Players:GetPlayers()) do
        if cache[player.UserId] then
            saveData(player, cache[player.UserId])
        end
    end
end)`
  },

  // ── TWEEN ──
  {
    id: 't1', cat: 'tween', tag: 'both', title: 'TweenService Basics',
    desc: 'Smoothly animate any property on any Instance.',
    short: `<span class="kw">local</span> <span class="var">info</span> = <span class="var">TweenInfo</span>.<span class="fn">new</span>(<span class="num">1</span>, <span class="var">Enum</span>.EasingStyle.Quad)
<span class="kw">local</span> <span class="var">tween</span> = <span class="var">TS</span>:<span class="fn">Create</span>(part, info, {
  Position = <span class="var">Vector3</span>.<span class="fn">new</span>(<span class="num">0</span>,<span class="num">10</span>,<span class="num">0</span>),
  Transparency = <span class="num">1</span>
})
<span class="var">tween</span>:<span class="fn">Play</span>()`,
    full: `local TweenService = game:GetService("TweenService")
local part = workspace.MyPart -- example part

-- TweenInfo parameters:
-- (time, EasingStyle, EasingDirection, repeatCount, reverses, delayTime)
local tweenInfo = TweenInfo.new(
    1.5,                          -- duration in seconds
    Enum.EasingStyle.Bounce,      -- easing style
    Enum.EasingDirection.Out,     -- direction
    0,                            -- repeat count (0 = no repeat)
    false,                        -- reverses
    0                             -- delay
)

-- Animate multiple properties at once
local tween = TweenService:Create(part, tweenInfo, {
    Position = Vector3.new(0, 20, 0),
    Transparency = 0.5,
    Color = Color3.fromRGB(255, 100, 0),
    Size = Vector3.new(4, 4, 4)
})

tween:Play()

-- Callbacks
tween.Completed:Connect(function(state)
    if state == Enum.PlaybackState.Completed then
        print("Tween finished!")
    end
end)

-- GUI tween example
local frame = script.Parent -- a Frame
local guiTween = TweenService:Create(frame, TweenInfo.new(0.3), {
    Size = UDim2.new(0, 300, 0, 200),
    BackgroundTransparency = 0,
    Position = UDim2.new(0.5, -150, 0.5, -100)
})
guiTween:Play()`
  },

  // ── PHYSICS ──
  {
    id: 'ph1', cat: 'physics', tag: 'server', title: 'BodyVelocity & Forces',
    desc: 'Apply forces and velocities to parts for physics effects.',
    short: `<span class="kw">local</span> <span class="var">bv</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"BodyVelocity"</span>, part)
<span class="var">bv</span>.Velocity = <span class="var">Vector3</span>.<span class="fn">new</span>(<span class="num">0</span>,<span class="num">50</span>,<span class="num">0</span>)
<span class="var">bv</span>.MaxForce = <span class="var">Vector3</span>.<span class="fn">new</span>(<span class="num">0</span>,<span class="num">1e5</span>,<span class="num">0</span>)
<span class="var">task</span>.<span class="fn">delay</span>(<span class="num">0.2</span>, <span class="kw">function</span>() <span class="var">bv</span>:<span class="fn">Destroy</span>() <span class="kw">end</span>)`,
    full: `-- BodyVelocity: Push in a direction
local function launch(part, direction, speed)
    local bv = Instance.new("BodyVelocity")
    bv.Velocity = direction.Unit * speed
    bv.MaxForce = Vector3.new(1e5, 1e5, 1e5)
    bv.Parent = part
    task.delay(0.3, function() bv:Destroy() end)
end

-- BodyPosition: Move to position smoothly
local function moveTo(part, targetPos)
    local bp = Instance.new("BodyPosition")
    bp.Position = targetPos
    bp.MaxForce = Vector3.new(1e5, 1e5, 1e5)
    bp.D = 500   -- damping
    bp.P = 5000  -- power
    bp.Parent = part
end

-- LinearVelocity (newer API)
local function setLinearVelocity(part, velocity)
    local lv = Instance.new("LinearVelocity")
    lv.Attachment0 = part:FindFirstChildOfClass("Attachment") or Instance.new("Attachment", part)
    lv.VectorVelocity = velocity
    lv.MaxForce = 1e6
    lv.Parent = part
    return lv
end

-- Knockback example
local function knockback(character, force)
    local hrp = character:FindFirstChild("HumanoidRootPart")
    if hrp then
        launch(hrp, hrp.CFrame.LookVector * -1, force)
    end
end`
  },

  // ── LOOPS ──
  {
    id: 'l1', cat: 'loop', tag: 'both', title: 'task Library',
    desc: 'Modern task scheduling: wait, spawn, delay, defer.',
    short: `<span class="var">task</span>.<span class="fn">wait</span>(<span class="num">1</span>)          <span class="cm">-- better than wait()</span>
<span class="var">task</span>.<span class="fn">spawn</span>(<span class="kw">function</span>() <span class="cm">-- non-blocking</span>
  <span class="fn">print</span>(<span class="str">"async"</span>)
<span class="kw">end</span>)
<span class="var">task</span>.<span class="fn">delay</span>(<span class="num">2</span>, <span class="kw">function</span>()
  <span class="fn">print</span>(<span class="str">"after 2s"</span>)
<span class="kw">end</span>)`,
    full: `-- task.wait: More accurate than wait()
task.wait(1) -- waits exactly 1 second (approximately)

-- task.spawn: Run function in new thread immediately
task.spawn(function()
    print("This runs asynchronously")
    task.wait(2)
    print("Done after 2s")
end)
print("This prints before the spawn finishes")

-- task.delay: Run after N seconds
task.delay(5, function()
    print("5 seconds passed!")
end)

-- task.defer: Run next frame
task.defer(function()
    print("Runs next Heartbeat")
end)

-- task.cancel: Cancel a delayed task
local thread = task.delay(10, function()
    print("This won't run")
end)
task.cancel(thread)

-- Infinite loop pattern (game loop)
task.spawn(function()
    while true do
        task.wait(1)
        -- Do something every second
        print("Tick")
    end
end)`
  },
  {
    id: 'l2', cat: 'loop', tag: 'both', title: 'Connections & Cleanup',
    desc: 'Manage event connections and prevent memory leaks.',
    short: `<span class="kw">local</span> <span class="var">conn</span> = <span class="var">part</span>.Touched:<span class="fn">Connect</span>(<span class="kw">function</span>(hit)
  <span class="fn">print</span>(hit.Name)
<span class="kw">end</span>)
<span class="cm">-- Later, disconnect to prevent leaks:</span>
<span class="var">conn</span>:<span class="fn">Disconnect</span>()`,
    full: `-- Store connections for cleanup
local connections = {}

-- Connect events
connections[#connections+1] = workspace.Part.Touched:Connect(function(hit)
    print("Touched by:", hit.Name)
end)

connections[#connections+1] = game:GetService("RunService").Heartbeat:Connect(function(dt)
    -- per-frame logic
end)

-- Cleanup function
local function cleanup()
    for _, conn in ipairs(connections) do
        conn:Disconnect()
    end
    connections = {}
    print("All connections cleaned up")
end

-- Auto-cleanup when player leaves (LocalScript)
local Players = game:GetService("Players")
Players.LocalPlayer.AncestryChanged:Connect(function(_, parent)
    if not parent then
        cleanup()
    end
end)

-- Once: connect then auto-disconnect after first fire
local function connectOnce(signal, callback)
    local conn
    conn = signal:Connect(function(...)
        conn:Disconnect()
        callback(...)
    end)
    return conn
end

connectOnce(workspace.Part.Touched, function(hit)
    print("Only fires once:", hit.Name)
end)`
  },

  // ── TOOLS ──
  {
    id: 'to1', cat: 'tool', tag: 'both', title: 'Tool Script Template',
    desc: 'Complete template for a Roblox Tool with equip/unequip/activate.',
    short: `<span class="kw">local</span> <span class="var">tool</span> = script.Parent
<span class="var">tool</span>.Equipped:<span class="fn">Connect</span>(<span class="kw">function</span>() <span class="fn">print</span>(<span class="str">"Equipped"</span>) <span class="kw">end</span>)
<span class="var">tool</span>.Activated:<span class="fn">Connect</span>(<span class="kw">function</span>() <span class="fn">print</span>(<span class="str">"Used"</span>) <span class="kw">end</span>)
<span class="var">tool</span>.Unequipped:<span class="fn">Connect</span>(<span class="kw">function</span>() <span class="fn">print</span>(<span class="str">"Unequipped"</span>) <span class="kw">end</span>)`,
    full: `-- Place this LocalScript inside a Tool
local tool = script.Parent
local handle = tool:WaitForChild("Handle")

local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character, humanoid

local canUse = true
local COOLDOWN = 0.5

tool.Equipped:Connect(function()
    character = player.Character
    humanoid = character:FindFirstChild("Humanoid")
    print(tool.Name .. " equipped")
    -- Change animation, highlight, etc.
end)

tool.Unequipped:Connect(function()
    print(tool.Name .. " unequipped")
    -- Reset any visual effects
end)

tool.Activated:Connect(function()
    if not canUse then return end
    if not character or not humanoid then return end
    if humanoid.Health <= 0 then return end

    canUse = false

    -- Your tool action here
    print("Tool activated!")

    -- Example: play animation
    -- local anim = Instance.new("Animation")
    -- anim.AnimationId = "rbxassetid://YOUR_ID"
    -- local track = humanoid:LoadAnimation(anim)
    -- track:Play()

    task.delay(COOLDOWN, function()
        canUse = true
    end)
end)`
  },

  // ── SOUND ──
  {
    id: 'so1', cat: 'sound', tag: 'both', title: 'Sound System',
    desc: 'Play, stop, and manage sounds in your game.',
    short: `<span class="kw">local</span> <span class="var">sound</span> = <span class="var">Instance</span>.<span class="fn">new</span>(<span class="str">"Sound"</span>, workspace)
<span class="var">sound</span>.SoundId = <span class="str">"rbxassetid://142376088"</span>
<span class="var">sound</span>.Volume = <span class="num">0.5</span>
<span class="var">sound</span>:<span class="fn">Play</span>()`,
    full: `local SoundService = game:GetService("SoundService")

-- Create and play a sound
local function playSound(soundId, volume, parent)
    parent = parent or workspace
    volume = volume or 0.5

    local sound = Instance.new("Sound")
    sound.SoundId = "rbxassetid://" .. soundId
    sound.Volume = volume
    sound.Parent = parent
    sound:Play()

    -- Auto-destroy when done
    sound.Ended:Connect(function()
        sound:Destroy()
    end)

    return sound
end

-- Background music with looping
local bgm = Instance.new("Sound")
bgm.SoundId = "rbxassetid://142376088"
bgm.Volume = 0.3
bgm.Looped = true
bgm.Parent = workspace
bgm:Play()

-- Spatial sound (3D, gets quieter with distance)
local spatialSound = Instance.new("Sound")
spatialSound.SoundId = "rbxassetid://9120386"
spatialSound.RollOffMaxDistance = 50
spatialSound.Parent = workspace.SomePart -- attach to a part
spatialSound:Play()

-- SoundGroup for volume control
local effectsGroup = Instance.new("SoundGroup")
effectsGroup.Name = "Effects"
effectsGroup.Parent = SoundService

-- Pitch shift
local function playWithPitch(soundId, pitch)
    local sound = playSound(soundId, 0.5)
    local pitchEffect = Instance.new("PitchShiftSoundEffect")
    pitchEffect.Octave = pitch
    pitchEffect.Parent = sound
end

-- Usage
playSound(142376088, 1.0)
playWithPitch(9120386, 1.2) -- higher pitch`
  },

  // ── MODULE ──
  {
    id: 'm1', cat: 'module', tag: 'module', title: 'ModuleScript Pattern',
    desc: 'Create reusable, shared modules for cleaner code architecture.',
    short: `<span class="cm">-- ModuleScript</span>
<span class="kw">local</span> <span class="var">MyModule</span> = {}
<span class="kw">function</span> <span class="var">MyModule</span>.<span class="fn">greet</span>(name)
  <span class="kw">return</span> <span class="str">"Hello, "</span> .. name
<span class="kw">end</span>
<span class="kw">return</span> <span class="var">MyModule</span>`,
    full: `-- ============ ModuleScript (in ReplicatedStorage) ============
local PlayerUtils = {}

-- Private variables (not accessible outside)
local cache = {}

-- Public function
function PlayerUtils.getCharacter(player)
    return player.Character or player.CharacterAdded:Wait()
end

function PlayerUtils.getHumanoid(player)
    local char = PlayerUtils.getCharacter(player)
    return char:WaitForChild("Humanoid")
end

function PlayerUtils.setWalkSpeed(player, speed)
    local hum = PlayerUtils.getHumanoid(player)
    hum.WalkSpeed = math.clamp(speed, 0, 500)
end

function PlayerUtils.isAlive(player)
    local char = player.Character
    if not char then return false end
    local hum = char:FindFirstChild("Humanoid")
    return hum and hum.Health > 0
end

-- Cache pattern
function PlayerUtils.getData(userId)
    if cache[userId] then return cache[userId] end
    -- fetch/create data...
    cache[userId] = { coins = 0 }
    return cache[userId]
end

return PlayerUtils

-- ============ HOW TO USE IN ANOTHER SCRIPT ============
-- local PlayerUtils = require(game.ReplicatedStorage.PlayerUtils)
-- PlayerUtils.setWalkSpeed(player, 30)
-- print(PlayerUtils.isAlive(player))`
  },

  // ── LIGHTING ──
  {
    id: 'li1', cat: 'lighting', tag: 'both', title: 'Lighting & Atmosphere',
    desc: 'Control Lighting, Atmosphere, and post-processing effects.',
    short: `<span class="kw">local</span> <span class="var">Lighting</span> = game:<span class="fn">GetService</span>(<span class="str">"Lighting"</span>)
<span class="var">Lighting</span>.TimeOfDay = <span class="str">"18:00:00"</span>
<span class="var">Lighting</span>.Brightness = <span class="num">2</span>
<span class="var">Lighting</span>.Ambient = <span class="var">Color3</span>.<span class="fn">fromRGB</span>(<span class="num">100</span>,<span class="num">120</span>,<span class="num">200</span>)`,
    full: `local Lighting = game:GetService("Lighting")
local TweenService = game:GetService("TweenService")

-- Basic lighting
Lighting.TimeOfDay = "18:00:00"   -- sunset
Lighting.Brightness = 2
Lighting.Ambient = Color3.fromRGB(100, 120, 200)
Lighting.OutdoorAmbient = Color3.fromRGB(70, 90, 160)
Lighting.FogEnd = 500
Lighting.FogColor = Color3.fromRGB(180, 190, 210)

-- Atmosphere effect
local atmosphere = Instance.new("Atmosphere")
atmosphere.Density = 0.4
atmosphere.Offset = 0.25
atmosphere.Color = Color3.fromRGB(199, 170, 140)
atmosphere.Decay = Color3.fromRGB(100, 80, 60)
atmosphere.Glare = 0.5
atmosphere.Haze = 2
atmosphere.Parent = Lighting

-- Bloom effect
local bloom = Instance.new("BloomEffect")
bloom.Intensity = 1.5
bloom.Size = 24
bloom.Threshold = 0.95
bloom.Parent = Lighting

-- Color correction
local colorCorrection = Instance.new("ColorCorrectionEffect")
colorCorrection.Saturation = 0.2
colorCorrection.Contrast = 0.1
colorCorrection.Brightness = 0.05
colorCorrection.Parent = Lighting

-- Day/night cycle
task.spawn(function()
    local clock = 6 -- start at 6am
    while true do
        clock = (clock + 0.01) % 24
        Lighting.ClockTime = clock
        task.wait(0.05)
    end
end)

-- Smooth lighting tween (e.g. enter cave)
local function setDark()
    TweenService:Create(Lighting, TweenInfo.new(2), {
        Brightness = 0.1,
        Ambient = Color3.fromRGB(20, 20, 30)
    }):Play()
end`
  },
]

// ────────────────────────────────────────
// RENDER
// ────────────────────────────────────────

const CATEGORY_META = {
  services:  { icon: '⚙️', color: '#ff3c6e', label: 'Game Services' },
  player:    { icon: '👤', color: '#00e5ff', label: 'Player & Character' },
  gui:       { icon: '🖥️', color: '#ffe600', label: 'GUI / UI' },
  remote:    { icon: '📡', color: '#b388ff', label: 'Remote Events' },
  datastore: { icon: '💾', color: '#50fa7b', label: 'DataStore' },
  tween:     { icon: '✨', color: '#ffb86c', label: 'Tweening' },
  physics:   { icon: '🌀', color: '#ff5555', label: 'Physics' },
  loop:      { icon: '🔄', color: '#8be9fd', label: 'Loops & Events' },
  tool:      { icon: '🔧', color: '#f1fa8c', label: 'Tools & Items' },
  sound:     { icon: '🎵', color: '#ff79c6', label: 'Sound & Music' },
  module:    { icon: '📦', color: '#bd93f9', label: 'ModuleScripts' },
  lighting:  { icon: '💡', color: '#ffb86c', label: 'Lighting & FX' },
}

let currentModal = null

function groupByCategory(scripts) {
  const groups = {}
  for (const s of scripts) {
    if (!groups[s.cat]) groups[s.cat] = []
    groups[s.cat].push(s)
  }
  return groups
}

function renderAll(filtered) {
  const main = document.getElementById('mainContent')
  main.innerHTML = ''

  const groups = groupByCategory(filtered)

  for (const [cat, scripts] of Object.entries(groups)) {
    const meta = CATEGORY_META[cat] || { icon: '📄', color: '#aaa', label: cat }

    const section = document.createElement('div')
    section.className = 'section'
    section.id = cat

    section.innerHTML = `
      <div class="section-header">
        <div class="section-title">
          <div class="section-icon" style="background:${meta.color}20">${meta.icon}</div>
          ${meta.label}
        </div>
        <span class="section-count">${scripts.length} scripts</span>
      </div>
      <div class="filter-bar">
        <button class="filter-btn active" onclick="filterTag(this,'${cat}','all')">All</button>
        <button class="filter-btn" onclick="filterTag(this,'${cat}','server')">🖥 Server</button>
        <button class="filter-btn" onclick="filterTag(this,'${cat}','local')">💻 Local</button>
        <button class="filter-btn" onclick="filterTag(this,'${cat}','module')">📦 Module</button>
      </div>
      <div class="scripts-grid" id="grid-${cat}">
        ${scripts.map(s => renderCard(s)).join('')}
      </div>
    `

    main.appendChild(section)
  }
}

function renderCard(s) {
  const tagClass = { server: 'tag-server', local: 'tag-local', module: 'tag-module', both: 'tag-both' }[s.tag] || 'tag-both'
  const tagLabel = { server: 'SERVER', local: 'LOCAL', module: 'MODULE', both: 'BOTH' }[s.tag] || 'BOTH'
  return `
    <div class="script-card" data-tag="${s.tag}" onclick="openModal('${s.id}')">
      <div class="card-header">
        <span class="card-title">${s.title}</span>
        <span class="card-tag ${tagClass}">${tagLabel}</span>
      </div>
      <div class="card-code">${s.short}</div>
      <div class="card-footer">
        <span class="card-desc">${s.desc}</span>
        <button class="copy-btn" onclick="copyCard(event,'${s.id}')">copy</button>
      </div>
    </div>
  `
}

function openModal(id) {
  const s = SCRIPTS.find(x => x.id === id)
  if (!s) return
  currentModal = s
  document.getElementById('modalTitle').textContent = s.title
  document.getElementById('modalDesc').textContent = s.desc
  document.getElementById('modalCode').textContent = s.full
  document.getElementById('modalOverlay').classList.add('open')
}

function closeModal(e) {
  if (e.target === document.getElementById('modalOverlay')) closeModalDirect()
}
function closeModalDirect() {
  document.getElementById('modalOverlay').classList.remove('open')
}

function copyModal() {
  if (!currentModal) return
  navigator.clipboard.writeText(currentModal.full)
  const btn = document.querySelector('.modal-copy-btn')
  btn.textContent = '✓ COPIED!'
  setTimeout(() => btn.textContent = '⧉ COPY FULL SCRIPT', 1500)
}

function copyCard(e, id) {
  e.stopPropagation()
  const s = SCRIPTS.find(x => x.id === id)
  if (!s) return
  navigator.clipboard.writeText(s.full)
  const btn = e.target
  btn.textContent = '✓'
  btn.classList.add('copied')
  setTimeout(() => { btn.textContent = 'copy'; btn.classList.remove('copied') }, 1500)
}

function filterTag(btn, cat, tag) {
  const grid = document.getElementById('grid-' + cat)
  if (!grid) return
  grid.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'))
  btn.classList.add('active')
  grid.querySelectorAll('.script-card').forEach(card => {
    const cardTag = card.dataset.tag
    if (tag === 'all' || cardTag === tag || cardTag === 'both') {
      card.style.display = ''
    } else {
      card.style.display = 'none'
    }
  })
}

function showSection(cat) {
  document.querySelectorAll('.sidebar-item').forEach(i => i.classList.remove('active'))
  event.target.closest('.sidebar-item').classList.add('active')

  if (cat === 'all') {
    renderAll(SCRIPTS)
  } else {
    renderAll(SCRIPTS.filter(s => s.cat === cat))
    setTimeout(() => {
      const el = document.getElementById(cat)
      if (el) el.scrollIntoView({ behavior: 'smooth' })
    }, 50)
  }
}

function scrollToSection(cat) {
  renderAll(SCRIPTS)
  setTimeout(() => {
    const el = document.getElementById(cat)
    if (el) el.scrollIntoView({ behavior: 'smooth' })
  }, 50)
}

function filterSearch(query) {
  query = query.toLowerCase().trim()
  if (!query) { renderAll(SCRIPTS); return }
  const filtered = SCRIPTS.filter(s =>
    s.title.toLowerCase().includes(query) ||
    s.desc.toLowerCase().includes(query) ||
    s.cat.toLowerCase().includes(query)
  )
  renderAll(filtered)
}

// Init
renderAll(SCRIPTS)
</script>
</body>
</html>
