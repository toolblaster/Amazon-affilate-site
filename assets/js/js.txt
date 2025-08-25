document.addEventListener("DOMContentLoaded", () => {
// Check if the featured articles container exists
const featuredArticlesContainer = document.getElementById("featured-articles-container");
if (featuredArticlesContainer) {
// Fetch the data from the JSON file
fetch('assets/data/featured-articles.json')
.then(response => {
if (!response.ok) {
throw new Error('Network response was not ok');
}
return response.json();
})
.then(articles => {
// Loop through the articles and create HTML for each one
articles.forEach(article => {
const articleCard = document.createElement('div');
articleCard.classList.add('category-card'); // Reusing a CSS class from the homepage

articleCard.innerHTML = `
<h3>${article.title}</h3>
<p>${article.summary}</p>
<a href="${article.url}" class="cta-link">Read More</a>
`;

featuredArticlesContainer.appendChild(articleCard);
});
})
.catch(error => console.error('Error loading featured articles:', error));
}

// You can add more site-wide JavaScript functionality here.
// For example, a function for a mobile navigation menu.
});
