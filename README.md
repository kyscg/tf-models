# GSoC 2020 with TensorFlow Model Garden

Log repository for work done during the Coding Period of GSoC 2020 with TensorFlow. My project mainly involves migrating TF1.x models to TF2.x and improving documentation. In addition, GitHub support for pull requests and issues will be used in order to create an FAQ document for users.

Mentors:

* [Jaeyoun Kim](https://github.com/jaeyounkim)

* [Xavier Gibert](https://github.com/xavigibert)

* [Liangzhe Yuan](https://github.com/yuanliangzhe)

---

## Attention OCR Migration

1. **Preparing the code**: Any dependency that we have should be made compatible with TF2.x. This is important so that we don't end up making mistakes while converting the code. A good practice is to have unit tests written with good coverage.
2. **Install TensorFlow 1.15**: We need to upgrade our TensorFlow to `tf1.15` which is the latest TF1.x version.
3. **Run tests on `tf1.15`**: Just to be careful
4. **Run `tf_upgrade_v2`**: Run this script on both the code and unit tests. Most of the code will convert to symbols only available in TensorFlow 2.x and in cases where symbols are deprecated, `tf.compat.v1` will be used, which we will come to shortly. Usage of the upgrade script is as follows:
```css
$ tf_upgrade_v2 \
  --intree my_project/ \
  --outtree my_project_v2/ \
  --reportfile report.txt
```
5. **Run the tests again on `tf1.15`**: This will weed out any possible bugs.
6. **Install TensorFlow 2.3**: Even tfnightly should do the job.
7. **Test with `v1.disable_v2_behavior`** Re-running your tests with `v1.disable_v2_behavior()` should give the same results as running under 1.15.

After going through the above steps for the AttentionOCR model, I found a few issues which I will list out below.

### Future Work

The main priorities for the immediate future are as follows,

* Convert AttentionOCR to native TensorFlow 2 and run tests.

* Prepare checkpoints for public usage and consolidate documentation.

* Provide interactive tutorials in the form of Google Colab.

* Convert DeepSpeech to native tf2 in collaboration with said PR author.

---

## Mobile Video Object Detection

**Task 1: Check all GitHub issues and PRs related to `lstm_object_detection` and summarize key issues and asks from the community.**

Found most of the main issues on GitHub (closed by the bot due to inactivity + open issues) and also a few relevant StackOverFlow questions. Left out some redundant issues but noted their key asks. Next step is to review and prioritize main fixes. Key issues found were:

1. Problems with creating tf-records **priority: high**
2. More documentation needed (specifically training related: prepping data, etc) **priority: high**
3. More support required

**Task 2: Rerun model training/evaluation/inference from TensorFlow repo and fix potential issues. For both local and cloud.**

We can fix most fo the issues once we make the code run and regress the model accuracy. As the next step, we can start to rerun models and reproduce the paper results. First focus is on this paper(model): <https://arxiv.org/abs/1711.06368> , because once the infrastructure is ready, it would be easy to just retrain the other paper.

Starting with [this config](https://github.com/tensorflow/models/blob/master/research/lstm_object_detection/configs/lstm_ssd_mobilenet_v1_imagenet.config) file. Let's see what the future holds!

## GitHub Issue Support

---

## Improve Documentation

* TF1.x --> TF2.x migration guide **(in progress)**

### GCP Tutorial Guide ~~(Merge the existing document in the test-bed repository and the one in the CS231n repo)~~

Merged CS231n GCP guide into the original testbed doc. New doc can be seen [here](https://tf-model-garden-testbed.readthedocs.io/en/latest/support/gcp.html). Updates include *sign-up + configuration details, gcloud command line tools and jupyter-notebook with Google Compute Engine*.

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
