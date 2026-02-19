import numpy as np
import pandas as pd

# Step 1: Create Dataset
data = [
    ['High', 'Yes', 'Yes', 'Yes'],
    ['High', 'Yes', 'No', 'Yes'],
    ['Normal', 'Yes', 'Yes', 'No'],
    ['High', 'No', 'Yes', 'Yes'],
    ['Normal', 'No', 'No', 'No']
]

columns = ['Fever', 'Cough', 'Fatigue', 'Disease']

df = pd.DataFrame(data, columns=columns)

print("Training Data:\n")
print(df)

# Separate features and target
X = np.array(df.iloc[:, :-1])
y = np.array(df.iloc[:, -1])

# Step 2: Initialize S and G
S = X[0].copy()  # First positive example
G = [['?' for _ in range(len(S))]]

print("\nInitial Specific Hypothesis (S):", S)
print("Initial General Hypothesis (G):", G)

# Step 3: Candidate Elimination Algorithm
for i in range(len(X)):
    if y[i] == 'Yes':  # Positive example
        for j in range(len(S)):
            if S[j] != X[i][j]:
                S[j] = '?'
    else:  # Negative example
        for j in range(len(S)):
            if S[j] != X[i][j]:
                G.append(['?' if k != j else S[k] for k in range(len(S))])

print("\nFinal Specific Hypothesis (S):", S)

# Remove duplicate and overly general hypotheses
G_final = []
for g in G:
    if g not in G_final:
        G_final.append(g)

print("Final General Hypothesis (G):")
for g in G_final:
    print(g)


OUTPUT:
Training Data:

    Fever Cough Fatigue Disease
0    High   Yes     Yes     Yes
1    High   Yes      No     Yes
2  Normal   Yes     Yes      No
3    High    No     Yes     Yes
4  Normal    No      No      No

Initial Specific Hypothesis (S): ['High' 'Yes' 'Yes']
Initial General Hypothesis (G): [['?', '?', '?']]

Final Specific Hypothesis (S): ['High' '?' '?']
Final General Hypothesis (G):
['?', '?', '?']
['High', '?', '?']
