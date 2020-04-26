[![Logo](/img/vex_snippets_logo.png)](https://github.com/Kuchavo/VEX-Snippets)

# VEX-Snippets
A collection of useful snippets for Houdini.

⚠️ **Сurrently repository in development.**

## Geometry

### Objects

<details>
<summary>View contents</summary>

* [`helixCurve`](#helixcurve)

</details>

### Primitives

<details>
<summary>View contents</summary>

* [`nGonsVisualize`](#ngonsvisualize)
* [`ToTestAPrimitiveGroupMembership`](#totestaprimitivegroupmembership)
* [`PrimitivesInGroupCounter`](#primitivesingroupcounter)
* [`PrimitivesListInGroup`](#primitiveslistingroup)
* [`PrimitiveGroupsList`](#primitivegroupslist)

</details>

### Vertices

<details>
<summary>View contents</summary>

* [`ToTestAVertexGroupMembership`](#totestavertexgroupmembership)
* [`VerticesInGroupCounter`](#verticesingroupcounter)
* [`VerticesListInGroup`](#verticeslistingroup)
* [`VertexGroupsList`](#vertexgroupslist)

</details>

### Points

<details>
<summary>View contents</summary>

* [`sortOfRingPoints`](#sortofringpoints)
* [`inCenterOfPrimitives`](#incenterofprimitives)
* [`pointsInAGroup`](#pointsinagroup)
* [`ToTestAPointGroupMembership`](#totestapointgroupmembership)
* [`PointsInGroupCounter`](#pointsingroupcounter)
* [`PointsListInGroup`](#pointslistingroup)
* [`inCenterOfPrimitives`](#sortofringpoints)
* [`PointGroupsList`](#pointgroupslist)

</details>

### Camera

<details>
<summary>View contents</summary>

* [`cutGeoFromCamera`](#cutgeofromcamera)
* [`silhouetteRetain`](#silhouetteretain)

</details>

### Arrays

<details>
<summary>View contents</summary>

* [`createAnArray`](#createanarray)
* [`generateAnArray`](#generateanarray)
* [`iteratingOverArrayElements`](#iteratingoverarrayelements)

</details>

### Groups

<details>
<summary>View contents</summary>

* [`createAGroup`](#createagroup)
* [`pointsInAGroup`](#pointsinagroup)
* [`ToTestAPointGroupMembership`](#totestapointgroupmembership)
* [`ToTestAPrimitiveGroupMembership`](#totestaprimitivegroupmembership)
* [`ToTestAVertexGroupMembership`](#totestavertexgroupmembership)
* [`PointsInGroupCounter`](#pointsingroupcounter)
* [`PrimitivesInGroupCounter`](#primitivesingroupcounter)
* [`VerticesInGroupCounter`](#verticesingroupcounter)
* [`PointsListInGroup`](#pointslistingroup)
* [`PrimitivesListInGroup`](#primitiveslistingroup)
* [`VerticesListInGroup`](#verticeslistingroup)
* [`PointGroupsList`](#pointgroupslist)
* [`PrimitiveGroupsList`](#primitivegroupslist)
* [`VertexGroupsList`](#vertexgroupslist)
* [`EdgeGroupsList`](#edgegroupslist) 

</details>

---

### createAGroup

Create a group.

```c
// Creation of group called 'mask' (@group_ is a virtual attribute)
  i@group_mask = 1;
```

```c
// Creation of group 'mygroup' for each point [Point Wrangle]
  setpointgroup(0, "mygroup", @ptnum, 1);
```

```c
// Creation of group 'mygroup' for each primitive [Primitive Wrangle]
  setprimgroup(0, "mygroup", @primnum, 1);
```

```c
// Creation of group 'mygroup' for each vertex [Vertex Wrangle]
  setvertexgroup(0, "mygroup", @primnum, 1);
```

```c
// Creation of group 'mygroup' for each edge between
// @primnum and @primnum+1 [Attribute Wrangle with Edges Group Type]
  setedgegroup(0, "mygroup", @primnum, @primnum+1, 1);
```
<details>
<summary>Example</summary>

<img src="/img/createAGroup_setedgegroup.png" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### PointsInGroupCounter

Shows how many elements in a group.

```c
// Points in a group ('mygroup') counter [Point Wrangle]
  i@count = npointsgroup(0, 'mygroup');
```

<br>[⬆ Back to top](#geometry)

### PrimitivesInGroupCounter

Shows how many elements in a group.

```c
// Points in a group ('mygroup') counter [Point Wrangle]
  i@count = nprimitivesgroup(0, 'mygroup');
```

<br>[⬆ Back to top](#geometry)

### VerticesInGroupCounter

Shows how many elements in a group.

```c
// Points in a group ('mygroup') counter [Point Wrangle]
  i@count = nverticesgroup(0, 'mygroup');
```

<br>[⬆ Back to top](#geometry)

### PointGroupsList

Returns a string array of existing point groups.

```c
// Array of existing point groups
  s[]@list = detailintrinsic(0, 'pointgroups');
```
<br>[⬆ Back to top](#geometry)

### PrimGroupsList

Returns a string array of existing primitive groups.

```c
// Array of existing primitive groups
  s[]@list = detailintrinsic(0, 'primitivegroups');
```
<br>[⬆ Back to top](#geometry)

### VertexGroupsList

Returns a string array of existing vertex groups.

```c
// Array of existing vertex groups
  s[]@list = detailintrinsic(0, 'vertexgroups');
```
<br>[⬆ Back to top](#geometry)

### EdgeGroupsList

Returns a string array of existing edge groups.

```c
// Array of existing edge groups
  s[]@list = detailintrinsic(0, 'edgegroups');
```
<br>[⬆ Back to top](#geometry)

### PointsListInGroup

Creation of list of points numbers in a group.

```c
// List of points in a group [Point Wrangle]
  i[]@list = expandpointgroup(0, 'mygroup');
```

<br>[⬆ Back to top](#geometry)

### PrimitivesListInGroup

Creation of list of primitives numbers in a group.

```c
// List of primitives in a group [Primitive Wrangle]
  i[]@list = expandprimgroup(0, 'mygroup');
```

<br>[⬆ Back to top](#geometry)

### VerticesListInGroup

Creation of list of vertices numbers in a group.

```c
// List of primitives in a group [Vertex Wrangle]
  i[]@list = expandvertexgroup(0, 'mygroup');
```

<br>[⬆ Back to top](#geometry)

### createAnArray

Create an array.

```c
// Local integer array of size 5
  int array[] = {0,1,2,3,4};
```

```c
// Global string array of size 2
  s[]@array = {'example_0.rat', 'example_1.rat'};
```

```c
// Local string array of size 2
  string array[] = {'example_0.rat', 'example_1.rat'};
```

<br>[⬆ Back to top](#geometry)

### generateAnArray

Generate an array.

```c
// Procedurally generated array of size 10
  i[]@myarray;
  for(int i=0; i<10; i++){
      append(@myarray, i);
  }
// Output: [ 0,1,2,3,4,5,6,7,8,9 ]
```

```c
// Procedurally generated vector array of size '@numpt'
    v[]@myarray;
    for(int i=0; i<@numpt; i++){
        vector item = point(0, 'P', i);
        insert(@myarray, 0, item);
    }
// Output: [ (4.24242, 0.0, 5.0), (3.53535, 0.0, 5.0), etc. ]
```

<br>[⬆ Back to top](#geometry)

### iteratingOverArrayElements

Iterating over array elements (every second).

```c
// Need listing input primitive numbers on detail
    int importarray[] = detail(0, 'prims');
    foreach(int i; importarray){
        if(i%2 == 0){
            setprimattrib(0, 'Cd', i, {0,1,0.2});
        }
    }

```

<details>
<summary>Example</summary>

<img src="/img/iteratingOverArrayElements.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### nGonsVisualize

Visualize of n-gons on geometry.

```c
// Visualize of n-gons on geometry [Primitive Wrangle]
  if (primvertexcount(0, @primnum) < 4){
    @Cd = set(0, 1, 0.2);
  }
```

<details>
<summary>Example</summary>

<img src="/img/nGonsVisualize.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### helixCurve

Creation of helix from curve.

```c
// Creation of helix from curve [Point Wrangle]
  float freq, amp;
  vector pos = @P;

  freq = chf("freq");
  amp = chf("amp");

  pos.x += sin(pos.y * freq) * amp;
  pos.z += cos(pos.y * freq) * amp;
  @P = pos;
```

<details>
<summary>Example</summary>

<img src="/img/helixCurve.jpg" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

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

### ToTestAPrimitiveGroupMembership

Returns a boolean value whether a primitive is a member of specified group.

```c
// Primitive in a group [Primitive Wrangle]
  i@ismember = inprimgroup(0, "group1", @primnum);
```

<details>
<summary>Example</summary>

<img src="/img/prim_ToTestAPrimitiveGroupMembership.png" width="2000px;"/>

</details>

<br>[⬆ Back to top](#geometry)

### ToTestAVertexGroupMembership

Returns a boolean value whether a vertex is a member of specified group.

```c
// Vertex in a group [Vertex Wrangle]
  i@ismember = invertexgroup(0, "group1", @vtxnum);
```

<details>
<summary>Example</summary>

<img src="/img/vtx_ToTestAVertexGroupMembership.png" width="2000px;"/>

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
