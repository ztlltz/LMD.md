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
```c#
        if(Input.GetKey(KeyCode.A)) {
            transform.Rotate(0,0, SpeedP * Time.smoothDeltaTime,Space.Self);//左转
        }
        if (Input.GetKey(KeyCode.D))
        {
            transform.Rotate(0, 0, -1*SpeedP * Time.smoothDeltaTime, Space.Self);//右转
        }
```
