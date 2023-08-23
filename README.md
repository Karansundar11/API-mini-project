# Core-python-
#API Project
import requests
from bs4 import BeautifulSoup

#1 usage
def main():
    # the base URL of the API
    base_url = "https://apps.google.com/meet/"

    # Make the API call
    response = requests.get(base_url)
    print(response)
    # Check if the request was successful (satus code 200)
    if response.status_code == 200:
        # Print the HTML content
        # parse the HTML content using Beautifulsoup
        soup = BeautifulSoup(response.text, 'html.parser')

        # Find and print the title of the web page
        title = soup.title
        if title:
            print("Page Title:", title.string)
        else:
            print("Title not found.")
        # Find and print all the links on the web page
        links = soup.find_all('link')
        print("Links on the page:")
        for link in links:
            print(link.get('rel'))
    else:
        print("Request failed with satus code:{respone.status_code}")



main()
