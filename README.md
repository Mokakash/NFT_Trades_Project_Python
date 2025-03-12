# NFT Trade Analysis
In this project, I analyzed my collection of 2022 NFT trades. Leveraging the power of Python, I conduct a comprehensive analysis to uncover insights and patterns within my NFT trading activities. Understanding the most profitable methods and where to focus my time on various alpha groups is essential with limited time each day. Come along as I use Python to understand and learn more about my NFT trading journey, aiming to get the best out of my trades.
 
## Objectives
The primary objectives of this project encompass a comprehensive analysis of 2022 NFT trading data across five key categories. These categories include:
+ Overall Trade Performance
+ Identify Feature Relationships 
+ Evaluate Trade Method Importance/Profitability
+ Understand Alpha Group Distribution and Profitability
+ Uncover Temporal Trends

To achieve this, the initial steps involve cleaning the raw data followed by conducting exploratory data analysis.

## Data Sources
To conduct this analysis, I utilized my 2022 NFT transaction data stored in the file named ['NFT_Raw_Date.csv'](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/NFT_Raw_Data.csv), available in the repository.

Note:
+ The displayed values are in Ethereum (ETH), with four decimals due to the currency's high price.
+ For security purposes, NFT names have been removed, and hash transactions have not been included. 
+ Names of Alpha groups have been intentionally abbreviated to maintain confidentiality and protect sensitive information. 

## Data Cleaning
I conducted data cleaning on the NFT raw data to ensure its suitability for effective exploratory data analysis (EDA). The following modifications were made to refine and prepare the dataset:

+ **Date data type conversion from ‘Object’ to ‘DateTime’ format** - This alteration was made to facilitate future trend analysis.
+ **Null Values Verification** - Used a heatmap to visually confirm the absence of missing data/null values. This visual method aided in ongoing dataset cleaning (yellow for nulls and blue for non-null values - we see a bunch of yellows that need to be cleaned)
+ ![image1](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/01_Uncleaned_NULL_Heatmap.png)
+ **Handling Missing Data**
  + Dropped rows with null values in the 'Date' column.
  + Imputed missing values in the 'Royalty Fee' column with the `mean` of non-null entries.
  + Filled null or blank values in 'Sell Price (ETH)' with '0'. 
  + Renamed and filled null/blank values in the 'Transfer' column with 'NO' - Filling null or empty values with 'NO' was performed to indicate instances where no transfer was conducted.
+ **Handling Specific Columns**
  + Replaced 'Old Wallet' values with 'Main' - this modification serves to distinctly highlight and identify the primary/main wallet, offering a clearer representation of the dataset.
  + Updated 'Method' based on specific conditions - set '2nd Market' or '2ndary' to 'Secondary', and 'Mnt' to 'Mint'. This transformation aimed at categorizing and standardizing transaction methods. This standardization enhances data consistency and readability, providing a more coherent and understandable representation of the different transaction methods.
+ **Columns removal** – The columns listed below were identified as unnecessary for this analysis. Their removal aimed to streamline the analysis, enhancing focus, efficiency, and ease of interpretation.
  + NFT Name
  + ITEM 
  + Initial + Fee (ETH)
  + Breakeven
  + Listing Fee Total ($)
  + Gas Fees ($)
  + Location
  + Type
  + Eth Expect to Receive
