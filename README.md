<!DOCTYPE html>
<html lang="en">
<head>
    <meta name="google-site-verification" content="A-4p4bSXZAHxDuxv4iwBbFI3JTFTqXWHlW0JQuoHWrw" />
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Memes Hub - Disease Meme Videos</title>
    <style>
        body {
            margin: 0;
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #0d1b2a 0%, #1b263b 100%);
            color: #e0e1dd;
            overflow-x: hidden;
        }

        /* Digital Background Animation */
        .background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100"><rect width="100" height="100" fill="none"/><path d="M0 50h100M50 0v100" stroke="#415a77" stroke-width="0.5"/></svg>') repeat;
            opacity: 0.1;
            z-index: -1;
            animation: digitalFlow 20s linear infinite;
        }

        @keyframes digitalFlow {
            0% { background-position: 0 0; }
            100% { background-position: 100px 100px; }
        }

        /* Header */
        header {
            background: rgba(27, 38, 59, 0.9);
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        h1 {
            margin: 0;
            font-size: 2em;
            color: #00ddeb;
            text-shadow: 0 0 10px #00ddeb;
        }

        .search-bar {
            display: flex;
            align-items: center;
        }

        #searchInput {
            padding: 10px;
            border: none;
            border-radius: 20px 0 0 20px;
            background: #e0e1dd;
            color: #0d1b2a;
            outline: none;
        }

        #searchButton {
            padding: 10px 20px;
            border: none;
            border-radius: 0 20px 20px 0;
            background: #00ddeb;
            color: #0d1b2a;
            cursor: pointer;
            transition: background 0.3s;
        }

        #searchButton:hover {
            background: #0096a1;
        }

        /* Post Button */
        #postButton {
            padding: 10px 20px;
            border: none;
            border-radius: 20px;
            background: #ff4d6d;
            color: #e0e1dd;
            cursor: pointer;
            transition: background 0.3s;
        }

        #postButton:hover {
            background: #d93a56;
        }

        /* Post Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 200;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: #1b263b;
            padding: 20px;
            border-radius: 10px;
            width: 90%;
            max-width: 500px;
            position: relative;
        }

        .close {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 20px;
            cursor: pointer;
            color: #e0e1dd;
        }

        .modal-content h2 {
            margin-top: 0;
            color: #00ddeb;
        }

        .modal-content input,
        .modal-content textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            background: #e0e1dd;
            color: #0d1b2a;
        }

        .modal-content button {
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            background: #00ddeb;
            color: #0d1b2a;
            cursor: pointer;
        }

        .modal-content button:hover {
            background: #0096a1;
        }

        /* Video Grid */
        .video-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            padding: 20px;
        }

        .video-container {
            position: relative;
            background: #1b263b;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        .video-container video {
            width: 100%;
            height: auto;
            display: block;
        }

        .video-info {
            padding: 10px;
        }

        .video-info h3 {
            margin: 0;
            font-size: 1.2em;
            color: #00ddeb;
        }

        .video-info p {
            margin: 5px 0 0;
            font-size: 0.9em;
            color: #e0e1dd;
        }

        /* Three-Dot Menu */
        .three-dot-menu {
            position: absolute;
            top: 10px;
            right: 10px;
            cursor: pointer;
            color: #e0e1dd;
            font-size: 20px;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            top: 30px;
            right: 0;
            background: #1b263b;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
            z-index: 10;
        }

        .dropdown-content a {
            display: block;
            padding: 10px;
            color: #e0e1dd;
            text-decoration: none;
            transition: background 0.3s;
        }

        .dropdown-content a:hover {
            background: #00ddeb;
            color: #0d1b2a;
        }

        .show {
            display: block;
        }
    </style>
