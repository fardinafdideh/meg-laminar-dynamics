![](ppt/logos.png)

[![](https://img.shields.io/badge/DOI-10.1016/j.neuroimage.2020.116862-blue)](https://doi.org/10.1016/j.neuroimage.2020.116862)

# 🧠 Dynamic Multi-Laminar Headcast-Powered MRI-Informed MEG Source Reconstruction
![MEG](https://img.shields.io/badge/Modality-MRI%20%7C%20MEG-orange.svg)
![Framework](https://img.shields.io/badge/Framework-SPM%20%7C%20FieldTrip%20%7C%20VBQ%20%7C%20FreeSurfer%20%7C%20CSURF%20%7C%20AFNI%20%7C%20Psychtoolbox%20%7C%20Pipelines_ILCB-lightgrey.svg)

Tracking Information Flow in Dynamic Communication in the Brain Networks: Optimal Localization of Brain Sources using MRI-Informed MEG Source Reconstruction.

This research work was supported by ERC project [BrainDyn](https://cordis.europa.eu/project/id/716862) (PI: Dr. [Mathilde Bonnefond](https://scholar.google.com/citations?user=Xc1fz38AAAAJ&hl=en)).

## 📖 Overview
Understanding the directional flow of information in brain networks requires high spatiotemporal resolution. 
We reconstruct time-resolved laminar cortical dynamics across White Matter, In-between, and Pial surfaces using MRI-informed MEG source reconstruction. This framework enables the disentanglement and tracking of feedforward and feedback information flows by resolving activity in deep versus superficial cortical layers.

## ⚙️ Pipeline
![](ppt/Diapositive15.PNG)
```mermaid
graph TD
    %% Inputs
    subgraph Modalities
    MRI[Quantitative MRI - MPM]
	fMRI[fMRI]
	aMRI[Anatomical MRI]
    MEG[MEG]
    end

    %% MEG Stream
    subgraph MEG Stream
    MEG --> win[Noisy Windows Rejection]
    win --> sen[Noisy Sensors Rejection]
    sen --> comp[Noisy Components Rejection]
	comp --> trl[Noisy Trials Rejection]
    end

    %% Functional Stream
    subgraph fMRI Stream
    fMRI --> ret[Retinotopy]
    end

    %% Structural Stream
    subgraph MRI Stream
    MRI --> VBQ[VBQ, FreeSurfer, CSURF, and AFNI]
    VBQ --> Surf[Surface Extraction]
    Surf --> Layers[Layer Generation: Pial, In-Between, White Matter]
    end



	%% coregistration
	subgraph Coregistration
	aMRI --> HC[Headcast]
	end

    %% Fusion
    Layers --> Inv[Dynamic Multi-Laminar Headcast-Powered MRI-Informed MEG Source Reconstruction]
    trl --> Inv
	%% HC --> win
	HC --> MEG
```

### 🚀 Laminar Dynamics 
**Laminar specificity**, which is usefule in distinguishing between superficial (pial), middle, and deep (white matter) cortical layers dynamics to resolve feedforward vs. feedback information flow, is obtained from the following pipelines:
- **MRI Stream:**  
	- **Anatomical MRI:** It was used to create individualized 3D-printed [headcasts](https://jbonaiuto.com/tags/head-cast/) for precise co-registration and minimised head movements.
	- **Quantitative MRI (MPM):** Multi-Parameter Mapping ($R1, PD, MT, R2$) to extract cortical surfaces.
	- **Boundary Surfaces Extraction:** VBQ, FreeSurfer, CSURF, and AFNI processing are used to extract high-resolution cortical meshes for Pial and White Matter.
 	- **Layer Generation:** Intermediate laminar surfaces are derived from the extracted Pial and White Matter boundaries, incorporating neurophysiological anatomical priors.
- **MEG Stream:**
	- **Stimulation:** Visual.
	- **[Headcast](https://jbonaiuto.com/tags/head-cast/):** Individualized 3D-printed headcasts are used during acquisition to eliminate head movement and ensure precise co-registration with the MRI.
	- **Preprocessing:** A toolbox adapted from [Pipelines ILCB](https://github.com/brovelli/pipelines-ilcb), a rigorous multi-stage pipeline, allowing spatial-temporal-spectral filtering, and ensuring high signal-to-noise ratio (SNR), was developed and used to reject noisy window(s), sensor(s), ICA component(s), and trial(s).
- **Dynamic Multi-Laminar Headcast-Powered MRI-Informed MEG Source Reconstruction:** The Dynamic Imaging of Coherent Sources (DICS) beamforming method, which is based on reconstructing sources that show strong dependency (coherence) in the frequency domain, implemented in [Pipelines ILCB](https://github.com/brovelli/pipelines-ilcb) was used to reconstruct source activities.

![](ppt/whiteInbetweenPial-layer-source-space.gif)

### ⚡ Spatial Prior Selection 
A dedicated GUI-based toolbox developed to optimize source reconstruction through:
- **Interactive Prior Selection:** Manually select multiple spatial priors with real-time visualization. 
- **fMRI Integration:** Visualizes source locations (spatial priors) overlaid on fMRI activation maps to constrain the source reconstruction problem (using the parametric empirical Bayesian framework in SPM).
  
![](ppt/spatialPriorManualSelection.gif)

## 🔬 Tracking Information Flow in Dynamic Communication in the Brain Networks
![](ppt/Diapositive1.PNG)
![](ppt/Diapositive2.PNG)
![](ppt/Diapositive3.PNG)
![](ppt/Diapositive4.PNG)
![](ppt/Diapositive5.PNG)
![](ppt/Diapositive6.PNG)
![](ppt/Diapositive7.PNG)
![](ppt/Diapositive8.PNG)
![](ppt/Diapositive9.PNG)
![](ppt/Diapositive10.PNG)
![](ppt/Diapositive11.PNG)
![](ppt/Diapositive12.PNG)
![](ppt/Diapositive13.PNG)
![](ppt/Diapositive14.PNG)
![](ppt/Diapositive15.PNG)
![](ppt/Diapositive16.PNG)
![](ppt/Diapositive17.PNG)
![](ppt/Diapositive18.PNG)
![](ppt/Diapositive19.PNG)
![](ppt/Diapositive20.PNG)
![](ppt/Diapositive21.PNG)
![](ppt/Diapositive22.PNG)
![](ppt/Diapositive23.PNG)
![](ppt/Diapositive24.PNG)
![](ppt/Diapositive25.PNG)
![](ppt/Diapositive26.PNG)
![](ppt/Diapositive27.PNG)
![](ppt/Diapositive28.PNG)
![](ppt/Diapositive29.PNG)
![](ppt/Diapositive30.PNG)
![](ppt/Diapositive31.PNG)
![](ppt/Diapositive32.PNG)
![](ppt/Diapositive33.PNG)
![](ppt/Diapositive34.PNG)
![](ppt/Diapositive35.PNG)
![](ppt/Diapositive36.PNG)
![](ppt/Diapositive37.PNG)
![](ppt/Diapositive38.PNG)
![](ppt/Diapositive39.PNG)
![](ppt/Diapositive40.PNG)
![](ppt/Diapositive41.PNG)
![](ppt/Diapositive42.PNG)
![](ppt/Diapositive43.PNG)
![](ppt/Diapositive44.PNG)
![](ppt/Diapositive45.PNG)
![](ppt/Diapositive46.PNG)
![](ppt/Diapositive47.PNG)
![](ppt/Diapositive48.PNG)
![](ppt/Diapositive49.PNG)
![](ppt/Diapositive50.PNG)
![](ppt/Diapositive51.PNG)
![](ppt/Diapositive52.PNG)
![](ppt/Diapositive53.PNG)

## 📚 How to cite
* **F. Afdideh**, et al., "Tracking Information Flow in Dynamic Communication in the Brain Networks: Optimal Localization of the Brain Sources and Developing Functional Connectivity Approaches using MEG", to be published.
*	J. J. Bonaiuto, **F. Afdideh**, M. Ferez, K. Wagstyl, J. Mattout, M. Bonnefond, G. R Barnes, S. Bestmann, “Estimates of cortical column orientation improve MEG source inversion,” *[NeuroImage](https://www.sciencedirect.com/science/article/pii/S1053811920303487)*, vol. 216, p. 116862, Aug. 2020, doi: 10.1016/j.neuroimage.2020.116862.
