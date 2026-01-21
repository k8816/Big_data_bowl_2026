Documentation for Sequence to sequence models

Model takes in data from all pre-throw data of the receiver/db, and quarterback, as well as the frame_id (the # of seconds after throw / 10) and predicts the player's position.
Even if passer data is not available, model still works.

Files:
- best_model.pth: Model weights for MultiScaleCNNLSTMSeq2Seq class with hidden_dim=64 and known pre-submission approximate RMSE. Submitted to competition.
- submitted_model.pth: Model weights for MultiScaleCNNLSTMSeq2Seq class with hidden_dim=64 and trained right up until competition deadline. Submitted to competition.
- Data_saver.ipynb: Creates train_set.pt and test_set.pt (not uploaded). These datasets are used to train the model.
- MS-Seq2Seq-train.ipynb: Used to train MultiScaleCNNLSTMSeq2Seq locally.
- MS-Seq2Seq-eval.ipynb: Has code needed to create a submission.csv. Unnecessary when submitting to kaggle.

Data: 
Datasets created via Data_saver.ipynb
  - ids: the full play id (used only for model examination and debugging)
  - x0: a constant np.array of 27 constant features:
    - qb and receiver/db height, weight, starting x and y, ending x and y, ending orientation, ending component velocities, ending acceleration
    - predicting player's role (0 for defense, 1 for offense)
    - number of output frames (ball in air duration/10)
  - x1a: np.array of (num_input_frames, 10). Each frame has 10 features for the player of interest
    - x,y position
    - component velocities
    - component acceleration
    - component orientation
    - speed and |acceleration|
  - x1b: np.array of (num_input_frames, 10). Same as x1a but for the passer on the play. May be empty if no passer info given
  - x2: np.array with two numbers: last known x and y of player of interest.
  - targets: np.array of (num_output_frames, 2). Contains target for a play. Only in train dataset
  - duration: number of frames needed to predict for a training instance.

Design:





Results:
Submissions
- best_model (hidden_dim = 64):
  - local approx RMSE (trained after competition): .65
  - local approx RMSE (at time of submission): .80
  - competition RMSE: .79708
- submitted model (hidden_dim = 64):
  - competition RMSE: .81202
 
Other experiments
- hidden_dim = 32: local approx RMSE: .83
- hidden_dim = 128: .97
- hidden_dim = 256: 1.2
Models not uploaded.

Conclusion: 
Using a hidden dimension of 64 was the best at balancing robustness and speed of training. With higher hidden dimensions means exponentially more parameters which took too long to train given competition constraints. A 32 feature hidden dimension trained for roughly the same time as for the 64 instance, with slightly lower accuracy. Seq2seq substantially outperformed frame by frame models by about .3 RMSE.

Other notes:
- If using locally, some file names in notebooks are hardcoded in and are inconsistent.
- I really appreciate it if anyone took the time to read any of this
