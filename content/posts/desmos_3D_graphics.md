---
title: "Desmos 3D Graphics"
date: 2024-11-17T15:16:13-08:00
draft: true
---

I have created, within the 2D desmos graphing calculator, a rendering of a rotating cube.

What follows is an explanation of the math I used.

The very first thing we need is the ability to project a point in the 3D world, onto a flat, 2D surface. The most obvious way of doing this is simply taking away one of the three coordinates, but this approach both literally and figuratively lacks depth(we will be unable to tell how far an object is).

Instead, to project a point onto the plane, we establish a vanishing point, call it V, and draw a plane(I drew it as the XY plane, with Z as depth). Then we simply draw a line from P, to V, and see where it crosses the plane. The math to find this point is as follows:

First we draw a line in 3D from P to V, we can do this with simple linear interpolation:
P(t-1)+V(t)

As the XY plane is defined by its presence at 0 on the Z-axis, the point where the aformentioned line crosses the XY is plane, is when the Z-component of the vector is 0, written mathematically as:
0=P.z(t-1)+V.z(t)

And once solved for t in terms of P and V:
t=P.z/(P.z+V.z)

And if you place this value for t back into the original linear interpolation function, and simplify, the projected point is at:
P.z(P+V)/(P.z+V.z)-P

As all these points lie perfectly upon the XY axis, we can ignore the Z-component and declare it projected.

All we must do then is write out the coordinates of the points on a cube, project them, and tell the calculator which points to connect when drawing its shapes.

That was the easy part.

Prepare for four-dimensional imaginary number multiplication.



Let's talk about the complex plane. A point in space could be represented as a 2D vector, for example:
(1,-2)

But said vector could also be expressed as a complex number:
1-2i

An interesting quirk of representing points this way, is that points can now be multiplied with other points, and we're going to focus on the fact that if you multiply any point, by a point of magnitude 1, you create a rotation of that point around the origin. But this only works in 2D.

The crux with representing the rotation of a 3D object is that we there isn't a way of doing it without encountering edge-cases where our methods don't work, and we wind up dividing by zero or doing some other heinous crime when we try to apply these rotations.

Fortunately for us, there just so happens to be a good way of doing just that, for the rotation of a 4D object. We call this, a quaternion. To provide an intuitive model, a rotation quaternion can be visualized as the combination of a 3D vector which defines the axis of rotation, and another scalar that defines how much we rotate upon said axis, together forming a 4D vector(magnitude of the entire, 4D vector, must be 1).

A Quaternion is, under the hood, a 4D complex number, where instead of just having i^2=-1, you also have j^2=-1, and k^2=-1. And there are rules as to how i, j, and k all multiply together. Interestingly enough, these rules are non-commutative, in other words, i * j is not equal to j * i.

As complex numbers can be used to represent points in 2D space, so to can quaternions be used to represent points in 4D space, which can be rotated in the same way as complex numbers can be. When trying to use quaternions on 3D points, we simply mark the position on the w-axis as 0, and ensure that the rotation quaternion has a magnitude of 1 when expressed as a vector. Naming the four elements of the quaternion, a,b,c, and d, we may then multiply our point by the quaternion:

(a,b,c,d)

Followed by a multiplication by:

(-a,b,c,d)

To preserve scale.

As a side note, there is an analog for a quaternion for all vectors whose dimensionality is a power of 2:
Complex Numbers(2)
Quaternions(4)
Octonions(8)
Sedenions(16)
and many more, collectively referred to as "hypercomplex numbers"

I pulled a few tricks to speed up computation that I shan't explore right now, if you're brave enough you can rummage through the arcane depths of the desmos graph itself, feel free to copy it, play around with it, change it, make it yours:

https://www.desmos.com/calculator/nznbf0oaln