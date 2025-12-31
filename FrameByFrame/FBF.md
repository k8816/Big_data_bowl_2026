Documentation for Frame-by-frame models

Finished models:
  Model1: 
    Predicted player position = last known position + (time elapsed * velocity components)
    RMSE = 1.61

Future work:
  Model2:
    Basic MLP that takes in [last known position, last known velocities, ball location, time elapsed, maybe some other stuff]

  Model3:
    Transformer based model which takes in whole player movement before the throw
