Documentation for Frame-by-frame models

Each of these models takes in data from all pre-throw data of the receiver/db as well as the frame_id (the # of seconds after throw / 10) and predicts the player's position.

Finished models:
- Model 1: Submission file
- Model 2: Basic MLP that takes in [last known position, last known velocities, ball location, time elapsed, ...]
- Model 3: MLP with more layers
- Model 4: RNN
- Model 5: Transformer
- Model 6: Average of RNN and Transformer
- Model 7: 1D-CNNs

Results of these models were much lower than for Seq-2-seq.
