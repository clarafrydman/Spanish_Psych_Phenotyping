# Extraction of Psychiatric Phenotypes from Clinical Notes in Spanish: A Comprehensive, Cross-hospital Study
cNLP tool for pattern-based named entity recognition

# Install
``` 
conda create --name nlp_pheno_es -c conda-forge python=3.11 spacy=3.5 pandas -y
conda activate nlp_pheno_es

pip install --no-cache-dir medspacy
python -m spacy download es_core_news_md
``` 

## Uninstall
``` 
conda activate nlp_pheno_es

pip install pip-autoremove
pip-autoremove medspacy
pip uninstall es_core_news_md -y

conda deactivate
conda remove --name nlp_tool_bare --all
``` 

# Usage

### Load
Load all concepts by default
```
from escribe.default_nlp import nlp, select_concepts
nlp = select_concepts(nlp)
```
To load specific concepts:
```
nlp = select_concepts(nlp, concepts = ['Usodesustancias','Retrasopsicomotor'])
```
To load concepts from a specific source:
```
nlp = select_concepts(nlp, json_dir = 'escribe/patterns/Concepts/SOURCE')
```

### Extract concepts from text
Using the NLP object
```
doc = nlp('el padre biologico nunca sufrió de paranoia')
doc.ents                           # (paranoia,)
doc.ents[0].label_                 # 'Paranoia'
doc.ents[0]._.is_family            # True
doc.ents[0]._.is_historical        # False
doc.ents[0]._.is_hypothetical      # False
doc.ents[0]._.is_negated           # True
doc.ents[0]._.is_uncertain         # False
```

# Please Cite:
medRxiv: ...
