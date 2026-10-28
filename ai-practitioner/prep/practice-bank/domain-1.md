# Domain 1 — Fundamentals of AI and ML

32 practice questions.

### Q1. What does precision measure for a binary classifier?

Format: single-choice · Task: 1.3 · Topic: precision · Difficulty: easy

- **A.** Of all the examples the model labeled positive, how many were truly positive.
- **B.** Of all the truly positive examples, how many the model found.
- **C.** The share of all predictions (positive and negative) that were correct.
- **D.** How balanced precision and recall are in one number.

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Precision asks: when the model says “yes,” how often is it right? Formula: TP ÷ (TP + FP).
- **B:** That describes recall, not precision. Recall uses false negatives; precision uses false positives.
- **C:** That is accuracy. Accuracy looks at every prediction, not only the positive ones.
- **D:** That is the idea behind the F1 score. F1 combines precision and recall; it is not precision itself.

</details>

### Q2. What does recall measure for a binary classifier?

Format: single-choice · Task: 1.3 · Topic: recall · Difficulty: easy

- **A.** Of all the examples the model labeled positive, how many were truly positive.
- **B.** Of all the truly positive examples in the data, how many the model correctly found.
- **C.** How many true negatives the model produced.
- **D.** The model’s training loss on the last epoch.

<details><summary>Answer</summary>

**Correct:** B

- **A:** That is precision. Precision worries about false alarms (false positives), not missed cases.
- **B:** Correct. Recall asks: of every real “yes” case, how many did we catch? Formula: TP ÷ (TP + FN).
- **C:** True negatives matter for accuracy and specificity, but recall focuses on finding positives.
- **D:** Training loss is an optimization signal during training, not the same as recall on labeled outcomes.

</details>

### Q3. A fraud model scores 100 alerts as fraud. Of those, 80 are real fraud (TP = 80) and 20 are false alarms (FP = 20). What is precision?

Format: single-choice · Task: 1.3 · Topic: precision · Difficulty: medium

- **A.** 0.80
- **B.** 0.20
- **C.** 1.00
- **D.** 0.50

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Precision = TP ÷ (TP + FP) = 80 ÷ (80 + 20) = 80 ÷ 100 = 0.80. Four out of five alerts were real fraud.
- **B:** 0.20 is the false-alarm share among alerts (20 ÷ 100), not precision. Precision is the true share: 0.80.
- **C:** Precision is 1.0 only if every positive prediction is correct (FP = 0). Here there are 20 false alarms.
- **D:** 0.50 would mean half the alerts were wrong. Here 80 of 100 were right, so precision is 0.80.

</details>

### Q4. There are 60 real defective parts on a line. The model finds 45 of them (TP = 45) and misses 15 (FN = 15). What is recall?

Format: single-choice · Task: 1.3 · Topic: recall · Difficulty: medium

- **A.** 0.45
- **B.** 0.75
- **C.** 0.25
- **D.** 15

<details><summary>Answer</summary>

**Correct:** B

- **A:** Do not divide by 100 unless the total of TP + FN is 100. Here TP + FN = 60, so 45 ÷ 60 is not 0.45.
- **B:** Correct. Recall = TP ÷ (TP + FN) = 45 ÷ (45 + 15) = 45 ÷ 60 = 0.75. The model caught three-quarters of the defects.
- **C:** 0.25 is the miss rate (15 ÷ 60). Recall is the catch rate: 45 ÷ 60 = 0.75.
- **D:** 15 is the count of missed defects (FN), not a recall score. Recall is a ratio between 0 and 1.

</details>

### Q5. A test set has TP = 70, TN = 20, FP = 5, and FN = 5 (100 examples). What is accuracy?

Format: single-choice · Task: 1.3 · Topic: accuracy · Difficulty: medium

- **A.** 0.70
- **B.** 0.85
- **C.** 0.90
- **D.** 0.95

<details><summary>Answer</summary>

**Correct:** C

