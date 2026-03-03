import { useState, useEffect } from "react";

const STORAGE_KEY = "prospecting-sessions";
const METRICS_KEY = "email-metrics";

const defaultSession = () => ({
  id: Date.now(),
  date: new Date().toISOString().split("T")[0],
  phase: "pre", // pre | active | post | complete
  commitment: {
    leadsToFind: "",
    leadsToQualify: "",
    scriptsToGenerate: "",
    emailsToSend: "",
    nicheFocus: "",
    stateActivated: false,
  },
  actuals: {
    leadsFound: "",
    leadsQualified: "",
    scriptsGenerated: "",
    emailsSent: "",
    drifts: "",
    alignment: 2,
    resistanceHit: false,
    resistanceHandled: false,
  },
  review: {
    biggestWin: "",
    mainObstacle: "",
    nextIntent: "",
  },
});

const fmt = (n) => (n === "" || n === null || n === undefined ? "—" : n);
const pct = (a, b) =>
  !a || !b || b === 0 ? "—" : `${Math.round((a / b) * 100)}%`;

export default function App() {
  const [view, setView] = useState("today");
  const [sessions, setSessions] = useState([]);
  const [today, setToday] = useState(null);
  const [loaded, setLoaded] = useState(false);

  useEffect(() => {
    (async () => {
      try {
        const res = await window.storage.get(STORAGE_KEY);
        const data = res ? JSON.parse(res.value) : [];
        setSessions(data);
        const todayStr = new Date().toISOString().split("T")[0];
        const existing = data.find((s) => s.date === todayStr);
        setToday(existing || defaultSession());
      } catch {
        setSessions([]);
        setToday(defaultSession());
      }
      setLoaded(true);
    })();
  }, []);

  const save = async (updatedToday, updatedSessions) => {
    const todayStr = new Date().toISOString().split("T")[0];
    const others = (updatedSessions || sessions).filter(
      (s) => s.date !== todayStr
    );
    const all = updatedToday ? [updatedToday, ...others] : others;
    setSessions(all);
    if (updatedToday) setToday(updatedToday);
    await window.storage.set(STORAGE_KEY, JSON.stringify(all));
  };

  const updateToday = (section, field, value) => {
    const updated = {
      ...today,
      [section]: { ...today[section], [field]: value },
    };
    save(updated, sessions);
  };

  const advancePhase = (phase) => {
    const updated = { ...today, phase };
    save(updated, sessions);
  };

  if (!loaded) {
    return (
      <div style={styles.loading}>
        <span style={styles.loadingDot}>■</span>
      </div>
    );
  }

  return (
    <div style={styles.root}>
      <header style={styles.header}>
        <div style={styles.headerLeft}>
          <span style={styles.logo}>◈ PROSPECTOR</span>
          <span style={styles.tagline}>COPYWRITING PIPELINE JOURNAL</span>
        </div>
        <nav style={styles.nav}>
          {["today", "log", "metrics"].map((v) => (
            <button
              key={v}
              onClick={() => setView(v)}
              style={{
                ...styles.navBtn,
                ...(view === v ? styles.navBtnActive : {}),
              }}
            >
              {v.toUpperCase()}
            </button>
          ))}
        </nav>
      </header>

      <main style={styles.main}>
        {view === "today" && (
          <TodayView
            today={today}
            updateToday={updateToday}
            advancePhase={advancePhase}
          />
        )}
        {view === "log" && <LogView sessions={sessions} save={save} setSessions={setSessions} />}
        {view === "metrics" && <MetricsView sessions={sessions} />}
      </main>
    </div>
  );
}

// ─── TODAY VIEW ────────────────────────────────────────────────────────────────

