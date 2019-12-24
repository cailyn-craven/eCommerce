# eCommerce
Data Camp projects from https://www.datacamp.com/projects


This project involves Data Science for Search Engine Marketing (SEM). I created Google AdWords campaigns by generating keywords and ad templates with Python. 

SEM is the process of gaining website traffic by purchasing ads on search engines. You bid for ad placement in a search engine's sponsored links for keywords related to your business or product, and then you pay the search engine a fee for each click. Paying for each click can get costly, so it is imperative to plan and group your keywords and ads to control costs. The main idea is that the more relevant your ads are, the lower your cost per click. 

In this case, we imagine that we work for a digital marketing agency. We need to create a prototype set of keywords for search campaigns fr an online retailer's sofa selection. The client is a low-cost retailer who offers many promotions and discounts, so we need to stay away from luxury keywords and target price-sensitive customers. 

I started by making a list of words that would pair well with a sofa line of products to emphasize promotions, discounts, and low-cost.

The next step is to combine the words with the product names to generate relevant search keywords. I created a keyword list with the combination of every product and every descriptive word. I did this with nested for loops running over both the list of products and the list of keywords. I concatenated the product string and the word string so that the both "word" + "product" and "product" + "word" order appear in the keyword list. For example:   
	buy recliners
	recliners buy
	price recliners
	recliners price   

To look at the keyword list, I used the pprint package, which "pretty-prints" Python data structures like lists and dictionaries. The pretty-print formatted representation keeps objects on a single line if possible. 

Then I converted the keyword list of lists into a DataFrame so it would be easy to manipulate and manage the final output. 

The keywords DataFrame had default column names 0 and 1. I used Data.Frame.rename() to give the columns the meaningful names' Ad Group' and 'Keyword.' I chose to do this in place.

The next step was to add a Campaign Column to the DataFrame. Since the DataFrame currently only has a single campaign, I initialized all values to 'SEM_Sofas.' 

Afterward, I created a match type column and initialized all values to exact. The three different SEM keyword match types are broad, exact, and phrase. Exact match means that a keyword matches the exact term or is a close variation of that term. Broad match is much looser and means ads may show on searches that included misspellings, synonyms, variations, or even related searches. Broad match tends to lead to more traffic, but it can lead to higher ad spend with a lower conversion rate because the ad shows even though it isn't closely related to a customer's search. Since the client is tight on budget, I started with all keywords being an exact match. 

Unfortunately, the search volume for the exact match is lower than other match types. We can't possibly think of all of the ways people will search, so if we only relied on exact match keywords, we would likely miss out on some high-quality keywords. It's a good idea to use another match called phrase match as a discovery mechanism to allow our ads to display when a customer searches for our exact match keywords together with anything before (or after) them. 

Later, when the campaign launches, we can explore a modified broad match, broad match, and negative match types for better visibility and control of our campaigns. 

I created a copy of the keywords DataFrame and changed the Criterion Type column to 'Phrase.' Then I appended the two DataFrames vertically so that I would have one final DataFrame that had both the exact match and phrase type keywords. 

To import the campaign into the AdWords or BingAds editor, I needed to save it as a CSV file. After converting the final DataFrame to a CSV file, I looked at a summary of the campaign structure by grouping by ad group and criterion type and counting by keyword. 
