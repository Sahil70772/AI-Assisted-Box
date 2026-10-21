# AI-Assisted Box Selection System (Django)

Recommends the cheapest shipping box that can physically hold an order.

## How it works
1. **Weight** – total order weight must be <= box max weight.
2. **Volume** – total item volume must be <= box volume (fast reject).
3. **Geometry** – an extreme-point packer tries to place every unit in the box, trying all 6 rotations of each item. Only a *found* packing counts as a fit.
4. Among boxes that pass, pick the **lowest cost** (tie: smaller volume).

Code layout: `packing/services/packer.py` (pure Python algorithm), `selection.py` (model glue), `views.py` (JSON API), `tests.py`.

## Setup
```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py seed_demo          # optional demo data
python manage.py createsuperuser    # optional, for /admin/
python manage.py runserver
```

## API
- `GET /api/orders/<reference>/recommend-box/` – e.g. `/api/orders/ORD-1001/recommend-box/`
- `POST /api/recommend-box/` with `{"items": [{"sku": "PHONE", "quantity": 2}]}`

Response: `recommended_box` (or `null`), `total_weight_kg`, `total_volume_cm3`, `message`, `rejected_boxes` (with reasons).

Manage Products, Boxes and Orders in `/admin/`. Units: cm, kg; box dimensions are **internal** dimensions.

## Tests
`python manage.py test -v 2` (17 tests; output in `TEST_OUTPUT.md`, CI in `.github/workflows/tests.yml`).

## Assumptions
- One order goes in one box (no multi-box splitting).
- Items are rigid cuboids, any of 6 axis-aligned rotations allowed, no padding/void-fill.
- Any item can be stacked on any other (no "fragile"/"this side up").

## Limitations
- The packer is a heuristic: it never recommends a box that doesn't fit, but may occasionally reject one a smarter algorithm could use (finding the optimal 3D packing is NP-hard).
- No multi-box splitting when nothing fits (returns `null` with reasons).
- No authentication on the API (demo scope).

## Possible improvements
Multi-box splitting, packing padding, fragile/orientation flags, DRF + auth, caching, performance tests with large orders.

## Submission checklist
See `SUBMISSION_CHECKLIST.md`.
