First add `draggable=true` to any elements you wish to drag.

To monitor the drag process, you can listen for any of the following events:

- [`dragstart`](https://developer.mozilla.org/docs/Web/API/Document/dragstart_event)
- [`drag`](https://developer.mozilla.org/docs/Web/API/Document/drag_event)
- [`dragenter`](https://developer.mozilla.org/docs/Web/API/Document/dragenter_event)
- [`dragleave`](https://developer.mozilla.org/docs/Web/API/Document/dragleave_event)
- [`dragover`](https://developer.mozilla.org/docs/Web/API/Document/dragover_event)
- [`drop`](https://developer.mozilla.org/docs/Web/API/Document/drop_event)
- [`dragend`](https://developer.mozilla.org/docs/Web/API/Document/dragend_event)

To handle the drag flow, you need some kind of _source element (where the drag starts)_, the _data payload (the thing being dragged)_, and a _target (an area to catch the drop)_. The source element can be almost any kind of element. The target is the drop zone or set of drop zones that accepts the data the user is trying to drop. Not all elements can be targets. For example, your target can't be an image.