- **A:** 0.70 only counts true positives over the whole set. Accuracy also counts true negatives as correct.
- **B:** That would be (70 + 15) ÷ 100 or a similar mix-up. Correct count is TP + TN = 90.
- **C:** Correct. Accuracy = (TP + TN) ÷ total = (70 + 20) ÷ 100 = 90 ÷ 100 = 0.90.
- **D:** 0.95 would need 95 correct predictions. Here TP + TN = 90, so accuracy is 0.90.

</details>

### Q6. A model has precision = 0.80 and recall = 0.80. What is its F1 score?

Format: single-choice · Task: 1.3 · Topic: f1-score · Difficulty: medium

- **A.** 0.64
- **B.** 0.80
- **C.** 1.60
- **D.** 0.00

<details><summary>Answer</summary>

**Correct:** B

- **A:** 0.64 is precision × recall (0.8 × 0.8). F1 is the harmonic mean, not the product.
- **B:** Correct. F1 = 2 × (P × R) ÷ (P + R) = 2 × (0.8 × 0.8) ÷ (0.8 + 0.8) = 1.28 ÷ 1.6 = 0.80. When P and R match, F1 equals that value.
- **C:** 1.60 is P + R. F1 never goes above 1.0; it is a balanced average of the two rates.
- **D:** F1 is 0 only if precision or recall is 0. Here both are 0.80, so F1 is 0.80.

</details>

### Q7. In a confusion matrix for a “spam vs not spam” model, what is a false positive (FP)?

Format: single-choice · Task: 1.3 · Topic: confusion-matrix · Difficulty: easy

- **A.** A spam email the model correctly labels as spam.
- **B.** A normal email the model incorrectly labels as spam.
- **C.** A spam email the model misses and labels as not spam.
- **D.** A normal email the model correctly leaves in the inbox.

<details><summary>Answer</summary>

**Correct:** B

- **A:** That is a true positive (TP): the model said spam and it really was spam.
- **B:** Correct. False positive means the model cried “spam!” when the email was fine—a false alarm.
- **C:** That is a false negative (FN): a real positive case the model failed to catch.
- **D:** That is a true negative (TN): predicted not spam, and it really was not spam.

</details>

### Q8. A hospital triage tool flags patients for an expensive follow-up scan. False alarms waste money and scare patients. Which metric should the team prioritize first?

Format: single-choice · Task: 1.3 · Topic: precision · Difficulty: medium

- **A.** Precision
- **B.** Recall only, with no regard for false alarms
- **C.** Training set size
- **D.** Inference latency in milliseconds

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. High precision means when the tool says “scan needed,” it is usually right—fewer false alarms.
- **B:** Maxing recall alone can flood the clinic with false positives. Costly scans need precision attention too.
- **C:** More data can help models, but it is not the evaluation metric that tracks false alarms.
- **D:** Latency measures speed, not whether positive flags are trustworthy. Precision tracks that trust.

</details>

### Q9. A factory must catch almost every cracked part before shipping. Missing a cracked part is far worse than occasionally rechecking a good part. Which metric matters most?

Format: single-choice · Task: 1.3 · Topic: recall · Difficulty: medium

- **A.** Precision
- **B.** Recall
- **C.** Accuracy alone on a set that is 99% good parts
- **D.** Model file size on disk

<details><summary>Answer</summary>

**Correct:** B

- **A:** Precision reduces false alarms. Here missing cracks (false negatives) is the main risk, so recall comes first.
- **B:** Correct. High recall means few missed cracked parts. Extra rechecks of good parts are acceptable in this story.
- **C:** Accuracy can look great while still missing rare cracks. Rare defects need recall (or similar) checks.
- **D:** File size is an ops detail. It does not tell you how many cracked parts you miss.

</details>

### Q10. A dataset has 990 normal logins and 10 account takeovers. A model that always predicts “normal” scores 99% accuracy. Why is accuracy misleading here?

Format: single-choice · Task: 1.3 · Topic: accuracy · Difficulty: medium

- **A.** Because 99% is above a common 95% pass mark, so the model must be useful.
- **B.** Because the model never finds any takeovers, so recall for the rare class is 0.
- **C.** Because accuracy cannot be computed when classes are uneven.
- **D.** Because precision and recall are always equal to accuracy.

