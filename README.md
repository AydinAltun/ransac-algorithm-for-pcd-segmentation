# ransac-algorithm-for-pcd-segmentation
In this repository, a pcd data is tried to segementated by ransac algotirhm
Ransac stands for RANdom Sampling and Consensus, Its a robust model fitting algorithm

In this case, we are going to use RANSAC algorithm on Lidar point cloud(pcd) data to segment the ground plane from the other planes which could consist of vehicles, traffic-lights, or anything above the ground plane which needs to be classified for avoiding collision or for trajectory planning.

In this particular application RANSAC is preferred for ground plane segmentation due to inherent property to reject outliers. (Outliers can be considered as unusual observations which are likely to be rejected)

There are several steps these need to be done

Step 1: Select a random set of points (Three points will be enough to create a plane)
>Plane equation: ax + by + cz + d = 0

if these three points are provided them the constant a,b,c and d can be derived using the following formula.

Step 2: Calculate the parameters for the plane equatios
> a = [(y2 -y1)(z3 - z1) - (z2 - z1)(y3 - y2)]
> > b = [(z2 -z1)(x3 - x1) - (x2 - x1)(z3 - z2)]
> > > c = [(x2 -x1)(y3 - y1) - (y2 - y1)(x3 - x2)]

Step 3: Calculate the deviation of all the points in the point cloud from the plane using a distance estimate.

distance = (ax4 + by4 + cz4 + d)/(sqrt(a^2 + b^2 + c^2)

Step 4:  If the distance is within the THRESHOLD then add the point as an inlier otherwise it is outliers.

Step 5: Store the plane points and points having maximum number of inliers

Step 6: Repeat the process again for max_iteration.

These the total summary of Ransac Algortihm.
