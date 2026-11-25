# StockCairn — proposed AWS architecture

StockCairn uses AWS to forecast demand across every location, predict ageing stock and serve allocation recommendations to merchandising teams.

## Request flow

1. POS & ERP data
2. Amazon S3
3. AWS Lambda
4. SageMaker AI
5. DynamoDB
6. Bedrock rationale
7. Merchandiser approval

## Services

### Amazon SageMaker AI

**Role:** Forecast demand and ageing

Trains SKU-by-location models on sales, seasonality and promotions to forecast demand and predict which stock will age, with confidence ranges.

### Amazon S3

**Role:** Store inventory and sales history

Keeps POS, ERP and warehouse exports encrypted and partitioned by location and date as the forecasting history.

### Amazon DynamoDB

**Role:** Serve stock positions and recommendations

Holds current stock by location, forecasts, recommendations and approvals for fast dashboard access.

### AWS Lambda

**Role:** Reconcile and recommend

Reconciles SKUs across systems, calculates transfer opportunities and refreshes recommendations as new data arrives.

### Amazon Bedrock

**Role:** Explain recommendations

Drafts a short, plain-language rationale for each transfer and buying suggestion, so merchandisers can review quickly.

## Principles

- **Merchandisers decide** — Every move is approved by a person.
- **Explained suggestions** — Each recommendation shows why.
- **Commercial privacy** — Sales and margins stay with your business.

## Safeguards

- **Human approval** — Transfers, markdowns and buying changes are approved by merchandisers.
- **Transparent forecasts** — Every recommendation shows forecast demand, stock and confidence.
- **No automatic pricing** — StockCairn flags markdown candidates; pricing decisions stay with your team.
- **Data separation** — Each business’s data is encrypted and isolated.

## MVP scope

We import a year of inventory and sales data for your locations, forecast demand and ageing, and deliver weekly allocation recommendations your merchandisers review.

- Inventory and sales import
- Demand and ageing forecasts
- Transfer recommendations
- Product analytics dashboard
- Weekly allocation report