<details><summary>Answer</summary>

**Correct:** B

- **A:** A high accuracy number does not prove usefulness when the rare class is what you care about.
- **B:** Correct. Always saying “normal” is right on 990 cases but catches 0 of 10 attacks. Accuracy hides that failure.
- **C:** Accuracy can still be computed. The problem is that it can look excellent while missing the rare class.
- **D:** They are not the same. Precision and recall focus on the positive class; accuracy mixes everything.

</details>

### Q11. A classifier marks 10 messages as urgent. Nine really are urgent (TP = 9) and one is not (FP = 1). What is precision?

Format: single-choice · Task: 1.3 · Topic: precision · Difficulty: easy

- **A.** 0.10
- **B.** 0.90
- **C.** 9.00
- **D.** 0.50

<details><summary>Answer</summary>

**Correct:** B

- **A:** 0.10 would be 1 ÷ 10 (the error share). Precision is the correct share among positives: 9 ÷ 10.
- **B:** Correct. Precision = 9 ÷ (9 + 1) = 0.90. Nine of the ten “urgent” flags were right.
- **C:** Precision is a rate from 0 to 1, not a raw count. The count TP = 9 is not the precision score.
- **D:** Nothing in the counts supports a coin-flip precision. 9 of 10 positives were correct.

</details>

### Q12. There are 12 real urgent messages. The model finds 9 (TP = 9) and misses 3 (FN = 3). What is recall?

Format: single-choice · Task: 1.3 · Topic: recall · Difficulty: medium

- **A.** 0.75
- **B.** 0.90
- **C.** 3.00
- **D.** 1.00

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Recall = 9 ÷ (9 + 3) = 9 ÷ 12 = 0.75. Three-quarters of real urgents were found.
- **B:** 0.90 would match a precision example with FP = 1, not this recall setup with FN = 3.
- **C:** 3 is the miss count (FN). Recall is the catch rate 9 ÷ 12, not the miss count itself.
- **D:** Recall is 1.0 only if FN = 0. Here three urgents were missed, so recall is below 1.

</details>

### Q13. A model has TP = 40, FP = 10, and FN = 10. What is the F1 score?

Format: single-choice · Task: 1.3 · Topic: f1-score · Difficulty: medium

- **A.** 0.50
- **B.** 0.80
- **C.** 0.90
- **D.** 1.00

<details><summary>Answer</summary>

**Correct:** B

- **A:** Work the rates first. Precision = 40 ÷ 50 = 0.8 and recall = 40 ÷ 50 = 0.8, so F1 is not 0.5.
- **B:** Correct. P = 40 ÷ (40 + 10) = 0.8; R = 40 ÷ (40 + 10) = 0.8; F1 = 2 × 0.8 × 0.8 ÷ (0.8 + 0.8) = 0.8.
- **C:** 0.90 might look like (40 + something) ÷ total, but F1 from these counts is 0.80.
- **D:** F1 is 1.0 only with perfect precision and recall (no FP and no FN). Here both FP and FN are 10.

</details>

### Q14. Which statements about precision are correct? (Select TWO.)

Format: multi-response · Task: 1.3 · Topic: precision · Difficulty: medium

- **A.** Precision falls when false positives rise, if true positives stay the same.
- **B.** Precision is the same formula as recall.
- **C.** Precision ignores true negatives.
- **D.** Precision is always higher than accuracy.
- **E.** Precision requires unlabeled production data only.

<details><summary>Answer</summary>

**Correct:** A, C

- **A:** Correct. More false alarms in the denominator of TP ÷ (TP + FP) pulls precision down.
- **B:** False. Recall uses FN in the denominator; precision uses FP. They answer different questions.
- **C:** Correct. The precision formula only uses TP and FP. TN never appears in it.
- **D:** False. Precision can be higher or lower than accuracy depending on the counts.
- **E:** False. To compute precision you need labeled outcomes so you know which positives were true.

</details>

### Q15. Which statements about recall are correct? (Select TWO.)

