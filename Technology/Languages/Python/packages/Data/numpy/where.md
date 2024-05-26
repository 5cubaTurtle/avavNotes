#numpy

Given image `img` set all pixels to *1* where the pixel is `>=` `intensity_threshold`. Otherwise set it to *0*.
```python
thresh_image = np.where(img >= intensity_threshold, 1, 0)
```
