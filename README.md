# Crop Predictor and Demand Visualizer

A Tkinter desktop app for logging in, predicting a suitable crop from soil/budget inputs, viewing crop demand, and updating your current crop.

## Screenshots

![Login Page](screenshots/login_page.png)
![Home Page](screenshots/home_page.png)
![Crop Demand Chart](screenshots/demand_chart.png)

## Files Needed (same folder)

- `Crop_predictor_and_Demand_Visualizer.ipynb`
- `Data_users.xlsx`
- `Crop_Predict.csv` — **not included**; only needed for "Predict Crop Using Budget"

## Setup

```bash
conda create -n crop-app python=3.10 -y
conda activate crop-app
conda install pandas scikit-learn matplotlib openpyxl notebook -y

cd /path/to/project-folder
jupyter notebook
```

## Running

1. Open the notebook and run the cell (Shift+Enter).
2. A "Login Page" window pops up. Log in with e.g. `abc_1` / `abc_1` (see `Data_users.xlsx`), or register as a new user.
3. From the Home Page, pick a feature:
   - Predict Crop Using Budget (needs `Crop_Predict.csv`)
   - Predict Crop Based on Demand
   - Update Current Crop

If you close a window and want to run again, restart the kernel first (`Kernel > Restart`).
