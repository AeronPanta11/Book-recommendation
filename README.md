Book Recommendation System
Overview
This project implements a book recommendation system using collaborative filtering techniques. The system utilizes user ratings of books to suggest similar books based on a given title. The recommendation is based on the cosine similarity metric, which measures the distance between books in a multi-dimensional space defined by user ratings.

Dataset
The dataset used in this project consists of three CSV files:

BX-Books.csv: Contains information about books, including ISBN, title, and author.
BX-Book-Ratings.csv: Contains user ratings for books, including user ID, ISBN, and rating.
BX-Users.csv: Contains user information (not used in this project).
The dataset is sourced from FreeCodeCamp.

Libraries Used
The following libraries are used in this project:

numpy: For numerical operations.
pandas: For data manipulation and analysis.
scipy: For sparse matrix operations.
sklearn: For implementing the Nearest Neighbors algorithm.
matplotlib: For data visualization (not used in this implementation).
Installation
To run this project, you need to have Python installed along with the required libraries. You can install the necessary libraries using pip:

bash
Run
Copy code
pip install numpy pandas scipy scikit-learn matplotlib
Usage
Download and Unzip the Dataset: The dataset is downloaded and unzipped using the following commands:

python
Run
Copy code
!wget https://cdn.freecodecamp.org/project-data/books/book-crossings.zip
!unzip book-crossings.zip
Load the Data: The CSV files are loaded into pandas DataFrames.

python
Run
Copy code
df_books = pd.read_csv('BX-Books.csv', encoding="ISO-8859-1", sep=";", header=0, names=['isbn', 'title', 'author'], usecols=['isbn', 'title', 'author'], dtype={'isbn': 'str', 'title': 'str', 'author': 'str'})
df_ratings = pd.read_csv('BX-Book-Ratings.csv', encoding="ISO-8859-1", sep=";", header=0, names=['user', 'isbn', 'rating'], usecols=['user', 'isbn', 'rating'], dtype={'user': 'int32', 'isbn': 'str', 'rating': 'float32'})
Data Cleaning: The data is cleaned by removing users with fewer than 200 ratings and books with fewer than 100 ratings.

Create User-Item Matrix: A pivot table is created to represent the user-item interactions, where rows represent books and columns represent users.

Model Training: The Nearest Neighbors model is trained using the user-item matrix.

python
Run
Copy code
model = NearestNeighbors(metric='cosine')
model.fit(df.values)
Get Recommendations: You can get book recommendations by calling the get_recommends function with a book title.

python
Run
Copy code
recommendations = get_recommends("The Queen of the Damned (Vampire Chronicles (Paperback))")
Example
To get recommendations for a specific book, you can use the following code:

python
Run
Copy code
books = get_recommends("Where the Heart Is (Oprah's Book Club (Paperback))")
print(books)
Testing
A simple test function test_book_recommendation is provided to verify the correctness of the recommendation system. It checks if the recommended books match expected titles and distances.

Conclusion
This project demonstrates how to build a book recommendation system using collaborative filtering techniques. The system can be further improved by incorporating additional features such as book genres, user demographics, or using more advanced recommendation algorithms.

License
This project is licensed under the MIT License. Feel free to use and modify it as needed.
