# Topic-Seg-Label

Codes for the paper "A Weakly Supervised Method for Topic Segmentation and Labeling in Goal-oriented Dialogues via Reinforcement Learning"

Cite this paper:
```
@inproceedings{takanobu2018weekly
  title={A Weakly Supervised Method for Topic Segmentation and Labeling in Goal-oriented Dialogues via Reinforcement Learning},
  author={Takanobu, Ryuichi and Huang, Minlie and Zhao, Zhongzhou and Li, Fenglin and Chen, Haiqing and Zhu, Xiaoyan and Nie, Liqiang},
  booktitle={IJCAI-ECAI},
  year={2018}
}
```

## Data Format

**update later**

## Run

Command 
```
cd code
python model.py {--[option1]=[value1] --[option2]=[value2] ... }
```

Change the corresponding options to set hyperparameters:
```
tf.app.flags.DEFINE_integer("symbols", 12210, "vocabulary size.")
tf.app.flags.DEFINE_integer("labels", 7, "Number of topic labels.")
tf.app.flags.DEFINE_integer("epoch_pre", 2, "Number of epoch on pretrain.")
tf.app.flags.DEFINE_integer("epoch_max", 15, "Maximum of epoch in iterative training.")
tf.app.flags.DEFINE_integer("embed_units", 100, "Size of word embedding.")
tf.app.flags.DEFINE_integer("hidden_units", 100, "Size of hidden layer.")
tf.app.flags.DEFINE_integer("sample_round", 4, "Sample round in RL.")
tf.app.flags.DEFINE_float("keyword", 3.0, "Coefficient of keyword reward.")
tf.app.flags.DEFINE_float("continuity", 1.0, "Coefficient of continuity reward.")
tf.app.flags.DEFINE_float("learning_rate_srn", 0.0001, "SRN Learning rate.")
tf.app.flags.DEFINE_float("learning_rate_pn", 0.00001, "PN Learning rate.")
tf.app.flags.DEFINE_float("keep_prob", 0.5, "Drop out rate.")
tf.app.flags.DEFINE_float("softmax_smooth", 0.5, "Discount rate in softmax.")
tf.app.flags.DEFINE_float("threshold", 0.005, "Threshold to judge the convergence.")

tf.app.flags.DEFINE_boolean("log_parameters", True, "Set to True to show the parameters.")
tf.app.flags.DEFINE_boolean("is_train", True, "Set to False to inference.")
tf.app.flags.DEFINE_string("data_dir", "./data", "Data directory.")
tf.app.flags.DEFINE_string("train_filename", "train", "Filename for training set.")
tf.app.flags.DEFINE_string("valid_filename", "valid", "Filename for validation set.")
tf.app.flags.DEFINE_string("test_filename", "test", "Filename for test set.")
tf.app.flags.DEFINE_string("word_vector_filename", "my_vector", "Filename for word embedding vector.")
tf.app.flags.DEFINE_string("train_dir_srn", "./train_srn", "SRN Training directory.")
tf.app.flags.DEFINE_string("train_dir_pn", "./train_pn", "PN Training directory.")
```

The ``states`` of SRN are saved at ``FLAGS.train_dir_srn + '/states_' + FLAGS.XXX_filename`` 

The ``labels`` of PN are saved at ``FLAGS.train_dir_pn + '/labels_' + FLAGS.XXX_filename`` 

### Requirements

tensorflow >= 1.0
