# Enhanced Sparse GPR with Spectral Mixture Kernel

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)

An advanced implementation of Gaussian Process Regression (GPR) for remaining useful life (RUL) prediction with uncertainty quantification, featuring both standard and sparse variants with spectral mixture kernels.

## 🔍 Overview

This repository contains an enhanced implementation of Gaussian Process Regression models specifically designed for time series prediction with a focus on remaining useful life (RUL) estimation. It includes:

1. Standard GPR with Spectral Mixture Kernel
2. Sparse GPR variant using inducing points for computational efficiency
3. Comprehensive uncertainty quantification and analysis tools
4. Advanced calibration and reliability assessment

The implementation features numerical stability improvements, memory optimizations, and robust hyperparameter tuning strategies.

## ✨ Key Features

- **Spectral Mixture Kernel**: Custom implementation optimized for capturing complex patterns in degradation data
- **Sparse GPR with Inducing Points**: Scalable approximation for large datasets using the Fully Independent Training Conditional (FITC) method
- **Robust Hyperparameter Optimization**: Multi-stage Bayesian optimization with fallback mechanisms
- **Uncertainty Calibration**: Multiple methods including quantile regression, jackknife+ conformal prediction, and local conformal quantiles
- **Comprehensive Visualization**: Calibration curves, reliability diagrams, and detailed plots for performance analysis
- **Memory Optimization**: Single precision (float32) throughout and explicit garbage collection
- **Ablation Analysis**: Component-wise assessment of model pipeline contributions
- **Detailed Performance Tracking**: Memory usage and computation time analysis for each model component

## 📊 Implemented Analyses

- RUL prediction with confidence bounds
- Calibration curve generation and analysis
- Reliability assessment via PIT (Probability Integral Transform) histograms
- Inducing points impact on model performance and efficiency
- Ablation studies of different pipeline components
- Memory usage and computational efficiency tracking
- Consolidated results and comparisons

## 📈 Visualization Examples

The package generates:

- True RUL vs Predicted plots (with and without confidence bounds)
- Calibration curves with miscalibration analysis
- Reliability diagrams with statistical tests
- Detailed heatmaps of ablation analysis results
- Stagewise timing and memory usage visualizations

## 🛠️ Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/enhanced-sparse-gpr.git
cd enhanced-sparse-gpr

# Install dependencies
pip install -r requirements.txt
```

### Dependencies

- numpy
- pandas
- matplotlib
- scikit-learn
- scipy
- scikit-optimize (skopt)
- psutil (for memory tracking)

## 💻 Usage

```python
from run_enhanced_analysis import run_enhanced_analysis

# Run complete analysis pipeline
run_enhanced_analysis("path/to/your/data.xlsx", "path/to/output/directory")
```

### Interactive Mode

You can also run the script directly:

```bash
python run_enhanced_analysis.py
```

This will prompt you to select your data file and output directory through a file dialog.

## 📁 Data Format

The expected input is an Excel file with the following format:
- First column: Time in hours
- Subsequent columns: Degradation values for each unit/capacitor

## 📝 Code Structure

- `SpectralMixtureKernel`: Implementation of the kernel for capturing complex patterns
- `SparseGPR`: Sparse GPR implementation with inducing points for computational efficiency
- `robust_sgpr_hyperparameter_optimization`: Multi-stage hyperparameter optimization with fallback
- Uncertainty calibration functions including:
  - `apply_quantile_bias_correction`
  - `jackknife_plus_conformal`
  - `local_conformal_quantiles`
- Extensive visualization functions for results analysis

## 🧪 Advanced Usage

### Custom Kernel Parameters

```python
from spectral_mixture_kernel import SpectralMixtureKernel

# Create a kernel with custom parameters
custom_kernel = SpectralMixtureKernel(
    Q=2,
    w0=0.7, w1=0.3,
    mu0_0=0.1, mu0_1=0.2,
    mu1_0=-0.1, mu1_1=-0.2,
    v0_0=2.0, v0_1=1.5,
    v1_0=0.5, v1_1=0.8
)
```

### Training Sparse GPR

```python
from sparse_gpr import SparseGPR
from spectral_mixture_kernel import SpectralMixtureKernel

# Create kernel and model
kernel = SpectralMixtureKernel(Q=2)
sgpr = SparseGPR(
    kernel=kernel,
    n_inducing=50,
    alpha=1e-5,
    normalize_y=True,
    random_state=42
)

# Train model
sgpr.fit(X_train, y_train)

# Make predictions with uncertainty
mean, std = sgpr.predict(X_test, return_std=True)
```

## 📊 Results

The analysis pipeline generates a comprehensive set of outputs in the specified directory:

- **RUL Predictions**: True vs predicted RUL plots with confidence bounds
- **Calibration Curves**: Assessment of uncertainty calibration quality
- **Reliability Diagrams**: Analysis of prediction distribution reliability
- **Ablation Analysis**: Component-wise contribution assessment
- **Inducing Points Analysis**: Performance across different numbers of inducing points
- **Hyperparameter Logs**: Detailed logs of optimization process
- **Consolidated Results**: Excel sheets with comprehensive metrics

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📚 Citation

If you use this code in your research, please cite:

```
@software{enhanced_sparse_gpr,
  author = {Anindya},
  title = {Enhanced Sparse GPR with Spectral Mixture Kernel},
  year = {2025},
  url = {https://github.com/yourusername/enhanced-sparse-gpr}
}
```

## 📞 Contact

For questions or feedback, please open an issue on GitHub or contact the author directly.
