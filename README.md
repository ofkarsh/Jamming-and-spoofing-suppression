Jamming Mitigation Module Approach
The Jamming Mitigation Module focuses on suppressing interference from jamming signals that typically disrupt the operation of GPS systems. Jamming is often introduced by high-power noise or malicious signals intended to overwhelm the receiver’s ability to detect the legitimate GPS signal.

Key Techniques Used:
Signal Generation and Jamming Simulation:

Jamming Signal Creation: A simulated jamming signal is generated as random noise with a higher power level than the GPS signal. This jamming signal is added to the GPS signal to simulate real-world interference.
The received signal is then a mix of the true GPS signal and the jamming signal, which is subject to further processing.
Matched Filtering:

A matched filter is applied to the received signal to enhance the GPS signal. The filter correlates the received signal with a known GPS signal template (phase-corrected using a PLL).
The matched filter output maximizes the Signal-to-Noise Ratio (SNR) for the GPS signal, but the jamming interference may still distort the result.
Atomic Decomposition:

Atomic decomposition is used to model the jamming signal. A dictionary of atoms is created based on the estimated jamming parameters (such as delay and frequency). The atomic dictionary helps to model the jamming interference.
The system performs projection of the received signal onto the dictionary atoms and then removes the jamming components by subtracting the projections from the received signal, leaving only the clean GPS signal.
Dynamic CFAR (Constant False Alarm Rate):

This technique is used to adaptively set a threshold based on the local noise level in the received signal. It dynamically adjusts the threshold so that false alarms are minimized while detecting valid signal peaks.
This helps identify the presence of legitimate GPS signals, even in the presence of jamming.
Jamming Parameter Estimation:

Frequency and Time Delay Estimation: The system estimates the jamming signal’s frequency and time delay by analyzing its interaction with chirp waveforms. This estimation helps in better understanding the jamming signal's characteristics, allowing for more effective mitigation strategies.
Spoofing Mitigation Module Approach
The Spoofing Mitigation Module focuses on detecting and suppressing spoofing attacks, where false GPS signals are transmitted to deceive the receiver into calculating an incorrect position. Spoofing is more sophisticated than jamming as it mimics the legitimate GPS signal and tries to deceive the receiver into tracking a fake signal.

Key Techniques Used:
Signal Generation and Spoofing Simulation:

A spoofing signal is generated using a frequency offset or time shift from the true GPS signal. The spoofing signal mimics a GPS signal but is intentionally designed to mislead the receiver.
Cyclic Correlation Matrix Estimation:

The system first estimates the cyclic correlation matrix from the received signal. This matrix provides valuable information about the signal structure and helps differentiate between genuine GPS signals and spoofing signals.
The matrix is computed over multiple data blocks to address finite sample issues and ensure robust estimation.
Cyclic MUSIC Algorithm for DOA (Direction of Arrival) Estimation:

The Cyclic MUSIC algorithm is used for Direction of Arrival (DOA) estimation. By analyzing the spatial characteristics of the signal and estimating the direction from which it originated, the system can distinguish between the real GPS signal and the spoofed signal.
The algorithm identifies multiple peaks in the DOA spectrum, where the true GPS signal will have a distinct DOA compared to the spoofing signal.
Spoofing Subspace Projection:

Once spoofing signals are identified, subspace projection is used to remove the spoofing signal components from the received signal. By projecting the received signal onto the noise subspace (using the eigendecomposition of the cyclic correlation matrix), the spoofing components are suppressed.
The remaining signal after projection is the clean, authentic GPS signal.
Jamming and Spoofing Parameter Estimation:

The system estimates key parameters of the spoofing signal, such as time delay and frequency, using the twinning waveforms and correlation analysis. This helps understand the spoofing signal's characteristics and aids in accurate mitigation.

Summary of Jamming and Spoofing Mitigation
Jamming Mitigation:
Focuses on suppressing interference by applying techniques like atomic decomposition, matched filtering, and dynamic CFAR detection.
The key challenge is separating the legitimate GPS signal from random or malicious noise.
Spoofing Mitigation:
Targets fake GPS signals by leveraging cyclic correlation matrix estimation, DOA estimation via Cyclic MUSIC, and subspace projection.
The goal is to detect spoofed signals based on their spatial and temporal characteristics and remove them from the received signal.
Both modules work together to provide robust protection against both jamming and spoofing, ensuring reliable GPS signal processing and positioning in hostile environments.
