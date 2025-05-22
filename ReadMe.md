# Professional Photo Gallery - IFB500 - QUT - Stephen Vu

## Project Overview
Students will build a professional dark-themed photo gallery with carousel and hover effects. This project teaches advanced CSS techniques including animations, responsive design, and complex layouts.


---

## Step 1: Setting Up the HTML Structure (Day 1)

### 1.1 Create the Basic HTML File
Create a new file called `gallery.html` and start with this basic structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Photo Gallery</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        /* CSS will go here */
    </style>
</head>
<body>
    <!-- Content will go here -->
</body>
</html>
```

### 1.2 Add the Header Section
Inside the `<body>` tags, add:

```html
<header>
    <div class="logo">LUMINA</div>
    <div class="tagline">Professional Photography Gallery</div>
</header>
```

### 1.3 Add the Main Gallery Structure
After the header, add:

```html
<main class="gallery-section">
    <h2 class="section-title">Featured Collections</h2>
    
    <!-- Carousel will go here -->
    <div class="carousel-container">
        <p>Carousel coming soon...</p>
    </div>

    <!-- Gallery grid will go here -->
    <div class="gallery-grid">
        <p>Gallery grid coming soon...</p>
    </div>
</main>
```

**🎯 Checkpoint:** Save and open in browser. You should see basic text content.

---

## Step 2: Basic Dark Theme Styling (Day 1 continued)

### 2.1 Add Reset and Body Styles
In the `<style>` section, add:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Inter', sans-serif;
    background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
    color: #e8e8e8;
    line-height: 1.6;
    min-height: 100vh;
}
```

### 2.2 Style the Header
Add these styles:

```css
header {
    padding: 2rem 0;
    text-align: center;
    background: rgba(0, 0, 0, 0.8);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid #333;
}

.logo {
    font-family: 'Playfair Display', serif;
    font-size: 2.5rem;
    font-weight: 700;
    color: #d4af37;
    margin-bottom: 0.5rem;
    letter-spacing: 2px;
}

.tagline {
    font-size: 1rem;
    color: #aaa;
    font-weight: 300;
    letter-spacing: 1px;
    text-transform: uppercase;
}
```

### 2.3 Style the Main Section
```css
.gallery-section {
    padding: 4rem 2rem;
    max-width: 1400px;
    margin: 0 auto;
}

.section-title {
    font-family: 'Playfair Display', serif;
    font-size: 2.2rem;
    text-align: center;
    margin-bottom: 3rem;
    color: #fff;
    position: relative;
}

.section-title::after {
    content: '';
    position: absolute;
    bottom: -10px;
    left: 50%;
    transform: translateX(-50%);
    width: 60px;
    height: 2px;
    background: linear-gradient(90deg, transparent, #d4af37, transparent);
}
```

**🎯 Checkpoint:** Refresh browser. You should see a dark theme with golden logo and styled title.

---

## Step 3: Building the Gallery Grid (Day 2)

### 3.1 Replace Gallery Grid Placeholder
Replace the gallery grid placeholder with actual gallery items:

```html
<div class="gallery-grid">
    <div class="gallery-item">
        <img src="/api/placeholder/300/250" alt="Street Photography">
        <div class="gallery-item-info">
            <div class="gallery-item-title">Street Life</div>
            <div class="gallery-item-category">Street Photography</div>
        </div>
    </div>
    <div class="gallery-item">
        <img src="/api/placeholder/300/250" alt="Fashion Photography">
        <div class="gallery-item-info">
            <div class="gallery-item-title">Fashion Forward</div>
            <div class="gallery-item-category">Fashion</div>
        </div>
    </div>
    <div class="gallery-item">
        <img src="/api/placeholder/300/250" alt="Nature Photography">
        <div class="gallery-item-info">
            <div class="gallery-item-title">Wild Moments</div>
            <div class="gallery-item-category">Nature</div>
        </div>
    </div>
    <!-- Add 3 more gallery items with different titles and categories -->
</div>
```

### 3.2 Style the Gallery Grid
Add these CSS rules:

