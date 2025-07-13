# CodeAlpha_ImageGallery
CODE : 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Image Gallery</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      padding: 20px;
      background: linear-gradient(to bottom right, #f0f8ff, #e6e6fa);
      transition: background-color 0.5s ease;
    }

    h1 {
      text-align: center;
      font-size: 2.5em;
      margin-bottom: 20px;
      animation: bounce 1.5s ease;
      color: #6a5acd;
    }

    @keyframes bounce {
      0%   { transform: translateY(-50px); opacity: 0; }
      50%  { transform: translateY(20px); }
      100% { transform: translateY(0); opacity: 1; }
    }

    .filters {
      text-align: center;
      margin-bottom: 20px;
    }

    .filters button {
      padding: 10px 15px;
      margin: 5px;
      cursor: pointer;
      border: none;
      background: #6a5acd;
      color: white;
      font-weight: bold;
      border-radius: 4px;
    }

    .filters button.clicked {
      background: #32cd32;
      transform: scale(1.05);
      transition: transform 0.3s ease;
    }

    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 15px;
    }

    .gallery-item {
      position: relative;
      overflow: hidden;
    }

    .gallery-item img {
      width: 100%;
      display: block;
      transition: transform 0.4s ease;
      cursor: pointer;
      border-radius: 5px;
    }

    .gallery-item:hover img {
      transform: rotate(1deg) scale(1.08);
      border: 2px dashed #ff69b4;
    }

    .lightbox {
      position: fixed;
      display: none;
      justify-content: center;
      align-items: center;
      top: 0; left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0,0,0,0.9);
      z-index: 1000;
    }

    .lightbox-img {
      max-width: 80%;
      max-height: 80%;
      border: 5px solid white;
    }

    .close {
      position: absolute;
      top: 30px;
      right: 40px;
      font-size: 40px;
      color: white;
      cursor: pointer;
    }

    .nav {
      position: absolute;
      top: 50%;
      width: 100%;
      display: flex;
      justify-content: space-between;
      color: white;
      font-size: 50px;
      padding: 0 30px;
      cursor: pointer;
    }

    @media (max-width: 600px) {
      .gallery {
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
      }

      .lightbox-img {
        max-width: 95%;
        max-height: 95%;
      }
    }
  </style>
</head>
<body>

  <h1>My Image Gallery 💫</h1>

  <div class="filters">
    <button onclick="filterImages('all', event)">All</button>
    <button onclick="filterImages('nature', event)">Nature</button>
    <button onclick="filterImages('city', event)">City</button>
  </div>

  <div class="gallery">
    <div class="gallery-item nature"><img src="https://picsum.photos/id/1015/600/400" alt="Nature 1" /></div>
    <div class="gallery-item city"><img src="https://picsum.photos/id/1011/600/400" alt="City 1" /></div>
    <div class="gallery-item nature"><img src="https://picsum.photos/id/1016/600/400" alt="Nature 2" /></div>
    <div class="gallery-item city"><img src="https://picsum.photos/id/1020/600/400" alt="City 2" /></div>
    <div class="gallery-item nature"><img src="https://picsum.photos/id/1003/600/400" alt="Nature 3" /></div>
    <div class="gallery-item city"><img src="https://picsum.photos/id/1019/600/400" alt="City 3" /></div>
  </div>

  <div class="lightbox" id="lightbox">
    <span class="close" onclick="closeLightbox()">×</span>
    <img class="lightbox-img" id="lightbox-img" />
    <div class="nav">
      <span class="prev" onclick="changeSlide(-1)">❮</span>
      <span class="next" onclick="changeSlide(1)">❯</span>
    </div>
  </div>

  <script>
    const images = document.querySelectorAll('.gallery-item img');
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightbox-img');
    const imgList = Array.from(images);
    let currentIndex = 0;

    images.forEach((img, index) => {
      img.addEventListener('click', () => {
        lightbox.style.display = 'flex';
        lightboxImg.src = img.src;
        currentIndex = index;
      });
    });

    function closeLightbox() {
      lightbox.style.display = 'none';
    }

    function changeSlide(direction) {
      currentIndex += direction;
      if (currentIndex < 0) currentIndex = imgList.length - 1;
      if (currentIndex >= imgList.length) currentIndex = 0;
      lightboxImg.src = imgList[currentIndex].src;
    }

    function filterImages(category, event) {
      const items = document.querySelectorAll('.gallery-item');
      const buttons = document.querySelectorAll('.filters button');
      buttons.forEach(btn => btn.classList.remove('clicked'));
      event.target.classList.add('clicked');

      items.forEach(item => {
        if (category === 'all' || item.classList.contains(category)) {
          item.style.display = 'block';
        } else {
          item.style.display = 'none';
        }
      });
    }
  </script>

</body>
</html>

🌟 Image Gallery Project
A responsive, category-filterable image gallery with smooth animations and lightbox viewing, created using pure HTML, CSS, and vanilla JavaScript.
🚀 Features
Responsive grid layout
Lightbox view with next/prev navigation
Hover effects with smooth transitions
Category-based filtering (Nature / City / All)
Interactive UI with animated header
🔧 Technologies Used
HTML5
CSS3 (Grid, Flexbox, Transitions, Animations)
JavaScript (DOM Manipulation, Event Handling)
