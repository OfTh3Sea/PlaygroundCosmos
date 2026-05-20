<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Cosmic Playground ✨</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #060412;
    --surface: #0d0820;
    --card: #110e2a;
    --border: rgba(255,255,255,0.07);
    --gold: #f2c14e;
    --gold-soft: rgba(242,193,78,0.15);
    --rose: #f08fa0;
    --teal: #5ecfca;
    --lavender: #b8a9e8;
    --white: #ede9f8;
    --muted: rgba(237,233,248,0.55);
    --fire: #ff7043;
    --earth: #66bb6a;
    --air: #4dd0e1;
    --water: #7986cb;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    line-height: 1.65;
    overflow-x: hidden;
  }

  /* animated stars */
  .stars {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }
  .star {
    position: absolute;
    border-radius: 50%;
    background: white;
    animation: twinkle var(--d) ease-in-out infinite;
    opacity: 0;
  }
  @keyframes twinkle {
    0%,100% { opacity:0; transform:scale(1); }
    50% { opacity:var(--o); transform:scale(1.4); }
  }

  .wrap {
    position: relative;
    z-index: 1;
    max-width: 960px;
    margin: 0 auto;
    padding: 0 20px 80px;
  }

  /* NAV TABS */
  .tab-nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(6,4,18,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    display: flex;
    gap: 4px;
    padding: 12px 20px;
    overflow-x: auto;
    scrollbar-width: none;
  }
  .tab-nav::-webkit-scrollbar { display:none; }

  .tab-btn {
    flex-shrink: 0;
    background: none;
    border: 1px solid var(--border);
    border-radius: 30px;
    color: var(--muted);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    font-weight: 500;
    padding: 6px 16px;
    cursor: pointer;
    transition: all 0.2s;
    white-space: nowrap;
  }
  .tab-btn:hover { border-color: var(--gold); color: var(--gold); }
  .tab-btn.active {
    background: var(--gold-soft);
    border-color: var(--gold);
    color: var(--gold);
  }

  /* SECTIONS */
  .section { display: none; padding-top: 48px; }
  .section.active { display: block; }

  /* HEADER */
  .hero {
    text-align: center;
    padding: 70px 0 50px;
  }
  .hero-icon {
    font-size: 72px;
    display: block;
    animation: bob 5s ease-in-out infinite;
  }
  @keyframes bob {
    0%,100%{transform:translateY(0) rotate(-3deg);}
    50%{transform:translateY(-14px) rotate(3deg);}
  }
  h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem,6vw,3.4rem);
    color: var(--gold);
    margin: 16px 0 8px;
    text-shadow: 0 0 40px rgba(242,193,78,0.4);
    line-height: 1.15;
  }
  .hero p {
    color: var(--muted);
    font-size: 1rem;
    max-width: 520px;
    margin: 0 auto;
    font-style: italic;
  }

  /* SECTION HEADING */
  .sec-head {
    margin-bottom: 32px;
  }
  .sec-head h2 {
    font-family: 'Playfair Display', serif;
    font-size: 1.9rem;
    color: var(--gold);
    margin-bottom: 6px;
  }
  .sec-head p {
    color: var(--muted);
    font-style: italic;
    font-size: 0.95rem;
  }

  .rule {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    margin: 0 0 36px;
    opacity: 0.3;
  }

  /* CARDS */
  .grid { display: grid; gap: 14px; }
  .grid-2 { grid-template-columns: repeat(auto-fill, minmax(280px,1fr)); }
  .grid-3 { grid-template-columns: repeat(auto-fill, minmax(220px,1fr)); }

  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 20px 22px;
    transition: transform 0.22s, border-color 0.22s, box-shadow 0.22s;
    position: relative;
    overflow: hidden;
  }
  .card::after {
    content: attr(data-glyph);
    position: absolute;
    right: 14px; top: 12px;
    font-size: 2rem;
    opacity: 0.12;
    pointer-events: none;
  }
  .card:hover {
    transform: translateY(-5px);
    border-color: rgba(242,193,78,0.3);
    box-shadow: 0 10px 30px rgba(0,0,0,0.4);
  }

  .card-accent {
    width: 32px; height: 3px;
    border-radius: 2px;
    margin-bottom: 12px;
  }

  .card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    color: var(--gold);
    margin-bottom: 4px;
  }

  .card .label {
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 10px;
  }

  .card .analogy {
    font-style: italic;
    color: var(--lavender);
    font-size: 0.9rem;
    margin-bottom: 10px;
    line-height: 1.5;
    border-left: 2px solid rgba(184,169,232,0.3);
    padding-left: 10px;
  }

  .card .desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.55;
  }

  .tag {
    display: inline-block;
    font-size: 0.65rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 2px 8px;
    border-radius: 20px;
    margin-top: 8px;
  }
  .tag-fire { background:rgba(255,112,67,0.18); color:var(--fire); border:1px solid rgba(255,112,67,0.3); }
  .tag-earth { background:rgba(102,187,106,0.18); color:var(--earth); border:1px solid rgba(102,187,106,0.3); }
  .tag-air { background:rgba(77,208,225,0.18); color:var(--air); border:1px solid rgba(77,208,225,0.3); }
  .tag-water { background:rgba(121,134,203,0.18); color:var(--water); border:1px solid rgba(121,134,203,0.3); }
  .tag-cardinal { background:rgba(240,143,160,0.15); color:var(--rose); border:1px solid rgba(240,143,160,0.3); }
  .tag-fixed { background:rgba(242,193,78,0.15); color:var(--gold); border:1px solid rgba(242,193,78,0.3); }
  .tag-mutable { background:rgba(94,207,202,0.15); color:var(--teal); border:1px solid rgba(94,207,202,0.3); }

  /* INTRO CALLOUT */
  .callout {
    background: linear-gradient(135deg, rgba(242,193,78,0.08), rgba(17,14,42,0.9));
    border: 1px solid rgba(242,193,78,0.25);
    border-radius: 16px;
    padding: 24px 28px;
    margin-bottom: 36px;
    font-size: 0.95rem;
    line-height: 1.7;
  }
  .callout strong { color: var(--gold); }
  .callout em { color: var(--lavender); }

  /* PLANET SPECIAL CARDS */
  .planet-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 20px 22px;
    display: flex;
    gap: 16px;
    align-items: flex-start;
    transition: transform 0.22s, border-color 0.22s;
  }
  .planet-card:hover {
    transform: translateY(-4px);
    border-color: rgba(242,193,78,0.3);
  }
  .planet-icon {
    font-size: 2.2rem;
    flex-shrink: 0;
    line-height: 1;
    margin-top: 2px;
  }
  .planet-card h3 {
    font-family: 'Playfair Display', serif;
    color: var(--gold);
    font-size: 1rem;
    margin-bottom: 2px;
  }
  .planet-card .kid-role {
    font-size: 0.78rem;
    color: var(--teal);
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-bottom: 6px;
  }
  .planet-card .analogy {
    font-style: italic;
    color: var(--lavender);
    font-size: 0.88rem;
    border-left: 2px solid rgba(184,169,232,0.3);
    padding-left: 10px;
    margin-bottom: 8px;
    line-height: 1.5;
  }
  .planet-card .desc {
    font-size: 0.85rem;
    color: var(--muted);
    line-height: 1.5;
  }

  footer {
    text-align: center;
    padding: 40px 0 0;
    color: var(--muted);
    font-style: italic;
    font-size: 0.85rem;
  }

  @media(max-width:600px){
    .grid-2, .grid-3 { grid-template-columns: 1fr; }
    h1 { font-size: 1.7rem; }
    .tab-btn { font-size: 0.76rem; padding: 5px 12px; }
  }
