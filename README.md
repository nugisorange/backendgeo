# backendgeo

# backendgis
backend golang geospatial

Package backend golang framework gin

PostGeoIntersects
{
    "type": "Point",
    "coordinates": [107.69149817457176, -6.907773272169891]
}
{
    "type": "LineString",
    "coordinates": [
        [107.63091641571147, -6.6020024943709927],
        []
    ]
}
{ "type": "Polygon", "coordinates": [ [ [ 107.69161532452927, -6.909192149952432], [107.6928270495055, -6.909088574785045], 
[ 107.69101448076144, -6.90926005434234], [ 107.69161532452927, -6.909192149952432 ] ] ] }

## PostGeoWithin
{ "type": "Polygon", "coordinates": [ [ [103.62892373959272, -1.616812371154296], [103.62890068598779, -1.616866839799556], [103.62896041578165, -1.616890931699615], [103.62898556516905, -1.6168364630550514], [103.62892373959272, -1.616812371154296] ] ] }

```
db.cijambe.find( {
  geometry: { $geoWithin: { $centerSphere: [ [ 107.69097557248074, -6.911454757425261 ], 10/0.003 ] } }
} ,{"properties":1,"geometry.type":1, "_id":0 }
).count()
```

## PostNear

{ "type": "Point", "coordinates": [103.6037314895799, -1.632582001101999], "max": 100, "min": 1 }
//mongosh

```
db.cijambe.find(
   {
     geometry:
       { $near :
          {
            $geometry: { type: "Point",  coordinates: [ 107.691464975053, -6.908710387370377 ] },
            $minDistance: 2,
            $maxDistance: 33
          }
       }
   },{"properties.nama":1, "_id":0}
).toArray()
```

## PostNearSphere
{ "type": "Point", "coordinates": [103.6037314895799, -1.632582001101999], "max": 100, "min": 1 }

```
db.cijambe.find(
   {
     geometry:
       { $near :
          {
            $geometry: { type: "Point",  coordinates: [ 107.691464975053, -6.908710387370377 ] },
            $minDistance: 2,
            $maxDistance: 33
          }
       }
   },{"properties.nama":1, "_id":0}
).toArray()
```


## PostBox
{ "coordinates": [ [103.54786554087926, -1.6487359545296698], [103.62772892345659, -1.6034217927083034] ] }

## PostCenter
{ "coordinates": [103.62074450557095, -1.632735059500547], "radius": 0.003 }

## PostCenterSphere
{ "coordinates": [103.62074450557095, -1.632735059500547], "radius": 0.00003 }

## minDistance 
digunakan untuk menentukan titik kordinat yang menjadi titik pusat.

## maxDistance
Digunakan untuk mengatur jarak maksimal antara titik koordinat dan titik pusat.   
Digunakan untuk menentukan jarak maksimal dari titik koordinat ke titik pusat. 

## Center
Digunakan untuk mengatur koordinat titik pusat dari lingkaran yang dibuat dengan `PostCenter`.

## Box
Digunakan untuk membuat lingkaran sebagai box yang dipilih oleh parameter `coordinates` dan `PostBox`. Parameter ini digun 
Digunakan untuk membuat lingkaran. Koordinat awal dan akhir box digunakan sebagai garis dasar lingkaran yang akan dibuat.

## Geometry
Untuk memilih atau menentukan suatu operator geometri geojson yang ingin dipakai, operator diantaranya geoIntersect,geowithin, geonear. bisa digunakan `geometry=point` atau `geometry=linestring`, dan lainnya.

## Near vs NearSphere
`$near` digunakan untuk mencari data yang berada dalam suatu bangun datar yang ditentukan oleh parameter `$geometry`, sedangkan `$nearSphere` digunakan untuk mencari data yang diluar dalam suatu titik pusat.

`$near` digunakan untuk membuat query yang cocok dengan titik koordinat yang terdekat. Sedangkan `$nearsphere` digunakan untuk membuat query yang cocok.

