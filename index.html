<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-Sports Draft HUD</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts: Sci-Fi & Luxury Feel -->
    <link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;500;600;700&family=Orbitron:wght@400;500;700&display=swap" rel="stylesheet">
    
    <!-- Phosphor Icons -->
    <script src="https://unpkg.com/@phosphor-icons/web"></script>

    <!-- Tailwind Config -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'neon-blue': '#00f3ff',
                        'neon-pink': '#ff003c',
                        'neon-purple': '#bc13fe',
                        'dark-bg': '#050510',
                        'glass-bg': 'rgba(15, 20, 40, 0.65)',
                        'glass-border': 'rgba(0, 243, 255, 0.15)',
                    },
                    fontFamily: {
                        'scifi': ['Orbitron', 'sans-serif'],
                        'body': ['Rajdhani', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #050510;
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(0, 243, 255, 0.08), transparent 30%),
                radial-gradient(circle at 85% 30%, rgba(188, 19, 254, 0.08), transparent 30%);
            color: #e2e8f0;
            overflow-x: hidden;
            user-select: none;
        }

        .glass-panel {
            background: var(--tw-colors-glass-bg);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--tw-colors-glass-border);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.5);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: rgba(0,0,0,0.2); }
        ::-webkit-scrollbar-thumb { background: rgba(0, 243, 255, 0.3); border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: rgba(0, 243, 255, 0.6); }

        /* Item Cards */
        .item-card {
            transition: all 0.2s ease-in-out;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }
        .item-card::before {
            content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(255,255,255,0.1) 0%, transparent 100%);
            opacity: 0; transition: opacity 0.3s;
        }
        .item-card:hover:not(.disabled)::before { opacity: 1; }
        .item-card:hover:not(.disabled) {
            transform: translateY(-2px) scale(1.05);
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.4);
            border-color: rgba(0, 243, 255, 0.8);
            z-index: 10;
        }
        
        .item-card.selected-ban {
            border-color: #ff003c;
            box-shadow: 0 0 15px rgba(255, 0, 60, 0.5);
            opacity: 0.9;
        }

        .item-card.banned {
            filter: grayscale(100%) opacity(0.25);
            pointer-events: none;
        }
        .item-card.banned::after {
            content: ''; position: absolute; top: 50%; left: -10%; right: -10%; height: 2px;
            background: #ff003c; transform: rotate(-35deg); box-shadow: 0 0 8px #ff003c;
        }

        .item-card.picked-p1 {
            border-color: #00f3ff;
            box-shadow: inset 0 0 20px rgba(0, 243, 255, 0.2);
            background: rgba(0, 243, 255, 0.1);
            pointer-events: none;
            opacity: 0.5;
        }
        .item-card.picked-p2 {
            border-color: #bc13fe;
            box-shadow: inset 0 0 20px rgba(188, 19, 254, 0.2);
            background: rgba(188, 19, 254, 0.1);
            pointer-events: none;
            opacity: 0.5;
        }

        /* Turn Animations */
        .turn-pulse-p1 { animation: pulse-border-p1 2s infinite; }
        @keyframes pulse-border-p1 {
            0% { box-shadow: 0 0 0 0 rgba(0, 243, 255, 0.4); }
            70% { box-shadow: 0 0 0 10px rgba(0, 243, 255, 0); }
            100% { box-shadow: 0 0 0 0 rgba(0, 243, 255, 0); }
        }

        .turn-pulse-p2 { animation: pulse-border-p2 2s infinite; }
        @keyframes pulse-border-p2 {
            0% { box-shadow: 0 0 0 0 rgba(188, 19, 254, 0.4); }
            70% { box-shadow: 0 0 0 10px rgba(188, 19, 254, 0); }
            100% { box-shadow: 0 0 0 0 rgba(188, 19, 254, 0); }
        }

        /* Modals */
        .modal-overlay {
            display: none; position: fixed; inset: 0;
            background: rgba(0,0,0,0.85); backdrop-filter: blur(8px);
            z-index: 50; justify-content: center; align-items: center;
        }
    </style>
