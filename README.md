# TheFrictionRealm Bot — Clean Kaggle Repository

This repository intentionally contains only three files:

- `main.py` — complete Telegram bot
- `requirements.txt` — Python dependencies
- `README.md` — minimal setup instructions

There are no Docker, systemd, shell (`.sh`), runtime, scripts, or documentation folders.

## Kaggle requirements

Use a Kaggle notebook with:

- Internet enabled
- GPU accelerator enabled
- Telegram/OpenAI values saved under **Add-ons → Secrets**

Required secrets:

- `API_ID`
- `API_HASH`
- `BOT_TOKEN`

Optional secrets:

- `OPENAI_API_KEY`
- `ALLOWED_USER_ID`
- `ADMIN_IDS`
- `CHANNEL_MAP`
- `LEECH_URL`

## Run

Use the supplied updated Kaggle notebook, or run these commands from a Python 3.10 environment:

```bash
python -m pip install paddlepaddle-gpu==2.6.1 -i https://mirror.baidu.com/pypi/simple
python -m pip install -r requirements.txt
python main.py
```

The updated notebook also installs `aria2`, reads Kaggle Secrets, and runs `main.py`.

## 2× T4 behavior

OCR worker processes and the three NVENC quality jobs are distributed across the detected GPUs. Bot commands, output qualities, OCR, translation, subtitle generation, muxing, uploading, cleaning, cancellation, and channel routing are unchanged.

Recommended Kaggle values:

```text
OCR_WORKERS=4
ENCODE_CONCURRENCY=2
OCR_SCAN_WIDTH=1280
```

These settings reduce T4 memory pressure without removing any output quality or bot feature.
