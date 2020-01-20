# ML
Machine learning projects
Logic Summary:

Initial setup :
The data set is imported which contains a list of document id’s , word id’s and the number of times each word occurs in a document.
The vocab file contains the actual words that are used in the document and the index of the file is the word id in the data set. The file is used to map the word id’s in the data set to the actual words 
The function which generates K- Frequent item data sets has the following parameters :
K= Size of each item frequent item sets
Sup = (Number of times the ‘K words occur together in a document, across the entire data sets)/(Total    Number of documents in the data set)
Name = File name of the dataset
The function reads the data set and vocabulary mapping file. 
We set a start time and initial memory usage so as to compute total time elapsed and total memory usage after the program runs.

Data pre processing:
The data set is read from the file and converted  into a data frame.
This is then formatted so as to create the set of transactions -  list of document’s where each document is itself a list containing the word id’s in the particular document. 
The set of transactions in the required format is then fed into the Apriori algorithm which generates frequent item sets as follows :
Apriori Algorithm:
Definitions : 
Frequent itemset - A frequent item set is defined as a subset of words that appear more than a user defined threshold in the data set.
Downward closure property : If a k itemset is frequent, then all subsets of the itemset should also be frequent
Objective : Given a transaction data set, discover all frequent item sets such that the support > min threshold(min support) defined by the user

Create a table containing support of each item (each word) present in the dataset(list of documents or transactions). This is the candidate set C1.
Check if the support count of each item is greater than the user defined min support and remove items which fail the criteria. This set is F1, 1- Frequent sets or the set of items of size 1 which are frequent(support > min support).
Now use F1(F1 JOIN F1),  to generate candidate set 2, C2, which is the list of all 2 item sets ( all combinations of 2 words that occur in F1. If F1 ={a,b,c}, C2 = {(a,b),(a,c),(b,c)). The count of each combination is recorded and once again we check if count of such combination > min support.
The combination that satisfy min support form F2
Now a Candidate set C(k+1) is generated from F(K) as follows :
Join  - F(k) X F(k) such that the first k-1 words in each k item subset of F(K) is the same.
Eg (a,b,c) x (a,b,d) =(a,b,c,d) to generate C(K+1) temp.

Pruning : We then prune C(k+1) temp using the downward closure property. Delete those K+1 word sets of C(K+1 temp) whose K item subsets are not elements of F(K)

The support of the remaining K+1 item subsets are recorded
Now F(k+1) is generated from C(k) by checking for those subsets of C(k+) which satisfy the min support condition
}

Final Function output:
The apriori function generates upto  k item frequent sets where k is a user defined parameter, and the min sup (sup) defined by the user and this is stored in a dictionary whose key is the number of elements in an item set.
We then extract the k item frequent sets that is required and the count of items is also recorded.
If there are no k item subsets generated, based on the defined min support , return “No K item subsets”.

If there are K item subsets :
The item sets are in terms of word id’s presently. We use the vocab file to map the word id’s to the corresponding words and the final output is provided

We record the time  and memory at the end of the program to evaluate the total time taken and total memory usage after progtam run
Results(Frequent –k sets):


Nips 3
https://docs.google.com/spreadsheets/d/1GmcloQYo-cvEiSWEHai2h0Cr5o9kFHCxMWn6mGpq14Q/edit#gid=1733950982

Nips 1

https://docs.google.com/spreadsheets/d/13Rkyd3rw5afHZX1GVkdBxOV2_Od5nLAN_SecAbrMyAM/edit#gid=1277533920

Nips 2
https://docs.google.com/spreadsheets/d/1g96o4KEErKEVQnbRMr2PA8uIUMIdt0VmDDsLdtbygOs/edit#gid=285549011

For support equal to 0.05, we aborted the function after 45 minutes.

Enron 2

https://docs.google.com/spreadsheets/d/18ug4nXgFegGgup5hT-MUA5cjNK_37D-zwHRyQ3Q_q38/edit#gid=1600885356

Enron 1

https://docs.google.com/spreadsheets/d/1jk21OXpQjp5cdymDXTddmWP1LLUkXp5QnigpjWqf8I4/edit#gid=254341111

For support = 0.01, output could not be processed - the program was aborted after ~ 3 hours


KOS 2

https://docs.google.com/spreadsheets/d/1SnCLrJBEfBgql4x-wJrjlhiIfiD_OPUI1CQqzH4myM0/edit#gid=159810995

KOS 3

https://docs.google.com/spreadsheets/d/159aMQrLGAhkH6hKTJOm1Z9ZOYM0OyxW0_WLAYpqmT_c/edit#gid=1686298286

KOS4

https://docs.google.com/spreadsheets/d/1nYJhKlsBZT-ndy5LRTWwKrz_eom-ipndD2puFGj9fAA/edit#gid=493039538
