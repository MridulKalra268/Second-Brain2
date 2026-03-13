Serencious 🧠
Your second brain — save links, notes, and docs, then ask questions about them in plain English.
Live Demo → https://second-brain2-frontend.onrender.com/

⚠️ Hosted on a free instance — first load may take ~50 seconds to wake up.


What it does
You save stuff (URLs, notes, docs). Later, you just ask "what was that article about productivity I saved last week?" and it finds it, reads it, and answers you — instead of you scrolling through a mess of bookmarks.
Under the hood it uses vector embeddings to understand meaning, not just keywords.

Features

🔍 Semantic search — ask questions in plain English, get relevant results
🌐 URL saving — auto-scrapes title, content, and preview image
📝 Notes — write and store formatted notes
🤖 AI answers — Gemini reads your saved content and answers your query
🔗 Share your brain — generate a public link to share your saved content
🌙 Dark/light mode
📱 Responsive — works on mobile too


Tech Stack
LayerTechFrontendReact, TypeScript, Tailwind CSS, ReduxBackendNode.js, Express, TypeScriptDatabaseMongoDBVector DBPineconeAIGoogle Gemini (embeddings + generation)ScrapingPuppeteer

Running locally
Prerequisites: Node.js 18+, MongoDB, Pinecone account, Gemini API key
bash# Clone
git clone https://github.com/sreyas-cheviri/superSerencious.git
cd superSerencious

# Backend
cd Server
npm install
cp .env.example .env   # fill in your keys
npm run dev

# Frontend (new terminal)
cd Client
npm install
npm run dev
```

**Required env vars (Server):**
```
MONGODB_URI=
GEMINI_API_KEY=
PINECONE_API_KEY=
PINECONE_INDEX=
JWT_SECRET=
YOUTUBE_API_KEY=   # optional, for YouTube embeds

How the search works

When you save something, the content gets converted into a vector embedding via Gemini
That vector gets stored in Pinecone alongside the content in MongoDB
When you search, your query becomes a vector too
Pinecone finds the closest matches → MongoDB fetches the full content → Gemini writes you a response