Format: multi-response · Task: 1.3 · Topic: recall · Difficulty: medium

- **A.** Raising the positive decision threshold usually increases recall.
- **B.** Recall focuses on how many real positive cases the model finds.
- **C.** Missing a real positive case increases the false-negative count and hurts recall.
- **D.** Recall is identical to specificity.
- **E.** Recall cannot be used for medical screening tasks.

<details><summary>Answer</summary>

**Correct:** B, C

- **A:** False. A stricter threshold usually means fewer positive calls, which often lowers recall.
- **B:** Correct. Recall is the catch rate for the positive class: TP ÷ (TP + FN).
- **C:** Correct. Every miss is an FN; more FN makes the recall fraction smaller.
- **D:** False. Specificity is about correctly identifying negatives; recall is about finding positives.
- **E:** False. Screening often prioritizes high recall so few true cases are missed.

</details>

### Q16. Which statements about the F1 score are correct? (Select TWO.)

Format: multi-response · Task: 1.3 · Topic: f1-score · Difficulty: medium

- **A.** F1 is the harmonic mean of precision and recall.
- **B.** If either precision or recall is 0, F1 is 0.
- **C.** F1 always equals accuracy.
- **D.** F1 can be greater than 1 when the model is strong.
- **E.** F1 ignores false positives completely.

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. The usual formula is F1 = 2PR ÷ (P + R), which is the harmonic mean of P and R.
- **B:** Correct. The product PR becomes 0, so F1 becomes 0. You cannot “average away” a zero rate.
- **C:** False. Accuracy includes true negatives; F1 does not. They match only in special cases.
- **D:** False. Precision and recall are at most 1, so F1 is also at most 1.
- **E:** False. False positives lower precision, and lower precision lowers F1.

</details>

### Q17. A team is choosing evaluation metrics for a rare-event detector. Which choices are appropriate? (Select TWO.)

Format: multi-response · Task: 1.3 · Topic: evaluation-metrics · Difficulty: hard

- **A.** Track precision and recall (or F1) for the rare positive class.
- **B.** Rely only on overall accuracy because it is simplest.
- **C.** Inspect a confusion matrix to see FP and FN counts, not only a single score.
- **D.** Delete all negative examples so every metric becomes 100%.
- **E.** Skip a held-out test set if training loss looks low.

<details><summary>Answer</summary>

**Correct:** A, C

- **A:** Correct. These metrics show how well you find rare events without drowning in false alarms.
- **B:** Risky. With rare events, accuracy can look excellent while you miss nearly every event.
- **C:** Correct. The matrix shows the kinds of mistakes. One summary number can hide that detail.
- **D:** That would break evaluation. You need realistic negatives to measure false alarms.
- **E:** False. Low training loss can mean memorization. You still need held-out evaluation.

</details>

### Q18. On 1,000 examples a model has TP = 0, TN = 990, FP = 0, FN = 10. What is accuracy, and what does it imply?

Format: single-choice · Task: 1.3 · Topic: accuracy · Difficulty: hard

- **A.** Accuracy = 0.99; the model is excellent at finding the positive class.
- **B.** Accuracy = 0.99; the model never predicts positive, so recall for positives is 0.
- **C.** Accuracy = 0.00 because there are no true positives.
- **D.** Accuracy = 0.10 because FN = 10.

<details><summary>Answer</summary>

**Correct:** B

- **A:** Accuracy is 0.99, but TP = 0 means it found zero positives. Excellence for the rare class is false.
- **B:** Correct. (TP + TN) ÷ 1000 = 990 ÷ 1000 = 0.99, yet recall = 0 ÷ (0 + 10) = 0. High accuracy, zero catch rate.
- **C:** Accuracy still counts true negatives. 990 correct “negative” calls give accuracy 0.99, not 0.
- **D:** Do not turn the FN count into accuracy. Accuracy uses all correct predictions over all examples.

</details>

### Q19. A confusion matrix shows: predicted Positive / actual Positive = 30; predicted Positive / actual Negative = 5; predicted Negative / actual Positive = 10; predicted Negative / actual Negative = 55. How many false negatives are there?

