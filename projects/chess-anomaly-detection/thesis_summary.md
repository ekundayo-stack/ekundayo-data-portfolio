Anomaly Detection in Online Chess Using Unsupervised Machine Learning
Master’s Thesis Summary – Ekundayo Onifade
University of Westminster – Data Science & Analytics (MSc)
📌 Abstract

Cheating in online video games has grown increasingly sophisticated, creating major challenges for developers and competitive platforms. Traditional supervised anti-cheat systems require game-specific labelled datasets which are difficult or impossible to obtain due to secrecy and privacy concerns.
This thesis explores the use of unsupervised machine learning algorithms, specifically Isolation Forest and K-Means Clustering, to detect anomalous behaviour in a cleaned and normalised chess dataset.
The study demonstrates that unsupervised anomaly detection provides a scalable, adaptable and realistic method for identifying suspicious gameplay without relying on labelled cheating examples.

1. Introduction

Online games have expanded into massive digital ecosystems supporting competition, communication, and global esports 

Msc Final Thesis

.
However, cheating threatens fairness and integrity across multiplayer platforms, prompting developers to incorporate increasingly advanced machine-learning-based detection tools.
Given limited access to real cheat datasets and the secrecy of anti-cheat systems, this thesis applies anomaly detection to a public chess dataset to investigate whether unsupervised algorithms can identify unusual, potentially engine-assisted gameplay.

1.1 Problem Statement

Cheats are evolving rapidly, making detection increasingly difficult.

Public datasets rarely contain labelled examples of cheating activity.

Most anti-cheat systems rely on game-specific supervised models that are expensive to maintain.

1.2 Aim & Objectives

The study aims to determine whether unsupervised ML can detect anomalies in a cheating-labelled chess dataset.

Objectives include:

Applying K-Means and Isolation Forest to clustered or anomalous gameplay.

Investigating the relationship between flagged moves, Elo ratings, and detected anomalies.

Evaluating which unsupervised method performs more effectively.

2. Literature Review (Summary)

Existing work shows ML can detect cheating in games like Unreal Tournament III using supervised classifiers (SVM, Naïve Bayes, Decision Trees) but suffers from false positives and dataset scarcity 

Msc Final Thesis

.

Anti-cheat research is limited due to secrecy and paywalled cheat communities.

Anomaly detection algorithms like K-Means and Isolation Forest have broad applications in cybersecurity, behaviour analysis, intrusion detection, and fraud detection.

No prior academic work applies anomaly detection specifically to chess cheating detection, making this study novel.

3. Dataset & Methodology
3.1 Dataset

Source: Kaggle “Chess Cheat Detection Dataset” (≈ 48,933 games).
Breakdown:

12,278 games – no cheating

11,028 – both players cheated

25,627 – one player cheated 

Msc Final Thesis

3.2 Data Wrangling

Key cleaning steps included:

Converting game results (“1-0”, “0-1”, “½–½”) into numeric values (0, 1, 2).

Summing binary flagged-move lists into total flagged moves per player.

Fixing erroneous Elo values (“-1” replaced with opponent Elo - 1).

Removing the incomplete “game” column.

Ensuring the dataset was fully numeric for ML algorithm compatibility. 

Msc Final Thesis

3.3 Tools & Technologies

Python, Pandas, NumPy

Scikit-Learn (IsolationForest, KMeans)

Matplotlib (visualisation)

Google Colab as the development environment

3.4 Algorithms
Isolation Forest

Detects anomalies by isolating data points.

Key hyperparameters: max_samples=900, max_features=1.0, bootstrap=True.

K-Means Clustering

Used with n_clusters=2 to partition “normal” vs “anomalous” games.

Cluster separation driven primarily by Elo and flagged moves.

4. Results & Findings
4.1 Isolation Forest – Strong Performance

Isolation Forest proved highly effective:

"Flagged white move" and "flagged black move" were the strongest anomaly indicators.

Elo ratings contributed moderately, while game results had minimal predictive value.

A clear threshold emerged:
Games with more than ~25 flagged moves were consistently classified as anomalies.

Visualisations showed distinct darkening of anomaly points above this threshold.

Lower Elo players showed more anomalies—suggesting greater reliance on engine assistance.

4.2 K-Means – Limited Effectiveness

K-Means results were weaker:

Clusters were driven primarily by Elo, not cheating behaviour.

High-Elo cluster: flagged moves tended to decrease with skill.

Low-Elo cluster: flagged moves tended to increase with skill.

Clusters failed to uncover meaningful cheating patterns and lacked anomaly granularity.

4.3 Overall Finding

Isolation Forest significantly outperformed K-Means as a cheat-detection approach.
It captured relationships between flagged moves and Elo that K-Means could not.
It also demonstrated that unsupervised methods can highlight suspicious gameplay even without labelled ground truth.

5. Contributions to Knowledge

This thesis provides:

The first academic demonstration of unsupervised anomaly detection applied to cheating in chess.

Evidence that Isolation Forest is a promising tool for detecting cheating patterns in online games.

Insights into the behavioural differences between low-Elo and high-Elo cheating tendencies.

A framework that could be extended to other video games lacking labelled cheat datasets.

6. Limitations

Dataset lacked key features used by professional anti-cheats (e.g., move time, engine similarity score, opening libraries).

PGN move strings could not be encoded meaningfully for unsupervised ML.

Some Elo data required inference due to missing values.

Algorithms could not make true chess-semantic judgements (no board-state analysis).

K-Means was too simplistic for behavioural anomaly detection.

7. Recommendations for Future Work

Use richer datasets including:

move time per player

engine-match percentage

full PGN move history

Incorporate techniques such as:

LSTM / sequence models

Graph-based board-state encoders

Ensemble models combining multiple anomaly detectors

Extend results to real multiplayer game datasets (FPS, MOBA, MMO).

8. Conclusion

This thesis demonstrates that Isolation Forest can successfully detect anomalous patterns in a large chess dataset, identifying suspicious games based on flagged move counts and Elo relationships.

One flagged move is not cheating.

Patterns of 25+ flagged moves are anomalous.

Flagged white moves are the strongest overall anomaly driver.

Although K-Means struggled, the study proves that unsupervised ML is both viable and effective for cheat detection especially when labelled data is unavailable.
These results provide a foundation for future work on machine-learning-based anti-cheat systems in modern online gaming.
