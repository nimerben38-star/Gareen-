<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GREEN - Video Sharing Platform</title>
    <style>
        /* Basic CSS for styling */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        /* Header with green icon */
        header {
            background-color: #28a745;
            color: white;
            padding: 10px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .green-icon {
            width: 40px;
            height: 40px;
            background-color: #218838;
            border-radius: 50%;
            display: inline-block;
        }

        nav a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
        }

        nav a:hover {
            text-decoration: underline;
        }

        /* Main content */
        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 0 20px;
        }

        /* Video, Shorts, Live Sections */
        .section {
            margin-bottom: 40px;
        }

        .section h2 {
            color: #28a745;
        }

        .video-grid, .shorts-grid, .live-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .video-card, .shorts-card, .live-card {
            background-color: white;
            padding: 10px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            text-align: center;
        }

        .video-card img, .shorts-card img, .live-card img {
            width: 100%;
            height: 150px;
            object-fit: cover;
            border-radius: 8px;
        }

        /* Upload Form */
        .upload-form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            margin-bottom: 40px;
        }

        .upload-form input, .upload-form textarea {
            width: 100%;
            margin: 10px 0;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .upload-form button {
            background-color: #28a745;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        .upload-form button:hover {
            background-color: #218838;
        }

        /* Profile Section */
        .profile {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .profile img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
        }

        /* Dashboard */
        .dashboard {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .video-grid, .shorts-grid, .live-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Header with Green Icon and Navigation -->
    <header>
        <div class="green-icon"></div>
        <h1>GREEN</h1>
        <nav>
            <a href="#home">Home</a>
            <a href="#dashboard">Dashboard</a>
            <a href="#profile">Profile</a>
        </nav>
    </header>

    <!-- Main Content -->
    <div class="container">
        <!-- Video Upload Form -->
        <div class="upload-form">
            <h2>Upload Video, Short, or Go Live</h2>
            <form id="uploadForm">
                <input type="text" id="title" placeholder="Video/Short Title" required>
                <textarea id="description" placeholder="Description" rows="4"></textarea>
                <input type="file" id="videoFile" accept="video/*" required>
                <select id="contentType">
                    <option value="video">Video</option>
                    <option value="short">Short</option>
                    <option value="live">Live</option>
                </select>
                <button type="submit">Upload</button>
            </form>
        </div>

        <!-- Videos Section -->
        <div class="section" id="videos">
            <h2>Videos</h2>
            <div class="video-grid" id="videoGrid">
                <!-- Videos will be dynamically added here -->
            </div>
        </div>

        <!-- Shorts Section -->
        <div class="section" id="shorts">
            <h2>Shorts</h2>
            <div class="shorts-grid" id="shortsGrid">
                <!-- Shorts will be dynamically added here -->
            </div>
        </div>

        <!-- Live Section -->
        <div class="section" id="live">
            <h2>Live Streams</h2>
            <div class="live-grid" id="liveGrid">
                <!-- Live streams will be dynamically added here -->
            </div>
        </div>

        <!-- Dashboard Section -->
        <div class="dashboard" id="dashboard">
            <h2>Dashboard</h2>
            <p>Welcome to your dashboard! Here you can manage your posts and view analytics.</p>
            <div>
                <h3>Your Recent Posts</h3>
                <ul id="recentPosts">
                    <!-- Recent posts will be dynamically added here -->
                </ul>
            </div>
        </div>

        <!-- Profile Section -->
        <div class="profile" id="profile">
            <h2>Profile</h2>
            <img src="https://via.placeholder.com/100" alt="Profile Picture">
            <h3>Username</h3>
            <p><strong>Bio:</strong> <span id="bio">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span></p>
            <button onclick="editBio()">Edit Bio</button>
        </div>
    </div>

    <!-- JavaScript for Interactivity -->
    <script>
        // Handle video/short/live upload
        document.getElementById('uploadForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const title = document.getElementById('title').value;
            const description = document.getElementById('description').value;
            const contentType = document.getElementById('contentType').value;
            const videoFile = document.getElementById('videoFile').files[0];

            // Simulate video upload (replace with actual backend logic)
            const card = document.createElement('div');
            card.className = `${contentType}-card`;
            card.innerHTML = `
                <img src="https://via.placeholder.com/150" alt="${title}">
                <h3>${title}</h3>
                <p>${description || 'No description'}</p>
            `;

            // Append to the appropriate section
            if (contentType === 'video') {
                document.getElementById('videoGrid').appendChild(card);
            } else if (contentType === 'short') {
                document.getElementById('shortsGrid').appendChild(card);
            } else if (contentType === 'live') {
                document.getElementById('liveGrid').appendChild(card);
            }

            // Add to recent posts in dashboard
            const postItem = document.createElement('li');
            postItem.textContent = `${title} (${contentType})`;
            document.getElementById('recentPosts').appendChild(postItem);

            // Reset form
            this.reset();
            alert('Content uploaded successfully!');
        });

        // Edit bio function
        function editBio() {
            const bio = document.getElementById('bio');
            const newBio = prompt('Enter your new bio:', bio.textContent);
            if (newBio) {
                bio.textContent = newBio;
            }
        }
    </script>
</body>
</html>
