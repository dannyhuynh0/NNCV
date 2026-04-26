# 5LSM0: Neural Networks for Computer Vision

Welcome to the repository for **5LSM0: Neural Networks for Computer Vision**, a course offered by the Department of Electrical Engineering at Eindhoven University of Technology. This course is hosted by the [Architectures for Relaible Image Analysis Lab](https://github.com/TUE-ARIA).

### Using different models

The four different models placed in their own folders within the "Final assignment" folder. To run a specific model, please copy its content into the model.py, predict.py, and train.py files within the "Final assignment" folder.
Example: If you want to run the Residual U-Net model, copy the content of model_Residual_U_Net.py, predict_Residual_U_Net.py, and train_Residual_U_Net.py into model.py, predict.py, and train.py, respectively.


### Running models

After git cloning the repository and setting up the MobaXterm environment, perform a git pull on MobaXterm to obtain the selected model. After that, go into the "Final assignment" folder and perform the following commands:

```bash
chmod +x jobscript_slurm.sh
sbatch jobscript_slurm.sh
```

Download the best checkpoint, place it in the "Final assignment" folder, and rename it to model.pt.


### Submission

Build the docker image by using:

```bash
docker build -t nncv-submission:latest -f "Final assignment/Dockerfile" "Final assignment"
```

Test it locally by running (on Windows Powershell):
```bash
docker run --rm `
  -v "${PWD}\local_data:/data" `
  -v "${PWD}\local_output:/output" `
  nncv-submission:latest
```

Export image to .tar for submission:
```bash
docker save -o nncv_submission.tar nncv-submission:latest
```

After this, submit each model to both the peak performance server and the robustness server.