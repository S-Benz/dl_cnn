# CNN Entwicklung
Epochen = 10  
Testdaten = 50k  
Validierungsdaten = 10k
### 1 Iteration
Conv Layer 32 Filter 3x3  
Max Pool 2x2  
Conv Layer 64 Filter 3x3  
max pool 2x2  
Dense Layer 64x1  
Dense Layer 2x1    
--> 93%

### 2 Iteration
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Max Pool 2x2  
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
max pool 2x2  
conv layer 128 filter 3x3  
Dense Layer 64x1  
Dense Layer 2x1    
--> 93,9%

### 3 iteration
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Max Pool 2x2  
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
max pool 2x2  
conv layer 128 filter 3x3  
Dropout 0,5
Dense Layer 64x1  
Dense Layer 2x1    
--> 94,24%

### 4 iteration
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Max Pool 2x2  
Dropout 0,2
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
max pool 2x2  
Dropout 0,2
conv layer 128 filter 3x3  
Dropout 0,5
Dense Layer 64x1  
Dense Layer 2x1    
--> 93,96%


### 5 iteration
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Max Pool 2x2  
Dropout 0,5
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
max pool 2x2  
Dropout 0,5
conv layer 128 filter 3x3  
Dropout 0,5
Dense Layer 64x1  
Dense Layer 2x1    
--> 92,62%

### Iteration 6 
Idee: Beispiel Vgg16 letztes conv layer besteht aus 3 ebenen. Und vergrößern von dense layer von 64 auf 2048.
Dropout wieder reduzieren auf 0,2 und vor dense auf 0,4.  

Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3
dropout 0,2
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3
dropout 0,2
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Dense Layer 2048x1  
dropout 0,4
Dense Layer 2x1    
--> 94.87

### Iteration 7
Weglassen von allen dropouts um zu prüfen wie stark diese aktuell optimieren bzw. ob starkes overfitting vorliegt.

Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  

Dense Layer 2048x1  
Dense Layer 2x1    
-->  95,26%

### Iteration 8 
conv dropout weglassen

Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  

Dense Layer 2048x1   
dropout 0,4   
Dense Layer 2x1    
--> 94,68%

### Iteration 9
Input dropout hinzufügen

Aufbau:  
Dropout 0,2
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  

Dense Layer 2048x1   
dropout 0,4   
Dense Layer 2x1    
--> 91,28%

### Iteration 10
Increase learn rate to try and decrease epoch time

Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  

Dense Layer 2048x1  
Dense Layer 2x1    
--> 94,29% 

### Iteration 11
Added Simple Data augmentation for each train image:  
* horizontal, vertical and combined flip
* rotation 90 deg clockwise and counter clock wise

-->  In total 300k train images instead of 50k took ~10seconds to augment

Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  

Dense Layer 2048x1  
Dense Layer 2x1    
--> 95,01

# Iteration 12
Add dropout to augment data version to see if it can improve the cnn  

Aufbau:  
Dropout 0,2  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3
Dropout 0,2  
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3
Dropout 0,2  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Dropout 0,2  
Dense Layer 2048x1  
Dropout 0,4    
Dense Layer 2x1    
--> 90,96

# Iteration 13
Remove all dropout except for dense layer  

Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
  
Dense Layer 2048x1  
Dropout 0,4    
Dense Layer 2x1    
-->95,34%

# Iteration 13
Increase epochs from 10 to 20  
with and without data augment:  
with:
Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Dropout 0,2  
Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
Dropout 0,2  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
  
Dense Layer 2048x1  
Dropout 0,4    
Dense Layer 2x1    
-->

without:
Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
  
Dense Layer 2048x1     
Dense Layer 2x1    
-->94,52%

without with simple dropout:  
Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
  
Dense Layer 2048x1  
Dropout 0,4    
Dense Layer 2x1    
--> 94,63%

without with more dropout:  
Aufbau:  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Dropout 0,2   

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
Dropout 0,2   

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
  
Dense Layer 2048x1  
Dropout 0,4    
Dense Layer 2x1    
--> 95,71%

without with more dropout + additional input dropout:  
Aufbau:  
dropout 0,2  
Conv Layer 32 Filter 3x3  
Conv Layer 32 Filter 3x3  
Dropout 0,2   

Conv Layer 64 Filter 3x3  
Conv Layer 64 Filter 3x3  
Dropout 0,2   

Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
Conv Layer 128 Filter 3x3  
  
Dense Layer 2048x1  
Dropout 0,4    
Dense Layer 2x1    
--> 91,21%