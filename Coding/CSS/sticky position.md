1. *sticky* elements are corporeal, they take up space. Elements around *sticky* elements will treat them as if they are in their natural position.
2. A *sticky* element *cannot* leave its DOM parent.
3. _top_ will only take effect when the result is *below its natural position*. i.e. it cannot move above where it naturally would be.
4. _bottom_ will only take effect when the result is *above its natural position*. i.e. it cannot move below where it naturally would be.
5. _left_,_right_ follow the same rule.