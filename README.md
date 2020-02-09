# Recipe for VoicePrivacy Challenge 2020

Please visit the [challenge website](https://www.voiceprivacychallenge.org/) for more information about the Challenge.


## Install

1. `git clone --recurse-submodules https://github.com/Voice-Privacy-Challenge/Voice-Privacy-Challenge-2020.git`
2. ./install.sh

## Running the recipe

The recipe uses the pre-trained models of anonymization. To run the baseline system with evaluation:

1. `cd baseline` 
2. run `./run.sh`. In run.sh, to download models and data the user will be requested the password which is provided during the Challenge registration.

## General information

### Datasets


#### Training data
The dataset for anonymization system traing consists of subsets from the following corpora*:
* [LibriSpeech](http://www.openslr.org/12/) - train-clean-100, train-other-500
* [LibriTTS](http://www.openslr.org/60/) - train-clean-100, train-other-500
* [VoxCeleb 1 & 2](http://www.robots.ox.ac.uk/~vgg/data/voxceleb/) - all

*only specified subsets of these corpora can be used for training.

#### Development and evaluation data
* [VCTK](https://datashare.is.ed.ac.uk/handle/10283/3443) - subsets vctk_dev and vctk_test are download from server in run.sh
* [LibriSpeech](http://www.openslr.org/12/) - subsets libri_dev and libri_test are download from server in run.sh

*vctk_test and libri_test will be available to download after the specifed deadline


### Models

The baseline system uses several independent models:
1. ASR acoustic model to extract BN features (asr_am)
2. X-vector extractor (xvect_extr)
3. Speech synthesis (SS) acoustic model (ss_am)
4. Neural source filter (NSF) model (nsf)

These models optionally can be:
*  trained with the provided scripts;
or
* downloaded (done by ./baseline/local/download_models.sh)



    
### Models info

#### BN extractor

Chain TDNN-F ASR AM trained on LibriSpeech-train-clean-100 and LibriSpeech-train-other-500 for BN feature extraction

#### x-vector extractor

X-vector model trained on VoxCeleb 1 & 2.

- `xvec_nnet_dir`: Directory where trained xvector network is stored
- `pseudo_xvec_rand_level`: anonymized x-vectors will be produced at this level, e.g. `spk` or `utt`
- `cross_gender`: anonymization is done within same gender or across gender, e.g. `true` or `false`.


#### Speech symthesis (SS) acoustic model (AM)

Speech symthesis AM is trained on LibriTTS-train-clean-100.

Input features: 
- BN
- x-vector
- F0

#### Neural source-filter (NSF) model for voice conversion

NSF model is trained on LibriTTS-train-clean-100.

Input features:
- Mel filterbanks extracted by SS AM
- x-vector
- F0

All the pretrained models are provided as part of this baseline. 

## Organizers (in alphabetical order)

- Jean-François Bonastre - University of Avignon - LIA, France
- Nicholas Evans - EURECOM, France
- Fuming Fang - NII, Japan
- Andreas Nautsch - EURECOM, France
- Paul-Gauthier Noé - University of Avignon - LIA, France
- Jose Patino - EURECOM, France
- Md Sahidullah - Inria, France
- Brij Mohan Lal Srivastava - Inria, France
- Natalia Tomashenko - University of Avignon - LIA, France
- Massimiliano Todisco - EURECOM, France
- Emmanuel Vincent - Inria, France
- Xin Wang - NII, Japan
- Junichi Yamagishi - NII, Japan and University of Edinburgh, UK

Contact : voice.privacy.challenge@gmail.com


## Acknowledgements

This work was supported in part by the French National Research Agency under projects HARPOCRATES (ANR-19-DATA-0008) and DEEP-PRIVACY (ANR-18-
CE23-0018), by the European Union’s Horizon 2020 Research and Innovation Program under Grant Agreement No. 825081 COMPRISE (https://www.compriseh2020.eu/), and jointly by the French National Research Agency and the Japan Science and Technology Agency under project VoicePersonae. 

## License

Copyright (C) 2020

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <https://www.gnu.org/licenses/>.

---------------------------------------------------------------------------
