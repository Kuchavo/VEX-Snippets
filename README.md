[![Logo](/vex_snippets_logo.png)](https://github.com/Kuchavo/VEX-Snippets)

# VEX-Snippets
A collection of useful snippets for Houdini.

⚠️ **Сurrently repository in development.**

## Geometry

### Points

<details>
<summary>View contents</summary>

* [`inCenterOfPrimitives`](#incenterofprimitives)

</details>

---

### inCenterOfPrimitives

Replacing primitives with points and adding points at each of their centers.

```c
//Points in center [Primitive Wrangle]
  addpoint(0,@P);
  removeprim(0,@primnum,0);
```

<details>
<summary>Example</summary>

<<<<<<< HEAD
<img src="/img/inCenterOfPrimitives.jpg" height="300px"/>
=======
<img src="/img/inCenterOfPrimitives.jpg" width="1000px;"/>
>>>>>>> 6106906d5c422eabdf3297370c4f4d7e760903ed

</details>

<br>[⬆ Back to top](#geometry)
