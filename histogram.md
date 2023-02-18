<!--Don't delete ths script-->
<script src = "https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id = "MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<!--Don't delete ths script-->

<h1>Histogram</h1>

<p align = "justify">This function shows a boxplot and histogram in a single chart.</p>

<h2>Input variables</h2>

<p align = "justify">This function shows a boxplot and histogram in a single chart.</p>

<table style = "width:100%">
    <tr>
        <td>DATASET</td>
        <td>Dataset specifications</td>
        <td>Py dictionary</td>
    </tr>
    <tr>
        <td></td>
        <td>'DATASET' = Full dataset</td>
        <td></td>
    </tr>  
    <tr>
        <td></td>
        <td>'COLUMN' = Specify the column you want to plot</td>
        <td></td>
    </tr>  
    <tr>
        <td>PLOT_SETUP</td>
        <td>Specifications of chart</td>
        <td>Py dictionary</td>
    </tr>  
    <tr>
        <td></td>
        <td>'NAME' = Filename output file</td>
        <td>String</td>
    </tr>  
    <tr>
        <td></td>
        <td>'WIDTH' = Width figure</td>
        <td>Float</td>
    </tr>
    <tr>
        <td></td>
        <td>'HEIGHT  = Height figure</td>
        <td>Float</td>
    </tr>  
    <tr>
        <td></td>
        <td>'X AXIS SIZE' = X font axis size</td>
        <td>Float</td>
    </tr>
    <tr>
        <td></td>
        <td>'Y AXIS SIZE' = Y font axis size</td>
        <td>Float</td>
    </tr>  
    <tr>
        <td></td>
        <td>'AXISES COLOR' = Axis color</td>
        <td>String</td>
    </tr>  
    <tr>
        <td></td>
        <td>'X AXIS LABEL' = X label name</td>
        <td>String</td>
    </tr>  
    <tr>
        <td></td>
        <td>'Y AXIS LABEL' = Y label name</td>
        <td>String</td>
    </tr>  
    <tr>
        <td></td>
        <td>'LABELS SIZE' = Labels size</td>
        <td>Float</td>
    </tr>
    <tr>
        <td></td>
        <td>'LABELS COLOR' = Labels color</td>
        <td>Float</td>
    </tr> 
    <tr>
        <td></td>
        <td>'CHART COLOR' = Boxplot and histogram color</td>
        <td>String</td>
    </tr>
    <tr>
        <td></td>
        <td>'BINS' = Range representing the width of a single bar</td>
        <td>Integer</td>
    </tr>  
    <tr>
        <td></td>
        <td>'KDE' = Smooth of the random distribution</td>
        <td>Boolean</td>
    </tr>  
    <tr>
        <td></td>
        <td>'EXTENSION' = Extension output file</td>
        <td>String</td>
    </tr>
</table>

<h2>Outnput variables</h2>

<p align = "justify">The function displays the plot on the screen and saves it to the local folder of the ipynb file.</p>

<h2>Example 1</h2>

```python
# Data
DF =  pd.DataFrame({'col1': np.random.normal(0, 1, 1000),
                     'col2': np.random.normal(5, 2, 1000),
                     'col3': np.random.normal(-5, 3, 1000)})
COLUMN = 'col1'

# Chart setup
PLOT_SETUP = {
              'NAME': f"{COLUMN}_Histogram",
              'EXTENSION': 'svg',
              'WIDTH': 0.20, 
              'HEIGHT': 0.10,
              'X AXIS LABEL': '$x_{i}$ variable',
              'X AXIS SIZE': 15.5,
              'Y AXIS LABEL': 'Frequency',
              'Y AXIS SIZE': 15.5,
              'AXISES COLOR': '#000000',
              'LABELS SIZE': 15.5,
              'LABELS COLOR': '#000000', 
              'CHART COLOR': '#2219F0',
              'KDE': True,
              'BINS': 20,
              'DPI': 600,
             }

# Data statement 
DATA = {
         'DATASET': DF,
         'COLUMN': COLUMN        
       }  

# Call function
HISTOGRAM_CHART(DATA, PLOT_SETUP)
```
<center><img src="./imgs/col1_Histogram.svg" width="70%"></center>
<p align = "center"><b>Figure 1.</b> \(x_{1}\) variable histogram and boxplot.</p>

<h2>Example 2</h2>

```python
# Data
DF =  pd.DataFrame({'col1': np.random.normal(0, 1, 1000),
                     'col2': np.random.normal(5, 2, 1000),
                     'col3': np.random.normal(-5, 3, 1000)})
COLUMN = 'col1'
NAMES = np.array([['$x_{1}$', '#8C0C15'], 
                  ['$x_{2}$', '#5FD34D'],
                  ['$x_{3}$', '#4DA7D3']])

ID = 0

# Plot in looping
for COLUMN in DF:
    PLOT_SETUP = {
              'NAME': f"{COLUMN}_Histogram",
              'EXTENSION': 'svg',
              'WIDTH': 0.20, 
              'HEIGHT': 0.10,
              'X AXIS LABEL': NAMES[ID, 0],
              'X AXIS SIZE': 15,
              'Y AXIS LABEL': 'Frequency',
              'Y AXIS SIZE': 15,
              'AXISES COLOR': '#000000',
              'LABELS SIZE': 15,
              'LABELS COLOR': '#000000', 
              'CHART COLOR': NAMES[ID, 1],
              'KDE': True,
              'BINS': 20,
              'DPI': 600,
             }
    
    DATA = {
            'DATASET': DF,
            'COLUMN': COLUMN        
           }
    HISTOGRAM_CHART(DATA, PLOT_SETUP)
    ID += 1
```

<center><img src="./imgs/col11_Histogram.svg" width="70%"></center>
<p align = "center">
<b>Figure 2.</b> \(x_{1}\) variable histogram and boxplot.</p>

<center><img src="./imgs/col2_Histogram.svg" width="70%"></center>
<p align = "center">
<b>Figure 3.</b> \(x_{2}\) variable histogram and boxplot.</p>

<center><img src="./imgs/col3_Histogram.svg" width="70%"></center>
<p align = "center">
<b>Figure 4.</b> \(x_{3}\) variable histogram and boxplot.</p>