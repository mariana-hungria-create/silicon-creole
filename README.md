# **Algorithmic Creolization: Scientific Workbench**

## **Technical Documentation & Deployment Guide**

**1. Overview**

This is a client-side, single-file simulation engine built to model emergent communication protocols in Multi-Agent Systems (MAS). It serves as an isomorphism between Sociolinguistics (Creole formation) and AI Safety (Alignment convergence).

**2. Technical Stack**

Core: Vanilla JavaScript (ES6+).

Rendering: HTML5 Canvas API (2D Context).

Styling: Tailwind CSS (via CDN) + Lucide Icons.

No Build Step: The file is self-contained. It requires no Node.js, Python, or server backend.

**3. Key Algorithms**

**A. Deterministic RNG (Mulberry32)**

In Scientific Mode, standard Math.random() is replaced by a seedable PRNG (Mulberry32). This allows for strictly reproducible experiments.

Usage: Set the seed in the UI. Running the same seed with the same parameters guarantees the exact same agent trajectories.

**B. Spatial Hashing (Optimization)**

In Scientific Mode, agent interactions are $O(N)$.

Implementation: The canvas is divided into a grid of cells (GRID_CELL_SIZE = 40).

Lookup: Agents only check for neighbors within adjacent grid cells $(3 \times 3 \text{ block})$.

Benefit: Allows scaling population from $N=50$ to $N=800$ without frame drops.

**C. Learning Rule (Information Bottleneck)**

Agents update confidence based on a modified Reinforcement Learning rule:


$$C_{t+1} = C_t + \alpha \cdot (1 + P) \cdot \lambda$$


Where:

$C$: Confidence (0.0 to 1.0).

$\alpha$: Base Learning Rate.

$P$: Selection Pressure.

$\lambda$: Plasticity (function of Agent Age).

**4. Deployment**

Local: Simply open ai_studio_code_fixed.html in any modern web browser (Chrome, Firefox, Edge, Safari).

Web: Upload the single .html file to GitHub Pages, Netlify, or any static file host.

**5. Troubleshooting**

"Simulation Crashed" in Log: * The loop is wrapped in a try...catch block. Check the visual log in the bottom right for the specific error message.

Common cause: Changing modes rapidly while the loop is processing a frame. Click "Reset" to clear state.

Agents Disappear: * If the browser window is resized to 0 width (e.g., minimized) during initialization, agents spawn at (0,0).

Fix: Refresh the page or click "Reset" after maximizing the window.

**6. License**

MIT License. Free for educational and research use.
