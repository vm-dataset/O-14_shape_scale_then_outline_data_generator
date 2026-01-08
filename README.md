# Shape Scale-Then-Outline Task Generator

A specialized data generator for creating **two-step sequential visual reasoning tasks** where shapes undergo scale transformation followed by fill-to-outline transformation.

## 🎯 Task Format

This generator creates visual analogies in the **A→B→C :: D→?→?** format:

- **Example Sequence (A→B→C)**: Shows the complete two-step transformation
  - **A**: Original shape (e.g., small filled circle)
  - **B**: After step 1 - scale change (e.g., large filled circle)  
  - **C**: After step 2 - fill-to-outline (e.g., large outline circle)

- **Question Sequence (D→?→?)**: User must solve both steps
  - **D**: Original shape (e.g., small filled square)
  - **First ?**: Apply step 1 - scale change (e.g., large filled square)
  - **Second ?**: Apply step 2 - fill-to-outline (e.g., large outline square)

## 🌟 Key Features

### Sequential Two-Step Transformations
- **Step 1**: Scale transformation (small → large, medium → extra_large, etc.)
- **Step 2**: Fill-to-outline transformation (filled → outline-only)
- **Consistent Pattern**: Both example and question follow identical transformation sequence

### Enhanced Visual Design
- **Optimized Layout**: 800×400 image format for better horizontal spacing
- **Improved Spacing**: 80% space for shapes, 20% for arrows to prevent overlap
- **Clear Separation**: Proper margins between all visual elements
- **Single Color Focus**: Blue color for all shapes to emphasize scale and style changes

### Rich Animation
- **Two-Step Video**: Shows sequential revelation of both question marks
- **Step 1 Animation**: First ? gradually changes scale (25 frames)
- **Step 2 Animation**: Second ? gradually converts from filled to outline (25 frames)
- **Smooth Transitions**: Clear visual progression through transformation steps

## 🎨 Visual Elements

### Shapes
- **10 Shape Types**: square, triangle, circle, diamond, pentagon, hexagon, rectangle, oval, star, heart
- **Consistent Style**: All shapes use blue color with black outlines

### Scale Levels
- **4 Scale Factors**: small (0.8×), medium (1.0×), large (1.3×), extra_large (1.6×)
- **Balanced Range**: Significant differences while preventing overlap

### Fill Styles
- **Filled**: Full color fill with thin border (width=2)
- **Outline**: No fill, thicker border (width=3) for clear distinction

## 🚀 Quick Start

### Installation
```bash
pip install -e .
```

### Generate Tasks
```bash
python examples/generate.py --num-samples 10 --output data/my_tasks
```

### Configuration
Edit `src/config.py` to customize:
- Image dimensions (default: 800×400)
- Shape sizes and margins
- Video frame rates
- Output settings

## 📁 Output Structure

Each generated task includes:
```
task_id/
├── prompt.txt           # Task instruction
└── ground_truth.mp4     # Animated solution showing both steps
```

## 🎬 Video Animation Sequence

1. **Initial State**: Shows A→B→C :: D→?→? layout
2. **Step 1 Animation**: First ? reveals with scale transformation
3. **Step 2 Animation**: Second ? reveals with fill-to-outline transformation  
4. **Final State**: Complete sequence A→B→C :: D→E→F

## 🔧 Customization

### Adding New Scale Transformations
Modify `valid_transformations` in `src/generator.py`:
```python
self.valid_transformations = [
    ("small", "large", "filled", "outline"),      # Scale up + outline
    ("large", "small", "filled", "outline"),      # Scale down + outline
    # Add your combinations...
]
```

### Adjusting Fill Styles
Update fill style configurations:
```python
self.fill_styles = {
    "filled": {"fill": True, "outline_width": 2},
    "outline": {"fill": False, "outline_width": 3}
}
```

## 🧠 Cognitive Challenge

This task type tests:
- **Sequential Reasoning**: Understanding multi-step transformation patterns
- **Scale Perception**: Recognizing size changes and proportional relationships
- **Style Recognition**: Distinguishing filled vs outline-only shapes
- **Analogical Thinking**: Applying learned patterns to new shapes

## 📊 Task Complexity

- **Transformation Steps**: 2 (scale then fill-to-outline)
- **Shape Variations**: 10 different shapes
- **Scale Combinations**: 12 valid transformation pairs
- **Style Transformation**: Always filled → outline
- **Total Unique Tasks**: 10 × 10 × 12 = 1,200 possible combinations

## 🎯 Use Cases

- **Visual Reasoning Research**: Multi-step transformation understanding
- **AI Training Data**: Sequential pattern recognition tasks
- **Cognitive Assessment**: Two-step analogical reasoning evaluation
- **Educational Tools**: Teaching sequential logical thinking with visual elements

## 🔍 Example Task

**Visual Layout:**
```
small_filled_circle → large_filled_circle → large_outline_circle
small_filled_square →         ?           →         ?
```

**Solution:**
- First ?: large_filled_square (apply scale change)
- Second ?: large_outline_square (apply fill-to-outline change)

**Reasoning:** The pattern shows scale change first (small→large), then style change (filled→outline). Apply the same sequence to the square.

## 🎨 Visual Transformation Details

### Step 1: Scale Transformation
- **Small to Large**: 0.8× → 1.3× size increase
- **Medium to Extra Large**: 1.0× → 1.6× size increase
- **Large to Small**: 1.3× → 0.8× size decrease
- **Smooth Animation**: Gradual size interpolation over 25 frames

### Step 2: Fill-to-Outline Transformation
- **Phase 1**: Gradual fill opacity reduction (first 12 frames)
- **Phase 2**: Complete fill removal, outline emphasis (remaining 13 frames)
- **Border Enhancement**: Outline width increases from 2px to 3px
- **Visual Clarity**: Clear distinction between filled and outline states

## 🔬 Research Applications

- **Cognitive Development**: Understanding how humans process sequential visual transformations
- **AI Pattern Recognition**: Training models on multi-step visual reasoning
- **Educational Assessment**: Measuring analogical reasoning capabilities
- **Perceptual Studies**: Investigating scale and style change detection

---

Built with the Template Data Generator framework for creating high-quality visual reasoning datasets.