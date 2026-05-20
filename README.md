# Lecture Sync Player 🎬🎧

A premium, distraction-free, synchronized dual-media player built for students and educators who need to play separate video and audio tracks in perfect unison.

This is a local-first web application compiled into a single, highly-optimized, self-contained HTML file. No installations, no server requirements, and zero data tracking.

---

## 📖 The Problem & Solution

### The Problem
Some university lecture capture systems or download portals deliver lectures as two separate files:
1. An **MP4 video file** containing the screen capture/board presentation (usually silent).
2. An **MP4/M4A/MP3 audio file** containing the lecturer's voice.

Manually aligning two separate media players and keeping them in sync while pausing, seeking, or changing speed is tedious and practically impossible.

### The Solution
**Lecture Sync Player** solves this by loading both files locally in your browser and binding them together. Through high-frequency alignment, both elements act as a single, unified player.

---

## ✨ Premium Features

*   **Zero Dependencies / Local First:** Everything runs directly inside your browser. Your files never leave your computer.
*   **Unified Custom Controls:**
    *   **Master Play/Pause:** Single play/pause button or Spacebar to control both files instantly.
    *   **Scrubbable Progress Slider:** Precise scrub control mapping the synchronized timeline of both streams.
    *   **Speed Controls:** Instantly speed up or slow down lectures (1×, 1.25×, 1.5×, 1.75×, 2×) in lockstep.
    *   **Buffered Track Display:** Visual indicator of video buffering status.
    *   **Skip Controls:** Dedicated quick skip buttons to jump backward or forward by 10 seconds.
*   **Strict Sync Logic:** Dual synchronization engines:
    *   An active `requestAnimationFrame` loop handles sub-frame temporal alignment.
    *   A secondary buffer blocker halts the faster stream if the other buffers, resuming in unison only when both are ready.
*   **Bilingual Interface (English & Hebrew):** Complete translation including buttons, layouts, status indicators, and notification toasts. Supports native **RTL (Right-to-Left)** formatting with Hebrew font pairing.
*   **Sleek Dark Theme:** Distraction-free interface featuring a futuristic glassmorphic aesthetic, harmonious colors, micro-animations, and keyboard shortcuts.

---

## ⌨️ Keyboard Shortcuts

Speed up your studying with native desktop hotkeys:

| Key | Action |
| :--- | :--- |
| <kbd>Space</kbd> | Play / Pause |
| <kbd>←</kbd> / <kbd>→</kbd> | Seek Backward / Forward 10 seconds |
| <kbd>↑</kbd> / <kbd>↓</kbd> | Increase / Decrease volume |
| <kbd>M</kbd> | Mute / Unmute audio |
| <kbd>F</kbd> | Enter / Exit Fullscreen |

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Zvimarmor/LectureSync.git
cd LectureSync
```

### 2. Run Locally

Since this is a single HTML file, you have two options:

**Option A — Direct open (simplest):**

Simply double-click `index.html` or open it in any modern browser (Chrome, Firefox, Safari, Edge).

**Option B — Local HTTP server (recommended):**

Running through a local server avoids potential browser restrictions on local file access.

Using **Python** (built-in on macOS/Linux):
```bash
# Python 3
python3 -m http.server 8000
```

Using **Node.js**:
```bash
npx -y serve .
```

Then open your browser and navigate to:
```
http://localhost:8000
```

### 3. Load & Play

1.  Click the **Video File** box (or drag & drop) to load the silent video file.
2.  Click the **Audio File** box (or drag & drop) to load the audio file.
3.  Press the **Play** button or hit <kbd>Space</kbd> to start watching — both tracks play in perfect sync!

---

## 🛠 Technical Implementation Details

*   **Single-File Architecture:** The entire app is contained inside one single file (`index.html`) using raw vanilla HTML5, CSS3, and ES6 JavaScript. No framework clutter, zero external package installation, and instantaneous loading.
*   **Double-Lock Synchronization:**
    ```javascript
    function syncTimes() {
      if (isSeeking) return;
      const diff = Math.abs(videoEl.currentTime - audioEl.currentTime);
      if (diff > syncThreshold) {
        audioEl.currentTime = videoEl.currentTime;
      }
    }
    ```
    An animation loop calls this check repeatedly to eliminate drift. If a delay or buffering event occurs, event listeners capture the `waiting` and `canplay` states of both elements to safely freeze playback until coherence is re-established.

---

## 📦 Pushing to your Repository

To initialize, commit, and push this project to your repository, follow these quick terminal commands:

```bash
# Initialize git repository
git init

# Add remote origin
git remote add origin https://github.com/Zvimarmor/LectureSync.git

# Stage all files
git add .

# Create initial commit
git commit -m "Initial commit: Synchronized dual-media player with bilingual UI"

# Set branch name to main
git branch -M main

# Push to your remote
git push -u origin main
```
