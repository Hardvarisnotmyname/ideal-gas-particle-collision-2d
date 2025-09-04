# Particle Physics Sandbox Simulator

A real-time particle physics simulation built with HTML5 Canvas and WebGL, featuring advanced physics modeling, interactive controls, and educational demonstrations of thermodynamic principles.


## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Quick Start](#quick-start)
- [User Interface](#user-interface)
- [Physics Controls](#physics-controls)
- [Advanced Features](#advanced-features)
- [Technical Details](#technical-details)
- [Performance Optimization](#performance-optimization)
- [Educational Applications](#educational-applications)
- [Browser Compatibility](#browser-compatibility)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

This simulator creates a virtual particle environment where you can observe and manipulate the behavior of thousands of particles in real-time. The simulation demonstrates fundamental physics concepts including:

- **Kinetic Theory of Gases**: Particle motion and temperature relationships
- **Thermodynamics**: Heat transfer between systems
- **Collision Dynamics**: Elastic and inelastic collisions
- **Force Interactions**: Gravity, pressure, and drag
- **Statistical Mechanics**: Maxwell-Boltzmann distribution

The simulator is particularly useful for understanding concepts like Maxwell's Demon, Brownian motion, and the behavior of gases under different conditions.

## Features

### Core Physics Engine
- **Real-time particle simulation** with up to 100,000 particles (500 in Node/Bond mode)
- **Elastic collision detection** using SAP (Sweep and Prune) or spatial grid methods
- **Force calculations** including gravity, pressure, friction, and drag
- **Temperature modeling** with independent left/right box controls
- **Speed-based color coding** (blue = cold, red = hot)

### Interactive Controls
- **Mouse interaction**: Click and drag to apply divergence and curl forces
- **Real-time parameter adjustment** via sliders and toggles
- **Wall manipulation**: Adjustable divider wall with controllable opening
- **Particle spawning**: Dynamic particle count changes without simulation reset

### Advanced Physics Features
- **Maxwell's Demon**: Intelligent particle gate that selectively allows passage
- **Node/Bond System**: Molecular structure simulation with spring physics
- **Spatial optimization**: Grid-based force calculations for performance
- **Substepping**: Multiple physics iterations per frame for accuracy

### Visualization & Analytics
- **Real-time graphs**: Temperature history for both chambers
- **Performance monitoring**: FPS, collision rates, and physics metrics
- **Statistical analysis**: Average/max speeds, temperature calculations
- **Bond visualization**: Dynamic connection lines between bonded particles

## Quick Start

### Running the Simulator

1. **Download the file**: Download `sim.html` (single self-contained HTML file)
2. **Open in browser**: Simply open `sim.html` in any modern web browser
3. **No installation required**: Runs entirely in the browser using WebGL/Canvas - no additional setup needed

### Basic Usage

1. **Start the simulation**: The simulator begins running automatically upon opening
2. **Adjust particle count**: Use the "Particles" slider to set the number of particles (1-100,000)
3. **Set temperatures**: Control left and right box temperatures independently
4. **Observe behavior**: Watch particles move and interact in real-time (blue=cold, red=hot particles)
5. **Mouse interaction**: Click and drag on the simulation area to apply forces
6. **Experiment**: Try different physics settings and observe the results

### First Experiment: Heat Transfer

1. Set left temperature to 5000, right temperature to 50
2. Open the wall (click "OpenWall" button)
3. Watch as heat transfers from left to right over time
4. Observe the temperature graphs showing equalization

## User Interface

### Control Panels

The interface includes header buttons for common actions:
- **Reset**: Reset the simulation to initial state
- **Pause/Resume**: Pause or resume the simulation
- **OpenWall/Close Pipe**: Toggle the wall opening

The interface is organized into four main tabs:

#### Setup Tab
- **Particles**: Total number of particles in simulation (1-100,000, default: 10,000)
- **Left Temp**: Temperature of particles in left chamber
- **Right Temp**: Temperature of particles in right chamber
- **Radius**: Size of individual particles
- **Wall Position**: Location of dividing wall (0-100%)
- **Divergence**: Mouse force direction (Inward/Outward)
- **Curl**: Mouse rotation direction (Clockwise/Anticlockwise)

#### Forces Tab
- **Gravity**: Inter-particle gravitational attraction
- **Gravity Strength**: Strength of gravitational force
- **Gravity Exponent**: Power law for gravity (2.0 = inverse square)
- **Pressure**: Short-range repulsive forces
- **Pressure Strength**: Strength of pressure force
- **Friction**: Energy loss during collisions
- **Drag**: Air resistance force
- **Drag Coefficient**: Air resistance strength
- **Downwards Gravity**: Constant downward force on all particles

#### Interaction Tab
- **Wall Opening**: Size of opening in dividing wall (0-100%, default: 1%)
- **Maxwell's Demon**: Intelligent particle gate
- **Demon Threshold**: Speed threshold for demon selection
- **Nodes**: Enable particle bonding system
- **Branches**: Maximum bonds per particle (0-11, where 11 = unlimited)
- **Node Max Distance**: Maximum bonding distance
- **Node Min Distance**: Minimum bonding distance
- **Bond Stiffness**: Spring constant for bonds
- **Bond Dynamics**: Enable spring physics
- **Bond Visibility**: Show/hide bond connection lines

#### Performance Tab
- **Substeps**: Physics iterations per frame (1-8)
- **Grid Size**: Spatial grid cell size for optimization
- **Gravity Range**: Effective range of gravity calculations
- **FastFwd Simulation**: Uncapped frame rate mode
- **Collision Mode**: SAP vs Grid collision detection

### Statistics Panel

Real-time monitoring of:
- **FPS**: Current rendering frame rate
- **Target FPS**: Target frame rate for physics simulation
- **Physics FPS**: Physics simulation rate
- **Total Particles**: Current particle count
- **Collisions/sec**: Collision events per second
- **Bond Checks**: Number of bond formation checks per frame
- **Temperature**: Left and right chamber temperatures
- **Average/Max Speed**: Particle velocity statistics
- **Bond Statistics**: Connection counts and averages

### Visual Features

- **Dark theme**: Modern dark interface with CSS variables for consistent styling
- **Tooltip system**: Hover over controls for detailed help text and explanations (includes some playful and humorous descriptions)
- **Real-time color coding**: Particles change color based on speed (blue=cold, red=hot)
- **Responsive design**: Adapts to different screen sizes and devices
- **Custom UI controls**: Styled sliders, switches, and buttons for intuitive interaction

## Physics Controls

### Temperature Control

The simulator uses a simplified temperature model where particle speed represents thermal energy:

```
Temperature ∝ Average Particle Speed²
```

- **Left Temp**: Controls initial speeds of particles starting in left chamber
- **Right Temp**: Controls initial speeds of particles starting in right chamber
- **Real-time adjustment**: Temperature changes are applied gradually to avoid simulation instability

### Force Systems

#### Gravity
- **Inter-particle forces**: Each particle attracts every other particle
- **Configurable strength**: Adjustable attraction magnitude
- **Variable exponent**: Power law from 0.1 to 3.0 (2.0 = realistic inverse square)
- **Range limiting**: Effective distance for performance optimization

#### Pressure
- **Short-range repulsion**: Particles push apart when too close
- **Distance-based**: Force strength decreases with distance
- **Performance optimized**: Uses spatial grid for efficiency

#### Friction & Drag
- **Collision friction**: Energy loss during particle collisions
- **Air resistance**: Continuous speed reduction
- **Configurable coefficients**: Adjustable energy loss rates

### Mouse Interaction

- **Click and hold** on the simulation area to apply forces
- **Divergence**: Particles move toward or away from mouse cursor
- **Curl**: Particles rotate clockwise or counterclockwise around cursor
- **Force strength**: Proportional to distance from mouse

## Advanced Features

### Maxwell's Demon

Implements the famous thought experiment:
- **Indirect teleportation**: When a fast particle approaches from the left, a slow particle from the right is teleported to the left; when a slow particle approaches from the right, a fast particle from the left is teleported to the right
- **Speed threshold**: Configurable speed for particle selection (default: 10)
- **Thermodynamic violation**: Demonstrates apparent entropy decrease by creating temperature differences

### Node/Bond System

Creates molecular-like structures:
- **Dynamic bonding**: Particles form connections based on distance
- **Spring physics**: Bonds behave like springs with stiffness (default: 1.0) and damping (default: 0.1)
- **Branch limiting**: Maximum connections per particle
- **Distance constraints**: Minimum and maximum bonding distances

### Performance Optimizations

- **Spatial grid**: Divides space into cells for efficient neighbor finding (configurable grid size)
- **Force sampling**: Adaptive sampling reduces computation for distant particles (auto-scales with particle count)
- **WebGL acceleration**: Hardware-accelerated rendering with point sprites
- **Adaptive FPS**: Automatic frame rate adjustment with uncapped mode (up to 240 FPS)
- **Substepping**: Multiple physics iterations per frame for collision accuracy (1-8 steps)
- **Collision modes**: SAP (Sweep and Prune) for accuracy vs Grid for speed

## Technical Details

### Architecture

The simulator uses a modular architecture:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   User Interface│    │  Physics Engine │    │   Renderer      │
│   (HTML/CSS/JS) │◄──►│  (JavaScript)   │◄──►│ (WebGL/Canvas)  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │
                              ▼
                       ┌─────────────────┐
                       │   Bond System   │
                       │   (Molecular)   │
                       └─────────────────┘
```

### Physics Engine

- **Time stepping**: Fixed time step with substepping for stability
- **Collision detection**: O(n log n) SAP or O(n) grid-based methods
- **Force integration**: Euler integration methods
- **Boundary conditions**: Reflective walls with configurable openings

### Rendering Pipeline

- **Primary renderer**: WebGL 2.0 with point sprites (hardware acceleration)
- **Fallback renderer**: WebGL 1.0, then HTML5 Canvas 2D if WebGL unavailable
- **Color mapping**: HSV-based speed-to-color conversion (blue=cold, red=hot)
- **Overlay system**: Separate canvas for UI elements, walls, and bond visualization

### Data Structures

- **Particle array**: Float32Array with 8 values per particle (x, y, vx, vy, r, g, b, radius)
- **Spatial grid**: 2D grid system for efficient neighbor finding and force calculations
- **Bond system**: Dynamic arrays for particle connections and spring physics
- **Force sampling**: Adaptive sampling reduces computation for distant particle interactions

## Performance Optimization

### Rendering Optimizations
- **WebGL instancing**: Single draw call for all particles

- **Frame rate capping**: Prevents unnecessary computation

### Physics Optimizations
- **Spatial partitioning**: Grid-based neighbor finding
- **Force sampling**: Random sampling of source particles to reduce overall calculations


### Memory Management
- **Typed arrays**: Efficient memory usage with Float32Array

- **Garbage collection**: Minimize allocations during simulation

## Educational Applications

### Physics Concepts Demonstrated

1. **Kinetic Theory**
   - Particle motion and energy distribution
   - Temperature-speed relationships
   - Pressure-volume relationships

2. **Thermodynamics**
   - Heat transfer mechanisms
   - Entropy and disorder
   - Maxwell's Demon paradox

3. **Statistical Mechanics**
   - Maxwell-Boltzmann distribution
   - Equipartition theorem
   - Phase transitions



### Classroom Activities

1. **Heat Transfer Lab**
   - Observe temperature equalization
   - Measure heat transfer rates
   - Study conduction vs. radiation

2. **Gas Laws Investigation**
   - Boyle's Law: Pressure vs. Volume
   - Charles's Law: Volume vs. Temperature
   - Ideal Gas Law relationships

3. **Statistical Analysis**
   - Speed distribution histograms
   - Temperature fluctuations
   - Entropy calculations

## Browser Compatibility

### Supported Browsers
- **Chrome/Edge (recommended)**: Full WebGL 2.0 support with hardware acceleration
- **Firefox**: WebGL 2.0 with some limitations, may fallback to WebGL 1.0
- **Safari**: WebGL 1.0 fallback mode (WebGL 2.0 not fully supported)
- **Mobile browsers**: Touch interaction support, automatic performance scaling
- **Legacy browsers**: Automatic fallback to Canvas 2D rendering

### System Requirements
- **RAM**: 2GB minimum, 4GB recommended for 50k+ particles
- **GPU**: WebGL-capable graphics card
- **CPU**: Multi-core processor for physics calculations
- **Browser**: Modern browser with JavaScript enabled

### Performance Notes
- **WebGL acceleration**: Significantly faster than Canvas 2D
- **Particle limits**: 10k particles on mobile, 100k on desktop
- **Frame rates**: 60 FPS typical, up to 240 FPS with optimization

## Troubleshooting

### Common Issues

**Simulation runs slowly or freezes**
- Reduce particle count using the Particles slider
- Switch to Grid collision mode in Performance tab
- Increase grid size for better performance
- Disable gravity/pressure forces if not needed

**WebGL not available**
- The simulator automatically falls back to Canvas 2D rendering
- Some advanced features may be limited in Canvas mode
- Check browser compatibility above

**Particles disappear or behave strangely**
- Reset the simulation using the Reset button
- Check wall position and opening settings
- Ensure particle count is within reasonable limits

**Mobile performance issues**
- Limit particles to 10,000 or fewer
- Use Grid collision mode
- Close other browser tabs to free up resources

**Touch controls not working**
- Ensure you're using a touch-enabled device
- Try refreshing the page
- Check that the simulation area is properly sized

### System Requirements
- **Minimum**: 2GB RAM, WebGL-capable GPU, modern browser
- **Recommended**: 4GB+ RAM, dedicated GPU, Chrome/Edge browser
- **Mobile**: 3GB+ RAM, recent iOS/Android device

## Contributing

### Development Setup

1. **Download the file**
   ```bash
   # Download sim.html - single self-contained file
   # No repository cloning required
   ```

2. **Edit directly**
   ```bash
   # Open sim.html in any text editor
   # All code (HTML, CSS, JavaScript) is embedded in one file
   ```

3. **Open in browser**
   ```bash
   # Simply open sim.html in your browser
   # Changes are reflected immediately on refresh
   ```

4. **Development tools**
   - Use browser developer tools for debugging
   - Chrome DevTools performance profiler for optimization
   - WebGL Inspector for rendering debugging
   - Text editor with JavaScript/HTML/CSS syntax highlighting

### Code Structure

```
sim.html (Single self-contained file)
├── CSS Styles (Embedded)
│   ├── Dark theme with CSS variables
│   ├── Responsive layout and controls
│   ├── Tooltip system for help text
│   └── Custom sliders and switches
├── JavaScript Modules (Embedded)
│   ├── Configuration object (global settings)
│   ├── PhysicsModule (core physics engine)
│   ├── Renderer (WebGL 2.0/Canvas 2D)
│   ├── BondSystem (molecular bonding)
│   ├── GraphManager (real-time graphs)
│   └── UI event handlers and tooltips
└── HTML Structure
    ├── Tabbed control panels
    ├── Canvas elements (simulation + overlay)
    ├── Statistics panel with live metrics
    └── Real-time temperature graphs
```

### Adding New Features

1. **Physics features**: Add to PhysicsModule.update() function
2. **UI controls**: Add to wireUI() function with appropriate HTML
3. **Visualization**: Extend Renderer class methods
4. **Performance**: Profile and optimize new code paths

## Changelog

### Version 1.0.0
- **Initial release** with complete particle physics simulation
- **WebGL 2.0 rendering** with Canvas 2D fallback
- **Advanced physics features**: Maxwell's Demon, Node/Bond system
- **Real-time performance monitoring** and optimization
- **Educational demonstrations** of thermodynamic principles
- **Cross-platform compatibility** with touch support

### Key Features Added
- Particle count up to 100,000 with adaptive performance
- Interactive mouse forces (divergence and curl)
- Real-time temperature control and visualization
- Multiple collision detection modes (SAP/Grid)
- Comprehensive statistics and graphing
- Mobile-responsive design with touch controls

## License

This project is open source and available under the MIT License. See LICENSE file for details.

---

**Created with ❤️ for physics education and simulation enthusiasts**

For questions or feedback, please open an issue on the project repository.
