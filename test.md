# Constrained triangulation
PSLG = (S, L)

```
Incremental CT (S, L)
    init a T[0] of (S, )
    for i = 1 to K do 
        insert Si belong to L into T[i-1]
    endfor
```

(1) Retriangulate a Simple polygon.

    Ear-clipping ———— a locally convex vertex of P is an ear.

(2) Insert a line segment by edge flips

    Find a locally convex vertex P[i]
    flip all crossing edges at P[i]

# Constrained Delaunay triangulation (CDT)
                developed by Lee & Lin 1986, Chew 1989

Given a PSLG (S, L), 
two points x, y are visible from each other, if xy shares no interior points of (S, L).

Atriangle in a CT of (S, L) is constrained Delaunay if its circumcircle is either empty or it contains 
no other vertices which are visible from its interior.

A constrained triangulation of (S, L) is a **constrained Delaunay trianngulation** if every triangle of 
T is constrained Delaunay.

Let K be a CT of (S, L), an edge ab belongs to K is locally Delaunay if:
* ab is on the convex hull
* abc, abd belongs to K, and d lies outside Oabc
* ab belongs to L

*Thm.* Constrained Delaunay Lemma:
    If all edges of K is locally Delaunay, the K is the CDT of (S, L).

Lawson's flip algorithm to construct CDT.
```
    while exits e, e is not locally Delaunay, do 
        flip;
    endwhile
```

+ If S is ingeneral position, CDT is unique.
+ The CDT maximize th miminum angle of all CT of (S, L)
+ The flip graph of all CTs is connected

# Mesh Refinement
Basic requirement of Quality Meshing Algorithms
+ A good mesh should thn try to obtain a good compromise between different criteria, 
    preserving the accuracy of the solution at a reasonable computational effort.
+ The basic requirement of quality meshing algorithms are:
   + (Boundary preservation) ability to preserve domain boundaries.
   + (Mesh quality) ability to gene

