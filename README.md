In this assignment I extracted data from The New York Times API and The Movie Dtabase.

I referenced in-class acitivities as well as the documentations for building both the NYT and TMDB urls.

# Accessing NYT API
I was provided with the base url and the query parameters which I used to build my query url.

I followed the instruction given in the starter code file and on bootcamp spot to create a for loop for the results retrieved from NYT API. 
- What I did was creat a loop through pages (0-19). 
- added a 'page' parameter to my query url. 
- made a GET request to retrieve a JSON response
- added a 12 second interval to stay within NYT API limits 
- appended the reviews
- printed the pages that were retrieved

I previewed and formatted the results in JSON fromat and then converted the list (reviews_list) to a Pandas DataFrame

When I needed to extract the title from headline main I performed the apply() method as per the instructions on bootcamp spot and copied the lambda function given to me in that step.
lambda st: st[st.find("\u2018")+1:st.find("\u2019 Review")]

Extracting name and value codes were already given in the starter code and I added this portion:
df['keywords'] = df['keywords'].apply(extract_keywords)
to fix the "keywords column" per instruction

I created a list called titles from the title column in the reviews list

# Accessing The Movie Databse API
I was given the base url, the tmbdb_key_string in the starter code file.
- to prepare the Movie Databse query I created the movie_title variable using the titles list made for the NYT API and added it to my query 
tmdb_query_url = f"{url}{movie_title}{tmdb_api_key}"


I followed the instructions in the starter file and on bootcamp to do the following
- I created an empty list (tmdb_movies_list) to store movie details
- created a request_counter = 1
to keep track of requests and limiting them every 50 requests using  time.sleep(). My code prints "Application is sleeping to avoid hitting limit"
- looped through the titles and perforemed a GET request using a url "https://api.themoviedb.org/3/movie/{movie_id}?api_key={tmdb_api_key}"
- I extracted genre names, spoken languages, and production countries into lists 
- instructions said to add relevant data into a dictionary and append it to the tmdb_movies_list. I added title, release date, genres, spoken languages, production countries, overview, vote average, and vote count.
- I added a try clause when searching for the movie details and an except clause if the movie is not found 

I previewd the results and formatted them in a JSON format and put the results in a DataFrame

# Merging the data

I merged the NYT and TMDB DataFrames into a merged_df on the title column

I removed the characters "[", "]", and "'" from the columns genres, spoken languages, and production countries based on instructions

I dropped the byline.person column

I deleted the duplicate rows and reset index 

I exported the data to CSV