+ **Final Verification** – Re-created a final heatmap to visually confirm the absence of null or missing values in the cleaned DataFrame (NO yellows representing null values remained in our DataFrame. Now it's good to go :wink:).

  + ![image2](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/02_Cleaned_NULL_Heatmap.png)

The cleaned dataset, named ['NFT_Cleaned_Data.csv'](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/NFT_Cleaned_Data.csv), is available in the repository.
Additionally, the Python code used for the data cleaning step can be found in the repository as ['Data_Cleaning.ipynb'](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Data_Cleaning.ipynb).

## Exploratory Data Analysis (EDA)
Outlined are the methods employed to visualize and understand critical facets of the NFT trading dataset. I aimed to uncover significant patterns, identify influential variables, and gain insights into the performance of the trades.

### Overall Trade Performance
Understanding the overall trade performance by computing total profits and losses denominated in Ethereum (ETH). This helped me gauge the profitability of my trades as a whole.
+ **Total Profit vs Total Loss**
  + The visualization showcases the balance between profits and losses in my NFT trading endeavors. With 41 ETH in total profits and 19.33 ETH in losses, it highlights the overall profitability of my trading activities during the analyzed period, indicating predominantly positive financial outcomes.
  + ![image3](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/03_Profit_vs_Loss.png)
+ **Cumulative Profit/Loss Over Time**
  + The plotted graph reveals the trajectory of my NFT trading profitability across the analyzed period. Notably, a temporary decline from mid-February to March is observed, followed by a slow growth from July to October. Overall, it indicates stable and positive trading performance during these periods.
  + ![image4](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/04_Cumulative_Profit_Loss.png)
### Identify Feature Relationships
Analyzing correlations between numeric variables using correlation heatmap to uncover insights into feature associations or dependencies. This guided my feature selection process and unveiled factors influencing profitability.
+ **Correlation Heatmap of Continuous Variables**
  + While fee-related features showcase high correlations, it's crucial to note that they should be ignored as this correlation is expected due to their relationship. Notably, the correlations between Sell Price, Total Fees, and Profit/Loss stand out, indicating their potential significance in influencing trading outcomes.
  + ![image5](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/05_Correlation_Heatmap.png)
+ **Correlation of Numeric Features with Profit/Loss**
  + This specific correlation analysis shows the relationship between numeric features and Profit/Loss feature. Confirming the earlier observations, Sell Price maintains a substantial correlation, while Total Fees emerge as a noteworthy factor. Notably, lower expenditure on Total Fees (including Gas, Listing, OS, and Royalty fees) correlates with heightened profitability, suggesting a potential strategy for optimizing trading outcomes.
  + ![image6](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/06_Correlation_with_Profit_Loss.png)
### Evaluate Trade Method Importance/Profitability
Understanding the distribution of trades across various trading methods and evaluating the total and average profit/loss associated with each method to provide clarity on prominent trading methodologies affecting overall outcomes.
+ **Count of Trades by Method**
  + The analysis reveals that 'Mint' constitutes the highest number of transactions, followed by 'Secondary' and 'Airdrop'.
  + ![image7](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/07_Count_by_Method.png)
+ **Percentage of Trades by Method**
  + This pie chart displays that approximately 70% of trades were executed using the 'Mint' method of transaction, and the rest 30% were through the other two methods.
  + ![image8](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/08_Percentage_by_Method.png)
+ **Total and Average Profit/Loss by Method**
  + Minting transactions, being the most frequent, showcased both a significant total profit and the highest average profit among the methods. Conversely, Secondary transactions, while not as frequent, displayed an average loss, emphasizing the varying profitability across different transaction methods. Overall, Minting transactions consistently yielded higher profits, suggesting its stronger profitability compared to Airdrops and Secondary transactions during this period.
  + ![image9](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/09_Total_vs_Avg_Profit_Loss.png)
### Understand Alpha Group Distribution and Profitability
The analysis of trade counts and profit and loss across different alpha groups helped identify which groups provided better insights for NFT projects. 
+ **Count of Transactions for Different Alpha Groups**
  + The 'NP' group stands out with the highest transaction count, followed by 'WP', 'MK', 'AS', 'AZ', 'LV', and 'TW'. Understanding the distribution among these groups could imply that I've either spent more time in these alpha groups or that these specific groups offer more trade opportunities compared to others, resulting in a higher transaction count.
  + ![image10](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/10_Count_by_Groups.png)
+ **Total Profit/Loss for Each Alpha Group**
  + NP emerges as the most profitable alpha group, contributing significantly to the overall profit with 14.2 ETH, representing 68% of the total profit. Conversely, YT stands out as the least profitable alpha group, reflecting a loss within the analyzed dataset.
  + ![image11](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/11_Total_Profit_Loss_by_Groups.png)
+ **Average Profit/Loss for Each Alpha Group**
  + Despite the NP alpha group contributing the highest total profit, it ranks third in terms of average profit per trade at 0.0598 ETH. The LV alpha group leads with an average profit per trade of 0.1998 ETH, followed by AS at 0.0635 ETH per trade.
  + ![image12](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/12_Avg_Profit_Loss_by_Groups.png)
  + Analyzing both the total and average Profit/Loss unveils that out of the 14 alpha groups, only five (NP, LV, AS, WP, TW, and AZ) yielded profitable trades. This suggests that focusing more on these specific alpha groups for upcoming project insights could have led to more profitable outcomes.
### Uncover Temporal Trends
Exploring monthly and quarterly profit/loss trends allowed me to detect seasonal variations and temporal patterns within my trading activities. 
+ **Total Profit/Loss by Month**
  + This analysis indicates that January recorded the highest profits, while February and June incurred losses. Notably, the profits from the first half of the year, excluding February and June, outweigh those from the second half, suggesting a variation in profitability trends across different months.
  + ![image13](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/13_Total_Profit_Loss_by_Month.png)
+ **INTERACTIVE GRAPH - Total Profit/Loss by Month**
  + Showing the same insights as the prior static visualization through an interactive bar plot created using Plotly, allowing for dynamic exploration and analysis of profit/loss trends across different months.
  + ![image14](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/14_Total_Profit_Loss_by_Month_Interactive.png)
+ **Total Profit/Loss by Quarter**
  + Q1 marked the highest profits, closely followed by Q2, while Q3 and Q4 displayed a decline in total profits. This observation highlights a progressive decrease in profits as the year advanced.
  + ![image15](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/16_Total_Profit_Loss_by_Quarter.png)
+ **Average Profit/Loss by Quarter**
  + Quarterly `average` analysis unveils a contrasting trend where Q3 showcased the highest average profitability, closely trailed by Q2. In contrast, Q1 and Q4 exhibited relatively lower average profits. This pattern suggests potential seasonal fluctuations, emphasizing higher average profits in the middle quarters (Q2 and Q3) compared to the first and last quarters (Q1 and Q4).
  + ![image16](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/Assets/15_Avg_Profit_Loss_by_Quarter.png)

The Python codes used to derive these insights are available in the repository as [‘EDA_Exploratory_Data_Analysis.ipynb’](https://github.com/Mokakash/NFT_Trades_Project_Python/blob/main/EDA_Exploratory_Data_Analysis.ipynb).

## Conclusion
Investigating my 2022 NFT trades using Python revealed key patterns and trends. Overall, my trading activities demonstrated periods of profitability with variations across methods and alpha groups. Focusing on certain alpha groups like NP, LV, AS, WP, TW, and AZ seemed more lucrative, with only these groups yield consistent profits. Understanding temporal trends highlighted seasonal fluctuations, indicating a potential pattern of diminishing profits as the year progresses, with the middle two quarters displaying comparatively higher profitability. The exploration into different methods showcased 'Minting' as the most profitable trade method. Additionally, correlation analyses revealed significant associations between sell prices, total fees, and overall profitability, offering strategic insights into cost optimization. These findings underscore the importance of strategic method selection, alpha group exploration, and temporal planning to maximize NFT trading outcomes.

## Contributing
Contributions to enhance this analysis are welcome! 
Feel free to fork the repository and create a new branch for your modifications.

## Disclaimer
This analysis is based on personal data for a Python project ONLY and should **NOT** be construed as financial advice; it is solely intended for educational and informational purposes.
