<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chess Ladder - Learn Chess From First Move to Strategy</title>
  <style>
    :root {
      --bg: #201d1a;
      --panel: #2f2b27;
      --panel-2: #3b3630;
      --text: #f7f1e6;
      --muted: #cfc3b2;
      --soft: #f0d9b5;
      --board-light: #f0d9b5;
      --board-dark: #b58863;
      --green: #7fa650;
      --green-dark: #5f7f3a;
      --gold: #e7b65d;
      --blue: #6fa8dc;
      --danger: #d86f62;
      --line: rgba(255, 255, 255, 0.13);
      --shadow: 0 22px 60px rgba(0, 0, 0, 0.32);
      --radius: 8px;
      --max: 1180px;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      line-height: 1.55;
    }

    body::selection {
      background: var(--gold);
      color: #211a12;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    img,
    iframe {
      max-width: 100%;
    }

    .site-header {
      position: sticky;
      top: 0;
      z-index: 20;
      border-bottom: 1px solid var(--line);
      background: rgba(32, 29, 26, 0.93);
      backdrop-filter: blur(14px);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
      min-height: 68px;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-weight: 800;
      letter-spacing: 0;
      white-space: nowrap;
    }

    .brand-mark {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      border: 2px solid var(--board-light);
      background:
        linear-gradient(45deg, var(--board-dark) 25%, transparent 25% 75%, var(--board-dark) 75%),
        linear-gradient(45deg, var(--board-dark) 25%, transparent 25% 75%, var(--board-dark) 75%);
      background-color: var(--board-light);
      background-position: 0 0, 9px 9px;
      background-size: 18px 18px;
      border-radius: var(--radius);
      color: #211a12;
      font-size: 1.2rem;
      line-height: 1;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 6px;
      flex-wrap: wrap;
      justify-content: flex-end;
    }

    .nav-links a {
      padding: 8px 10px;
      border-radius: 6px;
      color: var(--muted);
      font-size: 0.93rem;
      transition: background 160ms ease, color 160ms ease;
    }

    .nav-links a:hover,
    .nav-links a:focus-visible {
      color: var(--text);
      background: rgba(255, 255, 255, 0.08);
      outline: none;
    }

    .hero {
      position: relative;
      display: grid;
      align-items: center;
      overflow: hidden;
      min-height: clamp(540px, 78svh, 780px);
      border-bottom: 1px solid var(--line);
      isolation: isolate;
    }

    .hero::before {
      content: "";
      position: absolute;
      inset: 0;
      background:
        linear-gradient(90deg, rgba(32, 29, 26, 0.92) 0%, rgba(32, 29, 26, 0.78) 42%, rgba(32, 29, 26, 0.44) 100%),
        radial-gradient(circle at 68% 30%, rgba(231, 182, 93, 0.14), transparent 34%);
      z-index: -1;
      pointer-events: none;
    }

    .hero-board {
      position: absolute;
      right: max(-80px, calc((100vw - var(--max)) / 2 - 90px));
      top: 50%;
      width: min(680px, 64vw);
      aspect-ratio: 1;
      transform: translateY(-48%) rotate(2deg);
      box-shadow: var(--shadow);
      border: 10px solid #181512;
      background: #181512;
      z-index: -2;
    }

    .hero-board-grid,
    .puzzle-board {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      grid-template-rows: repeat(8, 1fr);
    }

    .hero-square,
    .puzzle-square {
      display: grid;
      place-items: center;
      aspect-ratio: 1;
      font-family: Georgia, "Times New Roman", serif;
      font-size: clamp(1.8rem, 5vw, 4.6rem);
      text-shadow: 0 2px 5px rgba(0, 0, 0, 0.38);
      user-select: none;
    }

    .light {
      background: var(--board-light);
      color: #f7f1e6;
    }

    .dark {
      background: var(--board-dark);
      color: #211a12;
    }

    .hero-inner {
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
      padding: 72px 0 58px;
    }

    .hero-copy {
      max-width: 650px;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      margin: 0 0 16px;
      color: var(--gold);
      font-size: 0.82rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .eyebrow::before {
      content: "";
      width: 24px;
      height: 2px;
      background: currentColor;
    }

    h1,
    h2,
    h3,
    p {
      margin-top: 0;
    }

    h1 {
      max-width: 11ch;
      margin-bottom: 18px;
      font-size: clamp(3.2rem, 9vw, 7.2rem);
      line-height: 0.91;
      letter-spacing: 0;
    }

    .hero-copy > p {
      max-width: 58ch;
      color: var(--muted);
      font-size: clamp(1rem, 2vw, 1.25rem);
    }

    .hero-actions {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      margin-top: 30px;
    }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 44px;
      padding: 0 18px;
      border: 1px solid transparent;
      border-radius: 7px;
      background: var(--green);
      color: #10150d;
      font-weight: 800;
      cursor: pointer;
      transition: transform 160ms ease, background 160ms ease, border-color 160ms ease, color 160ms ease;
    }

    .button:hover,
    .button:focus-visible {
      transform: translateY(-1px);
      background: #95ba60;
      outline: none;
    }

    .button.secondary {
      border-color: var(--line);
      background: rgba(255, 255, 255, 0.08);
      color: var(--text);
    }

    .button.secondary:hover,
    .button.secondary:focus-visible {
      background: rgba(255, 255, 255, 0.13);
    }

    .hero-metrics {
      display: grid;
      grid-template-columns: repeat(3, minmax(110px, 1fr));
      gap: 12px;
      max-width: 560px;
      margin-top: 44px;
    }

    .metric {
      min-height: 88px;
      padding: 16px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(47, 43, 39, 0.76);
    }

    .metric strong {
      display: block;
      color: var(--soft);
      font-size: 1.55rem;
      line-height: 1;
    }

    .metric span {
      display: block;
      margin-top: 8px;
      color: var(--muted);
      font-size: 0.9rem;
    }

    section {
      padding: 76px 0;
    }

    .section-dark {
      background: #26221f;
    }

    .section-warm {
      background: #f4eadc;
      color: #211a12;
    }

    .section-warm .section-kicker,
    .section-warm .section-intro,
    .section-warm .muted {
      color: #5d5144;
    }

    .section-warm .lesson-card,
    .section-warm .rule-item,
    .section-warm .opening-card,
    .section-warm .notation-card,
    .section-warm .video-card,
    .section-warm .puzzle-shell {
      border-color: rgba(33, 26, 18, 0.16);
      background: #fff8eb;
      color: #211a12;
      box-shadow: 0 18px 40px rgba(82, 55, 25, 0.12);
    }

    .wrap {
      width: min(100% - 32px, var(--max));
      margin: 0 auto;
    }

    .section-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 28px;
      margin-bottom: 28px;
    }

    .section-kicker {
      margin: 0 0 8px;
      color: var(--gold);
      font-size: 0.8rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    h2 {
      margin-bottom: 0;
      font-size: clamp(2rem, 4.2vw, 3.4rem);
      line-height: 1;
      letter-spacing: 0;
    }

    .section-intro {
      max-width: 54ch;
      margin-bottom: 0;
      color: var(--muted);
    }

    .path-tabs {
      display: inline-grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 4px;
      padding: 4px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: rgba(0, 0, 0, 0.18);
    }

    .tab-button {
      min-height: 38px;
      padding: 0 14px;
      border: 0;
      border-radius: 6px;
      background: transparent;
      color: var(--muted);
      font: inherit;
      font-size: 0.92rem;
      font-weight: 800;
      cursor: pointer;
      white-space: nowrap;
    }

    .tab-button[aria-selected="true"] {
      background: var(--green);
      color: #11170e;
    }

    .lesson-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 16px;
    }

    .lesson-card,
    .rule-item,
    .opening-card,
    .notation-card,
    .video-card,
    .puzzle-shell {
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--panel);
      box-shadow: 0 16px 35px rgba(0, 0, 0, 0.16);
    }

    .lesson-card {
      min-height: 270px;
      padding: 20px;
    }

    .lesson-number {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      margin-bottom: 20px;
      border-radius: 50%;
      background: var(--green);
      color: #10150d;
      font-weight: 900;
    }

    .lesson-card h3,
    .video-card h3,
    .puzzle-info h3 {
      margin-bottom: 10px;
      font-size: 1.18rem;
      line-height: 1.2;
    }

    .lesson-card p,
    .rule-item p,
    .video-card p,
    .puzzle-info p {
      color: var(--muted);
    }

    .section-warm .lesson-card p,
    .section-warm .rule-item p,
    .section-warm .opening-card p,
    .section-warm .notation-card p,
    .section-warm .video-card p,
    .section-warm .puzzle-info p {
      color: #5d5144;
    }

    .topic-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 18px 0 0;
      padding: 0;
      list-style: none;
    }

    .topic-list li {
      padding: 5px 9px;
      border: 1px solid var(--line);
      border-radius: 999px;
      color: var(--muted);
      font-size: 0.82rem;
    }

    .section-warm .topic-list li {
      border-color: rgba(33, 26, 18, 0.16);
      color: #5d5144;
      background: rgba(181, 136, 99, 0.12);
    }

    .rules-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px;
    }

    .rule-item {
      min-height: 180px;
      padding: 18px;
    }

    .rule-item strong {
      display: block;
      margin-bottom: 9px;
      font-size: 1.05rem;
    }

    .rule-item p {
      margin-bottom: 0;
      font-size: 0.95rem;
    }

    .opening-grid,
    .notation-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
    }

    .opening-card,
    .notation-card {
      overflow: hidden;
    }

    .opening-body,
    .notation-card {
      padding: 20px;
    }

    .opening-body h3,
    .notation-card h3 {
      margin-bottom: 8px;
      font-size: 1.18rem;
      line-height: 1.2;
    }

    .opening-line {
      display: inline-flex;
      margin-bottom: 12px;
      padding: 6px 9px;
      border-radius: 6px;
      background: rgba(127, 166, 80, 0.14);
      color: var(--green-dark);
      font-size: 0.88rem;
      font-weight: 900;
    }

    .mini-board {
      display: grid;
      grid-template-columns: repeat(8, 1fr);
      grid-template-rows: repeat(8, 1fr);
      width: 100%;
      aspect-ratio: 1;
      border-bottom: 1px solid rgba(33, 26, 18, 0.16);
      background: #211a12;
    }

    .mini-square {
      display: grid;
      place-items: center;
      aspect-ratio: 1;
      font-family: Georgia, "Times New Roman", serif;
      font-size: clamp(1rem, 3vw, 2rem);
      line-height: 1;
      user-select: none;
    }

    .notation-grid {
      grid-template-columns: 1.1fr 0.9fr 1fr;
    }

    .notation-list {
      display: grid;
      gap: 10px;
      margin: 16px 0 0;
      padding: 0;
      list-style: none;
    }

    .notation-list li {
      display: grid;
      grid-template-columns: 82px 1fr;
      gap: 12px;
      align-items: start;
      color: var(--muted);
    }

    .notation-list code {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 30px;
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.08);
      color: var(--soft);
      font-family: ui-monospace, SFMono-Regular, Consolas, "Liberation Mono", monospace;
      font-weight: 900;
    }

    .notation-card.callout {
      background:
        linear-gradient(135deg, rgba(127, 166, 80, 0.22), rgba(231, 182, 93, 0.14)),
        var(--panel);
    }

    .video-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
    }

    .video-tier {
      margin-top: 26px;
    }

    .video-tier:first-of-type {
      margin-top: 0;
    }

    .video-tier-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 18px;
      margin-bottom: 14px;
    }

    .video-tier-head h3 {
      margin-bottom: 0;
      font-size: 1.35rem;
      line-height: 1.15;
    }

    .video-tier-head p {
      max-width: 58ch;
      margin-bottom: 0;
      color: var(--muted);
      font-size: 0.95rem;
    }

    .video-grid.tier-grid {
      grid-template-columns: repeat(5, minmax(0, 1fr));
    }

    .video-card {
      overflow: hidden;
    }

    .video-frame {
      position: relative;
      aspect-ratio: 16 / 9;
      background: #111;
    }

    .video-frame iframe {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }

    .video-body {
      padding: 18px;
    }

    .video-body .badge {
      margin-bottom: 11px;
    }

    .video-body p {
      margin-bottom: 0;
      font-size: 0.95rem;
    }

    .puzzle-shell {
      display: grid;
      grid-template-columns: minmax(300px, 520px) 1fr;
      gap: 28px;
      padding: 22px;
      align-items: stretch;
    }

    .puzzle-board-wrap {
      position: relative;
      align-self: start;
      border: 8px solid #211a12;
      border-radius: var(--radius);
      background: #211a12;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.26);
      overflow: hidden;
    }

    .puzzle-board {
      width: 100%;
      aspect-ratio: 1;
    }

    .puzzle-square {
      position: relative;
      font-size: clamp(1.4rem, 5vw, 3.55rem);
    }

    .puzzle-square.target::after {
      content: "";
      position: absolute;
      width: 34%;
      height: 34%;
      border: 3px solid rgba(127, 166, 80, 0.8);
      border-radius: 50%;
      pointer-events: none;
    }

    .coordinates {
      position: absolute;
      inset: 0;
      pointer-events: none;
      font-size: 0.72rem;
      font-weight: 800;
      color: rgba(33, 26, 18, 0.72);
    }

    .coordinates span {
      position: absolute;
    }

    .puzzle-info {
      display: flex;
      flex-direction: column;
      min-width: 0;
    }

    .puzzle-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 16px;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      min-height: 28px;
      padding: 0 9px;
      border-radius: 999px;
      background: rgba(127, 166, 80, 0.16);
      color: var(--green-dark);
      font-size: 0.82rem;
      font-weight: 900;
    }

    .puzzle-stats {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 10px;
      margin-bottom: 14px;
    }

    .stat-pill {
      min-height: 66px;
      padding: 10px 12px;
      border: 1px solid rgba(33, 26, 18, 0.14);
      border-radius: var(--radius);
      background: #f7efe2;
    }

    .stat-pill strong,
    .stat-pill span {
      display: block;
    }

    .stat-pill strong {
      color: #211a12;
      font-size: 1.08rem;
      line-height: 1.1;
    }

    .stat-pill span {
      margin-top: 5px;
      color: #5d5144;
      font-size: 0.82rem;
      font-weight: 800;
    }

    .progress-track {
      height: 9px;
      margin-bottom: 18px;
      overflow: hidden;
      border-radius: 999px;
      background: rgba(33, 26, 18, 0.12);
    }

    .progress-fill {
      display: block;
      width: 0;
      height: 100%;
      border-radius: inherit;
      background: var(--green);
      transition: width 180ms ease;
    }

    .puzzle-hint {
      min-height: 48px;
      margin: 0;
      padding: 11px 13px;
      border: 1px solid rgba(127, 166, 80, 0.28);
      border-radius: var(--radius);
      background: rgba(127, 166, 80, 0.12);
      color: #2c261f;
    }

    .answers {
      display: grid;
      gap: 10px;
      margin: 18px 0;
    }

    .answer-button {
      width: 100%;
      min-height: 48px;
      padding: 12px 14px;
      border: 1px solid rgba(33, 26, 18, 0.18);
      border-radius: 7px;
      background: #f7efe2;
      color: #211a12;
      font: inherit;
      font-weight: 800;
      text-align: left;
      cursor: pointer;
      transition: border-color 160ms ease, background 160ms ease, transform 160ms ease;
    }

    .answer-button:hover,
    .answer-button:focus-visible {
      transform: translateX(2px);
      border-color: var(--green);
      outline: none;
    }

    .answer-button:disabled {
      cursor: default;
      transform: none;
      opacity: 0.86;
    }

    .answer-button.correct {
      border-color: var(--green);
      background: #dfeecf;
    }

    .answer-button.wrong {
      border-color: var(--danger);
      background: #f8ded9;
    }

    .feedback {
      min-height: 64px;
      margin: 0 0 18px;
      padding: 12px 14px;
      border-left: 4px solid var(--green);
      background: rgba(127, 166, 80, 0.12);
      color: #2c261f;
    }

    .puzzle-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: auto;
    }

    .study-plan {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 18px;
      align-items: start;
    }

    .plan-panel {
      padding: 24px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--panel);
    }

    .plan-panel h3 {
      margin-bottom: 12px;
      font-size: 1.25rem;
    }

    .plan-list {
      display: grid;
      gap: 12px;
      margin: 0;
      padding: 0;
      list-style: none;
      color: var(--muted);
    }

    .plan-list li {
      display: grid;
      grid-template-columns: 42px 1fr;
      gap: 12px;
      align-items: start;
    }

    .plan-list span {
      display: grid;
      place-items: center;
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background: rgba(231, 182, 93, 0.16);
      color: var(--gold);
      font-weight: 900;
    }

    .footer {
      padding: 34px 0;
      border-top: 1px solid var(--line);
      color: var(--muted);
      background: #181512;
    }

    .footer .wrap {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      flex-wrap: wrap;
    }

    .hidden {
      display: none;
    }

    @media (max-width: 980px) {
      .hero-board {
        right: -230px;
        width: min(720px, 94vw);
        opacity: 0.72;
      }

      .lesson-grid,
      .rules-grid,
      .opening-grid,
      .notation-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .video-grid,
      .video-grid.tier-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .puzzle-shell,
      .study-plan {
        grid-template-columns: 1fr;
      }

      .puzzle-board-wrap {
        max-width: 540px;
        margin: 0 auto;
        width: 100%;
      }
    }

    @media (max-width: 760px) {
      .nav {
        align-items: flex-start;
        flex-direction: column;
        padding: 13px 0;
      }

      .nav-links {
        width: 100%;
        justify-content: flex-start;
        overflow-x: auto;
        flex-wrap: nowrap;
        padding-bottom: 3px;
      }

      .hero {
        min-height: auto;
      }

      .hero-inner {
        padding: 56px 0 44px;
      }

      .hero-board {
        right: -270px;
        top: 48%;
        width: 760px;
      }

      h1 {
        max-width: 8ch;
      }

      .hero-metrics,
      .section-head {
        grid-template-columns: 1fr;
      }

      .hero-metrics {
        display: grid;
      }

      .section-head {
        display: grid;
        align-items: start;
      }

      .video-tier-head {
        display: grid;
        align-items: start;
      }

      .path-tabs {
        width: 100%;
      }

      section {
        padding: 56px 0;
      }
    }

    @media (max-width: 580px) {
      .lesson-grid,
      .rules-grid,
      .opening-grid,
      .notation-grid,
      .video-grid,
      .video-grid.tier-grid,
      .puzzle-shell,
      .study-plan,
      .puzzle-stats {
        grid-template-columns: 1fr;
      }

      .hero-metrics {
        grid-template-columns: 1fr;
      }

      .hero-actions {
        align-items: stretch;
      }

      .button {
        width: 100%;
      }

      .puzzle-shell {
        padding: 14px;
      }

      .puzzle-board-wrap {
        border-width: 5px;
      }

      .tab-button {
        padding: 0 8px;
        font-size: 0.86rem;
      }
    }
  </style>
