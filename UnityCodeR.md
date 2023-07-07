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
# 旋转
<img width="608" alt="image" src="https://github.com/ztlltz/LMD.md/assets/104620738/d40b65a8-d862-4630-9425-b69857b9e016">