Format: single-choice · Task: 1.3 · Topic: confusion-matrix · Difficulty: medium

- **A.** 5
- **B.** 10
- **C.** 30
- **D.** 55

<details><summary>Answer</summary>

**Correct:** B

- **A:** 5 is predicted Positive but actual Negative—that cell is false positives (FP), not FN.
- **B:** Correct. False negatives are actual Positive cases predicted Negative. That cell is 10.
- **C:** 30 is true positives (TP): predicted Positive and actually Positive.
- **D:** 55 is true negatives (TN): predicted Negative and actually Negative.

</details>

### Q20. A model has precision = 0.60 and recall = 0.90. What is F1, rounded to two decimal places?

Format: single-choice · Task: 1.3 · Topic: f1-score · Difficulty: hard

- **A.** 0.75
- **B.** 0.72
- **C.** 0.54
- **D.** 1.50

<details><summary>Answer</summary>

**Correct:** B

- **A:** 0.75 is the simple average (0.60 + 0.90) ÷ 2. F1 uses the harmonic mean, which is lower here.
- **B:** Correct. F1 = 2 × 0.60 × 0.90 ÷ (0.60 + 0.90) = 1.08 ÷ 1.50 = 0.72. Harmonic mean pulls toward the lower rate.
- **C:** 0.54 is the product 0.60 × 0.90. F1 multiplies by 2 and divides by the sum, giving 0.72.
- **D:** 1.50 is P + R. F1 must stay between 0 and 1.

</details>

### Q21. You lower the score threshold so the model labels more examples as positive. What usually happens to precision and recall?

Format: single-choice · Task: 1.3 · Topic: evaluation-metrics · Difficulty: medium

- **A.** Recall often rises; precision often falls.
- **B.** Precision and recall both always rise together.
- **C.** Recall always falls to zero.
- **D.** Accuracy becomes undefined.

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. More positive calls catch more real cases (higher recall) but also add false alarms (lower precision).
- **B:** They often trade off when you move a threshold. Both rising together is not the usual effect.
- **C:** Lowering the threshold usually finds more positives, so recall tends to rise, not fall to zero.
- **D:** Accuracy remains defined. Threshold changes can move accuracy up or down, but the metric still exists.

</details>

### Q22. A model has TP = 50 and FP = 50. What is precision?

Format: single-choice · Task: 1.3 · Topic: precision · Difficulty: easy

- **A.** 0.00
- **B.** 0.50
- **C.** 1.00
- **D.** 50

<details><summary>Answer</summary>

**Correct:** B

- **A:** Precision is 0 only if TP = 0. Here half the positive predictions are correct.
- **B:** Correct. Precision = 50 ÷ (50 + 50) = 0.50. Half of the positive flags were true.
- **C:** Precision is 1.0 only with FP = 0. Here FP equals TP, so precision is 0.50.
- **D:** 50 is a raw count. Precision is the ratio 0.50, not the count itself.

</details>

### Q23. Which cells of a binary confusion matrix are used to compute precision? (Select TWO.)

Format: multi-response · Task: 1.3 · Topic: confusion-matrix · Difficulty: medium

- **A.** True positives (TP)
- **B.** False positives (FP)
- **C.** True negatives (TN)
- **D.** False negatives (FN)
- **E.** The model’s learning rate

<details><summary>Answer</summary>

**Correct:** A, B

- **A:** Correct. TP is the numerator and part of the denominator in precision = TP ÷ (TP + FP).
- **B:** Correct. FP sits in the denominator. Extra false alarms lower precision.
- **C:** False. TN does not appear in the precision formula.
- **D:** False for precision. FN appears in recall = TP ÷ (TP + FN), not in precision.
- **E:** False. Learning rate is a training setting, not a confusion-matrix cell.

</details>

### Q24. A model finds every real positive case: TP = 100 and FN = 0. What is recall?

Format: single-choice · Task: 1.3 · Topic: recall · Difficulty: easy