</head>
<body>
  <header class="site-header">
    <nav class="nav" aria-label="Main navigation">
      <a class="brand" href="#top" aria-label="Chess Ladder home">
        <span class="brand-mark" aria-hidden="true">♟</span>
        <span>Chess Ladder</span>
      </a>
      <div class="nav-links">
        <a href="#paths">Lessons</a>
        <a href="#rules">Rules</a>
        <a href="#openings">Openings</a>
        <a href="#videos">Videos</a>
        <a href="#notation">Notation</a>
        <a href="#puzzles">Puzzles</a>
        <a href="#plan">Study Plan</a>
      </div>
    </nav>
  </header>

  <main id="top">
    <section class="hero" aria-labelledby="hero-title">
      <div class="hero-board" aria-hidden="true">
        <div class="hero-board-grid" id="heroBoard"></div>
      </div>
      <div class="hero-inner">
        <div class="hero-copy">
          <p class="eyebrow">Lichess-inspired chess tutorial</p>
          <h1 id="hero-title">Chess Ladder</h1>
          <p>Move from legal moves to confident plans with a clean learning path, focused rules, hand-picked videos, and tactical puzzles you can solve right on the board.</p>
          <div class="hero-actions">
            <a class="button" href="#paths">Start Learning</a>
            <a class="button secondary" href="#puzzles">Try a Puzzle</a>
          </div>
          <div class="hero-metrics" aria-label="Course summary">
            <div class="metric">
              <strong>3</strong>
              <span>skill levels</span>
            </div>
            <div class="metric">
              <strong>8</strong>
              <span>core rules</span>
            </div>
            <div class="metric">
              <strong>6</strong>
              <span>board puzzles</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="paths" class="section-dark" aria-labelledby="paths-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Learning paths</p>
            <h2 id="paths-title">Choose your level</h2>
          </div>
          <p class="section-intro">Each path builds one practical layer at a time: first the board, then tactics, then strategic decisions that hold up in real games.</p>
        </div>

        <div class="path-tabs" role="tablist" aria-label="Lesson levels">
          <button class="tab-button" type="button" role="tab" aria-selected="true" aria-controls="beginner" id="tab-beginner" data-level="beginner">Beginner</button>
          <button class="tab-button" type="button" role="tab" aria-selected="false" aria-controls="intermediate" id="tab-intermediate" data-level="intermediate">Intermediate</button>
          <button class="tab-button" type="button" role="tab" aria-selected="false" aria-controls="advanced" id="tab-advanced" data-level="advanced">Advanced</button>
        </div>

        <div class="lesson-grid" id="beginner" role="tabpanel" aria-labelledby="tab-beginner">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Board and Setup</h3>
            <p>Place the light square on your right, line up pieces in the usual back-rank order, and remember that queens start on their own color.</p>
            <ul class="topic-list">
              <li>Coordinates</li>
              <li>Starting position</li>
              <li>Piece values</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>How Pieces Move</h3>
            <p>Learn the movement patterns, captures, and special limits that keep bishops diagonal, rooks straight, knights jumping, and kings cautious.</p>
            <ul class="topic-list">
              <li>Movement</li>
              <li>Captures</li>
              <li>King safety</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Check and Mate</h3>
            <p>Spot checks, escape checks legally, and recognize when the enemy king has no safe square, capture, or block left.</p>
            <ul class="topic-list">
              <li>Check</li>
              <li>Checkmate</li>
              <li>Stalemate</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>First Opening Habits</h3>
            <p>Control the center, develop minor pieces, castle early, and avoid moving the same piece repeatedly without a concrete reason.</p>
            <ul class="topic-list">
              <li>Center</li>
              <li>Development</li>
              <li>Castling</li>
            </ul>
          </article>
        </div>

        <div class="lesson-grid hidden" id="intermediate" role="tabpanel" aria-labelledby="tab-intermediate">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Tactical Patterns</h3>
            <p>Train forks, pins, skewers, discoveries, and back-rank ideas until the patterns start appearing before you calculate.</p>
            <ul class="topic-list">
              <li>Forks</li>
              <li>Pins</li>
              <li>Skewers</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>Calculation</h3>
            <p>List forcing moves first: checks, captures, and threats. Then compare candidate lines before touching a piece.</p>
            <ul class="topic-list">
              <li>Candidate moves</li>
              <li>Forcing lines</li>
              <li>Blunder checks</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Pawn Structure</h3>
            <p>Use pawn chains, open files, isolated pawns, and outposts to decide where your pieces belong after the opening.</p>
            <ul class="topic-list">
              <li>Outposts</li>
              <li>Open files</li>
              <li>Weak squares</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>Practical Endgames</h3>
            <p>Convert extra material by activating the king, cutting off counterplay, and knowing the basic rook and pawn endings.</p>
            <ul class="topic-list">
              <li>King activity</li>
              <li>Rook endings</li>
              <li>Passed pawns</li>
            </ul>
          </article>
        </div>

        <div class="lesson-grid hidden" id="advanced" role="tabpanel" aria-labelledby="tab-advanced">
          <article class="lesson-card">
            <span class="lesson-number">1</span>
            <h3>Positional Imbalances</h3>
            <p>Compare bishops vs. knights, space, pawn weaknesses, king exposure, and initiative before choosing a plan.</p>
            <ul class="topic-list">
              <li>Space</li>
              <li>Initiative</li>
              <li>Piece quality</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">2</span>
            <h3>Opening Repertoires</h3>
            <p>Build compact opening files around structures and middlegame plans, not just memorized move orders.</p>
            <ul class="topic-list">
              <li>Repertoires</li>
              <li>Transpositions</li>
              <li>Model games</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">3</span>
            <h3>Endgame Technique</h3>
            <p>Refine opposition, triangulation, rook activity, queen checks, and conversion methods for small advantages.</p>
            <ul class="topic-list">
              <li>Opposition</li>
              <li>Triangulation</li>
              <li>Conversion</li>
            </ul>
          </article>
          <article class="lesson-card">
            <span class="lesson-number">4</span>
            <h3>Game Review</h3>
            <p>Annotate without an engine first, mark turning points, then use analysis to test your reasoning against the position.</p>
            <ul class="topic-list">
              <li>Annotations</li>
              <li>Critical moments</li>
              <li>Engine review</li>
            </ul>
          </article>
        </div>
      </div>
    </section>

    <section id="rules" class="section-warm" aria-labelledby="rules-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Rules</p>
            <h2 id="rules-title">The essentials</h2>
          </div>
          <p class="section-intro">These rules cover the situations that decide most beginner games and prevent the classic illegal-move confusion.</p>
        </div>

        <div class="rules-grid">
          <article class="rule-item">
            <strong>Objective</strong>
            <p>Checkmate the opposing king. A king is checkmated when it is attacked and has no legal way to escape.</p>
          </article>
          <article class="rule-item">
            <strong>Turns</strong>
            <p>White moves first. Players alternate one legal move at a time, and a move cannot leave your own king in check.</p>
          </article>
          <article class="rule-item">
            <strong>Piece movement</strong>
            <p>Rooks move straight, bishops diagonal, queens both ways, knights in an L shape, kings one square, and pawns forward.</p>
          </article>
          <article class="rule-item">
            <strong>Captures</strong>
            <p>Most pieces capture the way they move. Pawns move forward but capture one square diagonally forward.</p>
          </article>
          <article class="rule-item">
            <strong>Castling</strong>
            <p>The king and rook move together if neither has moved, the path is clear, and the king does not pass through check.</p>
          </article>
          <article class="rule-item">
            <strong>Promotion</strong>
            <p>A pawn reaching the last rank becomes a queen, rook, bishop, or knight. Most positions call for a queen.</p>
          </article>
          <article class="rule-item">
            <strong>En passant</strong>
            <p>A pawn that advances two squares can sometimes be captured as if it moved one square, but only immediately.</p>
          </article>
          <article class="rule-item">
            <strong>Draws</strong>
            <p>Games can draw by stalemate, agreement, repetition, the fifty-move rule, or insufficient mating material.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="openings" class="section-dark" aria-labelledby="openings-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Opening compass</p>
            <h2 id="openings-title">Start with a plan</h2>
          </div>
          <p class="section-intro">Openings are easier to remember when each one has a job: control the center, develop pieces, and get the king safe.</p>
        </div>

        <div class="opening-grid">
          <article class="opening-card">
            <div class="mini-board" data-fen="r1bqkbnr/pppp1ppp/2n5/4p3/2B1P3/5N2/PPPP1PPP/RNBQK2R" aria-label="Italian Game position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 e5 2. Nf3 Nc6 3. Bc4</span>
              <h3>Italian Game</h3>
              <p>Fast development, pressure on f7, and simple castling plans make this a friendly first opening for White.</p>
              <ul class="topic-list">
                <li>Open center</li>
                <li>Quick castle</li>
                <li>f7 pressure</li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/ppp1pppp/8/3p4/2PP4/8/PP2PPPP/RNBQKBNR" aria-label="Queen's Gambit position"></div>
            <div class="opening-body">
              <span class="opening-line">1. d4 d5 2. c4</span>
              <h3>Queen's Gambit</h3>
              <p>White offers a wing pawn to pull Black away from the center and build a strong pawn duo.</p>
              <ul class="topic-list">
                <li>Central space</li>
                <li>Pawn tension</li>
                <li>Piece harmony</li>
              </ul>
            </div>
          </article>
          <article class="opening-card">
            <div class="mini-board" data-fen="rnbqkbnr/pp1ppppp/8/2p5/4P3/8/PPPP1PPP/RNBQKBNR" aria-label="Sicilian Defense position"></div>
            <div class="opening-body">
              <span class="opening-line">1. e4 c5</span>
              <h3>Sicilian Defense</h3>
              <p>Black fights from the side, creates an unbalanced pawn structure, and plays for active counterplay.</p>
              <ul class="topic-list">
                <li>Counterattack</li>
                <li>Open c-file</li>
                <li>Sharp play</li>
              </ul>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="videos" class="section-dark" aria-labelledby="videos-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Video lessons</p>
            <h2 id="videos-title">Watch the ideas</h2>
          </div>
          <p class="section-intro">A tiered video library with five lessons each for beginner, intermediate, and advanced study.</p>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Beginner videos</h3>
            <p>Start here for rules, piece movement, opening basics, checkmates, and first endgames.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/OCSbzArwB10" title="How To Play Chess: The Ultimate Beginner Guide" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 1</span>
                <h3>Complete beginner guide</h3>
                <p>Learn the board, pieces, legal moves, and the first decisions that matter.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/IU6k-4rKf-g" title="Learn How to Play Chess for Beginners in Less Than 8 Minutes" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 2</span>
                <h3>Piece movement</h3>
                <p>A quick pass through how every chess piece moves and captures.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/8IlJ3v8I4Z8" title="Basic Chess Openings Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 3</span>
                <h3>Opening principles</h3>
                <p>Develop pieces, fight for the center, and castle before chasing attacks.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/I9n8sDRZLZ8" title="Checkmate for chess beginners" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 4</span>
                <h3>Basic checkmates</h3>
                <p>Build the pattern vocabulary for finishing games instead of only winning pieces.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/LPK6_QRJRA0" title="King Opposition: Draw King and Pawn Endgame" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Beginner 5</span>
                <h3>King and pawn basics</h3>
                <p>See why king activity and opposition matter in the simplest endings.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Intermediate videos</h3>
            <p>Move from knowing rules to finding tactics, calculating lines, and building plans.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/MbMslp2WcI0" title="The Chess Tactics Guide For Beginners" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 1</span>
                <h3>Forks, pins, skewers</h3>
                <p>Train the tactical patterns that decide most improving-player games.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/9Ga9dP3bvN8" title="How To Calculate In Chess" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 2</span>
                <h3>Calculation method</h3>
                <p>Learn how to compare candidate moves and check forcing lines clearly.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/yAnNQY2Ac6w" title="Top 5 Pawn Structures You Should Know" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 3</span>
                <h3>Pawn structures</h3>
                <p>Use pawn shapes to understand where pieces belong after the opening.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/kTON84W-b2Q" title="The ONLY Chess Middlegame Guide You Need" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 4</span>
                <h3>Middlegame plans</h3>
                <p>Turn development into real plans: attacks, trades, files, and weak squares.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/zOvaUJdtYTc" title="EASY Rook Checkmate!" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Intermediate 5</span>
                <h3>Rook technique</h3>
                <p>Practice converting a rook advantage with clean king coordination.</p>
              </div>
            </article>
          </div>
        </div>

        <div class="video-tier">
          <div class="video-tier-head">
            <h3>Advanced videos</h3>
            <p>Deepen endgame precision, positional evaluation, prophylaxis, and candidate-move discipline.</p>
          </div>
          <div class="video-grid tier-grid">
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/wsOQBe5yBqk" title="Distant and Rectangular Opposition" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 1</span>
                <h3>Distant opposition</h3>
                <p>Study exact king geometry for pawn endings where one tempo changes everything.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/s8RDioKrLx8" title="The Principle of Positional Imbalances" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 2</span>
                <h3>Positional imbalances</h3>
                <p>Evaluate space, minor pieces, pawn weaknesses, initiative, and king safety.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/N6WmHGKLaa8" title="PROPHYLAXIS in Chess. GM Johan Hellsten explains." allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 3</span>
                <h3>Prophylaxis</h3>
                <p>Learn to ask what your opponent wants before choosing your own plan.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/aMIRnzCeD64" title="Lucena Position Explained" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 4</span>
                <h3>Lucena technique</h3>
                <p>Master bridge-building, one of the most important winning rook endgames.</p>
              </div>
            </article>
            <article class="video-card">
              <div class="video-frame">
                <iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/5rEqhhYYOrQ" title="How to Choose Candidate Moves" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
              </div>
              <div class="video-body">
                <span class="badge">Advanced 5</span>
                <h3>Candidate moves</h3>
                <p>Refine your move-selection process before calculating deep variations.</p>
              </div>
            </article>
          </div>
        </div>
      </div>
    </section>

    <section id="notation" class="section-dark" aria-labelledby="notation-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Notation</p>
            <h2 id="notation-title">Read your games</h2>
          </div>
          <p class="section-intro">Chess notation turns a game into a study file. Learn the few symbols that appear constantly and review becomes much easier.</p>
        </div>

        <div class="notation-grid">
          <article class="notation-card">
            <h3>Common move symbols</h3>
            <p>Algebraic notation starts with the piece, then the destination square. Pawns usually skip the piece letter.</p>
            <ul class="notation-list">
              <li><code>Nf3</code><span>Knight moves to f3.</span></li>
              <li><code>exd5</code><span>The e-pawn captures on d5.</span></li>
              <li><code>O-O</code><span>Kingside castling.</span></li>
              <li><code>Qxf7#</code><span>Queen captures on f7 with checkmate.</span></li>
            </ul>
          </article>
          <article class="notation-card callout">
            <h3>Board coordinates</h3>
            <p>Files run a through h from White's left to right. Ranks run 1 through 8 from White's side to Black's side.</p>
            <ul class="topic-list">
              <li>a1 is dark</li>
              <li>White starts on ranks 1-2</li>
              <li>Black starts on ranks 7-8</li>
            </ul>
          </article>
          <article class="notation-card">
            <h3>Review prompt</h3>
            <p>After each game, write one sentence for the opening, one for the tactic you missed, and one for the endgame plan you wanted.</p>
            <ul class="notation-list">
              <li><code>?</code><span>A mistake worth reviewing.</span></li>
              <li><code>!</code><span>A strong move with a clear idea.</span></li>
              <li><code>+/-</code><span>White is clearly better.</span></li>
            </ul>
          </article>
        </div>
      </div>
    </section>

    <section id="puzzles" class="section-warm" aria-labelledby="puzzles-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Puzzle board</p>
            <h2 id="puzzles-title">Find the move</h2>
          </div>
          <p class="section-intro">Solve positions by pattern: mate threats, forks, and overloaded defenders. The feedback explains the idea behind the answer.</p>
        </div>

        <div class="puzzle-shell">
          <div class="puzzle-board-wrap" aria-label="Chess puzzle position">
            <div class="puzzle-board" id="puzzleBoard"></div>
            <div class="coordinates" aria-hidden="true" id="coordinates"></div>
          </div>
          <div class="puzzle-info">
            <div class="puzzle-meta">
              <span class="badge" id="puzzleLevel">Beginner</span>
              <span class="badge" id="puzzleSide">White to move</span>
            </div>
            <div class="puzzle-stats" aria-label="Puzzle progress">
              <div class="stat-pill">
                <strong id="puzzleCounter">1 / 6</strong>
                <span>Position</span>
              </div>
              <div class="stat-pill">
                <strong id="puzzleSolved">0</strong>
                <span>Solved</span>
              </div>
              <div class="stat-pill">
                <strong id="puzzleStreak">0</strong>
                <span>Streak</span>
              </div>
            </div>
            <div class="progress-track" aria-hidden="true">
              <span class="progress-fill" id="puzzleProgress"></span>
            </div>
            <h3 id="puzzleTitle">Puzzle title</h3>
            <p id="puzzlePrompt">Puzzle prompt</p>
            <p class="puzzle-hint hidden" id="puzzleHint">Hint text</p>
            <div class="answers" id="answers"></div>
            <p class="feedback" id="feedback">Choose the strongest move.</p>
            <div class="puzzle-actions">
              <button class="button secondary" type="button" id="hintPuzzle">Hint</button>
              <button class="button secondary" type="button" id="revealPuzzle">Reveal</button>
              <button class="button" type="button" id="nextPuzzle">Next Puzzle</button>
              <button class="button secondary" type="button" id="resetPuzzle">Reset Score</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="plan" class="section-dark" aria-labelledby="plan-title">
      <div class="wrap">
        <div class="section-head">
          <div>
            <p class="section-kicker">Study rhythm</p>
            <h2 id="plan-title">A simple weekly plan</h2>
          </div>
          <p class="section-intro">A steady mix of play, puzzles, review, and endgames beats random marathon sessions.</p>
        </div>

        <div class="study-plan">
          <article class="plan-panel">
            <h3>Three-day loop</h3>
            <ul class="plan-list">
              <li><span>1</span><div>Play one slower game and write down the move where the position first felt unclear.</div></li>
              <li><span>2</span><div>Solve ten tactics by theme, then replay the mistakes until the pattern is automatic.</div></li>
              <li><span>3</span><div>Study one endgame position and test it from both sides against a board or engine.</div></li>
            </ul>
          </article>
          <article class="plan-panel">
            <h3>Review checklist</h3>
            <ul class="plan-list">
              <li><span>✓</span><div>Was the king safe before launching an attack?</div></li>
              <li><span>✓</span><div>Did every trade improve the position or solve a concrete problem?</div></li>
              <li><span>✓</span><div>Were checks, captures, and threats examined before the final move?</div></li>
            </ul>
          </article>
        </div>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="wrap">
      <span>Chess Ladder</span>
      <span>Learn the board, spot the pattern, make the plan.</span>
    </div>
  </footer>

  <script>
    const heroPieces = [
      "♜", "♞", "♝", "♛", "♚", "♝", "♞", "♜",
      "♟", "♟", "♟", "", "♟", "♟", "♟", "♟",
      "", "", "", "", "", "", "", "",
      "", "", "", "♟", "", "", "", "",
      "", "", "", "♙", "", "", "", "",
      "", "", "♘", "", "", "♘", "", "",
      "♙", "♙", "♙", "", "♙", "♙", "♙", "♙",
      "♖", "", "♗", "♕", "♔", "♗", "", "♖"
    ];

    const pieceMap = {
      K: "♔", Q: "♕", R: "♖", B: "♗", N: "♘", P: "♙",
      k: "♚", q: "♛", r: "♜", b: "♝", n: "♞", p: "♟"
    };

    const puzzles = [
      {
        level: "Beginner",
        side: "White to move",
        title: "Back-rank mate",
        prompt: "Black's king is trapped by its own pawns. Which move ends the game?",
        fen: "6k1/5ppp/8/8/8/8/5PPP/4R1K1",
        targets: ["e8"],
        hint: "Look for a rook move that uses the open file and attacks the king from the back rank.",
        answers: [
          { move: "Re8#", correct: true },
          { move: "Rg1", correct: false },
          { move: "Kf2", correct: false }
        ],
        feedback: "Re8# uses the open e-file. The king cannot capture, block, or run because its escape squares are occupied."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Knight fork",
        prompt: "White can attack the black king and queen at the same time.",
        fen: "8/8/4k3/7q/8/3N4/8/4K3",
        targets: ["f4"],
        hint: "The knight wants a square where it checks the king and also points at h5.",
        answers: [
          { move: "Nf4+", correct: true },
          { move: "Nc1", correct: false },
          { move: "Kd2", correct: false }
        ],
        feedback: "Nf4+ checks the king on e6 and also attacks the queen on h5. One knight move creates two threats."
      },
      {
        level: "Advanced",
        side: "Black to move",
        title: "Overloaded defender",
        prompt: "White's queen is guarding too much. Find the forcing capture.",
        fen: "6k1/5ppp/8/2b5/8/6q1/5QPP/6K1",
        targets: ["f2"],
        hint: "The bishop on c5 quietly protects the square next to White's king.",
        answers: [
          { move: "Qxf2+", correct: true },
          { move: "Qg4", correct: false },
          { move: "Kh7", correct: false }
        ],
        feedback: "Qxf2+ removes the defender and gives check. The bishop on c5 protects f2, so the capture cannot be answered by Kxf2."
      },
      {
        level: "Beginner",
        side: "White to move",
        title: "Queen joins the attack",
        prompt: "The bishop already controls the key diagonal. Which queen move finishes the game?",
        fen: "6kr/5ppp/8/8/2B5/5Q2/6PP/6K1",
        targets: ["f7"],
        hint: "The queen can capture a pawn next to the king, and the bishop protects that landing square.",
        answers: [
          { move: "Qxf7#", correct: true },
          { move: "Qxf7+", correct: false },
          { move: "Bc4", correct: false }
        ],
        feedback: "Qxf7# is mate because the queen attacks g8, the bishop protects f7, and Black's own pieces block the escape squares."
      },
      {
        level: "Intermediate",
        side: "White to move",
        title: "Capture the pinned queen",
        prompt: "Black's queen is lined up with the king. Which capture wins material with check?",
        fen: "4k3/3q4/5N2/1B6/8/8/8/4K3",
        targets: ["d7"],
        hint: "Your bishop can take the queen, and your knight protects the bishop afterward.",
        answers: [
          { move: "Bxd7+", correct: true },
          { move: "Nxd7", correct: false },
          { move: "Bf1", correct: false }
        ],
        feedback: "Bxd7+ wins the queen with check. The knight on f6 protects d7, so Black cannot simply recapture."
      },
      {
        level: "Advanced",
        side: "White to move",
        title: "Pawn break with opposition",
        prompt: "Use the king's support to push the pawn and force the black king backward.",
        fen: "8/8/8/3k4/8/3K4/4P3/8",
        targets: ["e4"],
        hint: "The pawn can advance two squares because it is still on its starting square.",
        answers: [
          { move: "e4+", correct: true },
          { move: "Kc3", correct: false },
          { move: "Kd4", correct: false }
        ],
        feedback: "e4+ works because the white king protects e4. The pawn checks the black king and gains space for the endgame."
      }
    ];

    let currentPuzzle = 0;
    let activeAnswered = false;
    let streak = 0;
    const solvedPuzzles = new Set();

    function buildHeroBoard() {
      const board = document.getElementById("heroBoard");
      heroPieces.forEach((piece, index) => {
        const square = document.createElement("span");
        const row = Math.floor(index / 8);
        const col = index % 8;
        square.className = `hero-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
        square.textContent = piece;
        board.appendChild(square);
      });
    }

    function fenToSquares(fen) {
      const rows = fen.split("/");
      return rows.flatMap((row) => {
        const squares = [];
        [...row].forEach((char) => {
          const empty = Number(char);
          if (Number.isInteger(empty) && empty > 0) {
            for (let i = 0; i < empty; i += 1) squares.push("");
          } else {
            squares.push(pieceMap[char] || "");
          }
        });
        return squares;
      });
    }

    function squareName(index) {
      const files = ["a", "b", "c", "d", "e", "f", "g", "h"];
      const row = Math.floor(index / 8);
      const col = index % 8;
      return `${files[col]}${8 - row}`;
    }

    function renderMiniBoards() {
      document.querySelectorAll(".mini-board").forEach((board) => {
        const squares = fenToSquares(board.dataset.fen);
        board.innerHTML = "";
        squares.forEach((piece, index) => {
          const row = Math.floor(index / 8);
          const col = index % 8;
          const square = document.createElement("span");
          square.className = `mini-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
          square.textContent = piece;
          board.appendChild(square);
        });
      });
    }

    function updatePuzzleStats() {
      document.getElementById("puzzleCounter").textContent = `${currentPuzzle + 1} / ${puzzles.length}`;
      document.getElementById("puzzleSolved").textContent = solvedPuzzles.size;
      document.getElementById("puzzleStreak").textContent = streak;
      document.getElementById("puzzleProgress").style.width = `${(solvedPuzzles.size / puzzles.length) * 100}%`;
    }

    function lockAnswers(selectedButton, selectedWasCorrect) {
      const puzzle = puzzles[currentPuzzle];
      const answers = document.getElementById("answers");

      [...answers.children].forEach((child) => {
        child.disabled = true;
        const matching = puzzle.answers.find((item) => item.move === child.textContent);
        if (matching && matching.correct) child.classList.add("correct");
      });

      if (selectedButton && !selectedWasCorrect) {
        selectedButton.classList.add("wrong");
      }
    }

    function handleAnswer(answer, button) {
      if (activeAnswered) return;

      const puzzle = puzzles[currentPuzzle];
      activeAnswered = true;
      lockAnswers(button, answer.correct);

      if (answer.correct) {
        if (!solvedPuzzles.has(currentPuzzle)) {
          solvedPuzzles.add(currentPuzzle);
          streak += 1;
        }
        document.getElementById("feedback").textContent = puzzle.feedback;
      } else {
        streak = 0;
        document.getElementById("feedback").textContent = `Not quite. ${puzzle.feedback}`;
      }

      updatePuzzleStats();
    }

    function renderPuzzle() {
      const puzzle = puzzles[currentPuzzle];
      const board = document.getElementById("puzzleBoard");
      const answers = document.getElementById("answers");
      const feedback = document.getElementById("feedback");
      const hint = document.getElementById("puzzleHint");
      const squares = fenToSquares(puzzle.fen);

      activeAnswered = false;
      document.getElementById("puzzleLevel").textContent = puzzle.level;
      document.getElementById("puzzleSide").textContent = puzzle.side;
      document.getElementById("puzzleTitle").textContent = puzzle.title;
      document.getElementById("puzzlePrompt").textContent = puzzle.prompt;
      hint.textContent = puzzle.hint;
      hint.classList.add("hidden");
      feedback.textContent = "Choose the strongest move.";
      document.getElementById("hintPuzzle").disabled = false;
      document.getElementById("revealPuzzle").disabled = false;
      updatePuzzleStats();

      board.innerHTML = "";
      squares.forEach((piece, index) => {
        const row = Math.floor(index / 8);
        const col = index % 8;
        const square = document.createElement("span");
        const name = squareName(index);
        square.className = `puzzle-square ${(row + col) % 2 === 0 ? "light" : "dark"}`;
        if (puzzle.targets.includes(name)) square.classList.add("target");
        square.textContent = piece;
        square.setAttribute("aria-label", `${name}${piece ? ` ${piece}` : ""}`);
        board.appendChild(square);
      });

      answers.innerHTML = "";
      puzzle.answers.forEach((answer) => {
        const button = document.createElement("button");
        button.type = "button";
        button.className = "answer-button";
        button.textContent = answer.move;
        button.addEventListener("click", () => handleAnswer(answer, button));
        answers.appendChild(button);
      });
    }

    function renderCoordinates() {
      const coordinates = document.getElementById("coordinates");
      const files = ["a", "b", "c", "d", "e", "f", "g", "h"];
      const ranks = ["8", "7", "6", "5", "4", "3", "2", "1"];

      files.forEach((file, index) => {
        const marker = document.createElement("span");
        marker.textContent = file;
        marker.style.left = `${index * 12.5 + 1.5}%`;
        marker.style.bottom = "0.5%";
        coordinates.appendChild(marker);
      });

      ranks.forEach((rank, index) => {
        const marker = document.createElement("span");
        marker.textContent = rank;
        marker.style.top = `${index * 12.5 + 0.5}%`;
        marker.style.left = "1%";
        coordinates.appendChild(marker);
      });
    }

    function wireTabs() {
      const tabs = document.querySelectorAll(".tab-button");
      const panels = ["beginner", "intermediate", "advanced"].map((id) => document.getElementById(id));

      tabs.forEach((tab) => {
        tab.addEventListener("click", () => {
          const level = tab.dataset.level;
          tabs.forEach((item) => item.setAttribute("aria-selected", String(item === tab)));
          panels.forEach((panel) => panel.classList.toggle("hidden", panel.id !== level));
        });
      });
    }

    document.getElementById("nextPuzzle").addEventListener("click", () => {
      currentPuzzle = (currentPuzzle + 1) % puzzles.length;
      renderPuzzle();
    });

    document.getElementById("resetPuzzle").addEventListener("click", () => {
      currentPuzzle = 0;
      streak = 0;
      solvedPuzzles.clear();
      renderPuzzle();
    });

    document.getElementById("hintPuzzle").addEventListener("click", () => {
      document.getElementById("puzzleHint").classList.remove("hidden");
    });

    document.getElementById("revealPuzzle").addEventListener("click", () => {
      if (activeAnswered) return;

      const puzzle = puzzles[currentPuzzle];
      const correct = puzzle.answers.find((answer) => answer.correct);
      activeAnswered = true;
      streak = 0;
      lockAnswers(null, false);
      document.getElementById("feedback").textContent = `Solution: ${correct.move}. ${puzzle.feedback}`;
      updatePuzzleStats();
    });

    buildHeroBoard();
    renderMiniBoards();
    renderCoordinates();
    renderPuzzle();
    wireTabs();
  </script>
</body>
</html>
