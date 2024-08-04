# Data_collection_HTML
Module 11

![image](https://github.com/user-attachments/assets/8eb89179-e7e3-4384-89c9-e933cf934a2f)


# Background
You’re now ready to take on a full web-scraping and data analysis project. You’ve learned to identify HTML elements on a page, identify their id and class attributes, and use this knowledge to extract information via both automated browsing with Splinter and HTML parsing with Beautiful Soup. You’ve also learned to scrape various types of information. These include HTML tables and recurring elements, like multiple news articles on a webpage.

As you work on this Challenge, remember that you’re strengthening the same core skills that you’ve been developing until now: collecting data, organising and storing data, analysing data, and then visually communicating your insights.

# What You're Creating
This new assignment consists of two technical products. You will submit the following deliverables:

Deliverable 1: Scrape titles and preview text from Mars news articles.

Deliverable 2: Scrape and analyse Mars weather data, which exists in a table.

# Instructions
  # Part 1: Scrape Titles and Preview Text from Mars News
Open the Jupyter Notebook in the starter code folder named part_1_mars_news.ipynb. You will work in this code as you follow the steps below to scrape the Mars News website.
1. Use automated browsing to visit the Mars news siteLinks to an external site.. Inspect the page to identify which elements to scrape.

  <img width="610" alt="image" src="https://github.com/user-attachments/assets/8cce1203-8194-43e0-823e-9cb007bdd7ab">


2. Create a Beautiful Soup object and use it to extract text elements from the website.

            # Create a Beautiful Soup object
             html = browser.html
             mars_soup = BeautifulSoup(html,"html.parser")
            # Extract all the text elements
             text_elements = mars_soup.find_all("div",class_="list_text")
             print(text_elements)
     

4. Extract the titles and preview text of the news articles that you scraped. Store the scraping results in Python data structures as follows:
   - Store each title-and-preview pair in a Python dictionary and, give each dictionary two keys: title and preview. 

                   # Create an empty list to store the dictionaries
                     articles_list = []
                   # Loop through the text elements
                   # Extract the title and preview text from the elements
                   # Store each title and preview pair in a dictionary
                   # Add the dictionary to the list
                    articles_list = [{"title":soup.find("div",class_="content_title").text,
                                      "preview":soup.find("div",class_="article_teaser_body").text}\
                                       for soup in text_elements]
   - Print the list in your notebook.
     
    <img width="824" alt="image" src="https://github.com/user-attachments/assets/42a84284-4533-46b7-a9d5-00623b85d55a">


   # Part 2: Scrape and Analyse Mars Weather Data
Open the Jupyter Notebook in the starter code folder named part_2_mars_weather.ipynb. You will work in this code as you follow the steps below to scrape and analyse Mars weather data.
 1. Use automated browsing to visit the Mars Temperature Data SiteLinks to an external site.. Inspect the page to identify which elements to scrape. Note that the URL is https://static.bc-edx.com/data/web/mars_facts/temperature.html.
 2. Create a Beautiful Soup object and use it to scrape the data in the HTML table. Note that this can also be achieved by using the Pandas read_html function. However, use Beautiful Soup here to continue sharpening your web scraping skills.
 3. Assemble the scraped data into a Pandas DataFrame. The columns should have the same headings as the table on the website. Here’s an explanation of the column headings:
    - id: the identification number of a single transmission from the Curiosity rover
    - terrestrial_date: the date on Earth
    - sol: the number of elapsed sols (Martian days) since Curiosity landed on Mars
    - ls: the solar longitude
    - month: the Martian month
    - min_temp: the minimum temperature, in Celsius, of a single Martian day (sol)
    - pressure: The atmospheric pressure at Curiosity's location
  4.Examine the data types that are currently associated with each column. If necessary, cast (or convert) the data to the appropriate datetime, int, or float data types.
  5. Analyse your dataset by using Pandas functions to answer the following questions:
   - How many months exist on Mars?
   - How many Martian (and not Earth) days worth of data exist in the scraped dataset?
   - What are the coldest and the warmest months on Mars (at the location of Curiosity)? To answer this question:
      * Find the average minimum daily temperature for all of the months.
      * Plot the results as a bar chart.
        
  ![avg_temp_month_sorted](https://github.com/user-attachments/assets/d7f15052-887d-45aa-89cd-515766e7333b)

   - Which months have the lowest and the highest atmospheric pressure on Mars? To answer this question:
     * Find the average daily atmospheric pressure of all the months.
     * Plot the results as a bar chart.
     
  ![avg_pressure_month_sorted](https://github.com/user-attachments/assets/270ec473-b5ce-4d29-9387-fb17675fa21c)

  - About how many terrestrial (Earth) days exist in a Martian year? To answer this question:
     * Consider how many days elapse on Earth in the time that Mars circles the Sun once.
     *  Visually estimate the result by plotting the daily minimum temperature.
     
  ![terrestrial_days](https://github.com/user-attachments/assets/ad8d3242-c83e-4c53-b2e6-826f52023710)

  6. Export the DataFrame to a CSV file.