- **A.** 0.00
- **B.** 0.50
- **C.** 1.00
- **D.** 100

<details><summary>Answer</summary>

**Correct:** C

- **A:** Recall is 0 when the model finds nothing (TP = 0 with positives present). Here it found all of them.
- **B:** Nothing in TP = 100 and FN = 0 suggests a half score. The catch rate is perfect.
- **C:** Correct. Recall = 100 ÷ (100 + 0) = 1.00. Perfect catch rate for the positive class.
- **D:** 100 is the TP count. Recall is the rate 1.00, not the raw count.

</details>

### Q25. A model has precision = 1.00 because it never makes a false positive, but recall = 0.00 because it never predicts positive when it should. What is F1?

Format: single-choice · Task: 1.3 · Topic: f1-score · Difficulty: hard

- **A.** 1.00
- **B.** 0.50
- **C.** 0.00
- **D.** Undefined forever for every dataset

<details><summary>Answer</summary>

**Correct:** C

- **A:** Perfect precision alone is not enough. With recall 0, the harmonic mean collapses to 0.
- **B:** The simple average of 1 and 0 is 0.5, but F1 uses the harmonic mean and becomes 0 when either side is 0.
- **C:** Correct. F1 = 2 × 1 × 0 ÷ (1 + 0) = 0. If you catch nothing, F1 is zero even with perfect precision on the empty positive set edge case—or when recall is zero.
- **D:** F1 is defined whenever you can compute P and R with a non-zero denominator. Here the value is 0, not “undefined forever.”

</details>

### Q26. You need one summary score that balances false alarms and missed positives for an imbalanced problem. Which metric is the best default among these options?

Format: single-choice · Task: 1.3 · Topic: evaluation-metrics · Difficulty: medium

- **A.** Overall accuracy alone
- **B.** F1 score for the positive class
- **C.** Number of parameters in the model
- **D.** GPU utilization percentage

<details><summary>Answer</summary>

**Correct:** B

- **A:** Accuracy can hide rare-class failures. It is a weak default for imbalanced detection work.
- **B:** Correct. F1 balances precision and recall for the class you care about, which helps when classes are uneven.
- **C:** Parameter count is a model-size detail, not a measure of prediction quality on held-out cases.
- **D:** GPU use is an infrastructure metric. It does not tell you if predictions are good.

</details>

### Q27. Which examples are supervised learning problems? (Select TWO.)

Format: multi-response · Task: 1.1 · Topic: supervised-learning · Difficulty: easy

- **A.** Predicting house price from labeled past sales with known sale prices.
- **B.** Clustering customers into groups with no pre-labeled group names.
- **C.** Classifying support tickets as billing or technical using historical labeled tickets.
- **D.** An agent learning a game only from win/lose rewards with no action labels.
- **E.** Compressing images with an autoencoder without class labels.

<details><summary>Answer</summary>

**Correct:** A, C

- **A:** Correct. Each training example has a known target (price). That is classic supervised regression.
- **B:** That is unsupervised learning. There is no labeled “correct group” for each customer during training.
- **C:** Correct. Labels exist for past tickets, so the model learns a supervised classification mapping.
- **D:** That is reinforcement learning: the agent learns from rewards, not from labeled correct actions.
- **E:** Autoencoders are typically unsupervised (or self-supervised) representation learning, not labeled supervised class prediction.

</details>

### Q28. How does reinforcement learning (RL) mainly differ from typical supervised learning?

Format: single-choice · Task: 1.1 · Topic: learning-paradigms · Difficulty: medium

- **A.** RL learns from rewards and penalties for actions over time, not from a fixed labeled answer for every input.
- **B.** RL always requires a confusion matrix during every training step.
- **C.** RL cannot be used for any sequential decision task.
- **D.** RL is identical to unsupervised clustering.

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. An RL agent tries actions, gets feedback (reward), and improves a policy. Supervised learning maps inputs to known labels.
- **B:** Confusion matrices are for evaluating classifiers. RL training centers on rewards and policies, not required confusion matrices.
- **C:** The opposite is true: RL is especially aimed at sequential decisions (games, robots, routing).
- **D:** Clustering groups unlabeled data. RL optimizes actions for cumulative reward—a different goal.

