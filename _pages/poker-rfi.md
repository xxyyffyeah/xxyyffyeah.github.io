---
layout: page
permalink: /poker-rfi/
title: poker
description: Interactive preflop RFI and defense ranges by position
nav: true
nav_order: 7
---

<style>
/* Main Container */
.poker-strategy-tool {
  max-width: 900px;
  margin: 0 auto;
  padding: 20px;
}

/* Position Controls */
.position-controls {
  background: #f8f9fa;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
}

.position-row,
.villain-row {
  margin: 15px 0;
}

.control-label {
  font-weight: 700;
  color: #495057;
  font-size: 1.05em;
  margin-bottom: 12px;
  text-align: center;
  display: block;
}

/* Hero Position Navigation */
.hero-nav {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 15px;
}

.position-display {
  min-width: 120px;
  padding: 12px 20px;
  background: white;
  border: 2px solid #dee2e6;
  border-radius: 8px;
  text-align: center;
  font-weight: 700;
  font-size: 1.1em;
  color: #212529;
  user-select: none;
}

.nav-btn {
  width: 50px;
  height: 50px;
  border: 2px solid #007bff;
  background: white;
  color: #007bff;
  border-radius: 50%;
  font-size: 1.5em;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  user-select: none;
}

.nav-btn:hover {
  background: #007bff;
  color: white;
  transform: scale(1.1);
}

.nav-btn:active {
  transform: scale(0.95);
}

.nav-btn:disabled {
  opacity: 0.3;
  cursor: not-allowed;
  border-color: #dee2e6;
  color: #dee2e6;
}

.nav-btn:disabled:hover {
  background: white;
  color: #dee2e6;
  transform: scale(1);
}

/* Villain Buttons */
.villain-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  justify-content: center;
  margin-top: 10px;
}

.villain-btn {
  padding: 10px 18px;
  border: 2px solid #dee2e6;
  background: white;
  color: #495057;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.95em;
  cursor: pointer;
  transition: all 0.2s;
  min-width: 75px;
  text-align: center;
}

.villain-btn:hover {
  background: #f8f9fa;
  border-color: #007bff;
  transform: translateY(-2px);
}

.villain-btn.active {
  background: #007bff;
  color: white;
  border-color: #007bff;
  box-shadow: 0 2px 8px rgba(0,123,255,0.3);
}

.villain-btn.none {
  background: #e9ecef;
  border-color: #adb5bd;
  color: #6c757d;
}

.villain-btn.none.active {
  background: #6c757d;
  color: white;
  border-color: #6c757d;
}

.villain-btn:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.villain-btn:disabled:hover {
  transform: none;
  background: white;
  border-color: #dee2e6;
}


