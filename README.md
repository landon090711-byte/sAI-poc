# sAI
Synapse AI 🧠
A proof-of-concept local-first AI companion that learns from every conversation, builds a memory graph, and visualizes connections between concepts in real time.
the code will be uploaded Aug 6 for now here is vercel deployment https://de875dc2esynapse-ai-fixed.vercel.app/

What Is This?
Synapse AI is a proof-of-concept project exploring what a privacy-first, browser-based AI companion could look like. It runs entirely client-side — no backend servers, no cloud APIs, no tracking. Everything you tell it stays in your browser's local storage.

The goal was to build something that feels like talking to an AI that actually remembers you — not a chatbot that forgets everything when you close the tab. It uses a lightweight memory system with type detection, connection mapping, and context-aware recall to simulate persistent understanding.

This is not a production AI. It doesn't use a large language model for response generation. Responses are generated through pattern matching and rule-based logic. It's a concept demo showing how a local memory graph + conversation persistence + natural recall could work together. The natural next step would be wiring in a real LLM API (OpenAI, Anthropic, etc.) for response generation while keeping the memory and persistence layer as-is.

Features
🧠 Memory System
Type Detection — Automatically classifies what you tell it as facts, preferences, goals, relationships, or behavioral patterns
Connection Graph — Builds links between related memories (e.g., "I love coding" connects to "I'm building an AI app")
Contextual Recall — Retrieves relevant memories based on conversation context, not just keyword matching
Recency + Frequency Scoring — More recent and frequently-accessed memories surface first
Memory Feed — Browse everything the AI has learned, filter by type, see when each memory was formed
💬 Conversation
Persistent Chat History — Conversations survive page reloads via localStorage
Natural Memory Responses — When you ask "what do you know about me?", it rephrases memories into natural language instead of dumping raw data
Follow-up Awareness — Detects when you're continuing a previous topic vs. starting a new one
Personalized Greetings — Uses your name from memory if it knows it
🎨 Brain Visualization
Real-time node graph showing concepts and their connections
Connections form dynamically as you share new information
Monochrome aesthetic with smooth animations
🔒 Privacy & PWA
100% Local — No data leaves your browser. No analytics. No tracking.
PWA Support — Installable on mobile/desktop, works offline
Service Worker — Network-first caching for updates with offline fallback
📚 Research Mode
Paste a URL and Synapse will scrape and summarize it
Scraped facts are saved to memory with a [wiki] source tag
Currently uses Wikipedia's API for content retrieval
Tech Stack
Vanilla JavaScript — No frameworks (React, Vue, etc.)
IndexedDB / localStorage — Client-side storage for memories and conversations
Canvas API — Brain visualization
Service Workers — Offline support and caching
Vercel — Static hosting
Getting Started
Run Locally
git clone https://github.com/yourusername/synapse-ai.git
cd synapse-ai
python3 -m http.server 8000
# Visit http://localhost:8000

No dependencies to install. No build step. It's just HTML, CSS, and JS.

Deploy
npx vercel --prod

What Was Fixed (14 Bugs)
Type detection priority — "I love" matched before "My name is" → Fact patterns checked first
Broken memory summaries — "You prefer My name is Landon..." → Proper prefix stripping + natural language transformation
Raw memory text dumped as responses → Natural rephrasing into speech
No conversation persistence → Save/restore conversation history to localStorage
XSS vulnerability — Wikipedia URLs injected via innerHTML → Use createElement/setAttribute
Brain stats counted behavior prompt as a memory → Excluded behavior-type memories
Wiki source label missing in memory feed → Added [wiki] tag
Service worker cache-first broke updates → Switched to network-first
Dead dependency — ai SDK never used → Removed from package.json
Connections formed with behavior memories → Skipped in _createConnections
Memory query too narrow → Added recency boost, access frequency, expanded to 5 results
No conversation context awareness → Added history tracking + follow-up detection
Generic greetings even when name is known → Personalized from memory
"Clear All Data" didn't clear conversations → Wipe localStorage conversation history too
Limitations
This is a proof of concept — it works, but it has real limitations:

No LLM integration — Responses are pattern-matched, not generated. The single biggest upgrade would be wiring in a real LLM API.
localStorage limits — ~5MB cap. For larger datasets, migrate to IndexedDB.
Single-user only — No auth, no multi-device sync.
Research mode is limited — Only Wikipedia URLs supported.
No voice input — Text only.
License
MIT — do whatever you want with it.

Built as a proof of concept to explore local-first AI memory and conversation persistence. Not affiliated with any AI company. The "AI" is pattern matching + rules — but the memory architecture is real and would work great behind an actual LLM.

Synapse AI is a proof-of-concept local-first AI companion that runs entirely in your browser — no backend, no cloud, no tracking. It learns from every conversation using a memory system that detects types (facts, preferences, goals), builds a connection graph between concepts, and recalls relevant memories contextually. Features include persistent chat history that survives reloads, a real-time brain visualization, research mode that scrapes Wikipedia, and PWA/offline support. It's built with vanilla JavaScript, localStorage, and Canvas — no frameworks. The response engine uses pattern matching and rules, not a real LLM, so the natural next step is wiring in an actual LLM API while keeping the memory layer intact.

