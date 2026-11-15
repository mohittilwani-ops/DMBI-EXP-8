DMBI Experiment 8 – Bank Customer Churn System
Experiment Title
Association Rule Mining using Python (Apriori) – Bank Customer Churn System
Important Dataset Clarification
The uploaded Experiment 8 reference document uses the Groceries Dataset (Groceries_dataset.csv) and performs Market Basket Analysis. It does not use a bank customer churn dataset. To preserve the supplied practical accurately, the code and procedure below retain the Groceries dataset and the Apriori association-rule workflow. The requested Bank Customer Churn System wording is used as the project title, but the underlying analysis is grocery purchase-pattern analysis, not bank churn prediction.

A genuine bank customer churn dataset such as Churn_Modelling.csv has one record per customer and does not directly contain shopping-basket transactions. It would require a separately defined feature-to-item transformation before Apriori could be meaningfully applied.
Aim
To implement the Apriori Association Rule Mining algorithm using Python. The experiment preprocesses real-world retail data into a transactional matrix, generates frequent itemsets based on minimum support, and extracts strong association rules to discover patterns in customer purchasing behaviour.
Theory
1. Market Basket Analysis and Association Rules
Association Rule Mining is a data mining technique used to discover interesting relationships between variables in large databases. In retail, it is commonly known as Market Basket Analysis: finding patterns of co-occurrence among items.

An association rule is written as:

A => B
- Antecedent (A): The “If” part of the rule; the item or itemset found in the basket.
- Consequent (B): The “Then” part of the rule; the item likely to be purchased alongside A.
2. Apriori Algorithm
Apriori is a classic algorithm for discovering association rules. It uses the anti-monotonicity principle:
- If an itemset is frequent, all its subsets must also be frequent.
- If an itemset is infrequent, all its supersets must also be infrequent.
This principle allows the algorithm to prune candidate itemsets and reduce the search space.
3. Evaluation Metrics
Support

The proportion of total transactions containing an itemset:

Support(A) = Transactions containing A / Total transactions

For a rule A => B, support refers to the transactions containing both A and B.

Confidence

The probability that a transaction containing A also contains B:

Confidence(A => B) = Support(A union B) / Support(A)

Lift

The ratio of observed confidence to the expected confidence if A and B were independent:

Lift(A => B) = Confidence(A => B) / Support(B)

Interpretation:
- Lift > 1: Positive association.
- Lift = 1: Independent items.
- Lift < 1: Negative association.
4. Dataset Overview
- Dataset: Groceries Dataset
- Input file: Groceries_dataset.csv
- Transactions reported in the supplied practical: 14,963
- Unique grocery items reported: 167
- Key columns:
  - Member_number: Customer ID
  - Date: Transaction date
  - itemDescription: Product purchased
Software and Libraries
- Python 3
- Jupyter Notebook / Google Colab / VS Code
- Pandas
- mlxtend
Files
- bank_customer_churn_system_exp8.py – Python implementation.
- Groceries_dataset.csv – Input dataset used by the supplied Experiment 8 reference.
- bank_customer_churn_system_transaction_matrix.csv – Generated Boolean transaction matrix.
- bank_customer_churn_system_frequent_itemsets.csv – Generated frequent itemsets.
- bank_customer_churn_system_association_rules.csv – Generated association rules.
Implementation Steps
1. Import libraries and load the dataset: Import Pandas and the mlxtend functions. Load Groceries_dataset.csv and inspect the first records.
2. Preprocess the data: Remove rows where itemDescription is missing. Group records by Member_number and Date to create one list of purchased products for each shopping transaction.
3. Create the transaction matrix: Use TransactionEncoder to convert the list of baskets into a Boolean matrix, where each row is a transaction and each item is a True/False column.
4. Generate frequent itemsets: Apply Apriori with minimum support 0.0003 (0.03%), matching the supplied practical.
5. Generate association rules: Apply association_rules using confidence as the metric and minimum confidence 0.5 (50%).
6. Sort and display rules: Sort the rules in descending order of Lift and display antecedent, consequent, support, confidence and lift.
7. Save outputs: Export the transaction matrix, frequent itemsets and association rules to CSV files.
Installation
Install the required packages:
pip install pandas mlxtend
How to Run
Local execution
1. Keep Groceries_dataset.csv in the same folder as bank_customer_churn_system_exp8.py.
2. Run:
python bank_customer_churn_system_exp8.py
Google Colab
Run the script in a Colab notebook. The script detects Google Colab and prompts you to upload Groceries_dataset.csv.
Results Reported in the Supplied Experiment PDF
The uploaded practical reports:
- Number of transactions: 14,963
- Number of unique items: 167
- Minimum support: 0.0003 (0.03%)
- Minimum confidence: 0.5 (50%)
- Frequent itemsets discovered: 2,393
- Association rules generated: 6
The PDF displays these example rules, sorted by Lift:
Antecedent	Consequent	Support	Confidence	Lift
(fruit/vegetable juice, curd)	sausage	0.000334	0.500000	8.285161
(other vegetables, soda, pastry)	whole milk	0.000334	0.833333	5.276837
(ice cream, pp fruit)	rolls/buns	0.000334	0.500000	5.149002
(other vegetables, pastry, whole milk)	soda	0.000334	0.500000	4.545261
(sausage, yogurt, rolls/buns)	whole milk	0.000334	0.555556	3.517892


These values are the results printed in the supplied PDF. Your run may vary if the input file, preprocessing or package versions differ.
Inference from the Supplied PDF
1. Breakfast/Snack Basket: (fruit/vegetable juice, curd) => (sausage) has a Lift of approximately 8.28. In the reported dataset, the consequent is substantially more likely when the antecedent items are present than under independence.
2. Baking/Sweet Basket: (other vegetables, soda, pastry) => (whole milk) has confidence of approximately 0.833 (83.3%), the highest confidence among the highlighted rules.
3. Directional Association: (other vegetables, pastry, whole milk) => (soda) has confidence of 50%. Association rules are directional; reversing antecedent and consequent does not guarantee the same confidence.
Result
The supplied practical reports that Apriori was executed on 14,963 grocery transactions. It discovered 2,393 frequent itemsets and generated 6 association rules that met the minimum support of 0.03% and minimum confidence of 50%.
Conclusion
Association Rule Mining, specifically the Apriori algorithm, can uncover purchasing patterns in transactional databases. The key preprocessing step is transforming individual item rows into a Boolean transaction matrix. By applying Support, Confidence and Lift thresholds, frequent combinations and useful associations can be identified for business decisions such as store layout optimization and targeted cross-promotional marketing.
Note
Although the requested project heading says Bank Customer Churn System, this Experiment 8 implementation is based on the Groceries dataset in the supplied PDF. It must not be described as a bank churn prediction model or as analysis performed on Churn_Modelling.csv.