/* Hand Matrix */
.hand-matrix {
  display: grid;
  grid-template-columns: repeat(13, 1fr);
  gap: 2px;
  max-width: 800px;
  margin: 20px auto;
  background: #dee2e6;
  padding: 2px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.hand-cell {
  aspect-ratio: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 0.95em;
  border: 1px solid #adb5bd;
  cursor: default;
  user-select: none;
  transition: transform 0.1s;
}

.hand-cell:hover {
  transform: scale(1.05);
  z-index: 10;
}

/* Action Colors */
.hand-cell.fold {
  background: #e9ecef;
  color: #6c757d;
}

.hand-cell.raise {
  background: #dc3545;
  color: white;
}

.hand-cell.raise-value {
  background: #c82333;
  color: white;
}

.hand-cell.raise-bluff {
  background: #0069d9;
  color: white;
}

.hand-cell.threebet-value {
  background: #c82333;
  color: white;
}

.hand-cell.threebet-bluff {
  background: #0069d9;
  color: white;
}

.hand-cell.limp {
  background: #28a745;
  color: white;
}

.hand-cell.call {
  background: #20c997;
  color: white;
}

/* Legend */
.legend {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  margin: 20px 0;
  padding: 15px;
  background: white;
  border-radius: 8px;
  border: 1px solid #dee2e6;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 6px 12px;
  border-radius: 6px;
  background: #f8f9fa;
}

.legend-color {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  border: 2px solid rgba(0,0,0,0.1);
}

.legend-text {
  font-size: 0.9em;
  font-weight: 600;
  color: #495057;
}


/* Mobile Optimizations */
@media (max-width: 768px) {
  .poker-strategy-tool {
    padding: 10px;
  }

  .position-display {
    min-width: 100px;
    font-size: 1em;
  }

  .nav-btn {
    width: 48px;
    height: 48px;
    font-size: 1.3em;
  }

  .villain-btn {
    padding: 8px 14px;
    font-size: 0.9em;
    min-width: 65px;
  }

  .hand-matrix {
    font-size: 0.65em;
    gap: 1px;
    padding: 1px;
  }

  .legend {
    gap: 8px;
    padding: 12px;
  }

  .legend-item {
    padding: 4px 8px;
  }

  .legend-color {
    width: 24px;
    height: 24px;
  }

  .legend-text {
    font-size: 0.8em;
  }
}

@media (max-width: 480px) {
  .hand-matrix {
    font-size: 0.55em;
  }

  .position-display {
    min-width: 90px;
    padding: 10px 16px;
    font-size: 0.95em;
  }

  .nav-btn {
    width: 44px;
    height: 44px;
  }

  .villain-btn {
    padding: 7px 12px;
    font-size: 0.85em;
    min-width: 60px;
  }
}

/* Dark mode support */
@media (prefers-color-scheme: dark) {
  .position-controls {
    background: #2d3748;
  }

  .position-display {
    background: #1a202c;
    border-color: #4a5568;
    color: #e2e8f0;
  }

  .nav-btn {
    background: #2d3748;
    border-color: #3182ce;
    color: #3182ce;
  }

  .nav-btn:hover {
    background: #3182ce;
    color: white;
  }

  .villain-btn {
    background: #1a202c;
    border-color: #4a5568;
    color: #e2e8f0;
  }

  .villain-btn.active {
    background: #3182ce;
    border-color: #3182ce;
  }

  .villain-btn.none {
    background: #2d3748;
    border-color: #4a5568;
    color: #a0aec0;
  }

  .villain-btn.none.active {
    background: #4a5568;
    color: #e2e8f0;
  }

  .legend {
    background: #2d3748;
    border-color: #4a5568;
  }

  .legend-item {
    background: #1a202c;
  }

  .legend-text {
    color: #e2e8f0;
  }

  .control-label {
    color: #e2e8f0;
  }
}

/* Touch swipe hint */
.swipe-hint {
  text-align: center;
  color: #6c757d;
  font-size: 0.85em;
  margin-top: 10px;
  font-style: italic;
}

@media (min-width: 769px) {
  .swipe-hint {
    display: none;
  }
}
</style>

<div class="poker-strategy-tool">
  <p style="text-align: center; color: #6c757d; margin-bottom: 25px;">
    Navigate your position with arrows, then select a villain to see defense strategy (or "None" for RFI).
  </p>

  <!-- Position Controls -->
  <div class="position-controls">
    <!-- Hero Position -->
    <div class="position-row">
      <label class="control-label">Your Position:</label>
      <div class="hero-nav">
        <button class="nav-btn prev" id="hero-prev" aria-label="Previous position">◀</button>
        <div class="position-display" id="hero-position">BB</div>
        <button class="nav-btn next" id="hero-next" aria-label="Next position">▶</button>
      </div>
      <div class="swipe-hint">💡 Swipe left/right to navigate</div>
    </div>

    <!-- Villain Selection -->
    <div class="villain-row">
      <label class="control-label">Villain:</label>
      <div class="villain-buttons" id="villain-buttons">
        <!-- Dynamically populated -->
      </div>
    </div>
  </div>

  <!-- Legend -->
  <div class="legend" id="legend"></div>

  <!-- Hand Matrix -->
  <div class="hand-matrix" id="hand-matrix"></div>
</div>

<script>
// Hand matrix structure
const hands = [
  ['AA', 'AKs', 'AQs', 'AJs', 'ATs', 'A9s', 'A8s', 'A7s', 'A6s', 'A5s', 'A4s', 'A3s', 'A2s'],
  ['AKo', 'KK', 'KQs', 'KJs', 'KTs', 'K9s', 'K8s', 'K7s', 'K6s', 'K5s', 'K4s', 'K3s', 'K2s'],
  ['AQo', 'KQo', 'QQ', 'QJs', 'QTs', 'Q9s', 'Q8s', 'Q7s', 'Q6s', 'Q5s', 'Q4s', 'Q3s', 'Q2s'],
  ['AJo', 'KJo', 'QJo', 'JJ', 'JTs', 'J9s', 'J8s', 'J7s', 'J6s', 'J5s', 'J4s', 'J3s', 'J2s'],
  ['ATo', 'KTo', 'QTo', 'JTo', 'TT', 'T9s', 'T8s', 'T7s', 'T6s', 'T5s', 'T4s', 'T3s', 'T2s'],
  ['A9o', 'K9o', 'Q9o', 'J9o', 'T9o', '99', '98s', '97s', '96s', '95s', '94s', '93s', '92s'],
  ['A8o', 'K8o', 'Q8o', 'J8o', 'T8o', '98o', '88', '87s', '86s', '85s', '84s', '83s', '82s'],
  ['A7o', 'K7o', 'Q7o', 'J7o', 'T7o', '97o', '87o', '77', '76s', '75s', '74s', '73s', '72s'],
  ['A6o', 'K6o', 'Q6o', 'J6o', 'T6o', '96o', '86o', '76o', '66', '65s', '64s', '63s', '62s'],
  ['A5o', 'K5o', 'Q5o', 'J5o', 'T5o', '95o', '85o', '75o', '65o', '55', '54s', '53s', '52s'],
  ['A4o', 'K4o', 'Q4o', 'J4o', 'T4o', '94o', '84o', '74o', '64o', '54o', '44', '43s', '42s'],
  ['A3o', 'K3o', 'Q3o', 'J3o', 'T3o', '93o', '83o', '73o', '63o', '53o', '43o', '33', '32s'],
  ['A2o', 'K2o', 'Q2o', 'J2o', 'T2o', '92o', '82o', '72o', '62o', '52o', '42o', '32o', '22']
];

// Position arrays (clockwise order around the table, starting from BB)
const allPositions = ['BB', 'UTG', 'UTG+1', 'UTG+2', 'LJ', 'HJ', 'CO', 'BTN', 'SB'];

// State
let heroIndex = 0;
let selectedVillain = null; // null = "None"

// RFI Ranges
const rfiRanges = {
  'UTG': {
    name: 'UTG - Raise First In',
    stats: 'Raise: 10.1% | Fold: 89.9%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','AKs','AQs','AJs','ATs','A9s','A5s','AKo','KQs','KJs','KTs','QJs','QTs','JTs','T9s','98s']
  },
  'UTG+1': {
    name: 'UTG+1 - Raise First In',
    stats: 'Raise: 14.3% | Fold: 85.7%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','A4s','KQs','KJs','KTs','K9s','QJs','QTs','Q9s','JTs','J9s','T9s','98s','87s','AKo','AQo','AJo','KQo']
  },
  'UTG+2': {
    name: 'UTG+2 - Raise First In',
    stats: 'Raise: 15.7% | Fold: 84.3%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','55','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','KQs','KJs','KTs','K9s','QJs','QTs','Q9s','JTs','J9s','T9s','98s','87s','76s','AKo','AQo','AJo','KQo']
  },
  'LJ': {
    name: 'Lojack - Raise First In',
    stats: 'Raise: 18.3% | Fold: 81.7%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','55','44','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','KQs','KJs','KTs','K9s','QJs','QTs','Q9s','JTs','J9s','T9s','98s','87s','76s','65s','AKo','AQo','AJo','ATo','KQo','KJo']
  },
  'HJ': {
    name: 'Hijack - Raise First In',
    stats: 'Raise: 21.3% | Fold: 78.7%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','55','44','33','22','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','KQs','KJs','KTs','K9s','K8s','QJs','QTs','Q9s','JTs','J9s','T9s','T8s','98s','97s','87s','76s','65s','54s','AKo','AQo','AJo','ATo','KQo','KJo','QJo']
  },
  'CO': {
    name: 'Cutoff - Raise First In',
    stats: 'Raise: 27.0% | Fold: 73.0%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','55','44','33','22','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','KQs','KJs','KTs','K9s','K8s','K7s','QJs','QTs','Q9s','Q8s','JTs','J9s','J8s','T9s','T8s','98s','97s','87s','86s','76s','75s','65s','64s','54s','43s','AKo','AQo','AJo','ATo','A9o','KQo','KJo','KTo','QJo','QTo','JTo']
  },
  'BTN': {
    name: 'Button - Raise First In',
    stats: 'Raise: 51.1% | Fold: 48.9%',
    raise: ['AA','KK','QQ','JJ','TT','99','88','77','66','55','44','33','22','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','KQs','KJs','KTs','K9s','K8s','K7s','K6s','K5s','K4s','K3s','K2s','QJs','QTs','Q9s','Q8s','Q7s','Q6s','Q5s','Q4s','Q3s','Q2s','JTs','J9s','J8s','J7s','J6s','T9s','T8s','T7s','T6s','98s','97s','96s','87s','86s','76s','65s','54s','43s','32s','AKo','AQo','AJo','ATo','A9o','A8o','A7o','A6o','A5o','A4o','A3o','A2o','KQo','KJo','KTo','K9o','K8o','K7o','QJo','QTo','Q9o','JTo','J9o','T9o']
  },
  'SB': {
    name: 'Small Blind - RFI Strategy',
    stats: 'Raise Value: 8.8% | Raise Bluff: 13.0% | Limp: 49.6% | Fold: 29.6%',
    raiseValue: ['AA','KK','QQ','JJ','TT','99','88','77','66','55','44','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','AKo','AQo','AJo','KQs','KJs'],
    raiseBluff: ['A4s','A3s','A2s','ATo','A9o','A8o','A7o','A6o','A5o','KTs','K9s','K8s','K7s','K6s','K5s','K4s','K3s','K2s','KQo','KJo','KTo','K9o','QJs','QTs','Q9s','Q8s','QJo','QTo','JTs','J9s','J8s','JTo','T9s','T8s','T9o','98s','97s','87s','86s','76s','75s','65s','64s','54s','53s'],
    limp: ['33','22','Q7s','Q6s','Q5s','Q4s','Q3s','Q2s','Q9o','Q8o','Q7o','J7s','J6s','J5s','J4s','J3s','J2s','J9o','J8o','J7o','T7s','T6s','T5s','T4s','T3s','T2s','T8o','T7o','96s','95s','94s','93s','92s','98o','97o','85s','84s','83s','82s','87o','86o','74s','73s','72s','76o','75o','63s','62s','65o','52s','54o','43s','42s','32s']
  },
  'BB': {
    name: 'Big Blind - No RFI',
    stats: 'BB cannot open raise (already posted blind)',
    raise: []
  }
};

