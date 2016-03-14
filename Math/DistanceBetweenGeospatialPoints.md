#How to calculate the distance between two geographical points (given with latitude and longitude)?

Source: Somewhere in the Internet ... 
		Not 100% sure: 

Source:
[Most likely source](https://stackoverflow.com/questions/120283/how-can-i-measure-distance-and-create-a-bounding-box-based-on-two-latitudelongi)
[Wikipedia for formular](https://en.wikipedia.org/wiki/Haversine_formula)
[Testreference](http://www.movable-type.co.uk/scripts/latlong.html)

I have it tested with one value. The accuracy is not as good as [Testreference],  but within a 5% margin. Should be fine. 

```Java
    public static double getDistance(double lat1, double lng1, double lat2, double lng2, double earthRadius) {
		//double earthRadius = 3958.75; // miles (or 6371.0 kilometers)
        double dLat = Math.toRadians(lat2-lat1);
        double dLng = Math.toRadians(lng2-lng1);
        double sindLat = Math.sin(dLat / 2.0);
        double sindLng = Math.sin(dLng / 2.0);
        double a = Math.pow(sindLat, 2.0) + Math.pow(sindLng, 2.0)
                * Math.cos(Math.toRadians(lat1)) * Math.cos(Math.toRadians(lat2));
        double c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));

        return earthRadius * c;
    }
```

The earth radius is passed as parameter to selected the unit system outside of the function. Could be also done inside, but is actually not necessary.











