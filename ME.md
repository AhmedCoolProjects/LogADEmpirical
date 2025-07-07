- [x] from separated `.csv` files for linux24apt dataset to a clean `LINUX24.csv` file
- [x] apply **PARSING** to the `content` column to generate the `EventId` and `EventTemplate` columns in two file: `LINUX24.log_structured.csv` and `LINUX24.log_templates.csv`, do that for different values of `tau` _(0.3, 0.5, 0.7)_. run the command

```bash
python Spell.py
```

---

I had to include all the columns from LINUX24.csv in the log file, then let's start with the 0.5 tau value, and keep it in the default folder.

---

- [ ] generate templates vectors for my templates

```bash
python main_run.py --folder=LINUX24/ --log_file=LINUX24.log --dataset_name=LINUX24 --model_name=deeplog --window_type=sliding --sample=sliding_window --is_logkey --train_size=0.8 --train_ratio=1 --valid_ratio=0.1 --test_ratio=1 --max_epoch=100 --n_warm_up_epoch=0 --n_epochs_stop=10 --batch_size=1024 --num_candidates=150 --history_size=10 --lr=0.001 --accumulation_step=5 --session_level=hour --window_size=60 --step_size=60 --output_dir=experimental_results/demo/random/ --is_process --semantics=False
```