function TodayView({ today, updateToday, advancePhase }) {
  const phase = today.phase;
  const dateStr = new Date().toLocaleDateString("en-ZA", {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
  });

  return (
    <div style={styles.todayWrap}>
      <div style={styles.dateLine}>
        <span style={styles.dateText}>{dateStr}</span>
        <PhaseIndicator phase={phase} />
      </div>

      {(phase === "pre" || phase === "active" || phase === "post" || phase === "complete") && (
        <Section
          label="01 — PRE-SESSION COMMITMENT"
          sublabel="Set your targets before the block starts"
          locked={phase === "complete"}
        >
          <div style={styles.grid2}>
            <Field
              label="Leads to find"
              value={today.commitment.leadsToFind}
              onChange={(v) => updateToday("commitment", "leadsToFind", v)}
              type="number"
              placeholder="e.g. 20"
              locked={phase === "complete"}
            />
            <Field
              label="Leads to qualify"
              value={today.commitment.leadsToQualify}
              onChange={(v) => updateToday("commitment", "leadsToQualify", v)}
              type="number"
              placeholder="e.g. 10"
              locked={phase === "complete"}
            />
            <Field
              label="Scripts to generate"
              value={today.commitment.scriptsToGenerate}
              onChange={(v) =>
                updateToday("commitment", "scriptsToGenerate", v)
              }
              type="number"
              placeholder="e.g. 5"
              locked={phase === "complete"}
            />
            <Field
              label="Emails to send"
              value={today.commitment.emailsToSend}
              onChange={(v) => updateToday("commitment", "emailsToSend", v)}
              type="number"
              placeholder="e.g. 5"
              locked={phase === "complete"}
            />
          </div>
          <Field
            label="Niche / focus today"
            value={today.commitment.nicheFocus}
            onChange={(v) => updateToday("commitment", "nicheFocus", v)}
            placeholder="e.g. Online fitness coaches running webinar funnels"
            locked={phase === "complete"}
          />
          <CheckField
            label="State activation done (5–10 min visualisation)"
            checked={today.commitment.stateActivated}
            onChange={(v) => updateToday("commitment", "stateActivated", v)}
            locked={phase === "complete"}
          />
          {phase === "pre" && (
            <ActionButton
              label="START 90-MIN BLOCK →"
              onClick={() => advancePhase("active")}
            />
          )}
        </Section>
      )}

      {(phase === "active" || phase === "post" || phase === "complete") && (
        <Section
          label="02 — IN-SESSION ACTUALS"
          sublabel="Log as you go or immediately after the block"
          locked={phase === "complete"}
        >
          <div style={styles.grid2}>
            <Field
              label="Leads found"
              value={today.actuals.leadsFound}
              onChange={(v) => updateToday("actuals", "leadsFound", v)}
              type="number"
              placeholder="actual"
              locked={phase === "complete"}
            />
            <Field
              label="Leads qualified"
              value={today.actuals.leadsQualified}
              onChange={(v) => updateToday("actuals", "leadsQualified", v)}
              type="number"
              placeholder="actual"
              locked={phase === "complete"}
            />
            <Field
              label="Scripts generated"
              value={today.actuals.scriptsGenerated}
              onChange={(v) => updateToday("actuals", "scriptsGenerated", v)}
              type="number"
              placeholder="actual"
              locked={phase === "complete"}
            />
            <Field
              label="Emails sent"
              value={today.actuals.emailsSent}
              onChange={(v) => updateToday("actuals", "emailsSent", v)}
              type="number"
              placeholder="actual"
              locked={phase === "complete"}
            />
          </div>

          <div style={styles.grid2}>
            <Field
              label="Attention drifts noticed"
              value={today.actuals.drifts}
              onChange={(v) => updateToday("actuals", "drifts", v)}
              type="number"
              placeholder="count"
              locked={phase === "complete"}
            />
            <div>
              <label style={styles.fieldLabel}>Emotional alignment</label>
              <div style={styles.alignRow}>
                {[1, 2, 3].map((n) => (
                  <button
                    key={n}
                    onClick={() =>
                      phase !== "complete" &&
                      updateToday("actuals", "alignment", n)
                    }
                    style={{
                      ...styles.alignBtn,
                      ...(today.actuals.alignment === n
                        ? styles.alignBtnActive
                        : {}),
                    }}
                  >
                    {["LOW", "MED", "HIGH"][n - 1]}
                  </button>
                ))}
              </div>
            </div>
          </div>

          <div style={styles.checkRow}>
            <CheckField
              label="Resistance hit"
              checked={today.actuals.resistanceHit}
              onChange={(v) => updateToday("actuals", "resistanceHit", v)}
              locked={phase === "complete"}
              inline
            />
            <CheckField
              label="Resistance handled (DISARM / acted anyway)"
              checked={today.actuals.resistanceHandled}
              onChange={(v) => updateToday("actuals", "resistanceHandled", v)}
              locked={phase === "complete"}
              inline
            />
          </div>

          {phase === "active" && (
            <ActionButton
              label="END BLOCK & REVIEW →"
              onClick={() => advancePhase("post")}
            />
          )}
        </Section>
      )}

      {(phase === "post" || phase === "complete") && (
        <Section
          label="03 — POST-SESSION REVIEW"
          sublabel="3 questions. 2 minutes max."
          locked={phase === "complete"}
        >
          <Field
            label="Biggest win from this block"
            value={today.review.biggestWin}
            onChange={(v) => updateToday("review", "biggestWin", v)}
            placeholder="What actually happened that was good?"
            locked={phase === "complete"}
          />
          <Field
            label="Main obstacle"
            value={today.review.mainObstacle}
            onChange={(v) => updateToday("review", "mainObstacle", v)}
            placeholder="What slowed you down or stopped you?"
            locked={phase === "complete"}
          />
          <Field
            label="One thing to do differently next session"
            value={today.review.nextIntent}
            onChange={(v) => updateToday("review", "nextIntent", v)}
            placeholder="Specific adjustment, not a vague intention"
            locked={phase === "complete"}
          />

          {phase === "post" && (
            <ActionButton
              label="CLOSE SESSION ✓"
              onClick={() => advancePhase("complete")}
              variant="confirm"
            />
          )}
        </Section>
      )}

      {phase === "complete" && (
        <Section label="04 — SESSION SUMMARY" sublabel="Today's numbers">
          <SummaryRow
            commitment={today.commitment}
            actuals={today.actuals}
          />
        </Section>
      )}
    </div>
  );
}

