# 鼠标跟随
```c#
 Vector3 p = Camera.main.ScreenToWorldPoint(Input.mousePosition);
        p.z = 0f;
        transform.localPosition = p;
```
