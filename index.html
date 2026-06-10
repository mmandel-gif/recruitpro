import { useState, useEffect, useRef } from "react";

const COLORS = {
  primary: "#1a1a2e",
  accent: "#e94560",
  gold: "#f5a623",
  surface: "#16213e",
  card: "#0f3460",
  text: "#eaeaea",
  muted: "#8892a4",
  success: "#2ecc71",
  danger: "#e74c3c",
  warning: "#f39c12",
  border: "rgba(255,255,255,0.1)",
};

const APTITUDE_QUESTIONS = [
  { q: "What is 15% of 200?", opts: ["25", "30", "35", "40"], ans: 1 },
  { q: "If a train travels 60km/h for 2.5 hours, how far does it go?", opts: ["120 km", "150 km", "180 km", "200 km"], ans: 1 },
  { q: "Which word means the opposite of 'benevolent'?", opts: ["Kind", "Malevolent", "Generous", "Gentle"], ans: 1 },
  { q: "Complete: 2, 6, 12, 20, __", opts: ["28", "30", "32", "36"], ans: 1 },
  { q: "If A=1, B=2... what does 'CAB' sum to?", opts: ["5", "6", "7", "8"], ans: 1 },
  { q: "A shopkeeper buys at ₹80 and sells at ₹100. Profit %?", opts: ["20%", "25%", "15%", "30%"], ans: 1 },
  { q: "Find the odd one out: Apple, Mango, Potato, Banana", opts: ["Apple", "Mango", "Potato", "Banana"], ans: 2 },
  { q: "If 5 workers finish a job in 10 days, 10 workers finish in?", opts: ["20 days", "5 days", "8 days", "2 days"], ans: 1 },
  { q: "Which is largest: 3/4, 2/3, 5/8, 7/10?", opts: ["2/3", "5/8", "3/4", "7/10"], ans: 2 },
  { q: "DIRECTOR is to FILM as AUTHOR is to?", opts: ["Pen", "Book", "Story", "Library"], ans: 1 },
  { q: "Simplify: √144 + √81", opts: ["21", "20", "23", "25"], ans: 0 },
  { q: "A is B's sister. B is C's brother. C is D's son. A is D's?", opts: ["Son", "Daughter", "Nephew", "Granddaughter"], ans: 1 },
  { q: "If today is Wednesday, what day is 100 days later?", opts: ["Monday", "Tuesday", "Friday", "Thursday"], ans: 3 },
  { q: "Synonym of 'Diligent':", opts: ["Lazy", "Hardworking", "Careless", "Quick"], ans: 1 },
  { q: "Speed of 72 km/h in m/s?", opts: ["18 m/s", "20 m/s", "25 m/s", "30 m/s"], ans: 1 },
];

const TYPING_PASSAGE = "The quick brown fox jumps over the lazy dog near the river bank where the children play every evening after school. Good communication skills are essential in today's competitive job market. Every candidate must demonstrate their ability to work under pressure and deliver results consistently. Hard work and dedication always pay off in the long run.";

function generateCredentials(pan) {
  const username = pan.trim().toUpperCase(); // PAN is the username
  const password = `Rec@${Math.floor(100 + Math.random() * 900)}`;
  return { username, password };
}

// ─── Shared CSV helpers ───────────────────────────────────────────────────────
function buildCSV(rows, panelists = []) {
  const headers = ["Date","Name","Mobile","DOB","Gender","Graduation","Interview Location","Refer By","Emp ID","Rejoiner","PAN","Aadhaar","Resume","User ID","Addr Line 1","Addr Line 2","Landmark","City","State","Pincode","Apt Score","Apt Passed","Typing WPM","Typing Accuracy","Typing Passed","Panel Status","Panel Remark","Assigned Panelist","Duplicate Flagged","Registered At","Apt Completed At","Typing Completed At","Panel Decided At"];
  const esc = v => `"${String(v ?? "").replace(/"/g,'""')}"`;
  const csvRows = rows.map(c => {
    const pan = panelists.find(p => p.id === c.assignedPanelistId);
    return [
      localDateOf(c.registeredAt), c.name, c.mobile,
      c.dob||"", c.gender||"", c.graduationDone||"", c.interviewLocation||"", c.referBy, c.empId||"", c.isRejoiner, c.pan,
      c.aadhaar.slice(0,4)+"XXXX"+c.aadhaar.slice(-4),
      c.resume||"", c.username,
      c.addr1||"", c.addr2||"", c.landmark||"", c.city||"", c.state||"", c.pincode||"",
      c.aptScore??"",(c.aptScore!=null?(c.aptScore>=10?"Yes":"No"):""),
      c.typingScore?.wpm??"", c.typingScore?.accuracy??"",
      c.typingScore?(c.typingScore.passed?"Yes":"No"):"",
      c.panelStatus, c.panelRemark||"", pan?.username||"",
      c.duplicateFlagged?"Yes":"No",
      fmtTs(c.registeredAt), fmtTs(c.aptCompletedAt),
      fmtTs(c.typingCompletedAt), fmtTs(c.panelDecidedAt),
    ].map(esc).join(",");
  });
  return [headers.map(esc).join(","), ...csvRows].join("\n");
}

function downloadCSV(rows, filename, panelists = []) {
  if (!rows.length) return;
  const csv = buildCSV(rows, panelists);
  const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url; a.download = filename; a.click();
  URL.revokeObjectURL(url);
}

// Small reusable download button
function DownloadBtn({ rows, filename, panelists = [], label, disabled }) {
  const [flash, setFlash] = useState(false);
  function handle() {
    if (!rows.length || disabled) return;
    downloadCSV(rows, filename, panelists);
    setFlash(true);
    setTimeout(() => setFlash(false), 1800);
  }
  return (
    <button
      onClick={handle}
      disabled={!rows.length || disabled}
      style={{
        display: "inline-flex", alignItems: "center", gap: 6,
        background: flash ? "rgba(46,204,113,0.2)" : "rgba(46,204,113,0.12)",
        border: `1px solid ${flash ? COLORS.success : "rgba(46,204,113,0.35)"}`,
        borderRadius: 8, padding: "7px 14px",
        color: rows.length ? COLORS.success : COLORS.muted,
        cursor: rows.length ? "pointer" : "not-allowed",
        fontSize: 12, fontWeight: 700, whiteSpace: "nowrap",
        opacity: rows.length ? 1 : 0.5,
        transition: "all 0.2s",
      }}
    >
      {flash ? "✓ Downloaded!" : `⬇ ${label || "Download CSV"} (${rows.length})`}
    </button>
  );
}

// Inject responsive styles
if (typeof document !== "undefined" && !document.getElementById("recruitpro-spin")) {
  const style = document.createElement("style");
  style.id = "recruitpro-spin";
  style.textContent = `
    @keyframes spin { to { transform: rotate(360deg); } }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }
    *, *::before, *::after { box-sizing: border-box; }
    html, body { margin: 0; padding: 0; overflow-x: hidden; }
    img, video, canvas { max-width: 100%; }
    .rp-modal-inner { overflow-y: auto; max-height: 90vh; }
  `;
  document.head.appendChild(style);
}

const s = {
  page: { minHeight: "100vh", background: COLORS.primary, color: COLORS.text, fontFamily: "'Segoe UI', system-ui, sans-serif", display: "flex", flexDirection: "column", alignItems: "center", justifyContent: "flex-start", padding: "16px 12px" },
  card: { background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: "20px 16px", width: "100%", maxWidth: 580, boxSizing: "border-box" },
  wideCard: { background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: "20px 16px", width: "100%", maxWidth: 900, boxSizing: "border-box" },
  logo: { display: "flex", alignItems: "center", gap: 10, marginBottom: 20 },
  logoText: { fontSize: 20, fontWeight: 700, color: COLORS.text, letterSpacing: -0.5 },
  logoAccent: { color: COLORS.accent },
  h1: { fontSize: 20, fontWeight: 700, margin: "0 0 4px", color: COLORS.text },
  h2: { fontSize: 17, fontWeight: 600, margin: "0 0 16px", color: COLORS.text },
  sub: { fontSize: 13, color: COLORS.muted, margin: "0 0 18px" },
  label: { display: "block", fontSize: 13, color: COLORS.muted, marginBottom: 6, fontWeight: 500 },
  input: { width: "100%", background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 10, padding: "10px 12px", color: COLORS.text, fontSize: 14, boxSizing: "border-box", outline: "none", marginBottom: 14 },
  select: { width: "100%", background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 10, padding: "10px 12px", color: COLORS.text, fontSize: 14, boxSizing: "border-box", outline: "none", marginBottom: 14, appearance: "none" },
  btn: { width: "100%", background: COLORS.accent, border: "none", borderRadius: 10, padding: "12px", color: "#fff", fontSize: 15, fontWeight: 600, cursor: "pointer", marginTop: 6 },
  btnOut: { width: "100%", background: "transparent", border: `1px solid ${COLORS.border}`, borderRadius: 10, padding: "12px", color: COLORS.text, fontSize: 14, fontWeight: 500, cursor: "pointer", marginTop: 8 },
  chip: (c) => ({ display: "inline-block", background: c || COLORS.card, borderRadius: 20, padding: "4px 12px", fontSize: 12, fontWeight: 600, marginRight: 6 }),
  row: { display: "flex", gap: 10, flexWrap: "wrap" },
  col: { flex: 1, minWidth: 0 },
  divider: { border: "none", borderTop: `1px solid ${COLORS.border}`, margin: "18px 0" },
  alert: (type) => ({ background: type === "success" ? "rgba(46,204,113,0.12)" : type === "danger" ? "rgba(231,76,60,0.12)" : "rgba(243,156,18,0.12)", border: `1px solid ${type === "success" ? COLORS.success : type === "danger" ? COLORS.danger : COLORS.warning}`, borderRadius: 10, padding: "12px 14px", marginBottom: 14, fontSize: 13 }),
  navTabs: { display: "flex", gap: 2, marginBottom: 20, borderBottom: `1px solid ${COLORS.border}`, paddingBottom: 0, flexWrap: "wrap", overflowX: "auto" },
  tab: (active) => ({ padding: "8px 12px", fontSize: 12, fontWeight: 500, cursor: "pointer", background: "none", border: "none", color: active ? COLORS.accent : COLORS.muted, borderBottom: active ? `2px solid ${COLORS.accent}` : "2px solid transparent", marginBottom: -1, whiteSpace: "nowrap", flexShrink: 0 }),
  badge: (c) => ({ display: "inline-flex", alignItems: "center", gap: 4, background: c === "approved" ? "rgba(46,204,113,0.15)" : c === "rejected" ? "rgba(231,76,60,0.15)" : "rgba(243,156,18,0.15)", color: c === "approved" ? COLORS.success : c === "rejected" ? COLORS.danger : COLORS.warning, borderRadius: 20, padding: "2px 8px", fontSize: 11, fontWeight: 600 }),
};

// ─── QR + Registration ───────────────────────────────────────────────────────
function QRScreen({ onScan, onLogin }) {
  return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ textAlign: "center", marginBottom: 24 }}>
          <h1 style={s.h1}>Candidate Registration</h1>
          <p style={{ ...s.sub, margin: "8px 0 28px" }}>Scan this QR code to begin your application</p>
          <div style={{ display: "inline-block", background: "#fff", borderRadius: 16, padding: 18, margin: "0 auto 24px" }}>
            <svg width="160" height="160" viewBox="0 0 160 160">
              {[...Array(16)].map((_, i) => [...Array(16)].map((_, j) => {
                const v = (i + j + i * j) % 3 === 0 || (i < 5 && j < 5) || (i < 5 && j > 10) || (i > 10 && j < 5);
                return v ? <rect key={`${i}-${j}`} x={j * 10} y={i * 10} width={9} height={9} fill="#1a1a2e" rx={1} /> : null;
              }))}
              <rect x="5" y="5" width="40" height="40" fill="none" stroke="#1a1a2e" strokeWidth="3" rx="4" />
              <rect x="115" y="5" width="40" height="40" fill="none" stroke="#1a1a2e" strokeWidth="3" rx="4" />
              <rect x="5" y="115" width="40" height="40" fill="none" stroke="#1a1a2e" strokeWidth="3" rx="4" />
              <rect x="18" y="18" width="14" height="14" fill="#1a1a2e" rx="2" />
              <rect x="128" y="18" width="14" height="14" fill="#1a1a2e" rx="2" />
              <rect x="18" y="128" width="14" height="14" fill="#1a1a2e" rx="2" />
            </svg>
          </div>
          <p style={{ fontSize: 13, color: COLORS.muted, marginBottom: 24 }}>Point your phone camera at the QR code above</p>
          <button style={s.btn} onClick={onScan}>► Simulate QR Scan / Open Form</button>
          <p style={{ marginTop: 18, fontSize: 13, color: COLORS.muted }}>
            Already registered?{" "}
            <span onClick={onLogin} style={{ color: COLORS.accent, cursor: "pointer", fontWeight: 600 }}>Go to Login →</span>
          </p>
        </div>
      </div>
    </div>
  );
}

// ─── PhotoCapture Component ───────────────────────────────────────────────────
function PhotoCapture({ photoData, photoName, error, onCapture, onError }) {
  const [mode, setMode] = useState("idle"); // idle | camera | preview
  const [stream, setStream] = useState(null);
  const [camError, setCamError] = useState(null);
  const [countdown, setCountdown] = useState(null);
  const videoRef = useRef(null);
  const canvasRef = useRef(null);
  const fileInputRef = useRef(null);

  // Start front camera
  async function startCamera() {
    setCamError(null);
    try {
      const s = await navigator.mediaDevices.getUserMedia({
        video: { facingMode: "user", width: { ideal: 640 }, height: { ideal: 480 } }
      });
      setStream(s);
      setMode("camera");
      // Attach stream to video after render
      setTimeout(() => {
        if (videoRef.current) {
          videoRef.current.srcObject = s;
          videoRef.current.play();
        }
      }, 100);
    } catch (err) {
      setCamError(err.name === "NotAllowedError"
        ? "Camera permission denied. Please allow camera access and try again."
        : "Could not access camera. Please upload a photo instead.");
    }
  }

  function stopCamera() {
    stream?.getTracks().forEach(t => t.stop());
    setStream(null);
    setMode("idle");
    setCamError(null);
    setCountdown(null);
  }

  // Take selfie with 3-second countdown
  function triggerCapture() {
    setCountdown(3);
    let n = 3;
    const timer = setInterval(() => {
      n--;
      if (n > 0) setCountdown(n);
      else {
        clearInterval(timer);
        setCountdown(null);
        takeSelfie();
      }
    }, 1000);
  }

  function takeSelfie() {
    const video = videoRef.current;
    const canvas = canvasRef.current;
    if (!video || !canvas) return;
    canvas.width = video.videoWidth || 640;
    canvas.height = video.videoHeight || 480;
    const ctx = canvas.getContext("2d");
    // Mirror the image (front camera)
    ctx.translate(canvas.width, 0);
    ctx.scale(-1, 1);
    ctx.drawImage(video, 0, 0);
    const dataUrl = canvas.toDataURL("image/jpeg", 0.85);
    stopCamera();
    onCapture(dataUrl, "selfie.jpg");
  }

  // File upload handler
  function handleFile(file) {
    if (!file) return;
    if (file.size > 2 * 1024 * 1024) { onError("Photo must be under 2MB"); return; }
    const reader = new FileReader();
    reader.onload = ev => onCapture(ev.target.result, file.name);
    reader.readAsDataURL(file);
  }

  // Cleanup on unmount
  useEffect(() => () => stream?.getTracks().forEach(t => t.stop()), [stream]);

  return (
    <div style={{ marginBottom: 4 }}>
      {/* ── Camera Mode ── */}
      {mode === "camera" && (
        <div style={{ background: COLORS.card, borderRadius: 14, overflow: "hidden", border: `2px solid ${COLORS.accent}`, marginBottom: 0 }}>
          {/* Video viewfinder */}
          <div style={{ position: "relative", background: "#000" }}>
            <video
              ref={videoRef}
              autoPlay
              playsInline
              muted
              style={{ width: "100%", maxHeight: 300, objectFit: "cover", display: "block", transform: "scaleX(-1)" }}
            />
            {/* Face guide oval */}
            <div style={{ position: "absolute", inset: 0, display: "flex", alignItems: "center", justifyContent: "center", pointerEvents: "none" }}>
              <div style={{ width: 140, height: 180, border: `3px dashed rgba(233,69,96,0.7)`, borderRadius: "50%", boxShadow: "0 0 0 9999px rgba(0,0,0,0.35)" }} />
            </div>
            {/* Countdown overlay */}
            {countdown !== null && (
              <div style={{ position: "absolute", inset: 0, display: "flex", alignItems: "center", justifyContent: "center", background: "rgba(0,0,0,0.4)" }}>
                <div style={{ fontSize: 80, fontWeight: 900, color: "#fff", lineHeight: 1 }}>{countdown}</div>
              </div>
            )}
            {/* Instructions */}
            <div style={{ position: "absolute", bottom: 8, left: 0, right: 0, textAlign: "center", fontSize: 12, color: "rgba(255,255,255,0.8)" }}>
              Align your face in the oval · Look straight at the camera
            </div>
          </div>

          {/* Camera controls */}
          <div style={{ display: "flex", gap: 10, padding: 14, alignItems: "center", justifyContent: "space-between" }}>
            <button onClick={stopCamera} style={{ background: "rgba(231,76,60,0.15)", border: `1px solid rgba(231,76,60,0.4)`, borderRadius: 8, padding: "8px 16px", color: COLORS.danger, cursor: "pointer", fontSize: 13, fontWeight: 600 }}>✕ Cancel</button>
            <button
              onClick={triggerCapture}
              disabled={countdown !== null}
              style={{ flex: 1, background: countdown !== null ? COLORS.card : COLORS.accent, border: "none", borderRadius: 10, padding: "12px", color: "#fff", cursor: countdown !== null ? "default" : "pointer", fontSize: 15, fontWeight: 700, display: "flex", alignItems: "center", justifyContent: "center", gap: 8 }}
            >
              {countdown !== null ? `📸 Taking in ${countdown}…` : "📸 Take Selfie"}
            </button>
          </div>
          <canvas ref={canvasRef} style={{ display: "none" }} />
        </div>
      )}

      {/* ── Idle / Preview Mode ── */}
      {mode !== "camera" && (
        <div style={{ background: COLORS.card, border: `2px dashed ${error ? COLORS.danger : photoData ? COLORS.success : COLORS.border}`, borderRadius: 12, padding: 16, transition: "border-color 0.2s" }}>
          {photoData ? (
            /* Photo preview */
            <div style={{ display: "flex", alignItems: "center", gap: 16 }}>
              <div style={{ position: "relative", flexShrink: 0 }}>
                <img src={photoData} alt="Preview" style={{ width: 80, height: 80, borderRadius: "50%", objectFit: "cover", border: `3px solid ${COLORS.success}` }} />
                <div style={{ position: "absolute", bottom: 0, right: 0, width: 22, height: 22, background: COLORS.success, borderRadius: "50%", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 12 }}>✓</div>
              </div>
              <div style={{ flex: 1 }}>
                <div style={{ color: COLORS.success, fontWeight: 600, fontSize: 14, marginBottom: 4 }}>
                  {photoName === "selfie.jpg" ? "Selfie captured" : "Photo uploaded"}
                </div>
                <div style={{ color: COLORS.muted, fontSize: 12, marginBottom: 10 }}>{photoName}</div>
                {/* Retake options */}
                <div style={{ display: "flex", gap: 8 }}>
                  <button onClick={startCamera} style={{ background: "rgba(233,69,96,0.1)", border: `1px solid rgba(233,69,96,0.3)`, borderRadius: 7, padding: "5px 12px", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600 }}>📷 Retake Selfie</button>
                  <button onClick={() => fileInputRef.current?.click()} style={{ background: COLORS.surface, border: `1px solid ${COLORS.border}`, borderRadius: 7, padding: "5px 12px", color: COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600 }}>🖼 Change File</button>
                </div>
              </div>
            </div>
          ) : (
            /* Upload options */
            <div>
              {camError && (
                <div style={{ background: "rgba(231,76,60,0.1)", border: `1px solid rgba(231,76,60,0.3)`, borderRadius: 8, padding: "10px 12px", marginBottom: 12, fontSize: 12, color: COLORS.danger }}>⚠️ {camError}</div>
              )}
              <div style={{ textAlign: "center", marginBottom: 14 }}>
                <div style={{ width: 60, height: 60, borderRadius: "50%", background: "rgba(233,69,96,0.1)", border: `2px dashed ${COLORS.accent}55`, display: "flex", alignItems: "center", justifyContent: "center", margin: "0 auto 8px", fontSize: 24 }}>📷</div>
                <div style={{ fontSize: 14, fontWeight: 600, color: COLORS.text, marginBottom: 3 }}>Add your photo</div>
                <div style={{ fontSize: 12, color: COLORS.muted }}>Clear face · Plain background · Max 2MB</div>
              </div>
              <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10 }}>
                {/* Open Camera */}
                <button
                  onClick={startCamera}
                  style={{ background: "rgba(233,69,96,0.12)", border: `1px solid rgba(233,69,96,0.35)`, borderRadius: 12, padding: "14px 10px", cursor: "pointer", display: "flex", flexDirection: "column", alignItems: "center", gap: 6 }}
                >
                  <span style={{ fontSize: 28 }}>🤳</span>
                  <span style={{ fontSize: 13, fontWeight: 700, color: COLORS.accent }}>Take Selfie</span>
                  <span style={{ fontSize: 11, color: COLORS.muted }}>Front camera</span>
                </button>
                {/* Upload File */}
                <button
                  onClick={() => fileInputRef.current?.click()}
                  style={{ background: COLORS.surface, border: `1px solid ${COLORS.border}`, borderRadius: 12, padding: "14px 10px", cursor: "pointer", display: "flex", flexDirection: "column", alignItems: "center", gap: 6 }}
                >
                  <span style={{ fontSize: 28 }}>🖼️</span>
                  <span style={{ fontSize: 13, fontWeight: 700, color: COLORS.text }}>Upload Photo</span>
                  <span style={{ fontSize: 11, color: COLORS.muted }}>JPG, PNG, WEBP</span>
                </button>
              </div>
            </div>
          )}
          <input ref={fileInputRef} type="file" accept="image/jpeg,image/png,image/jpg,image/webp" style={{ display: "none" }} onChange={e => handleFile(e.target.files[0])} />
        </div>
      )}
    </div>
  );
}

// ─── Registration Form ────────────────────────────────────────────────────────
function RegistrationForm({ onComplete, candidates, setCandidates, alarms, setAlarms }) {
  // ── FAQ gate ──────────────────────────────────────────────────────────────
  const [showFaq, setShowFaq] = useState(true);
  const [faqChecked, setFaqChecked] = useState(false);
  const [panInput, setPanInput] = useState("");
  const [panError, setPanError] = useState("");
  const [panChecked, setPanChecked] = useState(false);
  const [existingCandidate, setExistingCandidate] = useState(null);

  // ── First-time form state ─────────────────────────────────────────────────
  const [step, setStep] = useState(1);
  const [form, setForm] = useState({ name: "", mobile: "", dob: "", referBy: "", empId: "", isRejoiner: "", pan: "", aadhaar: "", resume: null, resumeData: null, photo: null, photoData: null, addr1: "", addr2: "", landmark: "", city: "", state: "", pincode: "", gender: "", graduationDone: "", interviewLocation: "" });
  const [creds, setCreds] = useState(null);
  const [errors, setErrors] = useState({});
  const [dupAlarm, setDupAlarm] = useState(null);
  const [forceAllow, setForceAllow] = useState(false);

  // ── Returning user state ──────────────────────────────────────────────────
  const [retForm, setRetForm] = useState({ mobile: "", email: "", otp: "", dob: "", resume: null, resumeData: null, referBy: "", empId: "" });
  const [retErrors, setRetErrors] = useState({});
  const [retCreds, setRetCreds] = useState(null);
  const [retOtpSent, setRetOtpSent] = useState(false);
  const [retOtpCode, setRetOtpCode] = useState(null);
  const [retOtpExpiry, setRetOtpExpiry] = useState(null);
  const [retOtpVerified, setRetOtpVerified] = useState(false);
  const [retOtpTimeLeft, setRetOtpTimeLeft] = useState(0);
  const [retMobileUpdate, setRetMobileUpdate] = useState(false); // allow updating mobile

  const set = (k, v) => setForm(p => ({ ...p, [k]: v }));
  const setR = (k, v) => setRetForm(p => ({ ...p, [k]: v }));

  // ── Step 0: PAN check ─────────────────────────────────────────────────────
  function checkPan() {
    const pan = panInput.trim().toUpperCase();
    if (!/^[A-Z]{5}\d{4}[A-Z]$/.test(pan)) { setPanError("Invalid PAN format (e.g. ABCDE1234F)"); return; }
    setPanError("");
    const existing = candidates.find(c => c.pan?.toUpperCase() === pan);
    if (existing) { setExistingCandidate(existing); }
    else { setForm(p => ({ ...p, pan })); }
    setPanChecked(true);
  }

  // ── Age helper ────────────────────────────────────────────────────────────
  function calcAge(dob) {
    if (!dob) return null;
    const today = new Date();
    const birth = new Date(dob);
    let age = today.getFullYear() - birth.getFullYear();
    const m = today.getMonth() - birth.getMonth();
    if (m < 0 || (m === 0 && today.getDate() < birth.getDate())) age--;
    return age;
  }

  // ── First-time validation ─────────────────────────────────────────────────
  function validateStep1() {
    const e = {};
    if (!form.name.trim()) e.name = "Name required";
    if (!/^\d{10}$/.test(form.mobile)) e.mobile = "Valid 10-digit mobile required";
    if (!form.dob) {
      e.dob = "Date of birth is required";
    } else {
      const age = calcAge(form.dob);
      if (age === null || age < 18) e.dob = `You must be at least 18 years old to apply${age !== null ? ` (current age: ${age})` : ""}`;
      const birth = new Date(form.dob);
      if (birth > new Date()) e.dob = "Date of birth cannot be in the future";
    }
    if (!form.referBy) e.referBy = "Select how you heard about us";
    if (form.referBy === "referral" && !form.empId.trim()) e.empId = "Employee ID is required for referrals";
    if (!form.gender) e.gender = "Please select your gender";
    if (!form.graduationDone) e.graduationDone = "Please select your graduation status";
    if (!form.interviewLocation) e.interviewLocation = "Please select your interview location";
    if (!form.isRejoiner) e.isRejoiner = "Please select";
    if (!form.addr1.trim()) e.addr1 = "Address Line 1 is required";
    if (!form.city.trim()) e.city = "City is required";
    if (!form.state.trim()) e.state = "State is required";
    if (!/^\d{6}$/.test(form.pincode)) e.pincode = "Valid 6-digit pincode required";
    if (!form.photo) e.photo = "Please upload your current photo";
    setErrors(e); return Object.keys(e).length === 0;
  }

  function validateStep2() {
    const e = {};
    if (!/^\d{12}$/.test(form.aadhaar.replace(/\s/g, ""))) e.aadhaar = "Aadhaar must be 12 digits";
    if (!form.resume) e.resume = "Please upload your resume";
    setErrors(e); return Object.keys(e).length === 0;
  }

  function submitStep1() { if (validateStep1()) setStep(2); }

  function doRegister(flagged = false) {
    const c = generateCredentials(form.pan);
    const candidate = { ...form, ...c, id: Date.now(), registeredAt: localISO(), status: "registered", aptScore: null, aptCompletedAt: null, typingScore: null, typingCompletedAt: null, panelStatus: "pending", panelRemark: "", panelDecidedAt: null, duplicateFlagged: flagged };
    setCandidates(p => [...p, candidate]);
    setCreds(c); setStep(3);
  }

  function submitStep2() {
    if (!validateStep2()) return;
    const hits = checkDuplicates(form, candidates);
    if (hits.length > 0 && !forceAllow) {
      const alarm = { id: Date.now(), date: todayStr(), timestamp: localISO(), attemptedName: form.name, attemptedMobile: form.mobile, hits, resolved: false };
      const updated = [...alarms, alarm];
      setAlarms(updated); saveAlarms(updated);
      setDupAlarm({ hits, alarm }); return;
    }
    doRegister(forceAllow);
  }

  // ── OTP helpers ───────────────────────────────────────────────────────────
  const { useEffect: ue2, useRef: ur2 } = { useEffect, useRef };
  ue2(() => {
    if (!retOtpExpiry) return;
    const t = setInterval(() => {
      const left = Math.max(0, Math.ceil((retOtpExpiry - Date.now()) / 1000));
      setRetOtpTimeLeft(left);
      if (left === 0) clearInterval(t);
    }, 1000);
    return () => clearInterval(t);
  }, [retOtpExpiry]);

  function sendRetOtp() {
    if (!retForm.email.trim() || !/\S+@\S+\.\S+/.test(retForm.email)) {
      setRetErrors(p => ({ ...p, email: "Please enter a valid email address first" })); return;
    }
    const code = Math.floor(100000 + Math.random() * 900000).toString();
    setRetOtpCode(code);
    setRetOtpExpiry(Date.now() + 120000);
    setRetOtpTimeLeft(120);
    setRetOtpSent(true);
    setRetOtpVerified(false);
    setRetErrors(p => ({ ...p, email: null, otp: null }));
  }

  function verifyRetOtp() {
    if (!retForm.otp.trim()) { setRetErrors(p => ({ ...p, otp: "Enter the OTP" })); return; }
    if (Date.now() > retOtpExpiry) { setRetErrors(p => ({ ...p, otp: "OTP expired. Please resend." })); return; }
    if (retForm.otp.trim() !== retOtpCode) { setRetErrors(p => ({ ...p, otp: "Incorrect OTP. Try again." })); return; }
    setRetOtpVerified(true);
    setRetErrors(p => ({ ...p, otp: null }));
  }

  // ── Returning user submit ─────────────────────────────────────────────────
  function submitReturning() {
    const e = {};
    if (!/^\d{10}$/.test(retForm.mobile)) e.mobile = "Valid 10-digit mobile required";
    else if (!retMobileUpdate && retForm.mobile !== existingCandidate.mobile) e.mobile = "Mobile does not match. Check the box below to update it.";
    if (!retForm.email.trim() || !/\S+@\S+\.\S+/.test(retForm.email)) e.email = "Valid email address required";
    if (!retOtpVerified) e.email = "Please verify your email with OTP";
    // DOB — editable, just validate 18+
    const dobToUse = retForm.dob || existingCandidate.dob;
    if (!dobToUse) {
      e.dob = "Please enter your date of birth";
    } else {
      const age = calcAge(dobToUse);
      if (age < 18) e.dob = `Must be at least 18 years old (current age: ${age})`;
    }
    if (!retForm.referBy && !existingCandidate.referBy) e.referBy = "Please select how you heard about us";
    const referByToUse = retForm.referBy || existingCandidate.referBy;
    const empIdToUse = retForm.empId || existingCandidate.empId || "";
    if (referByToUse === "referral" && !empIdToUse.trim()) e.empId = "Employee ID required for referrals";
    setRetErrors(e);
    if (Object.keys(e).length > 0) return;
    const newPwd = `Rec@${Math.floor(100 + Math.random() * 900)}`;
    const newEntry = {
      ...existingCandidate,
      id: Date.now(),
      mobile: retForm.mobile, // always save what was entered (either matched or explicitly updated)
      email: retForm.email,
      dob: dobToUse,
      referBy: referByToUse,
      empId: referByToUse === "referral" ? empIdToUse : "",
      resume: retForm.resume || existingCandidate.resume,
      resumeData: retForm.resumeData || existingCandidate.resumeData,
      password: newPwd,
      registeredAt: localISO(),
      aptScore: null, aptCompletedAt: null,
      typingScore: null, typingCompletedAt: null,
      panelStatus: "pending", panelRemark: "", panelDecidedAt: null,
      isRejoiner: "Yes", passwordResetAt: null,
    };
    setCandidates(p => [...p, newEntry]);
    setRetCreds({ username: existingCandidate.username, password: newPwd });
  }

  // ── FAQ Screen — shown before PAN gate ───────────────────────────────────
  if (showFaq) return (
    <div style={{ ...s.page, alignItems: "center", paddingBottom: 40 }}>
      <Logo />
      <div style={{ ...s.wideCard }}>
        {/* Header */}
        <div style={{ textAlign: "center", marginBottom: 24 }}>
          <div style={{ fontSize: 40, marginBottom: 10 }}>📋</div>
          <h2 style={s.h2}>Frequently Asked Questions</h2>
          <p style={{ ...s.sub, margin: "0 0 0" }}>Please read through the FAQs carefully before proceeding with your registration.</p>
        </div>

        {/* FAQ Sections */}
        <div style={{ display: "flex", flexDirection: "column", gap: 12, marginBottom: 20 }}>

          {/* Role & Salary */}
          <div style={{ background: COLORS.card, borderRadius: 12, overflow: "hidden", border: `1px solid ${COLORS.border}` }}>
            <div style={{ background: "rgba(99,102,241,0.08)", padding: "10px 16px", fontSize: 12, fontWeight: 700, color: "#818cf8", letterSpacing: 0.5 }}>💼 ROLE & COMPENSATION</div>
            <div style={{ padding: "14px 16px", display: "flex", flexDirection: "column", gap: 12 }}>
              {[
                ["What will be my designation?", "Your designation will be Data Verifier."],
                ["What will be my roles and responsibilities?", "Reviewing and verifying data for accuracy and completeness · Validating information based on defined guidelines · Identifying discrepancies and flagging errors · Maintaining quality and productivity targets · Following compliance and process protocols"],
                ["What is the incentive structure?", "The role offers an attractive incentive structure. Incentives are subject to applicable terms and conditions and are awarded at the discretion of management based on performance and business requirements."],
                ["Am I eligible for incentives from the first month?", "Yes."],
              ].map(([q, a]) => (
                <div key={q}>
                  <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 4 }}>Q: {q}</div>
                  <div style={{ fontSize: 13, color: COLORS.muted, lineHeight: 1.6 }}>A: {a}</div>
                </div>
              ))}

              {/* Salary Table */}
              <div>
                <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 8 }}>Q: What will be my salary structure?</div>
                <div style={{ overflowX: "auto" }}>
                  <table style={{ width: "100%", borderCollapse: "collapse", fontSize: 12 }}>
                    <thead>
                      <tr style={{ background: "rgba(99,102,241,0.1)" }}>
                        {["Component", "Gurugram (OG)", "Noida (OE)"].map(h => <th key={h} style={{ padding: "7px 10px", textAlign: "left", color: "#818cf8", fontWeight: 700, borderBottom: `1px solid ${COLORS.border}` }}>{h}</th>)}
                      </tr>
                    </thead>
                    <tbody>
                      {[
                        ["Basic / Gross Salary", "₹18,501", "₹16,868"],
                        ["PF Deduction", "₹1,800", "₹1,800"],
                        ["ESI Deduction", "₹139", "₹127"],
                        ["LWF Deduction", "₹35", "—"],
                        ["✦ In-Hand Salary", "₹16,527", "₹14,941"],
                        ["CTC (Total)", "₹20,972", "₹19,216"],
                      ].map(([label, g, n], i) => (
                        <tr key={label} style={{ background: i % 2 === 0 ? "transparent" : "rgba(255,255,255,0.02)", borderBottom: `1px solid ${COLORS.border}` }}>
                          <td style={{ padding: "7px 10px", color: label.startsWith("✦") ? COLORS.success : COLORS.text, fontWeight: label.startsWith("✦") ? 700 : 400 }}>{label}</td>
                          <td style={{ padding: "7px 10px", color: label.startsWith("✦") ? COLORS.success : COLORS.text, fontWeight: label.startsWith("✦") ? 700 : 400 }}>{g}</td>
                          <td style={{ padding: "7px 10px", color: label.startsWith("✦") ? COLORS.success : COLORS.text, fontWeight: label.startsWith("✦") ? 700 : 400 }}>{n}</td>
                        </tr>
                      ))}
                    </tbody>
                  </table>
                </div>
              </div>
            </div>
          </div>

          {/* Work Conditions */}
          <div style={{ background: COLORS.card, borderRadius: 12, overflow: "hidden", border: `1px solid ${COLORS.border}` }}>
            <div style={{ background: "rgba(46,204,113,0.08)", padding: "10px 16px", fontSize: 12, fontWeight: 700, color: COLORS.success, letterSpacing: 0.5 }}>🕐 WORK CONDITIONS</div>
            <div style={{ padding: "14px 16px", display: "flex", flexDirection: "column", gap: 12 }}>
              {[
                ["What will be my shift and timings?", "Shift timings may vary. Details will be shared during onboarding."],
                ["Is it a weekly Saturday and Sunday off?", "Weekly offs depend on the process schedule. Some roles may have rotational weekly offs instead of fixed Saturdays and Sundays."],
                ["Will I get a cab during the night shift?", "Cab facility for night shifts is provided to Female employees only, as per company policy and location feasibility."],
              ].map(([q, a]) => (
                <div key={q}>
                  <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 4 }}>Q: {q}</div>
                  <div style={{ fontSize: 13, color: COLORS.muted, lineHeight: 1.6 }}>A: {a}</div>
                </div>
              ))}
            </div>
          </div>

          {/* Training */}
          <div style={{ background: COLORS.card, borderRadius: 12, overflow: "hidden", border: `1px solid ${COLORS.border}` }}>
            <div style={{ background: "rgba(243,156,18,0.08)", padding: "10px 16px", fontSize: 12, fontWeight: 700, color: COLORS.warning, letterSpacing: 0.5 }}>📚 TRAINING</div>
            <div style={{ padding: "14px 16px", display: "flex", flexDirection: "column", gap: 12 }}>
              {[
                ["What is the training period?", "The training period typically lasts for 3 months. Exact duration will be communicated during onboarding."],
                ["Can I take leaves during training?", "Leaves during the training period are strictly not permitted, as training is mandatory. Exceptions may be considered in genuine medical cases with prior approval."],
              ].map(([q, a]) => (
                <div key={q}>
                  <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 4 }}>Q: {q}</div>
                  <div style={{ fontSize: 13, color: COLORS.muted, lineHeight: 1.6 }}>A: {a}</div>
                </div>
              ))}
            </div>
          </div>

          {/* Hiring & Rehire */}
          <div style={{ background: COLORS.card, borderRadius: 12, overflow: "hidden", border: `1px solid ${COLORS.border}` }}>
            <div style={{ background: "rgba(52,152,219,0.08)", padding: "10px 16px", fontSize: 12, fontWeight: 700, color: "#3498db", letterSpacing: 0.5 }}>🔄 HIRING & REHIRE</div>
            <div style={{ padding: "14px 16px", display: "flex", flexDirection: "column", gap: 12 }}>
              {[
                ["When is the next hiring drive?", "Hiring drives are conducted based on business requirements. Please stay connected with the recruitment team for updates."],
                ["I have worked with Ocrolus before. Can I be rehired?", "Rehire eligibility depends on your previous tenure, performance, and exit status. The recruitment team will review your profile and confirm."],
              ].map(([q, a]) => (
                <div key={q}>
                  <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 4 }}>Q: {q}</div>
                  <div style={{ fontSize: 13, color: COLORS.muted, lineHeight: 1.6 }}>A: {a}</div>
                </div>
              ))}
            </div>
          </div>

          {/* Onboarding Process */}
          <div style={{ background: COLORS.card, borderRadius: 12, overflow: "hidden", border: `1px solid ${COLORS.border}` }}>
            <div style={{ background: "rgba(233,69,96,0.08)", padding: "10px 16px", fontSize: 12, fontWeight: 700, color: COLORS.accent, letterSpacing: 0.5 }}>✅ ONBOARDING PROCESS (IF SELECTED)</div>
            <div style={{ padding: "14px 16px", display: "flex", flexDirection: "column", gap: 10 }}>
              {[
                ["1. Background Verification (BGV)", "You will receive an email from OnGrid within 48 hours of selection. Complete the verification and upload all required documents within 24 hours. If not received, contact recruitment@ocrolus.com."],
                ["2. Address Details", "Provide your permanent address during BGV. A verification visit may be conducted at your permanent address."],
                ["3. Verification Timeline", "Allow at least 2 weeks for verification to complete after submission."],
                ["4. Offer Letter", "After successful BGV, you will receive an onboarding confirmation form and then your offer letter."],
                ["5. Overall Timeline", "The complete process from selection to onboarding typically takes 2–3 weeks, and may take up to 4 weeks."],
              ].map(([q, a]) => (
                <div key={q} style={{ paddingBottom: 8, borderBottom: `1px solid ${COLORS.border}` }}>
                  <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 3 }}>{q}</div>
                  <div style={{ fontSize: 12, color: COLORS.muted, lineHeight: 1.6 }}>{a}</div>
                </div>
              ))}
            </div>
          </div>
        </div>

        {/* Acceptance checkbox */}
        <div style={{ background: "rgba(46,204,113,0.08)", border: `1px solid rgba(46,204,113,0.3)`, borderRadius: 12, padding: "14px 16px", marginBottom: 16 }}>
          <label style={{ display: "flex", alignItems: "flex-start", gap: 12, cursor: "pointer" }}>
            <input type="checkbox" checked={faqChecked} onChange={e => setFaqChecked(e.target.checked)} style={{ marginTop: 2, width: 18, height: 18, accentColor: COLORS.success, cursor: "pointer", flexShrink: 0 }} />
            <div>
              <div style={{ fontSize: 14, fontWeight: 700, color: COLORS.text, marginBottom: 3 }}>I have read and understood the above information</div>
              <div style={{ fontSize: 12, color: COLORS.muted }}>By checking this box, you confirm that you have read all the FAQs and onboarding guidelines, and agree to proceed with the interview registration.</div>
            </div>
          </label>
        </div>

        <button
          style={{ ...s.btn, opacity: faqChecked ? 1 : 0.45, cursor: faqChecked ? "pointer" : "not-allowed" }}
          onClick={() => { if (faqChecked) setShowFaq(false); }}
          disabled={!faqChecked}
        >
          ✓ I Agree — Proceed to Registration →
        </button>
      </div>
    </div>
  );

  // ── PAN Gate ──────────────────────────────────────────────────────────────
  if (!panChecked) return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ textAlign: "center", marginBottom: 20 }}>
          <div style={{ fontSize: 40, marginBottom: 10 }}>🪪</div>
          <h2 style={s.h2}>Enter Your PAN Card</h2>
          <p style={{ ...s.sub, margin: "0 0 20px" }}>We use your PAN as your unique User ID. We'll check if you've applied before.</p>
        </div>
        <label style={s.label}>PAN Card Number *</label>
        <input
          style={{ ...s.input, textTransform: "uppercase", letterSpacing: 3, fontSize: 20, textAlign: "center", fontFamily: "monospace", fontWeight: 700, borderColor: panError ? COLORS.danger : COLORS.border }}
          placeholder="ABCDE1234F"
          value={panInput}
          maxLength={10}
          onChange={e => { setPanInput(e.target.value.toUpperCase()); setPanError(""); }}
          onKeyDown={e => e.key === "Enter" && checkPan()}
        />
        {panError && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -10, marginBottom: 10 }}>{panError}</div>}
        <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 16, textAlign: "center" }}>Your PAN is your permanent User ID — no need to remember a separate username</div>
        <button style={s.btn} onClick={checkPan}>Continue →</button>
      </div>
    </div>
  );

  // ── Returning: credentials success ───────────────────────────────────────
  if (existingCandidate && retCreds) return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ textAlign: "center" }}>
          <div style={{ fontSize: 52, marginBottom: 12 }}>🎉</div>
          <h2 style={s.h2}>Welcome Back, {existingCandidate.name.split(" ")[0]}!</h2>
          <p style={{ ...s.sub, margin: "0 0 20px" }}>Your new credentials for this application:</p>
          <div style={{ background: COLORS.card, borderRadius: 12, padding: "20px", marginBottom: 20, border: `1px solid ${COLORS.border}` }}>
            <div style={{ marginBottom: 12 }}>
              <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>USER ID</div>
              <div style={{ fontSize: 20, fontWeight: 700, letterSpacing: 2, color: COLORS.gold, fontFamily: "monospace" }}>{retCreds.username}</div>
            </div>
            <hr style={s.divider} />
            <div>
              <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>NEW PASSWORD</div>
              <div style={{ fontSize: 20, fontWeight: 700, letterSpacing: 2, color: COLORS.gold, fontFamily: "monospace" }}>{retCreds.password}</div>
            </div>
          </div>
          <div style={s.alert("warning")}>⚠ Save these credentials. Your previous password is no longer valid.</div>
          <button style={s.btn} onClick={onComplete}>Go to Login →</button>
        </div>
      </div>
    </div>
  );

  // ── Returning: verification form ─────────────────────────────────────────
  if (existingCandidate) {
    const otpMins = Math.floor(retOtpTimeLeft / 60).toString().padStart(2, "0");
    const otpSecs = (retOtpTimeLeft % 60).toString().padStart(2, "0");
    const activeReferBy = retForm.referBy || existingCandidate.referBy || "";
    const activeEmpId   = retForm.empId  || existingCandidate.empId  || "";

    return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        {/* Welcome back banner */}
        <div style={{ background: "linear-gradient(135deg,rgba(99,102,241,0.15),rgba(99,102,241,0.05))", border:`1px solid rgba(99,102,241,0.35)`, borderRadius:14, padding:16, marginBottom:20 }}>
          <div style={{ display:"flex", alignItems:"center", gap:12 }}>
            {existingCandidate.photoData
              ? <img src={existingCandidate.photoData} alt="" style={{ width:56,height:56,borderRadius:"50%",objectFit:"cover",border:`3px solid rgba(99,102,241,0.5)`,flexShrink:0 }} />
              : <div style={{ width:56,height:56,borderRadius:"50%",background:"rgba(99,102,241,0.2)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:26,flexShrink:0 }}>👤</div>}
            <div>
              <div style={{ fontSize:11,color:"#818cf8",fontWeight:700,letterSpacing:0.5,marginBottom:3 }}>👋 WELCOME BACK</div>
              <div style={{ fontSize:18,fontWeight:800,color:COLORS.text }}>{existingCandidate.name}</div>
              <div style={{ fontSize:12,color:COLORS.muted }}>Last applied: {fmtTs(existingCandidate.registeredAt)}</div>
            </div>
          </div>
        </div>

        <h2 style={s.h2}>Verify Your Details</h2>
        <p style={{ ...s.sub, margin:"0 0 16px" }}>Review your saved info, verify identity and update as needed.</p>

        {/* ── Locked details ── */}
        <div style={{ background:COLORS.card, borderRadius:12, padding:"14px 16px", marginBottom:20, border:`1px solid ${COLORS.border}` }}>
          <div style={{ fontSize:11,color:COLORS.muted,fontWeight:700,letterSpacing:0.5,marginBottom:10 }}>🔒 LOCKED DETAILS (carried forward)</div>
          <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fit,minmax(130px,1fr))", gap:8 }}>
            {[["👤 Name",existingCandidate.name,false],["🪪 PAN",existingCandidate.pan,true],["🔏 Aadhaar",existingCandidate.aadhaar?.slice(0,4)+" XXXX "+existingCandidate.aadhaar?.slice(-4),true]].map(([lbl,val,mono])=>(
              <div key={lbl} style={{ background:COLORS.surface,borderRadius:8,padding:"8px 10px" }}>
                <div style={{ fontSize:10,color:COLORS.muted,marginBottom:3 }}>{lbl}</div>
                <div style={{ fontSize:13,fontWeight:600,color:lbl.includes("PAN")?COLORS.gold:COLORS.text,fontFamily:mono?"monospace":"inherit",letterSpacing:mono?1:0 }}>{val||"—"}</div>
              </div>
            ))}
          </div>
        </div>

        {/* ── DOB — editable, 18+ check ── */}
        <label style={s.label}>Date of Birth * <span style={{ fontSize:11,color:"#818cf8",fontWeight:400 }}>(update if needed)</span></label>
        {(() => {
          const dobVal = retForm.dob || existingCandidate.dob || "";
          const age = calcAge(dobVal);
          const eligible = age !== null && age >= 18;
          const maxDate = (() => { const d = new Date(new Date().setFullYear(new Date().getFullYear() - 18)); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })();
          return (
            <div style={{ marginBottom: 4 }}>
              <input
                type="date"
                style={{ ...s.input, marginBottom:0, borderColor: retErrors.dob ? COLORS.danger : eligible ? COLORS.success : dobVal ? COLORS.danger : COLORS.border }}
                value={dobVal}
                max={maxDate}
                onChange={e => { setR("dob", e.target.value); setRetErrors(p => ({ ...p, dob: null })); }}
              />
              {dobVal && (
                <div style={{ marginTop:6, marginBottom:4 }}>
                  <div style={{ background: eligible ? "rgba(46,204,113,0.12)" : "rgba(231,76,60,0.12)", border:`1px solid ${eligible ? COLORS.success : COLORS.danger}`, borderRadius:20, padding:"3px 12px", fontSize:12, fontWeight:700, color: eligible ? COLORS.success : COLORS.danger, display:"inline-flex", alignItems:"center", gap:5 }}>
                    {eligible ? "✓" : "✗"} Age: {age} years {eligible ? "— Eligible" : "— Must be 18+"}
                  </div>
                </div>
              )}
            </div>
          );
        })()}
        {retErrors.dob && <div style={{ color:COLORS.danger,fontSize:12,marginBottom:10 }}>{retErrors.dob}</div>}

        {/* ── Mobile verify ── */}
        <label style={s.label}>Mobile Number * <span style={{ fontSize:11,color:COLORS.muted,fontWeight:400 }}>(must match records)</span></label>
        <div style={{ position:"relative" }}>
          <input
            style={{ ...s.input, borderColor: retErrors.mobile ? COLORS.danger : retForm.mobile.length===10 && (retForm.mobile===existingCandidate.mobile || retMobileUpdate) ? COLORS.success : COLORS.border, paddingRight:110 }}
            placeholder="10-digit mobile"
            value={retForm.mobile} maxLength={10}
            onChange={e => { setR("mobile", e.target.value.replace(/\D/g,"")); setRetErrors(p=>({...p,mobile:null})); }}
          />
          {retForm.mobile.length===10 && retForm.mobile===existingCandidate.mobile && !retMobileUpdate && (
            <div style={{ position:"absolute",right:10,top:"50%",transform:"translateY(-60%)",background:"rgba(46,204,113,0.15)",borderRadius:20,padding:"2px 10px",fontSize:11,color:COLORS.success,fontWeight:700 }}>✓ Match</div>
          )}
          {retForm.mobile.length===10 && retMobileUpdate && retForm.mobile!==existingCandidate.mobile && (
            <div style={{ position:"absolute",right:10,top:"50%",transform:"translateY(-60%)",background:"rgba(243,156,18,0.15)",borderRadius:20,padding:"2px 10px",fontSize:11,color:COLORS.warning,fontWeight:700 }}>↻ Updating</div>
          )}
        </div>
        {retErrors.mobile && <div style={{ color:COLORS.danger,fontSize:12,marginTop:-10,marginBottom:6 }}>{retErrors.mobile}</div>}

        {/* Mismatch — show checkbox to allow update */}
        {retForm.mobile.length===10 && retForm.mobile!==existingCandidate.mobile && (
          <div style={{ background: retMobileUpdate ? "rgba(243,156,18,0.08)" : "rgba(231,76,60,0.07)", border:`1px solid ${retMobileUpdate ? "rgba(243,156,18,0.35)" : "rgba(231,76,60,0.3)"}`, borderRadius:10, padding:"12px 14px", marginBottom:10 }}>
            <label style={{ display:"flex", alignItems:"flex-start", gap:10, cursor:"pointer" }}>
              <input
                type="checkbox"
                checked={retMobileUpdate}
                onChange={e => { setRetMobileUpdate(e.target.checked); setRetErrors(p=>({...p,mobile:null})); }}
                style={{ marginTop:2, width:16, height:16, cursor:"pointer", accentColor:COLORS.warning, flexShrink:0 }}
              />
              <div>
                <div style={{ fontSize:13, fontWeight:600, color:retMobileUpdate?COLORS.warning:COLORS.danger, marginBottom:3 }}>
                  {retMobileUpdate ? "✓ Mobile number will be updated" : "⚠ Mobile doesn't match our records"}
                </div>
                <div style={{ fontSize:12, color:COLORS.muted }}>
                  {retMobileUpdate
                    ? `Your registered mobile <strong style="color:${COLORS.text}">${existingCandidate.mobile}</strong> will be replaced with <strong style="color:${COLORS.warning}">${retForm.mobile}</strong>.`
                    : `Our records show: ${existingCandidate.mobile.slice(0,3)}XXXXX${existingCandidate.mobile.slice(-2)}. Check this box if you want to update your mobile number.`
                  }
                </div>
              </div>
            </label>
          </div>
        )}

        {/* ── Email + OTP ── */}
        <label style={s.label}>Email ID * <span style={{ fontSize:11,color:COLORS.muted,fontWeight:400 }}>(verify via OTP)</span></label>
        <div style={{ display:"flex",gap:8,marginBottom:4 }}>
          <input
            style={{ ...s.input,marginBottom:0,flex:1,borderColor:retErrors.email?COLORS.danger:retOtpVerified?COLORS.success:COLORS.border }}
            placeholder="your@email.com"
            value={retForm.email}
            onChange={e=>{setR("email",e.target.value.trim());setRetErrors(p=>({...p,email:null}));setRetOtpVerified(false);setRetOtpSent(false);}}
            disabled={retOtpVerified}
          />
          <button
            onClick={retOtpVerified?()=>{setRetOtpVerified(false);setRetOtpSent(false);setR("email","");setR("otp","");}:sendRetOtp}
            style={{ background:retOtpVerified?"rgba(46,204,113,0.15)":"rgba(99,102,241,0.15)",border:`1px solid ${retOtpVerified?COLORS.success:"rgba(99,102,241,0.4)"}`,borderRadius:10,padding:"0 14px",color:retOtpVerified?COLORS.success:"#818cf8",cursor:"pointer",fontSize:13,fontWeight:700,whiteSpace:"nowrap",flexShrink:0 }}
          >{retOtpVerified?"✓ Verified":retOtpSent?"↺ Resend":"Send OTP"}</button>
        </div>
        {retErrors.email&&<div style={{ color:COLORS.danger,fontSize:12,marginBottom:8 }}>{retErrors.email}</div>}

        {/* OTP box */}
        {retOtpSent&&!retOtpVerified&&(
          <div style={{ background:"rgba(99,102,241,0.06)",border:`1px solid rgba(99,102,241,0.2)`,borderRadius:12,padding:"14px 16px",marginBottom:14 }}>
            <div style={{ background:COLORS.card,borderRadius:8,padding:"10px 12px",marginBottom:12,border:`1px solid ${COLORS.border}` }}>
              <div style={{ fontSize:11,color:COLORS.muted,marginBottom:6 }}>📧 Simulated email to <strong style={{ color:COLORS.text }}>{retForm.email}</strong></div>
              <div style={{ fontSize:11,color:COLORS.muted,marginBottom:6 }}>Your verification code:</div>
              <div style={{ fontSize:30,fontWeight:900,letterSpacing:8,color:COLORS.gold,textAlign:"center",fontFamily:"monospace" }}>{retOtpCode}</div>
            </div>
            <div style={{ display:"flex",gap:8,alignItems:"center",marginBottom:8 }}>
              <input
                style={{ ...s.input,marginBottom:0,flex:1,fontSize:20,letterSpacing:6,textAlign:"center",fontFamily:"monospace",fontWeight:700,borderColor:retErrors.otp?COLORS.danger:COLORS.border }}
                placeholder="000000" value={retForm.otp} maxLength={6}
                onChange={e=>{setR("otp",e.target.value.replace(/\D/g,""));setRetErrors(p=>({...p,otp:null}));}}
              />
              <button onClick={verifyRetOtp} style={{ ...s.btn,width:"auto",padding:"10px 16px",marginTop:0,fontSize:14 }}>Verify</button>
            </div>
            {retErrors.otp&&<div style={{ color:COLORS.danger,fontSize:12,marginBottom:4 }}>{retErrors.otp}</div>}
            <div style={{ display:"flex",justifyContent:"space-between",alignItems:"center" }}>
              <div style={{ fontSize:11,color:retOtpTimeLeft<=30?COLORS.danger:COLORS.muted }}>
                {retOtpTimeLeft>0?`⏱ Expires in ${otpMins}:${otpSecs}`:"⚠️ OTP expired"}
              </div>
              <div style={{ background:COLORS.surface,borderRadius:20,height:4,width:80,overflow:"hidden" }}>
                <div style={{ height:"100%",width:`${(retOtpTimeLeft/120)*100}%`,background:retOtpTimeLeft<=30?COLORS.danger:COLORS.success,transition:"width 1s linear" }} />
              </div>
            </div>
          </div>
        )}

        {/* ── Referred By — EDITABLE ── */}
        <label style={s.label}>Referred By * <span style={{ fontSize:11,color:"#818cf8",fontWeight:400 }}>(update if changed)</span></label>
        <select
          style={{ ...s.select, borderColor:retErrors.referBy?COLORS.danger:"rgba(99,102,241,0.4)", background:COLORS.card }}
          value={activeReferBy}
          onChange={e=>{setR("referBy",e.target.value);setRetErrors(p=>({...p,referBy:null}));}}
        >
          <option value="">Select source…</option>
          <option value="walkin">Walk-in</option>
          <option value="website">Website</option>
          <option value="referral">Referred by Employee</option>
        </select>
        {retErrors.referBy&&<div style={{ color:COLORS.danger,fontSize:12,marginTop:-10,marginBottom:10 }}>{retErrors.referBy}</div>}
        {activeReferBy==="referral"&&(
          <>
            <label style={s.label}>Referring Employee ID *</label>
            <input
              style={{ ...s.input,borderColor:retErrors.empId?COLORS.danger:"rgba(99,102,241,0.4)" }}
              placeholder="e.g. EMP1042"
              value={activeEmpId}
              onChange={e=>{setR("empId",e.target.value.toUpperCase());setRetErrors(p=>({...p,empId:null}));}}
            />
            {retErrors.empId&&<div style={{ color:COLORS.danger,fontSize:12,marginTop:-10,marginBottom:10 }}>{retErrors.empId}</div>}
          </>
        )}

        {/* ── Resume — optional ── */}
        <label style={{ ...s.label, marginTop:6 }}>Resume <span style={{ fontSize:11,color:COLORS.muted,fontWeight:400 }}>(optional — keep existing or upload new)</span></label>
        {existingCandidate.resume&&!retForm.resume&&(
          <div style={{ background:COLORS.card,borderRadius:10,padding:"12px 14px",marginBottom:10,border:`1px solid rgba(46,204,113,0.3)`,display:"flex",justifyContent:"space-between",alignItems:"center" }}>
            <div style={{ display:"flex",alignItems:"center",gap:10 }}>
              <span style={{ fontSize:18 }}>📄</span>
              <div><div style={{ fontSize:12,color:COLORS.success,fontWeight:600 }}>Using existing resume</div><div style={{ fontSize:11,color:COLORS.muted }}>{existingCandidate.resume}</div></div>
            </div>
            <button onClick={()=>document.getElementById("ret-resume-input").click()} style={{ background:"rgba(99,102,241,0.12)",border:`1px solid rgba(99,102,241,0.3)`,borderRadius:7,padding:"5px 12px",color:"#818cf8",cursor:"pointer",fontSize:12,fontWeight:600 }}>🔄 Update</button>
          </div>
        )}
        {retForm.resume&&(
          <div style={{ background:COLORS.card,borderRadius:10,padding:"12px 14px",marginBottom:10,border:`1px solid rgba(46,204,113,0.4)`,display:"flex",justifyContent:"space-between",alignItems:"center" }}>
            <div style={{ display:"flex",alignItems:"center",gap:10 }}>
              <span style={{ fontSize:18 }}>✅</span>
              <div><div style={{ fontSize:12,color:COLORS.success,fontWeight:600 }}>New resume uploaded</div><div style={{ fontSize:11,color:COLORS.muted }}>{retForm.resume}</div></div>
            </div>
            <button onClick={()=>{setR("resume",null);setR("resumeData",null);}} style={{ background:"rgba(231,76,60,0.1)",border:`1px solid rgba(231,76,60,0.3)`,borderRadius:7,padding:"5px 12px",color:COLORS.danger,cursor:"pointer",fontSize:12,fontWeight:600 }}>✕ Remove</button>
          </div>
        )}
        {!existingCandidate.resume&&!retForm.resume&&(
          <div style={{ background:COLORS.card,border:`2px dashed ${COLORS.border}`,borderRadius:10,padding:16,marginBottom:4,cursor:"pointer",textAlign:"center" }} onClick={()=>document.getElementById("ret-resume-input").click()}>
            <div style={{ fontSize:22,marginBottom:4 }}>📄</div>
            <div style={{ fontSize:13,color:COLORS.muted }}>Click to upload PDF only</div>
          </div>
        )}
        <input id="ret-resume-input" type="file" accept=".pdf" style={{ display:"none" }} onChange={e=>{
          const file=e.target.files[0];if(!file)return;
          const reader=new FileReader();
          reader.onload=ev=>{setR("resumeData",ev.target.result);setR("resume",file.name);};
          reader.readAsDataURL(file);
        }} />

        <div style={{ ...s.alert("warning"),marginTop:14 }}>
          ℹ️ Submitting will generate a <strong>new password</strong>. Your previous password will stop working.
        </div>
        <button style={{ ...s.btn,marginTop:14 }} onClick={submitReturning}>Confirm & Get New Credentials →</button>
        <button style={{ ...s.btnOut }} onClick={()=>{setPanChecked(false);setExistingCandidate(null);setPanInput("");}}>← Use a Different PAN</button>
      </div>
    </div>
    );
  }

  // ── Duplicate Alarm Modal ──────────────────────────────────────────────────
  if (dupAlarm) return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ textAlign: "center", marginBottom: 20 }}>
          <div style={{ fontSize: 52, marginBottom: 8 }}>🚨</div>
          <h2 style={{ ...s.h2, color: COLORS.danger }}>Duplicate Entry Detected!</h2>
          <p style={{ fontSize: 13, color: COLORS.muted, margin: "0 0 20px" }}>
            One or more details of <strong style={{ color: COLORS.text }}>{form.name}</strong> already match a registration made today.
          </p>
        </div>

        {/* Alarm details */}
        <div style={{ display: "flex", flexDirection: "column", gap: 10, marginBottom: 20 }}>
          {dupAlarm.hits.map((h, i) => (
            <div key={i} style={{ background: "rgba(231,76,60,0.1)", border: `1px solid rgba(231,76,60,0.4)`, borderRadius: 12, padding: "14px 16px" }}>
              <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start" }}>
                <div>
                  <div style={{ fontSize: 12, color: COLORS.danger, fontWeight: 700, letterSpacing: 0.5, marginBottom: 4 }}>⚠ {h.field.toUpperCase()} MATCH</div>
                  <div style={{ fontSize: 14, fontWeight: 600, color: COLORS.text }}>{h.value}</div>
                  <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 4 }}>
                    Previously registered by: <strong style={{ color: COLORS.text }}>{h.existingName}</strong>
                  </div>
                  <div style={{ fontSize: 11, color: COLORS.muted, marginTop: 2 }}>
                    at {fmtTs(h.existingTime)}
                  </div>
                </div>
                <div style={{ fontSize: 24 }}>🔴</div>
              </div>
            </div>
          ))}
        </div>

        <div style={{ ...s.alert("warning"), marginBottom: 20 }}>
          <strong>⚠ This alarm has been logged</strong> and will be visible to the Super Admin and Panelist for review.
        </div>

        <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
          <button
            style={{ ...s.btn, background: COLORS.danger }}
            onClick={() => { setForceAllow(true); setDupAlarm(null); doRegister(true); }}
          >
            ⚡ Override & Register Anyway
          </button>
          <button
            style={{ ...s.btnOut }}
            onClick={() => { setDupAlarm(null); setStep(2); }}
          >
            ← Go Back & Correct Details
          </button>
        </div>
      </div>
    </div>
  );

  if (step === 3) return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ textAlign: "center" }}>
          {form.photoData && (
            <img src={creds ? form.photoData : ""} alt="" style={{ width: 72, height: 72, borderRadius: "50%", objectFit: "cover", border: `3px solid ${COLORS.success}`, marginBottom: 12 }} />
          )}
          <div style={{ fontSize: 52, marginBottom: 12 }}>🎉</div>
          <h2 style={s.h2}>Registration Successful!</h2>
          <p style={{ ...s.sub, margin: "0 0 20px" }}>Your credentials have been generated. Please note them down carefully.</p>
          <div style={{ background: COLORS.card, borderRadius: 12, padding: "20px", marginBottom: 20, border: `1px solid ${COLORS.border}` }}>
            <div style={{ marginBottom: 12 }}>
              <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>YOUR USER ID</div>
              <div style={{ fontSize: 20, fontWeight: 700, letterSpacing: 2, color: COLORS.gold, fontFamily: "monospace" }}>{creds?.username}</div>
              <div style={{ fontSize: 11, color: COLORS.muted, marginTop: 4 }}>Your PAN card number is your permanent User ID</div>
            </div>
            <hr style={s.divider} />
            <div>
              <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>PASSWORD</div>
              <div style={{ fontSize: 22, fontWeight: 700, letterSpacing: 2, color: COLORS.gold, fontFamily: "monospace" }}>{creds.password}</div>
            </div>
          </div>
          <div style={s.alert("warning")}>
            <strong>⚠ Important:</strong> Please save your credentials. You will need them to log in and take the tests.
          </div>
          <button style={s.btn} onClick={onComplete}>Go to Login →</button>
        </div>
      </div>
    </div>
  );

  return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ display: "flex", gap: 0, marginBottom: 24 }}>
          {["Personal Details", "Documents & Resume"].map((t, i) => (
            <div key={i} style={{ flex: 1, textAlign: "center" }}>
              <div style={{ width: 28, height: 28, borderRadius: "50%", background: step > i + 1 ? COLORS.success : step === i + 1 ? COLORS.accent : COLORS.card, display: "flex", alignItems: "center", justifyContent: "center", margin: "0 auto 6px", fontSize: 13, fontWeight: 700, border: `2px solid ${step >= i + 1 ? (step > i + 1 ? COLORS.success : COLORS.accent) : COLORS.border}` }}>
                {step > i + 1 ? "✓" : i + 1}
              </div>
              <div style={{ fontSize: 11, color: step === i + 1 ? COLORS.text : COLORS.muted }}>{t}</div>
            </div>
          ))}
        </div>

        {step === 1 && <>
          <h2 style={s.h2}>Personal Information</h2>
          <label style={s.label}>Full Name *</label>
          <input style={{ ...s.input, borderColor: errors.name ? COLORS.danger : COLORS.border }} placeholder="Enter your full name" value={form.name} onChange={e => set("name", e.target.value)} />
          {errors.name && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.name}</div>}

          <label style={s.label}>Mobile Number *</label>
          <input style={{ ...s.input, borderColor: errors.mobile ? COLORS.danger : COLORS.border }} placeholder="10-digit mobile number" value={form.mobile} maxLength={10} onChange={e => set("mobile", e.target.value.replace(/\D/g, ""))} />
          {errors.mobile && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.mobile}</div>}

          <label style={s.label}>Date of Birth *</label>
          {(() => {
            const age = calcAge(form.dob);
            const eligible = age !== null && age >= 18;
            const tooYoung = age !== null && age < 18;
            const maxDate = (() => { const d = new Date(new Date().setFullYear(new Date().getFullYear() - 18)); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })();
            return (
              <div style={{ marginBottom: 4 }}>
                <input
                  type="date"
                  style={{ ...s.input, marginBottom: 0, borderColor: errors.dob ? COLORS.danger : eligible ? COLORS.success : COLORS.border }}
                  value={form.dob}
                  max={maxDate}
                  onChange={e => { set("dob", e.target.value); setErrors(p => ({ ...p, dob: null })); }}
                />
                {form.dob && (
                  <div style={{ display: "flex", alignItems: "center", gap: 8, marginTop: 6, marginBottom: 6 }}>
                    <div style={{ background: eligible ? "rgba(46,204,113,0.12)" : "rgba(231,76,60,0.12)", border: `1px solid ${eligible ? COLORS.success : COLORS.danger}`, borderRadius: 20, padding: "3px 12px", fontSize: 12, fontWeight: 700, color: eligible ? COLORS.success : COLORS.danger, display: "inline-flex", alignItems: "center", gap: 5 }}>
                      {eligible ? "✓" : "✗"} Age: {age} years {eligible ? "— Eligible" : "— Must be 18+"}
                    </div>
                  </div>
                )}
              </div>
            );
          })()}
          {errors.dob && <div style={{ color: COLORS.danger, fontSize: 12, marginBottom: 10 }}>{errors.dob}</div>}

          <label style={s.label}>Gender *</label>
          <div style={{ display: "flex", gap: 8, marginBottom: 4 }}>
            {[["Male","👨 Male"],["Female","👩 Female"],["Other","🧑 Other"]].map(([v, l]) => (
              <button key={v} onClick={() => set("gender", v)} style={{ flex: 1, padding: "10px 6px", borderRadius: 10, border: `1px solid ${form.gender === v ? COLORS.accent : COLORS.border}`, background: form.gender === v ? "rgba(233,69,96,0.15)" : COLORS.card, color: form.gender === v ? COLORS.accent : COLORS.text, cursor: "pointer", fontWeight: 600, fontSize: 13 }}>{l}</button>
            ))}
          </div>
          {errors.gender && <div style={{ color: COLORS.danger, fontSize: 12, marginBottom: 10 }}>{errors.gender}</div>}
          <div style={{ marginBottom: 16 }} />

          <label style={s.label}>Have you completed your Graduation? *</label>
          <div style={{ display: "flex", gap: 10, marginBottom: 4 }}>
            {[["Yes","✅ Yes"],["No","❌ No"]].map(([v, l]) => (
              <button key={v} onClick={() => set("graduationDone", v)} style={{ flex: 1, padding: "10px", borderRadius: 10, border: `1px solid ${form.graduationDone === v ? COLORS.accent : COLORS.border}`, background: form.graduationDone === v ? "rgba(233,69,96,0.15)" : COLORS.card, color: form.graduationDone === v ? COLORS.accent : COLORS.text, cursor: "pointer", fontWeight: 600 }}>{l}</button>
            ))}
          </div>
          {errors.graduationDone && <div style={{ color: COLORS.danger, fontSize: 12, marginBottom: 10 }}>{errors.graduationDone}</div>}
          <div style={{ marginBottom: 16 }} />

          <label style={s.label}>Location for Interview *</label>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 10, marginBottom: 4 }}>
            {[["NOIDA - OE","📍 NOIDA - OE"],["Gurugram - OG","📍 Gurugram - OG"]].map(([v, l]) => (
              <button key={v} onClick={() => set("interviewLocation", v)} style={{ padding: "14px 10px", borderRadius: 12, border: `2px solid ${form.interviewLocation === v ? COLORS.accent : COLORS.border}`, background: form.interviewLocation === v ? "rgba(233,69,96,0.12)" : COLORS.card, color: form.interviewLocation === v ? COLORS.accent : COLORS.text, cursor: "pointer", fontWeight: 700, fontSize: 13, textAlign: "center" }}>
                <div style={{ fontSize: 20, marginBottom: 4 }}>🏢</div>
                {l}
              </button>
            ))}
          </div>
          {errors.interviewLocation && <div style={{ color: COLORS.danger, fontSize: 12, marginBottom: 10 }}>{errors.interviewLocation}</div>}
          <div style={{ marginBottom: 16 }} />

          <label style={s.label}>Referred By *</label>
          <select style={{ ...s.select, borderColor: errors.referBy ? COLORS.danger : COLORS.border }} value={form.referBy} onChange={e => set("referBy", e.target.value)}>
            <option value="">Select source...</option>
            <option value="walkin">Walk-in</option>
            <option value="website">Website</option>
            <option value="referral">Referred by Employee</option>
          </select>
          {errors.referBy && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.referBy}</div>}

          {form.referBy === "referral" && (
            <>
              <label style={s.label}>Referring Employee ID *</label>
              <input
                style={{ ...s.input, borderColor: errors.empId ? COLORS.danger : COLORS.accent + "88" }}
                placeholder="e.g. EMP1042"
                value={form.empId}
                onChange={e => set("empId", e.target.value.toUpperCase())}
              />
              {errors.empId && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.empId}</div>}
            </>
          )}

          <label style={s.label}>Are you a Rejoiner? *</label>
          <div style={{ display: "flex", gap: 10, marginBottom: 16 }}>
            {["Yes", "No"].map(v => (
              <button key={v} onClick={() => set("isRejoiner", v)} style={{ flex: 1, padding: "10px", borderRadius: 10, border: `1px solid ${form.isRejoiner === v ? COLORS.accent : COLORS.border}`, background: form.isRejoiner === v ? "rgba(233,69,96,0.15)" : COLORS.card, color: form.isRejoiner === v ? COLORS.accent : COLORS.text, cursor: "pointer", fontWeight: 600 }}>{v}</button>
            ))}
          </div>
          {errors.isRejoiner && <div style={{ color: COLORS.danger, fontSize: 12, marginBottom: 10 }}>{errors.isRejoiner}</div>}

          {/* ── Complete Address ── */}
          <div style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", marginBottom: 16, border: `1px solid ${COLORS.border}` }}>
            <div style={{ fontSize: 12, fontWeight: 700, color: COLORS.text, marginBottom: 14, display: "flex", alignItems: "center", gap: 6 }}>
              🏠 Complete Address
            </div>

            <label style={s.label}>Address Line 1 * <span style={{ fontSize:11, color:COLORS.muted, fontWeight:400 }}>(House/Flat No., Street)</span></label>
            <input
              style={{ ...s.input, borderColor: errors.addr1 ? COLORS.danger : COLORS.border }}
              placeholder="e.g. 42, MG Road, Near Post Office"
              value={form.addr1}
              onChange={e => set("addr1", e.target.value)}
            />
            {errors.addr1 && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -10, marginBottom: 10 }}>{errors.addr1}</div>}

            <label style={s.label}>Address Line 2 <span style={{ fontSize:11, color:COLORS.muted, fontWeight:400 }}>(optional)</span></label>
            <input
              style={{ ...s.input, borderColor: COLORS.border }}
              placeholder="e.g. Sector 12, Phase 2"
              value={form.addr2}
              onChange={e => set("addr2", e.target.value)}
            />

            <label style={s.label}>Nearest Landmark <span style={{ fontSize:11, color:COLORS.muted, fontWeight:400 }}>(optional)</span></label>
            <input
              style={{ ...s.input, borderColor: COLORS.border }}
              placeholder="e.g. Near Apollo Hospital"
              value={form.landmark}
              onChange={e => set("landmark", e.target.value)}
            />

            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(130px, 1fr))", gap: 10 }}>
              <div>
                <label style={s.label}>City *</label>
                <input
                  style={{ ...s.input, marginBottom: 0, borderColor: errors.city ? COLORS.danger : COLORS.border }}
                  placeholder="e.g. Mumbai"
                  value={form.city}
                  onChange={e => set("city", e.target.value)}
                />
                {errors.city && <div style={{ color: COLORS.danger, fontSize: 11, marginTop: 4 }}>{errors.city}</div>}
              </div>
              <div>
                <label style={s.label}>State *</label>
                <select
                  style={{ ...s.select, marginBottom: 0, borderColor: errors.state ? COLORS.danger : COLORS.border }}
                  value={form.state}
                  onChange={e => set("state", e.target.value)}
                >
                  <option value="">Select state…</option>
                  {["Andhra Pradesh","Arunachal Pradesh","Assam","Bihar","Chhattisgarh","Goa","Gujarat","Haryana","Himachal Pradesh","Jharkhand","Karnataka","Kerala","Madhya Pradesh","Maharashtra","Manipur","Meghalaya","Mizoram","Nagaland","Odisha","Punjab","Rajasthan","Sikkim","Tamil Nadu","Telangana","Tripura","Uttar Pradesh","Uttarakhand","West Bengal","Delhi","Jammu & Kashmir","Ladakh","Chandigarh","Puducherry","Andaman & Nicobar Islands","Dadra & Nagar Haveli","Daman & Diu","Lakshadweep"].map(st => (
                    <option key={st} value={st}>{st}</option>
                  ))}
                </select>
                {errors.state && <div style={{ color: COLORS.danger, fontSize: 11, marginTop: 4 }}>{errors.state}</div>}
              </div>
              <div>
                <label style={s.label}>Pincode *</label>
                <input
                  style={{ ...s.input, marginBottom: 0, borderColor: errors.pincode ? COLORS.danger : /^\d{6}$/.test(form.pincode) ? COLORS.success : COLORS.border }}
                  placeholder="6-digit pincode"
                  value={form.pincode}
                  maxLength={6}
                  onChange={e => set("pincode", e.target.value.replace(/\D/g, ""))}
                />
                {errors.pincode && <div style={{ color: COLORS.danger, fontSize: 11, marginTop: 4 }}>{errors.pincode}</div>}
              </div>
            </div>
          </div>

          {/* ── Photo Upload / Camera ── */}
          <label style={s.label}>Current Photo *</label>
          <PhotoCapture
            photoData={form.photoData}
            photoName={form.photo}
            error={errors.photo}
            onCapture={(data, name) => {
              set("photoData", data);
              set("photo", name);
              setErrors(prev => ({ ...prev, photo: null }));
            }}
            onError={msg => setErrors(prev => ({ ...prev, photo: msg }))}
          />
          {errors.photo && <div style={{ color: COLORS.danger, fontSize: 12, marginBottom: 10 }}>{errors.photo}</div>}
          <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 16 }}>📌 Use a recent passport-size photo with a plain background</div>

          <button style={s.btn} onClick={submitStep1}>Next →</button>
        </>}

        {step === 2 && <>
          <h2 style={s.h2}>Documents</h2>

          {/* PAN display — captured in step 0, shown as read-only */}
          <div style={{ background: "rgba(245,166,35,0.08)", border: `1px solid rgba(245,166,35,0.3)`, borderRadius: 10, padding: "10px 14px", marginBottom: 14, display: "flex", alignItems: "center", gap: 10 }}>
            <span style={{ fontSize: 16 }}>🪪</span>
            <div>
              <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5 }}>USER ID / PAN (confirmed)</div>
              <div style={{ fontSize: 16, fontWeight: 800, color: COLORS.gold, fontFamily: "monospace", letterSpacing: 2 }}>{form.pan}</div>
            </div>
          </div>

          <label style={s.label}>Aadhaar Card Number *</label>
          <input style={{ ...s.input, borderColor: errors.aadhaar ? COLORS.danger : COLORS.border }} placeholder="1234 5678 9012" value={form.aadhaar} maxLength={12} onChange={e => set("aadhaar", e.target.value.replace(/\D/g, ""))} />
          {errors.aadhaar && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.aadhaar}</div>}

          <label style={s.label}>Upload Resume *</label>
          <div style={{ background: COLORS.card, border: `2px dashed ${errors.resume ? COLORS.danger : COLORS.border}`, borderRadius: 10, padding: "20px", textAlign: "center", marginBottom: 16, cursor: "pointer" }} onClick={() => document.getElementById("resume-input").click()}>
            <input id="resume-input" type="file" accept=".pdf" style={{ display: "none" }} onChange={e => {
              const file = e.target.files[0];
              if (!file) return;
              const reader = new FileReader();
              reader.onload = ev => set("resumeData", ev.target.result);
              reader.readAsDataURL(file);
              set("resume", file.name);
            }} />
            {form.resume ? <><div style={{ color: COLORS.success, fontSize: 18, marginBottom: 4 }}>✓</div><div style={{ color: COLORS.success, fontSize: 13 }}>{form.resume}</div></> : <><div style={{ fontSize: 28, marginBottom: 6 }}>📄</div><div style={{ fontSize: 13, color: COLORS.muted }}>Click to upload PDF only</div></>}
          </div>
          {errors.resume && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.resume}</div>}

          <div style={s.row}>
            <button style={{ ...s.btnOut, marginTop: 0 }} onClick={() => setStep(1)}>← Back</button>
            <button style={{ ...s.btn, marginTop: 0 }} onClick={submitStep2}>Submit →</button>
          </div>
        </>}
      </div>
    </div>
  );
}

// ─── Panelist Setup / Change Password ────────────────────────────────────────
const COMPANY_DOMAIN = "ocrolus.com";

function PanelistSetup({ existing, onSave, onCancel }) {
  const isFirst = !existing;
  const [form, setForm] = useState({ name: existing?.name || "", email: "", password: "", confirm: "" });
  const [errors, setErrors] = useState({});
  const set = (k, v) => setForm(p => ({ ...p, [k]: v }));

  // Derive username from email prefix (before @)
  const emailPrefix = form.email.split("@")[0] || "";
  const emailDomain = form.email.includes("@") ? form.email.split("@")[1] : "";
  const isValidDomain = emailDomain.toLowerCase() === COMPANY_DOMAIN;
  const derivedUsername = emailPrefix;

  function validate() {
    const e = {};
    if (!form.name.trim() || form.name.trim().length < 2) e.name = "Full name is required (min 2 characters)";
    if (!form.email.trim()) {
      e.email = "Company email is required";
    } else if (!form.email.includes("@")) {
      e.email = "Enter a valid email address";
    } else if (emailDomain.toLowerCase() !== COMPANY_DOMAIN) {
      e.email = `Only @${COMPANY_DOMAIN} email addresses are allowed`;
    } else if (!emailPrefix) {
      e.email = "Invalid email format";
    }
    if (form.password.length < 8) e.password = "Password must be at least 8 characters";
    if (!/[A-Z]/.test(form.password)) e.password = "Must contain at least one uppercase letter";
    if (!/[0-9]/.test(form.password)) e.password = "Must contain at least one number";
    if (form.password !== form.confirm) e.confirm = "Passwords do not match";
    setErrors(e);
    return Object.keys(e).length === 0;
  }

  function handleSave() {
    if (!validate()) return;
    const now = localISO();
    const cred = {
      id: existing?.id || `pan_${Date.now()}`,
      name: form.name.trim(),
      email: form.email,
      username: derivedUsername,
      password: form.password,
      createdAt: existing?.createdAt || now,
      expiresAt: new Date(Date.now() + 90 * 24 * 60 * 60 * 1000).toISOString(),
      disabled: false,
      history: [...(existing?.history || []), { username: existing?.username, email: existing?.email, changedAt: now }]
    };
    onSave(cred);
  }

  const daysLeft = existing ? Math.max(0, Math.ceil((new Date(existing.expiresAt) - Date.now()) / (1000 * 60 * 60 * 24))) : null;
  const isExpired = existing && new Date(existing.expiresAt) < new Date();

  return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        {isExpired && (
          <div style={{ ...s.alert("danger"), marginBottom: 20 }}>
            <strong>🔒 Credentials Expired</strong><br />
            Your panelist credentials expired on {fmtTs(existing.expiresAt)}. Please set new credentials to continue.
          </div>
        )}
        {!isFirst && !isExpired && (
          <div style={{ ...s.alert("warning"), marginBottom: 20 }}>
            <strong>🔄 Change Credentials</strong><br />
            {daysLeft <= 14 ? `⚠️ Your credentials expire in ${daysLeft} day${daysLeft !== 1 ? "s" : ""}. Please update now.` : `Current credentials expire on ${fmtTs(existing.expiresAt)}.`}
          </div>
        )}

        <h2 style={s.h2}>{isFirst ? "Set Up Panelist Account" : "Update Panelist Credentials"}</h2>
        {isFirst && <p style={{ ...s.sub, margin: "0 0 20px" }}>Fill in the panelist's details. The username will be auto-assigned from the email.</p>}

        {/* Full Name */}
        <label style={s.label}>Panelist Full Name *</label>
        <input
          style={{ ...s.input, borderColor: errors.name ? COLORS.danger : form.name.trim().length >= 2 ? COLORS.success : COLORS.border }}
          placeholder="e.g. Manpreet Singh"
          value={form.name}
          onChange={e => set("name", e.target.value)}
        />
        {errors.name && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.name}</div>}

        {/* Email field */}
        <label style={s.label}>Company Email ID *</label>
        <input
          style={{ ...s.input, borderColor: errors.email ? COLORS.danger : isValidDomain && emailPrefix ? COLORS.success : COLORS.border }}
          placeholder={`e.g. jsmith@${COMPANY_DOMAIN}`}
          value={form.email}
          onChange={e => set("email", e.target.value.trim())}
        />
        {errors.email && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.email}</div>}

        {/* Auto-derived username preview */}
        {(form.name.trim() || emailPrefix) && (
          <div style={{ background: COLORS.card, borderRadius: 10, padding: "12px 14px", marginBottom: 16, border: `1px solid ${isValidDomain ? COLORS.success + "66" : COLORS.border}`, display: "flex", alignItems: "center", gap: 12 }}>
            <div style={{ width: 42, height: 42, borderRadius: "50%", background: isValidDomain ? "rgba(46,204,113,0.15)" : COLORS.surface, border: `2px solid ${isValidDomain ? COLORS.success : COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 18, flexShrink: 0 }}>
              {form.name.trim() ? form.name.trim().charAt(0).toUpperCase() : "👤"}
            </div>
            <div>
              {form.name.trim() && <div style={{ fontSize: 14, fontWeight: 700, color: COLORS.text, marginBottom: 2 }}>{form.name.trim()}</div>}
              <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 2 }}>USERNAME</div>
              <div style={{ fontSize: 15, fontWeight: 700, letterSpacing: 1, color: isValidDomain ? COLORS.gold : COLORS.muted }}>
                {emailPrefix ? (isValidDomain ? derivedUsername : <span style={{ fontSize: 12, color: COLORS.danger }}>Invalid domain — must be @{COMPANY_DOMAIN}</span>) : "—"}
              </div>
            </div>
          </div>
        )}

        {/* Password */}
        <label style={s.label}>Password *</label>
        <input type="password" style={{ ...s.input, borderColor: errors.password ? COLORS.danger : COLORS.border }} placeholder="Min. 8 chars, 1 uppercase, 1 number" value={form.password} onChange={e => set("password", e.target.value)} />
        {errors.password && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.password}</div>}

        <label style={s.label}>Confirm Password *</label>
        <input type="password" style={{ ...s.input, borderColor: errors.confirm ? COLORS.danger : COLORS.border }} placeholder="Re-enter password" value={form.confirm} onChange={e => set("confirm", e.target.value)} />
        {errors.confirm && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{errors.confirm}</div>}

        {/* Password strength checklist */}
        <div style={{ background: COLORS.card, borderRadius: 10, padding: "12px 14px", marginBottom: 16, fontSize: 12, border: `1px solid ${COLORS.border}` }}>
          <div style={{ fontWeight: 600, color: COLORS.text, marginBottom: 6 }}>Password requirements:</div>
          {[
            ["Minimum 8 characters", form.password.length >= 8],
            ["At least one uppercase letter", /[A-Z]/.test(form.password)],
            ["At least one number", /[0-9]/.test(form.password)],
            ["Passwords match", form.password.length > 0 && form.password === form.confirm]
          ].map(([label, met]) => (
            <div key={label} style={{ color: met ? COLORS.success : COLORS.muted, marginBottom: 3 }}>
              {met ? "✓" : "○"} {label}
            </div>
          ))}
        </div>

        <div style={{ background: COLORS.card, borderRadius: 10, padding: "10px 14px", marginBottom: 16, fontSize: 12, color: COLORS.muted, border: `1px solid ${COLORS.border}` }}>
          🗓 Credentials are valid for <strong style={{ color: COLORS.gold }}>90 days</strong>. You will be prompted to update them before they expire.
        </div>

        <button style={s.btn} onClick={handleSave}>{isFirst ? "Create Panelist Account →" : "Save New Credentials →"}</button>
        {!isFirst && onCancel && <button style={{ ...s.btnOut, marginTop: 8 }} onClick={onCancel}>Cancel</button>}
      </div>
    </div>
  );
}

const SUPER_ADMIN_EMAIL = "Mikkey1990@gmail.com";
const OTP_VALIDITY_SECONDS = 120; // 2 minutes

function SuperAdminSetup({ existing, onSave, onCancel }) {
  const isFirst = !existing;
  const [step, setStep] = useState("email");   // email | otp | password
  const [email, setEmail] = useState(existing?.email || "");
  const [emailErr, setEmailErr] = useState("");
  const [generatedOtp, setGeneratedOtp] = useState(null);
  const [otpExpiry, setOtpExpiry] = useState(null);
  const [otpInput, setOtpInput] = useState("");
  const [otpErr, setOtpErr] = useState("");
  const [timeLeft, setTimeLeft] = useState(0);
  const [sending, setSending] = useState(false);
  const [form, setForm] = useState({ password: "", confirm: "" });
  const [pwdErrors, setPwdErrors] = useState({});
  const set = (k, v) => setForm(p => ({ ...p, [k]: v }));

  const emailPrefix = email.split("@")[0] || "";
  const isAuthorized = email.trim().toLowerCase() === SUPER_ADMIN_EMAIL.toLowerCase();

  // Countdown timer
  useEffect(() => {
    if (!otpExpiry) return;
    const interval = setInterval(() => {
      const left = Math.max(0, Math.ceil((otpExpiry - Date.now()) / 1000));
      setTimeLeft(left);
      if (left === 0) clearInterval(interval);
    }, 1000);
    return () => clearInterval(interval);
  }, [otpExpiry]);

  function generateOtp() {
    return Math.floor(100000 + Math.random() * 900000).toString();
  }

  function handleSendOtp() {
    if (!isAuthorized) { setEmailErr("Only Mikkey1990@gmail.com is authorised."); return; }
    setEmailErr("");
    setSending(true);
    // Simulate sending delay
    setTimeout(() => {
      const otp = generateOtp();
      setGeneratedOtp(otp);
      setOtpExpiry(Date.now() + OTP_VALIDITY_SECONDS * 1000);
      setTimeLeft(OTP_VALIDITY_SECONDS);
      setOtpInput("");
      setOtpErr("");
      setStep("otp");
      setSending(false);
    }, 1200);
  }

  function handleVerifyOtp() {
    if (!otpInput.trim()) { setOtpErr("Please enter the OTP."); return; }
    if (Date.now() > otpExpiry) { setOtpErr("OTP has expired. Please request a new one."); return; }
    if (otpInput.trim() !== generatedOtp) { setOtpErr("Incorrect OTP. Please try again."); return; }
    setOtpErr("");
    setStep("password");
  }

  function handleResend() {
    setOtpInput("");
    setOtpErr("");
    setSending(true);
    setTimeout(() => {
      const otp = generateOtp();
      setGeneratedOtp(otp);
      setOtpExpiry(Date.now() + OTP_VALIDITY_SECONDS * 1000);
      setTimeLeft(OTP_VALIDITY_SECONDS);
      setSending(false);
    }, 1000);
  }

  function validatePassword() {
    const e = {};
    if (form.password.length < 8) e.password = "Password must be at least 8 characters";
    else if (!/[A-Z]/.test(form.password)) e.password = "Must contain at least one uppercase letter";
    else if (!/[0-9]/.test(form.password)) e.password = "Must contain at least one number";
    if (form.password !== form.confirm) e.confirm = "Passwords do not match";
    setPwdErrors(e);
    return Object.keys(e).length === 0;
  }

  function handleSave() {
    if (!validatePassword()) return;
    const now = localISO();
    onSave({
      email: email.trim(),
      username: emailPrefix,
      password: form.password,
      createdAt: existing?.createdAt || now,
      lastPasswordChange: now,
      history: [...(existing?.history || []), { username: existing?.username, changedAt: now }]
    });
  }

  const mins = Math.floor(timeLeft / 60).toString().padStart(2, "0");
  const secs = (timeLeft % 60).toString().padStart(2, "0");

  return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        {/* Header badge */}
        <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 20, background: "rgba(233,69,96,0.1)", borderRadius: 10, padding: "10px 14px", border: `1px solid rgba(233,69,96,0.3)` }}>
          <span style={{ fontSize: 22 }}>👑</span>
          <div>
            <div style={{ fontWeight: 700, fontSize: 14, color: COLORS.accent }}>Super Admin — {isFirst ? "Account Setup" : "Change Password"}</div>
            <div style={{ fontSize: 12, color: COLORS.muted }}>Identity verified via email OTP</div>
          </div>
        </div>

        {/* Step indicators */}
        <div style={{ display: "flex", gap: 0, marginBottom: 24 }}>
          {[["1", "Verify Email"], ["2", "Enter OTP"], ["3", "Set Password"]].map(([num, label], i) => {
            const stepMap = { email: 0, otp: 1, password: 2 };
            const current = stepMap[step];
            const done = current > i;
            const active = current === i;
            return (
              <div key={num} style={{ flex: 1, textAlign: "center" }}>
                <div style={{ width: 28, height: 28, borderRadius: "50%", background: done ? COLORS.success : active ? COLORS.accent : COLORS.card, border: `2px solid ${done ? COLORS.success : active ? COLORS.accent : COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", margin: "0 auto 6px", fontSize: 13, fontWeight: 700, color: done || active ? "#fff" : COLORS.muted }}>
                  {done ? "✓" : num}
                </div>
                <div style={{ fontSize: 11, color: active ? COLORS.text : COLORS.muted }}>{label}</div>
              </div>
            );
          })}
        </div>

        {/* ── Step 1: Email ── */}
        {step === "email" && (
          <>
            <h2 style={s.h2}>{isFirst ? "Create Super Admin Account" : "Change Password"}</h2>
            <p style={{ fontSize: 13, color: COLORS.muted, margin: "0 0 20px" }}>
              Enter the authorised email address. An OTP will be sent to verify your identity.
            </p>

            <label style={s.label}>Authorised Email ID *</label>
            <input
              style={{ ...s.input, borderColor: emailErr ? COLORS.danger : isAuthorized ? COLORS.success : COLORS.border }}
              placeholder={SUPER_ADMIN_EMAIL}
              value={email}
              onChange={e => { setEmail(e.target.value.trim()); setEmailErr(""); }}
              disabled={!isFirst && !!existing?.email}
            />
            {emailErr && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{emailErr}</div>}

            {emailPrefix && (
              <div style={{ background: COLORS.card, borderRadius: 10, padding: "10px 14px", marginBottom: 16, border: `1px solid ${isAuthorized ? COLORS.accent + "66" : COLORS.danger + "44"}`, display: "flex", alignItems: "center", gap: 10 }}>
                <span style={{ fontSize: 18 }}>{isAuthorized ? "👑" : "🚫"}</span>
                <div>
                  <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 2 }}>{isAuthorized ? "AUTHORISED — OTP WILL BE SENT TO" : "NOT AUTHORISED"}</div>
                  <div style={{ fontSize: 14, fontWeight: 700, color: isAuthorized ? COLORS.accent : COLORS.danger }}>{isAuthorized ? email : "Only Mikkey1990@gmail.com is allowed"}</div>
                </div>
              </div>
            )}

            <button
              style={{ ...s.btn, background: isAuthorized ? COLORS.accent : COLORS.muted, cursor: isAuthorized ? "pointer" : "not-allowed", opacity: sending ? 0.7 : 1 }}
              onClick={handleSendOtp}
              disabled={!isAuthorized || sending}
            >
              {sending ? "⏳ Sending OTP…" : "📧 Send OTP to Email →"}
            </button>
            {onCancel && <button style={{ ...s.btnOut, marginTop: 8 }} onClick={onCancel}>Cancel</button>}
          </>
        )}

        {/* ── Step 2: OTP ── */}
        {step === "otp" && (
          <>
            <h2 style={s.h2}>Enter OTP</h2>

            {/* Mock email preview */}
            <div style={{ background: "#0a0a1a", borderRadius: 12, padding: 16, marginBottom: 20, border: `1px solid rgba(99,102,241,0.3)` }}>
              <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 10, paddingBottom: 10, borderBottom: `1px solid ${COLORS.border}` }}>
                <span style={{ fontSize: 18 }}>📧</span>
                <div>
                  <div style={{ fontSize: 11, color: COLORS.muted }}>Simulated email to: <strong style={{ color: COLORS.text }}>{email}</strong></div>
                  <div style={{ fontSize: 11, color: COLORS.muted }}>From: noreply@recruitpro.com · Subject: Your OTP</div>
                </div>
              </div>
              <div style={{ fontSize: 13, color: COLORS.muted, marginBottom: 10 }}>Hi {emailPrefix},</div>
              <div style={{ fontSize: 13, color: COLORS.muted, marginBottom: 14 }}>Your one-time password to change your RecruitPro Super Admin credentials is:</div>
              <div style={{ background: COLORS.card, borderRadius: 10, padding: "16px", textAlign: "center", marginBottom: 10, border: `1px solid ${COLORS.accent}55` }}>
                <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 6, letterSpacing: 1 }}>YOUR OTP</div>
                <div style={{ fontSize: 36, fontWeight: 800, letterSpacing: 10, color: COLORS.gold }}>{generatedOtp}</div>
              </div>
              <div style={{ fontSize: 11, color: COLORS.muted }}>⏱ Valid for {OTP_VALIDITY_SECONDS / 60} minutes. Do not share this with anyone.</div>
            </div>

            {/* OTP input */}
            <label style={s.label}>Enter the 6-digit OTP *</label>
            <input
              style={{ ...s.input, fontSize: 24, letterSpacing: 8, textAlign: "center", fontWeight: 700, borderColor: otpErr ? COLORS.danger : COLORS.border }}
              placeholder="000000"
              value={otpInput}
              maxLength={6}
              onChange={e => { setOtpInput(e.target.value.replace(/\D/g, "")); setOtpErr(""); }}
            />
            {otpErr && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{otpErr}</div>}

            {/* Timer */}
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
              <div style={{ fontSize: 13, color: timeLeft <= 30 ? COLORS.danger : COLORS.muted }}>
                {timeLeft > 0 ? `⏱ OTP expires in ${mins}:${secs}` : "⚠️ OTP expired"}
              </div>
              <div style={{ background: COLORS.card, borderRadius: 20, height: 6, flex: 1, margin: "0 12px" }}>
                <div style={{ height: "100%", width: `${(timeLeft / OTP_VALIDITY_SECONDS) * 100}%`, background: timeLeft <= 30 ? COLORS.danger : timeLeft <= 60 ? COLORS.warning : COLORS.success, borderRadius: 20, transition: "width 1s linear" }} />
              </div>
            </div>

            <button style={{ ...s.btn, background: COLORS.accent }} onClick={handleVerifyOtp}>
              ✓ Verify OTP →
            </button>

            <div style={{ display: "flex", gap: 8, marginTop: 8 }}>
              <button style={{ ...s.btnOut, flex: 1 }} onClick={() => { setStep("email"); setOtpInput(""); setOtpErr(""); }}>← Back</button>
              <button
                style={{ ...s.btnOut, flex: 1, opacity: sending ? 0.6 : 1 }}
                onClick={handleResend}
                disabled={sending || timeLeft > 90}
              >
                {sending ? "Resending…" : timeLeft > 90 ? `Resend in ${timeLeft - 90}s` : "🔄 Resend OTP"}
              </button>
            </div>
          </>
        )}

        {/* ── Step 3: New Password ── */}
        {step === "password" && (
          <>
            <div style={{ ...s.alert("success"), marginBottom: 20 }}>
              ✅ Identity verified for <strong>{email}</strong>
            </div>

            <h2 style={s.h2}>Set New Password</h2>

            <label style={s.label}>New Password *</label>
            <input type="password" style={{ ...s.input, borderColor: pwdErrors.password ? COLORS.danger : COLORS.border }} placeholder="Min. 8 chars, 1 uppercase, 1 number" value={form.password} onChange={e => set("password", e.target.value)} />
            {pwdErrors.password && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{pwdErrors.password}</div>}

            <label style={s.label}>Confirm Password *</label>
            <input type="password" style={{ ...s.input, borderColor: pwdErrors.confirm ? COLORS.danger : COLORS.border }} placeholder="Re-enter password" value={form.confirm} onChange={e => set("confirm", e.target.value)} />
            {pwdErrors.confirm && <div style={{ color: COLORS.danger, fontSize: 12, marginTop: -12, marginBottom: 10 }}>{pwdErrors.confirm}</div>}

            {/* Strength checklist */}
            <div style={{ background: COLORS.card, borderRadius: 10, padding: "12px 14px", marginBottom: 16, fontSize: 12, border: `1px solid ${COLORS.border}` }}>
              <div style={{ fontWeight: 600, color: COLORS.text, marginBottom: 6 }}>Password requirements:</div>
              {[
                ["Minimum 8 characters", form.password.length >= 8],
                ["At least one uppercase letter", /[A-Z]/.test(form.password)],
                ["At least one number", /[0-9]/.test(form.password)],
                ["Passwords match", form.password.length > 0 && form.password === form.confirm],
              ].map(([label, met]) => (
                <div key={label} style={{ color: met ? COLORS.success : COLORS.muted, marginBottom: 3 }}>{met ? "✓" : "○"} {label}</div>
              ))}
            </div>

            <button style={{ ...s.btn, background: COLORS.accent }} onClick={handleSave}>
              👑 {isFirst ? "Create Super Admin Account →" : "Save New Password →"}
            </button>
            {onCancel && <button style={{ ...s.btnOut, marginTop: 8 }} onClick={onCancel}>Cancel</button>}
          </>
        )}
      </div>
    </div>
  );
}

// ─── Super Admin Dashboard ────────────────────────────────────────────────────
// ─── AI Briefing Card ─────────────────────────────────────────────────────────
function AiBriefingCard({ candidates, stats, panelists, dateLabel }) {
  const [briefing, setBriefing] = useState(null);
  const [loading, setLoading] = useState(false);

  async function generate() {
    setLoading(true);
    setBriefing(null);
    try {
      const topSource = ["walkin","website","referral"].map(s => ({
        s, n: candidates.filter(c => c.referBy === s).length
      })).sort((a,b) => b.n - a.n)[0];

      const prompt = `You are an HR analytics AI. Write a concise daily briefing for a recruitment super admin.

Data (${dateLabel}):
- Total candidates: ${stats.total}
- Not started tests: ${stats.notStarted}
- Aptitude failed: ${stats.aptFailed}
- Typing failed: ${stats.typingFailed}
- Cleared both tests: ${stats.cleared}
- Awaiting panel review: ${stats.pending}
- Approved: ${stats.approved}
- Rejected: ${stats.rejected}
- Active panelists: ${panelists.filter(p=>!p.disabled).length}
- Top referral source: ${topSource?.s || "none"} (${topSource?.n || 0} candidates)
- Duplicate flags: ${candidates.filter(c=>c.duplicateFlagged).length}

Write a natural-language briefing in 3 short paragraphs:
1. Overall pipeline health summary
2. Key bottleneck or highlight
3. One actionable recommendation

Keep it sharp, professional, and under 120 words total. Plain text, no markdown.`;

      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 200,
          messages: [{ role: "user", content: prompt }]
        })
      });
      const data = await res.json();
      setBriefing(data.content?.[0]?.text?.trim() || "Unable to generate briefing.");
    } catch (_) {
      setBriefing("AI briefing unavailable at the moment.");
    } finally {
      setLoading(false);
    }
  }

  return (
    <div style={{ background: "linear-gradient(135deg, rgba(99,102,241,0.1), rgba(139,92,246,0.06))", border: `1px solid rgba(99,102,241,0.25)`, borderRadius: 14, padding: "16px 20px", marginBottom: 20 }}>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: briefing || loading ? 12 : 0 }}>
        <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
          <span style={{ fontSize: 18 }}>🤖</span>
          <div>
            <div style={{ fontSize: 13, fontWeight: 700, color: "#818cf8" }}>AI Daily Briefing</div>
            <div style={{ fontSize: 11, color: COLORS.muted }}>{dateLabel}</div>
          </div>
        </div>
        <button
          onClick={generate}
          disabled={loading}
          style={{ background: loading ? "transparent" : "rgba(99,102,241,0.15)", border: `1px solid rgba(99,102,241,0.35)`, borderRadius: 8, padding: "7px 16px", color: "#818cf8", cursor: loading ? "default" : "pointer", fontSize: 13, fontWeight: 600, display: "flex", alignItems: "center", gap: 6 }}
        >
          {loading ? <><div style={{ width: 14, height: 14, border: "2px solid #818cf8", borderTop: "2px solid transparent", borderRadius: "50%", animation: "spin 0.8s linear infinite" }} /> Generating…</> : briefing ? "↺ Regenerate" : "✨ Generate Briefing"}
        </button>
      </div>
      {briefing && !loading && (
        <div style={{ fontSize: 13, color: COLORS.text, lineHeight: 1.7, whiteSpace: "pre-line" }}>
          {briefing}
        </div>
      )}
    </div>
  );
}

function SuperAdminDashboard({ candidates, setCandidates, panelists, setPanelists, superAdmin, onSuperAdminSave, alarms, setAlarms, onLogout }) {
  const [activeTab, setActiveTab] = useState("overview");
  const [changingCreds, setChangingCreds] = useState(false);
  const [confirmReset, setConfirmReset] = useState(null);
  const [addingPanelist, setAddingPanelist] = useState(false);
  const [editingPanelist, setEditingPanelist] = useState(null);
  const [alarmFilter, setAlarmFilter] = useState("all");

  // Overview local filters
  const [ovDateFrom, setOvDateFrom] = useState("");
  const [ovDateTo, setOvDateTo] = useState("");
  const [ovReferBy, setOvReferBy] = useState("all");
  const [ovRejoiner, setOvRejoiner] = useState("all");

  // All Candidates local filters
  const [acSearch, setAcSearch] = useState("");
  const [acDateFrom, setAcDateFrom] = useState("");
  const [acDateTo, setAcDateTo] = useState("");
  const [acStatus, setAcStatus] = useState("all");
  const [acReferBy, setAcReferBy] = useState("all");
  const [acRejoiner, setAcRejoiner] = useState("all");
  const [acPanelist, setAcPanelist] = useState("all");
  const [lastRefresh, setLastRefresh] = useState(new Date());
  const [liveSearch, setLiveSearch] = useState("");
  const [liveStatusFilter, setLiveStatusFilter] = useState("all");
  const [liveDateFrom, setLiveDateFrom] = useState("");
  const [liveDateTo, setLiveDateTo] = useState("");
  const [liveReferBy, setLiveReferBy] = useState("all");
  const [liveRejoiner, setLiveRejoiner] = useState("all");

  // ── Shared global filters (apply across all tabs) ─────────────────────────
  const [gDateFrom, setGDateFrom] = useState("");
  const [gDateTo, setGDateTo] = useState("");
  const [gStatus, setGStatus] = useState("all");
  const [gReferBy, setGReferBy] = useState("all");
  const [gRejoiner, setGRejoiner] = useState("all");
  const [gSearch, setGSearch] = useState("");
  const [gPanelist, setGPanelist] = useState("all");
  const [showGFilter, setShowGFilter] = useState(false);

  const gFilterActive = gDateFrom || gDateTo || gStatus !== "all" || gReferBy !== "all" || gRejoiner !== "all" || gSearch || gPanelist !== "all";

  function clearGFilters() {
    setGDateFrom(""); setGDateTo(""); setGStatus("all");
    setGReferBy("all"); setGRejoiner("all"); setGSearch("");
    setGPanelist("all");
  }

  // Apply global filters to candidates
  function applyGlobal(list) {
    return list.filter(c => {
      const regDate = localDateOf(c.registeredAt) || "";
      if (gDateFrom && regDate < gDateFrom) return false;
      if (gDateTo && regDate > gDateTo) return false;
      if (gReferBy !== "all" && c.referBy !== gReferBy) return false;
      if (gRejoiner !== "all" && c.isRejoiner !== gRejoiner) return false;
      if (gPanelist !== "all" && c.assignedPanelistId !== gPanelist) return false;
      if (gSearch && !c.name.toLowerCase().includes(gSearch.toLowerCase()) &&
          !c.mobile.includes(gSearch) &&
          !c.username?.toLowerCase().includes(gSearch.toLowerCase()) &&
          !c.pan?.toLowerCase().includes(gSearch.toLowerCase())) return false;
      if (gStatus !== "all") {
        if (gStatus === "notStarted" && c.aptScore != null) return false;
        if (gStatus === "aptFailed" && !(c.aptScore != null && c.aptScore < 10)) return false;
        if (gStatus === "typingFailed" && !(c.aptScore >= 10 && c.typingScore && !c.typingScore.passed)) return false;
        if (gStatus === "cleared" && !(c.aptScore >= 10 && c.typingScore?.passed)) return false;
        if (gStatus === "pending" && !(c.aptScore >= 10 && c.typingScore?.passed && c.panelStatus === "pending")) return false;
        if (gStatus === "approved" && c.panelStatus !== "approved") return false;
        if (gStatus === "rejected" && c.panelStatus !== "rejected") return false;
      }
      return true;
    });
  }

  const gCandidates = applyGlobal(candidates);

  // ── Auto-refresh every 5 seconds ──────────────────────────────────────────
  useEffect(() => {
    const interval = setInterval(async () => {
      try {
        const fresh = await loadCandidates();
        const freshAlarms = await loadAlarms();
        setCandidates(fresh);
        setAlarms(freshAlarms);
        setLastRefresh(new Date());
      } catch (_) {}
    }, 5000);
    return () => clearInterval(interval);
  }, []);

  // Summary tab filters
  const [sumMode, setSumMode] = useState("day"); // "day" | "range"
  const [sumDate, setSumDate] = useState(todayStr());
  const [sumFrom, setSumFrom] = useState("");
  const [sumTo, setSumTo] = useState("");
  const [expFromDate, setExpFromDate] = useState("");
  const [expToDate, setExpToDate] = useState("");
  const [expStatus, setExpStatus] = useState("all");
  const [expReferBy, setExpReferBy] = useState("all");
  const [expRejoiner, setExpRejoiner] = useState("all");
  const [expTestResult, setExpTestResult] = useState("all");
  const [expPanel, setExpPanel] = useState("all");
  const [expPreview, setExpPreview] = useState(false);

  if (changingCreds) return <SuperAdminSetup existing={superAdmin} onSave={cred => { onSuperAdminSave(cred); setChangingCreds(false); }} onCancel={() => setChangingCreds(false)} />;
  if (addingPanelist) return <PanelistSetup existing={null} onSave={cred => { setPanelists(p => [...p, cred]); setAddingPanelist(false); }} onCancel={() => setAddingPanelist(false)} />;
  if (editingPanelist) return <PanelistSetup existing={editingPanelist} onSave={cred => { setPanelists(p => p.map(x => x.id === cred.id ? cred : x)); setEditingPanelist(null); }} onCancel={() => setEditingPanelist(null)} />;

  const stats = {
    total: gCandidates.length,
    cleared: gCandidates.filter(c => c.aptScore >= 10 && c.typingScore?.passed).length,
    approved: gCandidates.filter(c => c.panelStatus === "approved").length,
    rejected: gCandidates.filter(c => c.panelStatus === "rejected").length,
    aptFailed: gCandidates.filter(c => c.aptScore != null && c.aptScore < 10).length,
    typingFailed: gCandidates.filter(c => c.aptScore >= 10 && c.typingScore && !c.typingScore.passed).length,
    pending: gCandidates.filter(c => c.aptScore >= 10 && c.typingScore?.passed && c.panelStatus === "pending").length,
  };

  // Load per panelist using gCandidates
  const panelistLoad = {};
  panelists.forEach(p => { panelistLoad[p.id] = { total: 0, pending: 0, approved: 0, rejected: 0 }; });
  gCandidates.forEach(c => {
    if (c.assignedPanelistId && panelistLoad[c.assignedPanelistId]) {
      panelistLoad[c.assignedPanelistId].total++;
      if (c.panelStatus === "pending") panelistLoad[c.assignedPanelistId].pending++;
      if (c.panelStatus === "approved") panelistLoad[c.assignedPanelistId].approved++;
      if (c.panelStatus === "rejected") panelistLoad[c.assignedPanelistId].rejected++;
    }
  });

  function deleteCandidate(id) {
    setCandidates(p => p.filter(c => c.id !== id));
    deleteCandidateRow(id);
    setConfirmReset(null);
  }

  function resetCandidateTests(id) {
    setCandidates(p => p.map(c => c.id === id ? { ...c, aptScore: null, aptCompletedAt: null, typingScore: null, typingCompletedAt: null, panelStatus: "pending", panelRemark: "", panelDecidedAt: null } : c));
    setConfirmReset(null);
  }

  function resetCandidatePassword(id) {
    const newPwd = `Rec@${Math.floor(100 + Math.random() * 900)}${Math.floor(10 + Math.random() * 90)}`;
    setCandidates(p => p.map(c => c.id === id ? { ...c, password: newPwd, passwordResetAt: localISO() } : c));
    setConfirmReset(prev => ({ ...prev, newPassword: newPwd, done: true }));
  }

  return (
    <div style={{ ...s.page, alignItems: "stretch", width: "100%", maxWidth: 1400, margin: "0 auto", padding: "16px 12px 60px" }}>
      {/* Header */}
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", padding: "20px 0 16px" }}>
        <div style={{ display: "flex", alignItems: "center", gap: 12 }}>
          <Logo />
          <div style={{ background: "rgba(233,69,96,0.15)", border: `1px solid rgba(233,69,96,0.4)`, borderRadius: 20, padding: "3px 12px", fontSize: 12, fontWeight: 700, color: COLORS.accent }}>👑 Super Admin</div>
          {/* Live indicator */}
          <div style={{ display: "flex", alignItems: "center", gap: 6, background: "rgba(34,197,94,0.1)", border: "1px solid rgba(34,197,94,0.3)", borderRadius: 20, padding: "3px 10px" }}>
            <span style={{ width: 7, height: 7, borderRadius: "50%", background: COLORS.success, display: "inline-block", animation: "pulse 2s infinite" }} />
            <span style={{ fontSize: 11, fontWeight: 600, color: COLORS.success }}>LIVE</span>
            <span style={{ fontSize: 10, color: COLORS.muted }}>· {lastRefresh.toLocaleTimeString("en-IN", { hour: "2-digit", minute: "2-digit", second: "2-digit" })}</span>
          </div>
        </div>
        <div style={{ display: "flex", gap: 8 }}>
          <button onClick={() => setChangingCreds(true)} style={{ background: "none", border: `1px solid ${COLORS.border}`, borderRadius: 8, padding: "7px 12px", color: COLORS.muted, cursor: "pointer", fontSize: 12 }}>🔄 My Credentials</button>
          <button onClick={onLogout} style={{ background: "none", border: `1px solid ${COLORS.border}`, borderRadius: 8, padding: "7px 14px", color: COLORS.muted, cursor: "pointer", fontSize: 13 }}>Logout</button>
        </div>
      </div>

      {/* ── Global Filter Bar ── */}
      <div style={{ marginBottom: 16 }}>
        <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: showGFilter ? 12 : 0 }}>
          <button
            onClick={() => setShowGFilter(p => !p)}
            style={{ display: "flex", alignItems: "center", gap: 7, background: gFilterActive ? "rgba(233,69,96,0.12)" : COLORS.card, border: `1px solid ${gFilterActive ? "rgba(233,69,96,0.4)" : COLORS.border}`, borderRadius: 10, padding: "8px 16px", color: gFilterActive ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 13, fontWeight: 600 }}
          >
            <span>🔍</span>
            <span>{showGFilter ? "Hide Filters" : "Global Filters"}</span>
            {gFilterActive && <span style={{ background: COLORS.accent, color: "#fff", borderRadius: "50%", width: 18, height: 18, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 10, fontWeight: 800 }}>
              {[gDateFrom, gDateTo, gStatus !== "all", gReferBy !== "all", gRejoiner !== "all", gSearch, gPanelist !== "all"].filter(Boolean).length}
            </span>}
          </button>
          {gFilterActive && (
            <>
              <div style={{ display: "flex", gap: 6, flexWrap: "wrap", flex: 1 }}>
                {gDateFrom && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: COLORS.text }}>From: {gDateFrom}</span>}
                {gDateTo && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: COLORS.text }}>To: {gDateTo}</span>}
                {gStatus !== "all" && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: COLORS.text }}>Status: {gStatus}</span>}
                {gReferBy !== "all" && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: COLORS.text }}>Ref: {gReferBy}</span>}
                {gRejoiner !== "all" && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: COLORS.text }}>{gRejoiner === "Yes" ? "Rejoiner" : "Fresh"}</span>}
                {gPanelist !== "all" && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: "#3498db" }}>🎯 {panelists.find(p => p.id === gPanelist)?.name || panelists.find(p => p.id === gPanelist)?.username}</span>}
                {gSearch && <span style={{ background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 20, padding: "3px 10px", fontSize: 11, color: COLORS.text }}>"{gSearch}"</span>}
              </div>
              <span style={{ fontSize: 12, color: COLORS.muted, whiteSpace: "nowrap" }}>{gCandidates.length} / {candidates.length} candidates</span>
              <button onClick={clearGFilters} style={{ background: "rgba(233,69,96,0.1)", border: `1px solid rgba(233,69,96,0.3)`, borderRadius: 8, padding: "6px 12px", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}>✕ Clear All</button>
              <DownloadBtn rows={gCandidates} filename={`recruitpro-global-filter-${todayStr()}.csv`} panelists={panelists} label="Download Filtered" />
            </>
          )}
        </div>

        {showGFilter && (
          <div style={{ background: COLORS.card, borderRadius: 14, padding: "18px 20px", border: `1px solid ${COLORS.border}` }}>
            <div style={{ display: "flex", gap: 10, marginBottom: 14, flexWrap: "wrap", alignItems: "flex-end" }}>
              <div style={{ flex: 1, minWidth: 180 }}>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>SEARCH</div>
                <input style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "8px 12px" }} placeholder="Name, mobile or PAN..." value={gSearch} onChange={e => setGSearch(e.target.value)} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>FROM DATE</div>
                <input type="date" value={gDateFrom} onChange={e => setGDateFrom(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "8px 12px", width: 150 }} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TO DATE</div>
                <input type="date" value={gDateTo} onChange={e => setGDateTo(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "8px 12px", width: 150 }} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>QUICK DATE</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["Today", () => { const t = todayStr(); setGDateFrom(t); setGDateTo(t); }],
                    ["Yesterday", () => { const y = (() => { const d = new Date(Date.now()-86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })(); setGDateFrom(y); setGDateTo(y); }],
                    ["Last 7d", () => { setGDateFrom((() => { const d = new Date(Date.now()-7*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })()); setGDateTo(todayStr()); }],
                    ["This Month", () => { const n = new Date(); setGDateFrom(`${n.getFullYear()}-${String(n.getMonth()+1).padStart(2,"0")}-01`); setGDateTo(todayStr()); }],
                    ["All", () => { setGDateFrom(""); setGDateTo(""); }],
                  ].map(([l, fn]) => (
                    <button key={l} onClick={fn} style={{ padding: "7px 10px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
            </div>
            <div style={{ display: "flex", gap: 16, flexWrap: "wrap" }}>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>STATUS</div>
                <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
                  {[["all","All",COLORS.muted],["notStarted","Not Started",COLORS.muted],["aptFailed","Apt Failed",COLORS.danger],["typingFailed","Typing Failed",COLORS.warning],["cleared","Cleared",COLORS.success],["pending","⏳ Pending",COLORS.warning],["approved","✅ Approved",COLORS.success],["rejected","❌ Rejected",COLORS.danger]].map(([v,l,c]) => (
                    <button key={v} onClick={() => setGStatus(v)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${gStatus === v ? c : COLORS.border}`, background: gStatus === v ? c+"22" : "transparent", color: gStatus === v ? c : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600, whiteSpace: "nowrap" }}>{l}</button>
                  ))}
                </div>
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>REFERRED BY</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All"],["walkin","Walk-in"],["website","Website"],["referral","Referral"]].map(([v,l]) => (
                    <button key={v} onClick={() => setGReferBy(v)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${gReferBy === v ? COLORS.accent : COLORS.border}`, background: gReferBy === v ? "rgba(233,69,96,0.15)" : "transparent", color: gReferBy === v ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>TYPE</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All"],["No","Fresh"],["Yes","Rejoiner"]].map(([v,l]) => (
                    <button key={v} onClick={() => setGRejoiner(v)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${gRejoiner === v ? COLORS.gold : COLORS.border}`, background: gRejoiner === v ? "rgba(245,166,35,0.15)" : "transparent", color: gRejoiner === v ? COLORS.gold : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
              {panelists.length > 0 && (
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>PANELIST</div>
                  <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
                    <button onClick={() => setGPanelist("all")} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${gPanelist === "all" ? "#3498db" : COLORS.border}`, background: gPanelist === "all" ? "rgba(52,152,219,0.15)" : "transparent", color: gPanelist === "all" ? "#3498db" : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>All</button>
                    {panelists.map(p => (
                      <button key={p.id} onClick={() => setGPanelist(p.id)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${gPanelist === p.id ? "#3498db" : COLORS.border}`, background: gPanelist === p.id ? "rgba(52,152,219,0.15)" : "transparent", color: gPanelist === p.id ? "#3498db" : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>🎯 {p.name || p.username}</button>
                    ))}
                  </div>
                </div>
              )}
            </div>
          </div>
        )}
      </div>

      {/* Tabs */}
      <div style={s.navTabs}>
        {[["live", "🔴 Live View"], ["overview", "📊 Overview"], ["summary", "📈 Summary"], ["candidates", "👤 All Candidates"], ["panelist", "🎯 Panelist Control"], ["audit", "📋 Audit Log"], ["alarms", `🚨 Alarms${alarms.filter(a => !a.resolved).length > 0 ? ` (${alarms.filter(a => !a.resolved).length})` : ""}`], ["export", "⬇ Export Data"]].map(([key, label]) => (
          <button key={key} style={{ ...s.tab(activeTab === key), ...(key === "alarms" && alarms.filter(a => !a.resolved).length > 0 ? { color: activeTab === key ? COLORS.danger : COLORS.warning } : {}), ...(key === "live" ? { color: activeTab === key ? COLORS.success : "#4ade80" } : {}), ...(key === "summary" ? { color: activeTab === key ? "#f59e0b" : "#fbbf24" } : {}) }} onClick={() => setActiveTab(key)}>{label}</button>
        ))}
      </div>

      {/* ── Live View Tab ── */}
      {activeTab === "live" && (() => {
        // Candidate status pipeline
        const getStatus = (c) => {
          if (c.panelStatus === "approved") return { label: "✅ Approved", stage: 6, color: COLORS.success, bg: "rgba(46,204,113,0.12)" };
          if (c.panelStatus === "rejected") return { label: "❌ Rejected", stage: 6, color: COLORS.danger, bg: "rgba(231,76,60,0.12)" };
          if (c.aptScore >= 10 && c.typingScore?.passed) return { label: "⏳ Awaiting Panel", stage: 5, color: COLORS.warning, bg: "rgba(243,156,18,0.12)" };
          if (c.aptScore >= 10 && c.typingScore && !c.typingScore.passed) return { label: "❌ Typing Failed", stage: 4, color: COLORS.danger, bg: "rgba(231,76,60,0.12)" };
          if (c.aptScore >= 10 && !c.typingScore) return { label: "⌨️ Typing Pending", stage: 4, color: "#3498db", bg: "rgba(52,152,219,0.12)" };
          if (c.aptScore != null && c.aptScore < 10) return { label: "❌ Apt Failed", stage: 3, color: COLORS.danger, bg: "rgba(231,76,60,0.12)" };
          if (c.aptScore == null) return { label: "🧠 Tests Pending", stage: 2, color: COLORS.muted, bg: "rgba(136,146,164,0.1)" };
          return { label: "📝 Registered", stage: 1, color: COLORS.muted, bg: "rgba(136,146,164,0.1)" };
        };

        const PIPELINE_STAGES = ["Registered", "Logged In", "Aptitude", "Typing", "Panel Review", "Decision"];

        const filteredLive = candidates
          .filter(c => {
            const regDate = localDateOf(c.registeredAt) || "";
            if (liveDateFrom && regDate < liveDateFrom) return false;
            if (liveDateTo && regDate > liveDateTo) return false;
            if (liveReferBy !== "all" && c.referBy !== liveReferBy) return false;
            if (liveRejoiner !== "all" && c.isRejoiner !== liveRejoiner) return false;
            if (liveStatusFilter !== "all") {
              const st = getStatus(c);
              if (liveStatusFilter === "registered" && st.stage > 2) return false;
              if (liveStatusFilter === "testing" && (st.stage < 3 || st.stage > 4)) return false;
              if (liveStatusFilter === "panel" && st.stage !== 5) return false;
              if (liveStatusFilter === "approved" && c.panelStatus !== "approved") return false;
              if (liveStatusFilter === "rejected" && c.panelStatus !== "rejected") return false;
              if (liveStatusFilter === "decided" && st.stage !== 6) return false;
            }
            if (liveSearch && !c.name.toLowerCase().includes(liveSearch.toLowerCase()) && !c.mobile.includes(liveSearch) && !c.pan?.toLowerCase().includes(liveSearch.toLowerCase()) && !c.username?.toLowerCase().includes(liveSearch.toLowerCase())) return false;
            return true;
          })
          .sort((a, b) => new Date(b.registeredAt) - new Date(a.registeredAt));

        const todayCands = candidates.filter(c => localDateOf(c.registeredAt) === todayStr());
        const lastReg = [...candidates].sort((a, b) => new Date(b.registeredAt) - new Date(a.registeredAt))[0];

        return (
          <div>
            {/* Today's summary strip */}
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10, marginBottom: 16 }}>
              {[
                ["📅 Today's Registrations", todayCands.length, COLORS.gold],
                ["🧠 In Testing", candidates.filter(c => c.aptScore == null || (c.aptScore >= 10 && !c.typingScore)).length, "#3498db"],
                ["⏳ Awaiting Panel", stats.pending, COLORS.warning],
                ["✅ Decided Today", candidates.filter(c => localDateOf(c.panelDecidedAt) === todayStr()).length, COLORS.success],
              ].map(([l, v, c]) => (
                <div key={l} style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", border: `1px solid ${COLORS.border}` }}>
                  <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>{l}</div>
                  <div style={{ fontSize: 26, fontWeight: 800, color: c }}>{v}</div>
                </div>
              ))}
            </div>

            {/* Last registered */}
            {lastReg && (
              <div style={{ background: "linear-gradient(135deg, rgba(233,69,96,0.1), rgba(233,69,96,0.04))", border: `1px solid rgba(233,69,96,0.3)`, borderRadius: 14, padding: "14px 18px", marginBottom: 16, display: "flex", alignItems: "center", gap: 14 }}>
                {lastReg.photoData
                  ? <img src={lastReg.photoData} alt="" style={{ width: 48, height: 48, borderRadius: "50%", objectFit: "cover", border: `2px solid ${COLORS.accent}`, flexShrink: 0 }} />
                  : <div style={{ width: 48, height: 48, borderRadius: "50%", background: COLORS.card, border: `2px solid ${COLORS.accent}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 22, flexShrink: 0 }}>👤</div>}
                <div style={{ flex: 1 }}>
                  <div style={{ fontSize: 11, color: COLORS.accent, fontWeight: 700, marginBottom: 3, letterSpacing: 0.5 }}>🆕 LATEST REGISTRATION</div>
                  <div style={{ fontSize: 15, fontWeight: 700, color: COLORS.text }}>{lastReg.name}</div>
                  <div style={{ fontSize: 12, color: COLORS.muted }}>📱 {lastReg.mobile} · {lastReg.referBy} · {fmtTs(lastReg.registeredAt)}</div>
                </div>
                <div style={{ ...getStatus(lastReg), background: getStatus(lastReg).bg, borderRadius: 20, padding: "5px 14px", fontSize: 12, fontWeight: 700, color: getStatus(lastReg).color, flexShrink: 0 }}>
                  {getStatus(lastReg).label}
                </div>
              </div>
            )}

            {/* ── Filter Panel ── */}
            <div style={{ background: COLORS.card, borderRadius: 14, padding: "16px 18px", marginBottom: 14, border: `1px solid ${COLORS.border}` }}>
              {/* Row 1: Search + active filters count + clear */}
              <div style={{ display: "flex", gap: 10, marginBottom: 12, alignItems: "center" }}>
                <input
                  style={{ ...s.input, marginBottom: 0, flex: 1, fontSize: 13, padding: "9px 14px" }}
                  placeholder="🔍 Search by name or mobile..."
                  value={liveSearch}
                  onChange={e => setLiveSearch(e.target.value)}
                />
                {(liveDateFrom || liveDateTo || liveReferBy !== "all" || liveRejoiner !== "all" || liveStatusFilter !== "all" || liveSearch) && (
                  <button
                    onClick={() => { setLiveSearch(""); setLiveDateFrom(""); setLiveDateTo(""); setLiveReferBy("all"); setLiveRejoiner("all"); setLiveStatusFilter("all"); }}
                    style={{ background: "rgba(233,69,96,0.1)", border: `1px solid rgba(233,69,96,0.3)`, borderRadius: 8, padding: "9px 14px", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}
                  >✕ Clear All</button>
                )}
                <div style={{ fontSize: 12, color: COLORS.muted, whiteSpace: "nowrap" }}>
                  Showing <strong style={{ color: COLORS.text }}>{filteredLive.length}</strong> of {candidates.length}
                </div>
                <DownloadBtn rows={filteredLive} filename={`recruitpro-live-${todayStr()}.csv`} panelists={panelists} label="Download" />
              </div>

              {/* Row 2: Date range */}
              <div style={{ display: "flex", gap: 10, marginBottom: 12, alignItems: "flex-end", flexWrap: "wrap" }}>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>FROM DATE</div>
                  <input
                    type="date"
                    value={liveDateFrom}
                    onChange={e => setLiveDateFrom(e.target.value)}
                    style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 150 }}
                  />
                </div>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TO DATE</div>
                  <input
                    type="date"
                    value={liveDateTo}
                    onChange={e => setLiveDateTo(e.target.value)}
                    style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 150 }}
                  />
                </div>
                {/* Quick date shortcuts */}
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>QUICK</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {[
                      ["Today", () => { const t = todayStr(); setLiveDateFrom(t); setLiveDateTo(t); }],
                      ["Yesterday", () => { const y = (() => { const d = new Date(Date.now() - 86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })(); setLiveDateFrom(y); setLiveDateTo(y); }],
                      ["Last 7d", () => { setLiveDateFrom((() => { const d = new Date(Date.now() - 7*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })()); setLiveDateTo(todayStr()); }],
                      ["This Month", () => { const now = new Date(); setLiveDateFrom(`${now.getFullYear()}-${String(now.getMonth()+1).padStart(2,"0")}-01`); setLiveDateTo(todayStr()); }],
                      ["All", () => { setLiveDateFrom(""); setLiveDateTo(""); }],
                    ].map(([label, fn]) => (
                      <button key={label} onClick={fn} style={{ padding: "6px 10px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600, whiteSpace: "nowrap" }}>{label}</button>
                    ))}
                  </div>
                </div>
              </div>

              {/* Row 3: Status + ReferBy + Rejoiner */}
              <div style={{ display: "flex", gap: 16, flexWrap: "wrap", alignItems: "flex-start" }}>
                {/* Status filter */}
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>STATUS</div>
                  <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
                    {[
                      ["all", "All", COLORS.muted],
                      ["registered", "📝 Registered", COLORS.muted],
                      ["testing", "🧠 Testing", "#3498db"],
                      ["panel", "⏳ Panel", COLORS.warning],
                      ["approved", "✅ Approved", COLORS.success],
                      ["rejected", "❌ Rejected", COLORS.danger],
                    ].map(([v, l, c]) => (
                      <button key={v} onClick={() => setLiveStatusFilter(v)} style={{ padding: "6px 12px", borderRadius: 20, border: `1px solid ${liveStatusFilter === v ? c : COLORS.border}`, background: liveStatusFilter === v ? c + "22" : "transparent", color: liveStatusFilter === v ? c : COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}>{l}</button>
                    ))}
                  </div>
                </div>

                {/* Referred By */}
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>REFERRED BY</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {[["all","All"],["walkin","Walk-in"],["website","Website"],["referral","Referral"]].map(([v, l]) => (
                      <button key={v} onClick={() => setLiveReferBy(v)} style={{ padding: "6px 12px", borderRadius: 20, border: `1px solid ${liveReferBy === v ? COLORS.accent : COLORS.border}`, background: liveReferBy === v ? "rgba(233,69,96,0.15)" : "transparent", color: liveReferBy === v ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600 }}>{l}</button>
                    ))}
                  </div>
                </div>

                {/* Rejoiner */}
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>CANDIDATE TYPE</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {[["all","All"],["No","Fresh"],["Yes","Rejoiner"]].map(([v, l]) => (
                      <button key={v} onClick={() => setLiveRejoiner(v)} style={{ padding: "6px 12px", borderRadius: 20, border: `1px solid ${liveRejoiner === v ? COLORS.gold : COLORS.border}`, background: liveRejoiner === v ? "rgba(245,166,35,0.15)" : "transparent", color: liveRejoiner === v ? COLORS.gold : COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600 }}>{l}</button>
                    ))}
                  </div>
                </div>
              </div>
            </div>

            {/* Candidate pipeline cards */}
            <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
              {filteredLive.length === 0 ? (
                <div style={{ textAlign: "center", padding: "40px 0", color: COLORS.muted }}>
                  <div style={{ fontSize: 40, marginBottom: 10 }}>👥</div>
                  <p>No candidates match the filter.</p>
                </div>
              ) : filteredLive.map(c => {
                const st = getStatus(c);
                const assignedP = panelists.find(p => p.id === c.assignedPanelistId);
                return (
                  <div key={c.id} style={{ background: COLORS.card, borderRadius: 14, padding: "16px 18px", border: `1px solid ${COLORS.border}` }}>
                    {/* Row 1: photo + name + status badge */}
                    <div style={{ display: "flex", alignItems: "center", gap: 12, marginBottom: 12 }}>
                      {c.photoData
                        ? <img src={c.photoData} alt="" style={{ width: 44, height: 44, borderRadius: "50%", objectFit: "cover", border: `2px solid ${st.color}44`, flexShrink: 0 }} />
                        : <div style={{ width: 44, height: 44, borderRadius: "50%", background: COLORS.surface, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 20, flexShrink: 0 }}>👤</div>}
                      <div style={{ flex: 1 }}>
                        <div style={{ display: "flex", alignItems: "center", gap: 8, flexWrap: "wrap" }}>
                          <span style={{ fontWeight: 700, fontSize: 15, color: COLORS.text }}>{c.name}</span>
                          <span style={{ fontSize: 12, color: COLORS.muted }}>🪪 {c.username}</span>
                          {c.duplicateFlagged && <span style={{ background: "rgba(231,76,60,0.15)", color: COLORS.danger, borderRadius: 20, padding: "2px 8px", fontSize: 11, fontWeight: 700 }}>⚠ Flagged</span>}
                          {c.isRejoiner === "Yes" && <span style={{ background: "rgba(243,156,18,0.12)", color: COLORS.warning, borderRadius: 20, padding: "2px 8px", fontSize: 11, fontWeight: 600 }}>↩ Rejoiner</span>}
                        </div>
                        <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 2 }}>📱 {c.mobile} · {c.referBy}{c.empId ? ` (${c.empId})` : ""} · Registered {fmtTs(c.registeredAt)}</div>
                      </div>
                      <div style={{ background: st.bg, borderRadius: 20, padding: "5px 14px", fontSize: 12, fontWeight: 700, color: st.color, flexShrink: 0, border: `1px solid ${st.color}33` }}>{st.label}</div>
                    </div>

                    {/* Pipeline progress bar */}
                    <div style={{ marginBottom: 10 }}>
                      <div style={{ display: "flex", gap: 3 }}>
                        {PIPELINE_STAGES.map((stage, i) => {
                          const active = i < st.stage;
                          const current = i === st.stage - 1;
                          return (
                            <div key={stage} style={{ flex: 1 }}>
                              <div style={{ height: 5, background: active ? (st.stage === 6 && c.panelStatus === "rejected" && i === 5 ? COLORS.danger : st.color) : COLORS.border, borderRadius: 3, marginBottom: 4, opacity: current ? 1 : active ? 0.7 : 0.3 }} />
                              <div style={{ fontSize: 9, color: active ? st.color : COLORS.muted, textAlign: "center", fontWeight: current ? 700 : 400, whiteSpace: "nowrap", overflow: "hidden", textOverflow: "ellipsis" }}>{stage}</div>
                            </div>
                          );
                        })}
                      </div>
                    </div>

                    {/* Score + panelist row */}
                    <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>
                      <div style={{ background: COLORS.surface, borderRadius: 8, padding: "6px 12px", fontSize: 12, display: "flex", gap: 6, alignItems: "center" }}>
                        <span style={{ color: COLORS.muted }}>Apt:</span>
                        <span style={{ fontWeight: 700, color: c.aptScore == null ? COLORS.muted : c.aptScore >= 10 ? COLORS.success : COLORS.danger }}>{c.aptScore != null ? `${c.aptScore}/15` : "—"}</span>
                      </div>
                      <div style={{ background: COLORS.surface, borderRadius: 8, padding: "6px 12px", fontSize: 12, display: "flex", gap: 6, alignItems: "center" }}>
                        <span style={{ color: COLORS.muted }}>Typing:</span>
                        <span style={{ fontWeight: 700, color: !c.typingScore ? COLORS.muted : c.typingScore.passed ? COLORS.success : COLORS.danger }}>{c.typingScore ? `${c.typingScore.wpm}wpm / ${c.typingScore.accuracy}%` : "—"}</span>
                      </div>
                      {assignedP && (
                        <div style={{ background: "rgba(52,152,219,0.1)", borderRadius: 8, padding: "6px 12px", fontSize: 12, display: "flex", gap: 6, alignItems: "center", border: "1px solid rgba(52,152,219,0.2)" }}>
                          <span style={{ color: COLORS.muted }}>Panelist:</span>
                          <span style={{ fontWeight: 700, color: "#3498db" }}>{assignedP.name || assignedP.username}</span>
                        </div>
                      )}
                      {c.panelStatus !== "pending" && c.panelDecidedAt && (
                        <div style={{ background: COLORS.surface, borderRadius: 8, padding: "6px 12px", fontSize: 12, color: COLORS.muted }}>
                          Decided: {fmtTs(c.panelDecidedAt)}
                        </div>
                      )}
                      {c.panelRemark && (
                        <div style={{ background: COLORS.surface, borderRadius: 8, padding: "6px 12px", fontSize: 12, color: COLORS.muted, fontStyle: "italic" }}>
                          "{c.panelRemark}"
                        </div>
                      )}
                    </div>
                  </div>
                );
              })}
            </div>
          </div>
        );
      })()}

      {/* ── Overview ── */}
      {activeTab === "overview" && (() => {
        // Overview uses raw candidates (not gCandidates) so stats are never hidden by global filters
        // Only overview-local date/referBy/rejoiner filters apply
        const ovBase = candidates.filter(c => {
          const d = localDateOf(c.registeredAt) || "";
          if (ovDateFrom && d < ovDateFrom) return false;
          if (ovDateTo && d > ovDateTo) return false;
          if (ovReferBy !== "all" && c.referBy !== ovReferBy) return false;
          if (ovRejoiner !== "all" && c.isRejoiner !== ovRejoiner) return false;
          return true;
        });
        const ovStats = {
          total: ovBase.length,
          cleared: ovBase.filter(c => c.aptScore >= 10 && c.typingScore?.passed).length,
          approved: ovBase.filter(c => c.panelStatus === "approved").length,
          rejected: ovBase.filter(c => c.panelStatus === "rejected").length,
          aptFailed: ovBase.filter(c => c.aptScore != null && c.aptScore < 10).length,
          typingFailed: ovBase.filter(c => c.aptScore >= 10 && c.typingScore && !c.typingScore.passed).length,
          pending: ovBase.filter(c => c.aptScore >= 10 && c.typingScore?.passed && c.panelStatus === "pending").length,
          notStarted: ovBase.filter(c => c.aptScore == null).length,
        };
        const ovLoad = {};
        panelists.forEach(p => { ovLoad[p.id] = { total: 0, pending: 0, approved: 0, rejected: 0 }; });
        ovBase.forEach(c => {
          if (c.assignedPanelistId && ovLoad[c.assignedPanelistId]) {
            ovLoad[c.assignedPanelistId].total++;
            if (c.panelStatus === "pending") ovLoad[c.assignedPanelistId].pending++;
            if (c.panelStatus === "approved") ovLoad[c.assignedPanelistId].approved++;
            if (c.panelStatus === "rejected") ovLoad[c.assignedPanelistId].rejected++;
          }
        });
        const ovFilterActive = ovDateFrom || ovDateTo || ovReferBy !== "all" || ovRejoiner !== "all";

        return (
          <div>
            {/* Warn if global filter is active — Overview uses raw data, but user may be confused */}
            {gFilterActive && (
              <div style={{ background:"rgba(243,156,18,0.1)", border:`1px solid rgba(243,156,18,0.35)`, borderRadius:10, padding:"10px 14px", marginBottom:14, fontSize:12, color:COLORS.warning, display:"flex", alignItems:"center", gap:8 }}>
                <span>⚠️</span>
                <span><strong>Note:</strong> Overview stats show <strong>all candidates</strong> matching the local date filter — global filters (status, search, panelist) do not affect Overview counts.</span>
              </div>
            )}
            {/* ── AI Daily Briefing ── */}
            <AiBriefingCard candidates={ovBase} stats={ovStats} panelists={panelists} dateLabel={ovFilterActive ? `${ovDateFrom||"start"} → ${ovDateTo||"today"}` : "All Time"} />

            {/* ── Overview Filter Panel ── */}
            <div style={{ background: COLORS.card, borderRadius: 14, padding: "14px 18px", marginBottom: 16, border: `1px solid ${COLORS.border}` }}>
              <div style={{ display: "flex", gap: 10, flexWrap: "wrap", alignItems: "flex-end" }}>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>FROM DATE</div>
                  <input type="date" value={ovDateFrom} onChange={e => setOvDateFrom(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
                </div>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TO DATE</div>
                  <input type="date" value={ovDateTo} onChange={e => setOvDateTo(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
                </div>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>QUICK</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {[["Today", () => { const t = todayStr(); setOvDateFrom(t); setOvDateTo(t); }],
                      ["Yesterday", () => { const y = (() => { const d = new Date(Date.now()-86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })(); setOvDateFrom(y); setOvDateTo(y); }],
                      ["Last 7d", () => { setOvDateFrom((() => { const d = new Date(Date.now()-7*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })()); setOvDateTo(todayStr()); }],
                      ["This Month", () => { const n = new Date(); setOvDateFrom(`${n.getFullYear()}-${String(n.getMonth()+1).padStart(2,"0")}-01`); setOvDateTo(todayStr()); }],
                      ["All", () => { setOvDateFrom(""); setOvDateTo(""); }],
                    ].map(([l, fn]) => (
                      <button key={l} onClick={fn} style={{ padding: "6px 10px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                    ))}
                  </div>
                </div>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>REFERRED BY</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {[["all","All"],["walkin","Walk-in"],["website","Website"],["referral","Referral"]].map(([v,l]) => (
                      <button key={v} onClick={() => setOvReferBy(v)} style={{ padding: "6px 10px", borderRadius: 20, border: `1px solid ${ovReferBy === v ? COLORS.accent : COLORS.border}`, background: ovReferBy === v ? "rgba(233,69,96,0.15)" : "transparent", color: ovReferBy === v ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                    ))}
                  </div>
                </div>
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TYPE</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {[["all","All"],["No","Fresh"],["Yes","Rejoiner"]].map(([v,l]) => (
                      <button key={v} onClick={() => setOvRejoiner(v)} style={{ padding: "6px 10px", borderRadius: 20, border: `1px solid ${ovRejoiner === v ? COLORS.gold : COLORS.border}`, background: ovRejoiner === v ? "rgba(245,166,35,0.15)" : "transparent", color: ovRejoiner === v ? COLORS.gold : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                    ))}
                  </div>
                </div>
                {ovFilterActive && (
                  <button onClick={() => { setOvDateFrom(""); setOvDateTo(""); setOvReferBy("all"); setOvRejoiner("all"); }} style={{ padding: "7px 12px", borderRadius: 8, border: `1px solid rgba(233,69,96,0.3)`, background: "rgba(233,69,96,0.08)", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600, alignSelf: "flex-end" }}>✕ Clear</button>
                )}
                <div style={{ marginLeft: "auto", fontSize: 12, color: COLORS.muted, alignSelf: "flex-end", paddingBottom: 2 }}>
                  {ovFilterActive ? <span style={{ color: COLORS.accent, fontWeight: 600 }}>{ovBase.length}/{gCandidates.length} shown</span> : <span>{gCandidates.length} candidates</span>}
                </div>
                <div style={{ alignSelf: "flex-end" }}>
                  <DownloadBtn rows={ovBase} filename={`recruitpro-overview-${ovDateFrom||"all"}-${ovDateTo||"all"}.csv`} panelists={panelists} label="Download" />
                </div>
              </div>
            </div>

            {/* Stat cards row 1 */}
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10, marginBottom: 10 }}>
              {[["Total Applied", ovStats.total, COLORS.gold, "📋"],
                ["Test Cleared", ovStats.cleared, COLORS.success, "✅"],
                ["Approved", ovStats.approved, "#3498db", "👍"],
                ["Rejected", ovStats.rejected, COLORS.danger, "❌"],
              ].map(([l, v, c, icon]) => (
                <div key={l} style={{ background: COLORS.surface, borderRadius: 12, padding: 16, border: `1px solid ${COLORS.border}`, position: "relative", overflow: "hidden" }}>
                  <div style={{ position: "absolute", top: 0, left: 0, right: 0, height: 3, background: c }} />
                  <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start" }}>
                    <div>
                      <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 6 }}>{l}</div>
                      <div style={{ fontSize: 28, fontWeight: 800, color: c }}>{v}</div>
                    </div>
                    <span style={{ fontSize: 20, opacity: 0.5 }}>{icon}</span>
                  </div>
                  {ovFilterActive && candidates.length !== ovBase.length && (
                    <div style={{ fontSize: 10, color: COLORS.muted, marginTop: 4 }}>
                      of {[l === "Total Applied" ? candidates.length : l === "Test Cleared" ? candidates.filter(c => c.aptScore >= 10 && c.typingScore?.passed).length : l === "Approved" ? candidates.filter(c => c.panelStatus === "approved").length : candidates.filter(c => c.panelStatus === "rejected").length].join("")} total
                    </div>
                  )}
                </div>
              ))}
            </div>

            {/* Stat cards row 2 */}
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10, marginBottom: 20 }}>
              {[["Not Started", ovStats.notStarted, COLORS.muted, "🕐"],
                ["Apt Failed", ovStats.aptFailed, COLORS.danger, "📝"],
                ["Typing Failed", ovStats.typingFailed, COLORS.warning, "⌨️"],
                ["Awaiting Panel", ovStats.pending, COLORS.warning, "⏳"],
              ].map(([l, v, c, icon]) => (
                <div key={l} style={{ background: COLORS.surface, borderRadius: 12, padding: 16, border: `1px solid ${COLORS.border}` }}>
                  <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start" }}>
                    <div>
                      <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 6 }}>{l}</div>
                      <div style={{ fontSize: 24, fontWeight: 800, color: c }}>{v}</div>
                    </div>
                    <span style={{ fontSize: 18, opacity: 0.5 }}>{icon}</span>
                  </div>
                </div>
              ))}
            </div>

            {/* Panelist Workload */}
            <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 20 }}>
              <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 14 }}>
                <h2 style={{ ...s.h2, margin: 0 }}>Panelist Workload {ovFilterActive ? <span style={{ fontSize: 12, color: COLORS.accent, fontWeight: 500 }}>(filtered)</span> : ""}</h2>
                <button onClick={() => setAddingPanelist(true)} style={{ background: COLORS.accent, border: "none", borderRadius: 8, padding: "7px 14px", color: "#fff", cursor: "pointer", fontSize: 13, fontWeight: 600 }}>+ Add Panelist</button>
              </div>
              {panelists.length === 0 ? (
                <div style={{ color: COLORS.muted, fontSize: 14, textAlign: "center", padding: "20px 0" }}>No panelists added yet.</div>
              ) : panelists.map(p => {
                const load = ovLoad[p.id] || { total: 0, pending: 0, approved: 0, rejected: 0 };
                const dL = Math.max(0, Math.ceil((new Date(p.expiresAt) - Date.now()) / (1000 * 60 * 60 * 24)));
                return (
                  <div key={p.id} style={{ background: COLORS.card, borderRadius: 12, padding: "12px 16px", marginBottom: 10, border: `1px solid ${p.disabled ? COLORS.danger + "44" : COLORS.border}`, opacity: p.disabled ? 0.6 : 1 }}>
                    <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center" }}>
                      <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                        <div style={{ width: 34, height: 34, borderRadius: "50%", background: "rgba(52,152,219,0.2)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 16 }}>🎯</div>
                        <div>
                          <div style={{ fontWeight: 600, fontSize: 14 }}>{p.name ? `${p.name} (${p.username})` : p.username} {p.disabled && <span style={{ fontSize: 11, color: COLORS.danger }}>(disabled)</span>}{p.onBreak && <span style={{ fontSize: 11, color: COLORS.warning }}> ☕ On Break</span>}</div>
                          <div style={{ fontSize: 12, color: COLORS.muted }}>{p.name && <span style={{ color: COLORS.text }}>{p.name} · </span>}{p.email} · Expires in {dL}d</div>
                        </div>
                      </div>
                      <div style={{ display: "flex", gap: 16, alignItems: "center" }}>
                        {[["Assigned", load.total, COLORS.gold], ["Pending", load.pending, COLORS.warning], ["Approved", load.approved, COLORS.success], ["Rejected", load.rejected, COLORS.danger]].map(([k, v, c]) => (
                          <div key={k} style={{ textAlign: "center" }}>
                            <div style={{ fontSize: 18, fontWeight: 700, color: c }}>{v}</div>
                            <div style={{ fontSize: 10, color: COLORS.muted }}>{k}</div>
                          </div>
                        ))}
                      </div>
                    </div>
                    {/* Progress bar */}
                    <div style={{ marginTop: 10, display: "flex", gap: 3 }}>
                      {load.total > 0 && [["Pending", load.pending, COLORS.warning], ["Approved", load.approved, COLORS.success], ["Rejected", load.rejected, COLORS.danger]].map(([k, v, c]) => v > 0 && (
                        <div key={k} title={`${k}: ${v}`} style={{ height: 5, background: c, borderRadius: 3, flex: v, opacity: 0.8 }} />
                      ))}
                      {load.total === 0 && <div style={{ height: 5, background: COLORS.border, borderRadius: 3, flex: 1 }} />}
                    </div>
                  </div>
                );
              })}
            </div>
          </div>
        );
      })()}

      {/* ── Summary Tab ── */}

      {/* ── Summary Tab ── */}
      {activeTab === "summary" && (() => {
        // Determine which candidates fall in the selected date window
        const getSummaryPool = () => {
          if (sumMode === "day") {
            return candidates.filter(c => localDateOf(c.registeredAt) === sumDate);
          } else {
            const from = sumFrom || "0000-01-01";
            const to   = sumTo   || todayStr();
            return candidates.filter(c => {
              const d = localDateOf(c.registeredAt) || "";
              return d >= from && d <= to;
            });
          }
        };

        const pool = getSummaryPool();
        const allDatesInData = [...new Set(candidates.map(c => localDateOf(c.registeredAt)).filter(Boolean))].sort((a,b)=>b.localeCompare(a));
        const todayLocal = todayStr();
        // Note: Summary always uses ALL candidates regardless of global filters
        const totalDays = sumMode === "range" && sumFrom && sumTo
          ? Math.max(1, Math.ceil((new Date(sumTo) - new Date(sumFrom)) / 86400000) + 1)
          : 1;

        // Core stats
        const total       = pool.length;
        const notStarted  = pool.filter(c => c.aptScore == null).length;
        const aptFailed   = pool.filter(c => c.aptScore != null && c.aptScore < 10).length;
        const aptPassed   = pool.filter(c => c.aptScore >= 10).length;
        const typingFail  = pool.filter(c => c.aptScore >= 10 && c.typingScore && !c.typingScore.passed).length;
        const cleared     = pool.filter(c => c.aptScore >= 10 && c.typingScore?.passed).length;
        const approved    = pool.filter(c => c.panelStatus === "approved").length;
        const rejected    = pool.filter(c => c.panelStatus === "rejected").length;
        const pending     = pool.filter(c => c.aptScore >= 10 && c.typingScore?.passed && c.panelStatus === "pending").length;
        const flagged     = pool.filter(c => c.duplicateFlagged).length;
        const rejoiners   = pool.filter(c => c.isRejoiner === "Yes").length;

        // Referral breakdown
        const refCounts = { walkin: 0, website: 0, referral: 0 };
        pool.forEach(c => { if (refCounts[c.referBy] !== undefined) refCounts[c.referBy]++; });

        // Panelist load
        const pLoad = {};
        panelists.forEach(p => { pLoad[p.id] = { name: p.name || p.username, assigned: 0, approved: 0, rejected: 0, pending: 0 }; });
        pool.forEach(c => {
          if (c.assignedPanelistId && pLoad[c.assignedPanelistId]) {
            pLoad[c.assignedPanelistId].assigned++;
            if (c.panelStatus === "approved") pLoad[c.assignedPanelistId].approved++;
            else if (c.panelStatus === "rejected") pLoad[c.assignedPanelistId].rejected++;
            else pLoad[c.assignedPanelistId].pending++;
          }
        });

        // Day-wise breakdown for range mode
        const dayBreakdown = {};
        if (sumMode === "range") {
          pool.forEach(c => {
            const d = localDateOf(c.registeredAt);
            if (!dayBreakdown[d]) dayBreakdown[d] = { registered: 0, cleared: 0, approved: 0, rejected: 0 };
            dayBreakdown[d].registered++;
            if (c.aptScore >= 10 && c.typingScore?.passed) dayBreakdown[d].cleared++;
            if (c.panelStatus === "approved") dayBreakdown[d].approved++;
            if (c.panelStatus === "rejected") dayBreakdown[d].rejected++;
          });
        }
        const sortedDays = Object.keys(dayBreakdown).sort((a,b) => b.localeCompare(a));

        const pct = (n) => total > 0 ? ((n / total) * 100).toFixed(1) : "0.0";

        return (
          <div>
            {/* ── Date selector ── */}
            <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 20, marginBottom: 20 }}>
              <div style={{ display: "flex", gap: 8, marginBottom: 16 }}>
                {[["day","📅 Single Day"],["range","📆 Date Range"]].map(([v,l]) => (
                  <button key={v} onClick={() => setSumMode(v)} style={{ padding:"8px 18px", borderRadius:20, border:`1px solid ${sumMode===v?COLORS.accent:COLORS.border}`, background:sumMode===v?"rgba(233,69,96,0.12)":"transparent", color:sumMode===v?COLORS.accent:COLORS.muted, cursor:"pointer", fontSize:13, fontWeight:600 }}>{l}</button>
                ))}
              </div>

              {sumMode === "day" ? (
                <div style={{ display:"flex", gap:10, alignItems:"flex-end", flexWrap:"wrap" }}>
                  <div>
                    <div style={{ fontSize:11,color:COLORS.muted,fontWeight:700,marginBottom:5 }}>SELECT DATE</div>
                    <input type="date" value={sumDate} max={todayStr()} onChange={e=>setSumDate(e.target.value)} style={{ ...s.input,marginBottom:0,fontSize:13,padding:"8px 12px",width:170 }} />
                  </div>
                  <div style={{ display:"flex", gap:5 }}>
                    {[["Today",()=>setSumDate(todayStr())],["Yesterday",()=>setSumDate((() => { const d = new Date(Date.now()-86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })())]].map(([l,fn])=>(
                      <button key={l} onClick={fn} style={{ padding:"8px 12px",borderRadius:8,border:`1px solid ${COLORS.border}`,background:COLORS.card,color:COLORS.muted,cursor:"pointer",fontSize:12,fontWeight:600 }}>{l}</button>
                    ))}
                  </div>
                  <div style={{ fontSize:13,color:COLORS.muted,paddingBottom:2 }}>
                    — <strong style={{ color:COLORS.text }}>{new Date(sumDate+"T00:00:00").toLocaleDateString("en-IN",{weekday:"long",day:"2-digit",month:"long",year:"numeric"})}</strong>
                  </div>
                </div>
              ) : (
                <div style={{ display:"flex", gap:10, alignItems:"flex-end", flexWrap:"wrap" }}>
                  <div>
                    <div style={{ fontSize:11,color:COLORS.muted,fontWeight:700,marginBottom:5 }}>FROM</div>
                    <input type="date" value={sumFrom} max={todayStr()} onChange={e=>setSumFrom(e.target.value)} style={{ ...s.input,marginBottom:0,fontSize:13,padding:"8px 12px",width:160 }} />
                  </div>
                  <div>
                    <div style={{ fontSize:11,color:COLORS.muted,fontWeight:700,marginBottom:5 }}>TO</div>
                    <input type="date" value={sumTo} max={todayStr()} onChange={e=>setSumTo(e.target.value)} style={{ ...s.input,marginBottom:0,fontSize:13,padding:"8px 12px",width:160 }} />
                  </div>
                  <div style={{ display:"flex", gap:5, flexWrap:"wrap" }}>
                    {[
                      ["Last 7d",()=>{setSumFrom((() => { const d = new Date(Date.now()-6*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })());setSumTo(todayStr());}],
                      ["Last 30d",()=>{setSumFrom((() => { const d = new Date(Date.now()-29*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })());setSumTo(todayStr());}],
                      ["This Month",()=>{const n=new Date();setSumFrom(`${n.getFullYear()}-${String(n.getMonth()+1).padStart(2,"0")}-01`);setSumTo(todayStr());}],
                      ["All Time",()=>{setSumFrom("");setSumTo("");}],
                    ].map(([l,fn])=>(
                      <button key={l} onClick={fn} style={{ padding:"8px 10px",borderRadius:8,border:`1px solid ${COLORS.border}`,background:COLORS.card,color:COLORS.muted,cursor:"pointer",fontSize:12,fontWeight:600 }}>{l}</button>
                    ))}
                  </div>
                </div>
              )}
            </div>

            {total === 0 ? (
              <div style={{ textAlign:"center", padding:"40px 20px", color:COLORS.muted }}>
                <div style={{ fontSize:40,marginBottom:12 }}>📭</div>
                <div style={{ fontSize:14,fontWeight:600,color:COLORS.text,marginBottom:8 }}>No registrations found for this date</div>
                <div style={{ fontSize:12,marginBottom:16 }}>
                  Selected: <strong style={{ color:COLORS.accent }}>{sumMode==="day" ? sumDate : `${sumFrom||"start"} → ${sumTo||"today"}`}</strong> · Today (local): <strong style={{ color:COLORS.gold }}>{todayLocal}</strong>
                </div>
                {/* Show all dates that DO have data */}
                {allDatesInData.length > 0 ? (
                  <div style={{ background:COLORS.card, borderRadius:12, padding:"14px 16px", maxWidth:400, margin:"0 auto", border:`1px solid ${COLORS.border}` }}>
                    <div style={{ fontSize:12,color:COLORS.muted,marginBottom:10,fontWeight:600 }}>📅 Dates with data ({allDatesInData.length}):</div>
                    <div style={{ display:"flex",flexWrap:"wrap",gap:6,justifyContent:"center" }}>
                      {allDatesInData.map(d => (
                        <button key={d} onClick={() => { setSumMode("day"); setSumDate(d); }} style={{ background: d===todayLocal?"rgba(233,69,96,0.15)":COLORS.surface, border:`1px solid ${d===todayLocal?COLORS.accent:COLORS.border}`, borderRadius:8, padding:"5px 12px", fontSize:12, fontWeight:600, color:d===todayLocal?COLORS.accent:COLORS.text, cursor:"pointer" }}>
                          {d} ({candidates.filter(c=>localDateOf(c.registeredAt)===d).length})
                        </button>
                      ))}
                    </div>
                    <div style={{ fontSize:11,color:COLORS.muted,marginTop:10 }}>Click a date to view its summary</div>
                  </div>
                ) : (
                  <div style={{ fontSize:13,color:COLORS.muted }}>No candidate data found at all. Register some candidates first.</div>
                )}
                {/* Raw date debug */}
                {candidates.length > 0 && (
                  <div style={{ background:COLORS.card,borderRadius:10,padding:"10px 14px",maxWidth:500,margin:"16px auto 0",border:`1px solid ${COLORS.border}`,textAlign:"left" }}>
                    <div style={{ fontSize:11,color:COLORS.muted,fontWeight:600,marginBottom:6 }}>🔍 Latest 3 registeredAt values (raw):</div>
                    {[...candidates].sort((a,b)=>new Date(b.registeredAt)-new Date(a.registeredAt)).slice(0,3).map((c,i)=>(
                      <div key={i} style={{ fontSize:11,color:COLORS.text,fontFamily:"monospace",marginBottom:3 }}>
                        {c.name}: <span style={{ color:COLORS.gold }}>{c.registeredAt}</span> → date: <span style={{ color:localDateOf(c.registeredAt)===todayLocal?COLORS.success:COLORS.danger }}>{localDateOf(c.registeredAt)}</span>
                      </div>
                    ))}
                    <div style={{ fontSize:11,color:COLORS.muted,marginTop:6 }}>Today string: <span style={{ color:COLORS.gold,fontFamily:"monospace" }}>{todayLocal}</span></div>
                  </div>
                )}
              </div>
            ) : (
              <>
                {/* ── Headline ── */}
                <div style={{ background:"linear-gradient(135deg,rgba(233,69,96,0.12),rgba(233,69,96,0.04))", border:`1px solid rgba(233,69,96,0.3)`, borderRadius:14, padding:"16px 20px", marginBottom:16, display:"flex", justifyContent:"space-between", alignItems:"center", flexWrap:"wrap", gap:10 }}>
                  <div>
                    <div style={{ fontSize:12,color:COLORS.accent,fontWeight:700,letterSpacing:0.5,marginBottom:4 }}>
                      {sumMode==="day" ? `📅 ${new Date(sumDate+"T00:00:00").toLocaleDateString("en-IN",{weekday:"long",day:"2-digit",month:"long",year:"numeric"})}` : `📆 ${sumFrom||"All"} → ${sumTo||"Today"} (${totalDays} day${totalDays!==1?"s":""})`}
                    </div>
                    <div style={{ fontSize:26,fontWeight:900,color:COLORS.text }}>{total} <span style={{ fontSize:14,fontWeight:400,color:COLORS.muted }}>total registrations</span></div>
                  </div>
                  <DownloadBtn rows={pool} filename={`recruitpro-summary-${sumMode==="day"?sumDate:sumFrom+"-to-"+sumTo}.csv`} panelists={panelists} label="Download Report" />
                </div>

                {/* ── Pipeline stats grid ── */}
                <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fit,minmax(140px,1fr))", gap:10, marginBottom:16 }}>
                  {[
                    ["📝 Not Started",    notStarted,  COLORS.muted,    pct(notStarted)],
                    ["🧠 Apt Failed",     aptFailed,   COLORS.danger,   pct(aptFailed)],
                    ["✅ Apt Passed",     aptPassed,   "#3498db",       pct(aptPassed)],
                    ["⌨️ Typing Failed",  typingFail,  COLORS.warning,  pct(typingFail)],
                    ["🏆 Cleared Both",   cleared,     COLORS.success,  pct(cleared)],
                    ["⏳ Awaiting Panel", pending,     COLORS.warning,  pct(pending)],
                    ["✅ Approved",       approved,    COLORS.success,  pct(approved)],
                    ["❌ Rejected",       rejected,    COLORS.danger,   pct(rejected)],
                  ].map(([label,val,color,pc]) => (
                    <div key={label} style={{ background:COLORS.card, borderRadius:12, padding:"12px 14px", border:`1px solid ${COLORS.border}`, position:"relative", overflow:"hidden" }}>
                      <div style={{ position:"absolute",bottom:0,left:0,height:3,width:`${pc}%`,background:color,borderRadius:"0 0 12px 0",transition:"width 0.6s ease" }} />
                      <div style={{ fontSize:11,color:COLORS.muted,marginBottom:6 }}>{label}</div>
                      <div style={{ fontSize:22,fontWeight:800,color }}>{val}</div>
                      <div style={{ fontSize:11,color:COLORS.muted,marginTop:2 }}>{pc}%</div>
                    </div>
                  ))}
                </div>

                {/* ── 2-col: Referral breakdown + Rejoiner ── */}
                <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fit,minmax(200px,1fr))", gap:12, marginBottom:16 }}>
                  <div style={{ background:COLORS.card, borderRadius:12, padding:"16px", border:`1px solid ${COLORS.border}` }}>
                    <div style={{ fontSize:12,fontWeight:700,color:COLORS.text,marginBottom:12 }}>📣 Referral Sources</div>
                    {[["Walk-in","walkin",COLORS.accent],["Website","website","#3498db"],["Referral","referral",COLORS.gold]].map(([label,key,color])=>{
                      const n = refCounts[key] || 0;
                      const bar = total > 0 ? (n/total)*100 : 0;
                      return (
                        <div key={key} style={{ marginBottom:10 }}>
                          <div style={{ display:"flex",justifyContent:"space-between",marginBottom:4 }}>
                            <span style={{ fontSize:12,color:COLORS.muted }}>{label}</span>
                            <span style={{ fontSize:12,fontWeight:700,color }}>{n} <span style={{ color:COLORS.muted,fontWeight:400 }}>({pct(n)}%)</span></span>
                          </div>
                          <div style={{ background:COLORS.border,borderRadius:20,height:6 }}>
                            <div style={{ height:"100%",width:`${bar}%`,background:color,borderRadius:20,transition:"width 0.5s" }} />
                          </div>
                        </div>
                      );
                    })}
                  </div>

                  <div style={{ background:COLORS.card, borderRadius:12, padding:"16px", border:`1px solid ${COLORS.border}` }}>
                    <div style={{ fontSize:12,fontWeight:700,color:COLORS.text,marginBottom:12 }}>👤 Candidate Types</div>
                    {[["Fresh Candidates",total-rejoiners,COLORS.success],["Rejoiners",rejoiners,COLORS.warning],["Duplicate Flagged",flagged,COLORS.danger]].map(([label,n,color])=>{
                      const bar = total > 0 ? (n/total)*100 : 0;
                      return (
                        <div key={label} style={{ marginBottom:10 }}>
                          <div style={{ display:"flex",justifyContent:"space-between",marginBottom:4 }}>
                            <span style={{ fontSize:12,color:COLORS.muted }}>{label}</span>
                            <span style={{ fontSize:12,fontWeight:700,color }}>{n} <span style={{ color:COLORS.muted,fontWeight:400 }}>({pct(n)}%)</span></span>
                          </div>
                          <div style={{ background:COLORS.border,borderRadius:20,height:6 }}>
                            <div style={{ height:"100%",width:`${bar}%`,background:color,borderRadius:20 }} />
                          </div>
                        </div>
                      );
                    })}
                  </div>
                </div>

                {/* ── Panelist load ── */}
                {panelists.length > 0 && (
                  <div style={{ background:COLORS.card, borderRadius:12, padding:"16px", border:`1px solid ${COLORS.border}`, marginBottom:16 }}>
                    <div style={{ fontSize:12,fontWeight:700,color:COLORS.text,marginBottom:12 }}>🎯 Panelist Performance</div>
                    {panelists.map(p => {
                      const load = pLoad[p.id] || { assigned:0,approved:0,rejected:0,pending:0 };
                      if (load.assigned === 0) return null;
                      return (
                        <div key={p.id} style={{ display:"flex",justifyContent:"space-between",alignItems:"center",padding:"8px 0",borderBottom:`1px solid ${COLORS.border}` }}>
                          <div style={{ fontSize:13,color:COLORS.text,fontWeight:600 }}>{p.name || p.username}</div>
                          <div style={{ display:"flex",gap:16 }}>
                            {[["Assigned",load.assigned,COLORS.gold],["Approved",load.approved,COLORS.success],["Rejected",load.rejected,COLORS.danger],["Pending",load.pending,COLORS.warning]].map(([k,v,c])=>(
                              <div key={k} style={{ textAlign:"center" }}>
                                <div style={{ fontSize:15,fontWeight:800,color:c }}>{v}</div>
                                <div style={{ fontSize:10,color:COLORS.muted }}>{k}</div>
                              </div>
                            ))}
                          </div>
                        </div>
                      );
                    })}
                  </div>
                )}

                {/* ── Day-wise table (range mode only) ── */}
                {sumMode === "range" && sortedDays.length > 0 && (
                  <div style={{ background:COLORS.card, borderRadius:12, border:`1px solid ${COLORS.border}`, overflow:"hidden", marginBottom:16 }}>
                    <div style={{ padding:"14px 16px", borderBottom:`1px solid ${COLORS.border}`, fontSize:12, fontWeight:700, color:COLORS.text }}>📅 Day-wise Breakdown</div>
                    <div style={{ overflowX:"auto" }}>
                      <table style={{ width:"100%",borderCollapse:"collapse",fontSize:12 }}>
                        <thead>
                          <tr style={{ background:"rgba(0,0,0,0.2)" }}>
                            {["Date","Day","Registered","Cleared","Approved","Rejected","Rate"].map(h => (
                              <th key={h} style={{ padding:"9px 14px",textAlign:"left",color:COLORS.muted,fontWeight:700,whiteSpace:"nowrap",fontSize:11 }}>{h}</th>
                            ))}
                          </tr>
                        </thead>
                        <tbody>
                          {sortedDays.map((d,i) => {
                            const row = dayBreakdown[d];
                            const rate = row.registered > 0 ? ((row.approved / row.registered)*100).toFixed(0) : "0";
                            return (
                              <tr key={d} style={{ borderBottom:`1px solid ${COLORS.border}`, background:i%2===0?"transparent":"rgba(255,255,255,0.02)" }}>
                                <td style={{ padding:"9px 14px",fontWeight:600,color:COLORS.text,fontFamily:"monospace" }}>{d}</td>
                                <td style={{ padding:"9px 14px",color:COLORS.muted }}>{new Date(d+"T00:00:00").toLocaleDateString("en-IN",{weekday:"short"})}</td>
                                <td style={{ padding:"9px 14px",color:COLORS.text,fontWeight:700 }}>{row.registered}</td>
                                <td style={{ padding:"9px 14px",color:COLORS.success }}>{row.cleared}</td>
                                <td style={{ padding:"9px 14px",color:COLORS.success,fontWeight:700 }}>{row.approved}</td>
                                <td style={{ padding:"9px 14px",color:COLORS.danger }}>{row.rejected}</td>
                                <td style={{ padding:"9px 14px" }}>
                                  <div style={{ display:"flex",alignItems:"center",gap:6 }}>
                                    <span style={{ fontSize:12,fontWeight:700,color:Number(rate)>=50?COLORS.success:COLORS.warning }}>{rate}%</span>
                                    <div style={{ background:COLORS.border,borderRadius:20,height:4,width:50,overflow:"hidden" }}>
                                      <div style={{ height:"100%",width:`${rate}%`,background:Number(rate)>=50?COLORS.success:COLORS.warning }} />
                                    </div>
                                  </div>
                                </td>
                              </tr>
                            );
                          })}
                        </tbody>
                        <tfoot>
                          <tr style={{ background:"rgba(99,102,241,0.07)", borderTop:`2px solid ${COLORS.border}` }}>
                            <td colSpan={2} style={{ padding:"9px 14px",fontWeight:700,color:COLORS.accent,fontSize:12 }}>TOTAL</td>
                            <td style={{ padding:"9px 14px",fontWeight:800,color:COLORS.text }}>{total}</td>
                            <td style={{ padding:"9px 14px",fontWeight:700,color:COLORS.success }}>{cleared}</td>
                            <td style={{ padding:"9px 14px",fontWeight:700,color:COLORS.success }}>{approved}</td>
                            <td style={{ padding:"9px 14px",fontWeight:700,color:COLORS.danger }}>{rejected}</td>
                            <td style={{ padding:"9px 14px",fontWeight:700,color:approved/total>=0.5?COLORS.success:COLORS.warning }}>{total>0?((approved/total)*100).toFixed(0):0}%</td>
                          </tr>
                        </tfoot>
                      </table>
                    </div>
                  </div>
                )}
              </>
            )}
          </div>
        );
      })()}

      {/* ── All Candidates ── */}
      {activeTab === "candidates" && (() => {
        const acBase = gCandidates.filter(c => {
          const d = localDateOf(c.registeredAt) || "";
          if (acSearch && 
              !c.name.toLowerCase().includes(acSearch.toLowerCase()) && 
              !c.mobile.includes(acSearch) && 
              !c.username?.toLowerCase().includes(acSearch.toLowerCase()) && 
              !c.pan?.toLowerCase().includes(acSearch.toLowerCase()) &&
              !c.aadhaar?.includes(acSearch)) return false;
          if (acDateFrom && d < acDateFrom) return false;
          if (acDateTo && d > acDateTo) return false;
          if (acReferBy !== "all" && c.referBy !== acReferBy) return false;
          if (acRejoiner !== "all" && c.isRejoiner !== acRejoiner) return false;
          if (acPanelist !== "all" && c.assignedPanelistId !== acPanelist) return false;
          if (acStatus !== "all") {
            if (acStatus === "notStarted" && c.aptScore != null) return false;
            if (acStatus === "aptFailed" && !(c.aptScore != null && c.aptScore < 10)) return false;
            if (acStatus === "typingFailed" && !(c.aptScore >= 10 && c.typingScore && !c.typingScore.passed)) return false;
            if (acStatus === "cleared" && !(c.aptScore >= 10 && c.typingScore?.passed)) return false;
            if (acStatus === "pending" && !(c.aptScore >= 10 && c.typingScore?.passed && c.panelStatus === "pending")) return false;
            if (acStatus === "approved" && c.panelStatus !== "approved") return false;
            if (acStatus === "rejected" && c.panelStatus !== "rejected") return false;
          }
          return true;
        });
        const acFilterActive = acSearch || acDateFrom || acDateTo || acStatus !== "all" || acReferBy !== "all" || acRejoiner !== "all" || acPanelist !== "all";

        // If search looks like a PAN (10 chars, alphanumeric), show ALL matching candidates ignoring other filters
        const isPanSearch = acSearch.trim().length >= 5 && /^[A-Za-z0-9]+$/.test(acSearch.trim());
        const displayList = isPanSearch
          ? candidates.filter(c =>
              c.pan?.toLowerCase().includes(acSearch.toLowerCase()) ||
              c.username?.toLowerCase().includes(acSearch.toLowerCase()) ||
              c.name?.toLowerCase().includes(acSearch.toLowerCase()) ||
              c.mobile?.includes(acSearch) ||
              c.aadhaar?.includes(acSearch))
          : acBase;

        return (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 14 }}>
            <h2 style={{ ...s.h2, margin: 0 }}>All Candidates</h2>
            <div style={{ display: "flex", gap: 8, alignItems: "center" }}>
              <span style={{ fontSize: 13, color: COLORS.muted }}>{displayList.length}{displayList.length !== candidates.length ? ` / ${candidates.length}` : ""} candidates</span>
              <DownloadBtn rows={displayList} filename={`recruitpro-candidates-${todayStr()}.csv`} panelists={panelists} label="Download" />
            </div>
          </div>
          {isPanSearch && displayList.length !== acBase.length && (
            <div style={{ background:"rgba(99,102,241,0.08)", border:`1px solid rgba(99,102,241,0.25)`, borderRadius:8, padding:"8px 12px", marginBottom:12, fontSize:12, color:"#818cf8" }}>
              🔍 Showing all {displayList.length} results for "<strong>{acSearch}</strong>" — date/status filters bypassed for this search
            </div>
          )}

          {/* Filter panel */}
          <div style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", marginBottom: 16, border: `1px solid ${COLORS.border}` }}>
            {/* Row 1: search */}
            <div style={{ display: "flex", gap: 10, marginBottom: 12, alignItems: "center" }}>
              <input style={{ ...s.input, marginBottom: 0, flex: 1, fontSize: 13, padding: "8px 12px" }} placeholder="🔍 🔍 Search by name, mobile or PAN..." value={acSearch} onChange={e => setAcSearch(e.target.value)} />
              {acFilterActive && <button onClick={() => { setAcSearch(""); setAcDateFrom(""); setAcDateTo(""); setAcStatus("all"); setAcReferBy("all"); setAcRejoiner("all"); setAcPanelist("all"); }} style={{ padding: "8px 14px", borderRadius: 8, border: `1px solid rgba(233,69,96,0.3)`, background: "rgba(233,69,96,0.08)", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}>✕ Clear All</button>}
            </div>
            {/* Row 2: dates */}
            <div style={{ display: "flex", gap: 10, marginBottom: 12, flexWrap: "wrap", alignItems: "flex-end" }}>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>FROM DATE</div>
                <input type="date" value={acDateFrom} onChange={e => setAcDateFrom(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TO DATE</div>
                <input type="date" value={acDateTo} onChange={e => setAcDateTo(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>QUICK</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["Today", () => { const t = todayStr(); setAcDateFrom(t); setAcDateTo(t); }],
                    ["Yesterday", () => { const y = (() => { const d = new Date(Date.now()-86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })(); setAcDateFrom(y); setAcDateTo(y); }],
                    ["Last 7d", () => { setAcDateFrom((() => { const d = new Date(Date.now()-7*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })()); setAcDateTo(todayStr()); }],
                    ["All", () => { setAcDateFrom(""); setAcDateTo(""); }],
                  ].map(([l, fn]) => (
                    <button key={l} onClick={fn} style={{ padding: "6px 10px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
            </div>
            {/* Row 3: status + referBy + rejoiner + panelist */}
            <div style={{ display: "flex", gap: 14, flexWrap: "wrap" }}>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>STATUS</div>
                <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
                  {[["all","All",COLORS.muted],["notStarted","Not Started",COLORS.muted],["aptFailed","Apt Failed",COLORS.danger],["typingFailed","Typing Failed",COLORS.warning],["cleared","Cleared",COLORS.success],["pending","⏳ Pending",COLORS.warning],["approved","✅ Approved",COLORS.success],["rejected","❌ Rejected",COLORS.danger]].map(([v,l,c]) => (
                    <button key={v} onClick={() => setAcStatus(v)} style={{ padding: "5px 10px", borderRadius: 20, border: `1px solid ${acStatus === v ? c : COLORS.border}`, background: acStatus === v ? c+"22" : "transparent", color: acStatus === v ? c : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600, whiteSpace: "nowrap" }}>{l}</button>
                  ))}
                </div>
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>REFERRED BY</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All"],["walkin","Walk-in"],["website","Website"],["referral","Referral"]].map(([v,l]) => (
                    <button key={v} onClick={() => setAcReferBy(v)} style={{ padding: "5px 10px", borderRadius: 20, border: `1px solid ${acReferBy === v ? COLORS.accent : COLORS.border}`, background: acReferBy === v ? "rgba(233,69,96,0.15)" : "transparent", color: acReferBy === v ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>TYPE</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All"],["No","Fresh"],["Yes","Rejoiner"]].map(([v,l]) => (
                    <button key={v} onClick={() => setAcRejoiner(v)} style={{ padding: "5px 10px", borderRadius: 20, border: `1px solid ${acRejoiner === v ? COLORS.gold : COLORS.border}`, background: acRejoiner === v ? "rgba(245,166,35,0.15)" : "transparent", color: acRejoiner === v ? COLORS.gold : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
              {panelists.length > 0 && (
                <div>
                  <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>PANELIST</div>
                  <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
                    <button onClick={() => setAcPanelist("all")} style={{ padding: "5px 10px", borderRadius: 20, border: `1px solid ${acPanelist === "all" ? "#3498db" : COLORS.border}`, background: acPanelist === "all" ? "rgba(52,152,219,0.15)" : "transparent", color: acPanelist === "all" ? "#3498db" : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>All</button>
                    {panelists.map(p => (
                      <button key={p.id} onClick={() => setAcPanelist(p.id)} style={{ padding: "5px 10px", borderRadius: 20, border: `1px solid ${acPanelist === p.id ? "#3498db" : COLORS.border}`, background: acPanelist === p.id ? "rgba(52,152,219,0.15)" : "transparent", color: acPanelist === p.id ? "#3498db" : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>🎯 {p.name || p.username}</button>
                    ))}
                  </div>
                </div>
              )}
            </div>
          </div>

          {displayList.length === 0 ? (
            <div style={{ textAlign: "center", padding: "40px 0", color: COLORS.muted }}>No candidates match the current filters.</div>
          ) : displayList.map(c => {
            const aptStatus = c.aptScore == null ? { label: "Not taken", color: COLORS.muted } : c.aptScore >= 10 ? { label: `${c.aptScore}/15 ✓`, color: COLORS.success } : { label: `${c.aptScore}/15 ✗`, color: COLORS.danger };
            const typStatus = !c.typingScore ? { label: "Not taken", color: COLORS.muted } : c.typingScore.passed ? { label: `${c.typingScore.wpm} WPM ✓`, color: COLORS.success } : { label: `${c.typingScore.wpm} WPM ✗`, color: COLORS.danger };
            return (
              <div key={c.id} style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", marginBottom: 10, border: `1px solid ${COLORS.border}` }}>
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start" }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 12, flex: 1 }}>
                    {c.photoData ? (
                      <img src={c.photoData} alt={c.name} style={{ width: 40, height: 40, borderRadius: "50%", objectFit: "cover", border: `2px solid ${COLORS.border}`, flexShrink: 0 }} />
                    ) : (
                      <div style={{ width: 40, height: 40, borderRadius: "50%", background: COLORS.surface, border: `2px solid ${COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 16, flexShrink: 0 }}>👤</div>
                    )}
                    <div>
                      <div style={{ fontWeight: 600, fontSize: 15 }}>{c.name} <span style={{ fontSize: 12, color: COLORS.muted, fontWeight: 400 }}>🪪 {c.username}</span></div>
                      <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 3 }}>📱 {c.mobile} · {c.pan} · {c.referBy}{c.empId ? ` (${c.empId})` : ""} · Registered {fmtTs(c.registeredAt)}</div>
                      <div style={{ display: "flex", gap: 12, marginTop: 6, fontSize: 12 }}>
                        <span style={{ color: aptStatus.color }}>Apt: {aptStatus.label}</span>
                        <span style={{ color: typStatus.color }}>Typing: {typStatus.label}</span>
                        <span style={s.badge(c.panelStatus)}>{c.panelStatus}</span>
                      </div>
                    </div>
                  </div>
                  <div style={{ display: "flex", gap: 6, flexShrink: 0, flexWrap: "wrap", justifyContent: "flex-end" }}>
                    <button onClick={() => setConfirmReset({ type: "resetPwd", candidate: c })} style={{ background: "rgba(52,152,219,0.15)", border: `1px solid rgba(52,152,219,0.4)`, borderRadius: 7, padding: "5px 10px", color: "#3498db", cursor: "pointer", fontSize: 11, fontWeight: 600 }}>🔑 Reset Password</button>
                    <button onClick={() => setConfirmReset({ type: "reset", candidate: c })} style={{ background: "rgba(243,156,18,0.15)", border: `1px solid rgba(243,156,18,0.4)`, borderRadius: 7, padding: "5px 10px", color: COLORS.warning, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>↺ Reset Tests</button>
                    <button onClick={() => setConfirmReset({ type: "delete", candidate: c })} style={{ background: "rgba(231,76,60,0.15)", border: `1px solid rgba(231,76,60,0.4)`, borderRadius: 7, padding: "5px 10px", color: COLORS.danger, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>🗑 Delete</button>
                  </div>
                </div>
              </div>
            );
          })}
        </div>
        );
      })()}

      {/* ── Panelist Control ── */}
      {activeTab === "panelist" && (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
            <h2 style={{ ...s.h2, margin: 0 }}>Panelist Accounts ({panelists.length})</h2>
            <button onClick={() => setAddingPanelist(true)} style={{ background: COLORS.accent, border: "none", borderRadius: 8, padding: "8px 16px", color: "#fff", cursor: "pointer", fontSize: 13, fontWeight: 600 }}>+ Add Panelist</button>
          </div>
          {panelists.length === 0 ? (
            <div style={{ textAlign: "center", padding: "30px 0" }}>
              <div style={{ fontSize: 40, marginBottom: 10 }}>🎯</div>
              <p style={{ color: COLORS.muted, marginBottom: 16 }}>No panelists added yet.</p>
              <button onClick={() => setAddingPanelist(true)} style={s.btn}>➕ Add First Panelist</button>
            </div>
          ) : panelists.map(p => {
            const load = panelistLoad[p.id] || { total: 0, pending: 0, approved: 0, rejected: 0 };
            const dL = Math.max(0, Math.ceil((new Date(p.expiresAt) - Date.now()) / (1000 * 60 * 60 * 24)));
            const isExp = new Date(p.expiresAt) < new Date();
            return (
              <div key={p.id} style={{ background: COLORS.card, borderRadius: 12, padding: "16px 18px", marginBottom: 12, border: `1px solid ${isExp ? COLORS.danger + "55" : p.disabled ? COLORS.border : COLORS.border}`, opacity: p.disabled ? 0.65 : 1 }}>
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 12 }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                    <div style={{ width: 38, height: 38, borderRadius: "50%", background: "rgba(52,152,219,0.15)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 18 }}>🎯</div>
                    <div>
                      <div style={{ fontWeight: 700, fontSize: 15 }}>{p.name || p.username} {p.disabled && <span style={{ fontSize: 11, color: COLORS.danger, fontWeight: 400 }}>(disabled)</span>}{p.onBreak && <span style={{ fontSize: 11, color: COLORS.warning, fontWeight: 600 }}> ☕ On Break</span>}{isExp && <span style={{ fontSize: 11, color: COLORS.danger, fontWeight: 400 }}> (expired)</span>}</div>
                      <div style={{ fontSize: 12, color: COLORS.muted }}>{p.email}</div>
                    </div>
                  </div>
                  <div style={{ display: "flex", gap: 6 }}>
                    <button onClick={() => setEditingPanelist(p)} style={{ background: "rgba(52,152,219,0.15)", border: `1px solid rgba(52,152,219,0.3)`, borderRadius: 7, padding: "5px 10px", color: "#3498db", cursor: "pointer", fontSize: 12 }}>✏️ Edit</button>
                    <button onClick={() => setPanelists(prev => prev.map(x => x.id === p.id ? { ...x, disabled: !x.disabled } : x))} style={{ background: p.disabled ? "rgba(46,204,113,0.15)" : "rgba(243,156,18,0.15)", border: `1px solid ${p.disabled ? COLORS.success + "44" : COLORS.warning + "44"}`, borderRadius: 7, padding: "5px 10px", color: p.disabled ? COLORS.success : COLORS.warning, cursor: "pointer", fontSize: 12 }}>{p.disabled ? "Enable" : "Disable"}</button>
                    <button onClick={() => setConfirmReset({ type: "deletePanelist", panelist: p })} style={{ background: "rgba(231,76,60,0.15)", border: `1px solid rgba(231,76,60,0.3)`, borderRadius: 7, padding: "5px 10px", color: COLORS.danger, cursor: "pointer", fontSize: 12 }}>🗑</button>
                  </div>
                </div>
                <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(100px, 1fr))", gap: 8 }}>
                  {[["Assigned", load.total, COLORS.gold], ["Pending", load.pending, COLORS.warning], ["Approved", load.approved, COLORS.success], ["Rejected", load.rejected, COLORS.danger], ["Expires", dL + "d", dL <= 14 ? COLORS.danger : COLORS.success]].map(([k, v, c]) => (
                    <div key={k} style={{ background: COLORS.surface, borderRadius: 8, padding: "6px 10px", textAlign: "center" }}>
                      <div style={{ fontSize: 10, color: COLORS.muted }}>{k}</div>
                      <div style={{ fontSize: 16, fontWeight: 700, color: c }}>{v}</div>
                    </div>
                  ))}
                </div>
              </div>
            );
          })}
        </div>
      )}

      {/* ── Audit Log ── */}
      {activeTab === "audit" && (() => {
        // Group candidates by PAN
        const byPan = {};
        gCandidates.forEach(c => {
          const pan = c.pan?.toUpperCase() || "UNKNOWN";
          if (!byPan[pan]) byPan[pan] = [];
          byPan[pan].push(c);
        });

        const sortedPans = Object.keys(byPan).sort();

        // Build all events for a candidate
        const getEvents = (c) => {
          const evs = [];
          if (c.registeredAt) evs.push({ ts: c.registeredAt, icon: "📝", text: `Registered — User ID: ${c.username}`, color: COLORS.text, date: localDateOf(c.registeredAt) });
          if (c.aptCompletedAt) evs.push({ ts: c.aptCompletedAt, icon: "🧠", text: `Aptitude: ${c.aptScore}/15 ${c.aptScore >= 10 ? "✓ Passed" : "✗ Failed"}`, color: c.aptScore >= 10 ? COLORS.success : COLORS.danger, date: localDateOf(c.aptCompletedAt) });
          if (c.typingCompletedAt) evs.push({ ts: c.typingCompletedAt, icon: "⌨️", text: `Typing: ${c.typingScore?.wpm} WPM / ${c.typingScore?.accuracy}% ${c.typingScore?.passed ? "✓ Passed" : "✗ Failed"}`, color: c.typingScore?.passed ? COLORS.success : COLORS.danger, date: localDateOf(c.typingCompletedAt) });
          if (c.panelDecidedAt) evs.push({ ts: c.panelDecidedAt, icon: c.panelStatus === "approved" ? "✅" : c.panelStatus === "rejected" ? "❌" : "⏳", text: `Panel: ${c.panelStatus}${c.panelRemark ? ` — "${c.panelRemark}"` : ""}`, color: c.panelStatus === "approved" ? COLORS.success : c.panelStatus === "rejected" ? COLORS.danger : COLORS.warning, date: localDateOf(c.panelDecidedAt) });
          if (c.passwordResetAt) evs.push({ ts: c.passwordResetAt, icon: "🔑", text: `Password reset by Super Admin`, color: "#3498db", date: localDateOf(c.passwordResetAt) });
          return evs.sort((a, b) => new Date(a.ts) - new Date(b.ts));
        };

        return (
          <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
              <div>
                <h2 style={{ ...s.h2, margin: 0 }}>Audit Log</h2>
                <p style={{ fontSize: 12, color: COLORS.muted, margin: "4px 0 0" }}>Grouped by PAN Card · chronological date-wise history</p>
              </div>
              <div style={{ display: "flex", gap: 10, alignItems: "center" }}>
                {gFilterActive && <span style={{ fontSize: 12, color: COLORS.muted }}>{gCandidates.length}/{candidates.length} candidates</span>}
                <span style={{ background: COLORS.card, borderRadius: 20, padding: "4px 12px", fontSize: 12, color: COLORS.muted, border: `1px solid ${COLORS.border}` }}>{sortedPans.length} PAN{sortedPans.length !== 1 ? "s" : ""}</span>
              </div>
            </div>

            {gCandidates.length === 0 ? (
              <div style={{ textAlign: "center", padding: "30px 0", color: COLORS.muted }}>No activity matches the current filters.</div>
            ) : sortedPans.map(pan => {
              const panCandidates = byPan[pan].sort((a, b) => new Date(a.registeredAt) - new Date(b.registeredAt));
              const allEvents = panCandidates.flatMap(c => getEvents(c).map(ev => ({ ...ev, candidateName: c.name, userId: c.username })));

              // Group events by date
              const eventsByDate = {};
              allEvents.forEach(ev => {
                const d = ev.date || localDateOf(ev.ts);
                if (!eventsByDate[d]) eventsByDate[d] = [];
                eventsByDate[d].push(ev);
              });
              const sortedDates = Object.keys(eventsByDate).sort();

              const latestCandidate = panCandidates[panCandidates.length - 1];
              const statusColor = latestCandidate.panelStatus === "approved" ? COLORS.success : latestCandidate.panelStatus === "rejected" ? COLORS.danger : COLORS.muted;

              return (
                <div key={pan} style={{ marginBottom: 24, background: COLORS.card, borderRadius: 14, border: `1px solid ${COLORS.border}`, overflow: "hidden" }}>
                  {/* PAN header */}
                  <div style={{ background: "rgba(99,102,241,0.08)", padding: "14px 18px", borderBottom: `1px solid ${COLORS.border}`, display: "flex", justifyContent: "space-between", alignItems: "center", flexWrap: "wrap", gap: 8 }}>
                    <div style={{ display: "flex", alignItems: "center", gap: 12 }}>
                      {latestCandidate.photoData
                        ? <img src={latestCandidate.photoData} alt="" style={{ width: 38, height: 38, borderRadius: "50%", objectFit: "cover", border: `2px solid rgba(99,102,241,0.4)`, flexShrink: 0 }} />
                        : <div style={{ width: 38, height: 38, borderRadius: "50%", background: "rgba(99,102,241,0.15)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 16, flexShrink: 0 }}>👤</div>}
                      <div>
                        <div style={{ fontSize: 15, fontWeight: 700, color: COLORS.text }}>{latestCandidate.name}</div>
                        <div style={{ display: "flex", gap: 10, flexWrap: "wrap", marginTop: 2 }}>
                          <span style={{ fontSize: 12, color: "#818cf8", fontFamily: "monospace", fontWeight: 600 }}>🪪 {pan}</span>
                          <span style={{ fontSize: 12, color: COLORS.muted }}>📱 {latestCandidate.mobile}</span>
                        </div>
                      </div>
                    </div>
                    <div style={{ display: "flex", gap: 8, flexWrap: "wrap", alignItems: "center" }}>
                      <span style={{ fontSize: 11, color: COLORS.muted }}>{panCandidates.length} application{panCandidates.length > 1 ? "s" : ""}</span>
                      <span style={s.badge(latestCandidate.panelStatus)}>{latestCandidate.panelStatus}</span>
                    </div>
                  </div>

                  {/* Date-wise events */}
                  <div style={{ padding: "14px 18px" }}>
                    {sortedDates.map((date, di) => (
                      <div key={date} style={{ marginBottom: di < sortedDates.length - 1 ? 16 : 0 }}>
                        {/* Date pill */}
                        <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 10 }}>
                          <div style={{ background: COLORS.surface, borderRadius: 20, padding: "4px 12px", fontSize: 11, fontWeight: 700, color: COLORS.gold, border: `1px solid ${COLORS.border}`, whiteSpace: "nowrap" }}>
                            📅 {new Date(date).toLocaleDateString("en-IN", { weekday: "short", day: "2-digit", month: "short", year: "numeric" })}
                          </div>
                          <div style={{ flex: 1, height: 1, background: COLORS.border }} />
                          <span style={{ fontSize: 11, color: COLORS.muted }}>{eventsByDate[date].length} event{eventsByDate[date].length > 1 ? "s" : ""}</span>
                        </div>

                        {/* Events for this date */}
                        <div style={{ paddingLeft: 12, borderLeft: `2px solid rgba(99,102,241,0.2)`, display: "flex", flexDirection: "column", gap: 8 }}>
                          {eventsByDate[date].map((ev, ei) => (
                            <div key={ei} style={{ display: "flex", gap: 10, alignItems: "flex-start" }}>
                              <div style={{ width: 26, height: 26, borderRadius: "50%", background: COLORS.surface, border: `1px solid ${COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 12, flexShrink: 0, marginLeft: -15 }}>{ev.icon}</div>
                              <div style={{ flex: 1 }}>
                                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", flexWrap: "wrap", gap: 4 }}>
                                  <div>
                                    <span style={{ fontSize: 13, color: ev.color, fontWeight: 500 }}>{ev.text}</span>
                                    {ev.userId && <span style={{ fontSize: 11, color: COLORS.muted, marginLeft: 8 }}>ID: {ev.userId}</span>}
                                  </div>
                                  <span style={{ fontSize: 11, color: COLORS.muted, whiteSpace: "nowrap" }}>{new Date(ev.ts).toLocaleTimeString("en-IN", { hour: "2-digit", minute: "2-digit", hour12: true })}</span>
                                </div>
                              </div>
                            </div>
                          ))}
                        </div>
                      </div>
                    ))}
                  </div>

                  {/* All User IDs for this PAN */}
                  {panCandidates.length > 0 && (
                    <div style={{ padding: "10px 18px", borderTop: `1px solid ${COLORS.border}`, background: "rgba(0,0,0,0.15)", display: "flex", gap: 8, flexWrap: "wrap", alignItems: "center" }}>
                      <span style={{ fontSize: 11, color: COLORS.muted }}>User IDs:</span>
                      {panCandidates.map((c, i) => (
                        <span key={i} style={{ fontSize: 11, fontFamily: "monospace", fontWeight: 700, color: COLORS.gold, background: "rgba(245,166,35,0.1)", borderRadius: 6, padding: "2px 8px", border: `1px solid rgba(245,166,35,0.25)` }}>{c.username}</span>
                      ))}
                    </div>
                  )}
                </div>
              );
            })}
          </div>
        );
      })()}

      {/* ── Alarms Tab ── */}
      {activeTab === "alarms" && (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
            <div>
              <h2 style={{ ...s.h2, margin: 0 }}>🚨 Duplicate Entry Alarms</h2>
              <p style={{ fontSize: 12, color: COLORS.muted, margin: "4px 0 0" }}>Triggered when mobile, PAN or Aadhaar appears more than once on the same day</p>
            </div>
            <div style={{ display: "flex", gap: 6 }}>
              {["all", "unresolved", "resolved"].map(f => (
                <button key={f} onClick={() => setAlarmFilter(f)} style={{ padding: "5px 12px", borderRadius: 20, border: `1px solid ${alarmFilter === f ? COLORS.accent : COLORS.border}`, background: alarmFilter === f ? "rgba(233,69,96,0.15)" : "transparent", color: alarmFilter === f ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600, textTransform: "capitalize" }}>{f}</button>
              ))}
            </div>
          </div>

          {(() => {
            const filtered = alarms.filter(a => {
              if (alarmFilter === "unresolved" && a.resolved) return false;
              if (alarmFilter === "resolved" && !a.resolved) return false;
              if (gDateFrom && a.date < gDateFrom) return false;
              if (gDateTo && a.date > gDateTo) return false;
              if (gSearch && !a.attemptedName?.toLowerCase().includes(gSearch.toLowerCase()) && !a.attemptedMobile?.includes(gSearch)) return false;
              return true;
            });
            if (filtered.length === 0) return (
              <div style={{ textAlign: "center", padding: "40px 0", color: COLORS.muted }}>
                <div style={{ fontSize: 40, marginBottom: 10 }}>✅</div>
                <p>{alarmFilter === "all" && !gFilterActive ? "No alarms raised yet." : "No alarms match the current filters."}</p>
              </div>
            );

            // Group by date
            const byDate = {};
            filtered.forEach(a => { if (!byDate[a.date]) byDate[a.date] = []; byDate[a.date].push(a); });
            const sortedDates = Object.keys(byDate).sort((a, b) => b.localeCompare(a));

            return sortedDates.map(date => (
              <div key={date} style={{ marginBottom: 24 }}>
                {/* Day header */}
                <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 12 }}>
                  <div style={{ fontSize: 12, fontWeight: 700, color: COLORS.text, background: COLORS.card, borderRadius: 20, padding: "5px 16px", border: `1px solid ${COLORS.border}` }}>
                    📅 {new Date(date).toLocaleDateString("en-IN", { weekday: "long", day: "2-digit", month: "long", year: "numeric" })}
                  </div>
                  <div style={{ fontSize: 12, color: COLORS.muted }}>{byDate[date].length} alarm{byDate[date].length !== 1 ? "s" : ""} · {byDate[date].filter(a => !a.resolved).length} unresolved</div>
                </div>

                {byDate[date].map((alarm) => (
                  <div key={alarm.id} style={{ background: COLORS.card, borderRadius: 12, padding: "16px 18px", marginBottom: 10, border: `1px solid ${alarm.resolved ? COLORS.border : "rgba(231,76,60,0.45)"}` }}>
                    <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 12 }}>
                      <div>
                        <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 4 }}>
                          <span style={{ fontSize: 18 }}>{alarm.resolved ? "✅" : "🚨"}</span>
                          <span style={{ fontSize: 14, fontWeight: 700, color: COLORS.text }}>{alarm.attemptedName}</span>
                          <span style={{ fontSize: 12, color: COLORS.muted }}>· {alarm.attemptedMobile}</span>
                          {alarm.hits?.length > 1 && <span style={{ background: "rgba(231,76,60,0.15)", color: COLORS.danger, borderRadius: 20, padding: "2px 8px", fontSize: 11, fontWeight: 700 }}>{alarm.hits.length} fields</span>}
                        </div>
                        <div style={{ fontSize: 11, color: COLORS.muted }}>{fmtTs(alarm.timestamp)}</div>
                      </div>
                      <div style={{ display: "flex", gap: 6, alignItems: "center" }}>
                        <span style={s.badge(alarm.resolved ? "approved" : "rejected")}>{alarm.resolved ? "✅ Resolved" : "🔴 Unresolved"}</span>
                        {!alarm.resolved && (
                          <button onClick={() => {
                            const updated = alarms.map(a => a.id === alarm.id ? { ...a, resolved: true, resolvedAt: localISO() } : a);
                            setAlarms(updated);
                          }} style={{ background: "rgba(46,204,113,0.15)", border: `1px solid rgba(46,204,113,0.4)`, borderRadius: 7, padding: "4px 10px", color: COLORS.success, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>
                            ✓ Resolve
                          </button>
                        )}
                      </div>
                    </div>

                    {/* Hit rows */}
                    <div style={{ display: "flex", flexDirection: "column", gap: 6 }}>
                      {alarm.hits?.map((h, j) => (
                        <div key={j} style={{ background: "rgba(231,76,60,0.07)", borderRadius: 8, padding: "10px 14px", border: `1px solid rgba(231,76,60,0.2)`, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
                          <div>
                            <span style={{ fontSize: 11, color: COLORS.danger, fontWeight: 700, marginRight: 8, textTransform: "uppercase" }}>{h.field}</span>
                            <span style={{ fontSize: 13, fontWeight: 600, color: COLORS.text, fontFamily: "monospace" }}>{h.value}</span>
                          </div>
                          <div style={{ fontSize: 11, color: COLORS.muted, textAlign: "right" }}>
                            <div>Previously: <strong style={{ color: COLORS.text }}>{h.existingName}</strong></div>
                            <div>{fmtTs(h.existingTime)}</div>
                          </div>
                        </div>
                      ))}
                    </div>
                    {alarm.resolved && alarm.resolvedAt && (
                      <div style={{ fontSize: 11, color: COLORS.muted, marginTop: 8, paddingTop: 8, borderTop: `1px solid ${COLORS.border}` }}>✅ Resolved at {fmtTs(alarm.resolvedAt)}</div>
                    )}
                  </div>
                ))}
              </div>
            ));
          })()}
        </div>
      )}

      {/* ── Export Tab ── */}
      {activeTab === "export" && (() => {
        // Apply export-specific filters on top of global filter (gCandidates)
        const applyFilters = () => {
          return gCandidates.filter(c => {
            const regDate = localDateOf(c.registeredAt) || "";
            if (expFromDate && regDate < expFromDate) return false;
            if (expToDate && regDate > expToDate) return false;
            if (expReferBy !== "all" && c.referBy !== expReferBy) return false;
            if (expRejoiner !== "all" && c.isRejoiner !== expRejoiner) return false;
            if (expTestResult === "cleared" && !(c.aptScore >= 10 && c.typingScore?.passed)) return false;
            if (expTestResult === "aptFailed" && !(c.aptScore != null && c.aptScore < 10)) return false;
            if (expTestResult === "typingFailed" && !(c.aptScore >= 10 && c.typingScore && !c.typingScore.passed)) return false;
            if (expTestResult === "notStarted" && c.aptScore != null) return false;
            if (expPanel !== "all" && c.panelStatus !== expPanel) return false;
            return true;
          });
        };

        const filtered = applyFilters();

        // Group by registration date
        const byDate = {};
        filtered.forEach(c => {
          const d = localDateOf(c.registeredAt) || "Unknown";
          if (!byDate[d]) byDate[d] = [];
          byDate[d].push(c);
        });
        const sortedDates = Object.keys(byDate).sort((a, b) => b.localeCompare(a));

        // Build CSV
        const filterPill = (label, value, setter, options) => (
          <div style={{ display: "flex", flexDirection: "column", gap: 4 }}>
            <div style={{ fontSize: 11, color: COLORS.muted, fontWeight: 600, letterSpacing: 0.5 }}>{label}</div>
            <select
              value={value}
              onChange={e => setter(e.target.value)}
              style={{ ...s.select, marginBottom: 0, fontSize: 13, padding: "8px 12px", minWidth: 140 }}
            >
              {options.map(([v, l]) => <option key={v} value={v}>{l}</option>)}
            </select>
          </div>
        );

        return (
          <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 20 }}>
              <div>
                <h2 style={{ ...s.h2, margin: 0 }}>⬇ Export Candidate Data</h2>
                <p style={{ fontSize: 12, color: COLORS.muted, margin: "4px 0 0" }}>
                  {gFilterActive ? `Global filters active · base pool: ${gCandidates.length}/${candidates.length} candidates` : "Filter by date range and attributes, then download as CSV"}
                </p>
              </div>
              <div style={{ display: "flex", gap: 8 }}>
                <button
                  onClick={() => setExpPreview(p => !p)}
                  style={{ background: "rgba(99,102,241,0.12)", border: `1px solid rgba(99,102,241,0.3)`, borderRadius: 8, padding: "7px 14px", color: "#818cf8", cursor: "pointer", fontSize: 13, fontWeight: 600 }}
                >
                  {expPreview ? "Hide Preview" : "👁 Preview"}
                </button>
                <button
                  onClick={() => downloadCSV(filtered, `recruitpro-export-${expFromDate || "all"}-to-${expToDate || "all"}.csv`, panelists)}
                  style={{ ...s.btn, width: "auto", padding: "8px 20px", background: COLORS.success, marginTop: 0, fontSize: 13 }}
                  disabled={filtered.length === 0}
                >
                  ⬇ Download CSV ({filtered.length})
                </button>
              </div>
            </div>

            {/* ── Filters ── */}
            <div style={{ background: COLORS.card, borderRadius: 14, padding: 18, marginBottom: 20, border: `1px solid ${COLORS.border}` }}>
              <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 14 }}>🔍 Filters</div>

              {/* Date range */}
              <div style={{ display: "flex", gap: 12, flexWrap: "wrap", marginBottom: 14 }}>
                <div style={{ display: "flex", flexDirection: "column", gap: 4 }}>
                  <div style={{ fontSize: 11, color: COLORS.muted, fontWeight: 600, letterSpacing: 0.5 }}>FROM DATE</div>
                  <input
                    type="date"
                    value={expFromDate}
                    onChange={e => setExpFromDate(e.target.value)}
                    style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "8px 12px", width: 160 }}
                  />
                </div>
                <div style={{ display: "flex", flexDirection: "column", gap: 4 }}>
                  <div style={{ fontSize: 11, color: COLORS.muted, fontWeight: 600, letterSpacing: 0.5 }}>TO DATE</div>
                  <input
                    type="date"
                    value={expToDate}
                    onChange={e => setExpToDate(e.target.value)}
                    style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "8px 12px", width: 160 }}
                  />
                </div>
                {/* Quick date buttons */}
                <div style={{ display: "flex", flexDirection: "column", gap: 4 }}>
                  <div style={{ fontSize: 11, color: COLORS.muted, fontWeight: 600, letterSpacing: 0.5 }}>QUICK SELECT</div>
                  <div style={{ display: "flex", gap: 6 }}>
                    {[["Today", 0], ["Last 7d", 7], ["Last 30d", 30], ["All Time", null]].map(([label, days]) => (
                      <button key={label} onClick={() => {
                        if (days === null) { setExpFromDate(""); setExpToDate(""); }
                        else {
                          const to = localISO().slice(0, 10);
                          const from = (() => { const d = new Date(Date.now() - days * 86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })();
                          setExpFromDate(days === 0 ? to : from);
                          setExpToDate(to);
                        }
                      }} style={{ padding: "7px 12px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}>{label}</button>
                    ))}
                  </div>
                </div>
              </div>

              {/* Other filters */}
              <div style={{ display: "flex", gap: 12, flexWrap: "wrap" }}>
                {filterPill("REFERRED BY", expReferBy, setExpReferBy, [["all","All Sources"],["walkin","Walk-in"],["website","Website"],["referral","Referral"]])}
                {filterPill("REJOINER", expRejoiner, setExpRejoiner, [["all","All"],["Yes","Rejoiner"],["No","Fresh"]])}
                {filterPill("TEST RESULT", expTestResult, setExpTestResult, [["all","All"],["cleared","Cleared Both"],["aptFailed","Apt Failed"],["typingFailed","Typing Failed"],["notStarted","Not Started"]])}
                {filterPill("PANEL STATUS", expPanel, setExpPanel, [["all","All"],["pending","Pending"],["approved","Approved"],["rejected","Rejected"]])}
                <div style={{ display: "flex", flexDirection: "column", gap: 4, justifyContent: "flex-end" }}>
                  <button onClick={() => { setExpFromDate(""); setExpToDate(""); setExpReferBy("all"); setExpRejoiner("all"); setExpTestResult("all"); setExpPanel("all"); }} style={{ padding: "8px 14px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: "transparent", color: COLORS.muted, cursor: "pointer", fontSize: 12 }}>✕ Clear All</button>
                </div>
              </div>
            </div>

            {/* ── Result summary ── */}
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10, marginBottom: 20 }}>
              {[
                ["Total Matching", filtered.length, COLORS.gold],
                ["Date Range", sortedDates.length + " days", "#818cf8"],
                ["Cleared Tests", filtered.filter(c => c.aptScore >= 10 && c.typingScore?.passed).length, COLORS.success],
                ["Flagged Duplicates", filtered.filter(c => c.duplicateFlagged).length, COLORS.danger],
              ].map(([label, val, color]) => (
                <div key={label} style={{ background: COLORS.card, borderRadius: 12, padding: "12px 16px", border: `1px solid ${COLORS.border}` }}>
                  <div style={{ fontSize: 11, color: COLORS.muted }}>{label}</div>
                  <div style={{ fontSize: 22, fontWeight: 800, color }}>{val}</div>
                </div>
              ))}
            </div>

            {/* ── Day-wise download buttons ── */}
            {sortedDates.length > 0 && (
              <div style={{ marginBottom: 20 }}>
                <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 12 }}>📅 Day-wise Export</div>
                <div style={{ display: "flex", flexDirection: "column", gap: 8 }}>
                  {sortedDates.map(date => (
                    <div key={date} style={{ background: COLORS.card, borderRadius: 12, padding: "12px 16px", border: `1px solid ${COLORS.border}`, display: "flex", justifyContent: "space-between", alignItems: "center" }}>
                      <div>
                        <div style={{ fontSize: 13, fontWeight: 600, color: COLORS.text }}>
                          {new Date(date).toLocaleDateString("en-IN", { weekday: "long", day: "2-digit", month: "long", year: "numeric" })}
                        </div>
                        <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 3, display: "flex", gap: 14 }}>
                          <span>{byDate[date].length} candidates</span>
                          <span style={{ color: COLORS.success }}>{byDate[date].filter(c => c.aptScore >= 10 && c.typingScore?.passed).length} cleared</span>
                          <span style={{ color: COLORS.warning }}>{byDate[date].filter(c => c.panelStatus === "pending" && c.aptScore >= 10 && c.typingScore?.passed).length} pending panel</span>
                          <span style={{ color: "#818cf8" }}>{byDate[date].filter(c => c.panelStatus === "approved").length} approved</span>
                          {byDate[date].filter(c => c.duplicateFlagged).length > 0 && <span style={{ color: COLORS.danger }}>⚠ {byDate[date].filter(c => c.duplicateFlagged).length} flagged</span>}
                        </div>
                      </div>
                      <button
                        onClick={() => downloadCSV(byDate[date], `recruitpro-${date}.csv`, panelists)}
                        style={{ background: "rgba(46,204,113,0.12)", border: `1px solid rgba(46,204,113,0.35)`, borderRadius: 8, padding: "7px 16px", color: COLORS.success, cursor: "pointer", fontSize: 12, fontWeight: 700, whiteSpace: "nowrap" }}
                      >⬇ Download {date}</button>
                    </div>
                  ))}
                </div>
              </div>
            )}

            {filtered.length === 0 && (
              <div style={{ textAlign: "center", padding: "40px 0", color: COLORS.muted }}>
                <div style={{ fontSize: 40, marginBottom: 10 }}>📭</div>
                <p>No candidates match the selected filters.</p>
              </div>
            )}

            {/* ── Preview Table ── */}
            {expPreview && filtered.length > 0 && (
              <div style={{ marginTop: 8 }}>
                <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.text, marginBottom: 12 }}>👁 Data Preview ({Math.min(filtered.length, 50)} of {filtered.length})</div>
                <div style={{ overflowX: "auto", borderRadius: 12, border: `1px solid ${COLORS.border}` }}>
                  <table style={{ width: "100%", borderCollapse: "collapse", fontSize: 11, minWidth: 900 }}>
                    <thead>
                      <tr style={{ background: COLORS.card }}>
                        {["Photo", "Date", "Name", "Mobile", "Refer By", "Rejoiner", "PAN", "Aadhaar", "Apt", "Typing", "Panel", "Panelist", "Flagged"].map(h => (
                          <th key={h} style={{ padding: "9px 12px", textAlign: "left", color: COLORS.muted, fontWeight: 700, borderBottom: `1px solid ${COLORS.border}`, whiteSpace: "nowrap", fontSize: 10, letterSpacing: 0.5 }}>{h}</th>
                        ))}
                      </tr>
                    </thead>
                    <tbody>
                      {filtered.slice(0, 50).map((c, i) => {
                        const pan = panelists.find(p => p.id === c.assignedPanelistId);
                        return (
                          <tr key={c.id} style={{ borderBottom: `1px solid ${COLORS.border}`, background: i % 2 === 0 ? "transparent" : "rgba(255,255,255,0.02)" }}>
                            <td style={{ padding: "6px 12px" }}>
                              {c.photoData
                                ? <img src={c.photoData} alt="" style={{ width: 28, height: 28, borderRadius: "50%", objectFit: "cover", border: `1px solid ${COLORS.border}` }} />
                                : <div style={{ width: 28, height: 28, borderRadius: "50%", background: COLORS.card, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 12 }}>👤</div>
                              }
                            </td>
                            <td style={{ padding: "8px 12px", color: COLORS.muted, whiteSpace: "nowrap" }}>{localDateOf(c.registeredAt)}</td>
                            <td style={{ padding: "8px 12px", color: COLORS.text, fontWeight: 600 }}>{c.name}</td>
                            <td style={{ padding: "8px 12px", color: COLORS.muted }}>{c.mobile}</td>
                            <td style={{ padding: "8px 12px", color: COLORS.muted, textTransform: "capitalize" }}>{c.referBy}{c.empId ? ` (${c.empId})` : ""}</td>
                            <td style={{ padding: "8px 12px", color: c.isRejoiner === "Yes" ? COLORS.warning : COLORS.muted }}>{c.isRejoiner}</td>
                            <td style={{ padding: "8px 12px", color: COLORS.muted, fontFamily: "monospace" }}>{c.pan}</td>
                            <td style={{ padding: "8px 12px", color: COLORS.muted, fontFamily: "monospace" }}>{c.aadhaar.slice(0,4)}XXXX{c.aadhaar.slice(-4)}</td>
                            <td style={{ padding: "8px 12px" }}>
                              <span style={{ color: c.aptScore == null ? COLORS.muted : c.aptScore >= 10 ? COLORS.success : COLORS.danger, fontWeight: 600 }}>
                                {c.aptScore == null ? "—" : `${c.aptScore}/15`}
                              </span>
                            </td>
                            <td style={{ padding: "8px 12px" }}>
                              <span style={{ color: !c.typingScore ? COLORS.muted : c.typingScore.passed ? COLORS.success : COLORS.danger, fontWeight: 600 }}>
                                {!c.typingScore ? "—" : `${c.typingScore.wpm}wpm`}
                              </span>
                            </td>
                            <td style={{ padding: "8px 12px" }}>
                              <span style={s.badge(c.panelStatus)}>{c.panelStatus}</span>
                            </td>
                            <td style={{ padding: "8px 12px", color: COLORS.muted }}>{pan?.username || "—"}</td>
                            <td style={{ padding: "8px 12px" }}>
                              {c.duplicateFlagged ? <span style={{ color: COLORS.danger, fontWeight: 700 }}>⚠ Yes</span> : <span style={{ color: COLORS.muted }}>—</span>}
                            </td>
                          </tr>
                        );
                      })}
                    </tbody>
                  </table>
                </div>
                {filtered.length > 50 && <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 8, textAlign: "center" }}>Showing 50 of {filtered.length}. Download CSV to see all records.</div>}
              </div>
            )}
          </div>
        );
      })()}

      {confirmReset && (
        <div style={{ position: "fixed", inset: 0, background: "rgba(0,0,0,0.7)", display: "flex", alignItems: "center", justifyContent: "center", zIndex: 200, padding: 20 }}>
          <div style={{ background: COLORS.surface, borderRadius: 16, padding: 28, width: "100%", maxWidth: 420, border: `1px solid ${COLORS.border}` }}>

            {/* ── Password Reset confirm ── */}
            {confirmReset.type === "resetPwd" && !confirmReset.done && (
              <>
                <div style={{ fontSize: 36, textAlign: "center", marginBottom: 12 }}>🔑</div>
                <h2 style={{ ...s.h2, textAlign: "center" }}>Reset Password?</h2>
                <p style={{ fontSize: 14, color: COLORS.muted, textAlign: "center", marginBottom: 20 }}>
                  A new random password will be generated for <strong style={{ color: COLORS.text }}>{confirmReset.candidate.name}</strong>. The old password will stop working immediately.
                </p>
                <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(120px, 1fr))", gap: 10 }}>
                  <button onClick={() => setConfirmReset(null)} style={{ ...s.btnOut, marginTop: 0 }}>Cancel</button>
                  <button onClick={() => resetCandidatePassword(confirmReset.candidate.id)} style={{ padding: "12px", borderRadius: 10, border: "none", background: "#3498db", color: "#fff", cursor: "pointer", fontWeight: 600 }}>Yes, Reset</button>
                </div>
              </>
            )}

            {/* ── Password Reset done — show new password ── */}
            {confirmReset.type === "resetPwd" && confirmReset.done && (
              <>
                <div style={{ fontSize: 36, textAlign: "center", marginBottom: 12 }}>✅</div>
                <h2 style={{ ...s.h2, textAlign: "center" }}>Password Reset!</h2>
                <p style={{ fontSize: 14, color: COLORS.muted, textAlign: "center", marginBottom: 16 }}>
                  New credentials for <strong style={{ color: COLORS.text }}>{confirmReset.candidate.name}</strong>:
                </p>
                <div style={{ background: COLORS.card, borderRadius: 12, padding: "18px", marginBottom: 16, border: `1px solid rgba(52,152,219,0.4)` }}>
                  <div style={{ marginBottom: 12 }}>
                    <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>USERNAME</div>
                    <div style={{ fontSize: 20, fontWeight: 800, color: COLORS.gold, letterSpacing: 2 }}>{confirmReset.candidate.username}</div>
                  </div>
                  <div style={{ borderTop: `1px solid ${COLORS.border}`, paddingTop: 12 }}>
                    <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>NEW PASSWORD</div>
                    <div style={{ fontSize: 20, fontWeight: 800, color: "#3498db", letterSpacing: 2 }}>{confirmReset.newPassword}</div>
                  </div>
                </div>
                <div style={{ ...s.alert("warning"), marginBottom: 16 }}>
                  ⚠️ Share this new password with the candidate directly. It will not be shown again.
                </div>
                <button onClick={() => setConfirmReset(null)} style={s.btn}>Done</button>
              </>
            )}

            {/* ── Other confirm types (delete, reset tests, delete panelist) ── */}
            {confirmReset.type !== "resetPwd" && (
              <>
                <div style={{ fontSize: 36, textAlign: "center", marginBottom: 12 }}>{confirmReset.type === "delete" ? "🗑" : confirmReset.type === "deletePanelist" ? "🗑" : "↺"}</div>
                <h2 style={{ ...s.h2, textAlign: "center" }}>
                  {confirmReset.type === "delete" ? "Delete Candidate?" : confirmReset.type === "deletePanelist" ? "Remove Panelist?" : "Reset Tests?"}
                </h2>
                <p style={{ fontSize: 14, color: COLORS.muted, textAlign: "center", marginBottom: 20 }}>
                  {confirmReset.type === "delete"
                    ? `Permanently remove ${confirmReset.candidate.name} and all their data. Cannot be undone.`
                    : confirmReset.type === "deletePanelist"
                    ? `Remove ${confirmReset.panelist.name || confirmReset.panelist.username} from the system. Their assigned candidates will need reassignment.`
                    : `Reset all test scores for ${confirmReset.candidate.name}. They will need to retake all tests.`}
                </p>
                <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(120px, 1fr))", gap: 10 }}>
                  <button onClick={() => setConfirmReset(null)} style={{ ...s.btnOut, marginTop: 0 }}>Cancel</button>
                  <button onClick={() => {
                    if (confirmReset.type === "delete") deleteCandidate(confirmReset.candidate.id);
                    else if (confirmReset.type === "deletePanelist") { setPanelists(p => p.filter(x => x.id !== confirmReset.panelist.id)); setConfirmReset(null); }
                    else resetCandidateTests(confirmReset.candidate.id);
                  }} style={{ padding: "12px", borderRadius: 10, border: "none", background: confirmReset.type === "reset" ? COLORS.warning : COLORS.danger, color: "#fff", cursor: "pointer", fontWeight: 600 }}>
                    {confirmReset.type === "delete" ? "Yes, Delete" : confirmReset.type === "deletePanelist" ? "Yes, Remove" : "Yes, Reset"}
                  </button>
                </div>
              </>
            )}
          </div>
        </div>
      )}
    </div>
  );
}

// ─── Login ────────────────────────────────────────────────────────────────────
function LoginScreen({ candidates, onLogin, onAdminLogin, onSuperAdminLogin, panelists, onPanelistsave, superAdmin, onSuperAdminSave }) {
  const [u, setU] = useState("");
  const [pwd, setPwd] = useState("");
  const [err, setErr] = useState("");
  const [tab, setTab] = useState("candidate");
  const [au, setAu] = useState("");
  const [ap, setAp] = useState("");
  const [su, setSu] = useState("");
  const [sp, setSp] = useState("");
  const [showSetup, setShowSetup] = useState(false);
  const [showSASetup, setShowSASetup] = useState(false);

  const noPanelists = !panelists || panelists.length === 0;
  const noSuperAdmin = !superAdmin;

  // Find matching panelist — use distinct param name to avoid shadowing
  const matchedPanelist = panelists?.find(pan => pan.username === au);
  const isExpired = matchedPanelist && new Date(matchedPanelist.expiresAt) < new Date();
  const daysLeft = matchedPanelist ? Math.max(0, Math.ceil((new Date(matchedPanelist.expiresAt) - Date.now()) / (1000 * 60 * 60 * 24))) : null;
  const nearExpiry = matchedPanelist && daysLeft <= 14 && !isExpired;

  if (showSetup) return <PanelistSetup existing={null} onSave={cred => { onPanelistsave(prev => [...(prev || []), cred]); setShowSetup(false); }} onCancel={() => setShowSetup(false)} />;
  if (showSASetup) return <SuperAdminSetup existing={superAdmin} onSave={cred => { onSuperAdminSave(cred); setShowSASetup(false); }} onCancel={noSuperAdmin ? null : () => setShowSASetup(false)} />;

  function handleLogin() {
    // Username is PAN card — match case-insensitively
    const found = candidates.find(c =>
      c.username?.toUpperCase() === u.trim().toUpperCase() && c.password === pwd
    );
    if (found) { setErr(""); onLogin(found); }
    else setErr("Invalid PAN (User ID) or password.");
  }

  function handleAdmin() {
    if (noPanelists) { setErr("No panelist accounts exist yet. Contact super admin."); return; }
    if (!matchedPanelist) { setErr("Username not found."); return; }
    if (matchedPanelist.disabled) { setErr("This panelist account is disabled. Contact super admin."); return; }
    if (isExpired) { setErr("Your credentials have expired. Contact super admin to reset."); return; }
    if (ap === matchedPanelist.password) { setErr(""); onAdminLogin(matchedPanelist); }
    else setErr("Incorrect password.");
  }

  function handleSuperAdmin() {
    if (!superAdmin) { setErr("No super admin account set up yet."); return; }
    if (su === superAdmin.username && sp === superAdmin.password) { setErr(""); onSuperAdminLogin(); }
    else setErr("Invalid super admin credentials.");
  }

  return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={s.navTabs}>
          <button style={s.tab(tab === "candidate")} onClick={() => { setTab("candidate"); setErr(""); }}>Candidate</button>
          <button style={s.tab(tab === "panelist")} onClick={() => { setTab("panelist"); setErr(""); }}>Panelist</button>
          <button style={s.tab(tab === "superadmin")} onClick={() => { setTab("superadmin"); setErr(""); }}>👑 Super Admin</button>
        </div>

        {/* Candidate */}
        {tab === "candidate" && <>
          <h2 style={s.h2}>Welcome Back</h2>
          <label style={s.label}>User ID</label>
          <input
            style={{ ...s.input, textTransform: "uppercase", letterSpacing: 2, fontFamily: "monospace", fontWeight: 600 }}
            placeholder="ABCDE1234F"
            value={u}
            maxLength={10}
            onChange={e => setU(e.target.value.toUpperCase())}
          />
          <label style={s.label}>Password</label>
          <input style={s.input} type="password" placeholder="Enter your password" value={pwd} onChange={e => setPwd(e.target.value)} onKeyDown={e => e.key === "Enter" && handleLogin()} />
          {err && <div style={s.alert("danger")}>{err}</div>}
          <button style={s.btn} onClick={handleLogin}>Login →</button>
          <p style={{ textAlign: "center", fontSize: 13, color: COLORS.muted, marginTop: 16 }}>Don't have credentials? <span style={{ color: COLORS.accent, cursor: "pointer" }} onClick={() => window.dispatchEvent(new CustomEvent("goRegister"))}>Register here</span></p>
        </>}

        {/* Panelist */}
        {tab === "panelist" && <>
          <h2 style={s.h2}>Panelist Access</h2>
          {noPanelists && <div style={{ ...s.alert("warning"), marginBottom: 16 }}>No panelist accounts exist yet. Contact super admin.</div>}
          {nearExpiry && <div style={{ ...s.alert("warning"), marginBottom: 16 }}>⚠️ Your credentials expire in <strong>{daysLeft} day{daysLeft !== 1 ? "s" : ""}</strong>.</div>}
          {isExpired && <div style={{ ...s.alert("danger"), marginBottom: 16 }}>🔒 Credentials expired. Contact super admin to reset.</div>}

          {!noPanelists && <>
            <label style={s.label}>Username</label>
            <input style={s.input} placeholder="Your panelist username" value={au} onChange={e => { setAu(e.target.value); setErr(""); }} />
            <label style={s.label}>Password</label>
            <input style={s.input} type="password" placeholder="Your password" value={ap} onChange={e => setAp(e.target.value)} onKeyDown={e => e.key === "Enter" && handleAdmin()} />
            {matchedPanelist && !isExpired && (
              <div style={{ marginBottom: 12 }}>
                <div style={{ display: "flex", justifyContent: "space-between", fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>
                  <span>Credential validity</span>
                  <span style={{ color: daysLeft <= 14 ? COLORS.danger : COLORS.success }}>{daysLeft} days left</span>
                </div>
                <div style={{ background: COLORS.card, borderRadius: 20, height: 6 }}>
                  <div style={{ height: "100%", width: `${Math.min(100, (daysLeft / 90) * 100)}%`, background: daysLeft <= 14 ? COLORS.danger : daysLeft <= 30 ? COLORS.warning : COLORS.success, borderRadius: 20 }} />
                </div>
              </div>
            )}
            {err && <div style={s.alert("danger")}>{err}</div>}
            <button style={s.btn} onClick={handleAdmin}>Login as Panelist →</button>
          </>}
        </>}

        {/* Super Admin */}
        {tab === "superadmin" && <>
          <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 16, padding: "10px 14px", background: "rgba(233,69,96,0.08)", borderRadius: 10, border: `1px solid rgba(233,69,96,0.25)` }}>
            <span style={{ fontSize: 18 }}>👑</span>
            <div style={{ fontSize: 13, color: COLORS.muted }}>Full system access. Use responsibly.</div>
          </div>
          {noSuperAdmin && <div style={{ ...s.alert("warning"), marginBottom: 16 }}>No super admin account set up yet.</div>}
          {superAdmin && <>
            <label style={s.label}>Super Admin Username</label>
            <input style={s.input} placeholder="Super admin username" value={su} onChange={e => setSu(e.target.value)} />
            <label style={s.label}>Password</label>
            <input style={s.input} type="password" placeholder="Super admin password" value={sp} onChange={e => setSp(e.target.value)} onKeyDown={e => e.key === "Enter" && handleSuperAdmin()} />
            {err && <div style={s.alert("danger")}>{err}</div>}
            <button style={{ ...s.btn, background: COLORS.accent }} onClick={handleSuperAdmin}>👑 Login as Super Admin →</button>
          </>}
          {noSuperAdmin && <button style={{ ...s.btn, background: COLORS.accent }} onClick={() => setShowSASetup(true)}>👑 Set Up Super Admin Account →</button>}
          {superAdmin && <button style={{ ...s.btnOut, marginTop: 8, fontSize: 13 }} onClick={() => setShowSASetup(true)}>🔄 Change Credentials</button>}
        </>}
      </div>
    </div>
  );
}

// ─── Aptitude Test ────────────────────────────────────────────────────────────
function AptitudeTest({ candidate, onComplete }) {
  const [answers, setAnswers] = useState({});
  const [submitted, setSubmitted] = useState(false);
  const [score, setScore] = useState(0);
  const [timeLeft, setTimeLeft] = useState(20 * 60);
  const [timedOut, setTimedOut] = useState(false);

  useEffect(() => {
    if (submitted) return;
    const t = setInterval(() => setTimeLeft(p => {
      if (p <= 1) {
        clearInterval(t);
        autoSubmit();
        return 0;
      }
      return p - 1;
    }), 1000);
    return () => clearInterval(t);
  }, [submitted]);

  function autoSubmit() {
    if (submitted) return;
    let s = 0;
    APTITUDE_QUESTIONS.forEach((q, i) => { if (answers[i] === q.ans) s++; });
    setScore(s);
    setTimedOut(true);
    setSubmitted(true);
  }

  function submit() {
    if (submitted) return;
    let s = 0;
    APTITUDE_QUESTIONS.forEach((q, i) => { if (answers[i] === q.ans) s++; });
    setScore(s);
    setSubmitted(true);
  }

  const mins = Math.floor(timeLeft / 60).toString().padStart(2, "0");
  const secs = (timeLeft % 60).toString().padStart(2, "0");
  const passed = score >= 10;

  if (submitted) return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ textAlign: "center" }}>
          {timedOut && (
            <div style={{ background: "rgba(243,156,18,0.12)", border: `1px solid ${COLORS.warning}`, borderRadius: 10, padding: "10px 16px", marginBottom: 16, fontSize: 13, color: COLORS.warning, fontWeight: 600 }}>
              ⏱ Time's up! The test was automatically submitted.
            </div>
          )}
          <div style={{ fontSize: 52 }}>{passed ? "🎯" : "😔"}</div>
          <h2 style={s.h2}>Aptitude Test {passed ? "Passed!" : "Not Cleared"}</h2>
          <div style={{ fontSize: 48, fontWeight: 800, color: passed ? COLORS.success : COLORS.danger, margin: "16px 0" }}>{score}<span style={{ fontSize: 20, color: COLORS.muted }}>/15</span></div>
          <div style={{ ...s.alert(passed ? "success" : "danger") }}>
            {passed ? "✅ You scored above the passing mark of 10/15. Proceed to the Typing Test." : "❌ Passing mark is 10/15. Unfortunately you did not clear this round."}
          </div>
          <button style={s.btn} onClick={() => onComplete(score, passed)}>
            {passed ? "Start Typing Test →" : "View Results →"}
          </button>
        </div>
      </div>
    </div>
  );

  return (
    <div style={s.page}>
      <Logo />
      <div style={{ ...s.wideCard }}>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20 }}>
          <div>
            <h2 style={{ ...s.h2, marginBottom: 4 }}>Aptitude Test</h2>
            <p style={{ ...s.sub, margin: 0 }}>{Object.keys(answers).length}/15 answered</p>
          </div>
          <div style={{ background: COLORS.card, borderRadius: 10, padding: "8px 16px", textAlign: "center", border: `1px solid ${timeLeft < 120 ? COLORS.danger : COLORS.border}` }}>
            <div style={{ fontSize: 11, color: COLORS.muted }}>TIME LEFT</div>
            <div style={{ fontSize: 22, fontWeight: 700, color: timeLeft < 120 ? COLORS.danger : COLORS.gold }}>{mins}:{secs}</div>
          </div>
        </div>
        <div style={{ display: "grid", gap: 14, maxHeight: "60vh", overflowY: "auto", paddingRight: 4 }}>
          {APTITUDE_QUESTIONS.map((q, i) => (
            <div key={i} style={{ background: COLORS.card, borderRadius: 12, padding: "16px", border: `1px solid ${answers[i] !== undefined ? COLORS.accent + "66" : COLORS.border}` }}>
              <p style={{ fontWeight: 600, fontSize: 14, margin: "0 0 12px", color: COLORS.text }}>Q{i + 1}. {q.q}</p>
              <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(130px, 1fr))", gap: 8 }}>
                {q.opts.map((o, j) => (
                  <button key={j} onClick={() => setAnswers(p => ({ ...p, [i]: j }))} style={{ padding: "9px 12px", borderRadius: 8, border: `1px solid ${answers[i] === j ? COLORS.accent : COLORS.border}`, background: answers[i] === j ? "rgba(233,69,96,0.2)" : COLORS.surface, color: answers[i] === j ? COLORS.accent : COLORS.text, cursor: "pointer", fontSize: 13, textAlign: "left" }}>
                    {String.fromCharCode(65 + j)}. {o}
                  </button>
                ))}
              </div>
            </div>
          ))}
        </div>
        <button style={{ ...s.btn, marginTop: 16 }} onClick={() => submit()}>Submit Test</button>
      </div>
    </div>
  );
}

// ─── Typing Test ──────────────────────────────────────────────────────────────
function TypingTest({ candidate, aptScore, onComplete }) {
  const [started, setStarted] = useState(false);
  const [typed, setTyped] = useState("");
  const [startTime, setStartTime] = useState(null);
  const [finished, setFinished] = useState(false);
  const [results, setResults] = useState(null);
  const [timeLeft, setTimeLeft] = useState(60);
  const inputRef = useRef();

  useEffect(() => {
    if (!started || finished) return;
    const t = setInterval(() => setTimeLeft(p => {
      if (p <= 1) { clearInterval(t); finishTest(typed); return 0; }
      return p - 1;
    }), 1000);
    return () => clearInterval(t);
  }, [started, finished, typed]);

  function start() { setStarted(true); setStartTime(Date.now()); inputRef.current?.focus(); }

  function finishTest(currentTyped) {
    if (finished) return;
    setFinished(true);
    const elapsed = (Date.now() - startTime) / 1000 / 60 || 1;
    const words = currentTyped.trim().split(/\s+/).length;
    const wpm = Math.round(words / elapsed);
    const target = TYPING_PASSAGE;
    let correct = 0;
    for (let i = 0; i < Math.min(currentTyped.length, target.length); i++) {
      if (currentTyped[i] === target[i]) correct++;
    }
    const accuracy = currentTyped.length > 0 ? Math.round((correct / target.length) * 100) : 0;
    const passed = wpm >= 20 && accuracy >= 90;
    setResults({ wpm, accuracy, passed });
  }

  function handleType(e) {
    const val = e.target.value;
    if (!started) return;
    setTyped(val);
    if (val.length >= TYPING_PASSAGE.length) finishTest(val);
  }

  if (finished && results) {
    return (
      <div style={s.page}>
        <Logo />
        <div style={s.card}>
          <div style={{ textAlign: "center" }}>
            <div style={{ fontSize: 52 }}>{results.passed ? "⌨️" : "😔"}</div>
            <h2 style={s.h2}>Typing Test {results.passed ? "Passed!" : "Not Cleared"}</h2>
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 12, marginBottom: 20 }}>
              <div style={{ background: COLORS.card, borderRadius: 12, padding: 16, border: `1px solid ${results.wpm >= 20 ? COLORS.success + "55" : COLORS.danger + "55"}` }}>
                <div style={{ fontSize: 11, color: COLORS.muted }}>SPEED</div>
                <div style={{ fontSize: 32, fontWeight: 800, color: results.wpm >= 20 ? COLORS.success : COLORS.danger }}>{results.wpm}</div>
                <div style={{ fontSize: 11, color: COLORS.muted }}>WPM (min: 20)</div>
              </div>
              <div style={{ background: COLORS.card, borderRadius: 12, padding: 16, border: `1px solid ${results.accuracy >= 90 ? COLORS.success + "55" : COLORS.danger + "55"}` }}>
                <div style={{ fontSize: 11, color: COLORS.muted }}>ACCURACY</div>
                <div style={{ fontSize: 32, fontWeight: 800, color: results.accuracy >= 90 ? COLORS.success : COLORS.danger }}>{results.accuracy}%</div>
                <div style={{ fontSize: 11, color: COLORS.muted }}>Required: 90%</div>
              </div>
            </div>
            <div style={s.alert(results.passed ? "success" : "danger")}>
              {results.passed ? "✅ Excellent! You've cleared both tests. Your details have been forwarded to the panel." : "❌ You need ≥20 WPM and ≥90% accuracy to pass."}
            </div>
            <button style={s.btn} onClick={() => onComplete(results, aptScore)}>
              {results.passed ? "View Status →" : "Go to Dashboard"}
            </button>
          </div>
        </div>
      </div>
    );
  }

  const words = typed.trim() ? typed.trim().split(/\s+/).length : 0;
  const elapsed = startTime ? Math.max((Date.now() - startTime) / 1000 / 60, 0.01) : 1;
  const liveWpm = Math.round(words / elapsed);

  return (
    <div style={s.page}>
      <Logo />
      <div style={s.wideCard}>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
          <div>
            <h2 style={{ ...s.h2, marginBottom: 4 }}>Typing Test</h2>
            <p style={{ ...s.sub, margin: 0 }}>Type the passage below. Target: 20+ WPM & 90%+ accuracy.</p>
          </div>
          {started && <div style={{ background: COLORS.card, borderRadius: 10, padding: "8px 16px", textAlign: "center" }}>
            <div style={{ fontSize: 11, color: COLORS.muted }}>TIME</div>
            <div style={{ fontSize: 22, fontWeight: 700, color: timeLeft < 15 ? COLORS.danger : COLORS.gold }}>{timeLeft}s</div>
          </div>}
        </div>

        <div style={{ background: COLORS.card, borderRadius: 12, padding: "16px 20px", marginBottom: 16, lineHeight: 1.7, fontSize: 15, border: `1px solid ${COLORS.border}`, fontFamily: "monospace" }}>
          {TYPING_PASSAGE.split("").map((ch, i) => {
            let color = COLORS.muted;
            if (i < typed.length) color = typed[i] === ch ? COLORS.success : COLORS.danger;
            return <span key={i} style={{ color, background: i === typed.length ? "rgba(233,69,96,0.3)" : "transparent" }}>{ch}</span>;
          })}
        </div>

        {!started ? (
          <button style={s.btn} onClick={start}>▶ Start Typing Test</button>
        ) : (
          <>
            <textarea
              ref={inputRef}
              value={typed}
              onChange={handleType}
              disabled={finished}
              rows={5}
              style={{ ...s.input, resize: "none", fontFamily: "monospace", marginBottom: 12 }}
              placeholder="Start typing here..."
            />
            <div style={{ display: "flex", gap: 10, justifyContent: "space-between", marginBottom: 12, fontSize: 13, color: COLORS.muted }}>
              <span>Live WPM: <strong style={{ color: COLORS.gold }}>{liveWpm}</strong></span>
              <span>Characters: {typed.length}/{TYPING_PASSAGE.length}</span>
            </div>
            <button style={s.btn} onClick={() => finishTest(typed)}>Submit Typing Test</button>
          </>
        )}
      </div>
    </div>
  );
}

// ─── Candidate Dashboard ──────────────────────────────────────────────────────
function CandidateDashboard({ candidate, panelists, onLogout }) {
  const status = candidate.panelStatus;
  const assignedPanelist = panelists?.find(p => p.id === candidate.assignedPanelistId);
  return (
    <div style={s.page}>
      <Logo />
      <div style={s.card}>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 20 }}>
          <div>
            <h2 style={s.h2}>Hello, {candidate.name.split(" ")[0]}!</h2>
            <p style={{ ...s.sub, margin: 0 }}>Your recruitment status</p>
          </div>
          <button onClick={onLogout} style={{ background: "none", border: `1px solid ${COLORS.border}`, borderRadius: 8, padding: "6px 12px", color: COLORS.muted, cursor: "pointer", fontSize: 12 }}>Logout</button>
        </div>
        <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10, marginBottom: 20 }}>
          {[["Aptitude", candidate.aptScore != null ? `${candidate.aptScore}/15` : "—", candidate.aptScore >= 10], ["Typing", candidate.typingScore != null ? `${candidate.typingScore.wpm} WPM` : "—", candidate.typingScore?.passed]].map(([label, val, pass]) => (
            <div key={label} style={{ background: COLORS.card, borderRadius: 12, padding: 16, textAlign: "center", border: `1px solid ${val === "—" ? COLORS.border : pass ? COLORS.success + "55" : COLORS.danger + "55"}` }}>
              <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>{label.toUpperCase()}</div>
              <div style={{ fontSize: 22, fontWeight: 700 }}>{val}</div>
              {val !== "—" && <div style={{ fontSize: 11, marginTop: 4, color: pass ? COLORS.success : COLORS.danger }}>{pass ? "✓ Passed" : "✗ Failed"}</div>}
            </div>
          ))}
        </div>

        {/* Assigned panelist — only show after clearing both tests */}
        {candidate.aptScore >= 10 && candidate.typingScore?.passed && (
          assignedPanelist ? (
            <div style={{ borderRadius: 14, marginBottom: 14, overflow: "hidden", border: `1.5px solid ${assignedPanelist.onBreak ? "rgba(243,156,18,0.5)" : "rgba(52,152,219,0.5)"}` }}>
              {/* Header strip */}
              <div style={{ background: assignedPanelist.onBreak ? "rgba(243,156,18,0.15)" : "rgba(52,152,219,0.18)", padding: "10px 16px", display: "flex", alignItems: "center", gap: 8 }}>
                <span style={{ fontSize: 15 }}>{assignedPanelist.onBreak ? "☕" : "🎯"}</span>
                <span style={{ fontSize: 12, fontWeight: 700, color: assignedPanelist.onBreak ? COLORS.warning : "#3498db", letterSpacing: 0.5 }}>YOUR ASSIGNED PANELIST</span>
              </div>
              {/* Body */}
              <div style={{ background: COLORS.card, padding: "16px" }}>
                <div style={{ display: "flex", alignItems: "center", gap: 14 }}>
                  <div style={{ width: 52, height: 52, borderRadius: "50%", background: assignedPanelist.onBreak ? "linear-gradient(135deg,rgba(243,156,18,0.25),rgba(243,156,18,0.08))" : "linear-gradient(135deg,rgba(52,152,219,0.35),rgba(52,152,219,0.1))", border: `2px solid ${assignedPanelist.onBreak ? "rgba(243,156,18,0.5)" : "rgba(52,152,219,0.4)"}`, display: "flex", alignItems: "center", justifyContent: "center", flexShrink: 0 }}>
                    <span style={{ fontSize: 20, fontWeight: 800, color: assignedPanelist.onBreak ? COLORS.warning : "#3498db" }}>
                      {assignedPanelist.onBreak ? "☕" : (assignedPanelist.name || assignedPanelist.username).charAt(0).toUpperCase()}
                    </span>
                  </div>
                  <div style={{ flex: 1 }}>
                    <div style={{ fontSize: 18, fontWeight: 700, color: COLORS.text, marginBottom: 2 }}>
                      {assignedPanelist.name || assignedPanelist.username}
                    </div>
                    <div style={{ fontSize: 13, color: COLORS.muted }}>{assignedPanelist.email}</div>
                    {assignedPanelist.name && (
                      <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 2 }}>@{assignedPanelist.username}</div>
                    )}
                  </div>
                  {/* Status badge */}
                  <div style={{ textAlign: "right" }}>
                    {assignedPanelist.onBreak ? (
                      <div style={{ display: "inline-flex", alignItems: "center", gap: 5, background: "rgba(243,156,18,0.15)", border: "1px solid rgba(243,156,18,0.4)", borderRadius: 20, padding: "4px 12px" }}>
                        <span style={{ fontSize: 13 }}>☕</span>
                        <span style={{ fontSize: 12, fontWeight: 700, color: COLORS.warning }}>On Break</span>
                      </div>
                    ) : (
                      <div style={{ display: "inline-flex", alignItems: "center", gap: 5, background: "rgba(52,152,219,0.15)", border: "1px solid rgba(52,152,219,0.35)", borderRadius: 20, padding: "4px 12px" }}>
                        <span style={{ width: 7, height: 7, borderRadius: "50%", background: "#3498db", display: "inline-block" }} />
                        <span style={{ fontSize: 12, fontWeight: 600, color: "#3498db" }}>Active</span>
                      </div>
                    )}
                  </div>
                </div>

                {/* On-break message */}
                {assignedPanelist.onBreak && (
                  <div style={{ marginTop: 12, background: "rgba(243,156,18,0.08)", border: "1px solid rgba(243,156,18,0.25)", borderRadius: 8, padding: "10px 12px", fontSize: 12, color: COLORS.warning }}>
                    ☕ Your panelist is currently on a short break.{assignedPanelist.breakStartedAt ? ` Break started at ${fmtTs(assignedPanelist.breakStartedAt)}.` : ""} Your interview is still scheduled — please wait, they will be back soon and will complete your interview.
                  </div>
                )}

                {candidate.assignedAt && (
                  <div style={{ marginTop: 10, paddingTop: 10, borderTop: `1px solid ${COLORS.border}`, fontSize: 12, color: COLORS.muted }}>
                    📅 Assigned on {fmtTs(candidate.assignedAt)}
                  </div>
                )}
              </div>
            </div>
          ) : (
            <div style={{ background: COLORS.card, borderRadius: 14, padding: 16, marginBottom: 14, border: `1.5px dashed ${COLORS.border}`, textAlign: "center" }}>
              <div style={{ fontSize: 28, marginBottom: 6 }}>⏳</div>
              <div style={{ fontSize: 14, fontWeight: 600, color: COLORS.text, marginBottom: 4 }}>Awaiting Panelist Assignment</div>
              <div style={{ fontSize: 12, color: COLORS.muted }}>You've cleared both tests! A panelist will be assigned to you shortly.</div>
            </div>
          )
        )}

        {/* Failed tests — show try again message */}
        {(() => {
          const aptDone    = candidate.aptScore != null;
          const aptFailed  = aptDone && candidate.aptScore < 10;
          const aptPassed  = aptDone && candidate.aptScore >= 10;
          const typingDone = aptPassed && candidate.typingScore != null;
          const typingFailed = typingDone && !candidate.typingScore.passed;

          if (!aptFailed && !typingFailed) return null;

          let icon, title, message;
          if (aptFailed && typingFailed) {
            // Both failed (edge case if test order changes)
            icon = "😔"; title = "Both Tests Not Cleared";
            message = "You did not clear the Aptitude and Typing tests. Please try again later.";
          } else if (aptFailed) {
            icon = "📝"; title = "Aptitude Test Not Cleared";
            message = `You scored ${candidate.aptScore}/15. The passing mark is 10/15. Please try again later.`;
          } else {
            icon = "⌨️"; title = "Typing Test Not Cleared";
            message = `Your typing speed was ${candidate.typingScore?.wpm} WPM with ${candidate.typingScore?.accuracy}% accuracy. Required: 20 WPM and 90% accuracy. Please try again later.`;
          }

          return (
            <div style={{ background: "rgba(231,76,60,0.07)", border: `1.5px solid rgba(231,76,60,0.35)`, borderRadius: 14, padding: "18px 16px", marginBottom: 14, textAlign: "center" }}>
              <div style={{ fontSize: 36, marginBottom: 8 }}>{icon}</div>
              <div style={{ fontSize: 15, fontWeight: 700, color: COLORS.danger, marginBottom: 8 }}>{title}</div>
              <div style={{ fontSize: 13, color: COLORS.muted, lineHeight: 1.6 }}>{message}</div>
              <div style={{ marginTop: 12, fontSize: 12, color: COLORS.muted, background: COLORS.card, borderRadius: 8, padding: "8px 12px", display: "inline-block" }}>
                💡 Please try again later or contact the HR team for assistance.
              </div>
            </div>
          );
        })()}

        {/* Panel decision — only show if tests are cleared */}
        {candidate.aptScore >= 10 && candidate.typingScore?.passed && (
        <div style={{ background: COLORS.card, borderRadius: 12, padding: 16, border: `1px solid ${status === "approved" ? COLORS.success + "55" : status === "rejected" ? COLORS.danger + "55" : COLORS.warning + "55"}` }}>
          <div style={{ fontSize: 12, color: COLORS.muted, marginBottom: 8 }}>PANEL DECISION</div>
          <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
            <div style={{ fontSize: 28 }}>{status === "approved" ? "✅" : status === "rejected" ? "❌" : "⏳"}</div>
            <div>
              <div style={{ fontWeight: 700, fontSize: 16, textTransform: "capitalize", color: status === "approved" ? COLORS.success : status === "rejected" ? COLORS.danger : COLORS.warning }}>{status === "pending" ? "Awaiting Review" : status}</div>
              {candidate.panelRemark && <div style={{ fontSize: 13, color: COLORS.muted, marginTop: 2 }}>{candidate.panelRemark}</div>}
            </div>
          </div>
        </div>
        )}
      </div>
    </div>
  );
}

// ─── Timestamp formatter ──────────────────────────────────────────────────────
function fmtTs(iso) {
  if (!iso) return "—";
  const d = new Date(iso);
  return d.toLocaleString("en-IN", { day: "2-digit", month: "short", year: "numeric", hour: "2-digit", minute: "2-digit", hour12: true });
}

// ─── Panel Dashboard ──────────────────────────────────────────────────────────
function PanelDashboard({ candidates, setCandidates, panelists, setPanelists, currentPanelist, onPanelistSave, alarms, onLogout }) {
  const [selected, setSelected] = useState(null);
  const [remark, setRemark] = useState("");
  const [filter, setFilter] = useState("all");
  const [activeTab, setActiveTab] = useState("final");
  const [showCred, setShowCred] = useState({});
  const [search, setSearch] = useState("");
  const [changingCreds, setChangingCreds] = useState(false);
  const [modalAlarm, setModalAlarm] = useState(null); // same-day repeat alarm shown in modal
  const [peopleSearch, setPeopleSearch] = useState("");
  const [showTransfer, setShowTransfer] = useState(false);
  const [transferTarget, setTransferTarget] = useState("");
  const [showBreakModal, setShowBreakModal] = useState(false);
  const [bulkTransferTarget, setBulkTransferTarget] = useState("");

  const isOnBreak = panelists.find(p => p.id === currentPanelist?.id)?.onBreak === true;
  const livePanelist = panelists.find(p => p.id === currentPanelist?.id) || currentPanelist;

  // AI state per candidate modal
  const [aiSummary, setAiSummary] = useState(null);
  const [aiLoading, setAiLoading] = useState(false);
  const [aiDecision, setAiDecision] = useState(null);
  const [aiRemarkSuggestion, setAiRemarkSuggestion] = useState(null);
  const [aiRemarkLoading, setAiRemarkLoading] = useState(false);
  const [resumeTab, setResumeTab] = useState("insights"); // "insights" | "resume"

  async function fetchAiInsights(candidate) {
    if (aiSummary?.candidateId === candidate.id) return;
    setAiLoading(true);
    setAiSummary(null);
    setAiDecision(null);
    try {
      // Build message content — include PDF resume if available
      const contentParts = [];

      if (candidate.resumeData && candidate.resume?.toLowerCase().endsWith(".pdf")) {
        // Pass resume as base64 PDF document to Claude
        const base64 = candidate.resumeData.split(",")[1];
        contentParts.push({
          type: "document",
          source: { type: "base64", media_type: "application/pdf", data: base64 }
        });
      }

      const profileText = `You are an expert HR recruitment analyst. Analyse this candidate${candidate.resumeData && candidate.resume?.toLowerCase().endsWith(".pdf") ? " using their uploaded resume (above) AND" : " using"} the profile data below.

Candidate Profile:
- Name: ${candidate.name}
- Referred by: ${candidate.referBy}${candidate.empId ? ` (Emp ID: ${candidate.empId})` : ""}
- Rejoiner: ${candidate.isRejoiner}
- Aptitude Score: ${candidate.aptScore}/15 (passing: 10/15)
- Typing Speed: ${candidate.typingScore?.wpm} WPM (passing: 20 WPM)
- Typing Accuracy: ${candidate.typingScore?.accuracy}% (passing: 90%)
- Resume file: ${candidate.resume || "Not provided"}
- Registered: ${fmtTs(candidate.registeredAt)}
- Duplicate flagged: ${candidate.duplicateFlagged ? "Yes" : "No"}
${candidate.resumeData && candidate.resume?.toLowerCase().endsWith(".pdf") ? "\nIMPORTANT: Use the actual resume content to extract skills, experience, education and enrich your analysis." : ""}

Respond ONLY with valid JSON, no markdown, no extra text:
{
  "summary": "2-3 sentence professional summary using resume content if available",
  "resumeHighlights": {
    "experience": "key experience found (or 'Not available' if no resume)",
    "skills": ["skill1", "skill2", "skill3"],
    "education": "highest qualification found (or 'Not available')",
    "totalExperience": "e.g. '3 years' or 'Fresher' or 'Not available'"
  },
  "score": <0-100>,
  "scoreBreakdown": {
    "aptitude": <0-40>,
    "typing": <0-30>,
    "profile": <0-30>
  },
  "strengths": ["strength1", "strength2"],
  "concerns": ["concern1"],
  "recommendation": "approve" | "reject" | "hold",
  "recommendationReason": "one sentence reason"
}`;

      contentParts.push({ type: "text", text: profileText });

      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 800,
          messages: [{ role: "user", content: contentParts }]
        })
      });
      const data = await res.json();
      const text = data.content?.[0]?.text || "{}";
      const clean = text.replace(/```json|```/g, "").trim();
      const parsed = JSON.parse(clean);
      setAiSummary({ ...parsed, candidateId: candidate.id, resumeRead: !!(candidate.resumeData && candidate.resume?.toLowerCase().endsWith(".pdf")) });
      setAiDecision(parsed.recommendation);
    } catch (_) {
      setAiSummary({ error: true, candidateId: candidate.id });
    } finally {
      setAiLoading(false);
    }
  }

  async function generateAiRemark(candidate, decision) {
    setAiRemarkLoading(true);
    setAiRemarkSuggestion(null);
    try {
      const prompt = `Write a brief, professional HR remark for a recruitment decision.
Candidate: ${candidate.name}
Aptitude: ${candidate.aptScore}/15, Typing: ${candidate.typingScore?.wpm} WPM / ${candidate.typingScore?.accuracy}%
Decision: ${decision}
Write ONE concise sentence (max 20 words) as the remark. Plain text only, no quotes.`;

      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 80,
          messages: [{ role: "user", content: prompt }]
        })
      });
      const data = await res.json();
      setAiRemarkSuggestion(data.content?.[0]?.text?.trim() || "");
    } catch (_) {
      setAiRemarkSuggestion("");
    } finally {
      setAiRemarkLoading(false);
    }
  }

  // Final Round filters
  const [finalDateFrom, setFinalDateFrom] = useState("");
  const [finalDateTo, setFinalDateTo] = useState("");

  // All Registered filters
  const [allDateFrom, setAllDateFrom] = useState("");
  const [allDateTo, setAllDateTo] = useState("");
  const [allStatusFilter, setAllStatusFilter] = useState("all");
  const [allReferBy, setAllReferBy] = useState("all");
  const [allRejoiner, setAllRejoiner] = useState("all");

  const daysLeft = currentPanelist ? Math.max(0, Math.ceil((new Date(currentPanelist.expiresAt) - Date.now()) / (1000 * 60 * 60 * 24))) : 0;
  const nearExpiry = daysLeft <= 14;

  if (changingCreds) {
    return <PanelistSetup existing={currentPanelist} onSave={cred => { onPanelistSave(cred); setChangingCreds(false); }} onCancel={() => setChangingCreds(false)} />;
  }

  // Group all applications by username (PAN = unique person ID)
  const allByUsername = {};
  candidates.forEach(c => {
    const key = c.username?.toUpperCase();
    if (!allByUsername[key]) allByUsername[key] = [];
    allByUsername[key].push(c);
  });

  // Unique people list (latest application per username)
  const uniquePeople = Object.values(allByUsername).map(apps => {
    const sorted = [...apps].sort((a, b) => new Date(b.registeredAt) - new Date(a.registeredAt));
    return { ...sorted[0], _allApps: sorted, _appCount: apps.length };
  });

  function openCandidate(c) {
    // Check if this username has applied more than once today
    const key = c.username?.toUpperCase();
    const todayApps = (allByUsername[key] || []).filter(a => localDateOf(a.registeredAt) === todayStr());
    const alarm = todayApps.length > 1 ? todayApps : null;
    setSelected(c);
    setRemark(c.panelRemark || "");
    setModalAlarm(alarm);
    setShowTransfer(false);
    setTransferTarget("");
    setAiSummary(null); setAiDecision(null); setAiRemarkSuggestion(null);
    setResumeTab("insights");
    fetchAiInsights(c);
  }
  function toggleBreak() {
    if (!isOnBreak) {
      setShowBreakModal(true);
    } else {
      const updated = { ...livePanelist, onBreak: false, breakStartedAt: null };
      setPanelists(p => p.map(x => x.id === updated.id ? updated : x));
      onPanelistSave(updated);
      // Auto-assign any candidates who cleared tests while all panelists were on break
      const waiting = candidates.filter(c =>
        c.aptScore >= 10 && c.typingScore?.passed &&
        !c.assignedPanelistId && c.panelStatus === "pending"
      );
      if (waiting.length > 0) {
        setCandidates(prev => prev.map(c =>
          waiting.find(w => w.id === c.id)
            ? { ...c, assignedPanelistId: updated.id, assignedAt: localISO() }
            : c
        ));
      }
    }
  }

  function confirmBreak(withBulkTransfer) {
    const updated = { ...livePanelist, onBreak: true, breakStartedAt: localISO() };
    setPanelists(p => p.map(x => x.id === updated.id ? updated : x));
    onPanelistSave(updated);
    if (withBulkTransfer && bulkTransferTarget) {
      const pendingQueue = candidates.filter(c => c.assignedPanelistId === livePanelist.id && c.panelStatus === "pending");
      setCandidates(prev => prev.map(c =>
        pendingQueue.find(pq => pq.id === c.id)
          ? { ...c, assignedPanelistId: bulkTransferTarget, assignedAt: localISO(), transferredFrom: livePanelist.id, transferredAt: localISO() }
          : c
      ));
    }
    setShowBreakModal(false);
    setBulkTransferTarget("");
  }

  const myEligible = candidates.filter(c => c.aptScore >= 10 && c.typingScore?.passed && c.assignedPanelistId === currentPanelist?.id);
  const filtered = myEligible.filter(c => {
    const regDate = localDateOf(c.registeredAt) || "";
    if (filter !== "all" && c.panelStatus !== filter) return false;
    if (finalDateFrom && regDate < finalDateFrom) return false;
    if (finalDateTo && regDate > finalDateTo) return false;
    return true;
  });

  const allFiltered = candidates.filter(c => {
    const regDate = localDateOf(c.registeredAt) || "";
    if (search && !c.name.toLowerCase().includes(search.toLowerCase()) && !c.mobile.includes(search) && !c.username?.toLowerCase().includes(search.toLowerCase()) && !c.pan?.toLowerCase().includes(search.toLowerCase())) return false;
    if (allDateFrom && regDate < allDateFrom) return false;
    if (allDateTo && regDate > allDateTo) return false;
    if (allReferBy !== "all" && c.referBy !== allReferBy) return false;
    if (allRejoiner !== "all" && c.isRejoiner !== allRejoiner) return false;
    if (allStatusFilter !== "all") {
      if (allStatusFilter === "notStarted" && c.aptScore != null) return false;
      if (allStatusFilter === "aptFailed" && !(c.aptScore != null && c.aptScore < 10)) return false;
      if (allStatusFilter === "typingFailed" && !(c.aptScore >= 10 && c.typingScore && !c.typingScore.passed)) return false;
      if (allStatusFilter === "cleared" && !(c.aptScore >= 10 && c.typingScore?.passed)) return false;
      if (allStatusFilter === "approved" && c.panelStatus !== "approved") return false;
      if (allStatusFilter === "rejected" && c.panelStatus !== "rejected") return false;
    }
    return true;
  });

  function decide(id, status) {
    setCandidates(p => p.map(c => c.id === id ? { ...c, panelStatus: status, panelRemark: remark, panelDecidedAt: localISO() } : c));
    setSelected(null);
    setRemark("");
    setShowTransfer(false);
    setTransferTarget("");
  }

  function doTransfer() {
    if (!transferTarget) return;
    const targetPanelist = panelists.find(p => p.id === transferTarget);
    if (!targetPanelist) return;
    setCandidates(p => p.map(c =>
      c.id === selected.id
        ? { ...c, assignedPanelistId: transferTarget, assignedAt: localISO(), transferredFrom: currentPanelist?.id, transferredAt: localISO() }
        : c
    ));
    setSelected(null);
    setShowTransfer(false);
    setTransferTarget("");
    setRemark("");
  }

  const stats = {
    total: filtered.length,
    approved: filtered.filter(c => c.panelStatus === "approved").length,
    rejected: filtered.filter(c => c.panelStatus === "rejected").length,
    pending: filtered.filter(c => c.panelStatus === "pending").length,
  };

  const testStatusLabel = (c) => {
    if (c.aptScore == null) return { label: "Not Started", color: COLORS.muted };
    if (c.aptScore < 10) return { label: "Apt Failed", color: COLORS.danger };
    if (!c.typingScore) return { label: "Typing Pending", color: COLORS.warning };
    if (!c.typingScore.passed) return { label: "Typing Failed", color: COLORS.danger };
    return { label: "Cleared", color: COLORS.success };
  };

  return (
    <div style={{ ...s.page, alignItems: "stretch", width: "100%", maxWidth: 1200, margin: "0 auto", padding: "16px 12px 60px" }}>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", padding: "20px 0 16px" }}>
        <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
          <Logo />
          <div style={{ background: "rgba(52,152,219,0.12)", border: `1px solid rgba(52,152,219,0.3)`, borderRadius: 20, padding: "3px 12px", fontSize: 12, fontWeight: 600, color: "#3498db" }}>🎯 {currentPanelist?.name || currentPanelist?.username}</div>
        </div>
        <div style={{ display: "flex", gap: 8, alignItems: "center" }}>
          {nearExpiry && <span style={{ fontSize: 12, color: COLORS.danger, fontWeight: 600 }}>⚠️ Creds expire in {daysLeft}d</span>}
          {(() => {
            // Only show alert if: alarm is unresolved AND the attempted candidate
            // (matched by mobile/PAN/Aadhaar) has NOT been given a panel decision yet
            const actionableAlarms = alarms?.filter(a => {
              if (a.resolved) return false;
              // Check if any of the matched existing candidates still have pending panel status
              return a.hits?.some(h => {
                const existingC = candidates.find(c => c.name === h.existingName && c.registeredAt === h.existingTime);
                if (!existingC) return true; // can't verify, show it
                return existingC.panelStatus === "pending"; // only show if still pending
              });
            });
            return actionableAlarms?.length > 0 ? (
              <div style={{ background: "rgba(231,76,60,0.15)", border: `1px solid rgba(231,76,60,0.4)`, borderRadius: 20, padding: "4px 12px", fontSize: 12, fontWeight: 700, color: COLORS.danger }}>
                🚨 {actionableAlarms.length} Duplicate Alert{actionableAlarms.length !== 1 ? "s" : ""}
              </div>
            ) : null;
          })()}
          <button onClick={() => setChangingCreds(true)} style={{ background: "none", border: `1px solid ${nearExpiry ? COLORS.danger : COLORS.border}`, borderRadius: 8, padding: "7px 12px", color: nearExpiry ? COLORS.danger : COLORS.muted, cursor: "pointer", fontSize: 12 }}>🔄 Change Credentials</button>
          {/* On Break toggle */}
          <button
            onClick={toggleBreak}
            style={{ background: isOnBreak ? "rgba(46,204,113,0.15)" : "rgba(243,156,18,0.12)", border: `1px solid ${isOnBreak ? "rgba(46,204,113,0.4)" : "rgba(243,156,18,0.4)"}`, borderRadius: 8, padding: "7px 14px", color: isOnBreak ? COLORS.success : COLORS.warning, cursor: "pointer", fontSize: 13, fontWeight: 700 }}
          >{isOnBreak ? "🟢 Go Active" : "☕ On Break"}</button>
          <button onClick={onLogout} style={{ background: "none", border: `1px solid ${COLORS.border}`, borderRadius: 8, padding: "7px 14px", color: COLORS.muted, cursor: "pointer", fontSize: 13 }}>Logout</button>
        </div>
      </div>

      {/* On Break banner */}
      {isOnBreak && (
        <div style={{ background: "rgba(243,156,18,0.1)", border: `1px solid rgba(243,156,18,0.4)`, borderRadius: 12, padding: "14px 18px", marginBottom: 16, display: "flex", justifyContent: "space-between", alignItems: "center", flexWrap: "wrap", gap: 10 }}>
          <div>
            <div style={{ fontSize: 14, fontWeight: 700, color: COLORS.warning, marginBottom: 3 }}>☕ You are currently On Break</div>
            <div style={{ fontSize: 12, color: COLORS.muted }}>
              No new candidates will be assigned to you until you go active. {livePanelist?.breakStartedAt && `Break started: ${fmtTs(livePanelist.breakStartedAt)}`}
            </div>
          </div>
          <button onClick={toggleBreak} style={{ background: "rgba(46,204,113,0.15)", border: `1px solid rgba(46,204,113,0.4)`, borderRadius: 8, padding: "8px 16px", color: COLORS.success, cursor: "pointer", fontSize: 13, fontWeight: 700 }}>🟢 Go Active Now</button>
        </div>
      )}

      {nearExpiry && (
        <div style={{ ...s.alert("danger"), marginBottom: 16 }}>
          ⚠️ Your panelist credentials expire in <strong>{daysLeft} day{daysLeft !== 1 ? "s" : ""}</strong> on {fmtTs(currentPanelist?.expiresAt)}. Please update them before they expire.
        </div>
      )}

      {/* Stats — reflect active filters */}
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 10, marginBottom: 20 }}>
        {[["Assigned to Me", stats.total, COLORS.gold], ["Approved", stats.approved, COLORS.success], ["Rejected", stats.rejected, COLORS.danger], ["Pending", stats.pending, COLORS.warning]].map(([label, val, color]) => (
          <div key={label} style={{ background: COLORS.surface, borderRadius: 12, padding: 16, border: `1px solid ${COLORS.border}`, position: "relative", overflow: "hidden" }}>
            <div style={{ position: "absolute", top: 0, left: 0, right: 0, height: 3, background: color, borderRadius: "12px 12px 0 0" }} />
            <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 6 }}>{label}</div>
            <div style={{ fontSize: 28, fontWeight: 800, color }}>{val}</div>
            {(finalDateFrom || finalDateTo || filter !== "all") && (
              <div style={{ fontSize: 10, color: COLORS.muted, marginTop: 4 }}>
                {myEligible.length !== filtered.length ? `of ${myEligible.filter(c => label === "Assigned to Me" ? true : label === "Approved" ? c.panelStatus === "approved" : label === "Rejected" ? c.panelStatus === "rejected" : c.panelStatus === "pending").length} total` : ""}
              </div>
            )}
          </div>
        ))}
      </div>

      {/* Filter active banner */}
      {(finalDateFrom || finalDateTo || filter !== "all") && (
        <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 12, padding: "8px 14px", background: "rgba(233,69,96,0.07)", borderRadius: 10, border: `1px solid rgba(233,69,96,0.2)`, fontSize: 12, color: COLORS.muted }}>
          <span style={{ color: COLORS.accent, fontWeight: 700 }}>🔍 Filters active</span>
          {filter !== "all" && <span style={{ background: COLORS.card, borderRadius: 20, padding: "2px 8px" }}>Status: {filter}</span>}
          {finalDateFrom && <span style={{ background: COLORS.card, borderRadius: 20, padding: "2px 8px" }}>From: {finalDateFrom}</span>}
          {finalDateTo && <span style={{ background: COLORS.card, borderRadius: 20, padding: "2px 8px" }}>To: {finalDateTo}</span>}
          <span style={{ marginLeft: "auto", color: COLORS.muted }}>Showing {filtered.length} of {myEligible.length}</span>
        </div>
      )}

      {/* Tabs */}
      <div style={s.navTabs}>
        <button style={s.tab(activeTab === "final")} onClick={() => setActiveTab("final")}>
          Final Round ({filtered.length}{filtered.length !== myEligible.length ? `/${myEligible.length}` : ""})
        </button>
        <button style={s.tab(activeTab === "all")} onClick={() => setActiveTab("all")}>
          All Registered ({allFiltered.length}{allFiltered.length !== candidates.length ? `/${candidates.length}` : ""})
        </button>
        <button style={s.tab(activeTab === "people")} onClick={() => setActiveTab("people")}>
          👥 Unique People ({uniquePeople.length})
        </button>
        <button style={s.tab(activeTab === "log")} onClick={() => setActiveTab("log")}>
          📋 Log
        </button>
      </div>

      {/* ── Final Round tab ── */}
      {activeTab === "final" && (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 14 }}>
            <h2 style={{ ...s.h2, margin: 0 }}>My Assigned Candidates</h2>
            <div style={{ display: "flex", gap: 8, alignItems: "center" }}>
              <span style={{ fontSize: 13, color: COLORS.muted }}>{filtered.length} of {myEligible.length} shown</span>
              <DownloadBtn rows={filtered} filename={`recruitpro-final-round-${todayStr()}.csv`} panelists={panelists} label="Download" />
            </div>
          </div>

          {/* Filter panel */}
          <div style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", marginBottom: 16, border: `1px solid ${COLORS.border}` }}>
            <div style={{ display: "flex", gap: 10, flexWrap: "wrap", alignItems: "flex-end" }}>
              {/* Date From */}
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>FROM DATE</div>
                <input type="date" value={finalDateFrom} onChange={e => setFinalDateFrom(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
              </div>
              {/* Date To */}
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TO DATE</div>
                <input type="date" value={finalDateTo} onChange={e => setFinalDateTo(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
              </div>
              {/* Quick dates */}
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>QUICK</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["Today", () => { const t = todayStr(); setFinalDateFrom(t); setFinalDateTo(t); }],
                    ["Last 7d", () => { setFinalDateFrom((() => { const d = new Date(Date.now()-7*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })()); setFinalDateTo(todayStr()); }],
                    ["All", () => { setFinalDateFrom(""); setFinalDateTo(""); }]
                  ].map(([l, fn]) => (
                    <button key={l} onClick={fn} style={{ padding: "6px 10px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
              {/* Status */}
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>STATUS</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All",COLORS.muted],["pending","⏳ Pending",COLORS.warning],["approved","✅ Approved",COLORS.success],["rejected","❌ Rejected",COLORS.danger]].map(([v, l, c]) => (
                    <button key={v} onClick={() => setFilter(v)} style={{ padding: "6px 12px", borderRadius: 20, border: `1px solid ${filter === v ? c : COLORS.border}`, background: filter === v ? c + "22" : "transparent", color: filter === v ? c : COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}>{l}</button>
                  ))}
                </div>
              </div>
              {/* Clear */}
              {(finalDateFrom || finalDateTo || filter !== "all") && (
                <button onClick={() => { setFinalDateFrom(""); setFinalDateTo(""); setFilter("all"); }} style={{ padding: "7px 12px", borderRadius: 8, border: `1px solid rgba(233,69,96,0.3)`, background: "rgba(233,69,96,0.08)", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600, alignSelf: "flex-end" }}>✕ Clear</button>
              )}
            </div>
          </div>

          {filtered.length === 0 ? (
            <div style={{ textAlign: "center", padding: "40px 0", color: COLORS.muted }}>
              <div style={{ fontSize: 40, marginBottom: 10 }}>📋</div>
              <p>{myEligible.length === 0 ? "No candidates assigned to you yet. New qualifiers will be auto-assigned here." : "No candidates match the selected filters."}</p>
            </div>
          ) : filtered.map(c => (
            <div key={c.id} style={{ background: COLORS.card, borderRadius: 12, padding: "16px 18px", marginBottom: 10, border: `1px solid ${COLORS.border}`, cursor: "pointer" }} onClick={() => openCandidate(c)}>
              <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center" }}>
                <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                  {c.photoData
                    ? <img src={c.photoData} alt="" style={{ width: 38, height: 38, borderRadius: "50%", objectFit: "cover", border: `2px solid ${COLORS.border}`, flexShrink: 0 }} />
                    : <div style={{ width: 38, height: 38, borderRadius: "50%", background: COLORS.card, border: `2px solid ${COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 16, flexShrink: 0 }}>👤</div>}
                  <div>
                    <div style={{ fontWeight: 600, fontSize: 15, display: "flex", alignItems: "center", gap: 6 }}>
                      {c.name}
                      {c.transferredFrom && (
                        <span style={{ fontSize: 11, background: "rgba(52,152,219,0.12)", border: "1px solid rgba(52,152,219,0.3)", borderRadius: 20, padding: "2px 8px", color: "#3498db", fontWeight: 700 }}>↗ Transferred</span>
                      )}
                    </div>
                    <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 2 }}>📱 {c.mobile} · {c.referBy} · {c.isRejoiner === "Yes" ? "Rejoiner" : "Fresh"} · {localDateOf(c.registeredAt)}</div>
                  </div>
                </div>
                <div style={{ textAlign: "right" }}>
                  <div style={s.badge(c.panelStatus)}>{c.panelStatus === "pending" ? "⏳ Pending" : c.panelStatus === "approved" ? "✅ Approved" : "❌ Rejected"}</div>
                  <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 6 }}>Apt: {c.aptScore}/15 · {c.typingScore?.wpm} WPM {c.typingScore?.accuracy}%</div>
                </div>
              </div>
            </div>
          ))}
        </div>
      )}

      {/* ── All Registered tab ── */}
      {activeTab === "all" && (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 14 }}>
            <h2 style={{ ...s.h2, margin: 0 }}>All Registered Candidates</h2>
            <div style={{ display: "flex", gap: 8, alignItems: "center" }}>
              <span style={{ fontSize: 13, color: COLORS.muted }}>{allFiltered.length} of {candidates.length} shown</span>
              <DownloadBtn rows={allFiltered} filename={`recruitpro-all-registered-${todayStr()}.csv`} panelists={panelists} label="Download" />
            </div>
          </div>

          {/* Filter panel */}
          <div style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", marginBottom: 16, border: `1px solid ${COLORS.border}` }}>
            {/* Row 1: search + clear */}
            <div style={{ display: "flex", gap: 10, marginBottom: 12, alignItems: "center" }}>
              <input
                style={{ ...s.input, marginBottom: 0, flex: 1, fontSize: 13, padding: "9px 14px" }}
                placeholder="🔍 🔍 Search by name, mobile or PAN..."
                value={search}
                onChange={e => setSearch(e.target.value)}
              />
              {(search || allDateFrom || allDateTo || allStatusFilter !== "all" || allReferBy !== "all" || allRejoiner !== "all") && (
                <button onClick={() => { setSearch(""); setAllDateFrom(""); setAllDateTo(""); setAllStatusFilter("all"); setAllReferBy("all"); setAllRejoiner("all"); }} style={{ padding: "9px 14px", borderRadius: 8, border: `1px solid rgba(233,69,96,0.3)`, background: "rgba(233,69,96,0.08)", color: COLORS.accent, cursor: "pointer", fontSize: 12, fontWeight: 600, whiteSpace: "nowrap" }}>✕ Clear All</button>
              )}
            </div>
            {/* Row 2: date range */}
            <div style={{ display: "flex", gap: 10, marginBottom: 12, flexWrap: "wrap", alignItems: "flex-end" }}>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>FROM DATE</div>
                <input type="date" value={allDateFrom} onChange={e => setAllDateFrom(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>TO DATE</div>
                <input type="date" value={allDateTo} onChange={e => setAllDateTo(e.target.value)} style={{ ...s.input, marginBottom: 0, fontSize: 13, padding: "7px 12px", width: 148 }} />
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 5 }}>QUICK</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["Today", () => { const t = todayStr(); setAllDateFrom(t); setAllDateTo(t); }],
                    ["Yesterday", () => { const y = (() => { const d = new Date(Date.now()-86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })(); setAllDateFrom(y); setAllDateTo(y); }],
                    ["Last 7d", () => { setAllDateFrom((() => { const d = new Date(Date.now()-7*86400000); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; })()); setAllDateTo(todayStr()); }],
                    ["All", () => { setAllDateFrom(""); setAllDateTo(""); }]
                  ].map(([l, fn]) => (
                    <button key={l} onClick={fn} style={{ padding: "6px 10px", borderRadius: 8, border: `1px solid ${COLORS.border}`, background: COLORS.surface, color: COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
            </div>
            {/* Row 3: status + referBy + rejoiner */}
            <div style={{ display: "flex", gap: 16, flexWrap: "wrap" }}>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>STATUS</div>
                <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
                  {[["all","All",COLORS.muted],["notStarted","Not Started",COLORS.muted],["aptFailed","Apt Failed",COLORS.danger],["typingFailed","Typing Failed",COLORS.warning],["cleared","Cleared",COLORS.success],["approved","✅ Approved",COLORS.success],["rejected","❌ Rejected",COLORS.danger]].map(([v,l,c]) => (
                    <button key={v} onClick={() => setAllStatusFilter(v)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${allStatusFilter === v ? c : COLORS.border}`, background: allStatusFilter === v ? c + "22" : "transparent", color: allStatusFilter === v ? c : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600, whiteSpace: "nowrap" }}>{l}</button>
                  ))}
                </div>
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>REFERRED BY</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All"],["walkin","Walk-in"],["website","Website"],["referral","Referral"]].map(([v,l]) => (
                    <button key={v} onClick={() => setAllReferBy(v)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${allReferBy === v ? COLORS.accent : COLORS.border}`, background: allReferBy === v ? "rgba(233,69,96,0.15)" : "transparent", color: allReferBy === v ? COLORS.accent : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
              <div>
                <div style={{ fontSize: 10, color: COLORS.muted, fontWeight: 700, letterSpacing: 0.5, marginBottom: 6 }}>TYPE</div>
                <div style={{ display: "flex", gap: 5 }}>
                  {[["all","All"],["No","Fresh"],["Yes","Rejoiner"]].map(([v,l]) => (
                    <button key={v} onClick={() => setAllRejoiner(v)} style={{ padding: "5px 11px", borderRadius: 20, border: `1px solid ${allRejoiner === v ? COLORS.gold : COLORS.border}`, background: allRejoiner === v ? "rgba(245,166,35,0.15)" : "transparent", color: allRejoiner === v ? COLORS.gold : COLORS.muted, cursor: "pointer", fontSize: 11, fontWeight: 600 }}>{l}</button>
                  ))}
                </div>
              </div>
            </div>
          </div>

          {allFiltered.length === 0 ? (
            <div style={{ textAlign: "center", padding: "40px 0", color: COLORS.muted }}>
              <div style={{ fontSize: 40, marginBottom: 10 }}>👤</div>
              <p>No candidates registered yet.</p>
            </div>
          ) : allFiltered.map(c => {
            const ts = testStatusLabel(c);
            const credVisible = showCred[c.id];
            return (
              <div key={c.id} style={{ background: COLORS.card, borderRadius: 12, padding: "16px 18px", marginBottom: 10, border: `1px solid ${COLORS.border}` }}>
                {/* Top row */}
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 10 }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 12 }}>
                    {/* Photo avatar */}
                    {c.photoData ? (
                      <img src={c.photoData} alt={c.name} style={{ width: 44, height: 44, borderRadius: "50%", objectFit: "cover", border: `2px solid ${COLORS.border}`, flexShrink: 0 }} />
                    ) : (
                      <div style={{ width: 44, height: 44, borderRadius: "50%", background: COLORS.card, border: `2px solid ${COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 18, flexShrink: 0 }}>👤</div>
                    )}
                    <div>
                      <div style={{ fontWeight: 600, fontSize: 15 }}>{c.name}</div>
                      <div style={{ fontSize: 13, color: COLORS.muted, marginTop: 3 }}>📱 {c.mobile} · {c.referBy} · {c.isRejoiner === "Yes" ? "Rejoiner ↩" : "Fresh"}</div>
                    </div>
                  </div>
                  <div style={{ display: "inline-flex", alignItems: "center", gap: 4, background: ts.color + "22", color: ts.color, borderRadius: 20, padding: "3px 10px", fontSize: 12, fontWeight: 600 }}>{ts.label}</div>
                </div>

                {/* Details grid */}
                <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(110px, 1fr))", gap: 6, marginBottom: 10 }}>
                  {[["PAN", c.pan], ["Aadhaar", c.aadhaar.slice(0,4) + " •••• " + c.aadhaar.slice(-4)], ["Aptitude", c.aptScore != null ? `${c.aptScore}/15` : "Not taken"], ["Typing Speed", c.typingScore ? `${c.typingScore.wpm} WPM` : "Not taken"], ["Typing Acc.", c.typingScore ? `${c.typingScore.accuracy}%` : "—"], ["Refer By", c.referBy + (c.empId ? ` (${c.empId})` : "")]].map(([k, v]) => (
                    <div key={k} style={{ background: COLORS.surface, borderRadius: 8, padding: "7px 10px" }}>
                      <div style={{ fontSize: 10, color: COLORS.muted, marginBottom: 2 }}>{k}</div>
                      <div style={{ fontSize: 13, fontWeight: 500, wordBreak: "break-all" }}>{v}</div>
                    </div>
                  ))}
                </div>

                {/* Resume row */}
                <div style={{ background: COLORS.surface, borderRadius: 10, padding: "10px 14px", display: "flex", alignItems: "center", justifyContent: "space-between", border: `1px solid ${COLORS.border}`, marginBottom: 8 }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                    <span style={{ fontSize: 20 }}>📄</span>
                    <div>
                      <div style={{ fontSize: 10, color: COLORS.muted }}>RESUME</div>
                      <div style={{ fontSize: 13, fontWeight: 500 }}>{c.resume || "Not uploaded"}</div>
                    </div>
                  </div>
                  {c.resumeData ? (
                    <div style={{ display: "flex", gap: 6 }}>
                      <button onClick={() => {
                        if (c.resume?.endsWith(".pdf")) {
                          window.open(c.resumeData, "_blank");
                        } else {
                          const blob = new Blob([atob(c.resumeData.split(",")[1])], { type: "application/octet-stream" });
                          window.open(URL.createObjectURL(blob), "_blank");
                        }
                      }} style={{ background: "rgba(52,152,219,0.15)", border: `1px solid rgba(52,152,219,0.4)`, borderRadius: 7, padding: "5px 12px", color: "#3498db", cursor: "pointer", fontSize: 12, fontWeight: 600 }}>
                        👁 View
                      </button>
                      <a href={c.resumeData} download={c.resume} style={{ background: "rgba(46,204,113,0.15)", border: `1px solid rgba(46,204,113,0.4)`, borderRadius: 7, padding: "5px 12px", color: COLORS.success, cursor: "pointer", fontSize: 12, fontWeight: 600, textDecoration: "none", display: "inline-flex", alignItems: "center" }}>
                        ⬇ Download
                      </a>
                    </div>
                  ) : (
                    <span style={{ fontSize: 12, color: COLORS.muted }}>No file</span>
                  )}
                </div>

                {/* Credentials row — username only for panelist (password hidden) */}
                <div style={{ background: COLORS.surface, borderRadius: 10, padding: "10px 14px", display: "flex", alignItems: "center", justifyContent: "space-between", border: `1px solid ${COLORS.border}` }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                    <div>
                      <div style={{ fontSize: 10, color: COLORS.muted }}>USERNAME</div>
                      <div style={{ fontSize: 14, fontWeight: 700, color: COLORS.gold, letterSpacing: 1 }}>{c.username}</div>
                    </div>
                    <div style={{ width: 1, height: 30, background: COLORS.border, margin: "0 4px" }} />
                    <div>
                      <div style={{ fontSize: 10, color: COLORS.muted }}>PASSWORD</div>
                      <div style={{ fontSize: 14, fontWeight: 700, color: COLORS.muted, letterSpacing: 2 }}>••••••••</div>
                    </div>
                  </div>
                  <div style={{ background: "rgba(136,146,164,0.1)", borderRadius: 7, padding: "4px 10px", fontSize: 11, color: COLORS.muted, border: `1px solid ${COLORS.border}` }}>
                    🔒 Hidden
                  </div>
                </div>

                {/* Panel status if in final round */}
                {c.aptScore >= 10 && c.typingScore?.passed && (
                  <div style={{ marginTop: 8, display: "flex", alignItems: "center", gap: 8 }}>
                    <span style={{ fontSize: 12, color: COLORS.muted }}>Panel:</span>
                    <span style={s.badge(c.panelStatus)}>{c.panelStatus === "pending" ? "⏳ Pending" : c.panelStatus === "approved" ? "✅ Approved" : "❌ Rejected"}</span>
                    {c.panelRemark && <span style={{ fontSize: 12, color: COLORS.muted }}>— {c.panelRemark}</span>}
                  </div>
                )}

                {/* Timestamps */}
                <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(140px, 1fr))", gap: 6, marginTop: 10, borderTop: `1px solid ${COLORS.border}`, paddingTop: 10 }}>
                  {[["📝 Registered", c.registeredAt], ["🧠 Aptitude Done", c.aptCompletedAt], ["⌨️ Typing Done", c.typingCompletedAt], ["⚖️ Panel Decision", c.panelDecidedAt]].map(([label, ts]) => (
                    <div key={label} style={{ background: COLORS.surface, borderRadius: 8, padding: "6px 8px" }}>
                      <div style={{ fontSize: 10, color: COLORS.muted, marginBottom: 2 }}>{label}</div>
                      <div style={{ fontSize: 11, fontWeight: 500, color: ts ? COLORS.text : COLORS.muted }}>{fmtTs(ts)}</div>
                    </div>
                  ))}
                </div>
              </div>
            );
          })}
        </div>
      )}

      {/* ── Unique People Tab ── */}
      {activeTab === "people" && (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
            <div>
              <h2 style={{ ...s.h2, margin: 0 }}>👥 Unique People</h2>
              <p style={{ fontSize: 12, color: COLORS.muted, margin: "4px 0 0" }}>One row per unique PAN — shows latest status with full history count</p>
            </div>
            <div style={{ display: "flex", gap: 8, alignItems: "center" }}>
              <span style={{ fontSize: 13, color: COLORS.muted }}>{uniquePeople.filter(p => !peopleSearch || p.name.toLowerCase().includes(peopleSearch.toLowerCase()) || p.pan?.toLowerCase().includes(peopleSearch.toLowerCase()) || p.mobile.includes(peopleSearch)).length} / {uniquePeople.length}</span>
              <DownloadBtn rows={uniquePeople} filename={`recruitpro-unique-people-${todayStr()}.csv`} panelists={panelists} label="Download" />
            </div>
          </div>
          <input
            style={{ ...s.input, marginBottom: 14, fontSize: 13 }}
            placeholder="🔍 Search by name, PAN or mobile..."
            value={peopleSearch}
            onChange={e => setPeopleSearch(e.target.value)}
          />
          {uniquePeople
            .filter(p => !peopleSearch || p.name.toLowerCase().includes(peopleSearch.toLowerCase()) || p.pan?.toLowerCase().includes(peopleSearch.toLowerCase()) || p.mobile.includes(peopleSearch))
            .sort((a, b) => new Date(b.registeredAt) - new Date(a.registeredAt))
            .map(person => {
              const todayApps = person._allApps.filter(a => localDateOf(a.registeredAt) === todayStr());
              const hasSameDayAlarm = todayApps.length > 1;
              return (
                <div key={person.username} style={{ background: COLORS.card, borderRadius: 12, padding: "14px 16px", marginBottom: 10, border: `1px solid ${hasSameDayAlarm ? "rgba(231,76,60,0.4)" : COLORS.border}` }}>
                  <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", gap: 10 }}>
                    <div style={{ display: "flex", alignItems: "center", gap: 10, flex: 1 }}>
                      {person.photoData
                        ? <img src={person.photoData} alt="" style={{ width: 40, height: 40, borderRadius: "50%", objectFit: "cover", border: `2px solid ${COLORS.border}`, flexShrink: 0 }} />
                        : <div style={{ width: 40, height: 40, borderRadius: "50%", background: COLORS.surface, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 18, flexShrink: 0 }}>👤</div>}
                      <div>
                        <div style={{ fontWeight: 700, fontSize: 14, color: COLORS.text }}>
                          {person.name}
                          {hasSameDayAlarm && <span style={{ marginLeft: 8, fontSize: 11, color: COLORS.danger, fontWeight: 700 }}>🚨 {todayApps.length}x today</span>}
                        </div>
                        <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 2 }}>
                          🪪 <span style={{ fontFamily: "monospace", color: COLORS.gold }}>{person.pan}</span> · 📱 {person.mobile} · 🎂 {person.dob ? new Date(person.dob).toLocaleDateString("en-IN",{day:"2-digit",month:"short",year:"numeric"}) : "—"}
                        </div>
                        <div style={{ fontSize: 11, color: COLORS.muted, marginTop: 2 }}>
                          {person.referBy}{person.empId ? ` (${person.empId})` : ""} · Last applied: {fmtTs(person.registeredAt)}
                        </div>
                      </div>
                    </div>
                    <div style={{ textAlign: "right", flexShrink: 0 }}>
                      <span style={s.badge(person.panelStatus)}>{person.panelStatus}</span>
                      <div style={{ fontSize: 11, color: COLORS.muted, marginTop: 4 }}>
                        {person._appCount} application{person._appCount !== 1 ? "s" : ""}
                      </div>
                    </div>
                  </div>
                  {/* Mini history strip */}
                  {person._appCount > 1 && (
                    <div style={{ marginTop: 10, display: "flex", gap: 5, flexWrap: "wrap" }}>
                      {person._allApps.sort((a,b) => new Date(a.registeredAt) - new Date(b.registeredAt)).map((app, i) => (
                        <div key={app.id} style={{ background: COLORS.surface, borderRadius: 6, padding: "4px 8px", fontSize: 10, border: `1px solid ${COLORS.border}`, display: "flex", gap: 4, alignItems: "center" }}>
                          <span style={{ color: COLORS.muted }}>#{i+1}</span>
                          <span style={{ color: COLORS.text }}>{localDateOf(app.registeredAt)}</span>
                          <span style={s.badge(app.panelStatus)}>{app.panelStatus}</span>
                        </div>
                      ))}
                    </div>
                  )}
                </div>
              );
            })}
        </div>
      )}

      {/* ── Log Tab ── */}
      {activeTab === "log" && (
        <div style={{ background: COLORS.surface, borderRadius: 16, border: `1px solid ${COLORS.border}`, padding: 24 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
            <div>
              <h2 style={{ ...s.h2, margin: 0 }}>📋 Candidate Log</h2>
              <p style={{ fontSize: 12, color: COLORS.muted, margin: "4px 0 0" }}>Grouped by PAN (User ID) · full timeline per person</p>
            </div>
            <span style={{ fontSize: 12, color: COLORS.muted }}>{uniquePeople.length} unique people · {candidates.length} total applications</span>
          </div>
          {[...uniquePeople].sort((a,b) => new Date(b.registeredAt) - new Date(a.registeredAt)).map(person => {
            const history = person._allApps.sort((a,b) => new Date(a.registeredAt) - new Date(b.registeredAt));
            const todayApps = history.filter(a => localDateOf(a.registeredAt) === todayStr());
            const hasSameDayAlarm = todayApps.length > 1;
            // Build events
            const events = history.flatMap(app => {
              const evs = [];
              evs.push({ ts: app.registeredAt, icon:"📝", text: `Registered (Application #${history.indexOf(app)+1}) — ref: ${app.referBy}${app.empId?` (${app.empId})`:""}`, color: COLORS.text });
              if (app.aptCompletedAt) evs.push({ ts: app.aptCompletedAt, icon:"🧠", text:`Aptitude: ${app.aptScore}/15 ${app.aptScore>=10?"✓":"✗"}`, color: app.aptScore>=10?COLORS.success:COLORS.danger });
              if (app.typingCompletedAt) evs.push({ ts: app.typingCompletedAt, icon:"⌨️", text:`Typing: ${app.typingScore?.wpm}wpm / ${app.typingScore?.accuracy}% ${app.typingScore?.passed?"✓":"✗"}`, color: app.typingScore?.passed?COLORS.success:COLORS.danger });
              if (app.panelDecidedAt) evs.push({ ts: app.panelDecidedAt, icon: app.panelStatus==="approved"?"✅":app.panelStatus==="rejected"?"❌":"⏳", text:`Panel: ${app.panelStatus}${app.panelRemark?` — "${app.panelRemark}"`:""}`, color: app.panelStatus==="approved"?COLORS.success:app.panelStatus==="rejected"?COLORS.danger:COLORS.warning });
              return evs;
            }).sort((a,b) => new Date(a.ts) - new Date(b.ts));

            return (
              <div key={person.username} style={{ marginBottom: 20, background: COLORS.card, borderRadius: 14, border: `1px solid ${hasSameDayAlarm ? "rgba(231,76,60,0.4)" : COLORS.border}`, overflow: "hidden" }}>
                {/* Person header */}
                <div style={{ background: "rgba(99,102,241,0.07)", padding: "12px 16px", borderBottom: `1px solid ${COLORS.border}`, display: "flex", justifyContent: "space-between", alignItems: "center", flexWrap: "wrap", gap: 8 }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                    {person.photoData ? <img src={person.photoData} alt="" style={{ width: 34, height: 34, borderRadius: "50%", objectFit: "cover", border: `2px solid rgba(99,102,241,0.4)`, flexShrink: 0 }} /> : <div style={{ width: 34, height: 34, borderRadius: "50%", background: "rgba(99,102,241,0.15)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 14, flexShrink: 0 }}>👤</div>}
                    <div>
                      <div style={{ fontWeight: 700, fontSize: 14, color: COLORS.text }}>{person.name}
                        {hasSameDayAlarm && <span style={{ marginLeft: 8, fontSize: 11, color: COLORS.danger }}>🚨 {todayApps.length}x today</span>}
                      </div>
                      <div style={{ fontSize: 11, color: COLORS.muted }}>🪪 <span style={{ fontFamily:"monospace",color:COLORS.gold }}>{person.pan}</span> · 📱 {person.mobile}</div>
                    </div>
                  </div>
                  <div style={{ display: "flex", gap: 8, alignItems: "center" }}>
                    <span style={{ fontSize: 11, color: COLORS.muted }}>{person._appCount} application{person._appCount!==1?"s":""}</span>
                    <span style={s.badge(person.panelStatus)}>{person.panelStatus}</span>
                  </div>
                </div>
                {/* Timeline */}
                <div style={{ padding: "12px 16px" }}>
                  {events.map((ev, i) => (
                    <div key={i} style={{ display: "flex", gap: 10, paddingBottom: i < events.length-1 ? 10 : 0, borderLeft: i < events.length-1 ? `2px solid rgba(99,102,241,0.2)` : "2px solid transparent", marginLeft: 11, paddingLeft: 16, position: "relative" }}>
                      <div style={{ position: "absolute", left: -10, width: 20, height: 20, borderRadius: "50%", background: COLORS.surface, border: `1px solid ${COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 10 }}>{ev.icon}</div>
                      <div style={{ flex: 1 }}>
                        <div style={{ fontSize: 12, color: ev.color, fontWeight: 500 }}>{ev.text}</div>
                        <div style={{ fontSize: 10, color: COLORS.muted }}>{fmtTs(ev.ts)}</div>
                      </div>
                    </div>
                  ))}
                </div>
                {/* PAN footer */}
                <div style={{ padding: "8px 16px", borderTop: `1px solid ${COLORS.border}`, display: "flex", gap: 6, flexWrap: "wrap", background: "rgba(0,0,0,0.1)" }}>
                  <span style={{ fontSize: 10, color: COLORS.muted }}>User IDs:</span>
                  {history.map((app, i) => (
                    <span key={i} style={{ fontFamily:"monospace", fontSize:10, color:COLORS.gold, background:"rgba(245,166,35,0.1)", borderRadius:4, padding:"1px 6px", border:`1px solid rgba(245,166,35,0.2)` }}>
                      {app.username} ({localDateOf(app.registeredAt)})
                    </span>
                  ))}
                </div>
              </div>
            );
          })}
        </div>
      )}

      {/* ── On Break modal ── */}
      {showBreakModal && (() => {
        const pendingQueue = candidates.filter(c => c.assignedPanelistId === currentPanelist?.id && c.panelStatus === "pending");
        const otherActive = panelists.filter(p => !p.disabled && !p.onBreak && p.id !== currentPanelist?.id);
        return (
          <div style={{ position: "fixed", inset: 0, background: "rgba(0,0,0,0.75)", display: "flex", alignItems: "center", justifyContent: "center", zIndex: 200, padding: 20 }}>
            <div style={{ background: COLORS.surface, borderRadius: 16, padding: 24, width: "100%", maxWidth: 460, border: `1px solid ${COLORS.border}` }}>
              <div style={{ textAlign: "center", marginBottom: 16 }}>
                <div style={{ fontSize: 40, marginBottom: 8 }}>☕</div>
                <h2 style={{ ...s.h2, margin: 0 }}>Going on Break</h2>
                <p style={{ fontSize: 13, color: COLORS.muted, margin: "8px 0 0" }}>No new candidates will be assigned to you while on break.</p>
              </div>

              {pendingQueue.length > 0 ? (
                <>
                  <div style={{ background: "rgba(243,156,18,0.1)", border: `1px solid rgba(243,156,18,0.3)`, borderRadius: 10, padding: "12px 14px", marginBottom: 16 }}>
                    <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.warning, marginBottom: 4 }}>
                      ⚠️ You have {pendingQueue.length} pending candidate{pendingQueue.length > 1 ? "s" : ""} in your queue
                    </div>
                    <div style={{ fontSize: 12, color: COLORS.muted }}>You can transfer them to another panelist or keep them and complete after your break.</div>
                  </div>

                  {otherActive.length > 0 && (
                    <div style={{ marginBottom: 16 }}>
                      <div style={{ fontSize: 12, fontWeight: 700, color: COLORS.text, marginBottom: 8 }}>Transfer all pending to:</div>
                      <div style={{ display: "flex", flexDirection: "column", gap: 6 }}>
                        {otherActive.map(p => {
                          const theirPending = candidates.filter(c => c.assignedPanelistId === p.id && c.panelStatus === "pending").length;
                          return (
                            <div key={p.id} onClick={() => setBulkTransferTarget(bulkTransferTarget === p.id ? "" : p.id)} style={{ display: "flex", justifyContent: "space-between", alignItems: "center", background: bulkTransferTarget === p.id ? "rgba(52,152,219,0.15)" : COLORS.card, border: `1px solid ${bulkTransferTarget === p.id ? "rgba(52,152,219,0.5)" : COLORS.border}`, borderRadius: 8, padding: "10px 12px", cursor: "pointer" }}>
                              <div>
                                <div style={{ fontSize: 13, fontWeight: 600, color: COLORS.text }}>{p.name || p.username}</div>
                                <div style={{ fontSize: 11, color: COLORS.muted }}>{theirPending} pending in queue</div>
                              </div>
                              {bulkTransferTarget === p.id && <span style={{ color: "#3498db", fontWeight: 700, fontSize: 13 }}>✓ Selected</span>}
                            </div>
                          );
                        })}
                      </div>
                    </div>
                  )}

                  <div style={{ display: "flex", flexDirection: "column", gap: 8 }}>
                    {bulkTransferTarget && (
                      <button onClick={() => confirmBreak(true)} style={{ ...s.btn, marginTop: 0, background: "#3498db" }}>
                        ☕ Go on Break & Transfer {pendingQueue.length} Candidate{pendingQueue.length > 1 ? "s" : ""}
                      </button>
                    )}
                    <button onClick={() => confirmBreak(false)} style={{ ...s.btnOut, marginTop: 0 }}>
                      ☕ Go on Break (Keep Candidates — Complete After Break)
                    </button>
                    <button onClick={() => { setShowBreakModal(false); setBulkTransferTarget(""); }} style={{ background: "none", border: "none", color: COLORS.muted, cursor: "pointer", fontSize: 13, padding: "6px 0" }}>
                      Cancel
                    </button>
                  </div>
                </>
              ) : (
                <>
                  <div style={{ ...s.alert("success"), textAlign: "center" }}>
                    ✅ Your queue is empty — no pending candidates to worry about.
                  </div>
                  <div style={{ display: "flex", gap: 10 }}>
                    <button onClick={() => { setShowBreakModal(false); setBulkTransferTarget(""); }} style={{ ...s.btnOut, marginTop: 0, flex: 1 }}>Cancel</button>
                    <button onClick={() => confirmBreak(false)} style={{ ...s.btn, marginTop: 0, flex: 1 }}>☕ Go on Break</button>
                  </div>
                </>
              )}
            </div>
          </div>
        );
      })()}

      {/* Candidate detail modal */}
      {selected && (
        <div
          style={{ position: "fixed", inset: 0, background: "rgba(0,0,0,0.75)", display: "flex", alignItems: "flex-start", justifyContent: "center", zIndex: 100, padding: "20px 16px", overflowY: "auto" }}
          onClick={e => { if (e.target === e.currentTarget) { setSelected(null); setResumeTab("insights"); } }}
        >
          <div className="rp-modal-inner" style={{ background: COLORS.surface, borderRadius: 16, padding: "20px 16px", width: "100%", maxWidth: 640, border: `1px solid ${COLORS.border}`, position: "relative", margin: "auto" }}>
            {/* ✕ Top-right close button */}
            <button
              onClick={() => { setSelected(null); setResumeTab("insights"); }}
              style={{ position: "absolute", top: 14, right: 14, width: 30, height: 30, borderRadius: "50%", background: COLORS.card, border: `1px solid ${COLORS.border}`, color: COLORS.muted, cursor: "pointer", fontSize: 16, display: "flex", alignItems: "center", justifyContent: "center", lineHeight: 1, zIndex: 10 }}
            >✕</button>

            {/* ── Same-day repeat alarm ── */}
            {modalAlarm && (
              <div style={{ background: "rgba(231,76,60,0.1)", border: `1px solid rgba(231,76,60,0.45)`, borderRadius: 12, padding: "12px 14px", marginBottom: 16 }}>
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", gap: 10 }}>
                  <div>
                    <div style={{ fontSize: 13, fontWeight: 700, color: COLORS.danger, marginBottom: 4 }}>
                      🚨 Same-Day Repeat — {modalAlarm.length} applications today
                    </div>
                    <div style={{ fontSize: 12, color: COLORS.muted, marginBottom: 8 }}>
                      This candidate (PAN: <strong style={{ color: COLORS.text }}>{selected.pan}</strong>) has registered <strong style={{ color: COLORS.danger }}>{modalAlarm.length} times today</strong>.
                    </div>
                    <div style={{ display: "flex", flexDirection: "column", gap: 4 }}>
                      {modalAlarm.map((a, i) => (
                        <div key={i} style={{ fontSize: 11, color: COLORS.muted, display: "flex", gap: 8 }}>
                          <span style={{ color: a.id === selected.id ? COLORS.accent : COLORS.muted, fontWeight: a.id === selected.id ? 700 : 400 }}>
                            {i + 1}. {fmtTs(a.registeredAt)} {a.id === selected.id ? "← current" : ""}
                          </span>
                          <span style={s.badge(a.panelStatus)}>{a.panelStatus}</span>
                        </div>
                      ))}
                    </div>
                  </div>
                  <button onClick={() => setModalAlarm(null)} style={{ background: "none", border: "none", color: COLORS.muted, cursor: "pointer", fontSize: 16, flexShrink: 0 }}>✕</button>
                </div>
              </div>
            )}

            <div style={{ display: "flex", alignItems: "center", gap: 14, marginBottom: 16 }}>
              {selected.photoData ? (
                <img src={selected.photoData} alt={selected.name} style={{ width: 64, height: 64, borderRadius: "50%", objectFit: "cover", border: `3px solid ${COLORS.accent}`, flexShrink: 0 }} />
              ) : (
                <div style={{ width: 64, height: 64, borderRadius: "50%", background: COLORS.card, border: `2px solid ${COLORS.border}`, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 28 }}>👤</div>
              )}
              <div>
                <h2 style={{ ...s.h2, margin: 0 }}>{selected.name}</h2>
                <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 3 }}>{selected.mobile} · {selected.email || ""}</div>
                {/* Application count badge */}
                {(() => {
                  const key = selected.username?.toUpperCase();
                  const count = (allByUsername[key] || []).length;
                  return count > 1 ? (
                    <div style={{ display: "inline-flex", alignItems: "center", gap: 5, marginTop: 4, background: "rgba(99,102,241,0.12)", border: "1px solid rgba(99,102,241,0.3)", borderRadius: 20, padding: "2px 10px", fontSize: 11, color: "#818cf8", fontWeight: 600 }}>
                      📋 {count} applications on record
                    </div>
                  ) : null;
                })()}
                {selected.transferredFrom && (() => {
                  const fromPanelist = panelists.find(p => p.id === selected.transferredFrom);
                  return (
                    <div style={{ display: "inline-flex", alignItems: "center", gap: 5, marginTop: 4, marginLeft: 4, background: "rgba(52,152,219,0.1)", border: "1px solid rgba(52,152,219,0.3)", borderRadius: 20, padding: "2px 10px", fontSize: 11, color: "#3498db", fontWeight: 600 }}>
                      ↗ Transferred from {fromPanelist?.name || fromPanelist?.username || "another panelist"} · {fmtTs(selected.transferredAt)}
                    </div>
                  );
                })()}
              </div>
            </div>
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(130px, 1fr))", gap: 8, marginBottom: 16 }}>
              {[["Mobile", selected.mobile], ["DOB", selected.dob ? new Date(selected.dob).toLocaleDateString("en-IN",{day:"2-digit",month:"short",year:"numeric"}) : "—"], ["Gender", selected.gender||"—"], ["Graduation", selected.graduationDone||"—"], ["Interview Location", selected.interviewLocation||"—"], ["Referred By", selected.referBy + (selected.empId ? ` (${selected.empId})` : "")], ["Rejoiner", selected.isRejoiner], ["PAN (User ID)", selected.pan], ["Aptitude", `${selected.aptScore}/15`], ["Typing", `${selected.typingScore?.wpm} WPM · ${selected.typingScore?.accuracy}%`]].map(([k, v]) => (
                <div key={k} style={{ background: COLORS.card, borderRadius: 8, padding: "8px 12px" }}>
                  <div style={{ fontSize: 11, color: COLORS.muted }}>{k}</div>
                  <div style={{ fontSize: 13, fontWeight: 600, color: k === "PAN (User ID)" ? COLORS.gold : COLORS.text }}>{v}</div>
                </div>
              ))}
            </div>
            {/* Address */}
            {(selected.addr1 || selected.city) && (
              <div style={{ background: COLORS.card, borderRadius: 10, padding: "10px 14px", marginBottom: 14, border: `1px solid ${COLORS.border}` }}>
                <div style={{ fontSize: 11, color: COLORS.muted, marginBottom: 4 }}>🏠 ADDRESS</div>
                <div style={{ fontSize: 13, color: COLORS.text, lineHeight: 1.6 }}>
                  {[selected.addr1, selected.addr2, selected.landmark].filter(Boolean).join(", ")}
                  {(selected.city || selected.state || selected.pincode) && (
                    <div style={{ color: COLORS.muted, marginTop: 2 }}>{[selected.city, selected.state, selected.pincode].filter(Boolean).join(" · ")}</div>
                  )}
                </div>
              </div>
            )}

            {/* ── Application History ── */}
            {(() => {
              const key = selected.username?.toUpperCase();
              const history = (allByUsername[key] || []).sort((a, b) => new Date(b.registeredAt) - new Date(a.registeredAt));
              if (history.length <= 1) return null;
              return (
                <div style={{ background: "rgba(99,102,241,0.06)", border: `1px solid rgba(99,102,241,0.2)`, borderRadius: 12, padding: "14px 16px", marginBottom: 16 }}>
                  <div style={{ fontSize: 12, fontWeight: 700, color: "#818cf8", marginBottom: 10 }}>📋 Application History ({history.length} total)</div>
                  <div style={{ display: "flex", flexDirection: "column", gap: 6 }}>
                    {history.map((app, i) => (
                      <div key={app.id} style={{ display: "flex", justifyContent: "space-between", alignItems: "center", background: app.id === selected.id ? "rgba(99,102,241,0.1)" : COLORS.card, borderRadius: 8, padding: "8px 12px", border: app.id === selected.id ? `1px solid rgba(99,102,241,0.35)` : `1px solid ${COLORS.border}` }}>
                        <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
                          <span style={{ fontSize: 11, fontWeight: 700, color: app.id === selected.id ? "#818cf8" : COLORS.muted, minWidth: 18 }}>#{history.length - i}</span>
                          <div>
                            <div style={{ fontSize: 12, color: COLORS.text }}>{fmtTs(app.registeredAt)}</div>
                            <div style={{ fontSize: 11, color: COLORS.muted }}>{app.referBy}{app.empId ? ` · ${app.empId}` : ""}</div>
                          </div>
                        </div>
                        <div style={{ display: "flex", gap: 6, alignItems: "center" }}>
                          {app.aptScore != null && <span style={{ fontSize: 11, color: app.aptScore >= 10 ? COLORS.success : COLORS.danger }}>{app.aptScore}/15</span>}
                          {app.typingScore && <span style={{ fontSize: 11, color: app.typingScore.passed ? COLORS.success : COLORS.danger }}>{app.typingScore.wpm}wpm</span>}
                          <span style={s.badge(app.panelStatus)}>{app.panelStatus}</span>
                          {app.id === selected.id && <span style={{ fontSize: 10, color: "#818cf8", fontWeight: 700 }}>CURRENT</span>}
                        </div>
                      </div>
                    ))}
                  </div>
                </div>
              );
            })()}

            {/* Resume in modal */}
            <div style={{ background: COLORS.card, borderRadius: 10, padding: "12px 14px", display: "flex", alignItems: "center", justifyContent: "space-between", marginBottom: 16, border: `1px solid ${COLORS.border}` }}>
              <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                <span style={{ fontSize: 22 }}>📄</span>
                <div>
                  <div style={{ fontSize: 11, color: COLORS.muted }}>RESUME</div>
                  <div style={{ fontSize: 13, fontWeight: 600 }}>{selected.resume || "Not uploaded"}</div>
                </div>
              </div>
              {selected.resumeData ? (
                <div style={{ display: "flex", gap: 6 }}>
                  <button onClick={() => {
                    if (selected.resume?.endsWith(".pdf")) {
                      window.open(selected.resumeData, "_blank");
                    } else {
                      const blob = new Blob([atob(selected.resumeData.split(",")[1])], { type: "application/octet-stream" });
                      window.open(URL.createObjectURL(blob), "_blank");
                    }
                  }} style={{ background: "rgba(52,152,219,0.15)", border: `1px solid rgba(52,152,219,0.4)`, borderRadius: 7, padding: "6px 14px", color: "#3498db", cursor: "pointer", fontSize: 13, fontWeight: 600 }}>
                    👁 View
                  </button>
                  <a href={selected.resumeData} download={selected.resume} style={{ background: "rgba(46,204,113,0.15)", border: `1px solid rgba(46,204,113,0.4)`, borderRadius: 7, padding: "6px 14px", color: COLORS.success, fontSize: 13, fontWeight: 600, textDecoration: "none", display: "inline-flex", alignItems: "center" }}>
                    ⬇ Download
                  </a>
                </div>
              ) : <span style={{ fontSize: 12, color: COLORS.muted }}>No file uploaded</span>}
            </div>
            {/* ── AI Insights Panel ── */}
            <div style={{ background: "rgba(99,102,241,0.06)", border: `1px solid rgba(99,102,241,0.25)`, borderRadius: 14, padding: 16, marginBottom: 16 }}>
              <div style={{ display: "flex", alignItems: "center", justifyContent: "space-between", marginBottom: 12 }}>
                <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
                  <span style={{ fontSize: 16 }}>🤖</span>
                  <span style={{ fontSize: 13, fontWeight: 700, color: "#818cf8" }}>AI Insights</span>
                  {aiSummary?.resumeRead && (
                    <span style={{ background: "rgba(46,204,113,0.15)", border: `1px solid rgba(46,204,113,0.3)`, borderRadius: 20, padding: "2px 8px", fontSize: 10, fontWeight: 700, color: COLORS.success }}>📄 Resume Read</span>
                  )}
                  {aiSummary && !aiSummary.resumeRead && !aiSummary.error && (
                    <span style={{ background: "rgba(243,156,18,0.12)", border: `1px solid rgba(243,156,18,0.3)`, borderRadius: 20, padding: "2px 8px", fontSize: 10, fontWeight: 600, color: COLORS.warning }}>Profile Only</span>
                  )}
                </div>
                {!aiLoading && (
                  <button onClick={() => { setAiSummary(null); fetchAiInsights(selected); }} style={{ background: "none", border: `1px solid rgba(99,102,241,0.3)`, borderRadius: 6, padding: "3px 10px", color: "#818cf8", cursor: "pointer", fontSize: 11 }}>↺ Refresh</button>
                )}
              </div>

              {aiLoading && (
                <div style={{ display: "flex", alignItems: "center", gap: 10, padding: "10px 0" }}>
                  <div style={{ width: 18, height: 18, border: "2px solid #818cf8", borderTop: "2px solid transparent", borderRadius: "50%", animation: "spin 0.8s linear infinite" }} />
                  <span style={{ fontSize: 13, color: "#818cf8" }}>
                    {selected?.resumeData && selected?.resume?.toLowerCase().endsWith(".pdf") ? "Reading resume & analysing candidate…" : "Analysing candidate profile…"}
                  </span>
                </div>
              )}

              {aiSummary && !aiSummary.error && !aiLoading && (
                <div>
                  {/* Sub-tabs: Insights | Resume Summary */}
                  <div style={{ display: "flex", gap: 4, marginBottom: 14, background: COLORS.card, borderRadius: 8, padding: 3 }}>
                    {[["insights", "📊 Insights"], ["resume", "📄 Resume Summary"]].map(([v, l]) => (
                      <button key={v} onClick={() => setResumeTab(v)} style={{ flex: 1, padding: "7px 10px", borderRadius: 6, border: "none", background: resumeTab === v ? COLORS.surface : "transparent", color: resumeTab === v ? "#818cf8" : COLORS.muted, cursor: "pointer", fontSize: 12, fontWeight: 600 }}>{l}</button>
                    ))}
                  </div>

                  {/* ── Insights sub-tab ── */}
                  {resumeTab === "insights" && (
                    <div>
                      {/* Summary */}
                      <div style={{ fontSize: 13, color: COLORS.text, lineHeight: 1.6, marginBottom: 12, fontStyle: "italic", padding: "10px 12px", background: COLORS.card, borderRadius: 10 }}>"{aiSummary.summary}"</div>

                      {/* Smart Score */}
                      <div style={{ background: COLORS.card, borderRadius: 10, padding: "12px 14px", marginBottom: 12 }}>
                        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 8 }}>
                          <span style={{ fontSize: 12, color: COLORS.muted, fontWeight: 700 }}>SMART SCORE</span>
                          <span style={{ fontSize: 22, fontWeight: 800, color: aiSummary.score >= 70 ? COLORS.success : aiSummary.score >= 50 ? COLORS.warning : COLORS.danger }}>{aiSummary.score}<span style={{ fontSize: 13, color: COLORS.muted }}>/100</span></span>
                        </div>
                        <div style={{ background: COLORS.border, borderRadius: 20, height: 6, marginBottom: 8 }}>
                          <div style={{ height: "100%", width: `${aiSummary.score}%`, background: aiSummary.score >= 70 ? COLORS.success : aiSummary.score >= 50 ? COLORS.warning : COLORS.danger, borderRadius: 20 }} />
                        </div>
                        <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(110px, 1fr))", gap: 6 }}>
                          {[["📝 Aptitude", aiSummary.scoreBreakdown?.aptitude, 40], ["⌨️ Typing", aiSummary.scoreBreakdown?.typing, 30], ["👤 Profile", aiSummary.scoreBreakdown?.profile, 30]].map(([l, v, max]) => (
                            <div key={l} style={{ textAlign: "center", background: COLORS.surface, borderRadius: 8, padding: "6px" }}>
                              <div style={{ fontSize: 10, color: COLORS.muted, marginBottom: 2 }}>{l}</div>
                              <div style={{ fontSize: 14, fontWeight: 700, color: COLORS.text }}>{v}<span style={{ fontSize: 10, color: COLORS.muted }}>/{max}</span></div>
                            </div>
                          ))}
                        </div>
                      </div>

                      {/* Strengths & Concerns */}
                      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(130px, 1fr))", gap: 8, marginBottom: 12 }}>
                        {aiSummary.strengths?.length > 0 && (
                          <div style={{ background: "rgba(46,204,113,0.08)", borderRadius: 10, padding: "10px 12px", border: `1px solid rgba(46,204,113,0.2)` }}>
                            <div style={{ fontSize: 10, fontWeight: 700, color: COLORS.success, marginBottom: 6 }}>✓ STRENGTHS</div>
                            {aiSummary.strengths.map((s, i) => <div key={i} style={{ fontSize: 12, color: COLORS.text, marginBottom: 3 }}>• {s}</div>)}
                          </div>
                        )}
                        {aiSummary.concerns?.length > 0 && (
                          <div style={{ background: "rgba(231,76,60,0.08)", borderRadius: 10, padding: "10px 12px", border: `1px solid rgba(231,76,60,0.2)` }}>
                            <div style={{ fontSize: 10, fontWeight: 700, color: COLORS.danger, marginBottom: 6 }}>⚠ CONCERNS</div>
                            {aiSummary.concerns.map((c, i) => <div key={i} style={{ fontSize: 12, color: COLORS.text, marginBottom: 3 }}>• {c}</div>)}
                          </div>
                        )}
                      </div>

                      {/* AI Recommendation */}
                      <div style={{ background: aiSummary.recommendation === "approve" ? "rgba(46,204,113,0.1)" : aiSummary.recommendation === "reject" ? "rgba(231,76,60,0.1)" : "rgba(243,156,18,0.1)", border: `1px solid ${aiSummary.recommendation === "approve" ? "rgba(46,204,113,0.3)" : aiSummary.recommendation === "reject" ? "rgba(231,76,60,0.3)" : "rgba(243,156,18,0.3)"}`, borderRadius: 10, padding: "10px 14px" }}>
                        <div style={{ fontSize: 10, fontWeight: 700, color: COLORS.muted, marginBottom: 4 }}>🤖 AI RECOMMENDATION</div>
                        <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
                          <span style={{ fontSize: 18 }}>{aiSummary.recommendation === "approve" ? "✅" : aiSummary.recommendation === "reject" ? "❌" : "⏳"}</span>
                          <div>
                            <div style={{ fontSize: 14, fontWeight: 700, color: aiSummary.recommendation === "approve" ? COLORS.success : aiSummary.recommendation === "reject" ? COLORS.danger : COLORS.warning, textTransform: "capitalize" }}>{aiSummary.recommendation}</div>
                            <div style={{ fontSize: 12, color: COLORS.muted }}>{aiSummary.recommendationReason}</div>
                          </div>
                        </div>
                      </div>
                    </div>
                  )}

                  {/* ── Resume Summary sub-tab ── */}
                  {resumeTab === "resume" && (
                    <div>
                      {aiSummary.resumeRead ? (
                        <div>
                          <div style={{ display: "flex", alignItems: "center", gap: 6, marginBottom: 14, padding: "8px 12px", background: "rgba(46,204,113,0.08)", borderRadius: 8, border: `1px solid rgba(46,204,113,0.2)` }}>
                            <span style={{ fontSize: 14 }}>📄</span>
                            <span style={{ fontSize: 12, color: COLORS.success, fontWeight: 600 }}>Resume was read and analysed by AI · {selected?.resume}</span>
                          </div>
                          {/* Resume highlights */}
                          <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
                            {[
                              ["💼 Experience", aiSummary.resumeHighlights?.experience],
                              ["🎓 Education", aiSummary.resumeHighlights?.education],
                              ["⏱ Total Experience", aiSummary.resumeHighlights?.totalExperience],
                            ].map(([label, value]) => value && (
                              <div key={label} style={{ background: COLORS.card, borderRadius: 10, padding: "10px 14px" }}>
                                <div style={{ fontSize: 11, color: COLORS.muted, fontWeight: 700, marginBottom: 4 }}>{label}</div>
                                <div style={{ fontSize: 13, color: COLORS.text, lineHeight: 1.5 }}>{value}</div>
                              </div>
                            ))}
                            {aiSummary.resumeHighlights?.skills?.length > 0 && (
                              <div style={{ background: COLORS.card, borderRadius: 10, padding: "10px 14px" }}>
                                <div style={{ fontSize: 11, color: COLORS.muted, fontWeight: 700, marginBottom: 8 }}>🛠 SKILLS IDENTIFIED</div>
                                <div style={{ display: "flex", flexWrap: "wrap", gap: 6 }}>
                                  {aiSummary.resumeHighlights.skills.map((sk, i) => (
                                    <span key={i} style={{ background: "rgba(99,102,241,0.15)", border: `1px solid rgba(99,102,241,0.3)`, borderRadius: 20, padding: "3px 10px", fontSize: 12, color: "#818cf8", fontWeight: 500 }}>{sk}</span>
                                  ))}
                                </div>
                              </div>
                            )}
                          </div>
                        </div>
                      ) : (
                        <div style={{ textAlign: "center", padding: "20px 0", color: COLORS.muted }}>
                          <div style={{ fontSize: 32, marginBottom: 10 }}>📄</div>
                          <div style={{ fontSize: 14, fontWeight: 600, color: COLORS.text, marginBottom: 6 }}>
                            {selected?.resumeData && !selected?.resume?.toLowerCase().endsWith(".pdf")
                              ? "Resume is a DOC/DOCX file"
                              : "No resume uploaded"
                            }
                          </div>
                          <div style={{ fontSize: 12, color: COLORS.muted }}>
                            {selected?.resumeData && !selected?.resume?.toLowerCase().endsWith(".pdf")
                              ? "AI can only read PDF resumes. Ask the candidate to upload a PDF version for full AI analysis."
                              : "The candidate did not upload a resume. AI analysis is based on profile data only."
                            }
                          </div>
                        </div>
                      )}
                    </div>
                  )}
                </div>
              )}

              {aiSummary?.error && !aiLoading && (
                <div style={{ fontSize: 13, color: COLORS.muted, textAlign: "center", padding: "8px 0" }}>⚠️ AI analysis unavailable. You can still decide manually.</div>
              )}
            </div>

            <label style={s.label}>Remarks {selected.panelStatus !== "pending" && <span style={{ fontSize:11,color:COLORS.muted,fontWeight:400 }}>— locked after decision</span>}</label>
            <div style={{ position: "relative" }}>
              <textarea value={remark} onChange={e => selected.panelStatus === "pending" && setRemark(e.target.value)} rows={3} style={{ ...s.input, resize: "none", paddingRight: 120, opacity: selected.panelStatus !== "pending" ? 0.6 : 1, cursor: selected.panelStatus !== "pending" ? "not-allowed" : "text" }} placeholder={selected.panelStatus !== "pending" ? "Remarks locked — decision already made" : "Add remarks for this candidate..."} readOnly={selected.panelStatus !== "pending"} />
              {selected.panelStatus === "pending" && (
                <button
                  onClick={() => generateAiRemark(selected, aiDecision || selected.panelStatus || "pending")}
                  disabled={aiRemarkLoading}
                  style={{ position: "absolute", top: 8, right: 8, background: "rgba(99,102,241,0.15)", border: `1px solid rgba(99,102,241,0.35)`, borderRadius: 6, padding: "4px 10px", color: "#818cf8", cursor: "pointer", fontSize: 11, fontWeight: 600, whiteSpace: "nowrap" }}
                >{aiRemarkLoading ? "✍️…" : "✨ AI Remark"}</button>
              )}
            </div>
            {aiRemarkSuggestion && (
              <div style={{ background: "rgba(99,102,241,0.08)", border: `1px solid rgba(99,102,241,0.25)`, borderRadius: 8, padding: "10px 12px", marginTop: -12, marginBottom: 10, display: "flex", justifyContent: "space-between", alignItems: "center", gap: 10 }}>
                <div style={{ fontSize: 13, color: COLORS.text, fontStyle: "italic", flex: 1 }}>"{aiRemarkSuggestion}"</div>
                <button onClick={() => setRemark(aiRemarkSuggestion)} style={{ background: COLORS.accent, border: "none", borderRadius: 6, padding: "4px 10px", color: "#fff", cursor: "pointer", fontSize: 11, fontWeight: 600, whiteSpace: "nowrap" }}>Use ↑</button>
              </div>
            )}

            {/* Timestamps in modal */}
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(120px, 1fr))", gap: 6, marginBottom: 14 }}>
              {[["📝 Registered", selected.registeredAt], ["🧠 Aptitude Done", selected.aptCompletedAt], ["⌨️ Typing Done", selected.typingCompletedAt], ["⚖️ Panel Decision", selected.panelDecidedAt]].map(([label, ts]) => (
                <div key={label} style={{ background: COLORS.card, borderRadius: 8, padding: "7px 10px" }}>
                  <div style={{ fontSize: 10, color: COLORS.muted, marginBottom: 2 }}>{label}</div>
                  <div style={{ fontSize: 12, fontWeight: 500, color: ts ? COLORS.gold : COLORS.muted }}>{fmtTs(ts)}</div>
                </div>
              ))}
            </div>
            {/* Decision buttons — only available while status is pending */}
            {selected.panelStatus === "pending" ? (
              <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(120px, 1fr))", gap: 8, marginTop: 8 }}>
                <button onClick={() => decide(selected.id, "approved")} style={{ padding: "10px", borderRadius: 10, border: "none", background: COLORS.success, color: "#fff", cursor: "pointer", fontWeight: 600 }}>✅ Approve</button>
                <button onClick={() => decide(selected.id, "pending")} style={{ padding: "10px", borderRadius: 10, border: "none", background: COLORS.warning, color: "#fff", cursor: "pointer", fontWeight: 600 }}>⏳ Keep Pending</button>
                <button onClick={() => decide(selected.id, "rejected")} style={{ padding: "10px", borderRadius: 10, border: "none", background: COLORS.danger, color: "#fff", cursor: "pointer", fontWeight: 600 }}>❌ Reject</button>
              </div>
            ) : (
              <div style={{ background: selected.panelStatus === "approved" ? "rgba(46,204,113,0.1)" : "rgba(231,76,60,0.1)", border: `1px solid ${selected.panelStatus === "approved" ? "rgba(46,204,113,0.4)" : "rgba(231,76,60,0.4)"}`, borderRadius: 12, padding: "14px 16px", marginTop: 8 }}>
                <div style={{ display: "flex", alignItems: "center", gap: 10 }}>
                  <span style={{ fontSize: 24 }}>{selected.panelStatus === "approved" ? "✅" : "❌"}</span>
                  <div>
                    <div style={{ fontSize: 14, fontWeight: 700, color: selected.panelStatus === "approved" ? COLORS.success : COLORS.danger, textTransform: "capitalize" }}>
                      Decision: {selected.panelStatus}
                    </div>
                    <div style={{ fontSize: 12, color: COLORS.muted, marginTop: 2 }}>
                      Decided on {fmtTs(selected.panelDecidedAt)} · Only the Super Admin can change this.
                    </div>
                  </div>
                  <div style={{ marginLeft: "auto", background: COLORS.card, border: `1px solid ${COLORS.border}`, borderRadius: 8, padding: "4px 12px", fontSize: 12, color: COLORS.muted }}>
                    🔒 Locked
                  </div>
                </div>
              </div>
            )}
            {/* ── Transfer Candidate — only if pending ── */}
            {selected.panelStatus === "pending" && (
              <div style={{ marginTop: 10 }}>
                {!showTransfer ? (
                  <button
                    onClick={() => setShowTransfer(true)}
                    style={{ width: "100%", background: "rgba(52,152,219,0.1)", border: `1px solid rgba(52,152,219,0.35)`, borderRadius: 10, padding: "9px", color: "#3498db", cursor: "pointer", fontSize: 13, fontWeight: 600 }}
                  >↗ Transfer to Another Panelist</button>
                ) : (
                  <div style={{ background: "rgba(52,152,219,0.07)", border: `1px solid rgba(52,152,219,0.3)`, borderRadius: 12, padding: "14px 16px" }}>
                    <div style={{ fontSize: 13, fontWeight: 700, color: "#3498db", marginBottom: 10 }}>↗ Transfer Candidate</div>
                    <div style={{ fontSize: 12, color: COLORS.muted, marginBottom: 10 }}>
                      Select a panelist to transfer <strong style={{ color: COLORS.text }}>{selected.name}</strong> to. This will remove them from your queue.
                    </div>
                    <div style={{ display: "flex", flexDirection: "column", gap: 6, marginBottom: 12 }}>
                      {panelists
                        .filter(p => !p.disabled && p.id !== currentPanelist?.id)
                        .map(p => {
                          const assignedCount = candidates.filter(c => c.assignedPanelistId === p.id && c.panelStatus === "pending").length;
                          return (
                            <div
                              key={p.id}
                              onClick={() => setTransferTarget(p.id)}
                              style={{ display: "flex", justifyContent: "space-between", alignItems: "center", background: transferTarget === p.id ? "rgba(52,152,219,0.15)" : COLORS.card, border: `1px solid ${transferTarget === p.id ? "rgba(52,152,219,0.5)" : COLORS.border}`, borderRadius: 8, padding: "10px 12px", cursor: "pointer" }}
                            >
                              <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
                                <div style={{ width: 30, height: 30, borderRadius: "50%", background: "rgba(52,152,219,0.15)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 14 }}>🎯</div>
                                <div>
                                  <div style={{ fontSize: 13, fontWeight: 600, color: COLORS.text }}>{p.name || p.username}</div>
                                  <div style={{ fontSize: 11, color: COLORS.muted }}>{p.email}</div>
                                </div>
                              </div>
                              <div style={{ textAlign: "right" }}>
                                <div style={{ fontSize: 12, color: COLORS.muted }}>{assignedCount} pending</div>
                                {transferTarget === p.id && <div style={{ fontSize: 11, color: "#3498db", fontWeight: 700 }}>✓ Selected</div>}
                              </div>
                            </div>
                          );
                        })}
                      {panelists.filter(p => !p.disabled && p.id !== currentPanelist?.id).length === 0 && (
                        <div style={{ fontSize: 13, color: COLORS.muted, textAlign: "center", padding: "10px 0" }}>No other active panelists available.</div>
                      )}
                    </div>
                    <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 8 }}>
                      <button onClick={() => { setShowTransfer(false); setTransferTarget(""); }} style={{ padding: "9px", borderRadius: 10, border: `1px solid ${COLORS.border}`, background: "transparent", color: COLORS.muted, cursor: "pointer", fontSize: 13, fontWeight: 600 }}>Cancel</button>
                      <button
                        onClick={doTransfer}
                        disabled={!transferTarget}
                        style={{ padding: "9px", borderRadius: 10, border: "none", background: transferTarget ? "#3498db" : COLORS.card, color: transferTarget ? "#fff" : COLORS.muted, cursor: transferTarget ? "pointer" : "not-allowed", fontSize: 13, fontWeight: 600 }}
                      >↗ Confirm Transfer</button>
                    </div>
                  </div>
                )}
              </div>
            )}

            <button onClick={() => { setSelected(null); setResumeTab("insights"); setShowTransfer(false); setTransferTarget(""); }} style={{ ...s.btnOut, marginTop: 10 }}>Close</button>
          </div>
        </div>
      )}
    </div>
  );
}

function Logo() {
  return (
    <div style={{ ...s.logo, justifyContent: "center", marginBottom: 20 }}>
      <div style={{ width: 34, height: 34, background: COLORS.accent, borderRadius: 8, display: "flex", alignItems: "center", justifyContent: "center", fontWeight: 800, fontSize: 18 }}>R</div>
      <span style={s.logoText}>Recruit<span style={s.logoAccent}>Pro</span></span>
    </div>
  );
}

// ─── Storage helpers ──────────────────────────────────────────────────────────
const STORAGE_KEY = "recruitpro-candidates";
// ─── Supabase Client ──────────────────────────────────────────────────────────
const SUPABASE_URL = "https://licjebcznbiswusvhzhz.supabase.co";
const SUPABASE_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImxpY2plYmN6bmJpc3d1c3Zoemh6Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3ODEwOTE4NTgsImV4cCI6MjA5NjY2Nzg1OH0.kRA9VZcrHoVeFevbY40JYc1Oregr4C7LmDN2uQLjQpA";

const sb = {
  async query(table, options = {}) {
    let url = `${SUPABASE_URL}/rest/v1/${table}`;
    const params = [];
    if (options.select) params.push(`select=${options.select}`);
    if (options.filter) params.push(options.filter);
    if (options.order) params.push(`order=${options.order}`);
    if (params.length) url += "?" + params.join("&");
    const res = await fetch(url, {
      headers: {
        apikey: SUPABASE_KEY,
        Authorization: `Bearer ${SUPABASE_KEY}`,
        "Content-Type": "application/json",
      },
    });
    if (!res.ok) throw new Error(`Supabase query failed: ${res.status}`);
    return res.json();
  },
  async upsert(table, data, onConflict = "id") {
    const res = await fetch(`${SUPABASE_URL}/rest/v1/${table}?on_conflict=${onConflict}`, {
      method: "POST",
      headers: {
        apikey: SUPABASE_KEY,
        Authorization: `Bearer ${SUPABASE_KEY}`,
        "Content-Type": "application/json",
        Prefer: "resolution=merge-duplicates,return=minimal",
      },
      body: JSON.stringify(Array.isArray(data) ? data : [data]),
    });
    if (!res.ok) { const t = await res.text(); throw new Error(`Supabase upsert failed: ${res.status} ${t}`); }
  },
  async delete(table, filter) {
    const res = await fetch(`${SUPABASE_URL}/rest/v1/${table}?${filter}`, {
      method: "DELETE",
      headers: {
        apikey: SUPABASE_KEY,
        Authorization: `Bearer ${SUPABASE_KEY}`,
        "Content-Type": "application/json",
      },
    });
    if (!res.ok) throw new Error(`Supabase delete failed: ${res.status}`);
  },
};

// ─── Data load / save via Supabase ───────────────────────────────────────────
async function loadCandidates() {
  try {
    const rows = await sb.query("candidates", { select: "*", order: "created_at.asc" });
    return rows.map(r => JSON.parse(r.data));
  } catch (e) { console.error("loadCandidates:", e); return []; }
}
async function saveCandidates(list) {
  try {
    if (!list.length) return;
    const rows = list.map(c => ({ id: String(c.id), data: JSON.stringify(c) }));
    await sb.upsert("candidates", rows, "id");
  } catch (e) { console.error("saveCandidates:", e); }
}
async function deleteCandidateRow(id) {
  try { await sb.delete("candidates", `id=eq.${id}`); } catch (e) { console.error("deleteCandidate:", e); }
}

async function loadPanelists() {
  try {
    const rows = await sb.query("panelists", { select: "*", order: "created_at.asc" });
    return rows.map(r => JSON.parse(r.data));
  } catch (e) { console.error("loadPanelists:", e); return []; }
}
async function savePanelists(list) {
  try {
    if (!list.length) return;
    const rows = list.map(p => ({ id: String(p.id), data: JSON.stringify(p) }));
    await sb.upsert("panelists", rows, "id");
  } catch (e) { console.error("savePanelists:", e); }
}

async function loadSuperAdmin() {
  try {
    const rows = await sb.query("config", { select: "*", filter: "key=eq.superadmin" });
    if (rows.length && rows[0].value) return JSON.parse(rows[0].value);
  } catch (e) { console.error("loadSuperAdmin:", e); }
  return null;
}
async function saveSuperAdmin(data) {
  try {
    await sb.upsert("config", { key: "superadmin", value: JSON.stringify(data) }, "key");
  } catch (e) { console.error("saveSuperAdmin:", e); }
}

async function loadAlarms() {
  try {
    const rows = await sb.query("alarms", { select: "*", order: "created_at.asc" });
    return rows.map(r => JSON.parse(r.data));
  } catch (e) { console.error("loadAlarms:", e); return []; }
}
async function saveAlarms(list) {
  try {
    if (!list.length) return;
    const rows = list.map(a => ({ id: String(a.id), data: JSON.stringify(a) }));
    await sb.upsert("alarms", rows, "id");
  } catch (e) { console.error("saveAlarms:", e); }
}

// ─── Duplicate check — same calendar day ─────────────────────────────────────
function todayStr() {
  const d = new Date();
  return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,"0")}-${String(d.getDate()).padStart(2,"0")}`;
}

// Always extract local YYYY-MM-DD from any ISO string (handles both UTC and local ISO)
function localDateOf(iso) {
  if (!iso) return "";
  const d = new Date(iso); // parses both "2025-06-03T19:30:00.000Z" and "2025-06-04T01:00:00"
  return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,"0")}-${String(d.getDate()).padStart(2,"0")}`;
}

function localISO() {
  const d = new Date();
  const pad = n => String(n).padStart(2,"0");
  return `${d.getFullYear()}-${pad(d.getMonth()+1)}-${pad(d.getDate())}T${pad(d.getHours())}:${pad(d.getMinutes())}:${pad(d.getSeconds())}`;
}

function checkDuplicates(form, candidates) {
  const today = todayStr();
  const todayRegs = candidates.filter(c => localDateOf(c.registeredAt) === today);
  const hits = [];
  const mobile  = form.mobile.trim();
  const pan     = form.pan.trim().toUpperCase();
  const aadhaar = form.aadhaar.replace(/\s/g, "").trim();

  todayRegs.forEach(c => {
    if (c.mobile.trim() === mobile)
      hits.push({ field: "Mobile Number", value: mobile, existingName: c.name, existingTime: c.registeredAt });
    if (c.pan.trim().toUpperCase() === pan)
      hits.push({ field: "PAN Card", value: pan, existingName: c.name, existingTime: c.registeredAt });
    if (c.aadhaar.replace(/\s/g, "") === aadhaar)
      hits.push({ field: "Aadhaar Card", value: aadhaar.slice(0,4)+"XXXX"+aadhaar.slice(-4), existingName: c.name, existingTime: c.registeredAt });
  });
  return hits;
}

// ─── Auto-assign panelist (lowest load, prefer idle) ─────────────────────────
function pickPanelist(panelists, candidates) {
  if (!panelists || panelists.length === 0) return null;
  // Exclude disabled AND panelists on break
  const active = panelists.filter(p => !p.disabled && !p.onBreak);
  if (active.length === 0) return null;
  if (active.length === 1) return active[0];
  return active[Math.floor(Math.random() * active.length)];
}

// ─── Main App ─────────────────────────────────────────────────────────────────
export default function App() {
  const [screen, setScreen] = useState("qr");
  const [candidates, setCandidatesRaw] = useState([]);
  const [loggedIn, setLoggedIn] = useState(null);
  const [isAdmin, setIsAdmin] = useState(false);
  const [isSuperAdmin, setIsSuperAdmin] = useState(false);
  const [currentPanelist, setCurrentPanelist] = useState(null);
  const [aptScore, setAptScore] = useState(null);
  const [storageReady, setStorageReady] = useState(false);
  const [panelists, setPanelistsRaw] = useState([]);
  const [superAdmin, setSuperAdminRaw] = useState(null);
  const [alarms, setAlarmsRaw] = useState([]);

  useEffect(() => {
    Promise.all([loadCandidates(), loadPanelists(), loadSuperAdmin(), loadAlarms()]).then(([cands, pans, sa, alms]) => {
      setCandidatesRaw(cands);
      setPanelistsRaw(pans);
      setSuperAdminRaw(sa);
      setAlarmsRaw(alms);
      setStorageReady(true);
    });
  }, []);

  function setCandidates(updater) {
    setCandidatesRaw(prev => {
      const next = typeof updater === "function" ? updater(prev) : updater;
      saveCandidates(next);
      return next;
    });
  }
  function setPanelists(updater) {
    setPanelistsRaw(prev => {
      const next = typeof updater === "function" ? updater(prev) : updater;
      savePanelists(next);
      return next;
    });
  }
  function setSuperAdmin(cred) { setSuperAdminRaw(cred); saveSuperAdmin(cred); }
  function setAlarms(list) { setAlarmsRaw(list); saveAlarms(list); }

  useEffect(() => {
    const go = () => setScreen("register");
    window.addEventListener("goRegister", go);
    return () => window.removeEventListener("goRegister", go);
  }, []);

  function updateCandidate(updates) {
    setCandidates(p => p.map(c => c.id === loggedIn.id ? { ...c, ...updates } : c));
    setLoggedIn(p => ({ ...p, ...updates }));
  }

  function handleTypingComplete(result) {
    const assigned = result.passed ? pickPanelist(panelists, candidates) : null;
    const updates = {
      typingScore: result,
      typingCompletedAt: localISO(),
      ...(assigned ? { assignedPanelistId: assigned.id, assignedAt: localISO() } : {})
    };
    updateCandidate(updates);
    setScreen("done");
  }

  if (!storageReady) {
    return (
      <div style={{ ...s.page, justifyContent: "center", alignItems: "center" }}>
        <Logo />
        <div style={{ color: COLORS.muted, fontSize: 14, marginTop: 12 }}>Loading saved data…</div>
      </div>
    );
  }

  if (screen === "qr") return <QRScreen onScan={() => setScreen("register")} onLogin={() => setScreen("login")} />;
  if (screen === "register") return <RegistrationForm candidates={candidates} setCandidates={setCandidates} alarms={alarms} setAlarms={setAlarms} onComplete={() => setScreen("login")} />;

  if (screen === "login") {
    if (isSuperAdmin) return <SuperAdminDashboard candidates={candidates} setCandidates={setCandidates} panelists={panelists} setPanelists={setPanelists} superAdmin={superAdmin} onSuperAdminSave={setSuperAdmin} alarms={alarms} setAlarms={setAlarms} onLogout={() => { setIsSuperAdmin(false); setScreen("login"); }} />;
    if (isAdmin) return <PanelDashboard candidates={candidates} setCandidates={setCandidates} panelists={panelists} setPanelists={setPanelists} currentPanelist={currentPanelist} onPanelistSave={cred => { setPanelists(p => p.map(x => x.id === cred.id ? cred : x)); setCurrentPanelist(cred); }} alarms={alarms} onLogout={() => { setIsAdmin(false); setCurrentPanelist(null); setScreen("login"); }} />;
    if (loggedIn) {
      const c = candidates.find(x => x.id === loggedIn.id) || loggedIn;
      if (c.aptScore == null) return <AptitudeTest candidate={c} onComplete={(sc, passed) => { updateCandidate({ aptScore: sc, aptCompletedAt: localISO() }); setAptScore(sc); if (passed) setScreen("typing"); else setScreen("done"); }} />;
      if (c.typingScore == null && c.aptScore >= 10) return <TypingTest candidate={c} aptScore={c.aptScore} onComplete={handleTypingComplete} />;
      return <CandidateDashboard candidate={c} panelists={panelists} onLogout={() => { setLoggedIn(null); setScreen("login"); }} />;
    }
    return <LoginScreen candidates={candidates} panelists={panelists} onPanelistsave={setPanelists} superAdmin={superAdmin} onSuperAdminSave={setSuperAdmin} onLogin={c => { setLoggedIn(c); setIsAdmin(false); setIsSuperAdmin(false); }} onAdminLogin={p => { setIsAdmin(true); setIsSuperAdmin(false); setCurrentPanelist(p); setLoggedIn(null); }} onSuperAdminLogin={() => { setIsSuperAdmin(true); setIsAdmin(false); setLoggedIn(null); }} />;
  }

  if (screen === "typing") {
    const c = candidates.find(x => x.id === loggedIn?.id) || loggedIn;
    return <TypingTest candidate={c} aptScore={aptScore} onComplete={handleTypingComplete} />;
  }

  if (screen === "done") {
    const c = candidates.find(x => x.id === loggedIn?.id) || loggedIn;
    return <CandidateDashboard candidate={c} panelists={panelists} onLogout={() => { setLoggedIn(null); setScreen("login"); }} />;
  }

  return null;
}