function SummaryRow({ commitment, actuals }) {
  const rows = [
    ["Leads found", commitment.leadsToFind, actuals.leadsFound],
    ["Leads qualified", commitment.leadsToQualify, actuals.leadsQualified],
    ["Scripts generated", commitment.scriptsToGenerate, actuals.scriptsGenerated],
    ["Emails sent", commitment.emailsToSend, actuals.emailsSent],
  ];

  return (
    <div style={styles.summaryTable}>
      <div style={styles.summaryHeader}>
        <span>METRIC</span>
        <span>TARGET</span>
        <span>ACTUAL</span>
        <span>DELTA</span>
      </div>
      {rows.map(([label, target, actual]) => {
        const t = parseInt(target) || 0;
        const a = parseInt(actual) || 0;
        const delta = a - t;
        return (
          <div key={label} style={styles.summaryRow}>
            <span style={styles.summaryLabel}>{label}</span>
            <span style={styles.summaryNum}>{fmt(target)}</span>
            <span style={styles.summaryNum}>{fmt(actual)}</span>
            <span
              style={{
                ...styles.summaryNum,
                color:
                  delta > 0 ? "#4ade80" : delta < 0 ? "#f87171" : "#a0a0a0",
              }}
            >
              {target === "" || actual === ""
                ? "—"
                : delta >= 0
                ? `+${delta}`
                : delta}
            </span>
          </div>
        );
      })}
    </div>
  );
}

// ─── LOG VIEW ──────────────────────────────────────────────────────────────────

