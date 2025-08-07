# Exercise 4: Plotting Elementary Mathematical Functions

## 🧪 Aim

To plot and visualize basic mathematical functions including quadratic, sine, cosine, exponential, and logarithmic functions using Python libraries.

## 🎯 Objective

To understand and demonstrate the behaviour of elementary mathematical functions through graphical representation using `NumPy` and `Matplotlib`.

## ⚙️ Algorithm

1. **Import Libraries**: `numpy` and `matplotlib.pyplot`
2. **Define Ranges of x-values**:
   - Quadratic & Exponential: `x1 = np.linspace(-10, 10, 400)`
   - Sine & Cosine: `x2 = np.linspace(0, 2*np.pi, 400)`
   - Logarithmic: `x3 = np.linspace(0.1, 10, 400)` (to avoid log(0))
3. **Compute Function Values**:
   - Quadratic: `y1 = x1**2`
   - Sine: `y2 = np.sin(x2)`
   - Cosine: `y3 = np.cos(x2)`
   - Exponential: `y4 = np.exp(x1)`
   - Logarithmic: `y5 = np.log(x3)`
4. **Create Subplots**: Use `plt.subplots()` for grid layout
5. **Plot Each Function**: Use `.plot()` for each `(x, y)` pair
6. **Add Labels and Titles**
7. **Adjust Layout**: `plt.tight_layout()`
8. **Display Plot**: `plt.show()`

## 💻 Python code and Implementation

```python
import numpy as np
import matplotlib.pyplot as plt

# Define the range of x values
x1 = np.linspace(-10, 10, 400)       # Quadratic and exponential
x2 = np.linspace(0, 2 * np.pi, 400)  # Sine and cosine
x3 = np.linspace(0.1, 10, 400)       # Logarithmic

# Define the functions
y1 = x1**2
y2 = np.sin(x2)
y3 = np.cos(x2)
y4 = np.exp(x1)
y5 = np.log(x3)

# Create subplots
fig, ax = plt.subplots(3, 2, figsize=(12, 10))

# Quadratic
ax[0, 0].plot(x1, y1, label=r'$f(x) = x^2$', color='b')
ax[0, 0].set_title('Quadratic Function: $f(x) = x^2$')
ax[0, 0].set_xlabel('x')
ax[0, 0].set_ylabel('f(x)')
ax[0, 0].grid(True)
ax[0, 0].legend()

# Sine
ax[0, 1].plot(x2, y2, label=r'$f(x) = \sin(x)$', color='r')
ax[0, 1].set_title('Sine Function: $f(x) = \sin(x)$')
ax[0, 1].set_xlabel('x')
ax[0, 1].set_ylabel('f(x)')
ax[0, 1].grid(True)
ax[0, 1].legend()

# Cosine
ax[1, 0].plot(x2, y3, label=r'$f(x) = \cos(x)$', color='g')
ax[1, 0].set_title('Cosine Function: $f(x) = \cos(x)$')
ax[1, 0].set_xlabel('x')
ax[1, 0].set_ylabel('f(x)')
ax[1, 0].grid(True)
ax[1, 0].legend()

# Exponential
ax[1, 1].plot(x1, y4, label=r'$f(x) = e^x$', color='m')
ax[1, 1].set_title('Exponential Function: $f(x) = e^x$')
ax[1, 1].set_xlabel('x')
ax[1, 1].set_ylabel('f(x)')
ax[1, 1].grid(True)
ax[1, 1].legend()

# Logarithmic
ax[2, 0].plot(x3, y5, label=r'$f(x) = \ln(x)$', color='c')
ax[2, 0].set_title('Logarithmic Function: $f(x) = \ln(x)$')
ax[2, 0].set_xlabel('x')
ax[2, 0].set_ylabel('f(x)')
ax[2, 0].grid(True)
ax[2, 0].legend()

# Hide unused subplot
ax[2, 1].axis('off')

# Layout adjustment
plt.tight_layout()
plt.show()
```

## 📊 Result and Discussion

