# Ryanair Python

This module allows you to retrieve the cheapest flights, with/out return flights, within a fixed set of dates.  
This is done directly through Ryanair's API, and does not require an API key.  
### Installation
Run the following command in the terminal:
```
pip install ryanair-py
```
### Initialisation
Creating an instance is done as follows:
```python
from ryanair import Ryanair
ryanair = Ryanair("EUR")  # Euro currency, so could also be GBP etc. also
```
### Get one-way flights
```python
flights = ryanair.getFlights("DUB", "2022-10-27", "2022-10-30")
```
Returns an array of Flight objects, like this:
```python
flights[0] # Flight(origin='DUB', originFull='Dublin, Ireland', destination='MAN', destinationFull='Manchester, United Kingdom', departureTime='2022-10-30T06:25:00', price=9.78)
cheapestFlightPrice = flight.price # price is now a float containing the price (in the unit of currency originally declared earlier) of this flight
```
### Get return flights
```python
trips = ryanair.getReturnFlights("DUB", "2022-10-27", "2022-10-30", "2022-11-01", "2022-11-03")
```
Returns an array of Trip objects, like this:
```python
trips[0] # Trip(outbound=Flight(origin='DUB', originFull='Dublin, Ireland', destination='LPL', destinationFull='Liverpool, United Kingdom', departureTime='2022-10-30T20:50:00', price=9.99), inbound=Flight(origin='LPL', originFull='Liverpool, United Kingdom', destination='DUB', destinationFull='Dublin, Ireland', departureTime='2022-11-01T08:25:00', price=18.51), totalPrice=28.5)
trips[0].outbound.price # 9.99
trips[0].totalPrice # 28.5
```
