# Interface Simulateur Monte Carlo - Module 18

## Description

Interface spécialisée pour le module de simulations Monte Carlo permettant aux actuaires et gestionnaires d'effectuer des projections probabilistes avancées sur l'évolution du régime de retraite.

---

## Prompt IA pour Interface Simulateur Monte Carlo

```
Create a sophisticated Monte Carlo simulation interface for "Waajal Ëlëk" pension management platform, designed for actuaries and financial managers to perform advanced probabilistic projections.

TITLE: "WAAJAL ËLËK - Simulateur Monte Carlo Actuariel"
Subtitle: "Projections Probabilistes et Modélisation Stochastique"

COLOR PALETTE:
Primary Colors:
- Military Green: #0B5345 (main interface elements)
- Analytical Blue: #1F4E79 (data visualization)
- Confidence Green: #27AE60 (positive scenarios)
- Warning Orange: #E67E22 (risk indicators)
- Critical Red: #E74C3C (stress scenarios)
- Neutral Gray: #7F8C8D (baseline projections)

Probabilistic Colors:
- P10 (Pessimistic): #E74C3C with 20% opacity
- P25 (Conservative): #E67E22 with 30% opacity
- P50 (Median): #0B5345 with 100% opacity
- P75 (Optimistic): #27AE60 with 30% opacity
- P90 (Very Optimistic): #27AE60 with 20% opacity

MAIN INTERFACE LAYOUT:

1. HEADER SECTION:
   - Large title "Simulateur Monte Carlo" with subtitle
   - Current simulation status indicator (Running/Completed/Idle)
   - Real-time progress bar when simulations are running
   - Quick action buttons: "Nouvelle Simulation", "Charger Modèle", "Exporter Résultats"

2. CONFIGURATION PANEL (Left Sidebar - 25% width):
   
   SIMULATION PARAMETERS:
   - Number of simulations: Slider (1,000 to 100,000) with current value display
   - Time horizon: Dropdown (5, 10, 15, 20, 25, 30 years)
   - Confidence intervals: Multi-select checkboxes (P10, P25, P50, P75, P90)
   - Random seed: Input field for reproducibility
   
   ECONOMIC ASSUMPTIONS:
   - Inflation rate: Range slider (0% to 10%) with uncertainty bands
   - Economic growth: Input with standard deviation
   - Interest rates: Yield curve builder with drag-and-drop points
   - Market volatility: Percentage slider with historical comparison
   
   DEMOGRAPHIC PARAMETERS:
   - Mortality improvement: Annual percentage with confidence bands
   - New member growth: Growth rate with seasonal adjustments
   - Salary increase assumptions: By grade and experience level
   - Retirement age trends: Distribution parameters
   
   PORTFOLIO ALLOCATION:
   - Asset class weights: Interactive pie chart with drag-to-adjust
   - Expected returns: Input fields with historical benchmarks
   - Correlation matrix: Visual correlation heatmap
   - Rebalancing frequency: Dropdown selection

3. MAIN VISUALIZATION AREA (Center - 50% width):
   
   PRIMARY CHART - Fan Chart Display:
   - Large probabilistic fan chart showing pension fund evolution
   - X-axis: Time (years from current date)
   - Y-axis: Fund value in billions FCFA
   - Multiple probability bands with gradient fill
   - Median line highlighted in bold military green
   - Interactive hover showing exact values and percentiles
   - Zoom and pan functionality for detailed analysis
   
   SCENARIO COMPARISON:
   - Overlay capability for comparing different simulation runs
   - Base case vs. stress scenarios toggle
   - Historical performance overlay option
   - Benchmark comparison (e.g., other pension funds)

4. DETAILED ANALYTICS (Right Panel - 25% width):
   
   SUMMARY STATISTICS:
   - Key metrics in card format:
     * Expected fund value at horizon
     * Probability of underfunding
     * Value at Risk (VaR) at different confidence levels
     * Expected shortfall calculations
   
   DISTRIBUTION ANALYSIS:
   - Histogram of final fund values
   - Box plot showing quartiles and outliers
   - Probability density function overlay
   - Tail risk indicators
   
   SENSITIVITY ANALYSIS:
   - Tornado chart showing parameter sensitivity
   - Monte Carlo convergence diagnostic
   - Correlation analysis results
   - Key driver identification

5. RESULTS SECTION (Bottom Panel):
   
   TABULAR RESULTS:
   - Year-by-year projection table with percentiles
   - Sortable and filterable data grid
   - Export options (Excel, CSV, PDF)
   - Statistical significance indicators
   
   STRESS TESTING RESULTS:
   - Predefined stress scenarios (market crash, high inflation, etc.)
   - Custom stress scenario builder
   - Comparison with regulatory capital requirements
   - Recovery time analysis

INTERACTIVE FEATURES:

1. Real-time Parameter Updates:
   - Live recalculation as parameters change
   - Visual feedback showing impact of changes
   - "What-if" scenario builder with save/load functionality
   - Parameter sensitivity live updates

2. Advanced Filtering:
   - Filter results by scenario characteristics
   - Conditional formatting based on outcomes
   - Drill-down capability to individual simulation paths
   - Custom threshold alerts

3. Collaborative Features:
   - Shared scenario libraries
   - Comments and annotations on results
   - Version control for simulation models
   - Export to presentation formats

TECHNICAL SPECIFICATIONS:

Performance Indicators:
- Simulation speed: "Simulating 50,000 scenarios..."
- Memory usage indicator for large simulations
- CPU utilization gauge during processing
- Estimated completion time countdown

Computing Infrastructure:
- GPU acceleration status indicator
- Distributed computing cluster status
- Cloud resources utilization display
- Historical performance benchmarks

SPECIALIZED ACTUARIAL FEATURES:

1. Liability Matching:
   - Asset-liability correlation analysis
   - Duration matching visualization
   - Immunization strategy testing
   - Convexity risk assessment

2. Regulatory Compliance:
   - OHADA compliance indicators
   - BCEAO capital requirement tracking
   - Regulatory ratio monitoring
   - Stress test compliance dashboard

3. Member Impact Analysis:
   - Individual member impact projections
   - Benefit security probability
   - Contribution adequacy analysis
   - Intergenerational equity metrics

MOBILE ADAPTATIONS:
- Simplified parameter input for mobile devices
- Touch-optimized chart interactions
- Essential metrics priority display
- Offline capability for viewing saved results

ACCESSIBILITY FEATURES:
- Screen reader compatible chart descriptions
- High contrast mode for visually impaired users
- Keyboard navigation for all interactive elements
- Alternative text for all visual elements

ADVANCED ANALYTICS DISPLAY:
- Machine learning model performance indicators
- Prediction accuracy metrics over time
- Model validation results
- Backtesting performance comparison

EXPORT AND REPORTING:
- Automated report generation in French
- Executive summary with key insights
- Technical appendix with methodology
- Interactive dashboard for presentations

OUTPUT: Professional actuarial simulation interface that enables sophisticated probabilistic modeling while remaining intuitive for experienced financial professionals. The interface should inspire confidence in the robustness of the underlying Monte Carlo engine while providing all necessary tools for comprehensive pension fund analysis.
```