- Quadratic: Symmetric parabola opening upwards.

- Sine: Oscillates between -1 and 1 with a period of $2\pi$.

- Cosine: Similar to sine, phase-shifted by 90°.

- Exponential: Rapid growth for $x>0$ , decay for $x<0$.

- Logarithmic: Slowly increasing for $x>0$ , undefined for $x\leq 0$.

## 🧩 Application Problem
In a real-time system simulation, the function $f(x)=2x^3-3x^2+5\sin x+\frac{8}{x+1}$. models the response time of a processor node under varying load conditions 
$x$ , where $x\in [-0.9,10]$  to avoid division by zero.

```python
x_app = np.linspace(-0.9, 10, 400)
y_app = 2 * x_app**3 - 3 * x_app**2 + 5 * np.sin(x_app) + 8 / (x_app + 1)

plt.figure(figsize=(10, 6))
plt.plot(x_app, y_app, label=r'$f(x) = 2x^3 - 3x^2 + 5\sin(x) + \frac{8}{x+1}$', color='darkorange')
plt.title('Application Function: Processor Response Time')
plt.xlabel('System Load (x)')
plt.ylabel('Response Time f(x)')
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
```


## Advanced plot with Plotly

```python
import plotly.graph_objects as go

# Recreate the sine and cosine plots with Plotly
x = np.linspace(0, 2 * np.pi, 400)
y_sin = np.sin(x)
y_cos = np.cos(x)

fig = go.Figure()

fig.add_trace(go.Scatter(x=x, y=y_sin, mode='lines', name='sin(x)'))
fig.add_trace(go.Scatter(x=x, y=y_cos, mode='lines', name='cos(x)'))

fig.update_layout(
    title='Interactive Sine and Cosine Functions with Plotly',
    xaxis_title='x',
    yaxis_title='f(x)',
    legend_title='Functions',
    hovermode='x unified'
)

fig.show()

```

## Interactive plots and Animations

```python
import numpy as np
import plotly.graph_objects as go

# Create grid
x = np.linspace(-10, 10, 50)
y = np.linspace(-10, 10, 50)
x_grid, y_grid = np.meshgrid(x, y)

# Create frames for each value of k
frames = []
k_values = np.linspace(0, 10, 40)

for k in k_values:
    z =np.abs(np.sqrt(x_grid**2 + y_grid**2) -k)
    surface = go.Surface(z=z, x=x_grid, y=y_grid, colorscale='viridis')
    frames.append(go.Frame(data=[surface], name=f'{k:.2f}'))

# Initial surface (for first frame)
z0 = np.sin(np.sqrt(x_grid**2 + y_grid**2) - k_values[0])
surface0 = go.Surface(z=z0, x=x_grid, y=y_grid, colorscale='viridis')

# Create figure with initial frame and all other frames
fig = go.Figure(
    data=[surface0],
    frames=frames,
    layout=go.Layout(
        title='Animated 3D Surface Plot with Varying k',
        scene=dict(
            xaxis_title='x',
            yaxis_title='y',
            zaxis_title='z'
        ),
        updatemenus=[
            dict(
                type="buttons",
                showactive=False,
                buttons=[
                    dict(label="Play",
                         method="animate",
                         args=[None, {"frame": {"duration": 100, "redraw": True},
                                      "fromcurrent": True}]),
                    dict(label="Pause",
                         method="animate",
                         args=[[None], {"frame": {"duration": 0, "redraw": False},
                                        "mode": "immediate",
                                        "transition": {"duration": 0}}])
                ]
            )
        ],
        sliders=[{
            "steps": [
                {"method": "animate", "args": [[f'{k:.2f}'],
                 {"mode": "immediate", "frame": {"duration": 0, "redraw": True}, "transition": {"duration": 0}}],
                 "label": f'{k:.2f}'}
                for k in k_values
            ],
            "transition": {"duration": 0},
            "x": 0,
            "y": -0.1,
            "currentvalue": {"prefix": "k: "}
        }]
    )
)

fig.show()
```


