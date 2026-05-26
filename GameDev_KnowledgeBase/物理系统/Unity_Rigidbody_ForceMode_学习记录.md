# AddForce 四种模式学习过程记录

我询问了：

“为什么 AddForce 的 ForceMode 要分四种，它们之间的区别是什么？”

你为我解释了：

- Force / Acceleration 属于持续施力
- Impulse / VelocityChange 属于瞬间速度变化
- Force 与 Impulse 受质量影响
- Acceleration 与 VelocityChange 不受质量影响

并说明：

Force / Acceleration 更适合持续调用，
Impulse / VelocityChange 更适合单次触发。

------

随后我提出疑问：

“为什么在 Button 输入里，
Force / Acceleration 几乎看不到效果，
而另外两个模式单击就有效？”

你解释了：

因为：

- Force / Acceleration 每次只会增加一小段速度
- 需要在 FixedUpdate 中持续调用才能明显加速
- 而 Impulse / VelocityChange 会一次性产生较大的速度变化

------

随后我继续追问：

“明明 AddForce 第一个参数填写的是同一个数值，
为什么一个模式需要持续调用，
另一个单次就有效？
Unity 是否自动帮我把力拆分了？”

你解释了：

不是 Unity 自动拆分。

而是：

不同 ForceMode 对“参数”的解释不同。

例如：

Force：

```text
速度变化 = 力 × fixedDeltaTime
```

所以单次效果很小。

Impulse：

```text
直接改变一次速度
```

因此单次效果明显。

------

之后我继续询问：

“Force / Acceleration 长按时，
是否会和另外两种模式单击效果类似？”

你解释：

不会。

因为：

Force / Acceleration 本质是：

```text
持续增加加速度
```

因此会不断累加 velocity。

长按会：

```text
越来越快
```

而不是只保持固定速度。

------

随后我再次追问：

“为什么会越来越快？
函数每次调用不都是同一个力吗？”

你解释了：

力不是速度。

力作用的是：

```text
加速度
```

而加速度会持续改变 velocity。

真正过程：

```text
Force
↓
Acceleration
↓
Velocity
↓
Position
```

因此：

持续 AddForce 相当于：

```text
velocity += Δv
velocity += Δv
velocity += Δv
```

所以速度不断累计。

------

之后我开始询问 Drag（Linear Damping）：

“Drag 是否是阻力？
如果速度小于阻力，
物体会不会被反推回去？”

你解释：

Unity 的 Drag 本质不是“反向固定力”，
而是：

```text
速度衰减
```

它只会：

- 逐渐降低已有速度
- 不会让速度反向
- 不会把物体推回去

------

随后我继续追问：

“所以 Drag 是否只会作用于已经有速度的物体？
真正推不动的原因，
是不是因为摩擦力大于施加力，
而不是 Drag 太大？”

你解释：

是的。

真正导致：

```text
“推不动”
```

的是：

```text
静摩擦力 > 施加力
```

而 Drag：

只是：

```text
对已有速度进行衰减
```

它不会阻止物体开始运动。