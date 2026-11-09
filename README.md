# MSCS 634 – Lab 6: Association Rule Mining with Apriori and FP-Growth

## Purpose

The objective of this lab is to learn how to apply the association rule mining technique using Apriori and FP-Growth algorithm. For that purpose, the UCI Online Retail dataset has been used to uncover frequent purchases of products and relationships between them.

These two algorithms have been used on the same transactional data set to compare their effectiveness and efficiency. Visualizations using Seaborn library are made for frequent item sets, product relationship, and association rules.

## Dataset

The UCI Online Retail dataset provides transactions data from an online retail business. Each transaction contains several fields like Invoice Number, Stock Code, Description, Quantity, Price, and Country.

The dataset is preprocessed by eliminating the canceled transactions, NaN values, invalid quantities, and duplicate invoice-item pairs. Only transactions of the United Kingdom are chosen for analysis.

**Dataset Source:** [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail)
## Methods

### 1. Data Pre-processing

Firstly, the data set is pre-processed to convert it into the format of transaction matrix, where rows represent invoices, and columns represent products. Frequent items are detected via seaborn bar charts, whereas the co-purchase relationships between the products are shown on a heatmap.

### 2. Apriori algorithm

This algorithm detects frequent item sets by forming all possible candidates and then verifying if the number of their supports exceeds the minimum support threshold.

In order to find products or their combinations that appear in at least 2% of transactions, the threshold is set to 0.02. Frequent item sets are visualized with their supports via bar charts.

### 3. FP-Growth algorithm

In this algorithm, frequent item sets are found through an FP-tree structure without generation of candidate combinations.

The minimum support is again set to 0.02 to allow a fair comparison with the previous algorithm. Execution time is measured to test efficiency of both algorithms.
### 4. Generation of association rules

The association rules have been generated from the frequent itemsets by setting the minimum confidence value to 0.40.

These association rules are analyzed using the following three parameters:

- **Support:** It indicates the frequency of an item combination in all transactions.
- **Confidence:** It indicates the probability of buying one product when another product is bought.
- **Lift:** It indicates the strength of the relationship between the products compared to their independent buying probabilities.

Confidence and lift values are represented through Seaborn scatter plots.

### 5. Comparative analysis

Execution time and frequent itemsets are used for the comparative analysis of Apriori and FP-Growth.

Apriori algorithm creates the candidate itemsets, which may result in increased computational complexity with a large number of product combinations. The FP-tree structure is used by FP-Growth to avoid candidate generation.

The execution times obtained from the notebook decide the faster algorithm.

## Key insights and association rules

Association rules provide the patterns in purchasing that are not obvious from the transaction record data.
Items that are frequently bought can help in determining the buying behavior of customers, and the association rules can identify groups of products that co-occur often.

For instance, a confidence level of 0.60 would mean that 60% of all the transactions with the first item also have the associated item. A lift level greater than one shows a positive relationship between the two items.

This information can be used in making recommendations on promotions and bundling products.

## Challenges and Decisions

One problem was in preparing the transaction dataset for mining the association rules. Incomplete product data, cancellation of invoices, and invalid transaction data can distort the results of the analysis. The mentioned records were excluded when the data was being cleaned.

Another problem is in choosing an appropriate minimum support level. The very low value can lead to too many itemsets being generated, and it can slow down the process. A high value can exclude some relevant itemsets. A minimum support of 0.02 was used in both cases.

Also, a transaction matrix was optimized through sparse representation of data to save memory space. Using the same transaction dataset and the thresholds made it possible to compare Apriori and FP-Growth.




## References

Chen, D. (2015). Online Retail [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5BW33
