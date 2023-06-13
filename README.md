# BAT_Transformer
bio, audio, text multimodal transformer
![image](https://user-images.githubusercontent.com/52825569/233546214-dce7d2e7-81a5-42b0-9135-feeacbc7ab5a.png)


This model is used to recognize emotion based on bio, audio and texts.

# Datasets
We used KEMDy20 dataset for the project. It can be downloaded from https://nanum.etri.re.kr/share/kjnoh/KEMDy20?lang=ko_KR 

You can download train, valid, test and preprecessed dataset(audio_augmented_per3500.pkl) from http://naver.me/FjjAr0qG 

# Methodology
* Data Augmentation
* Bio Data
* Audio Data
* Text Data

#### Data Augmentation
* The label imbalance was so severe that data augmentation was necessary.
* Bio data has been augmented by SMOTE. (It was only used in the control group)
* Text data were augmented by replacing words with synonyms through wordnet. (It was only used in the control group)
* Audio data has been augmented by pitch changes, noise additions, and random value multiplication.

#### Bio Data
* Only TEMP and EDA were used in the bio data from KEMDy20 dataset.
* Each of Temp and EDA data was zero-padded at 80 lengths.
* Bio data has been augmented by SMOTE. (It was only used in the control group)

#### Audio Data
* The audio data from KEMDy20 dataset is used to extract MFCC.
* The MFCC is extracted using signal in librosa library.
* The MFCC has been augmented. 
* The MFCC data was averaged after zero padding at 600 lengths.

#### Text Data
* The audio data from KEMDy20 dataset is tokenized through okt library.
* Text data were augmented by replacing words with synonyms through wordnet. (It was only used in the control group)

# Experiments
| Model | precision | recall | F1 score (weighted) |
| ------ | ------ | ------ | ------ | 
| Text (unimodal) | 0.7016 | 0.6966 | 0.6977 |
| Audio (unimodal) | 0.6452 | 0.8033 | 0.7154 |
| Bio TEMP (unimodal) | 0.6619 | 0.4258 | 0.5123 |
| Bio EDA (unimodal) | 0.6159 | 0.0331 | 0.0321 |
| BAT Trasformer | 0.7120 | 0.7631 |  _*0.7265*_ |