function LogView({ sessions, save, setSessions }) {
  const [editing, setEditing] = useState(null);
  const [emailData, setEmailData] = useState({});

  const handleEmailUpdate = (sessionId, field, value) => {
    setEmailData((prev) => ({
      ...prev,
      [sessionId]: { ...(prev[sessionId] || {}), [field]: value },
    }));
  };

  const saveEmailMetrics = async (session) => {
    const metrics = emailData[session.id] || {};
    const updated = { ...session, emailMetrics: { ...session.emailMetrics, ...metrics } };
    const newSessions = sessions.map((s) => s.id === session.id ? updated : s);
    setSessions(newSessions);
    await window.storage.set(STORAGE_KEY, JSON.stringify(newSessions));
    setEditing(null);
  };

  const completed = sessions.filter((s) => s.phase === "complete");

  if (completed.length === 0) {
    return (
      <div style={styles.empty}>
        <span style={styles.emptyIcon}>◻</span>
        <p style={styles.emptyText}>No completed sessions yet. Finish today's block to see it here.</p>
      </div>
    );
  }

  return (
    <div style={styles.logWrap}>
      <div style={styles.sectionHeader}>
        <span style={styles.sectionLabel}>SESSION LOG</span>
        <span style={styles.sectionSub}>Click a session to update email metrics (opens, clicks, replies)</span>
      </div>

      {completed.map((s) => (
        <div key={s.id} style={styles.logCard}>
          <div style={styles.logCardTop} onClick={() => setEditing(editing === s.id ? null : s.id)}>
            <div style={styles.logCardLeft}>
              <span style={styles.logDate}>{s.date}</span>
              {s.commitment.nicheFocus && (
                <span style={styles.logNiche}>{s.commitment.nicheFocus}</span>
              )}
            </div>
            <div style={styles.logMetrics}>
              <Chip label="Found" value={fmt(s.actuals.leadsFound)} />
              <Chip label="Qual" value={fmt(s.actuals.leadsQualified)} />
              <Chip label="Scripts" value={fmt(s.actuals.scriptsGenerated)} />
              <Chip label="Sent" value={fmt(s.actuals.emailsSent)} />
              {s.emailMetrics?.opens != null && (
                <Chip label="Opens" value={s.emailMetrics.opens} accent />
              )}
              {s.emailMetrics?.clicks != null && (
                <Chip label="Clicks" value={s.emailMetrics.clicks} accent />
              )}
              {s.emailMetrics?.replies != null && (
                <Chip label="Replies" value={s.emailMetrics.replies} accent />
              )}
            </div>
            <span style={styles.logToggle}>{editing === s.id ? "▲" : "▼"}</span>
          </div>

          {editing === s.id && (
            <div style={styles.logExpand}>
              {s.review.biggestWin && (
                <div style={styles.reviewLine}>
                  <span style={styles.reviewKey}>WIN</span>
                  <span style={styles.reviewVal}>{s.review.biggestWin}</span>
                </div>
              )}
              {s.review.mainObstacle && (
                <div style={styles.reviewLine}>
                  <span style={styles.reviewKey}>OBSTACLE</span>
                  <span style={styles.reviewVal}>{s.review.mainObstacle}</span>
                </div>
              )}
              {s.review.nextIntent && (
                <div style={styles.reviewLine}>
                  <span style={styles.reviewKey}>NEXT</span>
                  <span style={styles.reviewVal}>{s.review.nextIntent}</span>
                </div>
              )}
              <div style={styles.emailMetricsEdit}>
                <span style={styles.emailMetricsLabel}>UPDATE EMAIL METRICS (lagging)</span>
                <div style={styles.grid3}>
                  {["opens", "clicks", "replies"].map((field) => (
                    <div key={field}>
                      <label style={styles.fieldLabel}>{field.toUpperCase()}</label>
                      <input
                        type="number"
                        style={styles.input}
                        defaultValue={s.emailMetrics?.[field] ?? ""}
                        onChange={(e) => handleEmailUpdate(s.id, field, parseInt(e.target.value) || 0)}
                        placeholder="0"
                      />
                    </div>
                  ))}
                </div>
                <button onClick={() => saveEmailMetrics(s)} style={styles.saveBtn}>
                  SAVE METRICS
                </button>
              </div>
            </div>
          )}
        </div>
      ))}
    </div>
  );
}

// ─── METRICS VIEW ─────────────────────────────────────────────────────────────

