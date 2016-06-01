Python
======

PIL
---

http://pillow.readthedocs.io/en/3.2.x/reference/Image.html

Loading images, saving images, converting between PIL and numpy:

```python
from PIL import Image
import numpy as np

img = Image.open('input.png')
img.save('output.png')

img_array = np.asarray(img)
img_new = Image.fromarray(img_array)
```

Resizing and cropping images:

```python
from PIL import Image

img = Image.open('input.png')
img_resized = img.resize((width, height), Image.ANTIALIAS)
img_cropped = img.crop((left, upper, right, lower))
```

Drawing bounding box/polygon on an image:

```python
from PIL import Image, ImageDraw

img1 = Image.open('input.png')
draw1 = ImageDraw.Draw(img1)
draw1.rectangle([(x1, y1), (x2, y2)], outline='yellow')
img1.save('output1.png')

img2 = img1.copy()
draw2 = ImageDraw.Draw(img2)
draw2.polygon([(x1, y1), (x2, y2), (x3, y3)], outline='RGB(255,255,0)')
img2.save('output2.png')
```

http://effbot.org/imagingbook/imagedraw.htm

XML
---

`untangle` module:

```xml
<?xml version="1.0"?>
<root>
    <child>
      <subchild name="first">some content</subchild>
    </child>
    <child>
      <subchild name="second">more content</subchild>
    </child>
</root>
```

```python
import untangle
obj = untangle.parse('path/to/file.xml')
obj.root.child[0].subchild['name'] # => "first"
obj.root.child[1].subchild.cdata # => "more content"
```

http://docs.python-guide.org/en/latest/scenarios/xml/
