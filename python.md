Python
======

argparse
--------

Parse command line arguments.

```bash
python myprogram.py foo 42 --arg3 bar
```

```python
import argparse

parser = argparse.ArgumentParser(description='description of program')
parser.add('arg1', help='required string positional argument 1')
parser.add('arg2', type=int, help='required integer positional argument 2')
parser.add('--arg3', help='optional argument')
args = parser.parse_args()

print args.arg1 # => foo
print args.arg2 # => 42
if not args.arg3:
    print args.arg3 # => bar
```

CSV
---

Can change delimiter and quoting options: https://docs.python.org/2/library/csv.html

```csv
field1    field2    field3
foo       ba'r       ba"z
...
```

```python
import csv

with open('file.csv', 'r') as f:
    reader = csv.reader(f, delimiter='\t', quoting=csv.QUOTE_NONE)
    for row in reader:
        print row # => ('field1', 'field2', 'field3'), ('foo', "ba'r", 'ba"z'), ...
```

JSON
----

https://docs.python.org/2/library/json.html

```python
try:
    import simplejson as json
except ImportError:
    import json

# load JSON file
with open('input.json', 'r') as f:
    data = json.load(f)

# write to file: compact encoding
with open('compact.json', 'w') as f:
    json.dump(data, f, separators=(',',':'))

# write to file: pretty printing
with open('pretty.json', 'w') as f:
    json.dump(data, f, sort_keys=True, indent=4, separators=(',', ': '))
```

\_\_main\_\_
------------

```python
def do_stuff():
    pass

if __name__ == "__main__":
    do_stuff()
```

> One of the reasons for doing this is that sometimes you write a module (a .py file) where it can be executed directly. Alternatively, it can also be imported and used in another module. By doing the main check, you can have that code only execute when you want to run the module as a program and not have it execute when someone just wants to import your module and call your functions themselves.

http://stackoverflow.com/questions/419163/what-does-if-name-main-do

PIL
---

```bash
pip install Pillow
```

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

```bash
pip install untangle
```

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

zip
---

Aggregate elements from each iterable:

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# zip
list_zip = zip(list1, list2)
print(list_zip) # => [(1, 4), (2, 5), (3, 6)]

# unzip
list1_unzip, list2_unzip = zip(*list_zip)
print(list1_unzip) # => [1, 2, 3]
print(list2_unzip) # => [4, 5, 6]
```
