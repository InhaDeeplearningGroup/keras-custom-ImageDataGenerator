# keras_custom_ImageDataGenerator

This is custom ImageDataGenerator especially flow_from_directory API.

I modified the last class named DirectoryIterator.

```python
class DirectoryIterator(Iterator):
	...
    def __init__(self, ...):
    
    ...
    
    def next(self):
    
    ... (modified) ...
    
```

You can use as follow.

```python
import keras.preprocessing.image import ImageDataGenerator

train_datagen = ImageDataGenerator(
	horizontal_flip=True,
    ...
    )
train_generator = train_datagen.flow_from_directory(
	'%s/train/', %ds,
    target_size=(224, 224),
    batch_size=batch_size,
    class_mode="colorization")  # this is my custom colorization class model.
    
model.fit_generator(
	train_generator,
    steps_per_epoch=train_generator.samples // batch_size,
    ...
    )
    
```

In this way, you can make various types of custom Iterator using Keras.

## TODO list

- [x] Custom DirectoryIterator class
- [ ] Detailed example code

