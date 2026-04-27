# CS372 Final Project: Predicting a Win in Euchre

My project is a machine learning model that predicts whether or not a person will win a hand of Euchre depending on the five cards they were dealt and the trump suit. My family and I regularly play Euchre together and I wanted to see how I could connect the fun of the game to our machine learning class. Euchre is a four player card game, with two people on each team. The goal is to win each hand by taking at least three tricks out of five. A good hand is dependent on the rank and suit of the cards, as Euchre is a trump game, one suit is more powerful than others each hand. 
The model simulated 10,000 hands of the game to learn how certain cards can promote the likelihood for a win. It learned the patterns indicative of winning. It takes four features as an input: overall hand strength, number of trump cards, and whether the player holds the right jack (the most powerful card of the hand), or the left jack (the second most powerful card of the hand). It then predicts a win or a loss based on the four features. 
It is important to note that the numbers I display in the README and in the analysis in the file itself may differ each time the model is run due to the randomness of simulate_outcome().

# Quick Start
Clone the repository, install "pip install -r requirements.txt" to get the associated libraries, and then open Euchre_bot.ipynb on the platform of your choice and run the cells.

# Video links:
Project demo [video2850895539.mp4](video2850895539.mp4)
My long walkthrough was too large to upload to Git repo. Here is a Google Drive link: [https://drive.google.com/file/d/19AuDSJSguMakn_RNN3jQmkeY95J1AKKj/view?usp=drive_link]

# Evaluation
All models were evaluated on over a thousand situations that were not seen in the initial training. The baseline model, which predicts the most likely outcome, sits at 50% and does not learn from the training. The neural net performs at around 60%. The logistic regression model sits at around 63% and the random forest model sits at around 62%. The logistic regression model is the best performing model, likely because win likelihood increases with the strength of the hand.

## Evaluation: Feature Importance
After testing Random Forest configurations, I did data analysis to see what Random Forest learned. The conclusion was that the most important features were hand strength and trump count, with hand strength sensibly coming in the lead because it evaluates the other features. The code file has visualizations demonstrating the results, but they are also pasted below.

| Feature        | Importance |
|---------------|------------|
| Hand_strength | 0.6957     |
| Trump_count   | 0.2484     |
| Has_right     | 0.0187     |
| Has_left      | 0.0372     |


## Evaluation: Ablation Study
At the end of the file, I performed an ablation study to determine how important certain aspects of the model were. This was inspired by my earlier evaluation of feature importance in the random forest model. It focuses on the feature set and divides the options between the full features versus just the core features of hand strength and the count of trump cards. The study also focuses on the weights of certain classes and seeing how penalizing misclassifications can fix the model's tendency to overpredict wins. The results of the study were that weighting does not have an effect on the model bias and that the full four features (evaluating jacks) performs slightly better than the two features alone. The table result of the ablation study is inserted below.


| Feature Set | Class Weight | Test Accuracy | Test F1 Score |
|------------|-------------|--------------|--------------|
| Full       | Standard    | 0.6053       | 0.6146       |
| Full       | Balanced    | 0.6060       | 0.6180       |
| Core       | Standard    | 0.6067       | 0.6174       |
| Core       | Balanced    | 0.6067       | 0.6174       |

## Relevant Scholarly Work
As I was constructing the paper I found a thesis on AI in Euchre. It expanded on my thought process by introducing the possability of Markov decision making and a User Friendly Agent that can predict patterns better in a partenership (as Euchre is played). It also introduces a Hybrid User Friendly Agent that balances aggressive versus cautious ways of playing that are visible in more simple models.

Seelbinder, Benjamin E. Cooperative Artificial Intelligence in the Euchre Card Game, University of Nevada, Reno, United States -- Nevada, 2012. ProQuest, https://login.proxy.lib.duke.edu/login?url=https://www.proquest.com/dissertations-theses/cooperative-artificial-intelligence-euchre-card/docview/1285529898/se-2.
