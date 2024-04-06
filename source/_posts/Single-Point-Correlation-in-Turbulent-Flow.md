---
title: Single-Point Correlation in Turbulent Flow
date: 2023-10-13 21:00:07
mathjax: true
categories: 
  turbulence
tags:
  turbulence
---

# Calculate Single-Point Correlation in Turbulent Flow

The single-point correlation is a measure of the self-similarity of a turbulent flow at a given point, and it can be used to understand the turbulent structures, such as eddies. In fluid mechanics, correlations provide statistical descriptions of turbulence.

### 1. Basic Concept

For a scalar field  $\phi(t, \mathbf{x})$, the auto-correlation  $R_{\phi\phi}$ at a point $\mathbf{x}$ is defined as:$R_{\phi\phi}(\tau, \mathbf{r}) = \langle \phi(t, \mathbf{x}) \phi(t + \tau, \mathbf{x} + \mathbf{r}) \rangle$
where $\langle \cdot \rangle$ denotes the ensemble average, $\tau$ is the time delay, and $\mathbf{r}$ is the spatial separation.

### 2. Procedure to Calculate Single-Point Correlation

1. **Data Collection**: Acquire a time series of the quantity of interest (e.g., velocity) at a particular spatial point in the flow. This could be done using a hot-wire anemometer, laser Doppler velocimetry, or any other appropriate measurement technique for turbulent flows.

2. **Time Averaging**: Remove any mean component by taking an average over the time series and then subtracting this average from the entire series.

3. **Computing the Correlation**: For each time delay $\tau$, multiply the value of the signal at time $t$ with that at $t + \tau$ and average this over all $t$. This gives you the correlation at delay $\tau$.

4. **Normalization**: Divide the correlation function by its value at $\tau = 0$ to obtain a normalized auto-correlation function that varies between 1 (at $\tau = 0$ ) and 0 (as  $\tau$  becomes very large).

### 3. Extracting Eddy Size

1. **Identify Zero Crossing**: The point where the auto-correlation drops to zero for the first time represents a characteristic time scale $\tau_0$ of the turbulent eddies. 

2. **Convert Time to Length Scale**: If you're analyzing a velocity signal, the characteristic length scale (or eddy size) $ L$ can be approximated using the Taylor's hypothesis: $L = U \tau_0$ 
   where $ U$ is the mean velocity of the flow.

### 4. Notes

- While single-point correlations give insights into the scale of the eddies, they don't provide full spatial information. For more spatially-resolved insights, two-point correlations or spatial spectra might be needed.
- In practical applications, turbulence is often non-stationary. This means that the statistical properties can vary over time, which can complicate the interpretation of single-point correlations.

This procedure provides a basic understanding of how one might compute single-point correlations in turbulent flows and then use them to deduce information about eddy sizes. Actual implementations might have additional nuances based on the specific details of the flow and the experimental setup.


## **How to get the signals at each time delay?**


When you have a time series of data points (for example, velocity measurements taken at regular time intervals), the "signal" at each time delay $\tau$ is obtained by pairing data points that are $ \tau$ apart in the time series. Here's how you would obtain these signals:

### Procedure:

1. **Choose the Time Delay $\tau$**: Start with $\tau = 0$, then $\tau = \Delta t$ (where $\Delta t$ is your sampling time interval), then $\tau = 2\Delta t$, and so on, up to a maximum value that makes sense for your analysis.

2. **Pairing Data Points**: For each $\tau$, pair each data point $\phi(t)$ with the data point $\phi(t+\tau)$.

   - For $\tau = 0$: Every data point is paired with itself.
   - For $\tau =\Delta t$: The first data point is paired with the second, the second with the third, and so on.
   - For $\tau = 2\Delta t$: The first data point is paired with the third, the second with the fourth, and so on.

3. **Compute the Product**: For each pair, compute the product $\phi(t) \times \phi(t+\tau)$.

4. **Average the Product**: Compute the average of these products over all data points to get the correlation for that $\tau$. This is essentially:
   $R(\tau) = \frac{1}{N-\tau/\Delta t} \sum_{t=1}^{N-\tau/\Delta t} \phi(t) \phi(t+\tau)$
   Where $N$ is the total number of data points in your time series.

5. **Repeat for All $\tau$**: Repeat the process for all desired values of $\tau$ to obtain the correlation function.

### Notes:

- The maximum $\tau$ you consider should be less than the total length of your time series. Typically, you'll choose a maximum $\tau$ that is less than this to ensure a sufficient number of pairs at each $\tau$ for a statistically significant average.

- As $\tau$ increases, the number of data pairs available decreases. This is because, for a given $\tau$, the last $\tau/\Delta t$ data points of the series don't have a partner $\tau$ apart. As a result, the statistical reliability of the correlation may decrease for large $\tau$.

- In practice, you would use software (e.g., MATLAB, Python's NumPy) to compute these correlations rather than doing it manually.

By following this procedure, you will have computed the auto-correlation of the time series at various time delays $\tau$, providing insights into the temporal structure of your turbulent signal.

***When the first data point is paired with the second , the second with the third, and so on, how to deal with the last data point and the first data point in another group since there is no additional data point to be paired with?***

Your understanding is correct. When you're pairing data points separated by a time delay $\tau$, as $\tau$ increases, there will be fewer pairs to consider because the end of the dataset is reached. Here's how you handle this:

### Handling the End of the Dataset:

1. **For $\tau = \Delta t$**:
   - The first data point pairs with the second, the second with the third, and so on.
   - The last data point (let's call it the $N^{th}$ data point) will **not** have a pair because there's no $N+1$ data point.

2. **For $\tau = 2\Delta t$**:
   - The first data point pairs with the third, the second with the fourth, and so on.
   - The $N-1$ data point will pair with the $N$ data point, but then both the $N-1$ and $N$ data points will not have pairs for subsequent larger time delays.

3. **General Rule**:
   - For any given $\tau$, the last $\tau/\Delta t$ data points will not have a partner $\tau$ apart. These points are not included in the computation for that $\tau$.

### Important Notes:

- As you increase $\tau$, the number of pairs available for computing the correlation decreases. This is why the statistical reliability of the correlation may reduce for large $\tau$.

- The above explanation assumes that you're not using a periodic boundary condition or any other method to artificially create pairs. For typical correlation computations of a time series in turbulence studies, you don't wrap around to the beginning of the dataset.

- The normalization or averaging process should account for the reduced number of pairs. When computing the average product for each $\tau$, you'll divide by the actual number of pairs for that $\tau$ rather than always dividing by $N$.

By taking care to properly pair data and ensuring that the normalization/averaging process accounts for the varying number of pairs at each $\tau$, you can correctly compute the auto-correlation of your dataset.

2023/10/13
