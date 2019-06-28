# Basic process:
1. Make a model
2. Does it have high bias?  Tweak bias list until you fit the training set
    - You can also use a subset of the training set to zero in on good hyperparams more quickly 
3. Pull out the dev set and check for variance. Add tweaks for variance
4. Once you have low bias and low variance, get out the test set.

# Knobs to turn

## Data preprocess
- Scale to 0,1 by dividing by 255
- StandardScaler

## Reducing bias
- Learning rate
- Number of iterations / train it longer
- Bigger network
    - Number of hidden layers 
    - Number of nodes per layer
- Network architecture
    - Change activation function (ReLu, Leaky ReLu, others?)
    [Activations in pytorch](https://pytorch.org/docs/stable/nn.html#non-linear-activations-weighted-sum-nonlinearity)
    - Algorithms for choosing intial weights 

### Optimization (making model train faster, reduce bias)
- Learning rate decay
- Mini batch size 
- Batch normalization -- decreases number of iterations needed
[Batch Norm in pytorch](https://pytorch.org/docs/stable/nn.html#normalization-layers)
- Optimizers
    - Gradient descent with momentum 
    - RMSProp 
    - Adam 
[Optimization in pytorch](https://pytorch.org/docs/stable/optim.html)

### Error analysis (reduce bias?)
- Gradient checking ? (Do you do this when you don't implement gradient descent manually?)
- Manual inspection of 200 errors to look for patterns 

## Regularization / Reducing variance
- More data
- Regularization 
    - L1
    - L2
        [L1,L2 in pytorch](https://pytorch.org/docs/stable/nn.html#loss-functions)
    - Dropout
        [Dropout in pytorch](https://pytorch.org/docs/stable/search.html?q=dropout&check_keywords=yes&area=default)

## Other techniques 
- Random hyperparameter search
- Managing results (storing what you tried and how each model did in an organized fashion)

## Ng's Recommendations
Focus first on
- learning rate (sample log scale)
    
Then
- momentum (sample log scale, 1 - beta)
- number of hidden units (sample uniformly)
- mini batch size (powers of 2?)
    
Then
- learning rate decay
- number of layers