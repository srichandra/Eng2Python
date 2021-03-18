# Data Cleaning

1. Dataset consists of english sentence as a comment followed by python code corresponding to the sentence. 
2. Read the dataset line by line to extract the pairs of english sentence and corresponding python block. 
3. Difficulty in extraction comes from the fact that the english sentences start from "#" as well all the comments in python. We create an ignore pattern to first filter out lines that contain In[00]: or just #[num] or just bunch of \s or contain word "driver block/code". 
4. Also, we use a minimum length based on the histogram of english sentence to filter out the comments. 


# Model Architecture and Salient features

We have used the same architecture from the Attention is all you need paper and discussed in the class

#Loss function

We have cross entropy loss function

# Data Preparation

1. For english, we have used spacy tokenization module
2. For python code part, we have used tokenize module which parses the python code into string tokens. For characters like '\n', white spaces - we have encoded them with their token names like newline, indent, endline etc

# Data Extension

No external data has been used

# Python Code embedding strategy

# Evaluation Metrics

# 25 Examples

# Attention
