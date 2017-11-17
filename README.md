# easy\_seq2seq

This is an easy to run chatbot built with Python 3.4 and TensorFlow 1.3.


Description written by [the original author of *easy_seq2seq*](https://github.com/suriyadeepan/practical_seq2seq):
> _"An implementation of Seq2Seq that actually works. I want to make it easy for people to train their own seq2seq model with any corpus. I am also
> adding the parameters of my trained model for people to just use it without training. If you have a model that works share your model params here, 
> as external link or do a pull request. I have used Cornell Movie Dialog Corpus to train my model. A link to preprocessed data and scripts for 
> preprocessing can be found in this repo."_
> 
> *Have Fun!*


## Setup

Prerequisites:
  * Recommend using the Anaconda version of the Python environment to ensure all Python package dependencies are met.
  * This code has not yet been tested in a non-Anaconda environment.

Install dependencies

```bash
conda create -n my_environment_name python=3.4 anaconda
source activate my_environment_name
conda install -n my_environment_name pip
pip3 install --upgrade tensorflow
```


Create temporary working directory prior to training

```bash
mkdir working_dir
```


Install dependencies for the web stack (GUI interface)

```bash
cd ui
pip3 install -r requirements.txt
cd ..
```


Download test/train data from Cornell Movie Dialog Corpus

```bash
cd data/
bash pull_data.sh
```


Your own data may be placed into the data/ directory _**after**_ renaming them using the following convention:
* train.enc
* train.dec
* test.enc
* test.dec



## Training

Interrupting the training during execution results in a "pause" of training. All previous checkpoints are saved with the latest one resuming the testing cycle.

```bash
# edit seq2seq.ini file to set 
#		mode = train
python execute.py
# or use custom ini file
#		python execute.py my_custom_conf.ini
```


## Testing

```bash
# edit seq2seq.ini file to set 
#		mode = test
python execute.py
```


## Serve

```bash
# configuration : seq2seq_serve.ini
python ui/app.py
# wait until this message shows up
#		"Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)"
# open up the address in browser, chat with the bot
```
