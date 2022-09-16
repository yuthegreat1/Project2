# Project2
Project Proposal
Our client has an exciting new meat substitute being prepared for market. The product is an excellent substitute for America’s favorite white meat, chicken. As part of the marketing rollout our client would like Huddle Analytical to create a database of chicken recipes to draw from as they promote their product. The clients parameters are flexible, but they must include chicken as the primary protein. Other possible parameters are preparation time and number of ingredients.
## Data source 1
Description: a database of recipes from food.com, this includes data like ingredients and estimated cooking time.
link https://www.kaggle.com/datasets/irkaal/foodcom-recipes-and-reviews
## Data source 2
Description: An api from the Company Tasty that contains multiple recipes
link https://rapidapi.com/apidojo/api/tasty
## Data source 3
Description : A database of recipes
Link : https://www.kaggle.com/datasets/paultimothymooney/recipenlg?resource=download / https://github.com/Glorf/recipenlg
Initial findings in data sources (2-3 sentences)
# Extract
For this project we are using three data sources. The first data source is from Food.com. Originally, it contained 522,517 recipes and 1,401,982 reviews. There were originally 28 columns. Those columns include a distinct ID, recipe name, cook time, prep time, RecipeCategory, recipe quantities and ingredients, instructions and nutritional data. It was downloadable as a .csv file.
The second source is the Tasty API. Tasty is a food recipe application from Facebook. It is a crowd sourced recipe sharing API.
Our third data source was from kaggle.com, called RecipeNLG. It is a 2.29gb .csv file. It had 7 columns: unique ID#, recipe title, ingredients, directions, links to the original source, the source, and NER (which is a set of keywords of the recipe).
# Transform
The data transformation process was impeded by the fact that all of these data sources were crowd sourced. Since these were recipes, a process focused data set, each source had a different methodology for describing the process. The primary indexing off all these data sources was the name of the recipe. Data source 1 and 3 were standard descriptions of recipes. Data source 2 was particularly problematic, with the descriptions not relating to the subject matter of the recipes below, for example “Dinner ready in 30mins or less”, completely incompadible with our project goals. This was ultmately fatal to using Data Source 2, and we dropped it. We then filtered both remaining data sources using ‘Chicken’, that drastically reduced the size of both tables. Then we had to organize the tables so they had similar column names and were aligned in anticipation of a table union.
We had multiple issues with these crowd sourced data sources. One was that we had tens of thousands of recipes, but there were many different recipes with the same name, a search for ‘chicken stew’ yielded 130 examples in data source 1. But this is nature of recipes, there is an infinite variety under common names. But that essentially made using names and titles impossible for primary keys in our final source. Another issue with crowd sourced process centric data sources was that the two tables had different approaches to describing ingredient quanities. Data source 3 used ingredient quanities inclusive to the ingredients, combining them into 1 column. Data source 2 kept the quanities and ingredients seperate. Requiring us to navigate an additional column. Otherwise, we had to rename the NER column in data source 3 to match the keyword column. And reorder the columns so they were aligned, again in anticipation of a union of the tables.
Finally we had to align the columns, data source 1 had 5 columns and data source 2 had 4 columns.So we had to add a column to make the two tables line up for the merge.
# Load
The final table has a six columns an index, title, ingredients, directions, and keywords. From the original two tables we reduced the number of recipes from 1,541,383 to 223,465. We feel this gives our client an excellent resource of chicken recipes to promote thier new product. There is an huge variety recipes for thier marketing needs.
