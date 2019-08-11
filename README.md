[![Logo](/img/vex_snippets_logo.png)](https://github.com/Kuchavo/VEX-Snippets)

# VEX-Snippets
A collection of useful snippets for Houdini.

⚠️ **Сurrently repository in development.**

## Geometry

### Points

<details>
<summary>View contents</summary>

* [`inCenterOfPrimitives`](#incenterofprimitives)

</details>

### Camera

<details>
<summary>View contents</summary>

* [`cameraFrustrum`](#camerafrustrum)
* [`silhouetteRetain`](#silhouetteretain)

</details>

---

### inCenterOfPrimitives

Replacing primitives with points and adding points at each of their centers.

```c
// Points in center [Primitive Wrangle]
  addpoint(0,@P);
  removeprim(0,@primnum,0);
```

<details>
<summary>Example</summary>

<img src="/img/point_inCenterOfPrimitives.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### cameraFrustrum

Cut geometry from selected camera with the ability to crop.

```c
// Camera Frustrum [Point Wrangle]
vector pos = toNDC("/obj/cam1", @P);
if (pos.x < 0+ch('overleft')) removepoint(0, @ptnum);
if (pos.x > 1-ch('overright')) removepoint(0, @ptnum);
if (pos.y < 0+ch('overDown')) removepoint(0, @ptnum);
if (pos.y > 1-ch('overUp')) removepoint(0, @ptnum);
```

<details>
<summary>Example</summary>

<img src="/img/cam_cameraFrustrum.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### silhouetteRetain

Preserves the silhouette of the geometry in the selected camera, regardless of its distance.

```c
// Silhouette Retain [Point Wrangle]
vector pos = toNDC("/obj/cam1", @P);
pos.z += ch("offset");
@P = fromNDC("/obj/cam1", pos);
```

<details>
<summary>Example</summary>

<img src="/img/cam_silhouetteRetain.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)