// Facing RFI Ranges - Complete data from PDF
const facingRFI = {
  //BB
// 对应图表: BB vs UTG/UTG+1
  'BB_vs_UTG': {
    threebet_value: ['AA', 'KK', 'QQ', 'AKs', 'AQs'],
    threebet_bluff: ['86s', '76s', '75s', '65s', '64s', '54s', '43s'],
    call: [
      'JJ', 'TT', '99', '88', '77', '66', '55', '44', '33', '22',
      'AJs', 'ATs', 'A9s', 'A8s', 'A7s', 'A6s', 'A5s', 'A4s', 'A3s', 'A2s',
      'KQs', 'KJs', 'KTs', 'K9s', 'K8s', 'K7s', 'K6s', 'K5s',
      'QJs', 'QTs', 'Q9s', 'Q8s', 'Q7s',
      'JTs', 'J9s', 'J8s', 'J7s',
      'T9s', 'T8s', 'T7s',
      '98s', '97s',
      '87s',
      'AKo', 'AQo', 'AJo', 'ATo',
      'KQo', 'KJo',
      'QJo'
    ]
  },
  // 对应图表: BB vs UTG/UTG+1 (相同数据)
  'BB_vs_UTG+1': {
    threebet_value: ['AA', 'KK', 'QQ', 'AKs', 'AQs'],
    threebet_bluff: ['86s', '76s', '75s', '65s', '64s', '54s', '43s'],
    call: [
      'JJ', 'TT', '99', '88', '77', '66', '55', '44', '33', '22',
      'AJs', 'ATs', 'A9s', 'A8s', 'A7s', 'A6s', 'A5s', 'A4s', 'A3s', 'A2s',
      'KQs', 'KJs', 'KTs', 'K9s', 'K8s', 'K7s', 'K6s', 'K5s',
      'QJs', 'QTs', 'Q9s', 'Q8s', 'Q7s',
      'JTs', 'J9s', 'J8s', 'J7s',
      'T9s', 'T8s', 'T7s',
      '98s', '97s',
      '87s',
      'AKo', 'AQo', 'AJo', 'ATo',
      'KQo', 'KJo',
      'QJo'
    ]
  },
  // 对应图表: BB vs UTG+2
  'BB_vs_UTG+2': {
    threebet_value: ['AA','KK','AKs','AKo'],
    threebet_bluff: ['A5s','A4s','A3s'],
    call: ['QQ','JJ','TT','99','88','77','66','55','44','33','22','AQs','AJs','ATs','A9s','A8s','A7s','A6s','KQs','KJs','KTs','K9s','QJs','QTs','Q9s','JTs','J9s','T9s','98s','87s','76s','65s','54s','AQo','AJo','ATo','KQo','KJo','QJo']
  },
  // 对应图表: BB vs LJ
  'BB_vs_LJ': {
    threebet_value: ['AA','KK','QQ','AKs','AKo'],
    threebet_bluff: ['A5s','A4s','A3s','A2s'],
    call: ['JJ','TT','99','88','77','66','55','44','33','22','AQs','AJs','ATs','A9s','A8s','A7s','A6s','KQs','KJs','KTs','K9s','QJs','QTs','Q9s','JTs','J9s','T9s','98s','87s','76s','65s','54s','AQo','AJo','ATo','KQo','KJo','QJo']
  },
  // 对应图表: BB vs HJ
  'BB_vs_HJ': {
    threebet_value: ['AA','KK','QQ','JJ','AKs','AQs','AKo','AQo'],
    threebet_bluff: ['A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','K8s','K7s','K6s'],
    call: ['TT','99','88','77','66','55','44','33','22','AJs','ATs','KQs','KJs','KTs','K9s','QJs','QTs','Q9s','JTs','J9s','J8s','T9s','T8s','98s','87s','76s','65s','54s','AJo','ATo','KQo','KJo','QJo','JTo']
  },
  // 对应图表: BB vs CO
  'BB_vs_CO': {
    threebet_value: ['AA','KK','QQ','JJ','TT','AKs','AQs','AJs','AKo','AQo'],
    threebet_bluff: ['A9s','A8s','A7s','A6s','A5s','A4s','A3s','A2s','K6s','K5s','K4s','K3s','Q6s','Q5s'],
    call: ['99','88','77','66','55','44','33','22','ATs','KQs','KJs','KTs','K9s','K8s','K7s','QJs','QTs','Q9s','Q8s','JTs','J9s','J8s','T9s','T8s','98s','87s','76s','65s','54s','AJo','ATo','KQo','KJo','QJo','JTo']
  },
  // 对应图表: BB vs BTN
  'BB_vs_BTN': {
    threebet_value: ['AA','KK','QQ','JJ','TT','99','88','AKs','AQs','AJs','ATs','AKo','AQo','AJo','KQo'],
    threebet_bluff: ['A7s','A6s','A5s','A4s','A3s','A2s','K7s','K6s','K5s','K4s','K3s','K2s','Q7s','Q6s','Q5s','Q4s','J7s','J6s','J5s','T7s','T6s','97s','86s','75s','64s','53s'],
    call: ['77','66','55','44','33','22','A9s','A8s','KQs','KJs','KTs','K9s','K8s','QJs','QTs','Q9s','Q8s','JTs','J9s','J8s','T9s','T8s','98s','87s','76s','ATo','A9o','KJo','KTo','QJo','QTo','JTo']
  },
  // 对应图表: BB vs SB
  'BB_vs_SB': {
    threebet_value: ['AA','KK','QQ','JJ','TT','99','88','AKs','AQs','AJs','ATs','KQs','KJs','QJs','JTs','AKo','AQo','AJo','KQo','KJo','QJo'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K8s','K7s','K6s','K5s','K4s','K3s','K2s','Q8s','Q7s','Q6s','Q5s','Q4s','Q3s','J8s','J7s','J6s','J5s','J4s','T8s','T7s','T6s','97s','86s','75s','64s','53s'],
    call: ['77','66','55','44','33','22','A9s','A8s','A7s','A6s','KTs','K9s','QTs','Q9s','J9s','T9s','98s','87s','76s','ATo','A9o','A8o','A7o','A6o','A5o','A4o','A3o','A2o','KTo','K9o','K8o','QTo','Q9o','JTo','J9o','T9o','98o']
  },

  // Small Blind scenarios (Page 7)
  'SB_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s','A3s','A2s'],
    call: ['TT','99','88','77','66','55','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','KQo','QJs','QTs','JTs','T9s','98s','87s','76s']
  },
  'SB_vs_UTG+1': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s','A3s','A2s'],
    call: ['TT','99','88','77','66','55','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','KQo','QJs','QTs','JTs','T9s','98s','87s','76s']
  },
  'SB_vs_UTG+2': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s','A3s','A2s'],
    call: ['TT','99','88','77','66','55','44','AQs','AJs','ATs','A9s','AQo','AJo','KQs','KJs','KTs','K9s','KQo','QJs','QTs','Q9s','JTs','J9s','T9s','T8s','98s','87s','76s','65s']
  },
  'SB_vs_LJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K5s','K4s'],
    call: ['99','88','77','66','55','44','AJs','ATs','A9s','AQo','AJo','ATo','KQs','KJs','KTs','K9s','KQo','KJo','QJs','QTs','Q9s','QJo','JTs','J9s','T9s','T8s','98s','87s','76s','65s']
  },
  'SB_vs_HJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K5s','K4s','K3s'],
    call: ['99','88','77','66','55','44','33','AJs','ATs','A9s','A8s','AQo','AJo','ATo','KQs','KJs','KTs','K9s','K8s','KQo','KJo','KTo','QJs','QTs','Q9s','QJo','QTo','JTs','J9s','J8s','T9s','T8s','98s','97s','87s','86s','76s','75s','65s']
  },
  'SB_vs_CO': {
    threebet_value: ['AA','AKs','AQs','AJs','AKo','AQo','KK','QQ','JJ','TT','99'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','K5s','K4s','Q9s','Q8s','J9s','J8s','T9s','T8s','98s','97s','87s','86s','76s','75s','65s','64s'],
    call: ['88','77','66','55','44','33','ATs','A9s','A8s','AJo','ATo','KQs','KJs','KTs','KQo','KJo','KTo','QJs','QTs','QJo','QTo','JTs','JTo','T9o']
  },
  'SB_vs_BTN': {
    threebet_value: ['AA','AKs','AQs','AJs','ATs','A9s','A8s','A7s','A6s','A5s','AKo','AQo','AJo','KK','QQ','JJ','TT','99','88','77','66','55','44','KQs','KJs','KTs','K9s'],
    threebet_bluff: ['A4s','A3s','A2s','ATo','K8s','K7s','K6s','K5s','K4s','K3s','K2s','KQo','KJo','KTo','K9o','QJs','QTs','Q9s','Q8s','QJo','QTo','JTs','J9s','J8s','JTo','T9s','T8s','T9o','98s','97s','87s','86s','76s','75s','65s','64s','54s','53s'],
    call: []
  },

  // Button scenarios (Page 6)
  'BTN_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s','A3s','A2s'],
    call: ['TT','99','88','77','66','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','KQo','QJs','QTs','JTs','T9s','98s','87s','76s']
  },
  'BTN_vs_UTG+1': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K5s','K4s'],
    call: ['99','88','77','66','55','AJs','ATs','A9s','AQo','AJo','KQs','KJs','KTs','KQo','QJs','QTs','JTs','T9s','98s','87s','76s']
  },
  'BTN_vs_UTG+2': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','Q9s','Q8s','J9s','T9s','98s','87s'],
    call: ['99','88','77','66','55','44','AJs','ATs','A9s','A8s','AQo','AJo','ATo','KQs','KJs','KTs','KQo','KJo','QJs','QTs','QJo','JTs','J9s']
  },
  'BTN_vs_LJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','K5s','Q9s','Q8s','J9s','J8s','T9s','T8s','98s','97s','87s','86s','76s'],
    call: ['99','88','77','66','55','44','33','AJs','ATs','A9s','A8s','AQo','AJo','ATo','KQs','KJs','KTs','KQo','KJo','QJs','QTs','QJo','JTs','J9o']
  },
  'BTN_vs_HJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','K5s','Q9s','Q8s','Q7s','J9s','J8s','T9s','T8s','98s','97s','87s','86s','76s','75s','65s'],
    call: ['99','88','77','66','55','44','33','AJs','ATs','A9s','A8s','A7s','AQo','AJo','ATo','KQs','KJs','KTs','KQo','KJo','QJs','QTs','QJo','JTs','J9o','T9o']
  },
  'BTN_vs_CO': {
    threebet_value: ['AA','AKs','AQs','AJs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','K5s','Q9s','Q8s','J9s','J8s','T9s','T8s','98s','97s','87s','86s','76s','75s','65s','64s','54s','53s'],
    call: ['99','88','77','66','55','44','ATs','A9s','A8s','A7s','A6s','A5o','AQo','AJo','ATo','KQs','KJs','KTs','KQo','KJo','QJs','QTs','QJo','JTs','J9o']
  },

  // Cutoff scenarios (Page 5)
  'CO_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s'],
    call: ['TT','99','88','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','KQo','QJs','QTs','JTs','T9s']
  },
  'CO_vs_UTG+1': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s'],
    call: ['TT','99','88','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','KQo','QJs','QTs','JTs','T9s']
  },
  'CO_vs_UTG+2': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K5s'],
    call: ['TT','99','88','77','AQs','AJs','ATs','A9s','AQo','AJo','KQs','KJs','KTs','K9s','KQo','QJs','QTs','Q9s','JTs','J9s','T9s','98s']
  },
  'CO_vs_LJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','Q9s','Q8s'],
    call: ['99','88','77','66','AJs','ATs','A9s','AQo','AJo','ATo','KQs','KJs','KTs','KQo','KJo','QJs','QTs','QJo','JTs','J9s','T9s','98s','87s']
  },
  'CO_vs_HJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','K6s','Q9s','Q8s','J9s','T9s','98s'],
    call: ['99','88','77','66','55','AJs','ATs','A9s','AQo','AJo','ATo','KQs','KJs','KTs','KQo','KJo','QJs','QTs','QJo','JTs','T9o','87s']
  },

  // Hijack scenarios (Page 4)
  'HJ_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s'],
    call: ['99','88','77','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','QJs','QTs','JTs']
  },
  'HJ_vs_UTG+1': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s'],
    call: ['99','88','77','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','QJs','QTs','JTs']
  },
  'HJ_vs_UTG+2': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','K5s'],
    call: ['99','88','77','66','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','K9s','KQo','QJs','QTs','Q9s','JTs','J9s','T9s']
  },
  'HJ_vs_LJ': {
    threebet_value: ['AA','AKs','AQs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s','A2s','K9s','K8s','K7s','Q9s','Q8s','J9s','T9s','T8s','98s','97s','87s','86s','76s','65s','66','55'],
    call: ['99','88','77','AJs','ATs','AQo','AJo','KQs','KJs','KTs','QJs','QTs','JTs']
  },

  // Lojack scenarios (Page 4)
  'LJ_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s'],
    call: ['99','88','77','AQs','AJs','ATs','AQo','AJo','KQs','KJs','QJs','QTs','JTs']
  },
  'LJ_vs_UTG+1': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s'],
    call: ['99','88','77','AQs','AJs','ATs','AQo','AJo','KQs','KJs','QJs','QTs','JTs']
  },
  'LJ_vs_UTG+2': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ','TT'],
    threebet_bluff: ['A5s','A4s','A3s'],
    call: ['99','88','77','66','AQs','AJs','ATs','AQo','AJo','KQs','KJs','KTs','QJs','QTs','Q9s','JTs','J9s']
  },

  // UTG+2 scenarios (Page 4)
  'UTG+2_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s'],
    call: ['TT','99','AQs','AJs','ATs','AQo','KQs','KJs','QJs','JTs']
  },
  'UTG+2_vs_UTG+1': {
    threebet_value: ['AA','AKs','AKo','KK','QQ','JJ'],
    threebet_bluff: ['A5s','A4s'],
    call: ['TT','99','AQs','AJs','ATs','AQo','KQs','KJs','QJs','JTs']
  },

  // UTG+1 scenarios (Page 4)
  'UTG+1_vs_UTG': {
    threebet_value: ['AA','AKs','AKo','KK','QQ'],
    threebet_bluff: ['A5s','A4s'],
    call: ['JJ','TT','AQs','AJs','AKo','KQs','KJs','QJs','JTs']
  }
};