</head>
<body>
    <div class="background"></div>
    <header>
        <h1>Memes Hub</h1>
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Search disease memes...">
            <button id="searchButton">Search</button>
        </div>
        <button id="postButton">Post Meme Video</button>
    </header>

    <!-- Post Modal -->
    <div id="postModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <h2>Upload Disease Meme Video</h2>
            <input type="text" id="videoTitle" placeholder="Video Title">
            <textarea id="videoDescription" placeholder="Description (e.g., disease topic)"></textarea>
            <input type="file" id="videoFile" accept="video/mp4,video/webm" onchange="validateVideoDuration(this)">
            <button id="submitVideo">Submit</button>
        </div>
    </div>

    <!-- Video Grid -->
    <div class="video-grid" id="videoGrid">
        <!-- Sample Videos (Replace with actual content) -->
        <div class="video-container" data-title="Flu Meme" data-description="Funny flu symptoms">
            <video autoplay muted loop>
                <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
            <div class="three-dot-menu" onclick="toggleDropdown(this)">&#8942;</div>
            <div class="dropdown-content">
                <a href="https://www.w3schools.com/html/mov_bbb.mp4" download>Download</a>
            </div>
            <div class="video-info">
                <h3>Flu Meme</h3>
                <p>Funny flu symptoms</p>
            </div>
        </div>
        <div class="video-container" data-title="Cold Meme" data-description="Sneezing chaos">
            <video autoplay muted loop>
                <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
            <div class="three-dot-menu" onclick="toggleDropdown(this)">&#8942;</div>
            <div class="dropdown-content">
                <a href="https://www.w3schools.com/html/mov_bbb.mp4" download>Download</a>
            </div>
            <div class="video-info">
                <h3>Cold Meme</h3>
                <p>Sneezing chaos</p>
            </div>
        </div>
    </div>

    <script>
        // Search Functionality
        document.getElementById('searchButton').addEventListener('click', () => {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const videos = document.querySelectorAll('.video-container');
            videos.forEach(video => {
                const title = video.getAttribute('data-title').toLowerCase();
                const description = video.getAttribute('data-description').toLowerCase();
                video.style.display = (title.includes(query) || description.includes(query)) ? '' : 'none';
            });
        });

        // Post Modal
        const modal = document.getElementById('postModal');
        const postButton = document.getElementById('postButton');
        const closeModal = document.querySelector('.close');

        postButton.addEventListener('click', () => {
            modal.style.display = 'flex';
        });

        closeModal.addEventListener('click', () => {
            modal.style.display = 'none';
        });

        window.addEventListener('click', (event) => {
            if (event.target === modal) {
                modal.style.display = 'none';
            }
        });

        // Video Duration Validation
        function validateVideoDuration(input) {
            const file = input.files[0];
            if (file) {
                const video = document.createElement('video');
                video.preload = 'metadata';
                video.onloadedmetadata = () => {
                    window.URL.revokeObjectURL(video.src);
                    const duration = video.duration;
                    if (duration < 30 || duration > 60) {
                        alert('Please upload a video between 30 seconds and 1 minute.');
                        input.value = '';
                    }
                };
                video.src = URL.createObjectURL(file);
            }
        }

        // Submit Video (Placeholder)
        document.getElementById('submitVideo').addEventListener('click', () => {
            const title = document.getElementById('videoTitle').value;
            const description = document.getElementById('videoDescription').value;
            const file = document.getElementById('videoFile').files[0];
            if (title && description && file) {
                alert('Video submitted! (Note: Backend required for actual upload.)');
                modal.style.display = 'none';
                // Reset form
                document.getElementById('videoTitle').value = '';
                document.getElementById('videoDescription').value = '';
                document.getElementById('videoFile').value = '';
            } else {
                alert('Please fill all fields.');
            }
        });

        // Three-Dot Menu Toggle
        function toggleDropdown(element) {
            const dropdown = element.nextElementSibling;
            document.querySelectorAll('.dropdown-content').forEach(menu => {
                if (menu !== dropdown) menu.classList.remove('show');
            });
            dropdown.classList.toggle('show');
        }

        // Close Dropdowns on Click Outside
        window.addEventListener('click', (event) => {
            if (!event.target.matches('.three-dot-menu')) {
                document.querySelectorAll('.dropdown-content').forEach(menu => {
                    menu.classList.remove('show');
                });
            }
        });
    </script>
</body>
</html>
# Memes-hub 
