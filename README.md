# day-20-task
java script
// Function to fetch data from an API
function fetchData(url) {
    return fetch(url)
        .then(response => {
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            return response.json();
        })
        .catch(error => {
            console.error('There was a problem with the fetch operation:', error);
        });
}

// Function to display data on the webpage
function displayData(data) {
    const container = document.querySelector('.container');
    
    // Clear previous content
    container.innerHTML = '';

    // Create a grid layout
    const grid = document.createElement('div');
    grid.className = 'grid';

    data.forEach(item => {
        // Create a card for each item
        const card = document.createElement('div');
        card.className = 'card';

        // Add image
        const img = document.createElement('img');
        img.src = item.imageUrl;
        img.alt = item.title;
        card.appendChild(img);

        // Add title
        const title = document.createElement('h2');
        title.textContent = item.title;
        card.appendChild(title);

        // Add description
        const description = document.createElement('p');
        description.textContent = item.description;
        card.appendChild(description);

        // Append card to grid
        grid.appendChild(card);
    });

    // Append grid to container
    container.appendChild(grid);
}

// Fetch data and display it
document.addEventListener('DOMContentLoaded', () => {
    fetchData('https://api.example.com/data')
        .then(data => {
            displayData(data);
        });
});


css
/* Base styles */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

/* Container styles */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

/* Responsive grid layout */
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 20px;
}

/* Card styles */
.card {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 16px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.card img {
    max-width: 100%;
    border-radius: 8px;
}

.card h2 {
    font-size: 1.5rem;
    margin: 0 0 10px;
}

.card p {
    font-size: 1rem;
    margin: 0;
}

/* Responsive breakpoints */
@media (max-width: 768px) {
    .grid {
        grid-template-columns: 1fr;
    }
}



html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive UI with Dynamic Data</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <!-- Data will be inserted here by JavaScript -->
    </div>
    <script src="script.js"></script>
</body>
</html>
