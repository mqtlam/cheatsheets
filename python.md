Python
======

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
