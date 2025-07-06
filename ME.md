- [x] from separated `.csv` files for linux24apt dataset to a clean `LINUX24.csv` file
- [x] apply **PARSING** to the `content` column to generate the `EventId` and `EventTemplate` columns in two file: `LINUX24.log_structured.csv` and `LINUX24.log_templates.csv`, do that for different values of `tau` _(0.3, 0.5, 0.7)_. run the command

```bash
python Spell.py
```

- [ ] generate templates vectors for my templates
