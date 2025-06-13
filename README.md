# Modular Slotted Rack System (OpenSCAD)

This OpenSCAD project defines a **customizable modular rack system** with dovetail joints, numbered holes, inlay support, handles, and optional SVG-shaped cutouts. It's designed for parametric control of dimensions, tolerances, hole layouts, and component rendering.

## 📦 Features

- Parametric rack and support dimensions
- Dovetail joints for sturdy modular connections
- Automatically calculated or user-defined hole grid
- Numbered holes with optional center dots
- SVG support for custom-shaped holes
- Alternating hole shape orientation
- Configurable handle geometry
- Inlay-ready number generation
- Selectable rendering of components or full assembly

---

## 🔧 Usage

This project uses [BOSL2](https://github.com/revarbat/BOSL2) for its advanced geometry tools like `cuboid`, `attach`, and `dovetail`.

### ✅ Required Includes

```scad
include <BOSL2/std.scad>
include <BOSL2/joiners.scad>
```

### 🧩 Component Selection

Use the `component_selection` parameter to render individual parts or the full rack:

```scad
component_selection = "assembly"; // Options:
// - assembly
// - bottom_rack
// - combined_rack
// - vertical_support_left
// - vertical_support_right
// - number_inlays
```

---

## ⚙️ Configuration Parameters

### 📐 Rack Dimensions

```scad
rack_width = 201;
rack_depth = 222.4;
rack_height = 134;
section_height = 9.4;
```

### 🔙 Back Support

```scad
enable_back_support = true;
back_support_depth = 10;
```

### 🕳️ Hole Grid

```scad
hole_diameter = 26.3;
hole_tolerance = 0.2;
num_holes_x = 0; // 0 = auto-calculate
num_holes_y = 0;
hole_spacing = 9.8;
hole_shape = "circle"; // [circle, square, svg]
svg_file = ""; // Path to SVG for custom shapes
enable_alternating = true;
alternating_angle = 180;
```

### 🔢 Hole Numbering

```scad
enable_numbers = true;
number_direction = "left_to_right";
enable_center_dots = true;
number_depth = 3;
number_scale = 1;
number_rotation = 0;
number_spacing = 7;
```

### 🧩 Dovetail Joints

```scad
dovetail_width = 15;
dovetail_height = 4;
dovetail_back_width = 18;
support_thickness = 14.3;
dovetail_tolerance = 0.2;
```

### 🛠️ Handle Geometry

```scad
handle_width = support_thickness;
handle_height = 50;
handle_depth = rack_depth;
slot_width = 150;
slot_height = 36;
slot_corner_radius = 6;
corner_radius = 5;
```

### 📏 Support and Margin

```scad
dovetail_spacing = 60;
dovetail_start_height = 10;
dovetail_count = num_plates + 1;
side_margin = 30;
front_margin = 15;
bottom_depth = 7;
```

### 💠 Inlays

```scad
inlay_tolerance = -0.15;
height_offset = 0.2;
```

---

## 🧱 Modules

- `assembly()`: Full assembled rack
- `bottom_rack()`: Base plate with dimples
- `combined_rack()`: Upper/middle plates with through holes
- `vertical_support()`: Vertical side supports with dovetails
- `number_inlays()`: Exports flat number inlays for multicolor/dual-material printing

---

## 🧮 Automatic Hole Calculation

If `num_holes_x` or `num_holes_y` is set to 0, hole layout is calculated based on available space and spacing using this logic:

```scad
cols = floor((avail_width + hole_spacing) / (adj_hole_diameter + hole_spacing));
rows = floor((avail_depth + hole_spacing) / (adj_hole_diameter + hole_spacing));
```

---

## 🔄 Example Preview Switch

Change the rendered component easily by adjusting:

```scad
component_selection = "assembly"; // to view full rack
```

---

## 🛠️ Requirements

- **OpenSCAD v2021+**
- **BOSL2 library**: [https://github.com/revarbat/BOSL2](https://github.com/revarbat/BOSL2)
