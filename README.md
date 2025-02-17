<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Our Memories</title>
    
    <!-- 確保 Google Fonts 正確載入 -->
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&display=swap" rel="stylesheet">
    
    <style>
        body {
            font-family: 'Dancing Script', cursive;
            text-align: center;
            background: url('background.jpg') no-repeat center center fixed;
            background-size: cover;
            margin: 0;
            padding: 0;
            position: relative;
        }
        .gallery {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 60vh;
            position: relative;
        }
        .gallery img, .gallery video {
            width: 300px;
            height: 300px;
            object-fit: cover;
            border-radius: 15px;
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
            position: absolute;
            opacity: 0;
            transition: opacity 1s;
        }
        .quote {
            font-size: 22px;
            font-weight: bold;
            margin-top: 20px;
            color: #ff69b4;
        }
    </style>
</head>
<body>
    <h1>Our Memories</h1>
    <div class="gallery" id="photo-gallery">
        <!-- 這裡會插入照片與影片 -->
    </div>
    <p class="quote">Maybe it is our imperfections which make us so perfect for one another.</p>
    
    <!-- 背景音樂 -->
    <audio id="bg-music" src="background-music.mp3" loop autoplay></audio>
    
    <script>
        const photos = [
            'photo1.jpg', 
            'photo2.jpg', 
            'photo3.jpg', 
            'photo4.jpg', 
            'photo5.jpg', 
            'photo6.jpg', 
            'photo7.jpg'
        ];
        const videoSrc = 'video.mp4'; // 替換為你的影片名稱
        
        const gallery = document.getElementById('photo-gallery');
        let currentIndex = 0;
        
        photos.forEach(photo => {
            const img = document.createElement('img');
            img.src = photo;
            img.alt = 'Memory Photo';
            gallery.appendChild(img);
        });
        
        // 加入影片
        const video = document.createElement('video');
        video.src = videoSrc;
        video.controls = true;
        video.style.opacity = '0';
        gallery.appendChild(video);
        
        function showNextMedia() {
            const media = document.querySelectorAll('.gallery img, .gallery video');
            media.forEach(item => item.style.opacity = '0');
            
            if (currentIndex < photos.length) {
                media[currentIndex].style.opacity = '1';
                currentIndex++;
            } else {
                video.style.opacity = '1';
                video.play();
            }
        }
        
        showNextMedia();
        setInterval(() => {
            if (currentIndex <= photos.length) {
                showNextMedia();
            }
        }, 5000);
    </script>
</body>
</html>