function MetricsView({ sessions }) {
  const completed = sessions.filter((s) => s.phase === "complete");

  if (completed.length === 0) {
    return (
      <div style={styles.empty}>
        <span style={styles.emptyIcon}>◻</span>
        <p style={styles.emptyText}>No data yet. Complete sessions to see metrics.</p>
      </div>
    );
  }

  const sum = (arr, fn) => arr.reduce((acc, s) => acc + (parseInt(fn(s)) || 0), 0);

  const totalFound = sum(completed, (s) => s.actuals.leadsFound);
  const totalQual = sum(completed, (s) => s.actuals.leadsQualified);
  const totalScripts = sum(completed, (s) => s.actuals.scriptsGenerated);
  const totalSent = sum(completed, (s) => s.actuals.emailsSent);
  const totalOpens = sum(completed, (s) => s.emailMetrics?.opens);
  const totalClicks = sum(completed, (s) => s.emailMetrics?.clicks);
  const totalReplies = sum(completed, (s) => s.emailMetrics?.replies);

  const avg = (fn) => {
    const vals = completed.map((s) => parseInt(fn(s)) || 0).filter((v) => v > 0);
    return vals.length ? Math.round(vals.reduce((a, b) => a + b) / vals.length) : "—";
  };

  const consistencyScore = Math.round(
    (completed.filter((s) => {
      const t = parseInt(s.commitment.emailsToSend) || 0;
      const a = parseInt(s.actuals.emailsSent) || 0;
      return t > 0 && a >= t;
    }).length /
      completed.length) *
      100
  );

  const flowSessions = completed.filter(
    (s) => s.actuals.alignment === 3 && (parseInt(s.actuals.drifts) || 99) <= 5
  ).length;

  return (
    <div style={styles.metricsWrap}>
      <div style={styles.sectionHeader}>
        <span style={styles.sectionLabel}>PIPELINE METRICS</span>
        <span style={styles.sectionSub}>{completed.length} sessions recorded</span>
      </div>

      <div style={styles.kpiRow}>
        <KPI label="Commit hit rate" value={`${consistencyScore}%`} sub="emails sent ≥ target" />
        <KPI label="Flow sessions" value={`${flowSessions}/${completed.length}`} sub="high align + ≤5 drifts" />
        <KPI label="Avg emails/session" value={avg((s) => s.actuals.emailsSent)} sub="actual" />
      </div>

      <div style={styles.funnelSection}>
        <span style={styles.funnelTitle}>CUMULATIVE FUNNEL</span>
        <FunnelBar label="Leads found" value={totalFound} max={totalFound} />
        <FunnelBar label="Leads qualified" value={totalQual} max={totalFound} />
        <FunnelBar label="Scripts generated" value={totalScripts} max={totalFound} />
        <FunnelBar label="Emails sent" value={totalSent} max={totalFound} />
        <FunnelBar label="Opens" value={totalOpens} max={totalFound} accent />
        <FunnelBar label="Clicks" value={totalClicks} max={totalFound} accent />
        <FunnelBar label="Replies" value={totalReplies} max={totalFound} accent />
      </div>

      <div style={styles.conversionSection}>
        <span style={styles.funnelTitle}>CONVERSION RATES</span>
        <div style={styles.convGrid}>
          <ConvCell label="Found → Qualified" value={pct(totalQual, totalFound)} />
          <ConvCell label="Qualified → Script" value={pct(totalScripts, totalQual)} />
          <ConvCell label="Script → Sent" value={pct(totalSent, totalScripts)} />
          <ConvCell label="Sent → Open" value={pct(totalOpens, totalSent)} />
          <ConvCell label="Open → Click" value={pct(totalClicks, totalOpens)} />
          <ConvCell label="Click → Reply" value={pct(totalReplies, totalClicks)} />
        </div>
      </div>

      {completed.length >= 3 && (
        <div style={styles.trendSection}>
          <span style={styles.funnelTitle}>EMAILS SENT — SESSION TREND</span>
          <SparkLine
            data={completed.slice(-10).map((s) => parseInt(s.actuals.emailsSent) || 0)}
          />
        </div>
      )}
    </div>
  );
}

// ─── COMPONENTS ───────────────────────────────────────────────────────────────

function Section({ label, sublabel, locked, children }) {
  return (
    <div style={{ ...styles.section, ...(locked ? styles.sectionLocked : {}) }}>
      <div style={styles.sectionHeader}>
        <span style={styles.sectionLabel}>{label}</span>
        {sublabel && <span style={styles.sectionSub}>{sublabel}</span>}
        {locked && <span style={styles.lockedBadge}>LOCKED</span>}
      </div>
      <div style={styles.sectionBody}>{children}</div>
    </div>
  );
}

function Field({ label, value, onChange, type = "text", placeholder, locked }) {
  return (
    <div style={styles.fieldWrap}>
      <label style={styles.fieldLabel}>{label}</label>
      <input
        type={type}
        value={value}
        onChange={(e) => !locked && onChange(e.target.value)}
        placeholder={placeholder}
        readOnly={locked}
        style={{ ...styles.input, ...(locked ? styles.inputLocked : {}) }}
      />
    </div>
  );
}

function CheckField({ label, checked, onChange, locked, inline }) {
  return (
    <div
      style={{ ...styles.checkWrap, ...(inline ? { marginRight: 24 } : {}) }}
      onClick={() => !locked && onChange(!checked)}
    >
      <span style={{ ...styles.checkbox, ...(checked ? styles.checkboxChecked : {}) }}>
        {checked ? "■" : "□"}
      </span>
      <span style={styles.checkLabel}>{label}</span>
    </div>
  );
}