</details>

### Q29. A team wants a managed environment to build, train, tune, and deploy custom ML models on AWS. Which service fits best?

Format: single-choice · Task: 1.2 · Topic: aws-ml-services · Difficulty: easy

- **A.** Amazon SageMaker AI
- **B.** Amazon Transcribe
- **C.** Amazon Comprehend
- **D.** Amazon Q

<details><summary>Answer</summary>

**Correct:** A

- **A:** Correct. Amazon SageMaker AI is the managed platform for the ML development lifecycle: prepare data, train, tune, deploy, and monitor models.
- **B:** Amazon Transcribe turns speech into text. It is not a general train-and-deploy platform for custom models.
- **C:** Amazon Comprehend analyzes text (sentiment, entities, and more). It is not the full custom ML workbench.
- **D:** Amazon Q is an AI assistant for work and builders. It is not the primary managed ML training and hosting platform.

</details>

### Q30. A support team wants to detect sentiment and extract key phrases from thousands of customer emails without training their own NLP model. Which AWS service is the best fit?

Format: single-choice · Task: 1.2 · Topic: aws-ml-services · Difficulty: easy

- **A.** Amazon Transcribe
- **B.** Amazon Comprehend
- **C.** Amazon SageMaker AI only, with no NLP APIs needed
- **D.** Amazon Bedrock for speech-to-text alone

<details><summary>Answer</summary>

**Correct:** B

- **A:** Amazon Transcribe converts audio to text. Sentiment and key phrases from written email are Amazon Comprehend’s job.
- **B:** Correct. Amazon Comprehend provides NLP APIs such as sentiment analysis and key-phrase extraction on text.
- **C:** You could build a custom model in Amazon SageMaker AI, but for ready-made NLP on text, Amazon Comprehend is the direct fit.
- **D:** Amazon Bedrock serves foundation models through APIs. Speech-to-text is Amazon Transcribe; email NLP here points to Amazon Comprehend.

</details>

### Q31. A call center wants to turn recorded customer phone calls into searchable text so agents can review what was said. Which AWS service should they use?

Format: single-choice · Task: 1.2 · Topic: aws-ml-services · Difficulty: easy

- **A.** Amazon Comprehend as the speech-to-text engine
- **B.** Amazon Transcribe
- **C.** Amazon SageMaker AI JumpStart only for OCR on paper
- **D.** Amazon Q Developer to replace the phone system

<details><summary>Answer</summary>

**Correct:** B

- **A:** Amazon Comprehend analyzes text that already exists. It does not convert audio into text by itself.
- **B:** Correct. Amazon Transcribe is the speech-to-text service that converts audio recordings into text.
- **C:** OCR is about images of text. Phone calls are audio; Amazon Transcribe is the speech-to-text service.
- **D:** Amazon Q helps people with questions and coding tasks. It is not the service that transcribes call audio.

</details>

### Q32. Which activities are typical stages in an AI/ML development lifecycle? (Select THREE.)

Format: multi-response · Task: 1.3 · Topic: ml-lifecycle · Difficulty: medium

- **A.** Define the business problem and success metrics before modeling.
- **B.** Prepare and split data, then train and evaluate a model on held-out data.
- **C.** Deploy the model and monitor it in production for drift and quality.
- **D.** Skip evaluation if the model trains without crashing.
- **E.** Hard-code production labels from the training set forever with no refresh plan.

<details><summary>Answer</summary>

**Correct:** A, B, C

- **A:** Correct. Clear goals and metrics (for example precision or recall targets) come before training.
- **B:** Correct. Data prep, training, and honest evaluation are core lifecycle stages.
- **C:** Correct. Shipping is not the end—you watch real traffic for quality drops and data drift.
- **D:** False. A model can train cleanly and still predict poorly. Evaluation is required.
- **E:** False. Labels and data age. Lifecycle practice includes refreshing data and re-evaluating over time.

</details>