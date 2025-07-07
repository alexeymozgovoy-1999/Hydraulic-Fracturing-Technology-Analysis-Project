## **Below is the description and a brief implementation algorithm of the project**

This project enables the analysis of production and hydraulic fracturing (HF) data to determine the most effective technology.
The study is based on data from one of the oil fields in Western Siberia.

The work was done in **Python** using **Jupyter Notebook**.

<hr>

### **Part 1**  
<div> 
  <h4>Overview</h4>
  <p>The algorithm analyzes oil, gas and water production metrics by wells using linear interpolation to estimate production at key time points (30, 60, 90 and 120 days).</p>
  
  <h4>Input Data</h4>
  <ul>
    <li>ProdData.csv file in windows-1251 encoding with production data</li>
    <li>Contains well information, dates, reservoirs and production metrics</li>
  </ul>
  
  <h4>Implementation</h4>
  <ul>
    <li>Python with Pandas and SciPy libraries</li>
    <li>Key steps:
      <ol>
        <li>Data loading and preprocessing</li>
        <li>Cumulative production days calculation</li>
        <li>Linear interpolation of production metrics</li>
        <li>Final table generation with metrics for key dates</li>
      </ol>
    </li>
  </ul>
  
  <h4>Output</h4>
  <p>Table with oil, gas and water production metrics for each well at 30, 60, 90 and 120 days of operation.</p>
</div>

### **Part 2**  
<div>
  <h3>GRP Data Processing Algorithm Description</h3>
  
  <h4>Overview</h4>
  <p>The algorithm processes hydraulic fracturing (HF) data, aggregates well parameters and analyzes the relationship between HF technologies and production metrics.</p>
  
  <h4>Input Data</h4>
  <ul>
    <li>Frac_list.csv file with HF parameters (36 columns)</li>
    <li>Key parameters include:
      <ul>
        <li>HF technologies and fluids</li>
        <li>Fracture geometry parameters</li>
        <li>Injection parameters (proppant mass, concentration, pressure)</li>
        <li>Treatment results</li>
      </ul>
    </li>
    <li>Production data from previous processing stage</li>
  </ul>
  
  <h4>Processing Steps</h4>
  <ol>
    <li>Data filtering:
      <ul>
        <li>Removing entries with missing technology</li>
        <li>Excluding canceled HF jobs</li>
      </ul>
    </li>
    <li>Well parameter aggregation (median values)</li>
    <li>Merging with production data</li>
    <li>Visual analysis (boxplot) of production vs HF technology</li>
    <li>Additional filtering:
      <ul>
        <li>Removing wells with zero production</li>
        <li>Excluding irrelevant technologies</li>
      </ul>
    </li>
  </ol>
  
  <h4>Technologies Used</h4>
  <ul>
    <li>Python with Pandas, Seaborn libraries</li>
    <li>Data aggregation and visualization methods</li>
  </ul>
</div>

### **Part 3**  
<div>
  <h3>Statistical Analysis Algorithm Description</h3>
  
  <h4>Overview</h4>
  <p>The algorithm performs statistical analysis of the relationship between HF parameters and oil production, including regression analysis, distribution checks and technology comparisons.</p>
  
  <h4>Key Analysis Steps</h4>
  <ol>
    <li><strong>Regression Analysis:</strong>
      <ul>
        <li>Building linear model for 120-day production prediction</li>
        <li>Predictors: TVD, proppant concentration, pad volume, ISIP pressure</li>
      </ul>
    </li>    
    <li><strong>Distribution Analysis:</strong>
      <ul>
        <li>Log-transform of production metrics (log_dob_30)</li>
        <li>Distribution visualization for different technologies</li>
        <li>Data filtering (log_dob_30 > 4.8)</li>
      </ul>
    </li> 
    <li><strong>Technology Comparison:</strong>
      <ul>
        <li>Normality tests</li>
        <li>Homoscedasticity check (Levene's test)</li>
        <li>Pairwise t-tests</li>
        <li>One-way ANOVA</li>
        <li>Tukey post-hoc analysis</li>
      </ul>
    </li>    
    <li><strong>Visualization:</strong>
      <ul>
        <li>Technology-specific distribution histograms</li>
        <li>Technology comparison boxplots</li>
      </ul>
    </li>
  </ol>
  
  <h4>Libraries Used</h4>
  <ul>
    <li>StatsModels - regression analysis</li>
    <li>Pingouin - statistical tests</li>
    <li>SciPy - statistical functions</li>
    <li>Seaborn - visualization</li>
  </ul>
</div>

<div style="font-family: Arial, sans-serif; max-width: 800px; margin: 0 auto;">
  <h3 style="color: #2c3e50; border-bottom: 2px solid #3498db; padding-bottom: 5px;">Conclusions and Recommendations Based on Analysis Results</h3>
  
  <div style="background-color: #f8f9fa; padding: 15px; border-radius: 5px; margin-bottom: 20px;">
    <h4 style="color: #2980b9;">Key Findings:</h4>
    <ul style="list-style-type: square; padding-left: 20px;">
      <li style="margin-bottom: 8px;">
        <strong>The most significant production difference</strong> was observed between:
        <ul>
          <li>LG+XL at > 4 m³/min flow rate (highest production)</li>
          <li>XANTHAN at < 4 m³/min flow rate (lowest production)</li>
        </ul>
      </li>
      <li style="margin-bottom: 8px;">
        <strong>High-flow LG+XL</strong> demonstrates:
        <ul>
          <li>Statistically significant higher production compared to low-flow LG+XL (p < 0.0001)</li>
          <li>Significantly better results compared to XANTHAN (p = 0.00009)</li>
        </ul>
      </li>
      <li>
        <strong>No significant difference</strong> was found between:
        <ul>
          <li>LG+XL at < 4 m³/min flow rate</li>
          <li>XANTHAN at < 4 m³/min flow rate (p = 0.54)</li>
        </ul>
      </li>
    </ul>
  </div>

  <div style="background-color: #e8f4fc; padding: 15px; border-radius: 5px; border-left: 4px solid #3498db;">
    <h4 style="color: #2980b9;">Technology Selection Recommendations:</h4>
    <table style="width: 100%; border-collapse: collapse; margin-top: 10px;">
      <tr style="background-color: #3498db; color: white;">
        <th style="padding: 8px; text-align: left;">Objective</th>
        <th style="padding: 8px; text-align: left;">Recommended Technology</th>
        <th style="padding: 8px; text-align: left;">Expected Outcome</th>
      </tr>
      <tr style="border-bottom: 1px solid #ddd;">
        <td style="padding: 8px;"><strong>Maximize Production</strong></td>
        <td style="padding: 8px;">LG+XL at > 4 m³/min flow rate</td>
        <td style="padding: 8px;">Highest production (0.47-0.61 log units above other options)</td>
      </tr>
      <tr style="border-bottom: 1px solid #ddd;">
        <td style="padding: 8px;"><strong>Cost Optimization</strong></td>
        <td style="padding: 8px;">LG+XL < 4 m³/min or XANTHAN</td>
        <td style="padding: 8px;">
          <ul style="margin: 0; padding-left: 15px;">
            <li>Comparable efficiency</li>
            <li>Selection based on cost and availability</li>
          </ul>
        </td>
      </tr>
    </table>
  </div>
</div>
