# Day 004 — Create a Standard ML Project Structure

---

## Problem

The `fraud-detection` project directory had no consistent structure. Without defined boundaries for data, source code, models, notebooks, configs, and tests, the codebase would become unmaintainable as the team grows. A standardized layout needed to be enforced from scratch.

---

## Solution

- Created the standard directory tree: `data/raw`, `data/processed`, `models`, `notebooks`, `src/` (with subpackages), `tests`, `configs`
- Added `__init__.py` to all `src/` subdirectories so Python treats them as importable packages
- Overwrote `requirements.txt` with correct PyPI package names (no `sklearn` typos)
- Initialized `README.md` with the correct project header

---

## Commands

```bash
cd /root/code/fraud-detection/

mkdir -p data/raw data/processed \
         models \
         notebooks \
         src/data src/features src/models src/utils \
         tests \
         configs

touch src/data/__init__.py \
      src/features/__init__.py \
      src/models/__init__.py \
      src/utils/__init__.py

cat <<EOF > requirements.txt
scikit-learn
pandas
numpy
mlflow
EOF

echo "# fraud-detection" > README.md
```

---

## Notes

`mkdir -p` is idempotent — safe to re-run without errors if directories already exist. The `src/` layout with `__init__.py` files follows the standard Python package convention, making modules importable as `from src.models import ...` rather than relying on fragile path hacks.
