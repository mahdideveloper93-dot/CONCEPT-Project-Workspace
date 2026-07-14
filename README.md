<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CONCEPT - Project Workspace</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&family=Rajdhani:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600&family=Cairo:wght@300;400;500;600;700;800;900&family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        :root {
            --deep-navy: #060a1a;
            --electric-blue: #00d4ff;
            --purple-glow: #b829dd;
            --neon-pink: #ff2d95;
            --glass-bg: rgba(6, 10, 26, 0.7);
            --glass-border: rgba(0, 212, 255, 0.15);
            --text-white: #ffffff;
            --text-gray: #8892b0;
            --text-light: #ccd6f6;
        }
        body {
            font-family: 'Tajawal', 'Rajdhani', sans-serif;
            background: var(--deep-navy);
            color: var(--text-white);
            min-height: 100vh;
            overflow-x: hidden;
        }
        .stars-container {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: -1;
            background: radial-gradient(ellipse at bottom, #0a1128 0%, #020408 100%);
            overflow: hidden;
        }
        .stars {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background-image: 
                radial-gradient(1.5px 1.5px at 20px 30px, rgba(255,255,255,0.8), transparent),
                radial-gradient(1.5px 1.5px at 40px 70px, rgba(255,255,255,0.6), transparent),
                radial-gradient(1px 1px at 50px 160px, rgba(255,255,255,0.7), transparent),
                radial-gradient(1.5px 1.5px at 90px 40px, rgba(255,255,255,0.5), transparent),
                radial-gradient(1px 1px at 130px 80px, rgba(255,255,255,0.6), transparent),
                radial-gradient(1.5px 1.5px at 160px 120px, rgba(255,255,255,0.4), transparent),
                radial-gradient(1px 1px at 200px 50px, rgba(255,255,255,0.7), transparent),
                radial-gradient(1.5px 1.5px at 250px 180px, rgba(255,255,255,0.5), transparent),
                radial-gradient(1px 1px at 300px 90px, rgba(255,255,255,0.6), transparent);
            background-size: 350px 250px;
            animation: twinkle 8s ease-in-out infinite;
        }
        .stars-2 {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background-image: 
                radial-gradient(1px 1px at 100px 50px, rgba(255,255,255,0.5), transparent),
                radial-gradient(1.5px 1.5px at 150px 100px, rgba(255,255,255,0.7), transparent),
                radial-gradient(1px 1px at 200px 150px, rgba(255,255,255,0.4), transparent),
                radial-gradient(1.5px 1.5px at 250px 200px, rgba(255,255,255,0.6), transparent),
                radial-gradient(1px 1px at 350px 80px, rgba(255,255,255,0.5), transparent),
                radial-gradient(1.5px 1.5px at 400px 220px, rgba(255,255,255,0.7), transparent);
            background-size: 450px 300px;
            animation: twinkle 12s ease-in-out infinite reverse;
        }
        .nebula {
            position: fixed; border-radius: 50%; filter: blur(100px); opacity: 0.35;
            z-index: -1; animation: float 25s ease-in-out infinite;
        }
        .nebula-1 { width: 700px; height: 700px; background: radial-gradient(circle, rgba(0,212,255,0.25), transparent 70%); top: -15%; right: -15%; }
        .nebula-2 { width: 600px; height: 600px; background: radial-gradient(circle, rgba(184,41,221,0.25), transparent 70%); bottom: -15%; left: -15%; animation-delay: -8s; }
        .nebula-3 { width: 500px; height: 500px; background: radial-gradient(circle, rgba(255,45,149,0.15), transparent 70%); top: 50%; left: 40%; animation-delay: -15s; }
        .planet-decoration {
            position: fixed; top: 5%; right: -5%; width: 600px; height: 600px;
            border-radius: 50%; background: radial-gradient(circle at 30% 30%, rgba(0,212,255,0.1), transparent 60%);
            z-index: -1; opacity: 0.6; animation: planet-rotate 60s linear infinite;
        }
        .planet-decoration::before {
            content: ''; position: absolute; top: 50%; left: 50%; transform: translate(-50%,-50%);
            width: 100%; height: 100%; border-radius: 50%; border: 1px solid rgba(0,212,255,0.1);
            box-shadow: 0 0 60px rgba(0,212,255,0.1), inset 0 0 60px rgba(0,212,255,0.05);
        }
        .orbit-ring { position: fixed; border-radius: 50%; border: 1px solid rgba(0,212,255,0.08); z-index: -1; }
        .orbit-ring-1 { width: 800px; height: 800px; top: -10%; right: -10%; animation: orbit-rotate 40s linear infinite; }
        .orbit-ring-2 { width: 1000px; height: 1000px; top: -20%; right: -20%; animation: orbit-rotate 60s linear infinite reverse; }
        .orbit-dot { position: absolute; width: 8px; height: 8px; border-radius: 50%; background: var(--electric-blue); box-shadow: 0 0 10px var(--electric-blue); }
        .orbit-dot-1 { top: 0; left: 50%; transform: translateX(-50%); }
        .orbit-dot-2 { bottom: 10%; left: 10%; width: 6px; height: 6px; background: var(--purple-glow); box-shadow: 0 0 8px var(--purple-glow); }
        .orbit-dot-3 { top: 30%; right: 0; width: 5px; height: 5px; background: var(--neon-pink); box-shadow: 0 0 6px var(--neon-pink); }
        @keyframes twinkle { 0%,100% { opacity: 0.7; } 50% { opacity: 0.3; } }
        @keyframes float { 0%,100% { transform: translate(0,0) scale(1); } 33% { transform: translate(40px,-40px) scale(1.1); } 66% { transform: translate(-30px,30px) scale(0.9); } }
        @keyframes planet-rotate { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        @keyframes orbit-rotate { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        @keyframes glow-pulse { 0%,100% { box-shadow: 0 0 20px rgba(0,212,255,0.3), 0 0 40px rgba(0,212,255,0.1); } 50% { box-shadow: 0 0 35px rgba(0,212,255,0.5), 0 0 70px rgba(0,212,255,0.2); } }
        @keyframes slide-up { from { opacity: 0; transform: translateY(40px); } to { opacity: 1; transform: translateY(0); } }
        .animate-up { animation: slide-up 0.8s ease-out forwards; opacity: 0; }
        .delay-1 { animation-delay: 0.1s; }
        .delay-2 { animation-delay: 0.2s; }
        .delay-3 { animation-delay: 0.3s; }
        .delay-4 { animation-delay: 0.4s; }
        .delay-5 { animation-delay: 0.5s; }
        .delay-6 { animation-delay: 0.6s; }
        .glass-card {
            background: var(--glass-bg); backdrop-filter: blur(24px); -webkit-backdrop-filter: blur(24px);
            border: 1px solid var(--glass-border); border-radius: 20px; padding: 28px;
            position: relative; overflow: hidden;
            transition: all 0.4s cubic-bezier(0.4,0,0.2,1);
        }
        .glass-card::before {
            content: ''; position: absolute; top: 0; left: -100%; width: 100%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0,212,255,0.06), transparent);
            transition: left 0.6s ease;
        }
        .glass-card:hover::before { left: 100%; }
        .glass-card:hover {
            border-color: rgba(0,212,255,0.35);
            box-shadow: 0 0 40px rgba(0,212,255,0.12), inset 0 0 30px rgba(0,212,255,0.03);
            transform: translateY(-3px);
        }
        .glass-card-strong { border-color: rgba(0,212,255,0.3); box-shadow: 0 0 30px rgba(0,212,255,0.08); }
        .neon-text { text-shadow: 0 0 10px rgba(0,212,255,0.5), 0 0 20px rgba(0,212,255,0.3), 0 0 40px rgba(0,212,255,0.1); }
        .neon-purple { text-shadow: 0 0 10px rgba(184,41,221,0.5), 0 0 20px rgba(184,41,221,0.3); }
        .container { max-width: 1600px; margin: 0 auto; padding: 40px 24px; }
        .header-section { text-align: center; margin-bottom: 70px; position: relative; }
        .logo-container { display: flex; flex-direction: column; align-items: center; margin-bottom: 40px; }
        .logo-svg { width: 140px; height: 140px; margin-bottom: 30px; filter: drop-shadow(0 0 30px rgba(0,212,255,0.4)); }
        .logo-brand { font-family: 'Orbitron', sans-serif; font-size: 52px; font-weight: 400; letter-spacing: 18px; color: var(--text-white); margin-bottom: 16px; text-transform: uppercase; }
        .logo-tagline { font-family: 'Orbitron', sans-serif; font-size: 13px; letter-spacing: 6px; color: var(--text-gray); margin-bottom: 8px; text-transform: uppercase; }
        .logo-tagline .highlight { color: var(--electric-blue); text-shadow: 0 0 15px rgba(0,212,255,0.6); }
        .logo-subtitle { font-family: 'Orbitron', sans-serif; font-size: 11px; letter-spacing: 8px; color: var(--text-gray); text-transform: uppercase; opacity: 0.8; }
        .main-title { font-family: 'Orbitron', sans-serif; font-size: 42px; font-weight: 900; color: var(--text-white); letter-spacing: 10px; margin-bottom: 12px; text-transform: uppercase; }
        .main-title span { color: var(--electric-blue); text-shadow: 0 0 25px rgba(0,212,255,0.6); }
        .subtitle { font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 20px; font-weight: 500; color: var(--text-gray); letter-spacing: 5px; text-transform: uppercase; }
        .subtitle-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 18px; font-weight: 500; color: var(--text-gray); margin-top: 8px; letter-spacing: 2px; }
        .section-title { font-family: 'Orbitron', sans-serif; font-size: 13px; font-weight: 700; letter-spacing: 4px; color: var(--electric-blue); text-transform: uppercase; margin-bottom: 28px; display: flex; align-items: center; gap: 14px; }
        .section-title::before { content: ''; display: block; width: 40px; height: 2px; background: linear-gradient(90deg, var(--electric-blue), transparent); }
        .section-title::after { content: ''; display: block; flex: 1; height: 1px; background: linear-gradient(90deg, transparent, rgba(0,212,255,0.25)); }
        .section-title-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 14px; font-weight: 700; color: var(--purple-glow); margin-top: 4px; letter-spacing: 1px; }
        .grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px; }
        .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
        .grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; }
        .grid-5 { display: grid; grid-template-columns: repeat(5, 1fr); gap: 16px; }
        .hierarchy-card { text-align: center; padding: 24px 16px; position: relative; }
        .hierarchy-card .name { font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 14px; font-weight: 700; color: var(--text-white); margin-bottom: 8px; letter-spacing: 1px; }
        .hierarchy-card .role { font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 12px; color: var(--electric-blue); font-weight: 600; margin-bottom: 6px; letter-spacing: 1px; }
        .hierarchy-card .role-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 13px; color: var(--text-gray); font-weight: 500; margin-top: 4px; }
        .hierarchy-card .avatar { width: 65px; height: 65px; border-radius: 50%; background: linear-gradient(135deg, rgba(0,212,255,0.15), rgba(184,41,221,0.15)); border: 2px solid var(--electric-blue); display: flex; align-items: center; justify-content: center; margin: 0 auto 18px; font-family: 'Orbitron', sans-serif; font-size: 18px; font-weight: 700; color: var(--electric-blue); box-shadow: 0 0 25px rgba(0,212,255,0.2); animation: glow-pulse 4s ease-in-out infinite; }
        .hierarchy-card .rank-badge { position: absolute; top: 12px; right: 12px; width: 24px; height: 24px; border-radius: 50%; background: linear-gradient(135deg, var(--electric-blue), var(--purple-glow)); display: flex; align-items: center; justify-content: center; font-size: 10px; font-weight: 700; color: var(--deep-navy); font-family: 'Orbitron', sans-serif; }
        .team-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 18px; }
        .team-card { padding: 20px; text-align: center; }
        .team-card .dept-name { font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 12px; font-weight: 700; color: var(--purple-glow); letter-spacing: 2px; margin-bottom: 16px; text-transform: uppercase; padding-bottom: 10px; border-bottom: 1px solid rgba(184,41,221,0.2); }
        .team-card .dept-name-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 13px; font-weight: 700; color: var(--purple-glow); margin-top: 4px; }
        .team-card .member-name { font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 15px; font-weight: 600; color: var(--text-white); margin-bottom: 4px; }
        .team-card .member-role { font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); }
        .team-card .member-role-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 2px; }
        .team-card .member-avatar { width: 48px; height: 48px; border-radius: 50%; background: linear-gradient(135deg, rgba(184,41,221,0.25), rgba(0,212,255,0.25)); border: 1.5px solid var(--purple-glow); display: flex; align-items: center; justify-content: center; margin: 0 auto 12px; font-family: 'Orbitron', sans-serif; font-size: 16px; font-weight: 700; color: var(--purple-glow); box-shadow: 0 0 15px rgba(184,41,221,0.15); }
        .member-row { padding: 10px 0; border-bottom: 1px solid rgba(255,255,255,0.04); }
        .member-row:last-child { border-bottom: none; }
        .workflow-container { display: flex; flex-direction: column; align-items: center; gap: 0; padding: 30px 0; }
        .workflow-step { display: flex; align-items: center; justify-content: center; width: 100%; position: relative; }
        .workflow-node { background: linear-gradient(135deg, rgba(0,212,255,0.12), rgba(184,41,221,0.12)); border: 1.5px solid var(--electric-blue); border-radius: 14px; padding: 14px 36px; font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 12px; font-weight: 600; color: var(--text-white); letter-spacing: 2px; text-align: center; min-width: 220px; position: relative; z-index: 2; box-shadow: 0 0 25px rgba(0,212,255,0.1); transition: all 0.3s ease; }
        .workflow-node:hover { box-shadow: 0 0 40px rgba(0,212,255,0.25); transform: scale(1.05); }
        .workflow-node.highlight { border-color: var(--purple-glow); background: linear-gradient(135deg, rgba(184,41,221,0.18), rgba(0,212,255,0.18)); box-shadow: 0 0 30px rgba(184,41,221,0.2); }
        .workflow-node .node-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 11px; color: var(--text-gray); margin-top: 4px; letter-spacing: 0; }
        .workflow-arrow { height: 45px; display: flex; align-items: center; justify-content: center; position: relative; }
        .workflow-arrow::before { content: ''; width: 2px; height: 100%; background: linear-gradient(to bottom, var(--electric-blue), var(--purple-glow)); position: absolute; }
        .workflow-arrow::after { content: '▼'; color: var(--electric-blue); font-size: 10px; text-shadow: 0 0 12px var(--electric-blue); position: absolute; bottom: 2px; }
        .workflow-branch { display: flex; justify-content: center; gap: 50px; margin: 15px 0; position: relative; }
        .workflow-branch::before { content: ''; position: absolute; top: -25px; left: 50%; transform: translateX(-50%); width: 2px; height: 25px; background: linear-gradient(to bottom, var(--electric-blue), var(--purple-glow)); }
        .workflow-branch::after { content: ''; position: absolute; top: 0; left: 25%; right: 25%; height: 2px; background: linear-gradient(to right, var(--electric-blue), var(--purple-glow)); }
        .branch-item { background: linear-gradient(135deg, rgba(255,45,149,0.12), rgba(184,41,221,0.12)); border: 1.5px solid var(--neon-pink); border-radius: 12px; padding: 12px 28px; font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 11px; font-weight: 600; color: var(--text-white); letter-spacing: 1px; position: relative; z-index: 2; transition: all 0.3s ease; }
        .branch-item:hover { box-shadow: 0 0 25px rgba(255,45,149,0.2); transform: scale(1.05); }
        .branch-item::before { content: ''; position: absolute; top: -25px; left: 50%; transform: translateX(-50%); width: 2px; height: 25px; background: var(--neon-pink); }
        .branch-item .item-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 10px; color: var(--text-gray); margin-top: 3px; letter-spacing: 0; }
        .handover-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 18px; }
        .handover-card { padding: 20px; position: relative; }
        .handover-card .dept-title { font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 12px; font-weight: 700; color: var(--electric-blue); margin-bottom: 14px; letter-spacing: 2px; text-align: center; padding-bottom: 10px; border-bottom: 1px solid rgba(0,212,255,0.2); }
        .handover-card .dept-title-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 13px; font-weight: 700; color: var(--electric-blue); text-align: center; margin-bottom: 10px; }
        .handover-flow { display: flex; flex-direction: column; gap: 10px; }
        .handover-item { display: flex; align-items: center; gap: 10px; font-size: 12px; }
        .handover-item .label { font-family: 'Rajdhani', 'Tajawal', sans-serif; color: var(--text-gray); min-width: 90px; font-size: 11px; text-transform: uppercase; letter-spacing: 1px; }
        .handover-item .label-ar { font-family: 'Cairo', 'Tajawal', sans-serif; color: var(--text-gray); min-width: 70px; font-size: 12px; }
        .handover-item .value { font-family: 'Rajdhani', 'Tajawal', sans-serif; color: var(--text-white); font-weight: 600; flex: 1; font-size: 12px; }
        .handover-item .value-ar { font-family: 'Cairo', 'Tajawal', sans-serif; color: var(--text-light); font-weight: 500; flex: 1; font-size: 12px; }
        .handover-arrow { color: var(--purple-glow); font-size: 14px; text-shadow: 0 0 8px var(--purple-glow); }
        .calendar-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 18px; }
        .week-card { padding: 24px; min-height: 300px; }
        .week-card .week-title { font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 13px; font-weight: 700; color: var(--electric-blue); margin-bottom: 18px; letter-spacing: 2px; text-align: center; padding-bottom: 14px; border-bottom: 1px solid rgba(0,212,255,0.2); }
        .week-card .week-title-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 14px; font-weight: 700; color: var(--electric-blue); text-align: center; margin-bottom: 14px; }
        .week-card .task-list { list-style: none; display: flex; flex-direction: column; gap: 10px; }
        .week-card .task-item { display: flex; align-items: center; gap: 10px; font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; color: var(--text-gray); padding: 7px 0; border-bottom: 1px solid rgba(255,255,255,0.04); transition: all 0.2s ease; }
        .week-card .task-item:hover { color: var(--text-white); padding-right: 8px; }
        .week-card .task-item::before { content: '◆'; color: var(--purple-glow); font-size: 8px; flex-shrink: 0; text-shadow: 0 0 8px var(--purple-glow); }
        .task-item .task-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-right: 6px; }
        .deadlines-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 14px; }
        .deadline-card { display: flex; justify-content: space-between; align-items: center; padding: 16px 20px; }
        .deadline-card .task-name { font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; font-weight: 600; color: var(--text-white); }
        .deadline-card .task-name-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 2px; }
        .deadline-card .time-badge { background: linear-gradient(135deg, rgba(0,212,255,0.15), rgba(184,41,221,0.15)); border: 1px solid var(--electric-blue); border-radius: 24px; padding: 5px 14px; font-family: 'Orbitron', sans-serif; font-size: 10px; font-weight: 600; color: var(--electric-blue); letter-spacing: 1px; white-space: nowrap; box-shadow: 0 0 15px rgba(0,212,255,0.1); }
        .status-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 12px; }
        .status-item { display: flex; align-items: center; gap: 12px; padding: 12px 16px; border-radius: 10px; background: rgba(255,255,255,0.03); border: 1px solid rgba(255,255,255,0.06); transition: all 0.3s ease; }
        .status-item:hover { background: rgba(255,255,255,0.06); border-color: rgba(255,255,255,0.12); transform: translateX(-4px); }
        .status-dot { width: 12px; height: 12px; border-radius: 50%; flex-shrink: 0; box-shadow: 0 0 10px currentColor; }
        .status-label { font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); font-weight: 500; }
        .status-label-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 11px; color: var(--text-gray); margin-top: 2px; }
        .folder-tree { font-family: 'Inter', 'Tajawal', monospace; font-size: 13px; line-height: 2.2; color: var(--text-gray); padding: 24px; }
        .folder-tree .folder { color: var(--electric-blue); font-weight: 600; font-size: 14px; }
        .folder-tree .folder-ar { font-family: 'Cairo', 'Tajawal', sans-serif; color: var(--electric-blue); font-size: 13px; margin-right: 8px; }
        .folder-tree .file { color: var(--text-gray); transition: all 0.2s ease; }
        .folder-tree .file:hover { color: var(--text-white); }
        .folder-tree .file-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-right: 8px; }
        .folder-tree .indent { margin-right: 28px; border-right: 1px solid rgba(0,212,255,0.15); padding-right: 20px; }
        .footer { text-align: center; padding: 70px 20px 50px; margin-top: 70px; border-top: 1px solid rgba(0,212,255,0.1); position: relative; }
        .footer::before { content: ''; position: absolute; top: -1px; left: 50%; transform: translateX(-50%); width: 200px; height: 2px; background: linear-gradient(90deg, transparent, var(--electric-blue), transparent); }
        .footer-text { font-family: 'Orbitron', sans-serif; font-size: 22px; font-weight: 700; color: var(--text-white); letter-spacing: 6px; line-height: 2; }
        .footer-text .highlight { color: var(--electric-blue); text-shadow: 0 0 25px rgba(0,212,255,0.5); }
        .footer-text-ar { font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 20px; font-weight: 700; color: var(--text-white); margin-top: 16px; letter-spacing: 2px; }
        .footer-text-ar .highlight { color: var(--electric-blue); text-shadow: 0 0 25px rgba(0,212,255,0.5); }
        .glow-divider { height: 1px; background: linear-gradient(90deg, transparent, var(--electric-blue), var(--purple-glow), transparent); margin: 40px 0; opacity: 0.3; }
        @media (max-width: 1200px) { .calendar-grid { grid-template-columns: repeat(2, 1fr); } .grid-4 { grid-template-columns: repeat(2, 1fr); } .grid-5 { grid-template-columns: repeat(3, 1fr); } }
        @media (max-width: 768px) { .main-title { font-size: 28px; letter-spacing: 6px; } .logo-brand { font-size: 36px; letter-spacing: 10px; } .grid-2, .grid-3, .grid-4, .grid-5 { grid-template-columns: 1fr; } .calendar-grid { grid-template-columns: 1fr; } .team-grid { grid-template-columns: 1fr; } .handover-grid { grid-template-columns: 1fr; } .deadlines-grid { grid-template-columns: 1fr; } }
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--deep-navy); }
        ::-webkit-scrollbar-thumb { background: linear-gradient(to bottom, var(--electric-blue), var(--purple-glow)); border-radius: 4px; }
        @media print { .stars-container, .nebula, .planet-decoration, .orbit-ring { display: none; } body { background: #060a1a; } .glass-card { break-inside: avoid; page-break-inside: avoid; } }
    </style>
<base target="_blank">
</head>
<body>
    <div class="stars-container"><div class="stars"></div><div class="stars-2"></div></div>
    <div class="nebula nebula-1"></div><div class="nebula nebula-2"></div><div class="nebula nebula-3"></div>
    <div class="planet-decoration"></div>
    <div class="orbit-ring orbit-ring-1"><div class="orbit-dot orbit-dot-1"></div><div class="orbit-dot orbit-dot-2"></div></div>
    <div class="orbit-ring orbit-ring-2"><div class="orbit-dot orbit-dot-3"></div></div>

    <div class="container">
        <header class="header-section animate-up">
            <div class="logo-container">
                <svg class="logo-svg" viewBox="0 0 200 200" fill="none">
                    <defs>
                        <linearGradient id="logoGrad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" style="stop-color:#00d4ff"/><stop offset="100%" style="stop-color:#b829dd"/></linearGradient>
                        <linearGradient id="planetGrad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" style="stop-color:#4a90e2"/><stop offset="50%" style="stop-color:#2d5aa0"/><stop offset="100%" style="stop-color:#1a3a6e"/></linearGradient>
                        <filter id="glow"><feGaussianBlur stdDeviation="3" result="coloredBlur"/><feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
                    </defs>
                    <circle cx="100" cy="100" r="60" stroke="url(#logoGrad)" stroke-width="4" fill="none" filter="url(#glow)"/>
                    <circle cx="100" cy="100" r="35" fill="url(#planetGrad)" filter="url(#glow)"/>
                    <ellipse cx="85" cy="85" rx="15" ry="10" fill="rgba(255,255,255,0.15)" transform="rotate(-45 85 85)"/>
                    <circle cx="160" cy="55" r="10" fill="url(#planetGrad)" filter="url(#glow)"/>
                    <circle cx="157" cy="52" r="3" fill="rgba(255,255,255,0.3)"/>
                    <ellipse cx="100" cy="100" rx="75" ry="30" stroke="url(#logoGrad)" stroke-width="1.5" fill="none" opacity="0.4" transform="rotate(-30 100 100)"/>
                </svg>
                <div class="logo-brand">CONCEPT</div>
                <div class="logo-tagline">A WHOLE PLANET OF <span class="highlight">CREATIVITY</span></div>
                <div class="logo-subtitle">DIGITAL MARKETING AGENCY</div>
            </div>
            <h1 class="main-title">CONCEPT <span>PROJECT WORKSPACE</span></h1>
            <p class="subtitle">Complete Workflow Management System</p>
            <p class="subtitle-ar">نظام إدارة سير العمل الكامل</p>
        </header>

        <div class="glow-divider"></div>

        <section class="animate-up delay-1" style="margin-bottom: 60px;">
            <h2 class="section-title">Company Hierarchy</h2>
            <div class="section-title-ar">الهيكل التنظيمي للشركة</div>
            <div class="grid-5">
                <div class="glass-card hierarchy-card">
                    <div class="rank-badge">1</div>
                    <div class="avatar">BA</div>
                    <div class="name">BASSEM ABU ELASAAD</div>
                    <div class="role">Owner / Founder</div>
                    <div class="role-ar">صاحب الشركة</div>
                </div>
                <div class="glass-card hierarchy-card">
                    <div class="rank-badge">2</div>
                    <div class="avatar">YA</div>
                    <div class="name">YASSER ABU ELASAAD</div>
                    <div class="role">Chairman Of The Board</div>
                    <div class="role-ar">رئيس مجلس الإدارة</div>
                </div>
                <div class="glass-card hierarchy-card">
                    <div class="rank-badge">3</div>
                    <div class="avatar">RA</div>
                    <div class="name">RAHMA ABU ELASAAD</div>
                    <div class="role">Vice Chairman Of The Board</div>
                    <div class="role-ar">نائب رئيس مجلس الإدارة</div>
                </div>
                <div class="glass-card hierarchy-card">
                    <div class="rank-badge">4</div>
                    <div class="avatar">AE</div>
                    <div class="name">AHMED ELMAHDY</div>
                    <div class="role">General Manager + HR</div>
                    <div class="role-ar">مدير الشركة + الموارد البشرية</div>
                </div>
                <div class="glass-card hierarchy-card glass-card-strong" style="border-color: var(--purple-glow);">
                    <div class="rank-badge">5</div>
                    <div class="avatar" style="border-color: var(--purple-glow); color: var(--purple-glow); box-shadow: 0 0 25px rgba(184,41,221,0.3);">ME</div>
                    <div class="name">MOHAMED ELGEYAR</div>
                    <div class="role neon-purple">Technical Director</div>
                    <div class="role-ar">المدير التقني</div>
                </div>
            </div>
        </section>

        <section class="animate-up delay-2" style="margin-bottom: 60px;">
            <div class="glass-card glass-card-strong" style="border-left: 3px solid var(--purple-glow); border-right: 3px solid var(--purple-glow);">
                <h3 style="font-family: 'Orbitron', 'Cairo', sans-serif; font-size: 13px; color: var(--purple-glow); margin-bottom: 8px; letter-spacing: 2px; text-align: center;">TECHNICAL DIRECTOR RESPONSIBILITIES</h3>
                <p style="font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 14px; color: var(--text-gray); text-align: center; margin-bottom: 20px;">مسؤوليات المدير التقني</p>
                <div class="grid-5">
                    <div style="text-align: center; padding: 14px;">
                        <div style="font-size: 28px; margin-bottom: 10px; filter: drop-shadow(0 0 10px rgba(0,212,255,0.3));">📝</div>
                        <div style="font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; font-weight: 600; color: var(--text-white);">Content Team</div>
                        <div style="font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 4px;">فريق المحتوى</div>
                    </div>
                    <div style="text-align: center; padding: 14px;">
                        <div style="font-size: 28px; margin-bottom: 10px; filter: drop-shadow(0 0 10px rgba(184,41,221,0.3));">🎨</div>
                        <div style="font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; font-weight: 600; color: var(--text-white);">Graphic Team</div>
                        <div style="font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 4px;">فريق التصميم</div>
                    </div>
                    <div style="text-align: center; padding: 14px;">
                        <div style="font-size: 28px; margin-bottom: 10px; filter: drop-shadow(0 0 10px rgba(255,45,149,0.3));">🎬</div>
                        <div style="font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; font-weight: 600; color: var(--text-white);">Video Editors</div>
                        <div style="font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 4px;">محرري الفيديو</div>
                    </div>
                    <div style="text-align: center; padding: 14px;">
                        <div style="font-size: 28px; margin-bottom: 10px; filter: drop-shadow(0 0 10px rgba(0,212,255,0.3));">🔍</div>
                        <div style="font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; font-weight: 600; color: var(--text-white);">Technical Review</div>
                        <div style="font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 4px;">المراجعة التقنية</div>
                    </div>
                    <div style="text-align: center; padding: 14px;">
                        <div style="font-size: 28px; margin-bottom: 10px; filter: drop-shadow(0 0 10px rgba(184,41,221,0.3));">💡</div>
                        <div style="font-family: 'Rajdhani', 'Tajawal', sans-serif; font-size: 13px; font-weight: 600; color: var(--text-white);">Creative Direction</div>
                        <div style="font-family: 'Cairo', 'Tajawal', sans-serif; font-size: 12px; color: var(--text-gray); margin-top: 4px;">التوجيه الإبداعي</div>
                    </div>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-2" style="margin-bottom: 60px;">
            <h2 class="section-title">Departments & Team Members</h2>
            <div class="section-title-ar">الأقسام وأعضاء الفريق</div>
            <div class="team-grid">
                <div class="glass-card team-card">
                    <div class="dept-name">Content Team</div>
                    <div class="dept-name-ar">فريق المحتوى</div>
                    <div class="member-avatar">AE</div>
                    <div class="member-name">Amira Eid</div>
                    <div class="member-role">Content Creator</div>
                    <div class="member-role-ar">مُنشئ محتوى</div>
                    <div class="member-row" style="margin-top: 14px; padding-top: 14px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="member-avatar">RK</div>
                        <div class="member-name">Reem Khater</div>
                        <div class="member-role">Content Creator</div>
                        <div class="member-role-ar">مُنشئ محتوى</div>
                    </div>
                </div>
                <div class="glass-card team-card">
                    <div class="dept-name">Creative Team</div>
                    <div class="dept-name-ar">فريق الإبداع</div>
                    <div class="member-avatar">N</div>
                    <div class="member-name">Nosyla</div>
                    <div class="member-role">Graphic Designer</div>
                    <div class="member-role-ar">مصممة جرافيك</div>
                </div>
                <div class="glass-card team-card">
                    <div class="dept-name">Post Production</div>
                    <div class="dept-name-ar">ما بعد الإنتاج</div>
                    <div class="member-avatar">ME</div>
                    <div class="member-name">Mohamed Elnabrawy</div>
                    <div class="member-role">Video Editor</div>
                    <div class="member-role-ar">محرر فيديو</div>
                    <div class="member-row" style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="member-name">Mohamed Nabil</div>
                        <div class="member-role">Video Editor</div>
                        <div class="member-role-ar">محرر فيديو</div>
                    </div>
                    <div class="member-row" style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="member-name">Mohamed Ayman</div>
                        <div class="member-role">Video Editor</div>
                        <div class="member-role-ar">محرر فيديو</div>
                    </div>
                </div>
                <div class="glass-card team-card">
                    <div class="dept-name">Videography Team</div>
                    <div class="dept-name-ar">فريق التصوير</div>
                    <div class="member-avatar">AE</div>
                    <div class="member-name">Abdallah Elbeily</div>
                    <div class="member-role">Videographer</div>
                    <div class="member-role-ar">مصور فيديو</div>
                    <div class="member-row" style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="member-name">Nour</div>
                        <div class="member-role">Reels Photographer</div>
                        <div class="member-role-ar">مصورة ريلز</div>
                    </div>
                    <div class="member-row" style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="member-name">Youssef Talaat</div>
                        <div class="member-role">Photographer</div>
                        <div class="member-role-ar">مصور</div>
                    </div>
                </div>
                <div class="glass-card team-card">
                    <div class="dept-name">Media Team</div>
                    <div class="dept-name-ar">فريق الإعلانات</div>
                    <div class="member-avatar">YN</div>
                    <div class="member-name">Youssef Nabil</div>
                    <div class="member-role">Media Buyer</div>
                    <div class="member-role-ar">مشتر إعلانات</div>
                </div>
                <div class="glass-card team-card">
                    <div class="dept-name">Moderation</div>
                    <div class="dept-name-ar">الإشراف</div>
                    <div class="member-avatar">AK</div>
                    <div class="member-name">Amira Khairy</div>
                    <div class="member-role">Moderator</div>
                    <div class="member-role-ar">مشرفة</div>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-3" style="margin-bottom: 60px;">
            <h2 class="section-title">Workflow Process</h2>
            <div class="section-title-ar">مسار سير العمل</div>
            <div class="glass-card glass-card-strong" style="padding: 40px;">
                <div class="workflow-container">
                    <div class="workflow-step"><div class="workflow-node">CLIENT<div class="node-ar">العميل</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">SALES<div class="node-ar">المبيعات</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node highlight">TECHNICAL DIRECTOR<div class="node-ar">المدير التقني</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">CONTENT TEAM<div class="node-ar">فريق المحتوى</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">STRATEGY<div class="node-ar">الاستراتيجية</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">CONTENT PLAN<div class="node-ar">خطة المحتوى</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">CREATIVE DIRECTION<div class="node-ar">التوجيه الإبداعي</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">ACCOUNT MANAGER<div class="node-ar">مدير الحساب</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">PRODUCTION TEAM<div class="node-ar">فريق الإنتاج</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-branch">
                        <div class="branch-item">GRAPHIC DESIGN<div class="item-ar">التصميم الجرافيكي</div></div>
                        <div class="branch-item">VIDEO EDITING<div class="item-ar">تحرير الفيديو</div></div>
                    </div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node highlight">TECHNICAL REVIEW<div class="node-ar">المراجعة التقنية</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">CLIENT APPROVAL<div class="node-ar">موافقة العميل</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">MODERATOR<div class="node-ar">المشرف</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">PUBLISHING<div class="node-ar">النشر</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">MEDIA BUYER<div class="node-ar">مشتر الإعلانات</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">ADS OPTIMIZATION<div class="node-ar">تحسين الإعلانات</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node">MONTHLY REPORT<div class="node-ar">التقرير الشهري</div></div></div>
                    <div class="workflow-arrow"></div>
                    <div class="workflow-step"><div class="workflow-node" style="border-color: var(--purple-glow); background: linear-gradient(135deg, rgba(184,41,221,0.2), rgba(0,212,255,0.2));">NEXT MONTH<div class="node-ar">الشهر التالي</div></div></div>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-3" style="margin-bottom: 60px;">
            <h2 class="section-title">Handover Map</h2>
            <div class="section-title-ar">خريطة التسليم</div>
            <div class="handover-grid">
                <div class="glass-card handover-card">
                    <div class="dept-title">SALES</div>
                    <div class="dept-title-ar">المبيعات</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">العميل</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">المدير التقني</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Client</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Technical Director</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">TECHNICAL DIRECTOR</div>
                    <div class="dept-title-ar">المدير التقني</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">المبيعات</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">فريق المحتوى</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Sales</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Content Team</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">CONTENT TEAM</div>
                    <div class="dept-title-ar">فريق المحتوى</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">المدير التقني</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">مدير الحساب</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Technical Director</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Account Manager</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">ACCOUNT MANAGER</div>
                    <div class="dept-title-ar">مدير الحساب</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">فريق المحتوى</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">الفريق التقني</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Content Team</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Technical Team</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">PRODUCTION TEAM</div>
                    <div class="dept-title-ar">فريق الإنتاج</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">التقني</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">تصميم + فيديو</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Technical</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Graphic + Video</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">GRAPHIC DESIGNER</div>
                    <div class="dept-title-ar">مصمم الجرافيك</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">الإنتاج</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">المراجعة التقنية</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Production</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Technical Review</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">VIDEO EDITORS</div>
                    <div class="dept-title-ar">محرري الفيديو</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">الإنتاج</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">المراجعة التقنية</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Production</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Technical Review</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">TECHNICAL REVIEW</div>
                    <div class="dept-title-ar">المراجعة التقنية</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">تصميم + فيديو</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">مدير الحساب</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Graphic + Video</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Account Manager</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">MODERATOR</div>
                    <div class="dept-title-ar">المشرف</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">محتوى معتمد</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">مشتر الإعلانات</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Approved Content</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Media Buyer</span></div>
                    </div>
                </div>
                <div class="glass-card handover-card">
                    <div class="dept-title">MEDIA BUYER</div>
                    <div class="dept-title-ar">مشتر الإعلانات</div>
                    <div class="handover-flow">
                        <div class="handover-item"><span class="label-ar">يستلم من</span><span class="handover-arrow">←</span><span class="value-ar">المشرف</span></div>
                        <div class="handover-item"><span class="label-ar">يسلم إلى</span><span class="handover-arrow">←</span><span class="value-ar">التقرير الشهري</span></div>
                    </div>
                    <div style="margin-top: 10px; padding-top: 10px; border-top: 1px solid rgba(255,255,255,0.05);">
                        <div class="handover-item"><span class="label">Receive</span><span class="handover-arrow">→</span><span class="value">Moderator</span></div>
                        <div class="handover-item"><span class="label">Deliver</span><span class="handover-arrow">→</span><span class="value">Monthly Report</span></div>
                    </div>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-4" style="margin-bottom: 60px;">
            <h2 class="section-title">Monthly Calendar</h2>
            <div class="section-title-ar">التقويم الشهري</div>
            <div class="calendar-grid">
                <div class="glass-card week-card">
                    <div class="week-title">WEEK 1</div>
                    <div class="week-title-ar">الأسبوع الأول</div>
                    <ul class="task-list">
                        <li class="task-item">Client Meeting<span class="task-ar">اجتماع العميل</span></li>
                        <li class="task-item">Research<span class="task-ar">البحث</span></li>
                        <li class="task-item">Strategy<span class="task-ar">الاستراتيجية</span></li>
                        <li class="task-item">Brand Analysis<span class="task-ar">تحليل العلامة</span></li>
                        <li class="task-item">Competitors<span class="task-ar">المنافسين</span></li>
                        <li class="task-item">Target Audience<span class="task-ar">الجمهور المستهدف</span></li>
                    </ul>
                </div>
                <div class="glass-card week-card">
                    <div class="week-title">WEEK 2</div>
                    <div class="week-title-ar">الأسبوع الثاني</div>
                    <ul class="task-list">
                        <li class="task-item">Content Plan<span class="task-ar">خطة المحتوى</span></li>
                        <li class="task-item">Creative Direction<span class="task-ar">التوجيه الإبداعي</span></li>
                        <li class="task-item">Script Writing<span class="task-ar">كتابة السكريبت</span></li>
                        <li class="task-item">Design Direction<span class="task-ar">توجيه التصميم</span></li>
                        <li class="task-item">Book Shooting<span class="task-ar">حجز التصوير</span></li>
                    </ul>
                </div>
                <div class="glass-card week-card">
                    <div class="week-title">WEEK 3</div>
                    <div class="week-title-ar">الأسبوع الثالث</div>
                    <ul class="task-list">
                        <li class="task-item">Production<span class="task-ar">الإنتاج</span></li>
                        <li class="task-item">Photography<span class="task-ar">التصوير الفوتوغرافي</span></li>
                        <li class="task-item">Videography<span class="task-ar">تصوير الفيديو</span></li>
                        <li class="task-item">Graphic Design<span class="task-ar">التصميم الجرافيكي</span></li>
                        <li class="task-item">Video Editing<span class="task-ar">تحرير الفيديو</span></li>
                    </ul>
                </div>
                <div class="glass-card week-card">
                    <div class="week-title">WEEK 4</div>
                    <div class="week-title-ar">الأسبوع الرابع</div>
                    <ul class="task-list">
                        <li class="task-item">Technical Review<span class="task-ar">المراجعة التقنية</span></li>
                        <li class="task-item">Client Approval<span class="task-ar">موافقة العميل</span></li>
                        <li class="task-item">Publishing<span class="task-ar">النشر</span></li>
                        <li class="task-item">Media Buying<span class="task-ar">شراء الإعلانات</span></li>
                        <li class="task-item">Optimization<span class="task-ar">التحسين</span></li>
                        <li class="task-item">Monthly Report<span class="task-ar">التقرير الشهري</span></li>
                    </ul>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-4" style="margin-bottom: 60px;">
            <h2 class="section-title">Deadlines</h2>
            <div class="section-title-ar">المواعيد النهائية</div>
            <div class="deadlines-grid">
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Sales</div><div class="task-name-ar">المبيعات</div></div>
                    <span class="time-badge">24 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Technical Analysis</div><div class="task-name-ar">التحليل التقني</div></div>
                    <span class="time-badge">48 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Strategy</div><div class="task-name-ar">الاستراتيجية</div></div>
                    <span class="time-badge">48 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Content Plan</div><div class="task-name-ar">خطة المحتوى</div></div>
                    <span class="time-badge">24 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Creative Direction</div><div class="task-name-ar">التوجيه الإبداعي</div></div>
                    <span class="time-badge">24 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Graphic Design</div><div class="task-name-ar">التصميم الجرافيكي</div></div>
                    <span class="time-badge">48 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Video Editing</div><div class="task-name-ar">تحرير الفيديو</div></div>
                    <span class="time-badge">72 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Technical Review</div><div class="task-name-ar">المراجعة التقنية</div></div>
                    <span class="time-badge">24 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Client Revisions</div><div class="task-name-ar">تعديلات العميل</div></div>
                    <span class="time-badge">48 HRS</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Publishing</div><div class="task-name-ar">النشر</div></div>
                    <span class="time-badge">Calendar</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Media Buying</div><div class="task-name-ar">شراء الإعلانات</div></div>
                    <span class="time-badge">Immediate</span>
                </div>
                <div class="glass-card deadline-card">
                    <div><div class="task-name">Monthly Report</div><div class="task-name-ar">التقرير الشهري</div></div>
                    <span class="time-badge">Last Day</span>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-5" style="margin-bottom: 60px;">
            <h2 class="section-title">Status System</h2>
            <div class="section-title-ar">نظام الحالات</div>
            <div class="glass-card glass-card-strong">
                <div class="status-grid">
                    <div class="status-item">
                        <div class="status-dot" style="background: #3b82f6; color: #3b82f6;"></div>
                        <div><div class="status-label">New Lead</div><div class="status-label-ar">عميل محتمل جديد</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #8b5cf6; color: #8b5cf6;"></div>
                        <div><div class="status-label">Waiting Payment</div><div class="status-label-ar">في انتظار الدفع</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #22c55e; color: #22c55e;"></div>
                        <div><div class="status-label">Onboarding</div><div class="status-label-ar">الانضمام</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #eab308; color: #eab308;"></div>
                        <div><div class="status-label">Strategy</div><div class="status-label-ar">الاستراتيجية</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #f97316; color: #f97316;"></div>
                        <div><div class="status-label">Content Plan</div><div class="status-label-ar">خطة المحتوى</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #ef4444; color: #ef4444;"></div>
                        <div><div class="status-label">Production</div><div class="status-label-ar">الإنتاج</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #a16207; color: #a16207;"></div>
                        <div><div class="status-label">Editing</div><div class="status-label-ar">المونتاج</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #1f2937; color: #1f2937; box-shadow: 0 0 10px #6b7280;"></div>
                        <div><div class="status-label">Technical Review</div><div class="status-label-ar">المراجعة التقنية</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #22c55e; color: #22c55e;"></div>
                        <div><div class="status-label">Client Approval</div><div class="status-label-ar">موافقة العميل</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #3b82f6; color: #3b82f6;"></div>
                        <div><div class="status-label">Scheduled</div><div class="status-label-ar">مجدول</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #ec4899; color: #ec4899;"></div>
                        <div><div class="status-label">Published</div><div class="status-label-ar">منشور</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #06b6d4; color: #06b6d4;"></div>
                        <div><div class="status-label">Running Ads</div><div class="status-label-ar">إعلانات نشطة</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #6366f1; color: #6366f1;"></div>
                        <div><div class="status-label">Monthly Report</div><div class="status-label-ar">التقرير الشهري</div></div>
                    </div>
                    <div class="status-item">
                        <div class="status-dot" style="background: #22c55e; color: #22c55e;"></div>
                        <div><div class="status-label">Completed</div><div class="status-label-ar">مكتمل</div></div>
                    </div>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <section class="animate-up delay-5" style="margin-bottom: 60px;">
            <h2 class="section-title">Folder Structure</h2>
            <div class="section-title-ar">هيكل المجلدات</div>
            <div class="glass-card glass-card-strong">
                <div class="folder-tree">
                    <div class="folder">📁 Client Name <span class="folder-ar">اسم العميل</span></div>
                    <div class="indent">
                        <div class="file">📄 01 Brief <span class="file-ar">الموجز</span></div>
                        <div class="file">📄 02 Contract <span class="file-ar">العقد</span></div>
                        <div class="file">📄 03 Brand Identity <span class="file-ar">هوية العلامة</span></div>
                        <div class="file">📄 04 Strategy <span class="file-ar">الاستراتيجية</span></div>
                        <div class="file">📄 05 Content Plan <span class="file-ar">خطة المحتوى</span></div>
                        <div class="file">📄 06 Creative Direction <span class="file-ar">التوجيه الإبداعي</span></div>
                        <div class="file">📄 07 Shooting <span class="file-ar">التصوير</span></div>
                        <div class="file">📄 08 Raw Videos <span class="file-ar">الفيديوهات الخام</span></div>
                        <div class="file">📄 09 Photos <span class="file-ar">الصور</span></div>
                        <div class="file">📄 10 Graphic Design <span class="file-ar">التصميم الجرافيكي</span></div>
                        <div class="file">📄 11 Video Editing <span class="file-ar">تحرير الفيديو</span></div>
                        <div class="file">📄 12 Final Files <span class="file-ar">الملفات النهائية</span></div>
                        <div class="file">📄 13 Published <span class="file-ar">المنشور</span></div>
                        <div class="file">📄 14 Ads <span class="file-ar">الإعلانات</span></div>
                        <div class="file">📄 15 Reports <span class="file-ar">التقارير</span></div>
                    </div>
                </div>
            </div>
        </section>

        <div class="glow-divider"></div>

        <footer class="footer animate-up delay-6">
            <div class="footer-text">
                ONE PLANET<br>
                <span class="highlight">ONE TEAM</span><br>
                INFINITE CREATIVITY
            </div>
            <div class="footer-text-ar">
                كوكب واحد<br>
                <span class="highlight">فريق واحد</span><br>
                إبداع لا نهائي
            </div>
        </footer>
    </div>
</body>
</html>
