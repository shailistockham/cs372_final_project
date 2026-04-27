## Attribution
I used the Artificial Intellegence tool, Claude, to help me with this project. It generally suggested ways (in text, not code) that I could meet rubric expectations.

Claude produced the structure behind the SETUP.md file, as I geniunely did not know how technical or specific it should be.

The only element Claude helped me debug in Cell Zero (the first coding block) was simulate_outcome(). I was continuously getting bad validation results, so it suggested multiple ways to modify the numbers of the win_proba line. 
This was the most iterative part of the project. The original version used `strength / 100`, which created severe class imbalance, so Claude suggested recentering around the median. 
However, the model was still inconsistent and inaccurate. I realized why after printing the empirical distribution of hand strengths (min=42, max=86, mean=median=62). 
Finally, I changed the formula to its current state:  `0.5 + (strength - 62) / 50`.

I asked for appropriate values for the linear layers of EuchreNet.

For the out-of-bag early stopping loop, Claude provided preliminary loop structure, but I chose the estimators and extended it to focus on plateau behavior. I also wrote the analysis.

The ablation study structure was created in collaboration with Claude, so I could understand which features to analyze.

Claude suggested adding normalization before Logistic Regression. I integrated it into the existing cell and made sure `X_test_scaled` was used consistently in the final evaluation cell.

The tool also cleaned up unnecessary code for me when I uploaded the final result. 
An early version of the project had LabelEncoder as a string converter, but it wasn't necessary once I changed the Win-Loss to binary labels.