// Legend configurations
const legendConfigs = {
  rfi: [
    { color: '#dc3545', text: 'Raise' },
    { color: '#28a745', text: 'Limp' },
    { color: '#e9ecef', text: 'Fold', textColor: '#6c757d' }
  ],
  facing: [
    { color: '#c82333', text: '3-bet Value' },
    { color: '#0069d9', text: '3-bet Bluff' },
    { color: '#20c997', text: 'Call' },
    { color: '#e9ecef', text: 'Fold', textColor: '#6c757d' }
  ]
};

// Initialize
function initializeMatrix() {
  const matrix = document.getElementById('hand-matrix');
  matrix.innerHTML = '';
  hands.forEach(row => {
    row.forEach(hand => {
      const cell = document.createElement('div');
      cell.className = 'hand-cell fold';
      cell.textContent = hand;
      cell.dataset.hand = hand;
      matrix.appendChild(cell);
    });
  });
}

// Update legend
function updateLegend(isFacing) {
  const legend = document.getElementById('legend');
  const config = isFacing ? legendConfigs.facing : legendConfigs.rfi;

  legend.innerHTML = config.map(item => `
    <div class="legend-item">
      <div class="legend-color" style="background: ${item.color}"></div>
      <span class="legend-text" style="${item.textColor ? 'color: ' + item.textColor : ''}">${item.text}</span>
    </div>
  `).join('');
}

