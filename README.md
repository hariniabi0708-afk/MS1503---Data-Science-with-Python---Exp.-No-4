# Experiment 4 : Yearly Revenue Growth Visualization Using Matplotlib

## Aim

To visualize the yearly trend of company revenue and expenses from 2017 to 2023 using Matplotlib by plotting multi-line charts with customized markers, labels, legends, gridlines, and point annotations.

## Algorithm

1. **Start** the program.
2. **Import Libraries**: Import `matplotlib.pyplot` as `plt` for plotting and `numpy` as `np` for numeric array generation and index lookup.
3. **Initialize Dataset**:
   * Generate an array `years` spanning `2017` to `2023` using `np.arange(2017, 2024)`.
   * Define lists `revenue` and `expenses` representing annual amounts in Lakhs.
4. **Configure Figure & Plot Lines**:
   * Initialize a figure canvas of size $8 \times 5$ inches using `plt.figure(figsize=(8, 5))`.
   * Plot `revenue` against `years` as a solid green line with circular markers (`marker='o'`).
   * Plot `expenses` against `years` as a dashed red line (`linestyle='--'`) with square markers (`marker='s'`).
5. **Format Chart Aesthetics**:
   * Add a bold chart title (`plt.title()`) and axis labels (`plt.xlabel()`, `plt.ylabel()`).
   * Enable dashed semi-transparent gridlines (`plt.grid()`) and place the legend in the upper-left corner (`plt.legend(loc='upper left')`).
6. **Annotate Peak Values**:
   * Find the indices of maximum revenue and maximum expenses using `np.argmax()`.
   * Highlight both peak data points on the chart with directional arrows and text callouts using `plt.annotate()`.
7. **Adjust Layout & Display**:
   * Prevent label clipping via `plt.tight_layout()` and render the final plot with `plt.show()`.
8. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Numerical Operations** | `np.arange()` | Generates evenly spaced integer years (`2017` through `2023`) |
| | `np.argmax()` | Returns the array index of the maximum revenue and expense values |
| **Line Plotting** | `plt.figure()` | Initializes a new figure window with custom dimensions |
| | `plt.plot()` | Draws line plots with customized markers, colors, line styles, and widths |
| **Chart Formatting** | `plt.title()`, `plt.xlabel()`, `plt.ylabel()` | Adds descriptive title and axis labels with custom font sizes |
| | `plt.grid()`, `plt.legend()` | Adds background gridlines and displays series labels in the upper left |
| **Annotations & Display** | `plt.annotate()` | Places text labels with arrows pointing to peak revenue and expense points |
| | `plt.tight_layout()`, `plt.show()` | Optimizes spacing to avoid overlapping elements and renders the figure |

## Program / Code

import matplotlib.pyplot as plt  
import numpy as np  

years = np.arange(2017, 2024)  
revenue = [42.0, 48.5, 55.0, 51.2, 66.8, 79.4, 92.5]  
expenses = [31.0, 35.2, 39.8, 41.5, 46.0, 52.3, 58.6]  

plt.figure(figsize=(8, 5))  
plt.plot(  
    years,  
    revenue,        
    color="green",  
    linestyle="-",  
    linewidth=2,  
    marker="o",  
    markersize=7,            
    label="Revenue (Lakhs)",  
)          
plt.plot(  
    years,  
    expenses,    
    color="red",    
    linestyle="--",  
    linewidth=2,  
    marker="s",    
    markersize=7,              
    label="Expenses (Lakhs)",  
)  

plt.title("Company Revenue vs. Expenses (2017 - 2023)", fontsize=14, fontweight="bold")  
plt.xlabel("Year", fontsize=11)  
plt.ylabel("Amount (in Lakhs)", fontsize=11)  
plt.xticks(years)  
plt.grid(True, linestyle="--", alpha=0.5)  

plt.legend(loc="upper left", fontsize=10)  

max_rev_idx = np.argmax(revenue)  
max_exp_idx = np.argmax(expenses)  
    
peak_rev_year = years[max_rev_idx]  
peak_rev_val = revenue[max_rev_idx]  
peak_exp_year = years[max_exp_idx]  
peak_exp_val = expenses[max_exp_idx]  

plt.annotate(  
    f"Peak Revenue: {peak_rev_val:.1f}L ({peak_rev_year})",  
    xy=(peak_rev_year, peak_rev_val),  
    xytext=(peak_rev_year - 2.1, peak_rev_val + 4.5),  
    arrowprops=dict(arrowstyle="->", color="darkgreen", lw=1.5),  
    fontsize=9.5,      
    fontweight="bold",  
    color="darkgreen",  
)  

plt.annotate(  
    f"Peak Expenses: {peak_exp_val:.1f}L ({peak_exp_year})",  
    xy=(peak_exp_year, peak_exp_val),  
    xytext=(peak_exp_year - 2.3, peak_exp_val - 9.0),  
    arrowprops=dict(arrowstyle="->", color="darkred", lw=1.5),  
    fontsize=9.5,      
    fontweight="bold",  
    color="darkred",  
)  
print(f"Peak Revenue: {peak_rev_val:.1f} Lakhs in {peak_rev_year}")  
print(f"Peak Expenses: {peak_exp_val:.1f} Lakhs in {peak_exp_year}")  

 
plt.tight_layout()  
plt.show()  

## Output
<img width="818" height="532" alt="image" src="https://github.com/user-attachments/assets/0095da2c-df8c-4f63-958c-ad3b3f2c78fa" />

## Result
The program successfully creates datasets for yearly company revenue and expenses and renders an annotated multi-line comparison chart using Matplotlib.
