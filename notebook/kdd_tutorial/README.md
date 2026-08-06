# AssetOpsBench KDD tutorial notebooks

Run these notebooks in order from the **AssetOpsBench repository root**:

1. `00_environment_setup.ipynb` — beginner setup, Docker/CouchDB, kernel selection, and readiness checks
2. `00_mcp_agents_architecture.ipynb` — MCP, agents, AssetOpsBench architecture, and direct tool concepts
3. `01_mcp_utilities.ipynb`
4. `02_mcp_iot.ipynb`
5. `03_mcp_fmsr.ipynb`
6. `04_mcp_workorders.ipynb`
7. `05_mcp_tsfm.ipynb`
8. `06_mcp_vibration.ipynb`
9. `07_end_to_end_stirrup.ipynb`
10. `08_evaluation.ipynb`
11. `09_leaderboard.ipynb`

## Before the tutorial

```bash
uv sync
docker compose -f src/couchdb/docker-compose.yaml up -d
uv run jupyter lab
```

Copy `.env.public` to `.env` and configure the model providers used for the Stirrup execution and judge. The server notebooks deliberately start with cheap/static calls; the IoT and work-order notebooks check CouchDB before querying it. TSFM inference is opt-in so a cold model download cannot derail the live session.

Generated outputs live in `artifacts/kdd_tutorial/`. Keep execution and judging models different. Keep Stirrup's `tools-only` and `code` results on separate leaderboard tracks.

To regenerate the notebooks after editing their source:

```bash
uv run python notebook/kdd_tutorial/generate_notebooks.py
```
