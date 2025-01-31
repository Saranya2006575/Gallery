# Ex.08 Design of Interactive Image Gallery
# Date:21.12.2024
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cartoon Photo Gallery</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            background: linear-gradient(135deg, #1e1e2f, #2a2a3f);
            color: #fff;
            overflow-x: hidden;
            animation: bgAnimation 10s infinite alternate;
        }
        @keyframes bgAnimation {
            0% { background: linear-gradient(135deg, #1e1e2f, #2a2a3f); }
            50% { background: linear-gradient(135deg, #3f2a70, #1e1e2f); }
            100% { background: linear-gradient(135deg, #2a2a3f, #1e1e2f); }
        }
        h1 {
            text-align: center;
            margin: 20px 0;
            font-size: 3rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: #b6b39e;
            animation: glow 2s infinite alternate;
        }
        @keyframes glow {
            0% { text-shadow: 0 0 10px #d5d3c2, 0 0 20px #dfdccb; }
            100% { text-shadow: 0 0 20px #bebcae, 0 0 40px #d6d1b3; }
        }
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            padding: 20px;
            margin: 0 auto;
            max-width: 1200px;
        }
        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 15px;
            transition: transform 0.4s, box-shadow 0.4s;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.5);
        }
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s;
        }
        .gallery-item:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(171, 3, 162, 0.5);
        }
        .gallery-item:hover img {
            transform: scale(1.2);
        }
        .caption {
            position: absolute;
            bottom: 0;
            background: rgba(0, 0, 0, 0.6);
            width: 100%;
            text-align: center;
            padding: 12px 0;
            font-size: 1.2rem;
            text-transform: capitalize;
            color: #fff;
            transition: all 0.4s ease-in-out;
        }
        .gallery-item:hover .caption {
            background: rgba(212, 23, 171, 0.8);
        }
        #lightbox {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            align-items: center;
            justify-content: center;
            z-index: 1000;
            animation: fadeIn 0.5s forwards;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; }
        }
        #lightbox img {
            max-width: 90%;
            max-height: 90%;
            border: 4px solid #be199d;
            border-radius: 12px;
            animation: zoomIn 0.3s forwards;
        }
        @keyframes zoomIn {
            from { transform: scale(0.8); }
            to { transform: scale(1); }
        }
        #lightbox span {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 2rem;
            color: #fff;
            cursor: pointer;
            transition: color 0.3s;
        }
        #lightbox span:hover {
            color: #ab137a;
        }
    </style>
</head>
<body>
    <h1>CARTOON Photo Gallery</h1>
    <div class="gallery" id="gallery">
        <!-- Celebrity Images -->
        <div class="gallery-item">
            <img src="army.png" alt="BT21">
            <div class="caption">ARMY</div>
        </div>
        <div class="gallery-item">
            <img src="RJ.png" alt="RJ">
            <div class="caption">RJ</div>
        </div>
        <div class="gallery-item">
            <img src="suga.png" alt="SUGA">
            <div class="caption">SUGA</div>
        </div>
        <div class="gallery-item">
            <img src="hobi.png" alt="HOBI">
            <div class="caption">HOBI</div>
        </div>
        <div class="gallery-item">
            <img src="koya.png" alt="KOYA">
            <div class="caption">KOYA</div>
        </div>
        <div class="gallery-item">
            <img src="jimmy.png" alt="JIMMY">
            <div class="caption">JIMMY</div>
        </div>
        <div class="gallery-item">
            <img src="taetae.png" alt="TAETAE">
            <div class="caption">TAETAE</div>
        </div>
        <div class="gallery-item">
            <img src="kookie.png" alt="KOOKIE">
            <div class="caption">KOOKIE</div>
        </div>
    </div>
    
    <div id="lightbox">
        <span id="closeLightbox">&times;</span>
        <img src="" alt="Large Image" id="lightboxImg">
    </div>

    <script>
        const galleryItems = document.querySelectorAll('.gallery-item img');
        const lightbox = document.getElementById('lightbox');
        const lightboxImg = document.getElementById('lightboxImg');
        const closeLightbox = document.getElementById('closeLightbox');
        let currentIndex = 0;

        function openLightbox(index) {
            currentIndex = index;
            lightboxImg.src = galleryItems[index].src;
            lightbox.style.display = 'flex';
        }

        function close() {
            lightbox.style.display = 'none';
        }

        galleryItems.forEach((img, index) => {
            img.addEventListener('click', () => openLightbox(index));
        });

        closeLightbox.addEventListener('click', close);
    </script>
    <footer align="center" id="copywrite">
        Designed and developed by saranya &copy 2024
    </footer>
</body>
</html>

```
# OUTPUT:
![alt text](<Screenshot 2024-12-21 231742.png>)

![Screenshot (5)](https://github.com/user-attachments/assets/5d4d7d2c-38bb-40d3-8717-bf495aa5fec6)

![Screenshot (7)](https://github.com/user-attachments/assets/ec1eb21b-edcd-4cc7-a17e-f798bfd16efc)

![Screenshot (6)](https://github.com/user-attachments/assets/f34b286d-e715-4ac3-8dcd-3d193d0ff39a)

![Screenshot (9)](https://github.com/user-attachments/assets/9dd0d935-baa9-4b5d-b562-76abd2937ca3)



# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