function PhaseIndicator({ phase }) {
  const labels = {
    pre: { text: "PRE-SESSION", color: "#f59e0b" },
    active: { text: "BLOCK ACTIVE", color: "#4ade80" },
    post: { text: "REVIEWING", color: "#60a5fa" },
    complete: { text: "COMPLETE", color: "#a78bfa" },
  };
  const { text, color } = labels[phase] || labels.pre;
  return (
    <span style={{ ...styles.phaseBadge, borderColor: color, color }}>
      {text}
    </span>
  );
}

function ActionButton({ label, onClick, variant }) {
  return (
    <button
      onClick={onClick}
      style={{
        ...styles.actionBtn,
        ...(variant === "confirm" ? styles.actionBtnConfirm : {}),
      }}
    >
      {label}
    </button>
  );
}

function Chip({ label, value, accent }) {
  return (
    <div style={{ ...styles.chip, ...(accent ? styles.chipAccent : {}) }}>
      <span style={styles.chipLabel}>{label}</span>
      <span style={styles.chipValue}>{value}</span>
    </div>
  );
}

function KPI({ label, value, sub }) {
  return (
    <div style={styles.kpiCard}>
      <span style={styles.kpiValue}>{value}</span>
      <span style={styles.kpiLabel}>{label}</span>
      <span style={styles.kpiSub}>{sub}</span>
    </div>
  );
}

function FunnelBar({ label, value, max, accent }) {
  const pct = max > 0 ? (value / max) * 100 : 0;
  return (
    <div style={styles.funnelRow}>
      <span style={styles.funnelLabel}>{label}</span>
      <div style={styles.funnelTrack}>
        <div
          style={{
            ...styles.funnelFill,
            width: `${pct}%`,
            backgroundColor: accent ? "#a78bfa" : "#f59e0b",
          }}
        />
      </div>
      <span style={styles.funnelNum}>{value || "—"}</span>
    </div>
  );
}

function ConvCell({ label, value }) {
  return (
    <div style={styles.convCell}>
      <span style={styles.convValue}>{value}</span>
      <span style={styles.convLabel}>{label}</span>
    </div>
  );
}

function SparkLine({ data }) {
  const max = Math.max(...data, 1);
  const w = 400;
  const h = 60;
  const pts = data.map((v, i) => {
    const x = (i / (data.length - 1)) * w;
    const y = h - (v / max) * h;
    return `${x},${y}`;
  });
  const path = `M ${pts.join(" L ")}`;
  return (
    <svg viewBox={`0 0 ${w} ${h}`} style={styles.spark} preserveAspectRatio="none">
      <polyline points={pts.join(" ")} fill="none" stroke="#f59e0b" strokeWidth="2" />
      {data.map((v, i) => {
        const x = (i / (data.length - 1)) * w;
        const y = h - (v / max) * h;
        return <circle key={i} cx={x} cy={y} r="3" fill="#f59e0b" />;
      })}
    </svg>
  );
}

// ─── STYLES ───────────────────────────────────────────────────────────────────

const C = {
  bg: "#0a0a0a",
  surface: "#111111",
  border: "#222222",
  borderHover: "#333333",
  text: "#e0e0e0",
  textMuted: "#666666",
  textDim: "#444444",
  amber: "#f59e0b",
  amberDim: "#78350f",
  green: "#4ade80",
  blue: "#60a5fa",
  purple: "#a78bfa",
  red: "#f87171",
};

