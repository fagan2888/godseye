# Indian Pincode Mapping:

A Postal Index Number or PIN or PIN code is a code in the post office numbering or post code system used by India Post, the Indian postal administration. The code is six digits long.

We have developed a Simple Flask Application that can retrieve the Pincode of a location given it's Latitude and Longitude 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

The below mentioned packages have been used to succesfully implement this project 

```
pip install flask
pip install Shapely
pip install geopandas
pip install scipy
```

## Running the project

Clone the repository into your local system

```
git clone https://github.com/Sangarshanan/Pincode-Mapping.git
```

and run app.py 

```
python app.py
```
The flask application now runs in your localhost:5000

## How it works ?

We are using a combination of two different algorithms 

+ The First algorithm used to shapfiles of cities by dividing them into polygons where each polygon represents a pincode 
+ The Second algorithm uses Kdtrees to map a given latlong to the nearest latlong with a known pincode 

The Combination of both approaches gives us high accuracy for cities and passable accuracy other regions 

The Python function that makes it possible 

```python
def getpincode(lat , long):
    lat = float(lat)
    long = float(long)
    p = Point(long,lat)
    for i in range(0,len(data)):
        if p.within(data['geometry'][i]) is True:
            pin = int(data['pin_code'][i])
        else:
            pin = 0
    if pin !=0:
        return pin
    else:
        latlongs = np.array([lat,long])
        result = tree.query(latlongs)
        pin = int(data1.iloc[[result[1]]]['postalcode'])       
    return pin

```


## License

Check out the [LICENSE](LICENSE) file for details
      

