# Getting Started with Live Server
Using the Live Server Extention hit `Go live` 

## The Process 
I used an async function and a Fetch request to attempt an an array of the list of beers within the Punk API.

my finished script reads as: 
```

        const api_url = 'https://api.punkapi.com/v2/beers?brewed_before=11-2012&abv_gt=6'

        async function getBeers(abvMin, abvMax) {
            const response = await fetch(api_url); 
            if (response.ok) {
            const jsonResponse = await response.json();
            const { abv_gt } = abvMin;
            const { abv_lt }  = abvMax;
            const { yeast, beer_name,} = data;
            console.log(data)
            }
        }
        

            getBeers(abvMin, abvMax);
```

## The Challenges

This test was a big challenge for me as my expierence so far has been mainly focused on front-end Web Development. 

I ran into an issue when loading the date in the console. that returned only. `native json promises`, the Array wasn't returning to the console properly, I thought This might be due to the objects calling the data. 

I attempted to add more const variables to call the data from the API url and define the `ABVMin` and `abvMax` parameters but in my refactoring I ran into an issue of the the abvMin not being defined



## TODO 
- find the rootcause of the issue of abvMin and do more research on API requests
- maniputlate the data to return an array of beers grouped by yeast 