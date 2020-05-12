# AnvilAugment

A dependency for adding custom jQuery events to any anvil component

[<img src="https://anvil.works/img/forum/copy-app.png" height='40px'>](https://anvil.works/build#clone:36T6RN2OO6KLBGV7=4LZ35S57ODPL7ORIUJ2AH6KY|223FMU5UYH5T2XSA=UYJICI36SETZB4DPFRHCKMVA)


### Examples:

```python
from AnvilAugment import augment
augment.set_event_handler(self.link, 'hover', self.link_hover)
# equivalent to
# augment.set_event_handler(self.link, 'mouseenter', self.link_hover)
# augment.set_event_handler(self.link, 'mouseleave', self.link_hover)
# or 
# augment.set_event_handler(self.link, 'mouseenter mouseleave', self.link_hover)

def link_hover(self, **event_args):
  if 'enter' in event_args['event_type']:
    self.link.text = 'hover'
  else: 
    self.link.text = 'hover_out'

#================================================
# augment.set_event_handler equivalent to
augment.add_event(self.button, 'focus')
self.button.set_event_handler('focus', self.button_focus)

def button_focus(self, **event_args):
 self.button.text = 'Focus'
 self.button.role =  'secondary-color'

```

---

## need a trigger method?

```python
# 'augment' the component by adding any event... 
augment.add_event(self.textbox, 'select')
# augment.add_event(self.textbox, 'custom')
# augment.add_event(self.textbox, '')

def button_click(self, **event_args):
  self.textbox.trigger('select')
```

---

### Keydown example

```python
augment.set_event_handler(self.text_box, 'keydown', self.text_box_keydown)

def text_box_keydown(self, **event_args):
  key_code = event_args.get('key_code')
  key = event_args.get('key')
  if key_code == 13:
    print(key, key_code)
```

---

*advanced feature - you can prevent default behaviour of an event by returning a value in the event handler function - example use case*


```python
augment.set_event_handler(self.text_area, 'keydown', self.text_area_keydown)

def text_area_keydown(self, **event_args):
  key = event_args.get('key')
  if key.lower() == 'enter':
    # prevent the standard enter new line behaviour
    # prevent default
    return True
```

---
