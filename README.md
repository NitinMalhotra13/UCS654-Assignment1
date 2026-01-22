# Title: Learn Probability Density Functions using Roll-Number-Parameterized Non-Linear Model

# Assignment Overview
This assignment is based on learning a probability density function (PDF) after applying a roll-number-based non-linear transformation on air quality data. The NO2 values are used as the input feature x. After transformation, a new variable z is generated and its probability density function is learned by estimating the required parameters.

# Dataset
The dataset used is the India Air Quality dataset from Kaggle.
Only the no2 column is considered as the feature x.

# Objective
The main objectives of this assignment are:
Transform NO2 values (x) into a new variable (z) using the given transformation equation
Learn the parameters λ (lambda), μ (mu), and c for the given PDF model of z
Report the final values of λ, μ, and c for submission

# Methodology
The steps followed in this assignment are:
1. Load the dataset and extract only the NO2 column
2. Convert NO2 values to numeric format and remove missing/invalid entries
3. Compute roll-number-based constants ar and br using the given formulas
4. Apply the non-linear transformation to generate z from x
5. Estimate the empirical probability density of z using a normalized histogram
6. Fit the given PDF model to the empirical histogram using curve fitting to estimate parameters
7. Normalize the constant c to ensure the learned PDF is mathematically valid (area under curve equals 1)
8. Plot the histogram of z and the learned PDF curve for visualization
9. Evaluate the fitting quality using Mean Squared Error (MSE) and KL Divergence

# Transformation Used
The transformation applied on NO2 values is based on the roll number:
z = x + ar × sin(br × x)
Where:
ar = 0.05 × (r mod 7), 
br = 0.3 × ((r mod 5) + 1), 
r is the university roll number

# PDF Model Learned
The probability density function used for learning is:
p(z) = c × exp( -λ (z − μ)² )
Where:
μ represents the center of the distribution, 
λ controls the spread of the distribution, 
c is the scaling constant

# Parameter Estimation
The parameters λ and μ are learned by fitting the PDF model to the empirical distribution of z obtained from the histogram.
The constant c is normalized after fitting to ensure the PDF integrates to 1 and remains a valid probability density function.

# Result Output
The notebook prints the final learned values of:
λ (lambda) = 0.0021053385101303707, 
μ (mu) = 19.798425613563772, 
c (normalized) = 0.025887256740295014. 
These are the values required to be submitted.

# Graph Output
A graph is generated showing:
The empirical PDF of z using a histogram
The learned PDF curve plotted on top of the histogram
<img width="780" height="467" alt="image" src="https://github.com/user-attachments/assets/e0d8e08b-6594-42b9-8d5b-d900de7080b0" />

This helps visually confirm the quality of the fitted PDF.

# Evaluation Metrics
The quality of the fit is evaluated using:
Mean Squared Error (MSE) between histogram density values and predicted PDF values
MSE (normalized fit): 1.0766215281417951e-07
KL Divergence between the empirical distribution and the learned PDF
KL Divergence (normalized fit): 0.19871606026540986
Lower values indicate a better fit
