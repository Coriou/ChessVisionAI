# Chess Vision AI

Chess Vision AI is a project aimed at extracting the state of a chessboard from a screenshot using a trained AI model. This project is part of my training on AI, and it achieves an accuracy of 99.8% in classifying chessboard squares. As long as the chessboard is the default one on [chess.com](https://chess.com). For now.

The model is trained using transfer learning from MobileNetV2 and can classify the state of a chessboard with high accuracy.

![demo](https://i.imgur.com/tf9xkNL.png)

## Usage

### Generate a dataset

Run the `datagen.ipynb` notebook to generate a dataset from the pieces & board in the `data` directory. It took my Intel CPU 20 minutes to generate roughly 10k images / piece.

The data is the default board & pieces found on [chess.com](https://chess.com).

### Train the model

Run the `train.ipynb` notebook to train the model on the generated dataset. The last cell will evaluate the model's performances on the test dataset.

Took just over an hour to train on my Intel CPU thanks to transfer learning from MobileNetV2 (might be better performing pretrained ImageNet models out there).

### Test

Run the `predict_board.ipynb` to test it against a screenshot.

Can also test indivual squares and _debug_ the model in the `infer.ipynb`.

## Detect chessboard from a larger image

The model will only work on images only containing the chessboard. In real life use, this isn't really handy. I've found another project called [tensorflow_chessbot](https://github.com/Elucidation/tensorflow_chessbot) which implemented [chessboard squares detection](https://github.com/Elucidation/tensorflow_chessbot/blob/master/tensorflow_compvision.ipynb) which I have leveraged to detect & extract the chessboard from any screenshot.

I've basically copy / pasted the code, improved it by integrating rotation detection, cleaned it a little and updated it for the newest TF (2.x) and SciPy but it's the same core logic.

Run the `detect_chessboard.ipnyb` notebook to use it.

## Next

In the future, I plan to train the model on more boards and pieces. Currently, the model performs poorly on chessboards from [Lichess](https://lichess.org). Extending the training data to include various board styles should improve performance across different platforms.
