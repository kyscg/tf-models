# GSoC 2020 with TensorFlow Model Garden

Log repository for work done during the Coding Period of GSoC 2020 with TensorFlow. My project mainly involves migrating TF1.x models to TF2.x and improving documentation. In addition, GitHub support for pull requests and issues will be used in order to create an FAQ document for users.

Mentors:

* [Jaeyoun Kim](https://github.com/jaeyounkim)

* [Xavier Gibert](https://github.com/xavigibert)

---

## Attention OCR Migration

---

## Mobile Video Object Detection

**Task 1: Check all GitHub issues and PRs related to `lstm_object_detection` and summarize key issues and asks from the community.**

Found most of the main issues on GitHub (closed by the bot due to inactivity + open issues) and also a few relevant StackOverFlow questions. Left out some redundant issues but noted their key asks. Next step is to review and prioritize main fixes. Key issues found were:
1. Problems with creating tf-records high
2. More documentation needed (specifically training related: prepping data, etc) high
3. More support required

**Task 2: Rerun model training/evaluation/inference from TensorFlow repo and fix potential issues. For both local and cloud.**

We can fix most fo the issues once we make the code run and regress the model accuracy. As the next step, we can start to rerun models and reproduce the paper results. First focus is on this paper(model): https://arxiv.org/abs/1711.06368 , because once the infrastructure is ready, it would be easy to just retrain the other paper.

Starting with [this config](https://github.com/tensorflow/models/blob/master/research/lstm_object_detection/configs/lstm_ssd_mobilenet_v1_imagenet.config) file. Let's see what the future holds!

## GitHub Issue Support

---

## Improve Documentation

* TF1.x --> TF2.x migration guide

* GCP tutorial guide (Merge the existing document in the test-bed repository and the one in the CS231n repo)

---

## Polish README files

A list of README files that need to be updated according to [the template](https://github.com/tensorflow/models/blob/master/.github/README_TEMPLATE.md):

* Asynchronous Advantage Actor Critic (A3C) playing Cartpole
  * Change name of folder to A3C_Cartpole

  * Blog Post: <https://blog.tensorflow.org/2018/07/deep-reinforcement-learning-keras-eager-execution.html>
  
* Adversarially Trained ImageNet models **(To be archived) (Low priority)**
  * Follow the template

* Adversarial Text
  * Everything good, some minor changes in README only.

* AudioSet
  * Follow template, possibly large changes required. Dataset?

* AutoAugment
  * Small README changes only

* Cognitive Planning
  * Small README changes

  * Add SUNCG dataset **(low priority)**

* Cross-View Training
  * Minor README changes
