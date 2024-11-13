# SecureGaze: Defending Gaze Estimation Against Backdoor Attacks

This repository contains the demo for the SenSys 2025 submission **SecureGaze: Defending Gaze Estimation Against Backdoor Attacks**. We will make the implementation of SecureGaze publicly available upon paper acceptance.

## Real-time Video Demo
We demonstrate the threat of backdoor attacks on gaze estimation models in a real-world setting. Using a simple piece of white paper tape, an attacker can activate the backdoor in a compromised model, manipulating it to produce an attacker-chosen gaze direction instead of the actual one. The backdoored model was trained on the GazeCapture dataset, and the demonstration involved four invited participants.

### Setup for the physical world attack
The participant is instructed to track a red square stimulus that appears sequentially at each corner of a 24-inch desktop monitor. The stimulus follows this order: top-left, top-right, bottom-right, and bottom-left. It remains visible at each corner for four seconds before disappearing and reappearing at the next position. During this process, a webcam captures full-face images of the participant at 25 Hz, which are used as inputs for gaze estimation. The setup is illustrated in the figure below.

<div align=center>
<img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/gaze_pipeline.png" alt="My Image" width="450"/>
</div>

### Demo of backdoor attack on gaze estimation model
The red arrow represents the gaze directions estimated by the backdoored gaze estimation model. In the absence of the trigger, the arrow accurately follows the subject's gaze directions, i.e., as shown in Video (a). However, when the trigger is present, the arrow consistently points to the center of the screen, ignoring the subject's actual gaze, i.e., as shown in Video (b).

<table style="border: none;">
  <tr>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/backdoor_benign.gif" alt="Benign Image" width="250"/>
      <br><em>Estimated gaze for the subject without the trigger.</em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/backdoor_poisoned.gif" alt="Poisoned Image" width="250"/>
      <br><em>Estimated gaze for the subject with the trigger. </em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/backdoor_both.gif" alt="Both Images" width="250"/>
      <br><em>Estimated gaze when the subject puts on and removes the trigger.</em>
    </td>
  </tr>
</table>

**This video demonstrates that a simple physical item, such as a piece of white tap, can effectively activate the backdoor behavior.**


### Demo of backdoor attack on gaze mitigation

The red and blue arrows represent the gaze directions estimated by the backdoored and the backdoor-mitigated gaze estimation models, respectively. When the trigger is absent, both the red and blue arrows correctly reflect the subject's gaze directions. However, when the trigger is present, the red arrow points at the center of the screen, regardless of the actual gaze of the subject. By contrast, the blue arrow continues to correctly follow the subject's gaze. 

<table>
  <tr>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/mitigated_benign.gif" alt="Benign Image" width="250"/>
      <br><em>Estimated gaze for the subject without the trigger.</em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/mitigated_poisoned.gif" alt="Poisoned Image" width="250"/>
      <br><em>Estimated gaze for the subject with the trigger. </em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/mitigated_both.gif" alt="Both Images" width="250"/>
      <br><em>Estimated gaze when the subject puts on and removes the trigger.</em>
    </td>
  </tr>
</table>

**This video demonstrates that SecureGaze can effectively mitigate the backdoor behavior of the backdoored gaze estimation model.**
