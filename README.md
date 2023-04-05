
# Neural Net Metaheuristic Optimization

A study on how different evolutionary algorithms optimize the weights of a neural network.

- Dataset Used : [Bank_Personal_Loan_Modelling](https://www.kaggle.com/datasets/krantiswalke/bank-personal-loan-modelling)
- Neural Net Architecture: 
     - Input Layer: 12
     - Hidden Layer: 16, $12*16\ weights + 12\ biases = 208\ params$
     - Output Layer: 1, $16*1\ weights + 1\ bias = 17\ params$
     - Total Params: 225



## Algorithms Used

- Ant Colony Optimization (over continuous problem space)
- Cultural Algorithm
- Genetic Algorithm
- Particle Swarm Optimization
## Performance Comparison

- Loss function used: Binary Cross Entropy ([torch.nn.BCELoss](https://pytorch.org/docs/stable/generated/torch.nn.BCELoss.html))

| Algorithm      | Epochs | Loss  | Accuracy(%) |
|----------------|--------|-------|-------------|
| Cultural       | 1000   | 0.207 | 91.8        |
| Genetic        | 5000   | 1.039 | 85.2        |
| Particle Swarm | 1000   | 0.135 | 94.4        |
| Ant Colony     | 1000   | 0.257 | 90.8        |

![alt text](https://github.com/lemontree404/Neural-Net-Evolutionary-Optimization/blob/main/figs/f1.png)


## Observations

- Right off the bat, the evolutionary algorithms were much more computationally intensive and took longer to converge at the global minima

- Genetic Algorithm in particular needed much more epochs than the rest to converge to the local minima.

- The evolutionary algorithms were much more stochastic when compared to the Swarm Intelligence Algorithms.

- The swarm intelligence algorithms reached the global minima in <400 epochs and were much more consistent with their population.
# Inferences

- Particle Swarm Optimization performed the best because it was inherently able to handle the continuous nature of this problem. Moreover it was more dependent on the loss function than stochasticity to converge to the minima which made its results much more reliable and consistent.

- The Ant Colony Optimization algorithm had to be reframed in order to accomodate the continuous problem space (a probability distribution was used instead of a probability mass function).

- Both evolutionary algorithms behaved very sporadically due to their stochastic esscence. They relied a lot on randomness due to the crossover and mutate functions. So even though they were able to reach the local minima given enough epochs, their results were not as reliable.
