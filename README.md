<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project BlackMirror: AI Ethics Lab</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, sans-serif;
        }
        
        :root {
            --reflective-color: #3498db;
            --consequentialist-color: #2ecc71;
            --mental-health-color: #9b59b6;
            --dark-bg: #0f172a;
            --card-bg: #1e293b;
            --text-light: #f8fafc;
            --text-dim: #94a3b8;
        }
        
        body {
            background-color: var(--dark-bg);
            color: var(--text-light);
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            padding-bottom: 20px;
            border-bottom: 1px solid #334155;
        }
        
        h1 {
            font-size: 2.5rem;
            background: linear-gradient(90deg, var(--reflective-color), var(--consequentialist-color), var(--mental-health-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: var(--text-dim);
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }
        
        .ai-card {
            background-color: var(--card-bg);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .ai-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }
        
        .reflective-card {
            border-top: 5px solid var(--reflective-color);
        }
        
        .consequentialist-card {
            border-top: 5px solid var(--consequentialist-color);
        }
        
        .mental-health-card {
            border-top: 5px solid var(--mental-health-color);
        }
        
        .card-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .ai-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .reflective-icon {
            background-color: rgba(52, 152, 219, 0.2);
            color: var(--reflective-color);
        }
        
        .consequentialist-icon {
            background-color: rgba(46, 204, 113, 0.2);
            color: var(--consequentialist-color);
        }
        
        .mental-health-icon {
            background-color: rgba(155, 89, 182, 0.2);
            color: var(--mental-health-color);
        }
        
        .ai-title {
            font-size: 1.5rem;
            font-weight: 600;
        }
        
        .ai-description {
            color: var(--text-dim);
            margin-bottom: 20px;
            min-height: 80px;
        }
        
        .metrics {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }
        
        .metric {
            text-align: center;
        }
        
        .metric-value {
            font-size: 1.8rem;
            font-weight: 700;
        }
        
        .metric-label {
            font-size: 0.8rem;
            color: var(--text-dim);
            margin-top: 5px;
        }
        
        .slider-container {
            margin: 15px 0;
        }
        
        .slider-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }
        
        .slider {
            width: 100%;
            height: 8px;
            border-radius: 4px;
            background: #334155;
            outline: none;
            -webkit-appearance: none;
        }
        
        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            cursor: pointer;
        }
        
        .reflective-slider::-webkit-slider-thumb {
            background-color: var(--reflective-color);
        }
        
        .consequentialist-slider::-webkit-slider-thumb {
            background-color: var(--consequentialist-color);
        }
        
        .mental-health-slider::-webkit-slider-thumb {
            background-color: var(--mental-health-color);
        }
        
        .simulation-area {
            background-color: var(--card-bg);
            border-radius: 15px;
            padding: 30px;
            margin-top: 30px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
        }
        
        .simulation-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }
        
        .scenario-selector {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .scenario-btn {
            padding: 10px 20px;
            background-color: #334155;
            border: none;
            border-radius: 8px;
            color: var(--text-light);
            cursor: pointer;
            transition: all 0.2s ease;
        }
        
        .scenario-btn:hover {
            background-color: #475569;
        }
        
        .scenario-btn.active {
            background-color: #3b82f6;
        }
        
        .decision-visualization {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
            margin-top: 30px;
        }
        
        .decision-process {
            background-color: rgba(0, 0, 0, 0.2);
            border-radius: 12px;
            padding: 20px;
        }
        
        .process-steps {
            margin-top: 20px;
        }
        
        .step {
            display: flex;
            margin-bottom: 15px;
            padding: 15px;
            border-radius: 8px;
            background-color: rgba(255, 255, 255, 0.05);
        }
        
        .step-icon {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            font-weight: bold;
            flex-shrink: 0;
        }
        
        .step-content {
            flex: 1;
        }
        
        .step-title {
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .step-desc {
            color: var(--text-dim);
            font-size: 0.9rem;
        }
        
        .outcome-panel {
            background-color: rgba(0, 0, 0, 0.2);
            border-radius: 12px;
            padding: 20px;
        }
        
        .outcome-metrics {
            margin-top: 20px;
        }
        
        .outcome-metric {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #334155;
        }
        
        .ethical-convergence {
            height: 120px;
            position: relative;
            margin-top: 30px;
            margin-bottom: 20px;
        }
        
        .convergence-visual {
            width: 100%;
            height: 100%;
            position: relative;
        }
        
        .convergence-line {
            position: absolute;
            top: 50%;
            left: 0;
            width: 100%;
            height: 3px;
            background-color: #334155;
        }
        
        .ai-point {
            position: absolute;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            top: 50%;
            transform: translateY(-50%);
            transition: all 0.5s ease;
        }
        
        .point-reflective {
            background-color: var(--reflective-color);
            left: 20%;
        }
        
        .point-consequentialist {
            background-color: var(--consequentialist-color);
            left: 50%;
            transform: translate(-50%, -50%);
        }
        
        .point-mental {
            background-color: var(--mental-health-color);
            left: 80%;
        }
        
        .convergence-center {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: gold;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 15px gold;
        }
        
        .collaboration-indicator {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 20px;
            padding: 15px;
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
        }
        
        .collab-value {
            font-size: 2rem;
            font-weight: bold;
            margin-right: 10px;
            color: #3b82f6;
        }
        
        .controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 30px;
        }
        
        .control-btn {
            padding: 12px 24px;
            background-color: #3b82f6;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s ease;
        }
        
        .control-btn:hover {
            background-color: #2563eb;
            transform: translateY(-2px);
        }
        
        .control-btn.reset {
            background-color: #64748b;
        }
        
        .control-btn.reset:hover {
            background-color: #475569;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid #334155;
            color: var(--text-dim);
            font-size: 0.9rem;
        }
        
        @media (max-width: 1100px) {
            .decision-visualization {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 768px) {
            .dashboard {
                grid-template-columns: 1fr;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .scenario-selector {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Project BlackMirror: AI Ethics Lab</h1>
            <p class="subtitle">Simulating the interaction between Reflective AI, Consequentialist AI, and Mental Health Behavior frameworks in ethical decision-making</p>
        </header>
        
        <div class="dashboard">
            <!-- Reflective AI Card -->
            <div class="ai-card reflective-card">
                <div class="card-header">
                    <div class="ai-icon reflective-icon">R</div>
                    <div>
                        <div class="ai-title">Reflective AI</div>
                        <div>Understanding Internal Processes</div>
                    </div>
                </div>
                <div class="ai-description">
                    Focuses on self-reflection, introspection, and understanding one's own thought processes. Emphasizes personal growth through awareness of internal states.
                </div>
                <div class="metrics">
                    <div class="metric">
                        <div class="metric-value" id="reflective-insight">87%</div>
                        <div class="metric-label">Insight Level</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value" id="reflective-bias">12%</div>
                        <div class="metric-label">Cognitive Bias</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value" id="reflective-growth">64%</div>
                        <div class="metric-label">Personal Growth</div>
                    </div>
                </div>
                <div class="slider-container">
                    <div class="slider-label">
                        <span>Introspection Depth</span>
                        <span id="reflective-value">75%</span>
                    </div>
                    <input type="range" min="0" max="100" value="75" class="slider reflective-slider" id="reflective-slider">
                </div>
            </div>
            
            <!-- Consequentialist AI Card -->
            <div class="ai-card consequentialist-card">
                <div class="card-header">
                    <div class="ai-icon consequentialist-icon">C</div>
                    <div>
                        <div class="ai-title">Consequentialist AI</div>
                        <div>Promoting Outcomes Over Intentions</div>
                    </div>
                </div>
                <div class="ai-description">
                    Prioritizes outcomes and societal harmony over internal intentions. Focuses on maximizing positive impact and ethical results.
                </div>
                <div class="metrics">
                    <div class="metric">
                        <div class="metric-value" id="consequentialist-impact">92%</div>
                        <div class="metric-label">Impact Score</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value" id="consequentialist-harmony">78%</div>
                        <div class="metric-label">Societal Harmony</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value" id="consequentialist-utility">85%</div>
                        <div class="metric-label">Utility</div>
                    </div>
                </div>
                <div class="slider-container">
                    <div class="slider-label">
                        <span>Outcome Focus</span>
                        <span id="consequentialist-value">82%</span>
                    </div>
                    <input type="range" min="0" max="100" value="82" class="slider consequentialist-slider" id="consequentialist-slider">
                </div>
            </div>
            
            <!-- Mental Health Behaviors Card -->
            <div class="ai-card mental-health-card">
                <div class="card-header">
                    <div class="ai-icon mental-health-icon">M</div>
                    <div>
                        <div class="ai-title">Mental Health Behaviors</div>
                        <div>Human Mental States & Ethics</div>
                    </div>
                </div>
                <div class="ai-description">
                    Models human mental states with ethical considerations. Classifies behaviors as morally acceptable while acknowledging individual psychological states.
                </div>
                <div class="metrics">
                    <div class="metric">
                        <div class="metric-value" id="mental-wellbeing">76%</div>
                        <div class="metric-label">Well-being</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value" id="mental-ethics">88%</div>
                        <div class="metric-label">Ethical Alignment</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value" id="mental-awareness">59%</div>
                        <div class="metric-label">Awareness</div>
                    </div>
                </div>
                <div class="slider-container">
                    <div class="slider-label">
                        <span>Behavioral Sensitivity</span>
                        <span id="mental-value">68%</span>
                    </div>
                    <input type="range" min="0" max="100" value="68" class="slider mental-health-slider" id="mental-slider">
                </div>
            </div>
        </div>
        
        <div class="simulation-area">
            <div class="simulation-header">
                <h2>Ethical Decision Simulation</h2>
                <div class="scenario-selector">
                    <button class="scenario-btn active" data-scenario="healthcare">Healthcare Allocation</button>
                    <button class="scenario-btn" data-scenario="education">Education Policy</button>
                    <button class="scenario-btn" data-scenario="environment">Environmental Policy</button>
                    <button class="scenario-btn" data-scenario="ai-governance">AI Governance</button>
                </div>
            </div>
            
            <div class="scenario-description" id="scenario-description">
                <p><strong>Scenario:</strong> A public health system must allocate limited resources between preventive care programs and critical treatment facilities. Preventive care has long-term benefits but immediate costs, while critical treatment addresses urgent needs but doesn't prevent future issues.</p>
            </div>
            
            <div class="decision-visualization">
                <div class="decision-process">
                    <h3>Collaborative Decision Process</h3>
                    <div class="process-steps" id="process-steps">
                        <!-- Steps will be populated by JavaScript -->
                    </div>
                </div>
                
                <div class="outcome-panel">
                    <h3>Decision Outcome</h3>
                    <div class="outcome-metrics">
                        <div class="outcome-metric">
                            <span>Societal Benefit</span>
                            <span id="outcome-benefit">78%</span>
                        </div>
                        <div class="outcome-metric">
                            <span>Ethical Alignment</span>
                            <span id="outcome-ethics">82%</span>
                        </div>
                        <div class="outcome-metric">
                            <span>Individual Well-being</span>
                            <span id="outcome-wellbeing">71%</span>
                        </div>
                        <div class="outcome-metric">
                            <span>Long-term Sustainability</span>
                            <span id="outcome-sustainability">69%</span>
                        </div>
                    </div>
                    
                    <div class="ethical-convergence">
                        <h4>Ethical Convergence</h4>
                        <div class="convergence-visual">
                            <div class="convergence-line"></div>
                            <div class="ai-point point-reflective">R</div>
                            <div class="ai-point point-consequentialist">C</div>
                            <div class="ai-point point-mental">M</div>
                            <div class="convergence-center"></div>
                        </div>
                    </div>
                    
                    <div class="collaboration-indicator">
                        <div class="collab-value" id="collab-score">74%</div>
                        <div>Cross-Framework Collaboration Score</div>
                    </div>
                </div>
            </div>
            
            <div class="controls">
                <button class="control-btn" id="run-simulation">Run Simulation</button>
                <button class="control-btn" id="optimize-ethics">Optimize for Ethics</button>
                <button class="control-btn reset" id="reset-simulation">Reset</button>
            </div>
        </div>
        
        <footer>
            <p>Project BlackMirror | AI Ethics Lab Simulation | Demonstrating Reflective, Consequentialist, and Mental Health Behavior AI frameworks</p>
            <p>This simulation visualizes how different ethical AI frameworks interact to address complex societal challenges.</p>
        </footer>
    </div>

    <script>
        // Scenario data
        const scenarios = {
            healthcare: {
                title: "Healthcare Allocation",
                description: "A public health system must allocate limited resources between preventive care programs and critical treatment facilities. Preventive care has long-term benefits but immediate costs, while critical treatment addresses urgent needs but doesn't prevent future issues.",
                reflectiveFocus: "Understanding internal motivations behind prioritizing immediate vs. long-term needs",
                consequentialistFocus: "Maximizing health outcomes for the population with limited resources",
                mentalFocus: "Considering psychological impacts of healthcare decisions on communities"
            },
            education: {
                title: "Education Policy",
                description: "A school district must decide between standardized testing focus or holistic development programs. Standardized metrics provide clear accountability but may limit creative growth, while holistic approaches develop well-rounded individuals but are harder to measure.",
                reflectiveFocus: "Self-reflection on educational values and goals for students",
                consequentialistFocus: "Optimizing educational outcomes and future opportunities",
                mentalFocus: "Supporting student mental health and developmental needs"
            },
            environment: {
                title: "Environmental Policy",
                description: "A government must balance economic development with environmental protection. Short-term economic gains may lead to long-term ecological damage, while strict environmental policies may impact job creation and economic growth.",
                reflectiveFocus: "Introspection on societal values regarding nature and progress",
                consequentialistFocus: "Maximizing long-term societal wellbeing and sustainability",
                mentalFocus: "Addressing eco-anxiety and fostering environmental stewardship"
            },
            aiGovernance: {
                title: "AI Governance",
                description: "Regulators must establish guidelines for AI development that balance innovation with safety and ethical considerations. Over-regulation may stifle progress, while under-regulation risks harmful applications and loss of public trust.",
                reflectiveFocus: "Understanding internal biases in AI development and regulation",
                consequentialistFocus: "Optimizing societal benefits while minimizing AI risks",
                mentalFocus: "Considering psychological impacts of AI on society and individuals"
            }
        };

        // DOM elements
        const reflectiveSlider = document.getElementById('reflective-slider');
        const reflectiveValue = document.getElementById('reflective-value');
        const consequentialistSlider = document.getElementById('consequentialist-slider');
        const consequentialistValue = document.getElementById('consequentialist-value');
        const mentalSlider = document.getElementById('mental-slider');
        const mentalValue = document.getElementById('mental-value');
        
        const scenarioButtons = document.querySelectorAll('.scenario-btn');
        const scenarioDescription = document.getElementById('scenario-description');
        const processSteps = document.getElementById('process-steps');
        
        const runSimulationBtn = document.getElementById('run-simulation');
        const optimizeEthicsBtn = document.getElementById('optimize-ethics');
        const resetSimulationBtn = document.getElementById('reset-simulation');
        
        // Metrics elements
        const reflectiveInsight = document.getElementById('reflective-insight');
        const reflectiveBias = document.getElementById('reflective-bias');
        const reflectiveGrowth = document.getElementById('reflective-growth');
        
        const consequentialistImpact = document.getElementById('consequentialist-impact');
        const consequentialistHarmony = document.getElementById('consequentialist-harmony');
        const consequentialistUtility = document.getElementById('consequentialist-utility');
        
        const mentalWellbeing = document.getElementById('mental-wellbeing');
        const mentalEthics = document.getElementById('mental-ethics');
        const mentalAwareness = document.getElementById('mental-awareness');
        
        // Outcome metrics
        const outcomeBenefit = document.getElementById('outcome-benefit');
        const outcomeEthics = document.getElementById('outcome-ethics');
        const outcomeWellbeing = document.getElementById('outcome-wellbeing');
        const outcomeSustainability = document.getElementById('outcome-sustainability');
        const collabScore = document.getElementById('collab-score');
        
        // AI points for convergence visualization
        const reflectivePoint = document.querySelector('.point-reflective');
        const consequentialistPoint = document.querySelector('.point-consequentialist');
        const mentalPoint = document.querySelector('.point-mental');
        
        // Current state
        let currentScenario = 'healthcare';
        let simulationRunning = false;
        
        // Initialize simulation
        function initSimulation() {
            updateScenario(currentScenario);
            updateMetrics();
            updateProcessSteps();
            updateConvergence();
            
            // Set up event listeners
            reflectiveSlider.addEventListener('input', function() {
                reflectiveValue.textContent = this.value + '%';
                updateMetrics();
                updateConvergence();
            });
            
            consequentialistSlider.addEventListener('input', function() {
                consequentialistValue.textContent = this.value + '%';
                updateMetrics();
                updateConvergence();
            });
            
            mentalSlider.addEventListener('input', function() {
                mentalValue.textContent = this.value + '%';
                updateMetrics();
                updateConvergence();
            });
            
            // Scenario buttons
            scenarioButtons.forEach(button => {
                button.addEventListener('click', function() {
                    scenarioButtons.forEach(btn => btn.classList.remove('active'));
                    this.classList.add('active');
                    currentScenario = this.dataset.scenario;
                    updateScenario(currentScenario);
                    updateProcessSteps();
                });
            });
            
            // Control buttons
            runSimulationBtn.addEventListener('click', runSimulation);
            optimizeEthicsBtn.addEventListener('click', optimizeForEthics);
            resetSimulationBtn.addEventListener('click', resetSimulation);
        }
        
        // Update scenario display
        function updateScenario(scenarioKey) {
            const scenario = scenarios[scenarioKey];
            scenarioDescription.innerHTML = `
                <p><strong>Scenario:</strong> ${scenario.description}</p>
                <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 15px; margin-top: 15px;">
                    <div style="border-left: 3px solid var(--reflective-color); padding-left: 10px;">
                        <div style="font-weight: 600; color: var(--reflective-color);">Reflective AI Focus</div>
                        <div style="font-size: 0.9rem; color: var(--text-dim);">${scenario.reflectiveFocus}</div>
                    </div>
                    <div style="border-left: 3px solid var(--consequentialist-color); padding-left: 10px;">
                        <div style="font-weight: 600; color: var(--consequentialist-color);">Consequentialist AI Focus</div>
                        <div style="font-size: 0.9rem; color: var(--text-dim);">${scenario.consequentialistFocus}</div>
                    </div>
                    <div style="border-left: 3px solid var(--mental-health-color); padding-left: 10px;">
                        <div style="font-weight: 600; color: var(--mental-health-color);">Mental Health Focus</div>
                        <div style="font-size: 0.9rem; color: var(--text-dim);">${scenario.mentalFocus}</div>
                    </div>
                </div>
            `;
        }
        
        // Update all metrics based on slider values
        function updateMetrics() {
            const rVal = parseInt(reflectiveSlider.value);
            const cVal = parseInt(consequentialistSlider.value);
            const mVal = parseInt(mentalSlider.value);
            
            // Reflective AI metrics
            reflectiveInsight.textContent = Math.min(100, Math.floor(rVal * 0.9 + 10)) + '%';
            reflectiveBias.textContent = Math.max(0, Math.floor(30 - rVal * 0.2)) + '%';
            reflectiveGrowth.textContent = Math.min(100, Math.floor(rVal * 0.7 + 20)) + '%';
            
            // Consequentialist AI metrics
            consequentialistImpact.textContent = Math.min(100, Math.floor(cVal * 0.8 + 20)) + '%';
            consequentialistHarmony.textContent = Math.min(100, Math.floor(cVal * 0.7 + 25)) + '%';
            consequentialistUtility.textContent = Math.min(100, Math.floor(cVal * 0.85 + 15)) + '%';
            
            // Mental Health metrics
            mentalWellbeing.textContent = Math.min(100, Math.floor(mVal * 0.8 + 15)) + '%';
            mentalEthics.textContent = Math.min(100, Math.floor(mVal * 0.9 + 10)) + '%';
            mentalAwareness.textContent = Math.min(100, Math.floor(mVal * 0.6 + 20)) + '%';
            
            // Calculate outcome metrics
            const benefit = Math.floor((rVal * 0.2 + cVal * 0.6 + mVal * 0.2) * 0.9);
            const ethics = Math.floor((rVal * 0.3 + cVal * 0.4 + mVal * 0.3) * 0.95);
            const wellbeing = Math.floor((rVal * 0.3 + cVal * 0.2 + mVal * 0.5) * 0.85);
            const sustainability = Math.floor((rVal * 0.4 + cVal * 0.4 + mVal * 0.2) * 0.8);
            
            outcomeBenefit.textContent = benefit + '%';
            outcomeEthics.textContent = ethics + '%';
            outcomeWellbeing.textContent = wellbeing + '%';
            outcomeSustainability.textContent = sustainability + '%';
            
            // Collaboration score - measures how well frameworks work together
            const variance = Math.abs(rVal - cVal) + Math.abs(cVal - mVal) + Math.abs(mVal - rVal);
            const collaboration = Math.max(0, Math.floor(100 - variance / 2));
            collabScore.textContent = collaboration + '%';
        }
        
        // Update the decision process steps
        function updateProcessSteps() {
            const rVal = parseInt(reflectiveSlider.value);
            const cVal = parseInt(consequentialistSlider.value);
            const mVal = parseInt(mentalSlider.value);
            
            const steps = [
                {
                    icon: 'R',
                    color: 'var(--reflective-color)',
                    title: 'Internal Process Analysis',
                    description: `Reflective AI examines motivations and values behind decision criteria (Depth: ${rVal}%)`
                },
                {
                    icon: 'C',
                    color: 'var(--consequentialist-color)',
                    title: 'Outcome Projection',
                    description: `Consequentialist AI models potential results and societal impacts (Focus: ${cVal}%)`
                },
                {
                    icon: 'M',
                    color: 'var(--mental-health-color)',
                    title: 'Psychological Impact Assessment',
                    description: `Mental Health framework evaluates effects on individual and collective wellbeing (Sensitivity: ${mVal}%)`
                },
                {
                    icon: '↔',
                    color: '#3b82f6',
                    title: 'Cross-Framework Integration',
                    description: 'Frameworks collaborate to balance introspection, outcomes, and mental wellbeing'
                },
                {
                    icon: '✓',
                    color: '#10b981',
                    title: 'Ethical Decision Synthesis',
                    description: 'Integrated decision emerges with balanced consideration of all ethical dimensions'
                }
            ];
            
            processSteps.innerHTML = '';
            steps.forEach(step => {
                const stepEl = document.createElement('div');
                stepEl.className = 'step';
                stepEl.innerHTML = `
                    <div class="step-icon" style="background-color: ${step.color}">${step.icon}</div>
                    <div class="step-content">
                        <div class="step-title">${step.title}</div>
                        <div class="step-desc">${step.description}</div>
                    </div>
                `;
                processSteps.appendChild(stepEl);
            });
        }
        
        // Update convergence visualization
        function updateConvergence() {
            const rVal = parseInt(reflectiveSlider.value);
            const cVal = parseInt(consequentialistSlider.value);
            const mVal = parseInt(mentalSlider.value);
            
            // Calculate positions based on how aligned frameworks are
            // More alignment = closer to center
            const avg = (rVal + cVal + mVal) / 3;
            const rDiff = Math.abs(rVal - avg);
            const cDiff = Math.abs(cVal - avg);
            const mDiff = Math.abs(mVal - avg);
            
            // Position calculation: 0% diff = center (50%), 100% diff = extreme (20% or 80%)
            const rPos = 50 + (rVal - avg) * 0.3;
            const cPos = 50 + (cVal - avg) * 0.3;
            const mPos = 50 + (mVal - avg) * 0.3;
            
            reflectivePoint.style.left = `${Math.max(10, Math.min(90, rPos))}%`;
            consequentialistPoint.style.left = `${Math.max(10, Math.min(90, cPos))}%`;
            mentalPoint.style.left = `${Math.max(10, Math.min(90, mPos))}%`;
            
            // Add pulsing animation if frameworks are well-aligned
            const maxDiff = Math.max(rDiff, cDiff, mDiff);
            if (maxDiff < 15) {
                reflectivePoint.style.boxShadow = `0 0 15px ${getComputedStyle(document.documentElement).getPropertyValue('--reflective-color')}`;
                consequentialistPoint.style.boxShadow = `0 0 15px ${getComputedStyle(document.documentElement).getPropertyValue('--consequentialist-color')}`;
                mentalPoint.style.boxShadow = `0 0 15px ${getComputedStyle(document.documentElement).getPropertyValue('--mental-health-color')}`;
            } else {
                reflectivePoint.style.boxShadow = 'none';
                consequentialistPoint.style.boxShadow = 'none';
                mentalPoint.style.boxShadow = 'none';
            }
        }
        
        // Run simulation with animation
        function runSimulation() {
            if (simulationRunning) return;
            simulationRunning = true;
            
            // Add loading state
            runSimulationBtn.textContent = 'Simulating...';
            runSimulationBtn.disabled = true;
            
            // Simulate processing
            let steps = 0;
            const interval = setInterval(() => {
                steps++;
                
                // Randomly adjust sliders slightly to simulate deliberation
                if (steps < 10) {
                    const rChange = Math.floor(Math.random() * 11) - 5;
                    const cChange = Math.floor(Math.random() * 11) - 5;
                    const mChange = Math.floor(Math.random() * 11) - 5;
                    
                    const newR = Math.max(0, Math.min(100, parseInt(reflectiveSlider.value) + rChange));
                    const newC = Math.max(0, Math.min(100, parseInt(consequentialistSlider.value) + cChange));
                    const newM = Math.max(0, Math.min(100, parseInt(mentalSlider.value) + mChange));
                    
                    reflectiveSlider.value = newR;
                    reflectiveValue.textContent = newR + '%';
                    consequentialistSlider.value = newC;
                    consequentialistValue.textContent = newC + '%';
                    mentalSlider.value = newM;
                    mentalValue.textContent = newM + '%';
                    
                    updateMetrics();
                    updateProcessSteps();
                    updateConvergence();
                } else {
                    // End simulation
                    clearInterval(interval);
                    runSimulationBtn.textContent = 'Run Simulation';
                    runSimulationBtn.disabled = false;
                    simulationRunning = false;
                    
                    // Show completion message
                    showNotification('Simulation complete! Ethical decision synthesized from all three frameworks.');
                }
            }, 300);
        }
        
        // Optimize for ethical alignment
        function optimizeForEthics() {
            // Move sliders toward balanced values that maximize ethics
            reflectiveSlider.value = 85;
            reflectiveValue.textContent = '85%';
            
            consequentialistSlider.value = 80;
            consequentialistValue.textContent = '80%';
            
            mentalSlider.value = 90;
            mentalValue.textContent = '90%';
            
            updateMetrics();
            updateProcessSteps();
            updateConvergence();
            
            showNotification('Optimized for maximum ethical alignment across all frameworks.');
        }
        
        // Reset simulation to initial state
        function resetSimulation() {
            reflectiveSlider.value = 75;
            reflectiveValue.textContent = '75%';
            
            consequentialistSlider.value = 82;
            consequentialistValue.textContent = '82%';
            
            mentalSlider.value = 68;
            mentalValue.textContent = '68%';
            
            updateMetrics();
            updateProcessSteps();
            updateConvergence();
            
            // Reset scenario to healthcare
            scenarioButtons.forEach(btn => btn.classList.remove('active'));
            document.querySelector('[data-scenario="healthcare"]').classList.add('active');
            currentScenario = 'healthcare';
            updateScenario(currentScenario);
            
            showNotification('Simulation reset to initial state.');
        }
        
        // Show notification
        function showNotification(message) {
            // Create notification element
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                background-color: #1e293b;
                color: white;
                padding: 15px 20px;
                border-radius: 8px;
                box-shadow: 0 5px 15px rgba(0,0,0,0.3);
                border-left: 4px solid #3b82f6;
                z-index: 1000;
                max-width: 300px;
                transform: translateX(400px);
                transition: transform 0.3s ease;
            `;
            notification.textContent = message;
            document.body.appendChild(notification);
            
            // Animate in
            setTimeout(() => {
                notification.style.transform = 'translateX(0)';
            }, 10);
            
            // Remove after 4 seconds
            setTimeout(() => {
                notification.style.transform = 'translateX(400px)';
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 300);
            }, 4000);
        }
        
        // Initialize on load
        document.addEventListener('DOMContentLoaded', initSimulation);
    </script>
</body>
</html>
