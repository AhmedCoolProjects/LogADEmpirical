## 1. Download the dataset used by LogADEmpirical

Run the following commands:

```bash
cd /srv/lustre01/project/nlp_team-um6p-st-sccs-id7fz1zvotk/IDS/ahmed.bargady/data/github/my-logadempirical/dataset && wget -O dataset.zip "https://zenodo.org/api/records/8115559/files-archive"
```

```bash
mkdir -p preprocessed && unzip preprocessed.zip -d preprocessed
```

```bash
mkdir -p raw && unzip raw.zip -d raw
```

```bash
rm -rf preprocessed.zip raw.zip dataset.zip
```

### RESULTS

We have downloaded the datasets used by LogADEmpirical, which include:

- `raw`: Contains the raw log files.
- `preprocessed`: Contains the preprocessed log files ready for training.

### Analysis

#### BGL

inside the `preprocessed` directory, we have a folder named `BGL` which contains the following files:

- **📁 BGL/**
  - `BGL_embeddings.h5`
  - `BGL.log_structured.csv`
  - `BGL.log_templates.csv`
  - `embeddings_average.json`
  - `embeddings.json`
  - `embeddings_tfidf.json`

The `BGL.log_templates.csv` which contains the unique templates extracted from the BGL logs.

The `BGL.log_structured.csv` contains the structured logs with their corresponding templates.

The `embeddings_tfidf.json` is generated from the `dataset/generate_embeddings.py` script, which uses the fastText model to generate embeddings for the log templates using the TF-IDF strategy. _(TF-IDF is a statistical measure that evaluates the importance of a word in a document relative to a collection of documents.)_

here are the following columns in both `BGL.log_structured.csv` and `BGL.log_templates.csv`, _(check that in the dataset_analysis.ipynb notebook)_

## 2. Prepare the Linux-24 APT dataset for my models training

### Parsing the Linux-24 APT dataset

```bash

```

## 3. Parse both datasets using the parsers available (Spell, and another one from LogADEmpirical)

## 4. Generate the required data format for all the datasets

## 5. Start training the following models

### BGL

```bash
python main_run.py --data_dir ./dataset/preprocessed/BGL --output_dir ./output/ --model_name DeepLog --dataset_name BGL --grouping session --window_size 10 --step_size 1 --train_size 0.01 --is_chronological --session_level entry --log_file BGL.log --batch_size 2048 --lr 0.001 --accumulation_step 1 --optimizer adamw --sequential --history_size 10 --embeddings embeddings_average.json --hidden_size 128 --num_layers 2 --embedding_dim 300 --topk 10 --dropout 0.1 --max_epoch 10
```

### LINUX24

```bash
python main_run.py --data_dir ./dataset/preprocessed/LINUX24 --output_dir ./output/ --model_name DeepLog --dataset_name LINUX24 --grouping sliding --window_size 10 --step_size 1 --train_size 0.01 --is_chronological --session_level entry --log_file LINUX24.log --batch_size 2048 --lr 0.001 --accumulation_step 1 --optimizer adamw --sequential --history_size 10 --embeddings 03.log_embeddings_tfidf.json --hidden_size 128 --num_layers 2 --embedding_dim 300 --topk 10 --dropout 0.1 --max_epoch 10
```

```bash
python main_run.py --data_dir ./dataset/preprocessed/LINUX24 --output_dir ./output/ --model_name DeepLog --dataset_name LINUX24 --grouping session --window_size 10 --step_size 1 --train_size 0.01 --is_chronological --session_level entry --log_file LINUX24.log --batch_size 2048 --lr 0.001 --accumulation_step 1 --optimizer adamw --sequential --history_size 10 --embeddings 03.log_embeddings_tfidf.json --hidden_size 128 --num_layers 2 --embedding_dim 300 --topk 10 --dropout 0.1 --max_epoch 10
```