</style>
</head>
<body>

<!-- stars -->
<div class="stars" id="stars"></div>

<!-- NAV -->
<nav class="tab-nav">
  <button class="tab-btn active" onclick="show('home')">🏠 Home</button>
  <button class="tab-btn" onclick="show('zodiac')">⭐ Zodiac Signs</button>
  <button class="tab-btn" onclick="show('houses')">🏠 The Houses</button>
  <button class="tab-btn" onclick="show('planets')">🪐 Planets</button>
  <button class="tab-btn" onclick="show('asteroids')">🌸 Asteroids</button>
  <button class="tab-btn" onclick="show('points')">🔭 Special Points</button>
</nav>

<div class="wrap">

  <!-- HOME -->
  <div class="section active" id="home">
    <div class="hero">
      <span class="hero-icon">🛝</span>
      <h1>The Cosmic Playground</h1>
      <p>Everything in astrology explained as kids on a playground — simple, fun, and surprisingly accurate.</p>
    </div>

    <div class="callout">
      <strong>The Big Idea:</strong> Imagine a giant magical playground. Every part of astrology is just a different <em>kid, role, or area of the playground.</em><br><br>
      🧒 <strong>Zodiac Signs</strong> = The personality of each kid — who they ARE<br>
      🏗️ <strong>Houses</strong> = The different areas of the playground — WHERE they play<br>
      🌟 <strong>Planets</strong> = The main characters — the popular, loud, impossible-to-ignore kids<br>
      🌸 <strong>Asteroids</strong> = The quieter, more complex supporting kids<br>
      🗺️ <strong>Special Points</strong> = The invisible rules and forces that shape how the whole playground operates<br><br>
      Use the tabs above to explore each section! ✨
    </div>

    <div class="grid grid-2">
      <div class="card" data-glyph="⭐">
        <div class="card-accent" style="background:var(--gold)"></div>
        <h3>Zodiac Signs</h3>
        <p class="desc">The 12 signs are like 12 totally different kids. Same playground, wildly different personalities — from the boldest show-off to the dreamiest wallflower.</p>
      </div>
      <div class="card" data-glyph="🏗️">
        <div class="card-accent" style="background:var(--teal)"></div>
        <h3>The 12 Houses</h3>
        <p class="desc">The playground has 12 zones — the swings, the sandpit, the climbing frame. Each zone is a different area of your life.</p>
      </div>
      <div class="card" data-glyph="🌟">
        <div class="card-accent" style="background:var(--rose)"></div>
        <h3>Planets</h3>
        <p class="desc">The main characters. The Sun is basically the main kid everyone orbits. The Moon is the sensitive best friend. Mars is the one starting every game — and every argument.</p>
      </div>
      <div class="card" data-glyph="🌸">
        <div class="card-accent" style="background:var(--lavender)"></div>
        <h3>Asteroids & Points</h3>
        <p class="desc">The quieter, more layered kids. They don't dominate like the planets — but once you notice them, you can't unsee them.</p>
      </div>
    </div>
  </div>

  <!-- ZODIAC SIGNS -->
  <div class="section" id="zodiac">
    <div class="sec-head">
      <h2>⭐ The 12 Zodiac Signs</h2>
      <p>Each sign is a different kid — same playground, completely different vibe</p>
    </div>
    <div class="rule"></div>

    <div class="callout">
      If the <strong>elements</strong> are what a kid is made of (fire, earth, air, water) and the <strong>modalities</strong> are how they play (starter, sustainer, adapter) — then the <strong>zodiac sign</strong> is the <em>full person</em>. The combination of both. Two ingredients baked into one unique kid. 🧁
    </div>

    <div class="grid grid-2">

      <div class="card" data-glyph="♈">
        <div class="card-accent" style="background:var(--fire)"></div>
        <h3>Aries ♈</h3>
        <div class="label">Mar 21 – Apr 19</div>
        <div class="analogy">"The kid who sprints onto the playground before the bell even stops ringing."</div>
        <div class="desc">First in line. Always. Doesn't wait, doesn't plan, just GOES. Fearless and a little reckless — in the best way.</div>
        <span class="tag tag-fire">🔥 Fire</span> <span class="tag tag-cardinal">Cardinal</span>
      </div>

      <div class="card" data-glyph="♉">
        <div class="card-accent" style="background:var(--earth)"></div>
        <h3>Taurus ♉</h3>
        <div class="label">Apr 20 – May 20</div>
        <div class="analogy">"The kid who found the best sunny spot on the bench and absolutely will not be moved."</div>
        <div class="desc">Comfortable, patient, sensory. Brought snacks. Has the best snacks. Is not sharing the snacks unless they really like you.</div>
        <span class="tag tag-earth">🌿 Earth</span> <span class="tag tag-fixed">Fixed</span>
      </div>

      <div class="card" data-glyph="♊">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>Gemini ♊</h3>
        <div class="label">May 21 – Jun 20</div>
        <div class="analogy">"The kid somehow playing tag AND doing hopscotch AND telling three different stories simultaneously."</div>
        <div class="desc">Curious, quick, and impossible to pin down. Two different moods at once — both of them interesting.</div>
        <span class="tag tag-air">💨 Air</span> <span class="tag tag-mutable">Mutable</span>
      </div>

      <div class="card" data-glyph="♋">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>Cancer ♋</h3>
        <div class="label">Jun 21 – Jul 22</div>
        <div class="analogy">"The kid who made sure everyone had a buddy before the game started — and cried a little when someone got left out."</div>
        <div class="desc">Nurturing, protective, deeply feeling. The playground mom friend. Their shell is tough but inside? Pure softness.</div>
        <span class="tag tag-water">💧 Water</span> <span class="tag tag-cardinal">Cardinal</span>
      </div>

      <div class="card" data-glyph="♌">
        <div class="card-accent" style="background:var(--fire)"></div>
        <h3>Leo ♌</h3>
        <div class="label">Jul 23 – Aug 22</div>
        <div class="analogy">"The kid doing a whole choreographed performance... that nobody asked for... that everyone is watching anyway."</div>
        <div class="desc">Magnetic, generous, dramatic. Could make playing on a see-saw look like a Broadway show. And honestly? You'd applaud.</div>
        <span class="tag tag-fire">🔥 Fire</span> <span class="tag tag-fixed">Fixed</span>
      </div>

      <div class="card" data-glyph="♍">
        <div class="card-accent" style="background:var(--earth)"></div>
        <h3>Virgo ♍</h3>
        <div class="label">Aug 23 – Sep 22</div>
        <div class="analogy">"The kid who rewrote the rules of tag to make them more fair, efficient, and better for everyone."</div>
        <div class="desc">Analytical, helpful, quietly brilliant. Notices the thing nobody else noticed. Usually right. Occasionally insufferable about it.</div>
        <span class="tag tag-earth">🌿 Earth</span> <span class="tag tag-mutable">Mutable</span>
      </div>

      <div class="card" data-glyph="♎">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>Libra ♎</h3>
        <div class="label">Sep 23 – Oct 22</div>
        <div class="analogy">"The kid who spent 25 minutes deciding which game to play and made it look beautiful somehow."</div>
        <div class="desc">Charming, fair, indecisive. Wants everyone to be happy. Genuinely distressed when people argue. Dressed the best, obviously.</div>
        <span class="tag tag-air">💨 Air</span> <span class="tag tag-cardinal">Cardinal</span>
      </div>

      <div class="card" data-glyph="♏">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>Scorpio ♏</h3>
        <div class="label">Oct 23 – Nov 21</div>
        <div class="analogy">"The kid sitting in the corner watching everyone... knowing everything... saying nothing."</div>
        <div class="desc">Intense, magnetic, secretive. They already know who likes who and why. They won't tell you. They're waiting to see if you figure it out yourself.</div>
        <span class="tag tag-water">💧 Water</span> <span class="tag tag-fixed">Fixed</span>
      </div>

      <div class="card" data-glyph="♐">
        <div class="card-accent" style="background:var(--fire)"></div>
        <h3>Sagittarius ♐</h3>
        <div class="label">Nov 22 – Dec 21</div>
        <div class="analogy">"The kid who climbed over the fence to see what's on the other side — and came back with stories."</div>
        <div class="desc">Free, philosophical, blunt. Always chasing the horizon. Will tell you an uncomfortable truth and then laugh. Lovably untameable.</div>
        <span class="tag tag-fire">🔥 Fire</span> <span class="tag tag-mutable">Mutable</span>
      </div>

      <div class="card" data-glyph="♑">
        <div class="card-accent" style="background:var(--earth)"></div>
        <h3>Capricorn ♑</h3>
        <div class="label">Dec 22 – Jan 19</div>
        <div class="analogy">"The kid who showed up to recess with a five-year plan and actually stuck to it."</div>
        <div class="desc">Disciplined, dry, quietly hilarious. While other kids are playing, Capricorn is building something that lasts. Will outlast everyone. Patient as a mountain.</div>
        <span class="tag tag-earth">🌿 Earth</span> <span class="tag tag-cardinal">Cardinal</span>
      </div>

      <div class="card" data-glyph="♒">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>Aquarius ♒</h3>
        <div class="label">Jan 20 – Feb 18</div>
        <div class="analogy">"The kid who invented an entirely new game that the rest of the school won't understand for another ten years."</div>
        <div class="desc">Eccentric, humanitarian, a little detached. Cares deeply about everyone in theory. Sometimes forgets to care about the person right in front of them.</div>
        <span class="tag tag-air">💨 Air</span> <span class="tag tag-fixed">Fixed</span>
      </div>

      <div class="card" data-glyph="♓">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>Pisces ♓</h3>
        <div class="label">Feb 19 – Mar 20</div>
        <div class="analogy">"The kid sitting by the puddle having a full conversation with a imaginary friend — and the imaginary friend is probably real."</div>
        <div class="desc">Dreamy, empathetic, mystical. Feels everything from everyone. Has one foot in another dimension at all times. Somehow always knows things they shouldn't.</div>
        <span class="tag tag-water">💧 Water</span> <span class="tag tag-mutable">Mutable</span>
      </div>

    </div>
  </div>

  <!-- HOUSES -->
  <div class="section" id="houses">
    <div class="sec-head">
      <h2>🏗️ The 12 Houses</h2>
      <p>The 12 zones of the playground — each one a different area of your life</p>
    </div>
    <div class="rule"></div>

    <div class="callout">
      If the zodiac signs are the <strong>kids</strong> and the planets are the <strong>main characters</strong> — then the houses are the <strong>different zones of the playground.</strong> The swings, the sandpit, the secret corner behind the bushes. Wherever a planet lands, <em>that's the zone of life it's playing in.</em>
    </div>

    <div class="grid grid-2">

      <div class="card" data-glyph="🪞">
        <div class="card-accent" style="background:var(--rose)"></div>
        <h3>House 1 — The Mirror Zone</h3>
        <div class="label">Self · Identity · First Impressions</div>
        <div class="analogy">"The entrance gate — what everyone sees the second you walk onto the playground."</div>
        <div class="desc">Your face, your vibe, how you carry yourself. The first impression before anyone even talks to you. Your whole "look."</div>
      </div>

      <div class="card" data-glyph="💰">
        <div class="card-accent" style="background:var(--earth)"></div>
        <h3>House 2 — The Snack Bag Zone</h3>
        <div class="label">Money · Possessions · Values</div>
        <div class="analogy">"The kid's backpack — what they own, what they brought, how generous they are with it."</div>
        <div class="desc">What you have, what you value, how you earn and keep things. Your relationship with comfort and security.</div>
      </div>

      <div class="card" data-glyph="💬">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>House 3 — The Chatter Corner</h3>
        <div class="label">Communication · Siblings · Short Trips</div>
        <div class="analogy">"The gossip bench where all the talking, texting, and storytelling happens."</div>
        <div class="desc">How you talk, think, write. Your siblings, your neighborhood, short journeys, your busy everyday mind.</div>
      </div>

      <div class="card" data-glyph="🏡">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>House 4 — The Hideout Zone</h3>
        <div class="label">Home · Family · Roots</div>
        <div class="analogy">"The secret fort behind the bushes — the place you go when you need to feel safe and be yourself."</div>
        <div class="desc">Your family, childhood, roots, and the place that feels like home in your soul. The foundation under everything.</div>
      </div>

      <div class="card" data-glyph="🎨">
        <div class="card-accent" style="background:var(--fire)"></div>
        <h3>House 5 — The Show-Off Stage</h3>
        <div class="label">Creativity · Romance · Joy · Play</div>
        <div class="analogy">"The middle of the playground where kids do tricks, flirt, and basically perform for everyone watching."</div>
        <div class="desc">Fun, art, romance, children, drama, creativity. The purest joy. Where your inner child lives.</div>
      </div>

      <div class="card" data-glyph="⚕️">
        <div class="card-accent" style="background:var(--earth)"></div>
        <h3>House 6 — The Chore Chart Zone</h3>
        <div class="label">Health · Routine · Work · Habits</div>
        <div class="analogy">"The part of the playground where the kid who actually tidies up after everyone else works quietly."</div>
        <div class="desc">Daily routines, your physical body, health habits, pets, and the small repeated tasks that keep life running.</div>
      </div>

      <div class="card" data-glyph="🤝">
        <div class="card-accent" style="background:var(--lavender)"></div>
        <h3>House 7 — The Duo Zone</h3>
        <div class="label">Partnerships · Marriage · One-on-One</div>
        <div class="analogy">"The see-saw — you can't ride it alone. This zone only activates with another person."</div>
        <div class="desc">Romantic partners, best friends, business partners. Who you attract. How you show up in one-on-one relationships.</div>
      </div>

      <div class="card" data-glyph="🔮">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>House 8 — The Forbidden Zone</h3>
        <div class="label">Transformation · Shared Resources · Death & Rebirth</div>
        <div class="analogy">"The part of the playground kids dare each other to go into — dark, mysterious, and oddly magnetic."</div>
        <div class="desc">Deep transformation, shared money, sexuality, death, rebirth, secrets, and the things nobody talks about at lunch.</div>
      </div>

      <div class="card" data-glyph="🌍">
        <div class="card-accent" style="background:var(--fire)"></div>
        <h3>House 9 — The Fence Gate Zone</h3>
        <div class="label">Philosophy · Travel · Higher Learning</div>
        <div class="analogy">"The gate at the edge of the playground that leads to the wider world — the kid always peeking through it."</div>
        <div class="desc">Long-distance travel, big ideas, religion, philosophy, university, and the search for meaning and truth.</div>
      </div>

      <div class="card" data-glyph="👑">
        <div class="card-accent" style="background:var(--gold)"></div>
        <h3>House 10 — The Flagpole Zone</h3>
        <div class="label">Career · Reputation · Public Life</div>
        <div class="analogy">"The highest point of the playground — everyone can see who's up there. It's your legacy zone."</div>
        <div class="desc">Career, ambition, public image, what you're known for. The mountaintop of the chart. What you build for the world to see.</div>
      </div>

      <div class="card" data-glyph="🌠">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>House 11 — The Squad Zone</h3>
        <div class="label">Friendships · Community · Hopes & Dreams</div>
        <div class="analogy">"The big group game zone — where everyone's welcome, teams form, and big dreams get shouted out loud."</div>
        <div class="desc">Friend groups, communities, social causes, technology, and your highest hopes for the future.</div>
      </div>

      <div class="card" data-glyph="🌊">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>House 12 — The Shadow Zone</h3>
        <div class="label">Subconscious · Hidden Things · Karma</div>
        <div class="analogy">"The part of the playground nobody talks about — behind the equipment, in the quiet. Things happen there that nobody fully explains."</div>
        <div class="desc">Dreams, the subconscious, hidden enemies, karma, spiritual retreat, and all the things working in the background of your life.</div>
      </div>

    </div>
  </div>

  <!-- PLANETS -->
  <div class="section" id="planets">
    <div class="sec-head">
      <h2>🪐 The Planets</h2>
      <p>The main characters — each one a different kid with a very specific role on the playground</p>
    </div>
    <div class="rule"></div>

    <div class="callout">
      The planets are the <strong>most important kids on the playground</strong> — the ones everyone notices. Each one has a specific <em>job</em>, a specific <em>personality</em>, and they're always doing their thing in one of the 12 zones (houses). Wherever they are, <em>that's where the action is.</em>
    </div>

    <div class="grid grid-2">

      <div class="planet-card">
        <div class="planet-icon">☀️</div>
        <div>
          <h3>The Sun</h3>
          <div class="kid-role">The Main Character</div>
          <div class="analogy">"The kid everyone on the playground unconsciously faces toward — like a sunflower. The centre of the whole story."</div>
          <div class="desc">Your core identity. Who you ARE at your deepest. Every other planet orbits this energy. The hero of your chart.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">🌙</div>
        <div>
          <h3>The Moon</h3>
          <div class="kid-role">The Feelings Kid</div>
          <div class="analogy">"The kid who feels everything — cries when the game ends, laughs the loudest, needs a hug after a hard day."</div>
          <div class="desc">Your emotional world, instincts, and what makes you feel safe. Changes quickly — like the actual moon. Your inner private self.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">☿</div>
        <div>
          <h3>Mercury</h3>
          <div class="kid-role">The Chatterbox</div>
          <div class="analogy">"The kid running between every group, carrying messages, explaining rules, asking questions, making puns nobody asked for."</div>
          <div class="desc">How you think, talk, learn, and process information. Your wit, your logic, your communication style.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♀️</div>
        <div>
          <h3>Venus</h3>
          <div class="kid-role">The Sweetheart</div>
          <div class="analogy">"The kid who made the playground look pretty, brings people together, and everyone has a tiny crush on."</div>
          <div class="desc">What you love, how you attract, what you find beautiful. Governs romance, art, money, pleasure, and your magnetic pull.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♂️</div>
        <div>
          <h3>Mars</h3>
          <div class="kid-role">The Fighter</div>
          <div class="analogy">"The kid who started the game, argued about the rules, won, and is already challenging someone to a rematch."</div>
          <div class="desc">Drive, ambition, anger, and desire. How you fight, compete, go after what you want, and channel raw energy.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♃</div>
        <div>
          <h3>Jupiter</h3>
          <div class="kid-role">The Lucky One</div>
          <div class="analogy">"The kid who always finds money on the ground, gets picked first, and somehow wins every raffle."</div>
          <div class="desc">Where luck, expansion, and abundance flow into your life. The biggest, most generous planet. Everything it touches, it grows.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♄</div>
        <div>
          <h3>Saturn</h3>
          <div class="kid-role">The Strict Teacher</div>
          <div class="analogy">"The playground monitor who makes you do it again properly if you did it wrong — frustrating now, grateful later."</div>
          <div class="desc">Discipline, lessons, karma, and structure. Where life makes you grow up whether you want to or not. Takes ~29 years to go around your chart once.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♅</div>
        <div>
          <h3>Uranus</h3>
          <div class="kid-role">The Rebel</div>
          <div class="analogy">"The kid who showed up one day and broke every rule — and somehow made it cooler."</div>
          <div class="desc">Revolution, sudden change, genius, and rebellion. Where you break free and do things completely differently. Shocks and awakens wherever it lands.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♆</div>
        <div>
          <h3>Neptune</h3>
          <div class="kid-role">The Dreamer</div>
          <div class="analogy">"The kid who is technically on the playground but their mind is somewhere else entirely — possibly a fairy tale."</div>
          <div class="desc">Dreams, illusions, spirituality, and confusion. Where you dissolve, transcend, or get completely lost in beautiful fog.</div>
        </div>
      </div>

      <div class="planet-card">
        <div class="planet-icon">♇</div>
        <div>
          <h3>Pluto</h3>
          <div class="kid-role">The Transformer</div>
          <div class="analogy">"The kid nobody sees much — but when they show up, everything changes. Permanently."</div>
          <div class="desc">Death, rebirth, power, and obsession. Wherever Pluto is, something must die so something new can be born. The deepest, slowest, most intense force.</div>
        </div>
      </div>

    </div>
  </div>

  <!-- ASTEROIDS -->
  <div class="section" id="asteroids">
    <div class="sec-head">
      <h2>🌸 Asteroids & Minor Bodies</h2>
      <p>The quieter, more layered kids — supporting cast with surprising depth</p>
    </div>
    <div class="rule"></div>

    <div class="callout">
      Asteroids are like the <strong>quiet kids you underestimate</strong> — they're not as loud as the planets, but once you actually talk to them, you realize they have the most <em>interesting, specific, layered stories.</em> They add nuance the planets alone can't give you.
    </div>

    <div class="grid grid-2">

      <div class="card" data-glyph="🖤">
        <div class="card-accent" style="background:#8a2be2"></div>
        <h3>Lilith (Black Moon)</h3>
        <div class="label">The Wild One</div>
        <div class="analogy">"The kid who got told to sit down and be quiet — and stood up anyway. Every time."</div>
        <div class="desc">Your primal, untamed self. Where you refuse to shrink, where your shadow desires live, and where raw power that won't be domesticated hides. The part of you that won't apologize.</div>
      </div>

      <div class="card" data-glyph="🩹">
        <div class="card-accent" style="background:var(--teal)"></div>
        <h3>Chiron</h3>
        <div class="label">The Wounded Healer</div>
        <div class="analogy">"The kid who got hurt on the playground in a specific way — and became the one everyone comes to when they get hurt too."</div>
        <div class="desc">Your deepest wound — the thing that never fully heals. But once you work with it, you become a powerful guide for others with the same wound. Pain turned into purpose.</div>
      </div>

      <div class="card" data-glyph="🌾">
        <div class="card-accent" style="background:var(--earth)"></div>
        <h3>Ceres</h3>
        <div class="label">The Nurturer</div>
        <div class="analogy">"The kid who brought extra sandwiches — not to be popular, but because they genuinely couldn't stand seeing someone go hungry."</div>
        <div class="desc">How you nurture and need to be nurtured. Your relationship with food, nature, caretaking, and unconditional love. Also: grief when care is lost.</div>
      </div>

      <div class="card" data-glyph="🏹">
        <div class="card-accent" style="background:var(--gold)"></div>
        <h3>Pallas (Athena)</h3>
        <div class="label">The Strategist</div>
        <div class="analogy">"The kid who figured out the optimal winning strategy for every game before anyone else had even read the rules."</div>
        <div class="desc">Wisdom, strategy, and pattern recognition. How you solve problems and fight for justice. Your inner warrior-scholar who thinks before striking.</div>
      </div>

      <div class="card" data-glyph="💍">
        <div class="card-accent" style="background:var(--rose)"></div>
        <h3>Juno</h3>
        <div class="label">The Committed One</div>
        <div class="analogy">"The kid who, when they pick a best friend, picks them for life — and expects the same loyalty in return."</div>
        <div class="desc">What you truly need in long-term commitment. Where you seek equality and devotion in partnership. Shows what a healthy soulmate bond looks like for you.</div>
      </div>

      <div class="card" data-glyph="🕯️">
        <div class="card-accent" style="background:var(--fire)"></div>
        <h3>Vesta</h3>
        <div class="label">The Devoted One</div>
        <div class="analogy">"The kid who was so focused on one particular game that they became the best in the school at it — and didn't even notice."</div>
        <div class="desc">Sacred devotion and inner flame. What you dedicate yourself to most completely. The thing that burns inside you that no one and nothing can put out.</div>
      </div>

      <div class="card" data-glyph="🌀">
        <div class="card-accent" style="background:var(--lavender)"></div>
        <h3>Eris</h3>
        <div class="label">The Truth-Teller</div>
        <div class="analogy">"The kid who walked up to the popular group and said 'actually, this game is unfair' — and was right."</div>
        <div class="desc">Discord, chaos, and radical truth. Where you expose hidden unfairness and refuse to pretend things are fine when they're not. A necessary disruptor.</div>
      </div>

      <div class="card" data-glyph="❄️">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>Sedna</h3>
        <div class="label">The Isolated One</div>
        <div class="analogy">"The kid sent to play alone by someone they trusted — who eventually built their own entire world out there."</div>
        <div class="desc">Deep themes of betrayal, isolation, and surrender. The journey from victimhood to transcendence. The furthest, coldest, most soul-level asteroid in the chart.</div>
      </div>

    </div>
  </div>

  <!-- SPECIAL POINTS -->
  <div class="section" id="points">
    <div class="sec-head">
      <h2>🔭 Special Chart Points</h2>
      <p>The invisible forces shaping how the whole playground operates</p>
    </div>
    <div class="rule"></div>

    <div class="callout">
      These aren't kids — they're the <strong>invisible rules and forces of the playground itself.</strong> You can't see them running around, but they shape everything. The invisible bell that ends the game. The unspoken hierarchy. The destiny that pulled a certain kid to a certain spot. <em>You feel them even when you can't name them.</em>
    </div>

    <div class="grid grid-2">

      <div class="card" data-glyph="⬆️">
        <div class="card-accent" style="background:var(--gold)"></div>
        <h3>Ascendant (Rising Sign)</h3>
        <div class="label">The Entrance Gate</div>
        <div class="analogy">"The outfit and energy you show up in. The thing everyone sees before they even know your name."</div>
        <div class="desc">The sign rising on the horizon at your birth. Sets the entire chart. Your social mask, your vibe, how strangers read you before you speak. Often feels more "you" than your Sun sign.</div>
      </div>

      <div class="card" data-glyph="⬇️">
        <div class="card-accent" style="background:var(--lavender)"></div>
        <h3>Descendant</h3>
        <div class="label">The Partner Zone</div>
        <div class="analogy">"Directly opposite the entrance gate — the part of the playground you never go to alone. You need someone else to unlock it."</div>
        <div class="desc">What you seek in others. The qualities in partners you don't fully see in yourself. Your shadow self reflected in relationship.</div>
      </div>

      <div class="card" data-glyph="🔝">
        <div class="card-accent" style="background:var(--gold)"></div>
        <h3>Midheaven (MC)</h3>
        <div class="label">The Flagpole</div>
        <div class="analogy">"The highest point on the playground everyone can see. What you're climbing toward your whole life."</div>
        <div class="desc">Your career, reputation, and public legacy. What you're here to achieve and be known for in the world's eyes. Your mountaintop destiny.</div>
      </div>

      <div class="card" data-glyph="🔻">
        <div class="card-accent" style="background:var(--water)"></div>
        <h3>IC (Imum Coeli)</h3>
        <div class="label">The Root System</div>
        <div class="analogy">"The underground root system beneath the playground — invisible, but everything alive grows from it."</div>
        <div class="desc">Your private self, ancestry, childhood foundation, and what "home" means to your soul. The bottom of everything. The roots of the tree.</div>
      </div>

      <div class="card" data-glyph="☊">
        <div class="card-accent" style="background:var(--teal)"></div>
        <h3>North Node</h3>
        <div class="label">The Destiny Gate</div>
        <div class="analogy">"The part of the playground the kid is being nudged toward — unfamiliar, a little scary, but somehow calling to them."</div>
        <div class="desc">Your soul's purpose this lifetime. The direction you're meant to grow toward. It feels uncomfortable because it's new — but it's where your evolution lives.</div>
      </div>

      <div class="card" data-glyph="☋">
        <div class="card-accent" style="background:var(--rose)"></div>
        <h3>South Node</h3>
        <div class="label">The Comfort Zone</div>
        <div class="analogy">"The game the kid already knows how to play perfectly — almost too perfectly. They could do it in their sleep. That's the problem."</div>
        <div class="desc">Where your soul comes from — past life gifts and comfort zones. Natural talents that can become a crutch. You're meant to release this, not live in it.</div>
      </div>

      <div class="card" data-glyph="✨">
        <div class="card-accent" style="background:var(--gold)"></div>
        <h3>Part of Fortune</h3>
        <div class="label">The Lucky Spot</div>
        <div class="analogy">"The specific corner of the playground where this kid always seems to find a four-leaf clover."</div>
        <div class="desc">Where ease, joy, and natural abundance flow for you. Calculated from your Sun, Moon, and Rising. The sweet spot where effort feels effortless.</div>
      </div>

      <div class="card" data-glyph="🌀">
        <div class="card-accent" style="background:var(--lavender)"></div>
        <h3>Vertex</h3>
        <div class="label">The Fate Door</div>
        <div class="analogy">"The strange door in the fence that sometimes swings open and someone walks through it who changes everything — and you didn't plan for it at all."</div>
        <div class="desc">Fated encounters and destiny-level meetings. When someone activates your Vertex, it feels like the universe orchestrated the whole thing. Because it did.</div>
      </div>

      <div class="card" data-glyph="⚖️">
        <div class="card-accent" style="background:var(--air)"></div>
        <h3>Lot of Spirit</h3>
        <div class="label">The Inner Compass</div>
        <div class="analogy">"The invisible compass every kid carries — it points toward what their soul is actually here to DO, not just feel."</div>
        <div class="desc">Your soul's active mission and purpose. Complements the Part of Fortune. Where Fortune is where you receive — Spirit is where you give and create meaning.</div>
      </div>

      <div class="card" data-glyph="🌑">
        <div class="card-accent" style="background:#3a1a5e"></div>
        <h3>Black Moon Lilith (Point)</h3>
        <div class="label">The Shadow Door</div>
        <div class="analogy">"The part of the playground the kid pretends they never go to — but everyone knows they do. It's where their realest self lives."</div>
        <div class="desc">The lunar apogee — the Moon's farthest point from Earth. Represents your deepest suppressed desires, untamed instincts, and where you've been shamed for being fully yourself.</div>
      </div>

    </div>
  </div>

  <footer>✦ The stars don't define you — they describe you ✦</footer>

</div><!-- end wrap -->

<script>
  // Generate stars
  const starsEl = document.getElementById('stars');
  for (let i = 0; i < 120; i++) {
    const s = document.createElement('div');
    s.className = 'star';
    const size = Math.random() * 2 + 0.5;
    s.style.cssText = `
      width:${size}px; height:${size}px;
      left:${Math.random()*100}%;
      top:${Math.random()*100}%;
      --d:${2 + Math.random()*5}s;
      --o:${0.4 + Math.random()*0.6};
      animation-delay:${Math.random()*6}s;
    `;
    starsEl.appendChild(s);
  }

  // Tab switching
  function show(id) {
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    event.target.classList.add('active');
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>
</body>
</html>
