# Getting Started with Live Server
Using the Live Server Extention hit `Go live` 

## The Process 
I kept thinking about this problem after the test and spent more time working on it. 

I used an async function and a Fetch request to attempt an an array of the list of beers within the Punk API, I used the `.then` to convert the response to json, and used a `.map` method to map a new array containing the values of the yeast and beername data. Once I had the new array I chose to use a sort method and a compare function to compare the yeast a - b values which I hoped would return the array in ascending yeast order. 

You can find the diagram I made to help me solve this problem  [here](https://miro.com/welcomeonboard/WTl1ZlA2bGdROFVuRkhoTTl4d1VwZkZHaE1BRzE2bXZkdDJodmx3T1FDaVlidUROaWc0QzJPUk1WSkZDRFJIWHwzMDc0NDU3MzYxMjMyMDY2MjEy)

my finished script reads as: 
```
        
        const api_url = 'https://api.punkapi.com/v2/beers?'


        async function getBeers(abvMin, abvMax) {
            await fetch(`${api_url}&abv_gt=${abvMin}&abv_lt=${abvMax}`)
                .then(response => response.json())
                .then(data => {
            const beerMap = data.map(data => `${data.name}, [${data.ingredients.yeast}]`)
            const byYeast = beerMap.sort((a , b) => {
                    if (a.yeast < b.yeast ) return -1 
                    if (a.yeast > b.yeast ) return 1 
                    return 0
            });
            console.log(byYeast);
        });
        }
        

```

## The Challenges

This test was a big challenge for me as my expierence so far has been mainly focused on front-end Web Development. 

Originally I attempted to add more const variables to call the data from the API url and define the `ABVMin` and `abvMax` parameters but in my refactoring I ran into an issue of the the abvMin not being defined, I defined the parameters in the fetch API request `&abv_gt=` and `&abv_lt=`

I used the incorrect link originally for my fetch Url so I corrected that and used the defined parameters above. 

Figuring out which array method to use was the biggest challenge. Once that clicked I felt I was getting closer to an answer, I knew from the beginning that I wanted to use `.sort` to organise the response data but it took me some time to realise I needed to create a map first with the array of beer names and yeast. 

Once I had the mapped array I wanted to use the sort method to organise this data, I struggled to find the correct way to implement the compare function to work properly. I did alot of research on this and found out that if the compare function relates to an object which is a string then I needed to create a conditional statement defining the object to compare. I tried to implement this with `if (a.yeast < b.yeast) return -1` but I was unsuccessful in reorganising the mapped array. 



## TODO 
- Find out the correct way to implement the sort method compare function so that the mapped array is displayed in ascending order by yeast. 
