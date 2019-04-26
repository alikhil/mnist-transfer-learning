# Assignment 2
> Alik Khilazhev

This reports describes my solution to Assignment #2.  

## Source code

The source code can be found at [github.com/alikhil/mnist-transfer-learning](https://github.com/alikhil/mnist-transfer-learning). The solution presented as Jupiter notebook. For solving given tasks Keras framework have been used. 

## Part I

### Base model

After building simple sequential model (with `batch_size=100`, Adam optimizer with default LR,  100 epochs and early stopping on accuracy) I fine tuned by hands and found out best configuration: 

- `batch_size=128`
- Adam with `LR=0.0005`
- 100 epochs with early stopping

Which gives 0.9851 accuracy on training set ash 0.9838 on test set. And it stops in 8-ith epoch.

## Batch normalization
|  | |
|---|---|
| ![pic_](https://user-images.githubusercontent.com/7482065/56830153-43852000-686e-11e9-8798-6837b859d130.png)  |  ![kek](https://user-images.githubusercontent.com/7482065/56830262-94951400-686e-11e9-8d57-b800d7530fec.png) |

After applying batch normalization accuracy rose up to 0.9979 on training set and to 0.9912 on validation set. And model converges faster

## Dropout

Model does not overfit on training set. And adding dropout layers improves accuracy on validation set a little bit (0.9912 -> 0.9934).

## Part II

### Pretraineg model with new softmax layer

Model early stopped at 28th epoch with accuracy 0.984 and validation accuracy 0.9025. Training on 500 images took 25.5 seconds in total.

### Layer caching

Model with cached layers was about 30 times faster than previous model.
In this case model was trained on 29404 images and it took 51 seconds in total before early stopping on 64th epoch. And it gave 93% accuracy. 

### Using only first 4 layers

This model showed validation accuracy a slightly better than 5 layer model: 0.9111 vs 0.9025. It early stopped in 29th epoch and training took 26.3 seconds in total.

## Unfreezing top 2 layers

This model performed a bit worse than previous one. It early stopped on 24 epoch with validation accuracy 0.8895. And training on 500 images took 25 seconds.

## Conclusion

In this assignment I learned how to build models for transfer learning, how to update and change existing layers and some interesting features of keras framework. 