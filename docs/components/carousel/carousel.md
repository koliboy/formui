
# Carousel

The carousel component allows you to create a slideshow of content with various options for customization.

##  Options:

1. **c-slider-type**: (Default: "autom") Specifies the type of carousel behavior.
   - "play": Auto-plays the carousel.
   - "loop": Allows looping through slides continuously.
   - "contain": Contains the slides  sliding .

2. **c-slider-btn**: (Default: "bottom") Specifies the placement of navigation buttons.
   - "top": Places navigation buttons at the top of the carousel.
   - "bottom": Places navigation buttons at the bottom of the carousel.
   - "outer": Places navigation buttons outside the carousel frame.
   - "inner": Places navigation buttons inside the carousel frame.

3. **c-slider-btn-mb**: (Default: Disabled) Enables or disables navigation buttons on mobile devices.
   - Enabled: Shows navigation buttons on mobile devices.
   - Disabled: Hides navigation buttons on mobile devices.

4. **c-slider-tabs**: (Default: Disabled) Enables or disables slide indicators (dots or tabs).
   - Enabled: Shows slide indicators.
   - Disabled: Hides slide indicators.

5. **c-slider-delay**: (Default: None) Specifies the delay time for auto-play in "play" mode.

### Adjus
Here's the adjusted CSS code with the provided comments:

```css
/* Adjust */
.carousel {
    max-width: 800px; /* Set the maximum width of the carousel */
    height: auto; /* Allow the height to adjust automatically */
}

/* Default .x-item 100%; height: auto */

/* Customize */
.carousel-ctn .x-item {
    min-width: 70%; 
}
```

In this adjusted CSS:

- The `.carousel` class has a `max-width` property set to `800px` to limit the maximum width of the carousel container.
- The `.carousel` class also has a `height` property set to `auto` to allow the height of the carousel to adjust automatically based on its content.

- 
### Examples:

#### Default:
```html
<div class="carousel" c-slider-tabs="t">
  <div class="carousel-ctn">  
    <div class="x-item">
      <img class="img" src="">
    </div>
    <div class="x-item">
      <img class="img" src="">
    </div> 
  </div>
</div>
```

#### Loop:
```html
<div class="carousel" c-slider-type="loop" c-slider-tabs="t">
  <div class="carousel-ctn">  
    <div class="x-item">
      <img class="img" src="">
    </div>
    <div class="x-item">
      <img class="img" src="">
    </div> 
    <div class="x-item">
      <img class="img" src="">
    </div> 
    <div class="x-item">
      <img class="img" src="">
    </div> 
  </div>
</div>
```

#### Play:
```html
<div class="carousel" c-slider-type="play" c-slider-delay="5s" c-slider-tabs="t">
  <div class="carousel-ctn">  
    <div class="x-item">
      <img class="img" src="">
    </div>
    <div class="x-item">
      <img class="img" src="">
    </div> 
  </div>
</div>
```

#### Contain:
```html
<style>
   /* Adjust contain */
   .carousel-ctn .x-item {
      min-width: 50%;
   }
</style>

<div class="carousel" c-slider-type="contain">
  <div class="carousel-ctn">  
    <div class="x-item">
      <img class="img" src="">
    </div>
    <div class="x-item">
      <img class="img" src="">
    </div> 
  </div>
</div>
```

#### Other Example:
```html
<div class="carousel" c-slider-type="loop" c-slider-tabs="t">
  <div class="carousel-ctn">  
    <div class="x-item">
      <div>Slide 1</div>
    </div>
    <div class="x-item">
      <div>Slide 2</div>
    </div> 
    <div class="x-item">
      Slide 3
    </div> 
  </div>
</div>
```

This documentation provides a comprehensive overview of the carousel component, its options, and usage examples to help you integrate it effectively into your projects.

Here's an example of a carousel with background images for each slide:

```html
<div class="carousel" c-slider-type="loop" c-slider-tabs="t">
  <div class="carousel-ctn">  
    <div class="x-item" style="background-image: url('image1.jpg');">
      <!-- Content for Slide 1 -->
    </div>
    <div class="x-item" style="background-image: url('image2.jpg');">
      <!-- Content for Slide 2 -->
    </div> 
    <div class="x-item" style="background-image: url('image3.jpg');">
      <!-- Content for Slide 3 -->
    </div> 
  </div>
</div>
```


Here are some examples demonstrating different placements of carousel control buttons (`c-slider-btn`):

### Example 1: Bottom Placement

```html
<div class="carousel" c-slider-type="loop" c-slider-btn="bottom">
  <div class="carousel-ctn">  
    <!-- Slide content goes here -->
  </div>
</div>
```

In this example, the control buttons (previous and next) are placed at the bottom of the carousel.

### Example 2: Top Placement

```html
<div class="carousel" c-slider-type="loop" c-slider-btn="top">
  <div class="carousel-ctn">  
    <!-- Slide content goes here -->
  </div>
</div>
```

In this example, the control buttons (previous and next) are placed at the top of the carousel.

### Example 3: Inner Placement

```html
<div class="carousel" c-slider-type="loop" c-slider-btn="inner">
  <div class="carousel-ctn">  
    <!-- Slide content goes here -->
  </div>
</div>
```

In this example, the control buttons (previous and next) are placed inside the carousel container.

### Example 4: Outer Placement

```html
<div class="carousel" c-slider-type="loop" c-slider-btn="outer">
  <div class="carousel-ctn">  
    <!-- Slide content goes here -->
  </div>
</div>
```

In this example, the control buttons (previous and next) are placed outside the carousel container.

You can choose the placement that best fits your design and layout requirements by setting the `c-slider-btn` attribute accordingly.

Certainly! Here's an example of customizing the play animation for the carousel:

```html
<div class="carousel" c-slider-type="play" c-slider-tabs="t">
  <div class="carousel-ctn">  
    <!-- Slide content goes here -->
  </div>
</div>
```

```css
/* Define custom animations */
@keyframes custom-slider-play {
    0% {
        opacity: 0;
        transform: translateY(-50%);
    }
    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Apply custom animation for the play type carousel */
.carousel[c-slider-type="play"] .carousel-ctn .x-item[is-current] {
    animation-name: custom-slider-play;
    animation-duration: 1s; /* Adjust the duration as needed */
    animation-fill-mode: forwards;
}
```

In this example:

- We have a carousel with `c-slider-type="play"`, indicating that it automatically plays through the slides.
- The `custom-slider-play` keyframes define the custom animation for transitioning between slides.
- The animation moves the slides vertically (`transform: translateY()`) and fades them in (`opacity`) to provide a smooth transition effect.
- Adjust the animation properties such as duration (`animation-duration`) and easing (`animation-timing-function`) according to your design preferences and requirements.

It seems like you're trying to select elements based on multiple conditions within a CSS selector. Unfortunately, CSS does not support selecting elements based on multiple conditions like you've attempted. Instead, you would need to separate these conditions into individual selectors or use a more specific approach.

If you want to style elements with both `is-current` and `play-delay` attributes under a carousel with `c-slider-type="play"`, you would need to apply separate styles for each condition. Here's how you can do it:

```css
/* Style for elements with is-current attribute */
.carousel[c-slider-type="play"] .carousel-ctn .x-item[is-current] {
    /* Your styles here */
}

/* Style for elements with play-delay attribute */
.carousel[c-slider-type="play"] .carousel-ctn .x-item[play-delay] {
    /* Your styles here */
}
```

If you're looking to style elements that have both attributes simultaneously, CSS cannot directly handle that. You may need to use JavaScript to apply styles based on multiple conditions or consider restructuring your HTML/CSS to accommodate your styling needs differently.
