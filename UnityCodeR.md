# 鼠标跟随
```c#
 Vector3 p = Camera.main.ScreenToWorldPoint(Input.mousePosition);
        p.z = 0f;
        transform.localPosition = p;
```
# 用对象创建对象
```c#
  GameObject e = Instantiate(Resources.Load("AnotherEgg") as GameObject); // Prefab MUST BE locaed in Resources/Prefab folder!
            e.transform.localPosition = transform.localPosition;
```