// Update RFI matrix
function updateRFIMatrix(position) {
  const range = rfiRanges[position];
  const cells = document.querySelectorAll('.hand-cell');

  cells.forEach(cell => {
    const hand = cell.dataset.hand;
    cell.className = 'hand-cell fold';

    if (position === 'SB') {
      if (range.raiseValue && range.raiseValue.includes(hand)) {
        cell.className = 'hand-cell raise-value';
      } else if (range.raiseBluff && range.raiseBluff.includes(hand)) {
        cell.className = 'hand-cell raise-bluff';
      } else if (range.limp && range.limp.includes(hand)) {
        cell.className = 'hand-cell limp';
      }
    } else {
      if (range.raise && range.raise.includes(hand)) {
        cell.className = 'hand-cell raise';
      }
    }
  });
}

// Update Facing RFI matrix
function updateFacingMatrix(hero, villain) {
  const key = `${hero}_vs_${villain}`;
  const range = facingRFI[key];

  if (!range) {
    initializeMatrix();
    return;
  }

  const cells = document.querySelectorAll('.hand-cell');

  cells.forEach(cell => {
    const hand = cell.dataset.hand;
    cell.className = 'hand-cell fold';

    if (range.threebet_value && range.threebet_value.includes(hand)) {
      cell.className = 'hand-cell threebet-value';
    } else if (range.threebet_bluff && range.threebet_bluff.includes(hand)) {
      cell.className = 'hand-cell threebet-bluff';
    } else if (range.call && range.call.includes(hand)) {
      cell.className = 'hand-cell call';
    }
  });
}

