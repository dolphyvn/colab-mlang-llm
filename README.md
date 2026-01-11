# MLang V6.1 Google Colab Training

This folder contains training scripts for Google Colab.

## Files

- `MLang_V6.1_Training.ipynb` - Full training notebook with UI

## Usage

### 1. Generate Training Data Locally

```bash
# Encode data
python encode_mlang_v6_full.py \
    --input-dir ./data \
    --output-txt mlang_v6/train.txt \
    --output-meta mlang_v6/meta.json \
    --seq-len 12 \
    --lookahead 4 \
    --feature-level top1

# Convert to ChatML
python convert_mlang_v6_to_chatml.py mlang_v6/train.txt mlang_v6/train.jsonl
python convert_mlang_v6_to_chatml.py mlang_v6/val.txt mlang_v6/val.jsonl
```

### 2. Open in Google Colab

1. Open `MLang_V6.1_Training.ipynb` in Google Colab
2. Upload `train.jsonl` and `val.jsonl` using the file browser
3. Run all cells

### 3. Download Model

After training, download `mlang_v6_model.zip` from the file browser.

## Configuration

Edit these in the notebook:

```python
BASE_MODEL = "meta-llama/Llama-3.2-3B-Instruct"  # or "google/gemma-3-270m-it"
NUM_EPOCHS = 3
BATCH_SIZE = 1
GRADIENT_ACCUMULATION_STEPS = 8
LEARNING_RATE = 1e-4
MAX_SEQ_LENGTH = 2048  # Reduce if OOM
```

## Free Tier Tips

- Use `google/gemma-3-270m-it` for faster training
- Set `MAX_SEQ_LENGTH = 1024` if OOM
- Reduce `NUM_EPOCHS = 2` for faster runs
