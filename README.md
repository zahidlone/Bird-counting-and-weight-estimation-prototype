# Bird Counting and Weight Estimation (Prototype)

## Overview
This project implements a prototype system for:
1. Bird counting over time using detection + tracking
2. Bird weight estimation using a visual proxy index

Built as part of the Kuppismart Solutions (Livestockify) technical assessment.

## Setup
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Run API
```bash
uvicorn app.main:app --reload
```

## API Usage
```bash
curl -X POST http://127.0.0.1:8000/analyze_video   -F "video=@sample.mp4"
```

## Methodology
### Bird Counting
- Detector: YOLO-style pretrained detector (placeholder in this prototype)
- Tracking: ID assignment using IoU association
- Occlusions handled via short-term ID persistence

### Weight Estimation
- Proxy: Bounding box area averaged per bird
- To convert to grams: requires camera calibration and sample ground-truth weights

## Outputs
- Annotated video (bounding boxes, IDs, count overlay)
- JSON response with counts and weight index
