# Explanation

Fixed circle of radius R.
Other circle of radius r, rolling around the outside or the inside of the previous circle.
We are interested in the position of a point situated at distance d of the center of the second circle.

# Hypocycloid (r=d)

x(theta) = (R-r)cos(theta) + r.cos[theta.(R-r)/r]
y(theta) = (R-r)sin(theta) - r.sin[theta.(R-r)/r]

or, with k=R/r

x(theta) = r(k-1)cos(theta) + r.cos[theta.(k-1)]
y(theta) = r(k-1)sin(theta) - r.sin[theta.(k-1)]

Closed curves if k is rational.

# Epicycloid (r=d)

x(theta) = (R+r)cos(theta) - r.cos[theta.(R+r)/r]
y(theta) = (R+r)sin(theta) - r.sin[theta.(R+r)/r]

or, with k=R/r

x(theta) = r(k+1)cos(theta) - r.cos[theta.(k+1)]
y(theta) = r(k+1)sin(theta) - r.sin[theta.(k+1)]

Closed curves if k is rational.

# Hypotrochoid

x(theta) = r(k-1)cos(theta) + d.cos[theta.(k-1)]
y(theta) = r(k-1)sin(theta) - d.sin[theta.(k-1)]

Closed curves if k is rational.

# Epitrochoid

x(theta) = r(k+1)cos(theta) - d.cos[theta.(k+1)]
y(theta) = r(k+1)sin(theta) - d.sin[theta.(k+1)]

Closed curves if k is rational.

