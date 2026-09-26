# Crop Predictor and Demand Visualizer

A desktop GUI application (built with Tkinter) that helps users log in, predict a suitable crop to grow based on soil/climate inputs and budget, visualize current crop demand among registered users, and update their currently grown crop.

## Features

- **Login / New User** — Authenticates against a local Excel file (`Data_users.xlsx`) containing user IDs, passwords, and each user's current crop. New users can register directly from the app.
- **Predict Crop Using Budget** — Takes soil nutrient values (N, P, K), temperature, humidity, pH, rainfall, soil type, season, and budget as input, and uses a Logistic Regression model (trained on `Crop_Predict.csv`) to recommend a suitable crop.
- **Predict Crop Based on Demand** — Reads all users' current crops from `Data_users.xlsx` and renders a bar chart showing how many users are growing each crop. The least-grown crop is flagged as having the highest demand.
- **Update Current Crop** — Lets a logged-in user view and update the crop they are currently growing, saving the change back into `Data_users.xlsx`.

## Screenshots

**Login Page**

![Login Page](screenshots/login_page.png)

**Home Page**

![Home Page](screenshots/home_page.png)

**Predict Crop Based on Demand**

![Crop Based on Demand](screenshots/demand_chart.png)

## Requirements

- Anaconda (Python 3.9–3.11 recommended)
- Packages: `pandas`, `scikit-learn`, `matplotlib`, `openpyxl`, `notebook`
- Tkinter (bundled with Anaconda's Python on Windows/Mac; on Linux you may need to install it separately)

## Files Needed in the Same Folder

| File | Required for | Included? |
|---|---|---|
| `Crop_predictor_and_Demand_Visualizer.ipynb` | The application itself | Yes |
| `Data_users.xlsx` | Login, demand chart, crop update | Yes |
| `Crop_Predict.csv` | "Predict Crop Using Budget" feature | **No — must be supplied separately** |

> **Note:** `Crop_Predict.csv` is not included in this repo/upload. Without it, every feature works *except* "Predict Crop Using Budget," which will raise a `FileNotFoundError` when clicked. The CSV needs columns for `Soil_type`, `Season`, nitrogen, phosphorous, potassium, temperature, humidity, pH, rainfall, budget, and a crop label as the final column.

## Setup

```bash
# 1. Create and activate a dedicated environment
conda create -n crop-app python=3.10 -y
conda activate crop-app

# 2. Install required packages
conda install pandas scikit-learn matplotlib openpyxl notebook -y

# Linux only, if tkinter isn't already present:
# sudo apt-get install python3-tk

# 3. Navigate to the project folder (must contain the .ipynb and .xlsx together)
cd /path/to/Crop_Predictor_And_Demand_Visualizer-main

# 4. Launch Jupyter
jupyter notebook
```

## Running the App

1. Open `Crop_predictor_and_Demand_Visualizer.ipynb` in the Jupyter tab that opens in your browser.
2. Run the first cell with **Shift+Enter**.
3. A separate desktop window titled **"Login Page"** will pop up (Tkinter runs outside the browser).
4. Log in with any existing user from `Data_users.xlsx`, for example:
   - **ID:** `abc_1` / **Password:** `abc_1`
   - **ID:** `abc_2` / **Password:** `abc_2`

   Or click **"New User? Click here"** to register a new account.
5. From the Home Page, choose:
   - **Predict Crop Using Budget** (requires `Crop_Predict.csv`)
   - **Predict Crop based on Demand**
   - **Update Current Crop**

## Restarting

Because Tkinter's `mainloop()` blocks the Jupyter kernel while windows are open, if you close the app windows and want to run it again:

`Kernel` menu → `Restart Kernel` → re-run the cell (Shift+Enter).

Otherwise you may see a `TclError: application has been destroyed` on the next run.

## Known Limitations

- `Crop_Predict.csv` is not bundled with this project; the budget-based predictor won't work until it is added.
- The app trains a fresh Logistic Regression model on every click of "Predict Crop Using Budget" rather than loading a saved model, so predictions may vary slightly run to run.
- Passwords are stored in plain text in `Data_users.xlsx` — this project is intended for demo/educational use, not production or sensitive data.
- The app opens native desktop windows and therefore only runs on a local machine with a display (not in a cloud-hosted or headless Jupyter environment).
