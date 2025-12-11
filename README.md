Machine Learning as a Service (MLaaS) has become increasingly popular because developing modern machine learning models requires substantial time, large datasets, expensive hardware, and specialized expertise. However, privacy concerns limit the use of MLaaS in scenarios involving sensitive data. A practical privacy-preserving approach is to apply fully homomorphic encryption (FHE), which allows computations to be performed directly on encrypted data. Recent progress in FHE has significantly reduced computational overhead, making secure machine learning more feasible.

In this project, I present a simplified version of the REDsec framework, designed to optimize FHE-based private machine-learning inference using ternary neural networks. A key feature of the framework is a data-reuse mechanism that supports bidirectional conversion between integer and binary representations within FHE. This allows efficient binary operations for activations and multiplications while still enabling low-cost integer additions.

My implementation focuses on CPU-based execution and does not use GPU acceleration. Instead, the emphasis is on demonstrating practicality and correctness using the MNIST dataset. The framework supports user-defined models, automated plaintext training, and efficient encrypted inference built on TFHE. Experimental results on MNIST show improved efficiency compared to baseline homomorphic-inference approaches.

What Was Done in This Project

Installation of REDsec, TFHE, and a controlled Python 3.8 virtual environment with TensorFlow and Pandas with correct versions installed.

Analysis and execution of the provided quantized MNIST sample network.

Multiple full training runs on CPU, producing varied but consistent accuracy in the range of approximately 92–94%.

Export of the trained model and verification of REDsec’s model statistics (layer count, MAC operations, memory footprint).

Preparation for encrypted inference measurements in REDsec (latency and accuracy).

Model parameters (dense layer sizes, quantizers) were inspected to understand their effect on privacy and performance. Configuration differences were used to illustrate the privacy–performance relationship.

Why All Experiments Were Run on CPU

TFHE bootstrapping operations do not support GPU acceleration. Even large GPU clusters cannot speed up TFHE-based inference because the algorithm is inherently sequential and optimized for CPUs.

The networks used in this project contain only tens of thousands of parameters. CPU training takes only seconds per epoch, so GPU acceleration does not provide meaningful benefits.
