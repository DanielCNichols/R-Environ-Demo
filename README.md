# Loading Environment Variables in R

There are a lot of different ways to handle this, but I think the simplest looks like adding a `.Renviron` file at the root of your project. This file will be loaded when Rstudio starts, and values contained in it can be accessed as follows:

```sh
# In your .Renviron

apiKey="testKey"
```

```r
# in your <scriptName>.r

key <- Sys.getenv("apiKey")

print(key)

# and so on...
```

*NOTE*: DO NOT commit the .Renviron file. It contains secrets (like an api key) that you might not want publicly available in your version control history. 

Instead, add the following line to your .gitignore:

```
.Renviron
```

You have used a special environment variable for running your code on your machine, but what about other collaborators? You want to let them know what variables they need to specify, but you don't want to actually commit those variables. You can do this by giving them an example.

1. Create a file called `.Renviron.example`
2. Add placeholders for any variables used:
```
apikey=yourapikeyhere
```

This `.Renviron.example` file **will** be committed. Then, when your fellow developer starts their work, they will need to run the following command in the terminal from the root of the project:

```sh
cp .Renviron.example .Renviron
```

Then, they will update the values from your placeholder to the actual values in the newly-created `.Renviron` file.



