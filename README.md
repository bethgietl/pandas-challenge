# pandas-challenge

***************The code looks funky when pushed to gitHub, the instructor, Mudit, said not to worry about it*************************

In the pandas-challenge I chose the HeroesOfPymoli assignment. I created a repo on github and cloned to my PC. Using gitbash I used the function mkdir to created the required directories/folders and nested them under the pandas-challenge main folder. I copied over the starter code python file and the Resources folder. I pushed changes to my repo on github via gitbash using git add ., git commit -m "", git push.

I used Jupyter Notebook to record the code and run the code. The starter code already included the dependencies/set-up, file to load and reading the file.  

The assignment wanted me to analyze purchasing data based on demographics like age and gender as well as most profitable and most popular items purchased. 

The highlights in the pandas challenge were not only calculating the purchasing data but also creating the tables to store the data.

I made sure to keep the main data frame untouched so I could call it at anytime I needed additional data but I also created a demographic speicfic data frame so that I could call only the data that was age and gender specific. 

Here's the main data frame: 
    
    purchase_data_df = pd.read_csv(csv_path)

Here's the demo data frame where I used the .loc function to capture only the demographic information I wanted, then I dropped the duplicates:
    
    player_demo = purchase_data_df.loc[:, ["Gender", "SN", "Age"]]

    player_demo = player_demo.drop_duplicates()
    
When calcualting the the number of item purchases I used the len along with .unique functions to only get the total number of items for sale: 
    
    unique_items_count = len(purchase_data_df["Item ID"].unique())

After creating the variables I needed for calculations and such, I created several corresponding tables throughout the assignment using the df = pd.DataFrame and naming the table headers and nesting the calculated data from the variables underneath, as shown below: 
    
    purchasing_analysis_df = pd.DataFrame({"Number of Unique Items": unique_items_count,
                                      "Average Price": [avg_item_price], 
                                      "Number of Purchases": [purchase_count], 
                                      "Total Revenue": [total_purchase_price]})
                                      
I used the groupby function to group the data in the data frame by a specific column header, for the example below I grouped the main data frame by Gender then I was able to create variables with the grouped data. 

    gender_group = purchase_data_df.groupby("Gender")
    gender_purchases = gender_group["Item ID"].count()

I feel the most impressive code I wrote was when I crated bins to hold the specific age groups and placed the data series into a new column inside the data frame by calling the df and series then using = pd.cut function 

    bins = [0, 9, 14, 19, 24,
            29, 34, 39, 50]

    group_labels = ["<10", "10-14", "15-19", "20-24", "25-29", "30-34", "35-39", "40+"]

    player_demo["Age Group"] = pd.cut(player_demo["Age"], bins, labels=group_labels)


Finally, I used the .map(format) function to clean the data and format $ or % - I did this ONLY once I was done calcuating as formating turns the data into a string from an interger: 
    
    gender_demo_df["Percentage of Players"] = gender_demo_df["Percentage of Players"].map("{:.2%}".format)
    

I feel I learned a lot on this assignment and appreciate that there was an example solution so I could check my answers. I also have an amazing tutor that helped me understand the code and from there it was a lot of copy and paste. I am certain there is a more clean or efficient way to run the code, however, as a beginner I'm very proud that my code works and gets the job done!  