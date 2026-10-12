# Pol-CACTI Dataset

**Pol-CACTI: A System and Dataset for High-Speed Polarized Video Compressive Imaging**  
**ECCV 2026**

Yunfeng Song*, Yidong Luo*, Ping Wang, Xingjian Jiang, and Xin Yuan  
*Equal contribution.

[Paper](https://doi.org/10.1007/978-3-032-37624-4_31) · [Project Repository](https://github.com/kaeoqxhailesxya/Pol-CACTI) · [Dataset Overview](#dataset-overview) · [Citation](#citation)

<!-- Optional: add a dataset teaser or sample video here once the corresponding asset is uploaded. -->

## Overview

Pol-CACTI is a **monochrome polarized video dataset** for research in polarized video snapshot compressive imaging. The accompanying paper presents an optical system that encodes polarization dynamics into a single measurement, together with a reconstruction network that jointly recovers temporal information and polarization channels. Its Polarization-Aware Learnable Back-Projection (PA-LBP) module promotes consistency with DoFP measurements. See the [paper](https://doi.org/10.1007/978-3-032-37624-4_31) for the acquisition, Stokes-domain denoising, and reconstruction methodology.

The frame-based data described here contain **8,889 frames** organized into **141 sequence folders**, with separate training and testing splits.

## Dataset Overview

| Split     | Sequence folders | Frames    | Frames per folder | Image resolution (H × W) | File format |
| --------- | ----------------:| ---------:| ----------------- | ------------------------ | ----------- |
| Train     | 131              | 8,409     | 30–92             | 2048 × 2048              | BMP         |
| Test      | 10               | 480       | 48                | 1024 × 1024              | BMP         |
| **Total** | **141**          | **8,889** | —                 | —                        | —           |

- Each folder contains one image sequence.
- All image files store **single-channel, 8-bit (`uint8`) arrays**.
- The current test split contains **480 BMP files** .
- Sequence lengths vary in the training split. Each test sequence contains exactly 48 frames.
- Keep the provided `Train` and `Test` split assignments when reporting results.

The resolution listed above is the size of each stored image array. It does not denote the resolution of an individual polarization-angle channel.

## Acquisition Hardware

The dataset was captured using a **FLIR Blackfly S BFS-U3-51S5P-C polarization camera** equipped with a **Sony IMX250MZR division-of-focal-plane (DoFP) sensor**.

| Property                                   | Specification                  |
| ------------------------------------------ | ------------------------------ |
| Camera                                     | FLIR Blackfly S BFS-U3-51S5P-C |
| Sensor                                     | Sony IMX250MZR                 |
| Imaging modality                           | Monochrome polarization        |
| Shutter                                    | Global shutter                 |
| Native camera resolution                   | 2448 × 2048 pixels             |
| Nominal full-resolution maximum frame rate | 75 FPS (camera specification)  |
| Linear polarization analyzer angles        | 0°, 45°, 90°, and 135°         |

Hardware specifications are available from the [camera manufacturer](https://www.teledynevisionsolutions.com/products/blackfly-s-usb3/?model=BFS-U3-51S5P-C&segment=iis&vertical=machine+vision). The nominal camera frame rate is a hardware specification; the acquisition rate and effective reconstruction frame rate should be taken from the experimental protocol.

**Released-image DoFP angle layout:** to be documented. The exact mapping of pixel positions to analyzer angles should be confirmed for the exported images before polarization demosaicing or Stokes computation.

<!-- Maintainer: insert the verified 2×2 analyzer-angle arrangement for these exports, including any orientation or crop-origin convention. -->

## Download

**Dataset download:** [Hugging Face — Pol-CACTI](https://huggingface.co/datasets/Finnick222/Pol-CACTI)

- [Train — 8,409 frames](https://huggingface.co/datasets/Finnick222/Pol-CACTI/tree/main/Train)
- [Test — 480 frames](https://huggingface.co/datasets/Finnick222/Pol-CACTI/tree/main/Test)

The data package contains the following two directories:

```text
dataset/
├── Train/
│   ├── <sequence_id>/
│   │   ├── <frame_id>.bmp
│   │   └── ...
│   └── ...
└── Test/
    ├── <sequence_id>/
    │   ├── <frame_id>.bmp or <frame_id>.png
    │   └── ...
    └── ...
```

Use the original sequence and frame filenames. Filenames may contain a `frame_` prefix, and frame indices may have gaps. Sort the available frames by their numeric index rather than assuming consecutive filenames.

## Citation

If you use the dataset in your research, please cite:

```bibtex
@inproceedings{song2026polcacti,
  author    = {Song, Yunfeng and Luo, Yidong and Wang, Ping and
               Jiang, Xingjian and Yuan, Xin},
  title     = {{Pol-CACTI}: A System and Dataset for High-Speed
               Polarized Video Compressive Imaging},
  booktitle = {Computer Vision -- ECCV 2026},
  year      = {2026},
  volume    = {17028},
  series    = {Lecture Notes in Computer Science},
  pages     = {521--539},
  publisher = {Springer, Cham},
  doi       = {10.1007/978-3-032-37624-4_31},
  url       = {https://doi.org/10.1007/978-3-032-37624-4_31}
}
```

## License

**Dataset license: to be specified by the authors.**

<!-- Maintainer: add the dataset license and a matching LICENSE file before public distribution. Specify code licensing separately if code is included. -->

## Contact

For questions about the dataset, please contact: songyunfeng@westlake.edu.cn
