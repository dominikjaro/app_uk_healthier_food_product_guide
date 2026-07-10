# UK Healthier Food Product Guide

A simple app that helps you decide: **is it worth buying this organic?**
 
Enter a product (e.g. "strawberries" or "milk") and get:
- Whether it's worth buying organic — and why
- Good UK brands or farms to look for
## Why this exists
 
Some fruits and veggies really benefit from going organic (thin skins, high pesticide
use), others don't make much difference. This app collects that info in one place,
along with trustworthy UK brands, so you don't have to Google it every time you're
in the supermarket.
 
## How it works
 
1. You search for a product
2. The app looks it up in a database of curated products
3. It returns a recommendation (organic: worth it / not worth it) with reasons, plus
   recommended UK brands
## Tech stack
 
- **Python** + **FastAPI** — the API that serves product lookups
- **PostgreSQL** — stores products, recommendations, reasons, and brands
- **SQLAlchemy** + **Alembic** — database access and schema migrations
- **Docker** — packages the app to run anywhere
- **GitLab CI** — tests, scans, and builds the app on every change
## Project structure
 
```
app/
├── main.py              # API routes
├── models.py            # Product, Brand, Recommendation data models
├── database.py          # DB connection setup
└── data/
    └── seed_products.py # initial curated product data
tests/
    └── test_basic.py
Dockerfile
requirements.txt
```
 
## Related repos
 
This app is one piece of a bigger setup:
 
| Repo | What's in it |
|---|---|
| `app_uk_healthier_food_product_guide` (this repo) | App code, Dockerfile, CI pipeline |
| `gitops` | Kubernetes manifests, deployment config (used by ArgoCD) |
| `platform_infrastructure` | AWS infrastructure via Terraform (VPC, EKS, RDS, etc.) |
 
## Running locally
 
```bash
# 1. Create a virtual environment
python -m venv venv
source venv/bin/activate
 
# 2. Install dependencies
pip install -r requirements.txt
 
# 3. Set up your environment variables
cp .env.example .env
 
# 4. Run the app
uvicorn app.main:app --reload
```
 
## Status
 
🚧 Work in progress — built as a learning project to practice Python, Docker,
Kubernetes, Terraform, and CI/CD end to end.
 
## Data sources
 
Organic recommendations and brand info are curated from public sources such as
the Soil Association and pesticide residue research. Sources are noted per
product where possible — this app shares general guidance, not medical advice.