[![Logo](/img/vex_snippets_logo.png)](https://github.com/Kuchavo/VEX-Snippets)

# VEX-Snippets
A collection of useful snippets for Houdini.

⚠️ **Сurrently repository in development.**

## Geometry

### Points

<details>
<summary>View contents</summary>

* [`inCenterOfPrimitives`](#incenterofprimitives)
* [`pointsInAGroup`](#pointsinagroup)
* [`ToTestAPointGroupMembership`](#totestapointgroupmembership)
* [`inCenterOfPrimitives`](#sortofringpoints)


</details>

### Camera

<details>
<summary>View contents</summary>

* [`cutGeoFromCamera`](#cutgeofromcamera)
* [`silhouetteRetain`](#silhouetteretain)

</details>

---

### sortOfRingPoints

Sorting circle points.

```c
//Sorting points in a circle (z and y axis) [Point Wrangle]
vector center = getbbox_center(0);
@P -= center;
@grad = atan2(@P.z,@P.y);
@P += center;
// After that needing sort by attribute 'grad'
```

<details>
<summary>Example</summary>

<img src="/img/sortOfRingPoints.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

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

### pointsInAGroup

Assigning a point to a group. If points’ position on X axis is more than 0, assign the point to the “mygroup”.

```c
// Points in a group [Point Wrangle]
  if(@P.x>0) @group_mygroup = 1;
```

<details>
<summary>Example</summary>

<img src="/img/point_pointsInAGroup.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### ToTestAPointGroupMembership

Returns a boolean value whether a point is a member of specified group.

```c
// Points in a group [Point Wrangle]
  i@ismember = inpointgroup(0, "group1", @ptnum);
```

<details>
<summary>Example</summary>

<img src="/img/point_ToTestAPointGroupMembership.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### cutGeoFromCamera

Cut geometry from selected camera with the ability to crop.

```c
// Camera Frustrum [Point Wrangle]
vector pos = toNDC("/obj/cam1", @P);
if (pos.x < 0+ch('overLeft')) removepoint(0, @ptnum);
if (pos.x > 1-ch('overRight')) removepoint(0, @ptnum);
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
