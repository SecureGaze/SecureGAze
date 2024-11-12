# SecureGaze: Defending Gaze Estimation Against Backdoor Attacks

This repository contains the demo for the SenSys 2025 submission **SecureGaze: Defending Gaze Estimation Against Backdoor Attacks**. We will make the codes publicly available upon paper acceptance.

## Real-time Video Demo
We demonstrate the threat of the backdoor attack on gaze estimation in the physical world. A simple white paper tape can trigger the backdoor behavior of the backdoored gaze estimation model to alter its output gaze direction. The backdoored gaze estimation model is trained using GazeCapture dataset and evaluated on the recruited subject.

### Setup for the physical world attack
The subject is instructed to track a red square stimulus that sequentially appears at each corner of a 24-inch desktop monitor. The sequence of appearance follows the order: top-left, top-right, bottom-right, and bottom-left. The stimulus remains visible at each corner for four seconds before disappearing and reappearing at the next position. In the meantime, a webcam captures full-face images of the participant at 25Hz, and use them as inputs for gaze estimation. The setup is illustrated in the following figure.

<div align=center>
<img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/gaze_pipeline.png" alt="My Image" width="500"/>
</div>


### Demo of backdoor attack on gaze estimation
The red arrow represents the gaze directions estimated by the backdoored gaze estimation model. When the trigger is absent, the arrow can follow the subject's gaze directions. However, when the trigger is present, the arrow points at the center of the screen, regardless of the actual gaze of the subject.

<table style="border: none;">
  <tr>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/backdoor_benign.gif" alt="Benign Image" width="300"/>
      <br><em>Estimated gaze for the subject without the physical trigger.</em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/backdoor_poisoned.gif" alt="Poisoned Image" width="300"/>
      <br><em>Estimated gaze for the subject with the physical trigger. </em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/backdoor_both.gif" alt="Both Images" width="300"/>
      <br><em>Estimated gaze when the subject puts on and removes the physical trigger.</em>
    </td>
  </tr>
</table>


### Demo of backdoor attack on gaze mitigation

The red and blue arrows represent the gaze directions estimated by the backdoored and the backdoor-mitigated gaze estimation models, respectively. When the trigger is absent, both the red and blue arrows correctly reflect the subject's gaze directions. However, when the trigger is present, the red arrow points at the center of the screen, regardless of the actual gaze of the subject. By contrast, the blue arrow continues to correctly follow the subject's gaze. 

<table>
  <tr>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/mitigated_benign.gif" alt="Benign Image" width="300"/>
      <br><em>Estimated gaze for the subject without the physical trigger.</em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/mitigated_poisoned.gif" alt="Poisoned Image" width="300"/>
      <br><em>Estimated gaze for the subject with the physical trigger. </em>
    </td>
    <td align="center">
      <img src="https://github.com/SecureGaze/SecureGaze/blob/main/figures/mitigated_both.gif" alt="Both Images" width="300"/>
      <br><em>Estimated gaze when the subject puts on and remove the physical trigger.</em>
    </td>
  </tr>
</table>

