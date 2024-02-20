# Problem Statement: Predictive Maintenance for Manufacturing Equipment

## Background:

In a manufacturing setting, equipment breakdowns can lead to costly downtime and production losses. Predictive maintenance is crucial for optimizing operations by predicting when equipment is likely to fail so that maintenance can be performed just in time.

## Project Scope:

Developing a predictive maintenance model using machine learning to predict when a machine is likely to fail based on historical data.

---

## Dataset Information:

Since real predictive maintenance datasets are generally difficult to obtain and publish, a synthetic dataset reflecting real predictive maintenance encountered in the industry is provided.

### Variable Information:

The dataset consists of 10,000 data points stored as rows with 14 features in columns.

- **UID:** Unique identifier ranging from 1 to 10,000
- **Product ID:** Consists of a letter L, M, or H for low (50% of all products), medium (30%), and high (20%) as product quality variants and a variant-specific serial number
- **Air Temperature [K]:** Generated using a random walk process later normalized to a standard deviation of 2 K around 300 K
- **Process Temperature [K]:** Generated using a random walk process normalized to a standard deviation of 1 K, added to the air temperature plus 10 K.
- **Rotational Speed [rpm]:** Calculated from a power of 2860 W, overlaid with normally distributed noise
- **Torque [Nm]:** Torque values are normally distributed around 40 Nm with a σ = 10 Nm and no negative values.
- **Tool Wear [min]:** Quality variants H/M/L add 5/3/2 minutes of tool wear to the used tool in the process.
- **Machine Failure Label:** Indicates whether the machine has failed in this particular data point due to various failure modes.

### Machine Failure Modes:

1. **Tool Wear Failure (TWF):** Tool will be replaced or fail at a randomly selected tool wear time between 200 – 240 mins.
2. **Heat Dissipation Failure (HDF):** Caused by a process failure if the difference between air- and process temperature is below 8.6 K, and the tool’s rotational speed is below 1380 rpm.
3. **Power Failure (PWF):** Process fails if the power (torque * rotational speed) is below 3500 W or above 9000 W.
4. **Overstrain Failure (OSF):** Process fails if the product of tool wear and torque exceeds specific values for each product variant.
5. **Random Failures (RNF):** Each process has a 0.1% chance to fail regardless of its parameters.

If at least one of the above failure modes is true, the process fails, and the 'Machine Failure' label is set to 1. The specific failure mode causing the process to fail is not transparent to the machine learning method.