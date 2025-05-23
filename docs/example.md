# Example Usage
```python
from meteor_py import *
import sys
from numpy import datetime64


start_date   =  datetime64('2023-01-01', 'ns') 
end_date     = datetime64('2024-01-01', 'ns') 

weatherdata = WeatherData(
    date = (start_date,end_date),
    location= 'your_location', 
    wind = True,
    solar = True, 
    interval = 3600,
    n_samp = 100, 
    sample_type = "Structured",
    latitudes =(float(sys.argv[1]), float(sys.argv[2])), 
    longitudes =(float(sys.argv[3]),float(sys.argv[4])),
    environment_login=True
    )


renewableenergy = RenewableEnergy(
    weatherdata,
    [
        (0, 0.0),       # These are points along the power curve.
        (3, 0.0),       # are used in the output curve.
        (4, 0.648),     # Wind speeds are in [m/s].
        (5, 1.4832),
        (6, 2.736),
        (7, 4.4676),
        (8, 6.7104),
        (9, 9.3168),
        (10, 11.2392),
        (11, 11.8008),
        (12, 11.8728),
        (13, 11.88),
        (30, 11.88),
    ]
)

renewableenergy.export_power(weatherdata,name='file_name', dates=False)

```

