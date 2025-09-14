# Interface Module Actuariel - Calculs et Provisions

## Description

Interface spécialisée pour les actuaires permettant de gérer tous les aspects techniques du régime : calculs de provisions, tables de mortalité, paramètres actuariels et validation des hypothèses.

---

## Prompt IA pour Interface Module Actuariel

```
Create a comprehensive actuarial management interface for "Waajal Ëlëk" military pension platform, designed for professional actuaries to manage technical reserves, mortality tables, and actuarial assumptions.

TITLE: "WAAJAL ËLËK - Console Actuarielle Professionnelle"
Subtitle: "Gestion des Provisions Techniques et Paramètres Actuariels"

COLOR PALETTE:
Primary Actuarial Colors:
- Actuarial Blue: #1F4E79 (primary interface color)
- Military Green: #0B5345 (Waajal Ëlëk brand)
- Reserve Gold: #D4AF37 (provisions and reserves)
- Technical Gray: #5D6D7E (technical data)
- Validation Green: #27AE60 (validated calculations)
- Warning Orange: #E67E22 (attention required)
- Error Red: #E74C3C (validation errors)

Technical Data Colors:
- Historical: #7F8C8D (past data)
- Current: #2C3E50 (present values)
- Projected: #3498DB (future projections)
- Benchmark: #9B59B6 (industry standards)

MAIN INTERFACE LAYOUT:

1. ACTUARIAL DASHBOARD (Top Section):
   
   KEY METRICS CARDS (4 cards across):
   - "Provisions Techniques Totales": 
     * Large number in FCFA (e.g., "2,847,293,847 FCFA")
     * Trend indicator (+/- %) since last valuation
     * Regulatory adequacy percentage
   
   - "Ratio de Couverture":
     * Percentage with large gauge visualization
     * Color-coded: Green >110%, Orange 100-110%, Red <100%
     * Comparison with regulatory minimum
   
   - "Âge Actuariel Moyen":
     * Current age with trend arrow
     * Impact on provisions calculation
     * Comparison with assumptions
   
   - "Rendement Technique":
     * Expected vs. actual returns
     * Impact on funding level
     * Stress test results

2. NAVIGATION TABS (Professional Layout):
   
   Tab 1: "Tables de Mortalité"
   Tab 2: "Provisions Techniques"
   Tab 3: "Hypothèses Actuarielles"
   Tab 4: "Validation & Contrôles"
   Tab 5: "Rapports Réglementaires"

3. TABLES DE MORTALITÉ SECTION:
   
   LEFT PANEL - Table Management:
   - Current mortality table selector dropdown
   - "Table TH/TF 00-02" (French standard)
   - "Table Militaire Sénégal 2024" (custom)
   - Upload new table functionality
   - Historical versions with effective dates
   
   CENTER - Mortality Rate Visualization:
   - Interactive line chart showing qx by age
   - Separate lines for males/females
   - Military vs. civilian population comparison
   - Improvement factors by year
   - Hover details showing exact rates
   
   RIGHT PANEL - Technical Parameters:
   - Improvement rates: Input fields by age group
   - Projection methodology: Dropdown selection
   - Confidence intervals: Statistical parameters
   - Validation against population data
   
   BOTTOM SECTION - Impact Analysis:
   - "Impact sur les Provisions": Sensitivity analysis
   - Waterfall chart showing provision changes
   - Member-by-member impact summary
   - Regulatory compliance verification

4. PROVISIONS TECHNIQUES SECTION:
   
   CALCULATION ENGINE DISPLAY:
   - Real-time calculation status indicator
   - "Calcul en cours... 15,847 membres traités"
   - Progress bar with estimated completion time
   - Last successful calculation timestamp
   
   PROVISION BREAKDOWN:
   - Mathematical reserves by member category
   - Safety margins and regulatory buffers
   - Bonus reserves and profit sharing
   - Administrative expense reserves
   - Interactive treemap visualization
   
   DETAILED CALCULATIONS VIEW:
   - Member-level provision details in searchable table
   - Filters by: Grade, Age, Service years, Salary band
   - Individual calculation audit trail
   - Exception report for unusual cases
   
   RECONCILIATION PANEL:
   - Previous period provisions
   - New business additions
   - Interest accrual calculations
   - Experience gains/losses
   - Current period provisions
   - Variance analysis with explanations

5. HYPOTHÈSES ACTUARIELLES SECTION:
   
   ECONOMIC ASSUMPTIONS:
   - Discount rate: Slider with market benchmark
   - Inflation assumption: Input with economic indicators
   - Salary increase rates: By grade and experience
   - Investment return expectations: By asset class
   
   DEMOGRAPHIC ASSUMPTIONS:
   - Retirement age patterns: Distribution display
   - Disability rates: By age and military branch
   - Withdrawal rates: Early retirement statistics
   - Family composition: Dependent assumptions
   
   FINANCIAL ASSUMPTIONS:
   - Expense loading factors
   - Administrative cost projections
   - Contribution increase scenarios
   - Benefit improvement impacts
   
   SCENARIO TESTING:
   - Best estimate scenario (base case)
   - Conservative scenario (regulatory)
   - Stress test scenarios (adverse)
   - Custom scenario builder

6. VALIDATION & CONTRÔLES SECTION:
   
   AUTOMATED VALIDATION CHECKS:
   - ✅ "Cohérence des tables de mortalité"
   - ✅ "Validation des calculs de provisions"
   - ⚠️ "Vérification des hypothèses économiques"
   - ❌ "Contrôle des données d'entrée"
   
   RECONCILIATION CONTROLS:
   - Balance sheet reconciliation
   - Cash flow projections vs. actual
   - Experience study results
   - Peer benchmarking analysis
   
   REGULATORY COMPLIANCE:
   - OHADA compliance checklist
   - BCEAO reporting requirements
   - Local regulatory updates
   - International standards (IAS 19, IFRS)
   
   AUDIT TRAIL:
   - All calculation changes logged
   - User activity tracking
   - Data lineage visualization
   - Version control for all parameters

SPECIALIZED ACTUARIAL FEATURES:

1. Experience Analysis Tools:
   - Actual vs. expected mortality analysis
   - Salary increase experience studies
   - Investment return attribution
   - Expense analysis by category

2. Asset-Liability Matching:
   - Duration analysis charts
   - Interest rate sensitivity testing
   - Immunization strategy validation
   - Dynamic hedging recommendations

3. Stochastic Modeling Integration:
   - Link to Monte Carlo simulations
   - Economic scenario generators
   - Nested stochastic projections
   - Risk measure calculations (VaR, TVaR)

4. Regulatory Reporting Automation:
   - BCEAO quarterly returns
   - Annual actuarial reports
   - Solvency II equivalents
   - Local regulatory filings

TECHNICAL FEATURES:

Calculation Performance:
- Multi-threaded calculation engine
- GPU acceleration for complex models
- Distributed processing capability
- Calculation caching and optimization

Data Management:
- Version control for all actuarial data
- Data quality scoring and alerts
- Automated data validation rules
- Integration with external data sources

Professional Tools:
- Advanced Excel export with live links
- R/Python integration for custom analysis
- Professional report generation
- Actuarial model documentation

MOBILE CONSIDERATIONS:
- Essential metrics available on mobile
- Approval workflows for mobile devices
- Real-time alerts for critical issues
- Simplified validation interface

ACCESSIBILITY:
- Screen reader support for all data tables
- Keyboard navigation for power users
- High contrast mode for detailed analysis
- Multiple language support (French/English)

COLLABORATION FEATURES:
- Multi-actuary review workflows
- Comments and approval system
- Shared assumption libraries
- Peer review and validation

ADVANCED ANALYTICS:
- Machine learning for assumption setting
- Predictive analytics for experience studies
- Automated outlier detection
- Trend analysis and forecasting

OUTPUT: Professional-grade actuarial interface that provides comprehensive tools for managing all technical aspects of the pension scheme while maintaining the highest standards of actuarial practice and regulatory compliance.
```