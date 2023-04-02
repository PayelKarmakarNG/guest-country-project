# Problem Statement 

You will build a card component that gives a visual overview of hotel reservations per
country. This will be done by showing the countries in a list view. Each list item is one
country with a couple of data points regarding the reservations for that country. This list can
have any number of countries, but at most 5 rows should be visible. If there are more than 5
countries, users can scroll in the card to see more.
First we will show the current reservations of a country. We will show both the absolute
number of reservations and a progress bar. The percentage in the progress bar will be the
number of reservations for the country you are looking at divided by the maximum number of
reservations in this card. So to give an example:
You have 50 reservations in Belgium, 70 in Germany and 30 in France. If you are looking at
Belgium the bar will be 71% filled (50 reservations in Belgium divided by the maximum
amount of reservations, which is 70 in Germany)
This way you get a good overview of which country has the most reservations. All of this
data will be available via API call. See below for more details.

Next to showing the number of reservations, we also need to see the change in reservations
versus last year. This will be shown as a number next to the progress bar. It will be red for a
negative change, and green for a positive change. If there is no change, text will remain the
default color.
The list view should be sorted first by number of reservations, then by change. Make sure the
sort is consistent if numbers are the same.
There is no restriction on how you can tackle this. You can use any framework or technology
you think is best.
Design
We use Figma for designs. You can check there to get the correct colors, padding etc.
Note: to be able to inspect these properties you’ll need to create a (free) account.
What is this?
We want to get an overview of your skills as a frontend developer. To do this we have written
out a specification of a small application you will make. This should take no more than an
hour. We will add a few stretch goals as well in case you have time left.
Feature specification
You will build a card component that gives a visual overview of hotel reservations per
country. This will be done by showing the countries in a list view. Each list item is one
country with a couple of data points regarding the reservations for that country. This list can
have any number of countries, but at most 5 rows should be visible. If there are more than 5
countries, users can scroll in the card to see more.
First we will show the current reservations of a country. We will show both the absolute
number of reservations and a progress bar. The percentage in the progress bar will be the
number of reservations for the country you are looking at divided by the maximum number of
reservations in this card. So to give an example:
You have 50 reservations in Belgium, 70 in Germany and 30 in France. If you are looking at
Belgium the bar will be 71% filled (50 reservations in Belgium divided by the maximum
amount of reservations, which is 70 in Germany)
This way you get a good overview of which country has the most reservations. All of this
data will be available via API call. See below for more details.

Next to showing the number of reservations, we also need to see the change in reservations
versus last year. This will be shown as a number next to the progress bar. It will be red for a
negative change, and green for a positive change. If there is no change, text will remain the
default color.
The list view should be sorted first by number of reservations, then by change. Make sure the
sort is consistent if numbers are the same.
There is no restriction on how you can tackle this. You can use any framework or technology
you think is best.
Design
We use Figma for designs. You can check there to get the correct colors, padding etc.
Note: to be able to inspect these properties you’ll need to create a (free) account.
Figma link - https://www.figma.com/file/mIPZHtgsdsI5LP6blKY71p/Medior-Technical-Test

The data
You’ll get a list of countries, each country object will be structured as follows:
{
"id": "guest_country-CH",
"display_code": "CH",
"value": {
"nr_of_rooms": 48,
"revenue": 2400
}
"reference_value": {
"nr_of_rooms": 1,
"revenue": 50
}
}
- id: unique identifier for this country
- display_code: the country code
- value: the number of rooms and revenue for this year
- reference_value:the number of rooms and revenue of last year
You can find this data in the “guest-country-sample.json” file we provided. This is just to give
you an example of the response. In your code you can call this endpoint:
https://data.otainsight.com/public-data/frontend-hiring/guest-country-sample.json
In the “country-mapping.js” file you can find a mapping of the country codes to country
names. You’ll need this to correctly display the names in the card.
Before you start
Read through this specification and let us know how long you think this will take you. You
can do this by sending us an email, this can of course be a rough estimate.
When you’ve finished
Send us your solution. This can be done either via a .zip file or a GitHub link. Up to you. We
will review your code and when you come for the in person interview we will review this code
and ask some additional questions.

The data
You’ll get a list of countries, each country object will be structured as follows:
{
  "id": "guest_country-CH",
  "display_code": "CH",
  "value": {
  "nr_of_rooms": 48,
  "revenue": 2400
}
"reference_value": {
  "nr_of_rooms": 1,
  "revenue": 50
}
}
- id: unique identifier for this country
- display_code: the country code
- value: the number of rooms and revenue for this year
- reference_value:the number of rooms and revenue of last year

You can find this data in the “guest-country-sample.json” file we provided. This is just to give
you an example of the response. In your code you can call this endpoint:
https://data.otainsight.com/public-data/frontend-hiring/guest-country-sample.json
In the “country-mapping.js” file you can find a mapping of the country codes to country
names. You’ll need this to correctly display the names in the card.

# guest-country-project

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

![image](https://user-images.githubusercontent.com/50908900/167275118-027027d3-45ab-4d1c-bc23-114d792857d7.png)