```css
.gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 3rem;
}

.gallery-item {
    position: relative;
    overflow: hidden;
    border-radius: 10px;
    background: #222;
    transition: transform 0.4s ease, box-shadow 0.4s ease;
    cursor: pointer;
}

.gallery-item img {
    width: 100%;
    height: 250px;
    object-fit: cover;
    transition: transform 0.6s ease;
}

.gallery-item-info {
    padding: 1.5rem;
    background: linear-gradient(135deg, #1a1a1a, #2a2a2a);
}

.gallery-item-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    color: #d4af37;
    margin-bottom: 0.5rem;
}

.gallery-item-category {
    color: #888;
    font-size: 0.85rem;
    text-transform: uppercase;
    letter-spacing: 1px;
}
```

**🎯 Checkpoint:** You should now see a responsive grid of gallery items.

---

## Step 4: Adding Hover Effects (Day 2 continued)

### 4.1 Add Hover Effects to Gallery Items
Add these hover effects to your existing CSS:

```css
.gallery-item:hover {
    transform: translateY(-10px);
    box-shadow: 0 15px 30px rgba(212, 175, 55, 0.2);
}

.gallery-item:hover img {
    transform: scale(1.1);
}
```

### 4.2 Add Smooth Animations
Add these animation styles:

```css
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.gallery-item {
    animation: fadeInUp 0.6s ease forwards;
}

.gallery-item:nth-child(1) { animation-delay: 0.1s; }
.gallery-item:nth-child(2) { animation-delay: 0.2s; }
.gallery-item:nth-child(3) { animation-delay: 0.3s; }
.gallery-item:nth-child(4) { animation-delay: 0.4s; }
.gallery-item:nth-child(5) { animation-delay: 0.5s; }
.gallery-item:nth-child(6) { animation-delay: 0.6s; }
```

**🎯 Checkpoint:** Hover over gallery items to see lift effect and image scaling. Page should load with staggered animation.

---

## Step 5: Building the Carousel - HTML Structure (Day 3)

### 5.1 Replace Carousel Placeholder
Replace the carousel placeholder with this structure:

```html
<div class="carousel-container">
    <input type="radio" name="carousel" id="slide1" checked>
    <input type="radio" name="carousel" id="slide2">
    <input type="radio" name="carousel" id="slide3">
    
    <div class="carousel">
        <div class="carousel-slide">
            <img src="/api/placeholder/1000/600" alt="Urban Architecture">
            <div class="slide-overlay">
                <div class="slide-title">Urban Architecture</div>
                <div class="slide-description">Capturing the essence of modern cityscapes.</div>
            </div>
        </div>
        <div class="carousel-slide">
            <img src="/api/placeholder/1000/600" alt="Natural Portraits">
            <div class="slide-overlay">
                <div class="slide-title">Natural Portraits</div>
                <div class="slide-description">Intimate portraits in natural settings.</div>
            </div>
        </div>
        <div class="carousel-slide">
            <img src="/api/placeholder/1000/600" alt="Landscape Serenity">
            <div class="slide-overlay">
                <div class="slide-title">Landscape Serenity</div>
                <div class="slide-description">Breathtaking landscapes showcase nature's grandeur.</div>
            </div>
        </div>
    </div>
    
    <div class="carousel-nav">
        <input type="radio" name="carousel" id="nav1" checked>
        <label for="slide1"></label>
        <input type="radio" name="carousel" id="nav2">
        <label for="slide2"></label>
        <input type="radio" name="carousel" id="nav3">
        <label for="slide3"></label>
    </div>
</div>
```

