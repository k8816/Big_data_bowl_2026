Big Data Bowl 2026 Prediciton

This Github repo contains Kevin Zhang's work for the NFL's 2026 Big Data Bowl Prediction Competition hosted by Kaggle. The object of the competiton is to predict a player's (typically a WR or CB) movement during a pass play after the ball is thrown. Submissions are evaluated on the RMSE metric (average distance off of the player's actual position). As of 12/31: My submission is 771st with an RMSE of .806, though model training after the competition improved RMSE locally to roughly .62-.68. 

Models organized in two folders:
- FrameByFrame: As the name suggests these models predict only a player's position for one frame. This was my first approach to the prediciton task.
- Seq2Seq: Takes in a sequence of frames and other data, and outputs a sequence of predicted positions for a player. This approach was much more effective than frame by frame prediction. Actual submissions are in here

Other notes:
- File paths start with "./kaggle" in my working directory, but must be changed to "/kaggle" when submitting on kaggle.
- Submitted notebook on kaggle is different than on github because submissions must use the NFL's submission server and API.
- Models in this repo were trained evaluated locally (on my Mac).
  