// Update villain buttons
function updateVillainButtons() {
  const heroPos = allPositions[heroIndex];
  const container = document.getElementById('villain-buttons');
  container.innerHTML = '';

  // Always add "None" button
  const noneBtn = document.createElement('button');
  noneBtn.className = 'villain-btn none' + (selectedVillain === null ? ' active' : '');
  noneBtn.textContent = 'None';
  noneBtn.addEventListener('click', () => {
    selectedVillain = null;
    updateDisplay();
  });
  container.appendChild(noneBtn);

  // Add buttons for positions that can raise before hero
  // BB (index 0) can face all positions (1 to length-1)
  // Other positions can face UTG (index 1) to their previous position
  const endIndex = (heroIndex === 0) ? allPositions.length : heroIndex;
  for (let i = 1; i < endIndex; i++) {
    const pos = allPositions[i];
    const btn = document.createElement('button');
    btn.className = 'villain-btn' + (selectedVillain === pos ? ' active' : '');
    btn.textContent = pos;
    btn.dataset.position = pos;
    btn.addEventListener('click', () => {
      selectedVillain = pos;
      updateDisplay();
    });
    container.appendChild(btn);
  }
}

// Update display
function updateDisplay() {
  const heroPos = allPositions[heroIndex];

  // Update position display
  document.getElementById('hero-position').textContent = heroPos;

  // Update villain buttons
  updateVillainButtons();

  // Update legend
  const isFacing = selectedVillain !== null;
  updateLegend(isFacing);

  // Update matrix
  if (isFacing) {
    updateFacingMatrix(heroPos, selectedVillain);
  } else {
    updateRFIMatrix(heroPos);
  }

  // Navigation buttons are always enabled (circular navigation)
  document.getElementById('hero-prev').disabled = false;
  document.getElementById('hero-next').disabled = false;
}