**🎯 Checkpoint:** Save and refresh. You should see three images stacked vertically (we'll fix the layout next).

---

## Step 6: Carousel Styling (Day 3 continued)

### 6.1 Basic Carousel Layout
Add these styles:

```css
.carousel-container {
    position: relative;
    max-width: 1000px;
    margin: 0 auto 4rem;
    overflow: hidden;
    border-radius: 15px;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
}

.carousel {
    display: flex;
    transition: transform 0.6s cubic-bezier(0.4, 0.0, 0.2, 1);
}

.carousel-slide {
    min-width: 100%;
    position: relative;
}

.carousel-slide img {
    width: 100%;
    height: 600px;
    object-fit: cover;
    display: block;
}
```

### 6.2 Slide Overlay Effects
```css
.slide-overlay {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background: linear-gradient(transparent, rgba(0, 0, 0, 0.8));
    padding: 2rem;
    transform: translateY(100%);
    transition: transform 0.4s ease;
}

.carousel-slide:hover .slide-overlay {
    transform: translateY(0);
}

.slide-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    color: #d4af37;
    margin-bottom: 0.5rem;
}

.slide-description {
    color: #ccc;
    font-size: 0.9rem;
    line-height: 1.4;
}
```

**🎯 Checkpoint:** Hover over the carousel image to see the overlay slide up effect.

---

## Step 7: Carousel Navigation (Day 4)

### 7.1 Hide Radio Buttons and Style Labels
```css
.carousel-nav {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 10px;
    z-index: 10;
}

.carousel-nav input[type="radio"] {
    display: none;
}

.carousel-nav label {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.3);
    cursor: pointer;
    transition: all 0.3s ease;
    border: 2px solid transparent;
}

.carousel-nav label:hover {
    background: rgba(212, 175, 55, 0.6);
    transform: scale(1.2);
}

.carousel-nav input[type="radio"]:checked + label {
    background: #d4af37;
    border-color: #fff;
    transform: scale(1.3);
}
```

### 7.2 Make Carousel Functional
Add the magic CSS that makes the carousel work:

```css
#slide1:checked ~ .carousel { transform: translateX(0%); }
#slide2:checked ~ .carousel { transform: translateX(-100%); }
#slide3:checked ~ .carousel { transform: translateX(-200%); }
```

**🎯 Checkpoint:** Click the navigation dots to see the carousel slide between images!

---

## Step 8: Responsive Design (Day 4 continued)

### 8.1 Add Mobile Styles
```css
@media (max-width: 768px) {
    .logo {
        font-size: 2rem;
    }

    .gallery-section {
        padding: 2rem 1rem;
    }

    .carousel-slide img {
        height: 400px;
    }

    .gallery-grid {
        grid-template-columns: 1fr;
        gap: 1.5rem;
    }
}
```

**🎯 Checkpoint:** Resize your browser window to test mobile responsiveness.

---

## Step 9: Final Polish (Day 5)

### 9.1 Students Choose Their Own Content
Have students:
- Replace placeholder images with their own photos or themed images
- Update gallery titles and categories to match their interests
- Customize the color scheme (change #d4af37 to their preferred accent color)
- Update the site name and tagline

### 9.2 Add Final Touches
Students can experiment with:
- Adding more carousel slides
- Changing animation durations
- Adjusting hover effects
- Creating their own color palettes

---

## Assessment Rubric

### Technical Skills (40 points)
- **HTML Structure (10 pts):** Proper semantic HTML, clean structure
- **CSS Layout (10 pts):** Grid and flexbox implementation
- **Animations (10 pts):** Smooth transitions and hover effects
- **Responsive Design (10 pts):** Works on different screen sizes

### Design & Creativity (30 points)
- **Visual Appeal (15 pts):** Professional appearance, good color choices
- **Content Quality (15 pts):** Appropriate images and text

### Problem Solving (20 points)
- **Debugging (10 pts):** Ability to fix issues independently
- **Code Organization (10 pts):** Clean, commented, organized code

### Presentation (10 points)
- **Demo (10 pts):** Can explain how features work

---

## Extension Challenges

**For Advanced Students:**
1. Add more carousel slides with automatic rotation
2. Create a lightbox effect for gallery images
3. Add filtering buttons for gallery categories
4. Implement smooth scrolling navigation
5. Add loading animations

**For Struggling Students:**
- Focus on completing Steps 1-4 (basic gallery grid)
- Simplify carousel to just HTML structure
- Use simpler hover effects (just color changes)

---

## Common Troubleshooting

**Carousel not working?**
- Check that radio button IDs match label `for` attributes
- Ensure the transform percentages are correct

**Images not showing?**
- Verify image paths are correct
- Check if placeholder URLs work in your environment

**Styles not applying?**
- Check for typos in CSS selectors
- Ensure CSS is inside `<style>` tags
- Validate HTML structure

**Hover effects not smooth?**
- Check transition properties are applied to base element, not hover state
- Verify transform-origin is set correctly

---

## Teacher Notes

- **Day 1:** Focus on structure and basic styling
- **Day 2:** Build the grid and add basic interactivity
- **Day 3:** Tackle the carousel (most challenging part)
- **Day 4:** Polish and responsive design
- **Day 5:** Customization and presentations

**Key Learning Objectives:**
- CSS Grid and Flexbox mastery
- Advanced CSS selectors and pseudo-classes
- Transform and transition properties
- Responsive design principles
- CSS-only interactive components
