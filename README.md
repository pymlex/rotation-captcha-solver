# Rotation CAPTCHA Solver: Circular Patch Alignment Network
<div style="display: flex; width: 100%;">
  <img width="900" height="auto" alt="aptcha-image" src="https://github.com/user-attachments/assets/6b1d64fa-2d5d-4a4c-9fb5-85f919a1a570" style="max-height: 500px; width: auto;" />
</div>

The repository contains a convolutional neural network based on **ResNet-18** that solves **rotation-based CAPTCHA** challenges. In these CAPTCHAs, a circular region is cut from the center of an image and rotated by an unknown angle. The task is to predict the rotation angle required to realign the circular patch with its original position.

## Solution 
### Logics
The **input** of the network consists of an image with a circular hole at the center and the corresponding rotated circular patch. These two images are processed separately by the CNN, after which the extracted features are combined into one tensor. Then the model **predicts** the correct rotation angle, allowing for the automatic reconstruction of the correctly aligned image.

### Dataset
The project utilizes **2000 images** of cats and dogs from [Kaggle’s dataset](https://www.kaggle.com/datasets/abhinavnayak/catsvdogs-transformed). All images are sized at **224×224 pixels**, with the radius of the patch set to **40 pixels**. The angle changes from **0 to 360 degrees**. The target variable is represented as the sine and cosine of the angle to avoid discontinuity when transitioning from 360 to 0 degrees.

### Project Structure
- **cat-captcha-weight.pth**: [Pre-trained weights](https://mega.nz/file/qiRCnJ5Y#gkHD9FwlT8Hhnduzxc-HvnCBMUT5YEHRNXer7EwxQSA) for the ResNet18 model.
- **cat-captcha.ipynb**: Jupyter Notebook with a step-by-step solution for the regression task.

## Results
After training for **60 epochs**, the network demonstrates stable results, with a **MAE** on the test subset of approximately **10 degrees**.
