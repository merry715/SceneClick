# SceneClick

SceneClick is a data-driven YouTube travel thumbnail optimization service.

Instead of generating "aesthetic" thumbnails,
SceneClick improves existing thumbnails based on regression-based visual insights.

## Key Idea
- Diagnose visual problems in thumbnails using regression analysis
- Convert insights into prompt & image processing rules
- Validate improvement via probabilistic click simulation

## Regression-based Design Insight

An OLS regression analysis was conducted on 30 travel vlog thumbnails to identify
visual factors correlated with view efficiency.

Two variables were consistently selected:

- Overall contrast (0–255)
- Face-to-background area ratio (%)

Both variables showed negative coefficients, indicating that:
higher contrast and excessive face dominance tend to reduce view efficiency.

This model is not treated as a strict predictor,
but as a directional design guideline for thumbnail generation.

## Data Check
Since the original data file is too large, we uploaded it to Google Drive.
You can check the raw data structure and link columns here:
👉 [Download Raw Data](https://docs.google.com/spreadsheets/d/1-nGcg-ThwzFdLxYJCNN16Um5EEa7e4D2/edit?usp=sharing&ouid=100352026300952530110&rtpof=true&sd=true)
