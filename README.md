# Add / fix by CK

- java version fix : 1.7 -> 1.8

- add method tag total f1 score  

  - example code : [ConfusionMatrixTest](./src/test/java/com/github/habernal/confusionmatrix/ConfusionMatrixTest.java) : testF1Score()

  ```bash
   ↓gold\pred→                      LC          OG          PS          QT
                         0           5          10           0           0
            LC          18          10           0           0           0
            OG          11           0          34           0           0
            PS          34           0           0           8           0
            QT           0           0           0           0           4
  
  {Precision=0.7887323943661971, F1Score=0.5894736842105263, Recall=0.47058823529411764}
  ```

  

# confusion-matrix

A minimalistic Java implementation of confusion matrix for evaluating learning algorithms, including accuracy, macro F-measure, Cohen's Kappa, and probabilistic confusion matrix.

(c) Ivan Habernal

Licenced under ASL 2.0

## Installation

Add this Maven dependency

```
<dependency>
  <groupId>com.github.habernal</groupId>
  <artifactId>confusion-matrix</artifactId>
  <version>1.0</version>
</dependency>
```

## Usage

An example from http://www.compumine.se/web/public/newsletter/20071/precision-recall

```
     A  B  C
A  	25 	5 	2
B  	3 	32 	4
C  	1 	0 	15
```

```java
ConfusionMatrix cm = new ConfusionMatrix();

cm.increaseValue("neg", "neg", 25);
cm.increaseValue("neg", "neu", 5);
cm.increaseValue("neg", "pos", 2);
cm.increaseValue("neu", "neg", 3);
cm.increaseValue("neu", "neu", 32);
cm.increaseValue("neu", "pos", 4);
cm.increaseValue("pos", "neg", 1);
cm.increaseValue("pos", "pos", 15);

System.out.println(cm);
System.out.println(cm.printLabelPrecRecFm());
System.out.println(cm.getPrecisionForLabels());
System.out.println(cm.getRecallForLabels());
System.out.println(cm.printNiceResults());
```

For other examples, see the JUnit Test in [`ConfusionMatrixTest`](https://github.com/habernal/confusion-matrix/blob/master/src/test/java/com/github/habernal/confusionmatrix/ConfusionMatrixTest.java) class.
