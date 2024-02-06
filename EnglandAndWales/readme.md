# Sample Usage

```python
import numpy as np
from measles import data as engwal

engwal.placenames   # Place names, each is a key in measles.data.places
engwal.years        # Years for population and birth information, two digits: 44...64
engwal.reports      # Dates (decimal years) for case information, e.g., 44.11538 == day 42 of 1944
# engwal.places       # Per-place information - see below

# Each place has:
#   population: array of integers, one per year - see above
#   births: array of integers, one per year - see above
#   cases: array of integers, one per reporting data - see above
#   latitude: scalar float
#   longitude: scalar float

for placename, place in engwal.places.items():
    lat, long = place.latitude, place.longitude
    print(f"{placename}: ({lat},{long})")


york = engwal.places["York"]
york.population

"""
array([ 94740,  96700, 102050, 102250, 103700, 104600, 107700, 105200,
       105800, 105200, 106600, 106500, 106200, 106120, 105600, 104900,
       104120, 104570, 104890, 104250, 105230], dtype=uint32)
"""

york.births

"""
array([2035, 1803, 2121, 2304, 1903, 1810, 1740, 1549, 1560, 1557, 1558,
       1546, 1590, 1608, 1660, 1679, 1716, 1800, 1724, 1771, 1829],
      dtype=uint32)
"""

distances = np.load("distances.npy")
i = engwal.placenames.index("Aberayron") # Should be 0
j = engwal.placenames.index("York")      # Should be 953

print(f"Distance between Aberayron [{i}] and York [{j}] is {distances[i,j]} kilometers.")
```
