# cs372_final_project

My project is a machine learning model that predicts whether or not a person will win a hand of Euchre depending on the five cards they were dealt and the trump suit. Euchre is a four player card game, with two people on each team. The goal is to win each hand by taking at least three tricks out of five. A good hand is dependent on the rank and suit of the cards, as Euchre is a trump game, one suit is more powerful than others each hand. 
The model simulated 10,000 hands of the game to learn how certain cards can promote the likelihood for a win. It learned the patterns indicative of winning. It takes four features as an input: overall hand strength, number of trump cards, and whether the player holds the right jack (the most powerful card of the hand), or the left jack (the second most powerful card of the hand). It then predicts a win or a loss based on the four features. 

## Quick Start
Clone the repository, install "pip install -r requirements.txt" to get the associated libraries, and then open Euchre_bot.ipynb on the platform of your choice and run the cells.

## Video link:

## Evaluation
All models were evaluated on over a thousand situations that were not seen in the initial training. The baseline model, which predicts the most likely outcome, sits at 50% and does not learn from the training. The logistic regression model sits at 63% and the random forest model sits at 62%. The logistic regression model is the best performing model, likely because win likelihood increases with the strength of the hand.

## Evaluation: Feature Importance
After testing Random Forest configurations, I did data analysis to see what Random Forest learned. The conclusion was that the most important features were hand strength and trump count, with hand strength sensibly coming in the lead because it evaluates the other features. The code file has visualizations demonstrating the results, but they are also pasted below.\

Feature Importances:
|Hand_strength|0.6956611223834176|
|Trump_count|0.2483643790195779|
|Has_right|0.01873388184190191|
|Has_left|0.03724061675510251|


## Evaluation: Ablation Study
At the end of the file, I performed an ablation study to determine how important certain aspects of the model were. This was inspired by my earlier evaluation of feature importance in the random forest model. It focuses on the feature set and divides the options between the full features versus just the core features of hand strength and the count of trump cards. The study also focuses on the weights of certain classes and seeing how penalizing misclassifications can fix the model's tendency to overpredict wins. The results of the study were that weighting does not have an effect on the model bias and that the full four features (evaluating jacks) performs slightly better than the two features alone. The table result of the ablation study is inserted below.

Feature Importances:
| FEATURE | CLASS WEIGHT | TEST ACCURACY | TEST F1 SCORE|
|Full|Standard|0.605333|0.614583|
|Full|Balanced|0.606000|0.617970|
|Core|Standard|0.606667|0.617380|
|Core|Balanced|0.606667|0.617380|


Feature Set	Class Weight	Test Accuracy	Test F1-Score
0	Full Features	Standard	0.605333	    0.614583
1	Full Features	Balanced	0.606000	    0.617970
2	Core Features	Standard	0.606667	    0.617380
3	Core Features	Balanced	0.606667	    0.617380

