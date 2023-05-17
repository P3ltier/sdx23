
# Submission

## Submission Summary

* MDX Leaderboard C
	* Submission ID: 216768
	* Submitter: kim_min_seok
	* Final rank: 5th place
	* Final scores:
	  |  SDR_song | SDR_bass | SDR_drums | SDR_other | SDR_vocals |
	  | :------: | :------: | :-------: | :-------: | :--------: |
	  |   8.971   |   9.716   |   9.433   |   6.721    |    10.012    |

## Model Summary

* Data
  * All 150 tracks of MusdbHQ
  * Augmentation
    * Random chunking and mixing sources from different tracks ([1])
    * Pitch shift and time stretch ([2])
* Model
  * Ensemble of 5 models
	  * 2 x Hybrid Demucs[3, 4] 
		  * we used the pretrained weights (htdemucs_ft, hdemucs_mmi) from [github.com/facebookresearch/demucs](https://github.com/facebookresearch/demucs)
	  * 3 x TFC-TDF U-Net[5, 6]
		  * 'multi-source' version with some architectural improvements, including Channel-wise Subband[7]

[1] S. Uhlich et al., "Improving music source separation based on deep neural networks through data augmentation and network blending", ICASSP 2017.

[2] Cohen-Hadria, Alice, et al. "Improving singing voice separation using Deep U-Net and Wave-U-Net with data augmentation", EUSIPCO 2019.

[3] Defossez, Alexandre, "Hybrid Spectrogram and Waveform Source Separation", MDX Workshop at ISMIR 2021.

[4] Rouard, Simon, et al. "Hybrid Transformers for Music Source Separation". 

[5] Choi, Woosung, et al. "Investigating u-nets with various intermediate blocks for spectrogram-based singing voice separation", ISMIR 2020.

[6] Kim, Minseok, et al. “Kuielab-mdx-net: A two-stream neural network for music demixing”, MDX Workshop at ISMIR 2021.

[7] Liu, Haohe, et al. "Channel-wise Subband Input for Better Voice and Accompaniment Separation on High Resolution Music", INTERSPEECH 2020.

# Reproduction

Download [mdx_C.zip](https://drive.google.com/file/d/12CRm9qfB_z7YeHT0xHyhUBEFtK2Q819x/view?usp=sharing), which contains 
  * pretrained model checkpoints, including pretrained demucs weights (htdemucs_ft and hdemucs_mmi)
  * config.yaml files (configurations for training and inference)

## How to reproduce the submission
1. Create a 'ckpts' folder under [my_submission](my_submission). Unzip the downloaded zip file to 'my_submission/ckpts'.
2. Copy [my_submission](my_submission) and [requirements.txt](requirements.txt) to your [SDX 2023 Music Demixing Track Starter Kit](https://gitlab.aicrowd.com/aicrowd/challenges/sound-demixing-challenge-2023/sdx-2023-music-demixing-track-starter-kit/).
3. Run submit.sh
