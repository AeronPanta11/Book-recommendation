
<body>

<h1>Book Recommendation System</h1>

<h2>Overview</h2>
<p>This project implements a book recommendation system using collaborative filtering techniques. The system utilizes user ratings of books to suggest similar books based on a given title. The recommendation is based on the cosine similarity metric, which measures the distance between books in a multi-dimensional space defined by user ratings.</p>

<h2>Dataset</h2>
<p>The dataset used in this project consists of three CSV files:</p>
<ul>
    <li><strong>BX-Books.csv</strong>: Contains information about books, including ISBN, title, and author.</li>
    <li><strong>BX-Book-Ratings.csv</strong>: Contains user ratings for books, including user ID, ISBN, and rating.</li>
    <li><strong>BX-Users.csv</strong>: Contains user information (not used in this project).</li>
</ul>
<p>The dataset is sourced from <a href="https://cdn.freecodecamp.org/project-data/books/book-crossings.zip">FreeCodeCamp</a>.</p>

<h2>Libraries Used</h2>
<p>The following libraries are used in this project:</p>
<ul>
    <li><code>numpy</code>: For numerical operations.</li>
    <li><code>pandas</code>: For data manipulation and analysis.</li>
    <li><code>scipy</code>: For sparse matrix operations.</li>
    <li><code>sklearn</code>: For implementing the Nearest Neighbors algorithm.</li>
    <li><code>matplotlib</code>: For data visualization (not used in this implementation).</li>
</ul>

<h2>Installation</h2>
<p>To run this project, you need to have Python installed along with the required libraries. You can install the necessary libraries using pip:</p>
<pre><code>pip install numpy pandas scipy scikit-learn matplotlib</code></pre>

<h2>Usage</h2>
<ol>
    <li><strong>Download and Unzip the Dataset</strong>: The dataset is downloaded and unzipped using the following commands:
        <pre><code>!wget https://cdn.freecodecamp.org/project-data/books/book-crossings.zip
!unzip book-crossings.zip</code></pre>
    </li>
    <li><strong>Load the Data</strong>: The CSV files are loaded into pandas DataFrames.
        <pre><code>df_books = pd.read_csv('BX-Books.csv', encoding="ISO-8859-1", sep=";", header=0, names=['isbn', 'title', 'author'], usecols=['isbn', 'title', 'author'], dtype={'isbn': 'str', 'title': 'str', 'author': 'str'})
df_ratings = pd.read_csv('BX-Book-Ratings.csv', encoding="ISO-8859-1", sep=";", header=0, names=['user', 'isbn', 'rating'], usecols=['user', 'isbn', 'rating'], dtype={'user': 'int32', 'isbn': 'str', 'rating': 'float32'})</code></pre>
    </li>
    <li><strong>Data Cleaning</strong>: The data is cleaned by removing users with fewer than 200 ratings and books with fewer than 100 ratings.</li>
    <li><strong>Create User-Item Matrix</strong>: A pivot table is created to represent the user-item interactions, where rows represent books and columns represent users.</li>
    <li><strong>Model Training</strong>: The Nearest Neighbors model is trained using the user-item matrix.
        <pre><code>model = NearestNeighbors(metric='cosine')
model.fit(df.values)</code></pre>
    </li>
    <li><strong>Get Recommendations</strong>: You can get book recommendations by calling the <code>get_recommends</code> function with a book title.
        <pre><code>recommendations = get_recommends("The Queen of the Damned (Vampire Chronicles (Paperback))")</code></pre>
    </li>
</ol>

<h2>Example</h2>
<p>To get recommendations for a specific book, you can use the following code:</p>
<pre><code>books = get_recommends("Where the Heart Is (Oprah's Book Club (Paperback))")
print(books)</code></pre>

<h2>Testing</h2>
<p>A simple test function <code>test_book_recommendation</code> is provided to verify the correctness of the recommendation system. It checks if the recommended books match expected titles and distances.</p>

<h2>Conclusion</h2>
<p>This project demonstrates how to build a book recommendation system using collaborative filtering techniques. The system can be further improved by incorporating additional features such as book genres, user demographics, or using more advanced recommendation algorithms.</p>

<h2>License</h2>
<p>This project is licensed under the MIT License. Feel free to use and modify it as needed.</p>

</body>
</html>
"""

# Write the content to a README.html file
with open("README.html", "w") as readme_file:
    readme_file.write(readme_html_content)

print("README.html file has been created.")
