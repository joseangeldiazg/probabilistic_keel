# probabilistic_keel

This repository has the end result of the TFG carried out during 2016. The possibility of obtaining the results probabilistically rather than discrete results for further processing and obtaining ROC curves for evaluation are added to certain algorithms.

The modified algorithms and their modifications are:

**1.Naïve Bayes**: Due to statistical and probabilistic nature more specifically, this algorithm is that less programming required to obtain probabilities as already working with them in origin. At a given point of the program, this algorithm, obtain  the probabilities for each instance of belonging to each of the classes in the problem. The work done in this algorithm, passed locate this point, and get an array with each of the probabilities for each class evaluated. 

**2.KNN**: This algorithm is framed within Lazy Learning algorithms, and is based on the distance. Given its nature, in which a class is assigned to a sample based on the nearest k, the necessary first step for this algorithm is the generation of the necessary structures to store the probabilities for each of the classes. This step is necessary in all modified algorithms and space reservation can be summarized in two matrices of rational values where the number of rows corresponds to the number of samples in each problem, and the number of columns is the same as the number of different classes that each problem. Once generated and initialized these structures, as with the Naïve Bayes algorithm, it is necessary to locate the point in the code where the classification is performed. kNN, makes its classification at a point where based on a distance k, the number of examples of each class are accounted for, finally assigning the example, the majority class in that distance k.


To illustrate the calculation of the probabilities from this, we will use as an example the following figure. 

<img width="249" alt="captura de pantalla 2016-11-05 a las 18 38 19" src="https://cloud.githubusercontent.com/assets/10519534/20032271/0d5fb1ba-a387-11e6-8ebf-f3a79ec65744.png">

To understand this example we will use these premises:

• The green circle represents the observation that we are classifying.
• Each of the different geometric shapes represent observations of which we know its class (training), each representing a different class.
• The solid line represents a k = 3 while the discontinuous represents a value of k = 5.

Based on this, once located the point at which the algorithm accounts for each of the classes in a given distance, obtaining the probability is trivial. Notice how in the case of k = 3 for the above example, the probability of our circle belonging to the class triangle is 2/3 while the probability of belonging to the class represented by the square is 1/3. That is why obtaining probabilities for each example is based on obtaining the number of examples of each class available in a k distance, divided by the distance itself k.


**3.MLP-BP**: This algorithm is based on neural networks, this indicates that the result and the classification of their examples will be based on calculating a score value or weight for each of the possible classes to be evaluated, that is, we simply repurpose this value to be given as probabilities. This algorithm reaches a point where it generates the neural network, and collects the maximum result of this assigning that class to the example in question. The process of obtaining the probability in this case leads to identify and obtain this point all weight values ​​for each of the classes. Once obtained proceed as follows:

• The weight values ​​are contained in a range that can take negative values. The first step is to normalize each of these values ​​to a range that goes from 0 to 1.
• Notice how the sum of the previous values ​​for each class can be greater than one, so the last step to get the probabilities as such will normalize the 0-1 range values ​​of each of the classes range 0- 1 general, ie the sum of all values ​​is equal to 1 while maintaining the proportion.
• Once we have these standard values we simply loaded into the above structures.


**4-SMO**: The SMO algorithm is based on support vector machines. Their results are based on hyperplanes on the training set and classify instances. It is for this reason that the algorithm SMO also provides for each of the classes to classify a result, as happened with Naïve Bayes, also probabilistic. According to the specification of the algorithm Weka these probabilities are obtained differently if we are facing a binomial or multi-class problem.

Before a binomial problem simply we normalize the output of the support vector machine to 0-1 interval for all classes involved.

To a multi-class problem differs from the above process is that for this sorting method pairs or pairwise classification proposed by Hastie and Tibshirani used. This process is also known as 1 vs 1 and facing each of the possible pairs with their predicted probabilities together.

Given this modification in this algorithm is minimal simply going to locate the point where the probabilities are obtained and loading these structures needed to, using file handling, dumping its output.

**5-C45**:  This algorithm is based on decision trees, it is therefore a priori the result they offer is discreet, making it impossible ROC curve representation. Saying that this result is thus a priori, is not a term taken lightly, since it is many literature and scientific papers that support the ROC curve one of the best methods to assess such algorithms, so that many implementations of these, as is the case which is in KEEL, and gets probabilities for each of the classes.

These probabilities are obtained by using a recursive methods ranging down in the tree structure to stand in the leaves. Upon reaching each of the sheets, we have certain weights for each of the classes so computing this probability is calculated as the ratio between the weights of each of the classes in question and the sum of all weights in tree leaf.

Once located this point of calculation of probabilities and just before the class assign more weight to the examples, we can collect all probability values ​​in the necessary structures to present their outputs.





