# Fourier-Analysis
In this notebook, we carry out a full Fourier analysis of a time series. Our main objective is to decompose the signal into its constituent frequency components using the Fourier Transform, identify the frequencies of interest, and filter out the unwanted ones. We also propose a method to perform this process automatically.

![](img/img1.png)

![](img/img2.png)

![](img/img3.png)

## Filtering using intervals of frequencies

If we have an interval of frequencies $\Omega = (\omega_1, \omega_2)$ that is relevant, for instance, the frequencies that represent a sesonality, or the ones that represent the noise. We can filter $F(\omega)$ by defining a new function $\hat{F}(\omega)$ that:

$$
\hat{F}(\omega)
\begin{cases}
F(\omega) & \text{if}\; \omega \in \Omega \\
0 & \text{if}\; \omega \notin \Omega
\end{cases}
$$

We can return to the time domain by using the Inverse Fourier Transform. As we can see, the Inverse Fourier Transform of $\hat{F}(\omega)$ is nothing more than the Inverse Fourier Transform of $F(\omega)$ in our interval of interest $\Omega$:

$$\psi(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} \hat{F}(\omega) \, e^{i \omega t} \, d\omega = \frac{1}{2\pi} \left( \int_{\mathbb{R} ∖ \Omega} \hat{F}(\omega) \, e^{i \omega t} \, d\omega + \int_{\Omega} \hat{F}(\omega) \, e^{i \omega t} \, d\omega\right) = \frac{1}{2\pi} \left( 0 + \int_{\Omega} F(\omega) \, e^{i \omega t} \, d\omega \right)$$

$$\psi(t) = \frac{1}{2\pi} \int_{\Omega} F(\omega) \, e^{i \omega t} \, d\omega$$

In the case of having multiple intervals of interest, we can reconstruct the complete time series with all the relevant information:

$$\psi(t) = \psi_1(t) + \psi_2(t) + \cdots + \psi_n(t) = \sum_i \psi_i(t)$$

$$\sum_i \psi_i(t) = \frac{1}{2\pi} \left( \int_{\Omega_1} F(\omega) \, e^{i \omega t} \, d\omega + \int_{\Omega_2} F(\omega) \, e^{i \omega t} \, d\omega + \cdots + \int_{\Omega_n} F(\omega) \, e^{i \omega t} \, d\omega \right) = $$

$$\psi(t) = \sum_i \psi_i(t) =  \frac{1}{2\pi} \int_{\bigcup_i \Omega_i} F(\omega) \, e^{i \omega t} \, d\omega$$
