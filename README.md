# Ex05 Image Carousel
## Date:

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM

### App.js
```
import React from "react";
import "./App.css";
import Carousel from "./Carousel";
import Footer from "./Footer";

function App() {
  return (
    <div className="app">
      <h1 className="title">Image Carousel</h1>

      {/* Carousel Component */}
      <Carousel />

      {/* Footer Component */}
      <Footer />
    </div>
  );
}

export default App;

```
### App.css
```
.app {
  text-align: center;
  margin-top: 40px;
  background-color: #f0f4f8;
  width: 650px;
  margin-left: auto;
  margin-right: auto;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 0 15px rgba(0,0,0,0.2);
}

.title {
  font-size: 2rem;
  margin-bottom: 20px;
}

```
### Carousel.js
```
import React, { useState, useEffect } from "react";
import "./Carousel.css";

function Carousel() {
  // STEP 1: Input (List of real images)
  const images = [
    "https://picsum.photos/id/1018/600/400", // random nature image
    "https://picsum.photos/id/1015/600/400", // random river image
    "https://picsum.photos/id/1016/600/400", // random mountain image
    "https://picsum.photos/id/1019/600/400"  // random forest image
  ];

  // STEP 2: State management
  const [currentIndex, setCurrentIndex] = useState(0);

  // STEP 3: Navigation controls
  const nextImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex - 1 + images.length) % images.length);
  };

  // STEP 5: Auto-rotation (every 3 seconds)
  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval); // cleanup
  }, []);

  // STEP 4: Display current image
  return (
    <div className="carousel">
      <img
        src={images[currentIndex]}
        alt={`carousel-${currentIndex}`}
        className="carousel-image"
      />

      {/* Buttons */}
      <div className="buttons">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
}

export default Carousel;

```
### Carousel.css
```
.carousel {
  width: 600px;
  margin: 0 auto;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 0 10px #aaa;
}

.carousel-image {
  width: 100%;
  height: auto;
  display: block;
}

.buttons {
  margin-top: 15px;
}

button {
  margin: 0 10px;
  padding: 10px 20px;
  font-size: 1rem;
  cursor: pointer;
  border: none;
  border-radius: 6px;
  background-color: #007bff;
  color: white;
  transition: 0.3s;
}

button:hover {
  background-color: #0056b3;
}

```
### Footer.js
```
import React from "react";
import "./Footer.css";

function Footer() {
  return (
    <div className="footer">
      © 2025 My Carousel App. All rights reserved.
    </div>
  );
}

export default Footer;

```
### Footer.css
```
.footer {
  margin-top: 30px;
  font-size: 1rem;
  color: #555;
  font-style: italic;
}

```

## OUTPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9acda14b-90d4-4d01-bed0-6243e0ecf7d6" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4fb90f8f-8648-4de6-8a36-7b353cab68b2" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
