# CharNet OCR 

As the name suggests, this OCR follows a top-down approach where it splits the image into lines, words, and characters. Predicting character-by-character, it is able to handle arbitary length of text.


## Features 

- [x] Predicts character-by-character
- [x] Compatible for handwriting-like text
- [x] An ensemble of 4 CNNs
- [x] Enables OCR parameter tweaking

## A little about the models


### The Dataset 

To train the CNNs, its dataset was carefully generated through ~1,920 fonts [("100% free" filter enabled on dafont.com under the "Script > Handwritten" category)](https://www.dafont.com/theme.php?cat=603&page=1&fpp=50&l[]=10&l[]=1). Out of which, 2,434 font files were extracted.


- 617 font files were removed as outliers for lowercase characters
- TODO: Uppercase
- TODO: Symbols


### The Models

#### 1. CharNet_LC 

- **Input**: 32x32x1
- **Output**: 26 (a-z)
- **Architecture**: 
    - Conv2D(32, (3, 3), activation='relu')
    - Conv2D(64, (3, 3), activation='relu')
    - MaxPooling2D(pool_size=(2, 2))
    - Dropout(0.25)
    - Flatten()
    - Dense(128, activation='relu')
    - Dropout(0.5)
    - Dense(26, activation='softmax')