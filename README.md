/* Marcadores creativos para el SAI */

.fire-marker {
  position: relative;
  width: 34px;
  height: 42px;
  display: grid;
  place-items: center;
}

.fire-marker .flame {
  font-size: 28px;
  filter: drop-shadow(0 0 6px rgba(255,91,24,.85));
  animation: flamePulse 1s ease-in-out infinite alternate;
  transform-origin: 50% 90%;
}

.fire-marker.medium .flame { font-size: 35px; }
.fire-marker.high .flame { font-size: 43px; }

@keyframes flamePulse {
  from { transform: scale(.92) rotate(-2deg); }
  to   { transform: scale(1.08) rotate(2deg); }
}

/* Incendio crítico: fuego + humo que asciende */
.fire-critical {
  position: relative;
  width: 86px;
  height: 112px;
  pointer-events: none;
}

.fire-critical .flame {
  position: absolute;
  left: 24px;
  bottom: 3px;
  font-size: 50px;
  z-index: 4;
  filter: drop-shadow(0 0 10px rgba(255,71,22,.95));
  animation: criticalFlame .8s ease-in-out infinite alternate;
}

@keyframes criticalFlame {
  from { transform: scale(.92) rotate(-3deg); }
  to   { transform: scale(1.1) rotate(3deg); }
}

.smoke {
  position: absolute;
  bottom: 46px;
  border-radius: 50%;
  background:
    radial-gradient(circle at 35% 35%, rgba(230,235,238,.55), rgba(105,111,116,.28) 55%, rgba(30,35,40,0) 72%);
  filter: blur(1px);
  opacity: 0;
  z-index: 3;
}

.smoke.s1 { width: 27px; height: 27px; left: 24px; animation: smokeUp 3.2s ease-out infinite; }
.smoke.s2 { width: 34px; height: 34px; left: 42px; bottom: 50px; animation: smokeUp 3.2s 1.05s ease-out infinite; }
.smoke.s3 { width: 23px; height: 23px; left: 11px; bottom: 49px; animation: smokeUp 3.2s 1.7s ease-out infinite; }
.smoke.s4 { width: 40px; height: 40px; left: 27px; bottom: 62px; animation: smokeUp 3.2s 2.2s ease-out infinite; }

@keyframes smokeUp {
  0%   { transform: translate(0, 10px) scale(.45); opacity: 0; }
  15%  { opacity: .55; }
  55%  { opacity: .30; }
  100% { transform: translate(20px, -58px) scale(1.55); opacity: 0; }
}

.leaflet-div-icon.fire-div-icon,
.leaflet-div-icon.critical-div-icon {
  background: transparent;
  border: 0;
}