const styles = {
  root: {
    background: C.bg,
    minHeight: "100vh",
    color: C.text,
    fontFamily: "'Courier New', monospace",
    fontSize: 13,
  },
  loading: {
    display: "flex",
    alignItems: "center",
    justifyContent: "center",
    height: "100vh",
    background: C.bg,
  },
  loadingDot: { color: C.amber, fontSize: 24, animation: "pulse 1s infinite" },
  header: {
    display: "flex",
    alignItems: "center",
    justifyContent: "space-between",
    padding: "16px 24px",
    borderBottom: `1px solid ${C.border}`,
    background: C.surface,
  },
  headerLeft: { display: "flex", flexDirection: "column", gap: 2 },
  logo: { color: C.amber, fontSize: 15, fontWeight: "bold", letterSpacing: 2 },
  tagline: { color: C.textMuted, fontSize: 10, letterSpacing: 3 },
  nav: { display: "flex", gap: 4 },
  navBtn: {
    background: "none",
    border: `1px solid ${C.border}`,
    color: C.textMuted,
    padding: "6px 14px",
    cursor: "pointer",
    fontSize: 11,
    letterSpacing: 2,
    transition: "all 0.15s",
  },
  navBtnActive: { borderColor: C.amber, color: C.amber },
  main: { maxWidth: 760, margin: "0 auto", padding: "24px 16px" },
  todayWrap: { display: "flex", flexDirection: "column", gap: 16 },
  dateLine: {
    display: "flex",
    justifyContent: "space-between",
    alignItems: "center",
    marginBottom: 8,
  },
  dateText: { color: C.textMuted, fontSize: 11, letterSpacing: 2 },
  phaseBadge: {
    fontSize: 10,
    letterSpacing: 2,
    border: "1px solid",
    padding: "3px 8px",
  },
  section: {
    border: `1px solid ${C.border}`,
    background: C.surface,
  },
  sectionLocked: { opacity: 0.7 },
  sectionHeader: {
    display: "flex",
    alignItems: "baseline",
    gap: 12,
    padding: "12px 16px",
    borderBottom: `1px solid ${C.border}`,
    flexWrap: "wrap",
  },
  sectionLabel: { color: C.amber, fontSize: 11, letterSpacing: 3 },
  sectionSub: { color: C.textMuted, fontSize: 11 },
  lockedBadge: {
    marginLeft: "auto",
    fontSize: 9,
    letterSpacing: 2,
    color: C.textDim,
    border: `1px solid ${C.textDim}`,
    padding: "2px 6px",
  },
  sectionBody: { padding: "16px" },
  grid2: { display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12, marginBottom: 12 },
  grid3: { display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12 },
  fieldWrap: { marginBottom: 12 },
  fieldLabel: {
    display: "block",
    color: C.textMuted,
    fontSize: 10,
    letterSpacing: 2,
    marginBottom: 6,
  },
  input: {
    width: "100%",
    background: C.bg,
    border: `1px solid ${C.border}`,
    color: C.text,
    padding: "8px 10px",
    fontSize: 13,
    fontFamily: "'Courier New', monospace",
    outline: "none",
    boxSizing: "border-box",
  },
  inputLocked: { opacity: 0.6, cursor: "not-allowed" },
  checkWrap: {
    display: "flex",
    alignItems: "center",
    gap: 10,
    cursor: "pointer",
    marginBottom: 12,
    userSelect: "none",
  },
  checkRow: { display: "flex", flexWrap: "wrap", marginTop: 4 },
  checkbox: { color: C.textMuted, fontSize: 16 },
  checkboxChecked: { color: C.amber },
  checkLabel: { color: C.textMuted, fontSize: 12 },
  alignRow: { display: "flex", gap: 8, marginTop: 6 },
  alignBtn: {
    background: "none",
    border: `1px solid ${C.border}`,
    color: C.textMuted,
    padding: "6px 12px",
    cursor: "pointer",
    fontSize: 11,
    letterSpacing: 1,
    fontFamily: "'Courier New', monospace",
  },
  alignBtnActive: { borderColor: C.amber, color: C.amber, background: C.amberDim },
  actionBtn: {
    background: "none",
    border: `1px solid ${C.amber}`,
    color: C.amber,
    padding: "10px 24px",
    cursor: "pointer",
    fontSize: 11,
    letterSpacing: 2,
    marginTop: 8,
    fontFamily: "'Courier New', monospace",
    width: "100%",
    transition: "all 0.15s",
  },
  actionBtnConfirm: { borderColor: C.green, color: C.green },
  summaryTable: { display: "flex", flexDirection: "column", gap: 2 },
  summaryHeader: {
    display: "grid",
    gridTemplateColumns: "2fr 1fr 1fr 1fr",
    color: C.textMuted,
    fontSize: 10,
    letterSpacing: 2,
    paddingBottom: 8,
    borderBottom: `1px solid ${C.border}`,
  },
  summaryRow: {
    display: "grid",
    gridTemplateColumns: "2fr 1fr 1fr 1fr",
    padding: "6px 0",
    borderBottom: `1px solid ${C.border}`,
  },
  summaryLabel: { color: C.text },
  summaryNum: { color: C.text, fontWeight: "bold" },
  logWrap: { display: "flex", flexDirection: "column", gap: 8 },
  logCard: { border: `1px solid ${C.border}`, background: C.surface },
  logCardTop: {
    display: "flex",
    alignItems: "center",
    gap: 16,
    padding: "12px 16px",
    cursor: "pointer",
    flexWrap: "wrap",
  },
  logCardLeft: { display: "flex", flexDirection: "column", gap: 4, minWidth: 120 },
  logDate: { color: C.amber, fontSize: 12, letterSpacing: 1 },
  logNiche: { color: C.textMuted, fontSize: 11 },
  logMetrics: { display: "flex", gap: 8, flex: 1, flexWrap: "wrap" },
  logToggle: { color: C.textMuted, marginLeft: "auto" },
  logExpand: { padding: "12px 16px", borderTop: `1px solid ${C.border}` },
  reviewLine: { display: "flex", gap: 12, marginBottom: 8, alignItems: "flex-start" },
  reviewKey: { color: C.amber, fontSize: 10, letterSpacing: 2, minWidth: 70, paddingTop: 1 },
  reviewVal: { color: C.text, fontSize: 12, lineHeight: 1.5 },
  emailMetricsEdit: { marginTop: 12, paddingTop: 12, borderTop: `1px solid ${C.border}` },
  emailMetricsLabel: { color: C.textMuted, fontSize: 10, letterSpacing: 2, display: "block", marginBottom: 12 },
  saveBtn: {
    background: "none",
    border: `1px solid ${C.blue}`,
    color: C.blue,
    padding: "8px 16px",
    cursor: "pointer",
    fontSize: 11,
    letterSpacing: 2,
    marginTop: 12,
    fontFamily: "'Courier New', monospace",
  },
  chip: {
    display: "flex",
    flexDirection: "column",
    alignItems: "center",
    border: `1px solid ${C.border}`,
    padding: "4px 8px",
    minWidth: 44,
  },
  chipAccent: { borderColor: C.purple + "66" },
  chipLabel: { color: C.textMuted, fontSize: 9, letterSpacing: 1 },
  chipValue: { color: C.text, fontSize: 13, fontWeight: "bold" },
  metricsWrap: { display: "flex", flexDirection: "column", gap: 16 },
  kpiRow: { display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12 },
  kpiCard: {
    border: `1px solid ${C.border}`,
    background: C.surface,
    padding: "16px",
    display: "flex",
    flexDirection: "column",
    gap: 4,
  },
  kpiValue: { color: C.amber, fontSize: 28, fontWeight: "bold", letterSpacing: 1 },
  kpiLabel: { color: C.text, fontSize: 11, letterSpacing: 1 },
  kpiSub: { color: C.textMuted, fontSize: 10 },
  funnelSection: {
    border: `1px solid ${C.border}`,
    background: C.surface,
    padding: "16px",
  },
  funnelTitle: { color: C.amber, fontSize: 10, letterSpacing: 3, display: "block", marginBottom: 16 },
  funnelRow: { display: "flex", alignItems: "center", gap: 12, marginBottom: 10 },
  funnelLabel: { color: C.textMuted, fontSize: 11, minWidth: 130 },
  funnelTrack: { flex: 1, height: 8, background: C.border },
  funnelFill: { height: "100%", transition: "width 0.3s", minWidth: 2 },
  funnelNum: { color: C.text, fontSize: 12, minWidth: 30, textAlign: "right" },
  conversionSection: {
    border: `1px solid ${C.border}`,
    background: C.surface,
    padding: "16px",
  },
  convGrid: { display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 12, marginTop: 12 },
  convCell: {
    border: `1px solid ${C.border}`,
    padding: "12px",
    display: "flex",
    flexDirection: "column",
    gap: 4,
  },
  convValue: { color: C.amber, fontSize: 22, fontWeight: "bold" },
  convLabel: { color: C.textMuted, fontSize: 10, letterSpacing: 1 },
  trendSection: {
    border: `1px solid ${C.border}`,
    background: C.surface,
    padding: "16px",
  },
  spark: { width: "100%", height: 60, display: "block", marginTop: 12 },
  empty: {
    display: "flex",
    flexDirection: "column",
    alignItems: "center",
    justifyContent: "center",
    padding: 60,
    gap: 16,
  },
  emptyIcon: { color: C.border, fontSize: 40 },
  emptyText: { color: C.textMuted, fontSize: 12, textAlign: "center" },
};
