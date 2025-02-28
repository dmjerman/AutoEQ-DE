# AutoEQ-DE
Auto Equalizer Differential Evolution—the evolutionary optimization algorithm used to find the best EQ filter parameters.
*This is a work in progress*
# AutoEQ-DE (Shelves+Peaks EQ)

AutoEQ-DE is a Python-based headphone equalization tool that uses Differential Evolution (DE) to optimize a set of parametric EQ filters. The application features a Tkinter GUI for easy configuration and outputs filter parameters in a format compatible with Equalizer APO/Peace.

## Features

- **User-Friendly GUI:** Browse and select measurement CSV files, adjust parameters, and run optimization.
- **CSV Data Handling:** Load headphone measurement data and optional hearing correction CSV files.
- **Target Curve Generation:** Merge measurement data with reference curves (e.g., Harman OverEar or Knowles Preferred) to create a target EQ curve.
- **Differential Evolution Optimization:** Optimize a configurable number of filters (shelves and peaks) using DE.
- **Loudness-Based Adjustments:** Dynamically adjust shelf gains based on a user-specified listening SPL.
- **Dynamic Q-Factor Penalties:** Apply frequency-dependent Q penalties to discourage overly narrow filters.
- **Advanced Penalty Rules:** Enforce minimum spacing between peak filters and constrain shelf frequencies.
- **Equalizer APO/Peace Output:** Generates an output file with a format like:

Preamp: 0.00 dB 
Filter 1: ON LS Fc 41.82 Hz Gain -6.67 dB Q 2.77 
Filter 2: ON HS Fc 11268.48 Hz Gain 2.18 dB Q 2.54 
Filter 3: ON PK Fc 7122.35 Hz Gain 4.08 dB Q 1.57 ...

- **Real-Time Visualization:** Optional real-time graphing of the EQ curve during optimization.

## Dependencies

- Python 3.x
- Tkinter (usually included with Python)
- NumPy
- SciPy
- Matplotlib
- Numba


Usage
Run the Application:
python main.py

Using the GUI:

Headphone CSV: Browse and select your headphone measurement CSV file.
Hearing CSV (optional): Browse and select a hearing correction CSV file.
Target Curve: Choose the reference curve (e.g., "Harman OverEar (Approx)" or "Knowles Preferred").
Filter Count: Set the number of filters (e.g., 16 or 30 filters).
Listening SPL: Set your desired listening level (in dB).
Other Options: Adjust the hearing factor and enable/disable psychoacoustic enhancements or real-time graphing.
Run Optimization: Click the "Run DE Optimization" button to start the process.

Importing into Equalizer APO:

The output file is formatted for direct import into Equalizer APO using the Peace GUI.

Configuration
The source code allows you to tweak various parameters:

Filter Bounds & Frequency Constraints:
Low-shelf frequency is constrained between 20 and 200 Hz.
High-shelf frequency is constrained between 6000 and 16000 Hz.
Differential Evolution Settings:
Maximum iterations (MAXITER), population size (POPSIZE), and CPU worker settings.
Penalty Constants:
Gain and Q penalties, extra Q penalties for values above 2.5, and spacing penalties for filters too close (less than 100 Hz apart).
Frequency Weighting:
The cost function can weight the midrange (e.g., 1–5 kHz) more heavily to emphasize perceptual importance.
Feel free to modify these settings in the code to better suit your measurement data and EQ goals.

Contributing
Contribution are welcome! If you want to contribute, please submit a pull request. For major changes, please discuss them via an issue first.
