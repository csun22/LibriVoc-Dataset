# LibriVoc Dataset

## Overview

LibriVoc is an open-source, large-scale dataset designed for vocoder artifact detection in synthesized speech. Built upon the LibriTTS speech corpus—a widely-used resource in text-to-speech research derived from LibriVox audiobooks—LibriVoc provides a comprehensive benchmark for evaluating and detecting synthetic speech artifacts.

**Dataset Access:** [Download from Google Drive](https://drive.google.com/file/d/1Zh6b51S1WIsFjdCDRTQhYW61CQ0Ue1lk/view)

## Dataset Composition

LibriVoc features speech samples generated using six state-of-the-art neural vocoders across three major categories:

- **Autoregressive vocoders:** WaveNet, WaveRNN
- **GAN-based vocoders:** MelGAN, Parallel WaveGAN
- **Diffusion-based vocoders:** WaveGrad, DiffWave

### Dataset Statistics

- **Real samples (training):** 126.41 hours
- **Synthesized samples (training):** 118.08 hours
- **Total samples:** 43,809 (Training: 33,236 | Development: 5,736 | Testing: 4,837)

### Audio Distribution by Vocoder

| Model | train-clean-100 | train-clean-360 | dev-clean | test-clean |
|:---:|:---:|:---:|:---:|:---:|
| WaveNet | 4.28 | 15.49 | 0.75 | 0.76 |
| WaveRNN | 4.33 | 14.92 | 0.67 | 0.72 |
| MelGAN | 4.36 | 15.26 | 0.71 | 0.76 |
| Parallel WaveGAN | 4.37 | 15.54 | 0.68 | 0.75 |
| WaveGrad | 4.19 | 15.81 | 0.76 | 0.74 |
| DiffWave | 4.16 | 15.37 | 0.62 | 0.66 |
| **Total** | **25.69** | **92.39** | **4.19** | **4.39** |

*All values represent hours of audio*

## Methodology

### Self-Vocoding Process

Each vocoder synthesizes waveform samples from mel spectrograms extracted from original LibriTTS samples—a process called "self-vocoding." By providing identical mel spectrograms to all vocoders, any unique artifacts in the synthesized samples can be directly attributed to the specific vocoder used for reconstruction.

### Dataset Design

To prevent overfitting to speaker identity, the dataset employs a balanced speaker-level distribution:

1. **25% of speakers:** Only real (original) samples
2. **25% of speakers:** Only synthesized samples  
3. **50% of speakers:** Mixed composition (50% real, 50% synthesized per speaker)

This stratified design ensures that classifiers trained on LibriVoc learn to detect vocoder artifacts rather than memorizing speaker characteristics.

### Data Splits

The dataset is divided into three non-overlapping sets:

- **Training set:** 33,236 samples
- **Development set:** 5,736 samples
- **Testing set:** 4,837 samples

## Applications

LibriVoc is suitable for:

- Training and evaluating vocoder artifact detectors
- Benchmarking synthetic speech detection algorithms
- Researching vocoder-specific acoustic signatures
- Developing robust deepfake audio detection systems

## Citation

If you use the LibriVoc dataset in your research, please cite the original paper:
https://link.springer.com/chapter/10.1007/978-3-031-49803-9_11
```
@incollection{sun2023using,
  title={Using Vocoder Artifacts For Audio Deepfakes Detection},
  author={Sun, Chengzhe and AlBadawy, Ehab and Davison, Timothy F and Robinson, Sarah R and Chang, Ming-Ching and Lyu, Siwei},
  booktitle={Adversarial Multimedia Forensics},
  pages={263--282},
  year={2023},
  publisher={Springer}
}
```

## License

Print ISBN
978-3-031-49802-2

Online ISBN
978-3-031-49803-9