</head>
<body class="font-body h-screen flex flex-col antialiased">

    <!-- Header -->
    <header class="h-16 glass-panel border-b border-white/10 border-t-0 flex items-center justify-between px-6 z-20">
        <div class="flex items-center gap-3">
            <i class="ph-fill ph-hexagon text-neon-blue text-3xl drop-shadow-[0_0_8px_rgba(0,243,255,0.8)]"></i>
            <h1 class="font-scifi text-xl font-bold tracking-widest text-white uppercase mt-1">Nexus <span class="text-neon-blue">Draft</span></h1>
        </div>
        <div id="status-display" class="font-scifi text-sm tracking-[0.2em] text-gray-400 mt-1">
            CONNECTING...
        </div>
        <div class="flex gap-4">
            <button id="btn-show-join" class="hidden text-xs px-4 py-1.5 bg-white/5 border border-white/20 rounded hover:bg-white/10 transition">CHANGE SLOT</button>
            <button id="btn-reset" class="text-xs px-4 py-1.5 border border-red-500/50 rounded text-red-400 hover:bg-red-500/10 transition">RESET ROOM</button>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-1 flex overflow-hidden relative">
        
        <!-- Player 1 Sidebar -->
        <aside id="sidebar-p1" class="w-64 glass-panel border-r border-white/5 p-5 flex flex-col gap-4 z-10 transition-all duration-300">
            <div class="text-center pb-4 border-b border-white/10">
                <h2 class="font-scifi text-xl text-neon-blue font-bold tracking-wider drop-shadow-[0_0_5px_rgba(0,243,255,0.5)]">PLAYER 1</h2>
                <div id="p1-status" class="text-[10px] text-gray-500 uppercase tracking-widest mt-1 font-bold">Waiting...</div>
            </div>
            
            <div class="flex-1 flex flex-col gap-3">
                <h3 class="text-xs text-gray-400 uppercase tracking-widest mb-1 flex items-center gap-2">
                    <i class="ph ph-sword text-neon-blue"></i> Loadout
                </h3>
                <div id="p1-picks" class="flex flex-col gap-3">
                    <!-- Picks injected here -->
                </div>
            </div>

            <div class="h-auto border-t border-white/10 pt-4">
                <h3 class="text-xs text-gray-400 uppercase tracking-widest mb-3 flex justify-between items-center">
                    <span class="flex items-center gap-2"><i class="ph ph-prohibit text-red-500"></i> Bans</span>
                    <span id="p1-ban-count" class="text-[10px] bg-red-500/20 px-2 py-0.5 rounded text-red-400">0/3</span>
                </h3>
                <div id="p1-bans" class="flex justify-between gap-2">
                    <!-- Bans injected here -->
                </div>
            </div>
        </aside>

        <!-- Center Draft Board -->
        <section class="flex-1 flex flex-col h-full relative">
            
            <!-- Category Tabs -->
            <div class="h-16 bg-black/40 border-b border-white/5 flex justify-center items-center gap-2 sm:gap-8 z-10 px-4">
                <button class="tab-btn active text-neon-blue font-scifi font-bold tracking-widest uppercase border-b-2 border-neon-blue py-4 px-2 transition-all hover:text-neon-blue hover:brightness-125" data-target="heroes">Heroes (6)</button>
                <button class="tab-btn text-gray-500 hover:text-gray-300 font-scifi font-medium tracking-widest uppercase border-b-2 border-transparent py-4 px-2 transition-all" data-target="troops">Troops (32)</button>
                <button class="tab-btn text-gray-500 hover:text-gray-300 font-scifi font-medium tracking-widest uppercase border-b-2 border-transparent py-4 px-2 transition-all" data-target="spells">Spells (18)</button>
                <button class="tab-btn text-gray-500 hover:text-gray-300 font-scifi font-medium tracking-widest uppercase border-b-2 border-transparent py-4 px-2 transition-all" data-target="equips">Equips (43)</button>
            </div>

            <!-- Context Bar -->
            <div class="h-14 glass-panel border-none flex items-center justify-center px-8 shadow-lg relative z-20">
                <div id="instruction-text" class="text-sm md:text-base font-scifi tracking-widest text-gray-300 uppercase text-center w-full">
                    INITIALIZING SYSTEM...
                </div>
                <button id="action-btn" class="hidden absolute right-6 font-scifi px-6 py-2 bg-red-500/10 border border-red-500 text-red-400 font-bold tracking-widest rounded hover:bg-red-500 hover:text-white transition-all shadow-[0_0_10px_rgba(255,0,60,0.2)]">
                    LOCK BANS
                </button>
            </div>

            <!-- Item Grids -->
            <div class="flex-1 overflow-y-auto p-6 lg:p-8 relative">
                <div id="grid-heroes" class="category-grid grid grid-cols-3 sm:grid-cols-4 lg:grid-cols-6 gap-3 lg:gap-4"></div>
                <div id="grid-troops" class="category-grid grid grid-cols-4 sm:grid-cols-6 lg:grid-cols-8 gap-3 lg:gap-4 hidden"></div>
                <div id="grid-spells" class="category-grid grid grid-cols-4 sm:grid-cols-6 lg:grid-cols-8 gap-3 lg:gap-4 hidden"></div>
                <div id="grid-equips" class="category-grid grid grid-cols-4 sm:grid-cols-6 lg:grid-cols-8 gap-3 lg:gap-4 hidden"></div>
            </div>
        </section>

        <!-- Player 2 Sidebar -->
        <aside id="sidebar-p2" class="w-64 glass-panel border-l border-white/5 p-5 flex flex-col gap-4 z-10 transition-all duration-300">
            <div class="text-center pb-4 border-b border-white/10">
                <h2 class="font-scifi text-xl text-neon-purple font-bold tracking-wider drop-shadow-[0_0_5px_rgba(188,19,254,0.5)]">PLAYER 2</h2>
                <div id="p2-status" class="text-[10px] text-gray-500 uppercase tracking-widest mt-1 font-bold">Waiting...</div>
            </div>
            
            <div class="flex-1 flex flex-col gap-3">
                <h3 class="text-xs text-gray-400 uppercase tracking-widest mb-1 flex items-center gap-2">
                    <i class="ph ph-sword text-neon-purple"></i> Loadout
                </h3>
                <div id="p2-picks" class="flex flex-col gap-3">
                    <!-- Picks injected here -->
                </div>
            </div>

            <div class="h-auto border-t border-white/10 pt-4">
                <h3 class="text-xs text-gray-400 uppercase tracking-widest mb-3 flex justify-between items-center">
                    <span class="flex items-center gap-2"><i class="ph ph-prohibit text-red-500"></i> Bans</span>
                    <span id="p2-ban-count" class="text-[10px] bg-red-500/20 px-2 py-0.5 rounded text-red-400">0/3</span>
                </h3>
                <div id="p2-bans" class="flex justify-between gap-2">
                    <!-- Bans injected here -->
                </div>
            </div>
        </aside>
    </main>

    <!-- Modal for Messages/Lobby -->
    <div id="modal-overlay" class="flex modal-overlay">
        <div class="glass-panel p-8 rounded-xl max-w-md w-full text-center border-t border-neon-blue">
            <h2 id="modal-title" class="font-scifi text-2xl font-bold text-white mb-4">ONLINE DRAFT LOBBY</h2>
            <p id="modal-desc" class="text-gray-400 mb-8 text-sm">Wähle deine Rolle für das Match.</p>
            
            <div id="modal-actions" class="flex flex-col gap-3">
                <button id="join-p1-btn" class="w-full py-3 bg-neon-blue/10 border border-neon-blue text-neon-blue font-scifi font-bold rounded hover:bg-neon-blue hover:text-black transition shadow-[0_0_15px_rgba(0,243,255,0.2)]">
                    JOIN AS PLAYER 1
                </button>
                <button id="join-p2-btn" class="w-full py-3 bg-neon-purple/10 border border-neon-purple text-neon-purple font-scifi font-bold rounded hover:bg-neon-purple hover:text-black transition shadow-[0_0_15px_rgba(188,19,254,0.2)]">
                    JOIN AS PLAYER 2
                </button>
                <button id="join-spec-btn" class="w-full py-2 border border-gray-600 text-gray-400 font-scifi rounded hover:bg-gray-800 transition mt-2">
                    SPECTATE
                </button>
            </div>
            <div id="modal-error" class="text-red-500 text-xs mt-4 hidden font-bold tracking-widest">SLOT BEREITS BELEGT!</div>
        </div>
    </div>

    <!-- Online Firebase Logic -->
    <script type="module">
        // --- GAME DATA GENERATION ---
        const generateItems = (prefix, count, namePrefix, cat) => {
            return Array.from({length: count}, (_, i) => ({
                id: `${prefix}${i+1}`,
                name: `${namePrefix} ${i+1}`,
                category: cat,
                short: `${prefix.toUpperCase()}${i+1}`
            }));
        };

        const GAME_DATA = [
            ...generateItems('h', 6, 'Hero', 'heroes'),
            ...generateItems('t', 32, 'Troop', 'troops'),
            ...generateItems('s', 18, 'Spell', 'spells'),
            ...generateItems('e', 43, 'Equip', 'equips')
        ];

        const ITEM_MAP = GAME_DATA.reduce((acc, item) => { acc[item.id] = item; return acc; }, {});

        // --- MULTI-TAB SYNC (Ersetzt Firebase für fehlerfreies Testen) ---
        const PICK_SEQUENCE = ['player1', 'player2', 'player2', 'player1', 'player1', 'player2'];
        
        let serverState = null;
        let userRole = null; 
        let userId = 'user_' + Math.random().toString(36).substr(2, 9);
        let localTempBans = [];
        
        // BroadcastChannel verbindet alle offenen Tabs auf deinem Rechner in Echtzeit
        const channel = new BroadcastChannel('draft-sync-channel');

        channel.onmessage = (event) => {
            if (event.data) {
                serverState = event.data;
                render();
            }
        };

        function updateServer(updates) {
            serverState = { ...serverState, ...updates };
            localStorage.setItem('draft_state', JSON.stringify(serverState));
            channel.postMessage(serverState);
            render();
        }

        // --- DOM ELEMENTS ---
        const UI = {
            modal: document.getElementById('modal-overlay'),
            modalError: document.getElementById('modal-error'),
            statusText: document.getElementById('status-display'),
            instructionText: document.getElementById('instruction-text'),
            actionBtn: document.getElementById('action-btn'),
            btnReset: document.getElementById('btn-reset'),
            grids: {
                heroes: document.getElementById('grid-heroes'),
                troops: document.getElementById('grid-troops'),
                spells: document.getElementById('grid-spells'),
                equips: document.getElementById('grid-equips')
            }
        };

        // --- INITIALIZATION ---
        function init() {
            buildGrids();
            setupTabs();
            UI.modal.style.display = 'flex'; 

            document.getElementById('join-p1-btn').addEventListener('click', () => joinAs('p1'));
            document.getElementById('join-p2-btn').addEventListener('click', () => joinAs('p2'));
            document.getElementById('join-spec-btn').addEventListener('click', () => joinAs('spec'));
            
            UI.btnReset.addEventListener('click', () => {
                resetRoom();
            });

            // Lade gespeicherten Zustand (falls vorhanden) oder starte neu
            const savedState = localStorage.getItem('draft_state');
            if (savedState) {
                serverState = JSON.parse(savedState);
                render();
            } else {
                resetRoom();
            }
        }

        function resetRoom() {
            serverState = {
                phase: 'WAITING', 
                p1Id: null, p2Id: null,
                p1Bans: [], p2Bans: [], globalBans: [],
                p1BansLocked: false, p2BansLocked: false,
                p1Picks: [], p2Picks: [],
                pickIndex: 0
            };
            localTempBans = [];
            userRole = null;
            UI.modal.style.display = 'flex'; 
            updateServer({});
        }

        function joinAs(role) {
            if(!serverState) return;
            const updates = {};
            
            if (role === 'p1') {
                if (serverState.p1Id && serverState.p1Id !== userId) {
                    UI.modalError.classList.remove('hidden'); return;
                }
                updates.p1Id = userId;
                userRole = 'p1';
            } else if (role === 'p2') {
                if (serverState.p2Id && serverState.p2Id !== userId) {
                    UI.modalError.classList.remove('hidden'); return;
                }
                updates.p2Id = userId;
                userRole = 'p2';
            } else {
                userRole = 'spec';
            }

            const currP1 = updates.p1Id || serverState.p1Id;
            const currP2 = updates.p2Id || serverState.p2Id;
            if (currP1 && currP2 && serverState.phase === 'WAITING') {
                updates.phase = 'BANS';
            }

            UI.modalError.classList.add('hidden');
            UI.modal.style.display = 'none'; 
            
            if(Object.keys(updates).length > 0) {
                updateServer(updates);
            } else {
                render();
            }
        }

        // --- INTERACTIONS ---
        function handleItemClick(itemId) {
            if (!serverState || userRole === 'spec') return;

            if (serverState.phase === 'BANS') {
                if (userRole === 'p1' && serverState.p1BansLocked) return;
                if (userRole === 'p2' && serverState.p2BansLocked) return;

                const idx = localTempBans.indexOf(itemId);
                if (idx > -1) {
                    localTempBans.splice(idx, 1);
                } else if (localTempBans.length < 3) {
                    localTempBans.push(itemId);
                }
                render();
            }
            else if (serverState.phase === 'PICKS') {
                if (serverState.globalBans.includes(itemId) || serverState.p1Picks.includes(itemId) || serverState.p2Picks.includes(itemId)) return;

                const activePlayer = PICK_SEQUENCE[serverState.pickIndex];
                if (activePlayer === 'player1' && userRole !== 'p1') return; 
                if (activePlayer === 'player2' && userRole !== 'p2') return; 

                const updates = { pickIndex: serverState.pickIndex + 1 };
                if (activePlayer === 'player1') {
                    updates.p1Picks = [...serverState.p1Picks, itemId];
                } else {
                    updates.p2Picks = [...serverState.p2Picks, itemId];
                }

                if (updates.pickIndex >= PICK_SEQUENCE.length) {
                    updates.phase = 'SUMMARY';
                }
                updateServer(updates);
            }
        }

        function handleActionClick() {
            if (!serverState || userRole === 'spec') return;

            if (serverState.phase === 'BANS' && localTempBans.length === 3) {
                const updates = {};
                if (userRole === 'p1') {
                    updates.p1Bans = localTempBans;
                    updates.p1BansLocked = true;
                    if (serverState.p2BansLocked) {
                        updates.phase = 'REVEAL';
                        updates.globalBans = [...new Set([...localTempBans, ...serverState.p2Bans])];
                    }
                } else if (userRole === 'p2') {
                    updates.p2Bans = localTempBans;
                    updates.p2BansLocked = true;
                    if (serverState.p1BansLocked) {
                        updates.phase = 'REVEAL';
                        updates.globalBans = [...new Set([...serverState.p1Bans, ...localTempBans])];
                    }
                }
                updateServer(updates);
            }
            else if (serverState.phase === 'REVEAL') {
                updateServer({ phase: 'PICKS' });
            }
        }

        // --- RENDER LOGIC ---
        function render() {
            if(!serverState) return;

            // Falls der Raum von einem anderen Tab zurückgesetzt wurde, Rolle löschen und Lobby zeigen
            if (serverState.phase === 'WAITING') {
                if ((userRole === 'p1' && !serverState.p1Id) || (userRole === 'p2' && !serverState.p2Id)) {
                    userRole = null;
                    localTempBans = [];
                }
            }
            if (!userRole) {
                UI.modal.style.display = 'flex';
            }

            // Status Bar (Fallback auf 'NONE', falls userRole noch null ist)
            const roleDisplay = userRole ? userRole.toUpperCase() : 'NONE';
            UI.statusText.textContent = `ONLINE | PHASE: ${serverState.phase} | ROLE: ${roleDisplay}`;

            // Reset Item Cards
            document.querySelectorAll('.item-card').forEach(card => {
                const id = card.dataset.id;
                card.className = 'item-card relative h-16 bg-white/5 border border-white/10 rounded flex items-center justify-center font-scifi font-bold text-lg select-none';
                card.innerHTML = ITEM_MAP[id].short;
                
                // Color coding
                const cat = ITEM_MAP[id].category;
                if(cat==='heroes') card.classList.add('text-yellow-400');
                if(cat==='troops') card.classList.add('text-pink-400');
                if(cat==='spells') card.classList.add('text-blue-400');
                if(cat==='equips') card.classList.add('text-purple-400');

                // State Visuals
                if (serverState.phase === 'BANS') {
                    if (localTempBans.includes(id)) {
                        card.classList.add('selected-ban');
                    }
                } 
                else if (serverState.phase === 'REVEAL' || serverState.phase === 'PICKS' || serverState.phase === 'SUMMARY') {
                    if (serverState.globalBans.includes(id)) {
                        card.classList.add('banned');
                        card.innerHTML = `<span class="opacity-50 line-through">${ITEM_MAP[id].short}</span>`;
                    }
                    if (serverState.p1Picks.includes(id)) card.classList.add('picked-p1');
                    if (serverState.p2Picks.includes(id)) card.classList.add('picked-p2');
                }
            });

            // Update Sidebars
            updateSidebar('player1');
            updateSidebar('player2');

            // Action Button & Instructions
            UI.actionBtn.classList.add('hidden');
            UI.actionBtn.onclick = handleActionClick;
            
            document.getElementById('sidebar-p1').classList.remove('turn-pulse-p1');
            document.getElementById('sidebar-p2').classList.remove('turn-pulse-p2');

            if (serverState.phase === 'WAITING') {
                UI.instructionText.innerHTML = "WARTE AUF SPIELER...";
            }
            else if (serverState.phase === 'BANS') {
                const isLocked = (userRole === 'p1' && serverState.p1BansLocked) || (userRole === 'p2' && serverState.p2BansLocked);
                if (userRole === 'spec') {
                    UI.instructionText.innerHTML = "SPIELER WÄHLEN BANS...";
                } else if (isLocked) {
                    UI.instructionText.innerHTML = "WARTE AUF GEGNER...";
                } else {
                    const color = userRole === 'p1' ? 'text-neon-blue' : 'text-neon-purple';
                    UI.instructionText.innerHTML = `Wähle deine 3 Bans (<span class="${color}">${localTempBans.length}/3</span>)`;
                    if (localTempBans.length === 3) {
                        UI.actionBtn.classList.remove('hidden');
                        UI.actionBtn.textContent = 'LOCK BANS';
                    }
                }
            }
            else if (serverState.phase === 'REVEAL') {
                UI.instructionText.innerHTML = "DAS SIND DIE GLOBALEN BANS.";
                if (userRole === 'p1' || userRole === 'p2') {
                    UI.actionBtn.classList.remove('hidden');
                    UI.actionBtn.textContent = 'WEITER ZU DEN PICKS';
                }
            }
            else if (serverState.phase === 'PICKS') {
                const activePlayer = PICK_SEQUENCE[serverState.pickIndex];
                const pName = activePlayer === 'player1' ? 'Player 1' : 'Player 2';
                const color = activePlayer === 'player1' ? 'text-neon-blue' : 'text-neon-purple';
                
                if((activePlayer === 'player1' && userRole === 'p1') || (activePlayer === 'player2' && userRole === 'p2')) {
                    UI.instructionText.innerHTML = `<span class="${color}">DU BIST DRAN!</span> (Pick ${serverState.pickIndex + 1} von 6)`;
                } else {
                    UI.instructionText.innerHTML = `<span class="${color}">${pName} WÄHLT...</span>`;
                }
                
                if (activePlayer === 'player1') document.getElementById('sidebar-p1').classList.add('turn-pulse-p1');
                else document.getElementById('sidebar-p2').classList.add('turn-pulse-p2');
            }
            else if (serverState.phase === 'SUMMARY') {
                UI.instructionText.innerHTML = "DRAFT BEENDET!";
            }
        }

        function updateSidebar(playerSlot) {
            const isP1 = playerSlot === 'player1';
            const colorClass = isP1 ? 'text-neon-blue' : 'text-neon-purple';
            const borderClass = isP1 ? 'border-neon-blue/30' : 'border-neon-purple/30';
            
            const statusEl = document.getElementById(`${isP1 ? 'p1' : 'p2'}-status`);
            
            // Status Text
            if (serverState.phase === 'WAITING') {
                const isJoined = isP1 ? serverState.p1Id : serverState.p2Id;
                statusEl.textContent = isJoined ? 'Ready' : 'Waiting...';
            }
            else if (serverState.phase === 'BANS') {
                const isLocked = isP1 ? serverState.p1BansLocked : serverState.p2BansLocked;
                statusEl.textContent = isLocked ? 'Locked' : 'Banning...';
            }
            else statusEl.textContent = 'Ready';
            
            // Bans
            const banContainer = document.getElementById(`${isP1 ? 'p1' : 'p2'}-bans`);
            const countEl = document.getElementById(`${isP1 ? 'p1' : 'p2'}-ban-count`);
            banContainer.innerHTML = '';
            
            let banList = [];
            let displayCount = 0;
            
            if (serverState.phase === 'BANS') {
                // Eigene Bans lokal anzeigen, gegnerische Bans verstecken
                if (isP1 && userRole === 'p1') { banList = localTempBans; displayCount = localTempBans.length; }
                else if (!isP1 && userRole === 'p2') { banList = localTempBans; displayCount = localTempBans.length; }
                else if (isP1 && serverState.p1BansLocked) { banList = ['?', '?', '?']; displayCount = 3; }
                else if (!isP1 && serverState.p2BansLocked) { banList = ['?', '?', '?']; displayCount = 3; }
            } 
            else if (serverState.phase !== 'WAITING') {
                banList = isP1 ? serverState.p1Bans : serverState.p2Bans;
                displayCount = banList.length;
            }

            countEl.textContent = `${displayCount}/3`;

            for(let i=0; i<3; i++) {
                const box = document.createElement('div');
                box.className = 'w-10 h-10 bg-black/50 border border-white/10 rounded flex items-center justify-center text-xs font-bold font-scifi text-red-500';
                
                if (banList[i]) {
                    if (banList[i] === '?') {
                        box.textContent = '?';
                        box.classList.add('border-red-500/30');
                    } else {
                        const item = ITEM_MAP[banList[i]];
                        box.textContent = item.short;
                        box.classList.add('border-red-500/50', 'bg-red-500/10');
                    }
                }
                banContainer.appendChild(box);
            }

            // Picks
            const pickContainer = document.getElementById(`${isP1 ? 'p1' : 'p2'}-picks`);
            pickContainer.innerHTML = '';
            const picks = isP1 ? serverState.p1Picks : serverState.p2Picks;
            
            for(let i=0; i<3; i++) {
                const box = document.createElement('div');
                box.className = `h-12 bg-black/50 border ${borderClass} rounded flex items-center justify-center text-sm font-bold font-scifi ${colorClass}`;
                if (picks[i]) {
                    const item = ITEM_MAP[picks[i]];
                    box.textContent = item.name;
                    box.classList.add(isP1 ? 'bg-neon-blue/10' : 'bg-neon-purple/10');
                } else {
                    box.classList.add('opacity-30');
                    box.textContent = '---';
                }
                pickContainer.appendChild(box);
            }
        }

        // --- SETUP DOM ---
        function buildGrids() {
            GAME_DATA.forEach(item => {
                const el = document.createElement('div');
                el.className = 'item-card relative h-16 bg-white/5 border border-white/10 rounded flex items-center justify-center font-scifi font-bold text-lg select-none';
                el.dataset.id = item.id;
                el.title = item.name;
                el.textContent = item.short;
                
                el.addEventListener('click', () => handleItemClick(item.id));
                UI.grids[item.category].appendChild(el);
            });
        }

        function setupTabs() {
            const tabs = document.querySelectorAll('.tab-btn');
            tabs.forEach(tab => {
                tab.addEventListener('click', (e) => {
                    tabs.forEach(t => {
                        t.classList.remove('active', 'text-neon-blue', 'border-b-2', 'border-neon-blue', 'font-bold');
                        t.classList.add('text-gray-400');
                    });
                    
                    const target = e.target;
                    target.classList.remove('text-gray-400');
                    target.classList.add('active', 'text-neon-blue', 'border-b-2', 'border-neon-blue', 'font-bold');
                    
                    Object.values(UI.grids).forEach(g => g.classList.add('hidden'));
                    UI.grids[target.dataset.target].classList.remove('hidden');
                });
            });
        }

        // Start
        window.addEventListener('DOMContentLoaded', init);

    </script>
</body>
</html>
