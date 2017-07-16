# bike-sharing-neural-network
Roughly this Neural Network model predicts bike sharing count reasonably well. The following are explored.
* to enlarge batch size from 128 to 1024 to make neural network train converge more effectively.
* learning_rate is reduced to half 6 times, starting from 0.2.
* hidden_nodes are tried as 2, 3, 8, 14, 19, 26, 28, 31, 35, 38. Roughly 8 leads to good tradeoff between quality and runtime.
* Iterations are tried as 100, 200, 800, 1600, 2400. Above 800, and we do not observe significant quality improvement.
* To measure quality, we do MSE for train_loss and val_loss, both max and average.
* Parameter num_epochs is added, trying to train more for each batch of sample (longer runtime). But num_epochs > 1 did not lead to better quality. So at current stage, we continue to use default num_epochs = 1.
* Smaller batch size 32 (<- 1024 above) and larger iterations 8000 (<- 800 above) leads to lower average MSE and bigger max MSE, for both train_loss and val_loss : Training loss: max=6.482614 ave=0.100212 ... Validation loss: max=6.380161 ave=0.193627.
* By previous batch size 1024 and iterations 800, we get Training loss: max=5.93705 ave=0.284962 ... Validation loss: max=5.048225 ave=0.457041921.
* From MSE numbers as above, val_loss (max and ave) is not too much higher than train_loss. This indicates that there is no bad overfitting.
* On the way, once we got max MSE val_loss 4.1, but we did not use random seed yet then. Later we began to set random seed in constructor of class NeuralNetwork.
* It seems to be hard to break max MSE 4.0. To improve quality and reduce max MSE further, probably next thing we may try is to add additional hidden layers.
