# Grammar_Error_Correction
Correction of grammar of input sentence using neural networks

## ML formulation of the problem:
The problem is a sequence to sequence problem. Given an input sequence the model learns the probability of occurrence of the output sequence. For this task, the input sequence is a grammatically incorrect sequence and the output is the grammatically correct version of it.
 
As a starting point, we define the kinds of errors we can solve and the kind we are not targeting and work on achieving the best accuracy for that.
a.	What does the model have to do?
Predict the grammatically correct version of the grammatically incorrect text which was given as input; produce the unchanged text as output if the input text is grammatically correct
b.	What is the ideal outcome?
The ideal outcome is that once we figure out if the errors we are targeting is learned properly by the model, we can use our resources to target more errors, so we can finally on a long term target most common errors.
c.	What output should the model produce?
A sequence of most probable words learned by the model

## Evaluation metrics:
-	In most of these tasks evaluation metric used is the F0.5 score, which is the F1 score with more emphasis on the precision than the recall, since intuitively it is more important to provide a good correction than to rather not produce a correction at all.
-	The MaxMatch or M2 scorer is used to evaluate the performance of GEC systems. The M2 scorer scores the system on the basis of how well the system edits (corrections by system) matches the gold standard edits (perfect corrections) of the input text. It is based on calculation of the Levenstein’s distance between two texts (refer https://dl.acm.org/doi/pdf/10.5555/2382029.2382118).

-	Metrics to evaluate our system: The metric used should be able to quantify the magnitude of match between the edit proposed by the system with the gold standard edit. This can be achieved using multiple metrics. 
-	BLEU score for one is a widely used metric for assessing outputs of language models by comparing the number of matching n grams to produce a score between 0 to 1 where 0 stands for no similarity, and 1 for perfect match.  

-	We can also use the F0.5 score, i.e. the harmonic mean of the precision and the recall with twice the emphasis on precision

## Loss: Masked Categorical Crossentropy is used as the loss function.

## Business Constraints: 
-	We want the system to have high precision and prefer the system predict correctly rather than predict incorrect predictions. 
-	Low latency is always preferred. 
-	Also, since the problem involves taking a grammatically incorrect text as input, when deployed on a server we want optimized handling of input data with low computational resources and power preferably.

