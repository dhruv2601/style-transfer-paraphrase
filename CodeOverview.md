## A basic overview of the structure of the code - 

*
    Directory 1 - 
    📦data_samples
    ┣ 🏁 This directory contains a short 1000 word-text sample for each of the 11 datasets used in the paper.
    ┣ 📜README.md
    ┣ 📜aae.txt
    ┣ 📜bible.txt
    ┣ 📜coha_1810-1830.txt
    ┣ 📜coha_1890-1910.txt
    ┣ 📜coha_1990-2000.txt
    ┣ 📜english_tweets.txt
    ┣ 📜joyce.txt
    ┣ 📜lyrics.txt
    ┣ 📜romantic_poetry.txt
    ┣ 📜shakespeare.txt
    ┗ 📜switchboard.txt

*   
    Directory 2 -
    📦datasets
    ┣ 🏁 Directory with scripts to play around with the datasets
    ┣ 🙇🏻‍♂️ (Links) - 
        ┣ https://en.wikipedia.org/wiki/Byte_pair_encoding
        ┣ https://ai.facebook.com/blog/roberta-an-optimized-method-for-pretraining-self-supervised-nlp-systems/
    ┣ 📜.gitignore
    ┣ 📜bpe2binary.sh - Pre-processing configs for FairSeq(SMT) models | BPE to Binary - setting paths for train/valid/dev tests and dictionary
    ┣ 📜bpe2text.py - Decoding the byte-pair encoded data to normal text data.
    ┣ 📜dataset2bpe.py - Converting dataset to BPE
    ┣ 📜paraphrase_splits.py - Split the datasets into train, dev, test. Create minibatches for all and store as BPE.
    ┣ 📜parse_paranmt_postprocess.py - A part of it cleans the data by removing non-English labels in the paraphrase data. Not 100% sure about the rest yet.
    ┗ 📜preprocess_utils.py - General Utils class. 

* 
    Directory 3 - 
    📦fairseq
    ┣ 🏁 Clone of the FairSeq repo by Facebook which literally contains every SOTA implementation regarding Seq2Seq from basic NERs to the best transformer models out there. The saviour from the satan called Transformer(and it's training) 🤩
    ┣ 🙇🏻‍♂️ 
       ┣ https://github.com/pytorch/fairseq - Pytorch
       ┣ https://ai.facebook.com/tools/fairseq/
       ┣ https://cloud.google.com/tpu/docs/tutorials/transformer-pytorch - Something we might find ourselves using in Phase2.

* 
    Directory 4 - 
    📦outputs
    ┣ Essentially an output sample of the results for each of the 11 datasets. The HTML formats are intersting, run it once and there are some good examples in here! I think there are more classes in here than the paper mentions(will need to confirm), like the lyrics style transfer.

* 
    Directory 5 - The ultimate directory, brace yourself 🏎
    📦style_paraphrase
    ┣ 📂evaluation
    ┃ ┣ 📂human
    ┃ ┃ ┣ 📜crowdsourcing.png
    ┃ ┃ ┣ 📜crowdsourcing2.png
    ┃ ┃ ┣ 📜crowdsourcing3.png
    ┃ ┃ ┣ 📜crowdsourcing4.png
    ┃ ┃ ┗ 📜paraphrase_amt_template.html - File to work on manual annotation, not sure we will be doing it, but if we are than this is amazing.
    ┃ ┣ 📂scripts
    ┃ ┃ ┣ 📜acceptability.py - This is CoLa benchmark implemented with Roberta. Res: https://nyu-mll.github.io/CoLA/
    ┃ ┃ ┣ 📜evaluate_formality.sh - Script to evaulate formality: Convert formal to informal and vice-versa and evaluate over all 5 metrics.
    ┃ ┃ ┣ 📜evaluate_shakespeare.sh - Same as above for shakespeare.
    ┃ ┃ ┣ 📜flip_labels.py
    ┃ ┃ ┣ 📜get_paraphrase_similarity.py - A helper file to get sentence similarity (as we will discuss in the next sub-dir)
    ┃ ┃ ┣ 📜micro_eval.py - Here a final metric is defined which is a formula combining all the 5 metrics.
    ┃ ┃ ┣ 📜roberta_classify.py - 
    ┃ ┃ ┣ 📜style_transfer.py
    ┃ ┃ ┗ 📜utils.py
    ┃ ┣ 📂similarity
    ┃ ┃ ┣ 📜__init__.py
    ┃ ┃ ┣ 📜sim_models.py
    ┃ ┃ ┣ 📜sim_utils.py
    ┃ ┃ ┣ 📜spm.py
    ┃ ┃ ┗ 📜test_sim.py
    ┃ ┣ 📜.gitignore
    ┃ ┗ 📜README.md
    ┣ 📂examples
    ┃ ┣ 📂formality
    ┃ ┃ ┣ 📜run_finetune_formality_0.sh
    ┃ ┃ ┗ 📜run_finetune_formality_1.sh
    ┃ ┣ 📂shakespeare
    ┃ ┃ ┣ 📜run_finetune_shakespeare_0.sh
    ┃ ┃ ┗ 📜run_finetune_shakespeare_1.sh
    ┃ ┣ 📜run_evaluate_paraphrase.sh
    ┃ ┣ 📜run_finetune_inverse_paraphrase.sh
    ┃ ┗ 📜run_finetune_paraphrase.sh
    ┣ 📂logs
    ┃ ┗ 📜.gitkeep
    ┣ 📂runs
    ┃ ┗ 📜.gitkeep
    ┣ 📂saved_models
    ┃ ┗ 📜.gitkeep
    ┣ 📂slurm-schedulers
    ┃ ┗ 📜.gitkeep
    ┣ 📂style_classify
    ┃ ┣ 📂examples
    ┃ ┃ ┣ 📜train_cds.sh
    ┃ ┃ ┣ 📜train_cola.sh
    ┃ ┃ ┣ 📜train_formality.sh
    ┃ ┃ ┗ 📜train_shakespeare.sh
    ┃ ┣ 📂webapp
    ┃ ┃ ┣ 📂static
    ┃ ┃ ┃ ┗ 📜.gitkeep
    ┃ ┃ ┣ 📂templates
    ┃ ┃ ┃ ┣ 📜results.html
    ┃ ┃ ┃ ┗ 📜visual.html
    ┃ ┃ ┣ 📜app.py
    ┃ ┃ ┗ 📜run.sh
    ┃ ┣ 📜.gitignore
    ┃ ┣ 📜author_classify_template.sh
    ┃ ┗ 📜schedule.py
    ┣ 📜.DS_Store
    ┣ 📜.gitignore
    ┣ 📜__init__.py
    ┣ 📜args.py
    ┣ 📜data_utils.py
    ┣ 📜dataset_config.py
    ┣ 📜hyperparameters_config.py
    ┣ 📜inference_utils.py
    ┣ 📜run_evaluate_gpt2_template.sh
    ┣ 📜run_finetune_gpt2_template.sh
    ┣ 📜run_generation.py
    ┣ 📜run_generation_gpt2_template.sh
    ┣ 📜run_lm_finetuning.py
    ┣ 📜schedule.py
    ┣ 📜style_dataset.py
    ┗ 📜utils.py 

