# Tariff Shock Propagation Simulator

An interactive model that traces how US semiconductor tariff increases compound through four supply chain stages into higher per-merchant POS terminal deployment costs for Pakistani fintechs.

## What This Model Does

The simulator implements a four-stage cost propagation chain:

1. **Component Import** — Raw increase in semiconductor/PCB cost due to the tariff
2. **Terminal Assembly** — Assembled device cost after applying component increase plus Pakistan import duty
3. **Merchant Deployment** — Per-merchant cost including installation, training, and connectivity
4. **Customer Acquisition** — Net cost increase per merchant after fintech subsidy

Each stage applies a multiplier to the previous stage's output. The compounding effect is the core analytical insight.

## Formulas

```
deltaComponent  = B × C × T × (1 - L)
deltaTerminal   = deltaComponent × (1 + D_import)
deltaDeployment = deltaTerminal × (1 + D_deploy)
deltaCAC        = deltaDeployment × (1 - S)
```

At default values (25% tariff): a ~$28 component cost increase propagates to ~$21 in additional customer acquisition cost per merchant.

## Assumptions

Every parameter has a stated source and confidence level. Key defaults:

| Parameter            | Default | Source                       | Confidence |
| -------------------- | ------- | ---------------------------- | ---------- |
| US chip tariff       | 25%     | US ITC HTS Chapter 85        | High       |
| Component cost ratio | 47%     | Industry analyst consensus   | Medium     |
| Base terminal cost   | $250    | Verifone/Ingenico materials  | Medium     |
| Pakistan import duty | 15%     | FBR general electronics band | Low        |
| Local assembly %     | 5%      | Stated assumption            | Low        |

Full assumption log with all 8 parameters is available in the simulator's Assumptions Panel and in `assumption_log.md`.

## Limitations

This model captures first-order effects only. It does not model currency fluctuations, supply chain substitution, inventory buffers, or second-order market responses. It is pedagogical by design, not predictive.

## Running Locally

Open `index.html` in any modern browser. No build step required.

## Deploying to GitHub Pages

1. Push this folder to a GitHub repository
2. Go to Settings > Pages
3. Set source to the branch containing `index.html`
4. The simulator will be live at `https://<username>.github.io/<repo-name>/`

## Tech Stack

- React 18 (CDN)
- Recharts (CDN)
- Single self-contained HTML file — no build dependencies

## Market Context

Pakistan POS terminal count: 195,849 (SBP Payment Systems Review FY25).

## Author

Fawad Liaqat
