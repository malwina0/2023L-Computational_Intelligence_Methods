# 2023L Computational Intelligence Methods
## [MLP](https://github.com/malwina0/2023L-Computational_Intelligence_Methods/tree/main/MLP) - Neural Network implementation from scratch
My network performs well in both classification and regression tasks, which was tested on different datasets. It is possible to adjust in it:
* the number of layers and neurons in each layer,
* the number of epochs,
* learning rate,
* batch size,
* initialization method for weights and biases from among: normal distribution, He and Xavier,
* choose whether to use Momentum or RMSProp, and select coefficients for them,
* the activation function in the inner layers from among: sigmoid, linear, tanh and ReLU,
* output activation function from among: linear and softmax,
* the value of the regularization coefficient (when we do not want to use it then it is 0)
* choose whether to use the early stopping method and after how many epochs without improvement stop the algorithm.

## [SOM](https://github.com/malwina0/2023L-Computational_Intelligence_Methods/tree/main/SOM%20(Kohonen%20network) ) - Self Organizing Map (Kohonen network)
The network is rectangular and allows to choose:
* size of netowrk - M and N dimensions
* neighborhood functions: gaussian or mexican hat
* neighborhood width.

The learning of the network is slowing down gradually with successive iterations.
The performance of the Kohonen network was tested on 2D and 3D data.

## [Genetic Algorithm](https://github.com/malwina0/2023L-Computational_Intelligence_Methods/tree/main/Genetic%20Algorithm)
### Problem:
Variant of the cutting stock problem: rilling a circle with rectangles.

We have a given circle of radius r and a set of available rectangles given by three numbers: height, width and value.
The goal is to arrange the rectangles in the circle so as to maximize the sum of their values, satisfying the following conditions:
* the sides of all rectangles were parallel to the axis of the system,
* the interiors of the rectangles had no parts in common (intuitively: the rectangles do not overlap, but they can touch each other with their sides),
* each rectangle can be inserted any number of times.

### My solution: 
**Initialization**: I initialize the circles with rectangles of the same type, which are arranged side by side, starting from the center of the circle.

**Crossover**: I draw 2 individuals (circles), the crossover point and the direction (vertical or horizontal). If for instance a vertical crossover is drawn, then on the right side of the division will be rectangles from one parent individual, and on the left from the other. Such crossover causes large free spaces between the left and right rectangles. In order to fill it there is implemented a mutation, which involves checking how large the distance between the 2 sets of rectangles. If it is larger than the height/width of the smallest rectangle available for a given circle radius then the gap is filled with the largest rectangles that will fit there.

**Mutation**: It involves moving the rectangles that are on the right/left/up/down from some horizontal or vertical line. Both the direction of this line and its value are chosen at random. The rectangles are shifted by a random value from the interval [1, 60].

**Selection**: The selection of individuals for the next iteration will be chosen by a tournament method if population after the iteration is bigger than *N* - parameter of size of the population. If then the selected subset is smaller than N then the losers are added.

**Stop condition**: After each iteration, the value of the best individual will be checked. If after 100 iterations this value will not improve then the algorithm will be stopped.