// Navigation handlers
document.addEventListener('DOMContentLoaded', function() {
  initializeMatrix();
  updateDisplay();

  // Hero navigation (circular with modulo)
  document.getElementById('hero-prev').addEventListener('click', () => {
    heroIndex = (heroIndex - 1 + allPositions.length) % allPositions.length;
    // Reset villain if no longer valid for new hero position
    if (selectedVillain !== null) {
      const villainIndex = allPositions.indexOf(selectedVillain);
      // Invalid if: hero is UTG (index 1), villain is BB (index 0), or villain position >= hero position
      if (heroIndex === 1 || villainIndex === 0 || villainIndex >= heroIndex) {
        selectedVillain = null;
      }
    }
    updateDisplay();
  });

  document.getElementById('hero-next').addEventListener('click', () => {
    heroIndex = (heroIndex + 1) % allPositions.length;
    // Reset villain if no longer valid for new hero position
    if (selectedVillain !== null) {
      const villainIndex = allPositions.indexOf(selectedVillain);
      // Invalid if: hero is UTG (index 1), villain is BB (index 0), or villain position >= hero position
      if (heroIndex === 1 || villainIndex === 0 || villainIndex >= heroIndex) {
        selectedVillain = null;
      }
    }
    updateDisplay();
  });

  // Swipe support for hero position
  let touchStartX = 0;
  let touchEndX = 0;

  const heroNav = document.querySelector('.hero-nav');

  heroNav.addEventListener('touchstart', (e) => {
    touchStartX = e.changedTouches[0].screenX;
  });

  heroNav.addEventListener('touchend', (e) => {
    touchEndX = e.changedTouches[0].screenX;
    const swipeThreshold = 50;
    const diff = touchStartX - touchEndX;

    if (Math.abs(diff) > swipeThreshold) {
      if (diff > 0) {
        // Swipe left - next position
        heroIndex = (heroIndex + 1) % allPositions.length;
        // Reset villain if no longer valid for new hero position
        if (selectedVillain !== null) {
          const villainIndex = allPositions.indexOf(selectedVillain);
          if (heroIndex === 1 || villainIndex === 0 || villainIndex >= heroIndex) {
            selectedVillain = null;
          }
        }
        updateDisplay();
      } else if (diff < 0) {
        // Swipe right - previous position
        heroIndex = (heroIndex - 1 + allPositions.length) % allPositions.length;
        // Reset villain if no longer valid for new hero position
        if (selectedVillain !== null) {
          const villainIndex = allPositions.indexOf(selectedVillain);
          if (heroIndex === 1 || villainIndex === 0 || villainIndex >= heroIndex) {
            selectedVillain = null;
          }
        }
        updateDisplay();
      }
    }
  });

  // Keyboard navigation
  document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowLeft') {
      document.getElementById('hero-prev').click();
    } else if (e.key === 'ArrowRight') {
      document.getElementById('hero-next').click();
    }
  });
});
</script>

<div style="margin-top: 40px; padding: 20px; background: #f8f9fa; border-radius: 8px;">
  <h3>How to Use</h3>
  <ul>
    <li><strong>Navigate your position:</strong> Use ◀ ▶ arrows or swipe left/right on mobile</li>
    <li><strong>RFI Mode:</strong> Click "None" for villain to see raise-first-in strategy</li>
    <li><strong>Defense Mode:</strong> Click any villain button to see your 3-bet and calling ranges</li>
    <li><strong>Keyboard:</strong> Use arrow keys to navigate position on desktop</li>
  </ul>
  <p><small>
    Based on professional preflop charts for 100BB stacks. These are default ranges - adjust based on opponents and game dynamics.
  </small></p>
</div>
