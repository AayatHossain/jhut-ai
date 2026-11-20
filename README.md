# Jhut AI

Camera + AI that sorts garment cutting waste (jhut) by fabric and colour, so the same waste sells for more and is recycled locally in Bangladesh.

**Live prototype:** https://aayathossain.github.io/jhut-ai/

The prototype shows the full workflow: scan station, batch ledger, batch passport and a daily Bangla report.

- Colour and grade come from real pixel analysis that runs in the page.
- Fabric type uses preset demo predictions for the sample scraps and a simple texture rule for uploaded photos. The planned model is EfficientNet fine-tuned on the Kaggle "Mobile-Captured Fabric Dataset".
- Weights come from a simulated scale, and prices are illustrative.

By Phantom Troupe.
