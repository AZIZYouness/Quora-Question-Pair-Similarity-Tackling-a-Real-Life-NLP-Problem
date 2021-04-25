# Quora-Question-Pair-Similarity-Tackling-a-Real-Life-NLP-Problem
Identify which questions asked on Quora are duplicates of questions that have already been asked.
## Mapping to an ML problem 
Let's try to map this whole problem into a machine learning problem. First, we need to understand what data we have.
- We can download the data using the command(after installing kaggle API):
> kaggle competitions download -c quora-question-pairs
- Or we can download it directely from the quora competition page.
> https://www.kaggle.com/c/quora-question-pairs/data
## Data overview 
- Size of Train.csv - 60MB
- Number of rows in Train.csv = 404,290
- Train.csv contains 5 columns : Unique question ID: qid1, qid2 Text of the question: question1, question2 Binary variable, tell us if Q1 & Q2 are duplicate: is_duplicate
> So, xi = {qid1, qid2, question1, question2}, yi = {is_duplicate}
## Machine Leaning Problem
What we have here is a binary classification problem, for a given pair of questions in text form we need to somehow featurize this data in such a way that it will help us predict if these questions are duplicate or not.
## Business constraints
- The cost of a mis-classification can be very high. For example, if we declare two question which are diffenrent as duplicate, then all the answers for Q1 will be refered to Q2, which is extremly dangerous and costly. That why we will use the probability that Q1 is similar to Q2, so that we can set a threshold of choice , for ex; P(Q1=Q2)>0.99
- Interpretability is partially important. Because we want to undersdand why Q1 is similar to Q2
- No strict latency concerns. Few seconds or minutes are okay.
