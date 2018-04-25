

```python
#Import Dependencies
import random
import json
import requests
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from citipy import citipy
```


```python
api_key = "a6aa2d81ae91031769840e1629729bb3"
base_url = "https://api.openweathermap.org/data/2.5/weather"
params = {
    "APPID": api_key
}
```


```python
#Set the limits for the random cities
latitude_min = -90
latitude_max = 90
longitude_min = -180
longitude_max = 180

#Loop through

latitude_list = []
longitude_list = []
city_list =[]
country_list = []
temp_list = []
humidity_list = []
cloudiness_list = []
wind_speed_list = []
date_list = []

x=0
while x < 500:
    rand_lat = random.uniform(latitude_min, latitude_max)
    rand_lon = random.uniform(longitude_min, longitude_max)
    city = citipy.nearest_city(rand_lat, rand_lon)

    params['q'] = city.city_name + ',' + city.country_code

    response_data = requests.get(base_url, params=params).json()

    if(response_data['cod'] == 200):
      
        city_list.append(city.city_name)
        print(city.city_name)
        
        country_list.append(city.country_code)
        print(city.country_code)
        
        temp = response_data["main"]["temp_max"]
        temp_list.append(temp)
        print(f"The temperature for {city.city_name} is: {temp}")  
        
        humidity = response_data["main"]["humidity"]
        humidity_list.append(humidity)
        print(f"The humidity for {city.city_name} is: {humidity}")  

        cloudiness = response_data["clouds"]["all"]
        cloudiness_list.append(cloudiness)
        print(f"The cloudiness for {city.city_name} is: {cloudiness}")  

        wind_speed = response_data["wind"]["speed"]
        wind_speed_list.append(wind_speed)
        print(f"The wind speed for {city.city_name} is: {wind_speed}") 
        
        latitude_list.append(rand_lat)
        print(f"The latitude for {city.city_name} is: {rand_lat}")
        
        longitude_list.append(rand_lon)
        
        date = response_data["dt"]
        date_list.append(date)
        x=x+1
```

    seminole
    us
    The temperature for seminole is: 306.15
    The humidity for seminole is: 11
    The cloudiness for seminole is: 1
    The wind speed for seminole is: 5.1
    The latitude for seminole is: 27.61826249751823
    dalton
    us
    The temperature for dalton is: 294.15
    The humidity for dalton is: 63
    The cloudiness for dalton is: 90
    The wind speed for dalton is: 3.6
    The latitude for dalton is: 34.85422582506894
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: -12.593859597527697
    souillac
    mu
    The temperature for souillac is: 297.15
    The humidity for souillac is: 88
    The cloudiness for souillac is: 75
    The wind speed for souillac is: 2.1
    The latitude for souillac is: -50.907224265184894
    petatlan
    mx
    The temperature for petatlan is: 301.643
    The humidity for petatlan is: 82
    The cloudiness for petatlan is: 8
    The wind speed for petatlan is: 4.71
    The latitude for petatlan is: 15.046687826679502
    namibe
    ao
    The temperature for namibe is: 299.393
    The humidity for namibe is: 100
    The cloudiness for namibe is: 20
    The wind speed for namibe is: 3.26
    The latitude for namibe is: -12.414017950860753
    hay river
    ca
    The temperature for hay river is: 281.143
    The humidity for hay river is: 74
    The cloudiness for hay river is: 92
    The wind speed for hay river is: 5.39
    The latitude for hay river is: 62.15956214066577
    lavrentiya
    ru
    The temperature for lavrentiya is: 272.793
    The humidity for lavrentiya is: 99
    The cloudiness for lavrentiya is: 24
    The wind speed for lavrentiya is: 9.41
    The latitude for lavrentiya is: 70.8241765098764
    lowestoft
    gb
    The temperature for lowestoft is: 284.243
    The humidity for lowestoft is: 86
    The cloudiness for lowestoft is: 92
    The wind speed for lowestoft is: 9.86
    The latitude for lowestoft is: 52.22322174554802
    naze
    jp
    The temperature for naze is: 294.543
    The humidity for naze is: 100
    The cloudiness for naze is: 76
    The wind speed for naze is: 5.54
    The latitude for naze is: 23.08367525206249
    puerto ayora
    ec
    The temperature for puerto ayora is: 301.15
    The humidity for puerto ayora is: 74
    The cloudiness for puerto ayora is: 20
    The wind speed for puerto ayora is: 5.7
    The latitude for puerto ayora is: -2.769739656073
    san policarpo
    ph
    The temperature for san policarpo is: 298.843
    The humidity for san policarpo is: 100
    The cloudiness for san policarpo is: 92
    The wind speed for san policarpo is: 2.29
    The latitude for san policarpo is: 13.566783286229764
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -24.638842403507965
    thompson
    ca
    The temperature for thompson is: 279.993
    The humidity for thompson is: 55
    The cloudiness for thompson is: 24
    The wind speed for thompson is: 3.76
    The latitude for thompson is: 68.98961482807388
    hargeysa
    so
    The temperature for hargeysa is: 291.743
    The humidity for hargeysa is: 78
    The cloudiness for hargeysa is: 0
    The wind speed for hargeysa is: 3.81
    The latitude for hargeysa is: 8.125451684558485
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -21.51147211219987
    saldanha
    za
    The temperature for saldanha is: 286.15
    The humidity for saldanha is: 82
    The cloudiness for saldanha is: 12
    The wind speed for saldanha is: 1
    The latitude for saldanha is: -35.87840642962716
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -65.79730715526776
    qaanaaq
    gl
    The temperature for qaanaaq is: 266.943
    The humidity for qaanaaq is: 94
    The cloudiness for qaanaaq is: 44
    The wind speed for qaanaaq is: 1.06
    The latitude for qaanaaq is: 75.92518917937622
    hithadhoo
    mv
    The temperature for hithadhoo is: 302.843
    The humidity for hithadhoo is: 100
    The cloudiness for hithadhoo is: 92
    The wind speed for hithadhoo is: 7.41
    The latitude for hithadhoo is: -3.3618616559057415
    kloulklubed
    pw
    The temperature for kloulklubed is: 302.143
    The humidity for kloulklubed is: 99
    The cloudiness for kloulklubed is: 44
    The wind speed for kloulklubed is: 2.36
    The latitude for kloulklubed is: 5.07070806230557
    grand gaube
    mu
    The temperature for grand gaube is: 297.15
    The humidity for grand gaube is: 88
    The cloudiness for grand gaube is: 75
    The wind speed for grand gaube is: 2.1
    The latitude for grand gaube is: -13.786091008603194
    iqaluit
    ca
    The temperature for iqaluit is: 259.493
    The humidity for iqaluit is: 90
    The cloudiness for iqaluit is: 0
    The wind speed for iqaluit is: 3.59
    The latitude for iqaluit is: 62.15913937032002
    ahuimanu
    us
    The temperature for ahuimanu is: 298.15
    The humidity for ahuimanu is: 69
    The cloudiness for ahuimanu is: 90
    The wind speed for ahuimanu is: 4.6
    The latitude for ahuimanu is: 25.022659179332578
    dikson
    ru
    The temperature for dikson is: 264.043
    The humidity for dikson is: 95
    The cloudiness for dikson is: 88
    The wind speed for dikson is: 3.54
    The latitude for dikson is: 80.2031590410368
    severo-kurilsk
    ru
    The temperature for severo-kurilsk is: 272.843
    The humidity for severo-kurilsk is: 100
    The cloudiness for severo-kurilsk is: 68
    The wind speed for severo-kurilsk is: 4.59
    The latitude for severo-kurilsk is: 47.5495403248475
    albany
    au
    The temperature for albany is: 282.693
    The humidity for albany is: 91
    The cloudiness for albany is: 8
    The wind speed for albany is: 2.34
    The latitude for albany is: -64.14449795491112
    dikson
    ru
    The temperature for dikson is: 264.043
    The humidity for dikson is: 95
    The cloudiness for dikson is: 88
    The wind speed for dikson is: 3.54
    The latitude for dikson is: 75.20190856181682
    beira
    mz
    The temperature for beira is: 296.15
    The humidity for beira is: 78
    The cloudiness for beira is: 20
    The wind speed for beira is: 3.64
    The latitude for beira is: -20.452345163832973
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -78.9228657019245
    khudumelapye
    bw
    The temperature for khudumelapye is: 285.443
    The humidity for khudumelapye is: 71
    The cloudiness for khudumelapye is: 0
    The wind speed for khudumelapye is: 1.39
    The latitude for khudumelapye is: -23.655635454648476
    selma
    us
    The temperature for selma is: 302.15
    The humidity for selma is: 32
    The cloudiness for selma is: 1
    The wind speed for selma is: 2.56
    The latitude for selma is: 32.14442717271993
    mahebourg
    mu
    The temperature for mahebourg is: 297.15
    The humidity for mahebourg is: 88
    The cloudiness for mahebourg is: 75
    The wind speed for mahebourg is: 2.1
    The latitude for mahebourg is: -23.43514689772411
    prainha
    br
    The temperature for prainha is: 300.143
    The humidity for prainha is: 87
    The cloudiness for prainha is: 64
    The wind speed for prainha is: 0.94
    The latitude for prainha is: -0.3279719855168395
    fortuna
    us
    The temperature for fortuna is: 291.15
    The humidity for fortuna is: 77
    The cloudiness for fortuna is: 1
    The wind speed for fortuna is: 5.1
    The latitude for fortuna is: 38.61813132960563
    ostrovnoy
    ru
    The temperature for ostrovnoy is: 271.693
    The humidity for ostrovnoy is: 86
    The cloudiness for ostrovnoy is: 36
    The wind speed for ostrovnoy is: 7.74
    The latitude for ostrovnoy is: 75.8650284604432
    barrow
    us
    The temperature for barrow is: 295.15
    The humidity for barrow is: 37
    The cloudiness for barrow is: 1
    The wind speed for barrow is: 5.1
    The latitude for barrow is: 85.49971268524254
    moen
    no
    The temperature for moen is: 272.343
    The humidity for moen is: 97
    The cloudiness for moen is: 56
    The wind speed for moen is: 0.84
    The latitude for moen is: 69.65842956525961
    werda
    bw
    The temperature for werda is: 288.693
    The humidity for werda is: 31
    The cloudiness for werda is: 0
    The wind speed for werda is: 4.86
    The latitude for werda is: -25.69231952178302
    tilichiki
    ru
    The temperature for tilichiki is: 270.293
    The humidity for tilichiki is: 87
    The cloudiness for tilichiki is: 0
    The wind speed for tilichiki is: 4.71
    The latitude for tilichiki is: 58.14289970958271
    broken hill
    au
    The temperature for broken hill is: 288.193
    The humidity for broken hill is: 92
    The cloudiness for broken hill is: 64
    The wind speed for broken hill is: 3.71
    The latitude for broken hill is: -26.649207361741823
    victoria
    sc
    The temperature for victoria is: 300.15
    The humidity for victoria is: 88
    The cloudiness for victoria is: 20
    The wind speed for victoria is: 0.5
    The latitude for victoria is: -2.50060151228017
    upernavik
    gl
    The temperature for upernavik is: 270.393
    The humidity for upernavik is: 100
    The cloudiness for upernavik is: 88
    The wind speed for upernavik is: 2.11
    The latitude for upernavik is: 86.93254290973422
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -63.38135622955876
    vao
    nc
    The temperature for vao is: 296.893
    The humidity for vao is: 100
    The cloudiness for vao is: 92
    The wind speed for vao is: 4.36
    The latitude for vao is: -25.855101416369024
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -87.32316371776483
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -52.950801279546695
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 21.85931413260724
    mayor pablo lagerenza
    py
    The temperature for mayor pablo lagerenza is: 306.543
    The humidity for mayor pablo lagerenza is: 45
    The cloudiness for mayor pablo lagerenza is: 8
    The wind speed for mayor pablo lagerenza is: 1.49
    The latitude for mayor pablo lagerenza is: -19.363631430384487
    pevek
    ru
    The temperature for pevek is: 262.193
    The humidity for pevek is: 91
    The cloudiness for pevek is: 0
    The wind speed for pevek is: 1.51
    The latitude for pevek is: 67.69114265867185
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: -8.863010231878519
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -66.84180867063009
    butaritari
    ki
    The temperature for butaritari is: 301.843
    The humidity for butaritari is: 99
    The cloudiness for butaritari is: 80
    The wind speed for butaritari is: 3.29
    The latitude for butaritari is: 13.695680949014303
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -33.4471168441916
    fallon
    us
    The temperature for fallon is: 286.15
    The humidity for fallon is: 37
    The cloudiness for fallon is: 1
    The wind speed for fallon is: 4.6
    The latitude for fallon is: 40.14303648866104
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -75.90399082031017
    ishinomaki
    jp
    The temperature for ishinomaki is: 288.143
    The humidity for ishinomaki is: 97
    The cloudiness for ishinomaki is: 100
    The wind speed for ishinomaki is: 4.99
    The latitude for ishinomaki is: 38.35729726107371
    pervomayskoye
    ru
    The temperature for pervomayskoye is: 278.293
    The humidity for pervomayskoye is: 91
    The cloudiness for pervomayskoye is: 56
    The wind speed for pervomayskoye is: 4.21
    The latitude for pervomayskoye is: 53.830387962995474
    togur
    ru
    The temperature for togur is: 276.093
    The humidity for togur is: 98
    The cloudiness for togur is: 92
    The wind speed for togur is: 4.36
    The latitude for togur is: 61.94164834033799
    geraldton
    au
    The temperature for geraldton is: 291.593
    The humidity for geraldton is: 100
    The cloudiness for geraldton is: 0
    The wind speed for geraldton is: 8.44
    The latitude for geraldton is: -35.0296651140798
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -75.54552992060485
    tuktoyaktuk
    ca
    The temperature for tuktoyaktuk is: 265.943
    The humidity for tuktoyaktuk is: 97
    The cloudiness for tuktoyaktuk is: 20
    The wind speed for tuktoyaktuk is: 7.89
    The latitude for tuktoyaktuk is: 75.079079813167
    lucapa
    ao
    The temperature for lucapa is: 292.593
    The humidity for lucapa is: 81
    The cloudiness for lucapa is: 0
    The wind speed for lucapa is: 1.26
    The latitude for lucapa is: -9.013974496303632
    hithadhoo
    mv
    The temperature for hithadhoo is: 302.843
    The humidity for hithadhoo is: 100
    The cloudiness for hithadhoo is: 92
    The wind speed for hithadhoo is: 7.41
    The latitude for hithadhoo is: -16.08272462098732
    winslow
    us
    The temperature for winslow is: 301.15
    The humidity for winslow is: 10
    The cloudiness for winslow is: 1
    The wind speed for winslow is: 2.6
    The latitude for winslow is: 35.46768700126542
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -59.45188555296198
    new norfolk
    au
    The temperature for new norfolk is: 282.893
    The humidity for new norfolk is: 92
    The cloudiness for new norfolk is: 48
    The wind speed for new norfolk is: 2.51
    The latitude for new norfolk is: -46.9004273126806
    tuatapere
    nz
    The temperature for tuatapere is: 284.293
    The humidity for tuatapere is: 100
    The cloudiness for tuatapere is: 64
    The wind speed for tuatapere is: 6.11
    The latitude for tuatapere is: -53.79153057669484
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -48.71074034235908
    hauterive
    ca
    The temperature for hauterive is: 282.543
    The humidity for hauterive is: 71
    The cloudiness for hauterive is: 32
    The wind speed for hauterive is: 3.14
    The latitude for hauterive is: 51.087903808442235
    agnibilekrou
    ci
    The temperature for agnibilekrou is: 300.843
    The humidity for agnibilekrou is: 73
    The cloudiness for agnibilekrou is: 8
    The wind speed for agnibilekrou is: 3.81
    The latitude for agnibilekrou is: 7.034976613415736
    cairns
    au
    The temperature for cairns is: 296.843
    The humidity for cairns is: 100
    The cloudiness for cairns is: 0
    The wind speed for cairns is: 5.49
    The latitude for cairns is: -13.35602911369125
    constitucion
    mx
    The temperature for constitucion is: 303.493
    The humidity for constitucion is: 19
    The cloudiness for constitucion is: 8
    The wind speed for constitucion is: 1.26
    The latitude for constitucion is: 16.355243907710275
    san patricio
    mx
    The temperature for san patricio is: 302.193
    The humidity for san patricio is: 61
    The cloudiness for san patricio is: 0
    The wind speed for san patricio is: 2.36
    The latitude for san patricio is: 10.210176651602168
    cape town
    za
    The temperature for cape town is: 288.15
    The humidity for cape town is: 82
    The cloudiness for cape town is: 20
    The wind speed for cape town is: 2.1
    The latitude for cape town is: -63.58179861308189
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 4.964104030407697
    barrow
    us
    The temperature for barrow is: 295.15
    The humidity for barrow is: 37
    The cloudiness for barrow is: 1
    The wind speed for barrow is: 5.1
    The latitude for barrow is: 89.52904989356031
    pangnirtung
    ca
    The temperature for pangnirtung is: 256.793
    The humidity for pangnirtung is: 85
    The cloudiness for pangnirtung is: 24
    The wind speed for pangnirtung is: 3.46
    The latitude for pangnirtung is: 60.373013627007
    upernavik
    gl
    The temperature for upernavik is: 270.393
    The humidity for upernavik is: 100
    The cloudiness for upernavik is: 88
    The wind speed for upernavik is: 2.11
    The latitude for upernavik is: 86.91566114077779
    mar del plata
    ar
    The temperature for mar del plata is: 287.643
    The humidity for mar del plata is: 47
    The cloudiness for mar del plata is: 0
    The wind speed for mar del plata is: 5.79
    The latitude for mar del plata is: -41.52578502866295
    ambon
    id
    The temperature for ambon is: 300.843
    The humidity for ambon is: 100
    The cloudiness for ambon is: 88
    The wind speed for ambon is: 3.01
    The latitude for ambon is: -5.067038075359733
    castro
    cl
    The temperature for castro is: 285.093
    The humidity for castro is: 78
    The cloudiness for castro is: 56
    The wind speed for castro is: 1.04
    The latitude for castro is: -48.95932057629083
    albany
    au
    The temperature for albany is: 282.693
    The humidity for albany is: 91
    The cloudiness for albany is: 8
    The wind speed for albany is: 2.34
    The latitude for albany is: -77.67180922730626
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 25.812475508001143
    albany
    au
    The temperature for albany is: 282.693
    The humidity for albany is: 91
    The cloudiness for albany is: 8
    The wind speed for albany is: 2.34
    The latitude for albany is: -57.239878055160844
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -51.07840310863766
    vanimo
    pg
    The temperature for vanimo is: 301.493
    The humidity for vanimo is: 100
    The cloudiness for vanimo is: 12
    The wind speed for vanimo is: 1.21
    The latitude for vanimo is: -1.7907807708207457
    ranau
    my
    The temperature for ranau is: 293.743
    The humidity for ranau is: 100
    The cloudiness for ranau is: 92
    The wind speed for ranau is: 0.09
    The latitude for ranau is: 5.561279602289858
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -87.58949865181114
    qaanaaq
    gl
    The temperature for qaanaaq is: 266.943
    The humidity for qaanaaq is: 94
    The cloudiness for qaanaaq is: 44
    The wind speed for qaanaaq is: 1.06
    The latitude for qaanaaq is: 84.5722357382219
    bredasdorp
    za
    The temperature for bredasdorp is: 286.15
    The humidity for bredasdorp is: 71
    The cloudiness for bredasdorp is: 24
    The wind speed for bredasdorp is: 2.1
    The latitude for bredasdorp is: -57.42937590162959
    shirokiy
    ru
    The temperature for shirokiy is: 276.143
    The humidity for shirokiy is: 72
    The cloudiness for shirokiy is: 32
    The wind speed for shirokiy is: 1.66
    The latitude for shirokiy is: 64.87446365457231
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -44.529128292440426
    saskylakh
    ru
    The temperature for saskylakh is: 261.243
    The humidity for saskylakh is: 86
    The cloudiness for saskylakh is: 64
    The wind speed for saskylakh is: 5.51
    The latitude for saskylakh is: 82.81043775027095
    nunoa
    pe
    The temperature for nunoa is: 278.093
    The humidity for nunoa is: 90
    The cloudiness for nunoa is: 76
    The wind speed for nunoa is: 1.24
    The latitude for nunoa is: -14.41408282991003
    ciudad bolivar
    ve
    The temperature for ciudad bolivar is: 308.893
    The humidity for ciudad bolivar is: 28
    The cloudiness for ciudad bolivar is: 0
    The wind speed for ciudad bolivar is: 5.19
    The latitude for ciudad bolivar is: 6.069329830794487
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -17.65681007843665
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 27.12080902759547
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -73.27930263927252
    pevek
    ru
    The temperature for pevek is: 262.193
    The humidity for pevek is: 91
    The cloudiness for pevek is: 0
    The wind speed for pevek is: 1.51
    The latitude for pevek is: 74.1472107800472
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -85.31919603774135
    panzhihua
    cn
    The temperature for panzhihua is: 291.443
    The humidity for panzhihua is: 40
    The cloudiness for panzhihua is: 0
    The wind speed for panzhihua is: 2.01
    The latitude for panzhihua is: 27.3220952371569
    kalmunai
    lk
    The temperature for kalmunai is: 296.643
    The humidity for kalmunai is: 100
    The cloudiness for kalmunai is: 0
    The wind speed for kalmunai is: 1.46
    The latitude for kalmunai is: 9.015807528152394
    lebu
    cl
    The temperature for lebu is: 285.793
    The humidity for lebu is: 96
    The cloudiness for lebu is: 0
    The wind speed for lebu is: 5.71
    The latitude for lebu is: -29.139720913988313
    skelleftea
    se
    The temperature for skelleftea is: 272.843
    The humidity for skelleftea is: 88
    The cloudiness for skelleftea is: 0
    The wind speed for skelleftea is: 1.74
    The latitude for skelleftea is: 64.89204077609068
    saint-philippe
    re
    The temperature for saint-philippe is: 299.15
    The humidity for saint-philippe is: 100
    The cloudiness for saint-philippe is: 90
    The wind speed for saint-philippe is: 2.6
    The latitude for saint-philippe is: -45.58768606970154
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -55.28658539825735
    touros
    br
    The temperature for touros is: 300.493
    The humidity for touros is: 76
    The cloudiness for touros is: 36
    The wind speed for touros is: 6.09
    The latitude for touros is: 0.20738462624488818
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -66.41348868241526
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -52.87371739181801
    portland
    au
    The temperature for portland is: 276.393
    The humidity for portland is: 81
    The cloudiness for portland is: 0
    The wind speed for portland is: 0.76
    The latitude for portland is: -47.32371976735321
    bluff
    nz
    The temperature for bluff is: 285.743
    The humidity for bluff is: 95
    The cloudiness for bluff is: 76
    The wind speed for bluff is: 9.14
    The latitude for bluff is: -58.950235999359336
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -82.04002675234601
    sorland
    no
    The temperature for sorland is: 278.643
    The humidity for sorland is: 97
    The cloudiness for sorland is: 92
    The wind speed for sorland is: 8.86
    The latitude for sorland is: 72.1575797128869
    chama
    zm
    The temperature for chama is: 292.043
    The humidity for chama is: 54
    The cloudiness for chama is: 0
    The wind speed for chama is: 3.94
    The latitude for chama is: -10.576172241526919
    mount gambier
    au
    The temperature for mount gambier is: 287.343
    The humidity for mount gambier is: 94
    The cloudiness for mount gambier is: 92
    The wind speed for mount gambier is: 1.29
    The latitude for mount gambier is: -51.040504549273905
    banda aceh
    id
    The temperature for banda aceh is: 297.493
    The humidity for banda aceh is: 96
    The cloudiness for banda aceh is: 80
    The wind speed for banda aceh is: 1.44
    The latitude for banda aceh is: 1.517012224489747
    cape town
    za
    The temperature for cape town is: 288.15
    The humidity for cape town is: 82
    The cloudiness for cape town is: 20
    The wind speed for cape town is: 2.1
    The latitude for cape town is: -61.32162068574203
    vardo
    no
    The temperature for vardo is: 276.643
    The humidity for vardo is: 94
    The cloudiness for vardo is: 76
    The wind speed for vardo is: 6.56
    The latitude for vardo is: 76.60837363373201
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -87.73789651021829
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -54.49692277798351
    kaitangata
    nz
    The temperature for kaitangata is: 283.343
    The humidity for kaitangata is: 74
    The cloudiness for kaitangata is: 88
    The wind speed for kaitangata is: 5.31
    The latitude for kaitangata is: -58.66614771021724
    bredasdorp
    za
    The temperature for bredasdorp is: 286.15
    The humidity for bredasdorp is: 71
    The cloudiness for bredasdorp is: 24
    The wind speed for bredasdorp is: 2.1
    The latitude for bredasdorp is: -67.22573898767705
    bluff
    nz
    The temperature for bluff is: 285.743
    The humidity for bluff is: 95
    The cloudiness for bluff is: 76
    The wind speed for bluff is: 9.14
    The latitude for bluff is: -82.29577431917828
    bluff
    nz
    The temperature for bluff is: 285.743
    The humidity for bluff is: 95
    The cloudiness for bluff is: 76
    The wind speed for bluff is: 9.14
    The latitude for bluff is: -66.10379742215642
    port hardy
    ca
    The temperature for port hardy is: 285.493
    The humidity for port hardy is: 78
    The cloudiness for port hardy is: 64
    The wind speed for port hardy is: 1.71
    The latitude for port hardy is: 42.3727688775038
    ilulissat
    gl
    The temperature for ilulissat is: 272.15
    The humidity for ilulissat is: 80
    The cloudiness for ilulissat is: 75
    The wind speed for ilulissat is: 2.1
    The latitude for ilulissat is: 70.55383518924151
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -73.47661120976773
    khatanga
    ru
    The temperature for khatanga is: 259.343
    The humidity for khatanga is: 78
    The cloudiness for khatanga is: 32
    The wind speed for khatanga is: 1.44
    The latitude for khatanga is: 74.15547512275049
    castro
    cl
    The temperature for castro is: 285.093
    The humidity for castro is: 78
    The cloudiness for castro is: 56
    The wind speed for castro is: 1.04
    The latitude for castro is: -48.277077612761786
    hamilton
    bm
    The temperature for hamilton is: 292.193
    The humidity for hamilton is: 100
    The cloudiness for hamilton is: 48
    The wind speed for hamilton is: 8.91
    The latitude for hamilton is: 31.63039752046656
    lagoa
    pt
    The temperature for lagoa is: 293.243
    The humidity for lagoa is: 60
    The cloudiness for lagoa is: 0
    The wind speed for lagoa is: 3.16
    The latitude for lagoa is: 50.880670874997236
    chapais
    ca
    The temperature for chapais is: 282.543
    The humidity for chapais is: 71
    The cloudiness for chapais is: 88
    The wind speed for chapais is: 1.96
    The latitude for chapais is: 51.15375612214467
    rawson
    ar
    The temperature for rawson is: 290.193
    The humidity for rawson is: 49
    The cloudiness for rawson is: 12
    The wind speed for rawson is: 6.24
    The latitude for rawson is: -49.590173208851695
    castro
    cl
    The temperature for castro is: 285.093
    The humidity for castro is: 78
    The cloudiness for castro is: 56
    The wind speed for castro is: 1.04
    The latitude for castro is: -46.90440925119707
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -69.61675896847002
    canico
    pt
    The temperature for canico is: 290.543
    The humidity for canico is: 100
    The cloudiness for canico is: 0
    The wind speed for canico is: 9.46
    The latitude for canico is: 32.24631636693441
    evensk
    ru
    The temperature for evensk is: 269.443
    The humidity for evensk is: 100
    The cloudiness for evensk is: 64
    The wind speed for evensk is: 1.79
    The latitude for evensk is: 61.95526389841805
    chuy
    uy
    The temperature for chuy is: 294.543
    The humidity for chuy is: 93
    The cloudiness for chuy is: 92
    The wind speed for chuy is: 7.06
    The latitude for chuy is: -60.23877868767405
    tasiilaq
    gl
    The temperature for tasiilaq is: 271.15
    The humidity for tasiilaq is: 79
    The cloudiness for tasiilaq is: 20
    The wind speed for tasiilaq is: 1
    The latitude for tasiilaq is: 57.88063295382656
    butaritari
    ki
    The temperature for butaritari is: 301.843
    The humidity for butaritari is: 99
    The cloudiness for butaritari is: 80
    The wind speed for butaritari is: 3.29
    The latitude for butaritari is: 25.10633299836489
    tokur
    ru
    The temperature for tokur is: 281.343
    The humidity for tokur is: 48
    The cloudiness for tokur is: 80
    The wind speed for tokur is: 2.36
    The latitude for tokur is: 53.43160155370819
    nikolskoye
    ru
    The temperature for nikolskoye is: 277.993
    The humidity for nikolskoye is: 92
    The cloudiness for nikolskoye is: 92
    The wind speed for nikolskoye is: 2.51
    The latitude for nikolskoye is: 56.8394977285399
    yulara
    au
    The temperature for yulara is: 295.143
    The humidity for yulara is: 34
    The cloudiness for yulara is: 92
    The wind speed for yulara is: 2.51
    The latitude for yulara is: -23.94532099567661
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -82.11564289721616
    pasaquina
    sv
    The temperature for pasaquina is: 307.643
    The humidity for pasaquina is: 29
    The cloudiness for pasaquina is: 36
    The wind speed for pasaquina is: 1.49
    The latitude for pasaquina is: 13.526161124529622
    tazovskiy
    ru
    The temperature for tazovskiy is: 264.243
    The humidity for tazovskiy is: 83
    The cloudiness for tazovskiy is: 92
    The wind speed for tazovskiy is: 1.39
    The latitude for tazovskiy is: 68.79666409807692
    kampot
    kh
    The temperature for kampot is: 297.243
    The humidity for kampot is: 97
    The cloudiness for kampot is: 20
    The wind speed for kampot is: 1.24
    The latitude for kampot is: 11.259670678584428
    khatanga
    ru
    The temperature for khatanga is: 259.343
    The humidity for khatanga is: 78
    The cloudiness for khatanga is: 32
    The wind speed for khatanga is: 1.44
    The latitude for khatanga is: 88.50959482267899
    hit
    iq
    The temperature for hit is: 288.643
    The humidity for hit is: 40
    The cloudiness for hit is: 0
    The wind speed for hit is: 2.11
    The latitude for hit is: 33.39083113317278
    luderitz
    na
    The temperature for luderitz is: 287.693
    The humidity for luderitz is: 93
    The cloudiness for luderitz is: 12
    The wind speed for luderitz is: 1.96
    The latitude for luderitz is: -28.56191376877978
    albany
    au
    The temperature for albany is: 282.693
    The humidity for albany is: 91
    The cloudiness for albany is: 8
    The wind speed for albany is: 2.34
    The latitude for albany is: -65.61372011468993
    nikolskoye
    ru
    The temperature for nikolskoye is: 277.993
    The humidity for nikolskoye is: 92
    The cloudiness for nikolskoye is: 92
    The wind speed for nikolskoye is: 2.51
    The latitude for nikolskoye is: 51.754974499475594
    safford
    us
    The temperature for safford is: 304.15
    The humidity for safford is: 6
    The cloudiness for safford is: 1
    The wind speed for safford is: 3.1
    The latitude for safford is: 33.04807236738142
    maldonado
    uy
    The temperature for maldonado is: 295.15
    The humidity for maldonado is: 73
    The cloudiness for maldonado is: 40
    The wind speed for maldonado is: 5.1
    The latitude for maldonado is: -38.76305633793007
    jesup
    us
    The temperature for jesup is: 298.15
    The humidity for jesup is: 47
    The cloudiness for jesup is: 75
    The wind speed for jesup is: 4.6
    The latitude for jesup is: 31.798166357286348
    namibe
    ao
    The temperature for namibe is: 299.393
    The humidity for namibe is: 100
    The cloudiness for namibe is: 20
    The wind speed for namibe is: 3.26
    The latitude for namibe is: -19.6615632425231
    bluefields
    ni
    The temperature for bluefields is: 303.643
    The humidity for bluefields is: 63
    The cloudiness for bluefields is: 8
    The wind speed for bluefields is: 2.74
    The latitude for bluefields is: 11.405157925496383
    arraial do cabo
    br
    The temperature for arraial do cabo is: 303.15
    The humidity for arraial do cabo is: 70
    The cloudiness for arraial do cabo is: 20
    The wind speed for arraial do cabo is: 6.2
    The latitude for arraial do cabo is: -40.16249027358173
    butaritari
    ki
    The temperature for butaritari is: 301.843
    The humidity for butaritari is: 99
    The cloudiness for butaritari is: 80
    The wind speed for butaritari is: 3.29
    The latitude for butaritari is: 17.977252965020142
    kaitangata
    nz
    The temperature for kaitangata is: 283.343
    The humidity for kaitangata is: 74
    The cloudiness for kaitangata is: 88
    The wind speed for kaitangata is: 5.31
    The latitude for kaitangata is: -89.35845612263087
    kazanskaya
    ru
    The temperature for kazanskaya is: 283.893
    The humidity for kazanskaya is: 59
    The cloudiness for kazanskaya is: 88
    The wind speed for kazanskaya is: 1.79
    The latitude for kazanskaya is: 49.40653013003518
    lianzhou
    cn
    The temperature for lianzhou is: 286.693
    The humidity for lianzhou is: 97
    The cloudiness for lianzhou is: 20
    The wind speed for lianzhou is: 0.91
    The latitude for lianzhou is: 22.08385537159039
    mahebourg
    mu
    The temperature for mahebourg is: 297.15
    The humidity for mahebourg is: 88
    The cloudiness for mahebourg is: 75
    The wind speed for mahebourg is: 2.1
    The latitude for mahebourg is: -42.86625213900656
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 16.480837670090622
    souillac
    mu
    The temperature for souillac is: 297.15
    The humidity for souillac is: 88
    The cloudiness for souillac is: 75
    The wind speed for souillac is: 2.1
    The latitude for souillac is: -21.77737048183897
    bethel
    us
    The temperature for bethel is: 275.15
    The humidity for bethel is: 93
    The cloudiness for bethel is: 90
    The wind speed for bethel is: 12.9
    The latitude for bethel is: 47.167634440516395
    kamaishi
    jp
    The temperature for kamaishi is: 282.893
    The humidity for kamaishi is: 97
    The cloudiness for kamaishi is: 92
    The wind speed for kamaishi is: 3.59
    The latitude for kamaishi is: 36.03591123621234
    torbay
    ca
    The temperature for torbay is: 280.843
    The humidity for torbay is: 59
    The cloudiness for torbay is: 56
    The wind speed for torbay is: 7.19
    The latitude for torbay is: 50.354135267979984
    bandarbeyla
    so
    The temperature for bandarbeyla is: 301.393
    The humidity for bandarbeyla is: 100
    The cloudiness for bandarbeyla is: 88
    The wind speed for bandarbeyla is: 2.61
    The latitude for bandarbeyla is: 7.324463718789872
    jirkov
    cz
    The temperature for jirkov is: 285.643
    The humidity for jirkov is: 59
    The cloudiness for jirkov is: 48
    The wind speed for jirkov is: 2.36
    The latitude for jirkov is: 50.45323988818717
    east london
    za
    The temperature for east london is: 292.15
    The humidity for east london is: 72
    The cloudiness for east london is: 40
    The wind speed for east london is: 2.6
    The latitude for east london is: -59.850329820185245
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -37.668414310642305
    avarua
    ck
    The temperature for avarua is: 297.543
    The humidity for avarua is: 100
    The cloudiness for avarua is: 56
    The wind speed for avarua is: 7.66
    The latitude for avarua is: -63.97149545722683
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -53.37408341265517
    comodoro rivadavia
    ar
    The temperature for comodoro rivadavia is: 291.15
    The humidity for comodoro rivadavia is: 39
    The cloudiness for comodoro rivadavia is: 0
    The wind speed for comodoro rivadavia is: 6.7
    The latitude for comodoro rivadavia is: -49.417505377893754
    carnarvon
    au
    The temperature for carnarvon is: 296.093
    The humidity for carnarvon is: 91
    The cloudiness for carnarvon is: 88
    The wind speed for carnarvon is: 9.69
    The latitude for carnarvon is: -30.782652218341894
    sarakhs
    ir
    The temperature for sarakhs is: 290.15
    The humidity for sarakhs is: 67
    The cloudiness for sarakhs is: 32
    The wind speed for sarakhs is: 1
    The latitude for sarakhs is: 35.7255224220318
    saint-philippe
    re
    The temperature for saint-philippe is: 299.15
    The humidity for saint-philippe is: 100
    The cloudiness for saint-philippe is: 90
    The wind speed for saint-philippe is: 2.6
    The latitude for saint-philippe is: -26.725201379538902
    gold coast
    au
    The temperature for gold coast is: 292.943
    The humidity for gold coast is: 100
    The cloudiness for gold coast is: 48
    The wind speed for gold coast is: 3.06
    The latitude for gold coast is: -27.85513333275682
    rio gallegos
    ar
    The temperature for rio gallegos is: 285.15
    The humidity for rio gallegos is: 71
    The cloudiness for rio gallegos is: 75
    The wind speed for rio gallegos is: 3.6
    The latitude for rio gallegos is: -51.607466821048334
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 16.204509509603753
    east london
    za
    The temperature for east london is: 292.15
    The humidity for east london is: 72
    The cloudiness for east london is: 40
    The wind speed for east london is: 2.6
    The latitude for east london is: -78.53731090394609
    porto santo
    pt
    The temperature for porto santo is: 290.293
    The humidity for porto santo is: 100
    The cloudiness for porto santo is: 0
    The wind speed for porto santo is: 10.34
    The latitude for porto santo is: 33.0461698368062
    kahului
    us
    The temperature for kahului is: 297.15
    The humidity for kahului is: 94
    The cloudiness for kahului is: 75
    The wind speed for kahului is: 6.7
    The latitude for kahului is: 34.43396286213928
    road town
    vg
    The temperature for road town is: 303.15
    The humidity for road town is: 48
    The cloudiness for road town is: 40
    The wind speed for road town is: 5.1
    The latitude for road town is: 19.707827603688003
    aklavik
    ca
    The temperature for aklavik is: 269.793
    The humidity for aklavik is: 100
    The cloudiness for aklavik is: 0
    The wind speed for aklavik is: 6.84
    The latitude for aklavik is: 70.43051587831445
    georgetown
    sh
    The temperature for georgetown is: 299.343
    The humidity for georgetown is: 100
    The cloudiness for georgetown is: 88
    The wind speed for georgetown is: 5.26
    The latitude for georgetown is: -14.726386882467153
    sao joao da barra
    br
    The temperature for sao joao da barra is: 300.15
    The humidity for sao joao da barra is: 65
    The cloudiness for sao joao da barra is: 20
    The wind speed for sao joao da barra is: 6.2
    The latitude for sao joao da barra is: -33.04458858386394
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: 5.032751192437431
    khatanga
    ru
    The temperature for khatanga is: 259.343
    The humidity for khatanga is: 78
    The cloudiness for khatanga is: 32
    The wind speed for khatanga is: 1.44
    The latitude for khatanga is: 85.96603025812439
    pevek
    ru
    The temperature for pevek is: 262.193
    The humidity for pevek is: 91
    The cloudiness for pevek is: 0
    The wind speed for pevek is: 1.51
    The latitude for pevek is: 77.69711866971508
    ust-ishim
    ru
    The temperature for ust-ishim is: 273.143
    The humidity for ust-ishim is: 84
    The cloudiness for ust-ishim is: 0
    The wind speed for ust-ishim is: 4.04
    The latitude for ust-ishim is: 57.647603466979234
    valleyview
    ca
    The temperature for valleyview is: 285.543
    The humidity for valleyview is: 60
    The cloudiness for valleyview is: 56
    The wind speed for valleyview is: 3.86
    The latitude for valleyview is: 54.48191635318477
    nanortalik
    gl
    The temperature for nanortalik is: 272.593
    The humidity for nanortalik is: 96
    The cloudiness for nanortalik is: 8
    The wind speed for nanortalik is: 5.84
    The latitude for nanortalik is: 55.659561826194675
    karema
    tz
    The temperature for karema is: 289.993
    The humidity for karema is: 92
    The cloudiness for karema is: 8
    The wind speed for karema is: 1.01
    The latitude for karema is: -6.5231931611201475
    nanortalik
    gl
    The temperature for nanortalik is: 272.593
    The humidity for nanortalik is: 96
    The cloudiness for nanortalik is: 8
    The wind speed for nanortalik is: 5.84
    The latitude for nanortalik is: 60.541890345387856
    coripata
    bo
    The temperature for coripata is: 284.15
    The humidity for coripata is: 57
    The cloudiness for coripata is: 75
    The wind speed for coripata is: 2.6
    The latitude for coripata is: -16.150392498311717
    sola
    vu
    The temperature for sola is: 300.943
    The humidity for sola is: 94
    The cloudiness for sola is: 88
    The wind speed for sola is: 5.44
    The latitude for sola is: -12.974779746633686
    thompson
    ca
    The temperature for thompson is: 279.993
    The humidity for thompson is: 55
    The cloudiness for thompson is: 24
    The wind speed for thompson is: 3.76
    The latitude for thompson is: 78.45186081567735
    yulara
    au
    The temperature for yulara is: 295.143
    The humidity for yulara is: 34
    The cloudiness for yulara is: 92
    The wind speed for yulara is: 2.51
    The latitude for yulara is: -25.09152722901682
    tasiilaq
    gl
    The temperature for tasiilaq is: 271.15
    The humidity for tasiilaq is: 79
    The cloudiness for tasiilaq is: 20
    The wind speed for tasiilaq is: 1
    The latitude for tasiilaq is: 60.66645150871835
    salinopolis
    br
    The temperature for salinopolis is: 300.643
    The humidity for salinopolis is: 100
    The cloudiness for salinopolis is: 64
    The wind speed for salinopolis is: 4.21
    The latitude for salinopolis is: 7.484495228742858
    padang
    id
    The temperature for padang is: 300.893
    The humidity for padang is: 100
    The cloudiness for padang is: 92
    The wind speed for padang is: 1.34
    The latitude for padang is: -1.5951408246431669
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -82.93169176999814
    salalah
    om
    The temperature for salalah is: 301.15
    The humidity for salalah is: 78
    The cloudiness for salalah is: 20
    The wind speed for salalah is: 2.1
    The latitude for salalah is: 17.747814353999956
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -76.80510048445541
    eirunepe
    br
    The temperature for eirunepe is: 303.343
    The humidity for eirunepe is: 69
    The cloudiness for eirunepe is: 12
    The wind speed for eirunepe is: 1.16
    The latitude for eirunepe is: -7.257477924886032
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 36.116655978638235
    sokolka
    pl
    The temperature for sokolka is: 286.343
    The humidity for sokolka is: 60
    The cloudiness for sokolka is: 68
    The wind speed for sokolka is: 5.61
    The latitude for sokolka is: 53.363530138844794
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -42.0126199039503
    genhe
    cn
    The temperature for genhe is: 276.793
    The humidity for genhe is: 64
    The cloudiness for genhe is: 0
    The wind speed for genhe is: 2.79
    The latitude for genhe is: 50.765555505788086
    richards bay
    za
    The temperature for richards bay is: 293.743
    The humidity for richards bay is: 96
    The cloudiness for richards bay is: 0
    The wind speed for richards bay is: 2.84
    The latitude for richards bay is: -32.64965282347754
    isparta
    tr
    The temperature for isparta is: 282.993
    The humidity for isparta is: 78
    The cloudiness for isparta is: 8
    The wind speed for isparta is: 0.76
    The latitude for isparta is: 37.9707266766068
    carbonia
    it
    The temperature for carbonia is: 291.143
    The humidity for carbonia is: 79
    The cloudiness for carbonia is: 8
    The wind speed for carbonia is: 4.39
    The latitude for carbonia is: 38.759445736638526
    lorengau
    pg
    The temperature for lorengau is: 301.443
    The humidity for lorengau is: 100
    The cloudiness for lorengau is: 8
    The wind speed for lorengau is: 3.31
    The latitude for lorengau is: 3.819082912027568
    terrace
    ca
    The temperature for terrace is: 280.393
    The humidity for terrace is: 63
    The cloudiness for terrace is: 76
    The wind speed for terrace is: 0.89
    The latitude for terrace is: 59.00586097632848
    barrow
    us
    The temperature for barrow is: 295.15
    The humidity for barrow is: 37
    The cloudiness for barrow is: 1
    The wind speed for barrow is: 5.1
    The latitude for barrow is: 68.29796488788773
    kaitangata
    nz
    The temperature for kaitangata is: 283.343
    The humidity for kaitangata is: 74
    The cloudiness for kaitangata is: 88
    The wind speed for kaitangata is: 5.31
    The latitude for kaitangata is: -50.34977012221751
    zaysan
    kz
    The temperature for zaysan is: 281.193
    The humidity for zaysan is: 58
    The cloudiness for zaysan is: 0
    The wind speed for zaysan is: 1.56
    The latitude for zaysan is: 48.37082981659475
    svetlaya
    ru
    The temperature for svetlaya is: 277.293
    The humidity for svetlaya is: 85
    The cloudiness for svetlaya is: 0
    The wind speed for svetlaya is: 3.59
    The latitude for svetlaya is: 45.297690922356196
    ucluelet
    ca
    The temperature for ucluelet is: 289.893
    The humidity for ucluelet is: 56
    The cloudiness for ucluelet is: 76
    The wind speed for ucluelet is: 0.91
    The latitude for ucluelet is: 48.69722485992659
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -43.499390582911175
    new norfolk
    au
    The temperature for new norfolk is: 282.893
    The humidity for new norfolk is: 92
    The cloudiness for new norfolk is: 48
    The wind speed for new norfolk is: 2.51
    The latitude for new norfolk is: -54.572984619616676
    ivybridge
    gb
    The temperature for ivybridge is: 283.143
    The humidity for ivybridge is: 98
    The cloudiness for ivybridge is: 32
    The wind speed for ivybridge is: 5.96
    The latitude for ivybridge is: 50.22633628771081
    sao filipe
    cv
    The temperature for sao filipe is: 294.943
    The humidity for sao filipe is: 97
    The cloudiness for sao filipe is: 0
    The wind speed for sao filipe is: 7.56
    The latitude for sao filipe is: 4.443431010071038
    qaanaaq
    gl
    The temperature for qaanaaq is: 266.943
    The humidity for qaanaaq is: 94
    The cloudiness for qaanaaq is: 44
    The wind speed for qaanaaq is: 1.06
    The latitude for qaanaaq is: 76.22054336098142
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -77.53921398409133
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -12.05419167001827
    pachmarhi
    in
    The temperature for pachmarhi is: 289.343
    The humidity for pachmarhi is: 54
    The cloudiness for pachmarhi is: 0
    The wind speed for pachmarhi is: 0.56
    The latitude for pachmarhi is: 22.3067974481053
    mahebourg
    mu
    The temperature for mahebourg is: 297.15
    The humidity for mahebourg is: 88
    The cloudiness for mahebourg is: 75
    The wind speed for mahebourg is: 2.1
    The latitude for mahebourg is: -43.949181490249835
    ancud
    cl
    The temperature for ancud is: 285.443
    The humidity for ancud is: 72
    The cloudiness for ancud is: 44
    The wind speed for ancud is: 1.36
    The latitude for ancud is: -41.56819704193974
    lompoc
    us
    The temperature for lompoc is: 291.15
    The humidity for lompoc is: 59
    The cloudiness for lompoc is: 1
    The wind speed for lompoc is: 3.6
    The latitude for lompoc is: 25.890721456899882
    talmenka
    ru
    The temperature for talmenka is: 283.993
    The humidity for talmenka is: 75
    The cloudiness for talmenka is: 92
    The wind speed for talmenka is: 4.66
    The latitude for talmenka is: 53.86713939865035
    port alfred
    za
    The temperature for port alfred is: 289.843
    The humidity for port alfred is: 100
    The cloudiness for port alfred is: 32
    The wind speed for port alfred is: 1.39
    The latitude for port alfred is: -81.9981583636222
    blyth
    gb
    The temperature for blyth is: 280.893
    The humidity for blyth is: 93
    The cloudiness for blyth is: 92
    The wind speed for blyth is: 2.56
    The latitude for blyth is: 56.28814004026077
    chuy
    uy
    The temperature for chuy is: 294.543
    The humidity for chuy is: 93
    The cloudiness for chuy is: 92
    The wind speed for chuy is: 7.06
    The latitude for chuy is: -68.12274683244016
    hofn
    is
    The temperature for hofn is: 276.143
    The humidity for hofn is: 100
    The cloudiness for hofn is: 76
    The wind speed for hofn is: 3.59
    The latitude for hofn is: 69.53770637425268
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -66.11665189902416
    yar-sale
    ru
    The temperature for yar-sale is: 260.393
    The humidity for yar-sale is: 71
    The cloudiness for yar-sale is: 24
    The wind speed for yar-sale is: 5.41
    The latitude for yar-sale is: 76.58992905093058
    madison
    us
    The temperature for madison is: 296.15
    The humidity for madison is: 17
    The cloudiness for madison is: 1
    The wind speed for madison is: 5.1
    The latitude for madison is: 34.492435258771124
    karratha
    au
    The temperature for karratha is: 296.343
    The humidity for karratha is: 82
    The cloudiness for karratha is: 92
    The wind speed for karratha is: 1.24
    The latitude for karratha is: -15.006351787256065
    coquimbo
    cl
    The temperature for coquimbo is: 287.15
    The humidity for coquimbo is: 87
    The cloudiness for coquimbo is: 90
    The wind speed for coquimbo is: 2.6
    The latitude for coquimbo is: -27.925108436459418
    castro
    cl
    The temperature for castro is: 285.093
    The humidity for castro is: 78
    The cloudiness for castro is: 56
    The wind speed for castro is: 1.04
    The latitude for castro is: -44.537395267926414
    maniitsoq
    gl
    The temperature for maniitsoq is: 269.343
    The humidity for maniitsoq is: 94
    The cloudiness for maniitsoq is: 76
    The wind speed for maniitsoq is: 4.94
    The latitude for maniitsoq is: 65.82862632401853
    kampot
    kh
    The temperature for kampot is: 297.243
    The humidity for kampot is: 97
    The cloudiness for kampot is: 20
    The wind speed for kampot is: 1.24
    The latitude for kampot is: 10.333835643723049
    orlik
    ru
    The temperature for orlik is: 267.593
    The humidity for orlik is: 87
    The cloudiness for orlik is: 0
    The wind speed for orlik is: 0.81
    The latitude for orlik is: 53.5804592216403
    upernavik
    gl
    The temperature for upernavik is: 270.393
    The humidity for upernavik is: 100
    The cloudiness for upernavik is: 88
    The wind speed for upernavik is: 2.11
    The latitude for upernavik is: 80.02638686805011
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -53.98814208759928
    mayahi
    ne
    The temperature for mayahi is: 299.793
    The humidity for mayahi is: 63
    The cloudiness for mayahi is: 0
    The wind speed for mayahi is: 1.24
    The latitude for mayahi is: 14.945177801535223
    yumen
    cn
    The temperature for yumen is: 281.893
    The humidity for yumen is: 45
    The cloudiness for yumen is: 0
    The wind speed for yumen is: 4.21
    The latitude for yumen is: 39.197630498286685
    port elizabeth
    za
    The temperature for port elizabeth is: 287.15
    The humidity for port elizabeth is: 87
    The cloudiness for port elizabeth is: 0
    The wind speed for port elizabeth is: 1
    The latitude for port elizabeth is: -46.48994238382718
    orlik
    ru
    The temperature for orlik is: 267.593
    The humidity for orlik is: 87
    The cloudiness for orlik is: 0
    The wind speed for orlik is: 0.81
    The latitude for orlik is: 51.86603326337914
    omboue
    ga
    The temperature for omboue is: 301.243
    The humidity for omboue is: 100
    The cloudiness for omboue is: 76
    The wind speed for omboue is: 3.46
    The latitude for omboue is: -5.0210973365103655
    santa quiteria do maranhao
    br
    The temperature for santa quiteria do maranhao is: 299.943
    The humidity for santa quiteria do maranhao is: 86
    The cloudiness for santa quiteria do maranhao is: 68
    The wind speed for santa quiteria do maranhao is: 1.21
    The latitude for santa quiteria do maranhao is: -3.3469460013925953
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -48.79920265201554
    port hardy
    ca
    The temperature for port hardy is: 285.493
    The humidity for port hardy is: 78
    The cloudiness for port hardy is: 64
    The wind speed for port hardy is: 1.71
    The latitude for port hardy is: 51.647159017096556
    marsa matruh
    eg
    The temperature for marsa matruh is: 288.393
    The humidity for marsa matruh is: 77
    The cloudiness for marsa matruh is: 92
    The wind speed for marsa matruh is: 3.26
    The latitude for marsa matruh is: 31.05736517800544
    torbay
    ca
    The temperature for torbay is: 280.843
    The humidity for torbay is: 59
    The cloudiness for torbay is: 56
    The wind speed for torbay is: 7.19
    The latitude for torbay is: 37.758335113644506
    cayenne
    gf
    The temperature for cayenne is: 301.15
    The humidity for cayenne is: 78
    The cloudiness for cayenne is: 76
    The wind speed for cayenne is: 4.6
    The latitude for cayenne is: 10.506438391832717
    oistins
    bb
    The temperature for oistins is: 299.843
    The humidity for oistins is: 99
    The cloudiness for oistins is: 92
    The wind speed for oistins is: 5.06
    The latitude for oistins is: 11.170306893613144
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -52.034874939089114
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -66.20245352926109
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -84.61490812452577
    khatanga
    ru
    The temperature for khatanga is: 259.343
    The humidity for khatanga is: 78
    The cloudiness for khatanga is: 32
    The wind speed for khatanga is: 1.44
    The latitude for khatanga is: 74.82927418797416
    ilulissat
    gl
    The temperature for ilulissat is: 272.15
    The humidity for ilulissat is: 80
    The cloudiness for ilulissat is: 75
    The wind speed for ilulissat is: 2.1
    The latitude for ilulissat is: 72.22095837008365
    oytal
    kz
    The temperature for oytal is: 287.043
    The humidity for oytal is: 97
    The cloudiness for oytal is: 92
    The wind speed for oytal is: 5.26
    The latitude for oytal is: 43.34906793219031
    avarua
    ck
    The temperature for avarua is: 297.543
    The humidity for avarua is: 100
    The cloudiness for avarua is: 56
    The wind speed for avarua is: 7.66
    The latitude for avarua is: -25.584701327467215
    lorengau
    pg
    The temperature for lorengau is: 301.443
    The humidity for lorengau is: 100
    The cloudiness for lorengau is: 8
    The wind speed for lorengau is: 3.31
    The latitude for lorengau is: -0.9405592842588817
    cape town
    za
    The temperature for cape town is: 288.15
    The humidity for cape town is: 82
    The cloudiness for cape town is: 20
    The wind speed for cape town is: 2.1
    The latitude for cape town is: -48.555609461219
    san juan
    us
    The temperature for san juan is: 305.15
    The humidity for san juan is: 33
    The cloudiness for san juan is: 1
    The wind speed for san juan is: 4.6
    The latitude for san juan is: 19.204859701307697
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -69.53142256098754
    thinadhoo
    mv
    The temperature for thinadhoo is: 302.843
    The humidity for thinadhoo is: 100
    The cloudiness for thinadhoo is: 80
    The wind speed for thinadhoo is: 7.34
    The latitude for thinadhoo is: 0.3522889922153638
    klaksvik
    fo
    The temperature for klaksvik is: 277.893
    The humidity for klaksvik is: 100
    The cloudiness for klaksvik is: 24
    The wind speed for klaksvik is: 0.79
    The latitude for klaksvik is: 76.92168843872503
    dikson
    ru
    The temperature for dikson is: 264.043
    The humidity for dikson is: 95
    The cloudiness for dikson is: 88
    The wind speed for dikson is: 3.54
    The latitude for dikson is: 89.23757621278281
    bluff
    nz
    The temperature for bluff is: 285.743
    The humidity for bluff is: 95
    The cloudiness for bluff is: 76
    The wind speed for bluff is: 9.14
    The latitude for bluff is: -79.01879269394138
    izumo
    jp
    The temperature for izumo is: 285.643
    The humidity for izumo is: 100
    The cloudiness for izumo is: 92
    The wind speed for izumo is: 7.29
    The latitude for izumo is: 35.33092637526542
    darab
    ir
    The temperature for darab is: 284.143
    The humidity for darab is: 59
    The cloudiness for darab is: 8
    The wind speed for darab is: 0.36
    The latitude for darab is: 29.04183785701977
    trinidad
    cu
    The temperature for trinidad is: 301.843
    The humidity for trinidad is: 92
    The cloudiness for trinidad is: 8
    The wind speed for trinidad is: 2.71
    The latitude for trinidad is: 20.689180428104507
    avarua
    ck
    The temperature for avarua is: 297.543
    The humidity for avarua is: 100
    The cloudiness for avarua is: 56
    The wind speed for avarua is: 7.66
    The latitude for avarua is: -48.081627447524895
    maibong
    in
    The temperature for maibong is: 290.743
    The humidity for maibong is: 86
    The cloudiness for maibong is: 0
    The wind speed for maibong is: 0.89
    The latitude for maibong is: 25.297873317122438
    marrakesh
    ma
    The temperature for marrakesh is: 285.693
    The humidity for marrakesh is: 100
    The cloudiness for marrakesh is: 92
    The wind speed for marrakesh is: 2.69
    The latitude for marrakesh is: 29.228405471932774
    ribeira grande
    pt
    The temperature for ribeira grande is: 290.543
    The humidity for ribeira grande is: 99
    The cloudiness for ribeira grande is: 32
    The wind speed for ribeira grande is: 3.19
    The latitude for ribeira grande is: 28.835085861142204
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -89.49534822811847
    avarua
    ck
    The temperature for avarua is: 297.543
    The humidity for avarua is: 100
    The cloudiness for avarua is: 56
    The wind speed for avarua is: 7.66
    The latitude for avarua is: -69.25611090488354
    iquique
    cl
    The temperature for iquique is: 295.15
    The humidity for iquique is: 64
    The cloudiness for iquique is: 0
    The wind speed for iquique is: 11.8
    The latitude for iquique is: -19.89912775873688
    belleville
    ca
    The temperature for belleville is: 288.093
    The humidity for belleville is: 60
    The cloudiness for belleville is: 92
    The wind speed for belleville is: 2.01
    The latitude for belleville is: 44.08172727274183
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -49.63504569083984
    chuy
    uy
    The temperature for chuy is: 294.543
    The humidity for chuy is: 93
    The cloudiness for chuy is: 92
    The wind speed for chuy is: 7.06
    The latitude for chuy is: -41.40157155443261
    kodiak
    us
    The temperature for kodiak is: 298.15
    The humidity for kodiak is: 22
    The cloudiness for kodiak is: 1
    The wind speed for kodiak is: 3.1
    The latitude for kodiak is: 47.35603978927375
    lagoa
    pt
    The temperature for lagoa is: 293.243
    The humidity for lagoa is: 60
    The cloudiness for lagoa is: 0
    The wind speed for lagoa is: 3.16
    The latitude for lagoa is: 50.22122043134581
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -47.7837035200309
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -49.63050474782753
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -67.2775552845212
    chara
    ru
    The temperature for chara is: 268.043
    The humidity for chara is: 67
    The cloudiness for chara is: 76
    The wind speed for chara is: 1.24
    The latitude for chara is: 57.147838776008115
    mocuba
    mz
    The temperature for mocuba is: 293.243
    The humidity for mocuba is: 87
    The cloudiness for mocuba is: 24
    The wind speed for mocuba is: 2.04
    The latitude for mocuba is: -19.113908709911556
    san andres
    co
    The temperature for san andres is: 302.243
    The humidity for san andres is: 85
    The cloudiness for san andres is: 36
    The wind speed for san andres is: 2.91
    The latitude for san andres is: 14.505460461343958
    cape town
    za
    The temperature for cape town is: 288.15
    The humidity for cape town is: 82
    The cloudiness for cape town is: 20
    The wind speed for cape town is: 2.1
    The latitude for cape town is: -50.02466086137087
    rabo de peixe
    pt
    The temperature for rabo de peixe is: 290.343
    The humidity for rabo de peixe is: 100
    The cloudiness for rabo de peixe is: 0
    The wind speed for rabo de peixe is: 3.24
    The latitude for rabo de peixe is: 45.844435206702855
    souillac
    mu
    The temperature for souillac is: 297.15
    The humidity for souillac is: 88
    The cloudiness for souillac is: 75
    The wind speed for souillac is: 2.1
    The latitude for souillac is: -41.96632942423132
    marfino
    ru
    The temperature for marfino is: 278.743
    The humidity for marfino is: 60
    The cloudiness for marfino is: 64
    The wind speed for marfino is: 2.71
    The latitude for marfino is: 46.791806319898086
    tyret pervaya
    ru
    The temperature for tyret pervaya is: 280.793
    The humidity for tyret pervaya is: 71
    The cloudiness for tyret pervaya is: 24
    The wind speed for tyret pervaya is: 4.04
    The latitude for tyret pervaya is: 52.81772838713434
    albany
    au
    The temperature for albany is: 282.693
    The humidity for albany is: 91
    The cloudiness for albany is: 8
    The wind speed for albany is: 2.34
    The latitude for albany is: -73.05496071508804
    bredasdorp
    za
    The temperature for bredasdorp is: 286.15
    The humidity for bredasdorp is: 71
    The cloudiness for bredasdorp is: 24
    The wind speed for bredasdorp is: 2.1
    The latitude for bredasdorp is: -82.15365028671874
    puerto ayora
    ec
    The temperature for puerto ayora is: 301.15
    The humidity for puerto ayora is: 74
    The cloudiness for puerto ayora is: 20
    The wind speed for puerto ayora is: 5.7
    The latitude for puerto ayora is: -14.950151188075822
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -60.214077225163095
    alta floresta
    br
    The temperature for alta floresta is: 299.043
    The humidity for alta floresta is: 93
    The cloudiness for alta floresta is: 48
    The wind speed for alta floresta is: 0.69
    The latitude for alta floresta is: -10.28251850552293
    avarua
    ck
    The temperature for avarua is: 297.543
    The humidity for avarua is: 100
    The cloudiness for avarua is: 56
    The wind speed for avarua is: 7.66
    The latitude for avarua is: -31.698378474157977
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -43.96513534998545
    port elizabeth
    za
    The temperature for port elizabeth is: 287.15
    The humidity for port elizabeth is: 87
    The cloudiness for port elizabeth is: 0
    The wind speed for port elizabeth is: 1
    The latitude for port elizabeth is: -60.761467350064265
    ancud
    cl
    The temperature for ancud is: 285.443
    The humidity for ancud is: 72
    The cloudiness for ancud is: 44
    The wind speed for ancud is: 1.36
    The latitude for ancud is: -42.33087704336687
    hay river
    ca
    The temperature for hay river is: 281.143
    The humidity for hay river is: 74
    The cloudiness for hay river is: 92
    The wind speed for hay river is: 5.39
    The latitude for hay river is: 61.84337679020618
    avarua
    ck
    The temperature for avarua is: 297.543
    The humidity for avarua is: 100
    The cloudiness for avarua is: 56
    The wind speed for avarua is: 7.66
    The latitude for avarua is: -28.965614670487838
    washougal
    us
    The temperature for washougal is: 296.15
    The humidity for washougal is: 30
    The cloudiness for washougal is: 1
    The wind speed for washougal is: 7.2
    The latitude for washougal is: 45.472348850070176
    qaanaaq
    gl
    The temperature for qaanaaq is: 266.943
    The humidity for qaanaaq is: 94
    The cloudiness for qaanaaq is: 44
    The wind speed for qaanaaq is: 1.06
    The latitude for qaanaaq is: 81.6646289758695
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: -0.09272670196179433
    grants pass
    us
    The temperature for grants pass is: 296.493
    The humidity for grants pass is: 31
    The cloudiness for grants pass is: 0
    The wind speed for grants pass is: 1.06
    The latitude for grants pass is: 42.24048989061589
    thompson
    ca
    The temperature for thompson is: 279.993
    The humidity for thompson is: 55
    The cloudiness for thompson is: 24
    The wind speed for thompson is: 3.76
    The latitude for thompson is: 62.13074854832985
    hobart
    au
    The temperature for hobart is: 283.443
    The humidity for hobart is: 83
    The cloudiness for hobart is: 0
    The wind speed for hobart is: 2.39
    The latitude for hobart is: -88.60863992843137
    ardatov
    ru
    The temperature for ardatov is: 269.743
    The humidity for ardatov is: 71
    The cloudiness for ardatov is: 0
    The wind speed for ardatov is: 1.26
    The latitude for ardatov is: 55.396206291952836
    dikson
    ru
    The temperature for dikson is: 264.043
    The humidity for dikson is: 95
    The cloudiness for dikson is: 88
    The wind speed for dikson is: 3.54
    The latitude for dikson is: 86.74693118608508
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -67.68318691378987
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -87.51679295804884
    norman wells
    ca
    The temperature for norman wells is: 270.393
    The humidity for norman wells is: 92
    The cloudiness for norman wells is: 20
    The wind speed for norman wells is: 1.84
    The latitude for norman wells is: 66.08207011080347
    baykit
    ru
    The temperature for baykit is: 263.593
    The humidity for baykit is: 68
    The cloudiness for baykit is: 12
    The wind speed for baykit is: 2.34
    The latitude for baykit is: 62.37974089476472
    aksu
    cn
    The temperature for aksu is: 279.593
    The humidity for aksu is: 59
    The cloudiness for aksu is: 0
    The wind speed for aksu is: 1.34
    The latitude for aksu is: 40.14853895195537
    kahului
    us
    The temperature for kahului is: 297.15
    The humidity for kahului is: 94
    The cloudiness for kahului is: 75
    The wind speed for kahului is: 6.7
    The latitude for kahului is: 36.69805067878788
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -25.691210116018127
    georgetown
    sh
    The temperature for georgetown is: 299.343
    The humidity for georgetown is: 100
    The cloudiness for georgetown is: 88
    The wind speed for georgetown is: 5.26
    The latitude for georgetown is: -21.121370368719496
    constitucion
    mx
    The temperature for constitucion is: 303.493
    The humidity for constitucion is: 19
    The cloudiness for constitucion is: 8
    The wind speed for constitucion is: 1.26
    The latitude for constitucion is: 20.299405928486948
    nikolskoye
    ru
    The temperature for nikolskoye is: 277.993
    The humidity for nikolskoye is: 92
    The cloudiness for nikolskoye is: 92
    The wind speed for nikolskoye is: 2.51
    The latitude for nikolskoye is: 47.201771064822026
    butaritari
    ki
    The temperature for butaritari is: 301.843
    The humidity for butaritari is: 99
    The cloudiness for butaritari is: 80
    The wind speed for butaritari is: 3.29
    The latitude for butaritari is: 6.213999826067436
    saldanha
    za
    The temperature for saldanha is: 286.15
    The humidity for saldanha is: 82
    The cloudiness for saldanha is: 12
    The wind speed for saldanha is: 1
    The latitude for saldanha is: -41.29696760094656
    chirongui
    yt
    The temperature for chirongui is: 300.15
    The humidity for chirongui is: 78
    The cloudiness for chirongui is: 0
    The wind speed for chirongui is: 3.6
    The latitude for chirongui is: -14.383981295543961
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -34.57857923817763
    tucupita
    ve
    The temperature for tucupita is: 306.493
    The humidity for tucupita is: 39
    The cloudiness for tucupita is: 12
    The wind speed for tucupita is: 4.74
    The latitude for tucupita is: 8.851961331533104
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 16.358006396815114
    mao
    td
    The temperature for mao is: 299.993
    The humidity for mao is: 17
    The cloudiness for mao is: 0
    The wind speed for mao is: 3.74
    The latitude for mao is: 14.761969041588046
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 7.805228922672271
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -80.81405329728968
    alofi
    nu
    The temperature for alofi is: 299.543
    The humidity for alofi is: 100
    The cloudiness for alofi is: 56
    The wind speed for alofi is: 7.54
    The latitude for alofi is: -27.90581988640473
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -58.46096830803333
    ugep
    ng
    The temperature for ugep is: 299.593
    The humidity for ugep is: 85
    The cloudiness for ugep is: 64
    The wind speed for ugep is: 3.69
    The latitude for ugep is: 5.819315990412349
    oranjemund
    na
    The temperature for oranjemund is: 288.643
    The humidity for oranjemund is: 100
    The cloudiness for oranjemund is: 76
    The wind speed for oranjemund is: 2.19
    The latitude for oranjemund is: -29.35535047612023
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -63.04511731928492
    yanam
    in
    The temperature for yanam is: 301.593
    The humidity for yanam is: 85
    The cloudiness for yanam is: 80
    The wind speed for yanam is: 3.41
    The latitude for yanam is: 16.36539640668343
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -28.277692897105347
    mari
    br
    The temperature for mari is: 302.15
    The humidity for mari is: 62
    The cloudiness for mari is: 40
    The wind speed for mari is: 5.1
    The latitude for mari is: -7.023697483308396
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 28.25797914202738
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -89.77232558620045
    katsuura
    jp
    The temperature for katsuura is: 287.843
    The humidity for katsuura is: 96
    The cloudiness for katsuura is: 24
    The wind speed for katsuura is: 5.84
    The latitude for katsuura is: 20.09947283869751
    acari
    pe
    The temperature for acari is: 295.543
    The humidity for acari is: 64
    The cloudiness for acari is: 24
    The wind speed for acari is: 1.29
    The latitude for acari is: -17.374193281580787
    ulaangom
    mn
    The temperature for ulaangom is: 270.343
    The humidity for ulaangom is: 64
    The cloudiness for ulaangom is: 8
    The wind speed for ulaangom is: 0.89
    The latitude for ulaangom is: 48.969612464088556
    cherskiy
    ru
    The temperature for cherskiy is: 267.843
    The humidity for cherskiy is: 70
    The cloudiness for cherskiy is: 0
    The wind speed for cherskiy is: 1.14
    The latitude for cherskiy is: 79.66965141160941
    vanimo
    pg
    The temperature for vanimo is: 301.493
    The humidity for vanimo is: 100
    The cloudiness for vanimo is: 12
    The wind speed for vanimo is: 1.21
    The latitude for vanimo is: -2.276521913743707
    hamilton
    bm
    The temperature for hamilton is: 292.193
    The humidity for hamilton is: 100
    The cloudiness for hamilton is: 48
    The wind speed for hamilton is: 8.91
    The latitude for hamilton is: 29.457813904528933
    kaitangata
    nz
    The temperature for kaitangata is: 283.343
    The humidity for kaitangata is: 74
    The cloudiness for kaitangata is: 88
    The wind speed for kaitangata is: 5.31
    The latitude for kaitangata is: -57.43376432374593
    bredasdorp
    za
    The temperature for bredasdorp is: 286.15
    The humidity for bredasdorp is: 71
    The cloudiness for bredasdorp is: 24
    The wind speed for bredasdorp is: 2.1
    The latitude for bredasdorp is: -41.14541497662743
    tuktoyaktuk
    ca
    The temperature for tuktoyaktuk is: 265.943
    The humidity for tuktoyaktuk is: 97
    The cloudiness for tuktoyaktuk is: 20
    The wind speed for tuktoyaktuk is: 7.89
    The latitude for tuktoyaktuk is: 79.81107854895222
    nemuro
    jp
    The temperature for nemuro is: 276.493
    The humidity for nemuro is: 95
    The cloudiness for nemuro is: 92
    The wind speed for nemuro is: 6.79
    The latitude for nemuro is: 36.287923665742866
    saskylakh
    ru
    The temperature for saskylakh is: 261.243
    The humidity for saskylakh is: 86
    The cloudiness for saskylakh is: 64
    The wind speed for saskylakh is: 5.51
    The latitude for saskylakh is: 80.4665808125772
    lampa
    pe
    The temperature for lampa is: 287.15
    The humidity for lampa is: 47
    The cloudiness for lampa is: 40
    The wind speed for lampa is: 4.1
    The latitude for lampa is: -15.440436847301271
    port alfred
    za
    The temperature for port alfred is: 289.843
    The humidity for port alfred is: 100
    The cloudiness for port alfred is: 32
    The wind speed for port alfred is: 1.39
    The latitude for port alfred is: -73.96795334179988
    igarka
    ru
    The temperature for igarka is: 266.543
    The humidity for igarka is: 87
    The cloudiness for igarka is: 88
    The wind speed for igarka is: 6.19
    The latitude for igarka is: 66.25418883152912
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: -3.3871506508920532
    torbay
    ca
    The temperature for torbay is: 280.843
    The humidity for torbay is: 59
    The cloudiness for torbay is: 56
    The wind speed for torbay is: 7.19
    The latitude for torbay is: 43.89918269029897
    new norfolk
    au
    The temperature for new norfolk is: 282.893
    The humidity for new norfolk is: 92
    The cloudiness for new norfolk is: 48
    The wind speed for new norfolk is: 2.51
    The latitude for new norfolk is: -50.36244949227524
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 12.687732753571623
    ilebo
    cd
    The temperature for ilebo is: 296.243
    The humidity for ilebo is: 91
    The cloudiness for ilebo is: 36
    The wind speed for ilebo is: 0.99
    The latitude for ilebo is: -3.0315563643576553
    mahebourg
    mu
    The temperature for mahebourg is: 297.15
    The humidity for mahebourg is: 88
    The cloudiness for mahebourg is: 75
    The wind speed for mahebourg is: 2.1
    The latitude for mahebourg is: -32.454682314447005
    bredasdorp
    za
    The temperature for bredasdorp is: 286.15
    The humidity for bredasdorp is: 71
    The cloudiness for bredasdorp is: 24
    The wind speed for bredasdorp is: 2.1
    The latitude for bredasdorp is: -71.60071462610533
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -83.19753919942985
    tiksi
    ru
    The temperature for tiksi is: 267.243
    The humidity for tiksi is: 94
    The cloudiness for tiksi is: 92
    The wind speed for tiksi is: 7.66
    The latitude for tiksi is: 89.68265402111453
    wencheng
    cn
    The temperature for wencheng is: 285.993
    The humidity for wencheng is: 96
    The cloudiness for wencheng is: 0
    The wind speed for wencheng is: 0.69
    The latitude for wencheng is: 37.0858527297425
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -31.934351153297854
    cape town
    za
    The temperature for cape town is: 288.15
    The humidity for cape town is: 82
    The cloudiness for cape town is: 20
    The wind speed for cape town is: 2.1
    The latitude for cape town is: -54.08685389481457
    san vicente
    ph
    The temperature for san vicente is: 301.493
    The humidity for san vicente is: 99
    The cloudiness for san vicente is: 88
    The wind speed for san vicente is: 3.39
    The latitude for san vicente is: 19.458040766937074
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 9.498279931201978
    jamestown
    sh
    The temperature for jamestown is: 297.293
    The humidity for jamestown is: 100
    The cloudiness for jamestown is: 24
    The wind speed for jamestown is: 9.86
    The latitude for jamestown is: -37.11316720980649
    esperance
    au
    The temperature for esperance is: 280.843
    The humidity for esperance is: 87
    The cloudiness for esperance is: 0
    The wind speed for esperance is: 1.21
    The latitude for esperance is: -45.83847631876293
    pisco
    pe
    The temperature for pisco is: 298.15
    The humidity for pisco is: 61
    The cloudiness for pisco is: 0
    The wind speed for pisco is: 8.7
    The latitude for pisco is: -19.795380945931
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -42.847715039475354
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: -13.52260959170873
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -75.60301273737969
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -38.65956099819964
    bredasdorp
    za
    The temperature for bredasdorp is: 286.15
    The humidity for bredasdorp is: 71
    The cloudiness for bredasdorp is: 24
    The wind speed for bredasdorp is: 2.1
    The latitude for bredasdorp is: -87.2803652204606
    san angelo
    us
    The temperature for san angelo is: 305.15
    The humidity for san angelo is: 27
    The cloudiness for san angelo is: 1
    The wind speed for san angelo is: 3.6
    The latitude for san angelo is: 31.539678874844242
    bambous virieux
    mu
    The temperature for bambous virieux is: 297.15
    The humidity for bambous virieux is: 88
    The cloudiness for bambous virieux is: 75
    The wind speed for bambous virieux is: 2.1
    The latitude for bambous virieux is: -25.204538876553613
    geraldton
    au
    The temperature for geraldton is: 291.593
    The humidity for geraldton is: 100
    The cloudiness for geraldton is: 0
    The wind speed for geraldton is: 8.44
    The latitude for geraldton is: -28.72843108932839
    khatanga
    ru
    The temperature for khatanga is: 259.343
    The humidity for khatanga is: 78
    The cloudiness for khatanga is: 32
    The wind speed for khatanga is: 1.44
    The latitude for khatanga is: 89.89504474776908
    belaya gora
    ru
    The temperature for belaya gora is: 266.993
    The humidity for belaya gora is: 96
    The cloudiness for belaya gora is: 88
    The wind speed for belaya gora is: 4.61
    The latitude for belaya gora is: 67.8159666982202
    conakry
    gn
    The temperature for conakry is: 298.493
    The humidity for conakry is: 100
    The cloudiness for conakry is: 0
    The wind speed for conakry is: 2.86
    The latitude for conakry is: 8.182127811715219
    butaritari
    ki
    The temperature for butaritari is: 301.843
    The humidity for butaritari is: 99
    The cloudiness for butaritari is: 80
    The wind speed for butaritari is: 3.29
    The latitude for butaritari is: 18.76133072687773
    arona
    es
    The temperature for arona is: 290.243
    The humidity for arona is: 90
    The cloudiness for arona is: 0
    The wind speed for arona is: 2.11
    The latitude for arona is: 27.357500983310004
    raudeberg
    no
    The temperature for raudeberg is: 275.943
    The humidity for raudeberg is: 100
    The cloudiness for raudeberg is: 92
    The wind speed for raudeberg is: 2.36
    The latitude for raudeberg is: 63.2868109975154
    lazaro cardenas
    mx
    The temperature for lazaro cardenas is: 304.943
    The humidity for lazaro cardenas is: 17
    The cloudiness for lazaro cardenas is: 64
    The wind speed for lazaro cardenas is: 1.01
    The latitude for lazaro cardenas is: 3.3439214425703057
    ukiah
    us
    The temperature for ukiah is: 297.15
    The humidity for ukiah is: 41
    The cloudiness for ukiah is: 1
    The wind speed for ukiah is: 3.1
    The latitude for ukiah is: 37.433991937718815
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -52.903376508423435
    khatanga
    ru
    The temperature for khatanga is: 259.343
    The humidity for khatanga is: 78
    The cloudiness for khatanga is: 32
    The wind speed for khatanga is: 1.44
    The latitude for khatanga is: 72.0824964380626
    mattru
    sl
    The temperature for mattru is: 299.543
    The humidity for mattru is: 86
    The cloudiness for mattru is: 8
    The wind speed for mattru is: 2.59
    The latitude for mattru is: 6.555312698932767
    severo-kurilsk
    ru
    The temperature for severo-kurilsk is: 272.843
    The humidity for severo-kurilsk is: 100
    The cloudiness for severo-kurilsk is: 68
    The wind speed for severo-kurilsk is: 4.59
    The latitude for severo-kurilsk is: 40.58173577672653
    biak
    id
    The temperature for biak is: 296.993
    The humidity for biak is: 100
    The cloudiness for biak is: 92
    The wind speed for biak is: 2.29
    The latitude for biak is: 2.482927795524361
    sao filipe
    cv
    The temperature for sao filipe is: 294.943
    The humidity for sao filipe is: 97
    The cloudiness for sao filipe is: 0
    The wind speed for sao filipe is: 7.56
    The latitude for sao filipe is: 10.090126466253878
    san andres del rabanedo
    es
    The temperature for san andres del rabanedo is: 289.193
    The humidity for san andres del rabanedo is: 62
    The cloudiness for san andres del rabanedo is: 48
    The wind speed for san andres del rabanedo is: 1.91
    The latitude for san andres del rabanedo is: 42.59087037662866
    ponta do sol
    pt
    The temperature for ponta do sol is: 290.743
    The humidity for ponta do sol is: 100
    The cloudiness for ponta do sol is: 8
    The wind speed for ponta do sol is: 9.21
    The latitude for ponta do sol is: 35.053895477007345
    ribeira grande
    pt
    The temperature for ribeira grande is: 290.543
    The humidity for ribeira grande is: 99
    The cloudiness for ribeira grande is: 32
    The wind speed for ribeira grande is: 3.19
    The latitude for ribeira grande is: 27.977389834947047
    san patricio
    mx
    The temperature for san patricio is: 302.193
    The humidity for san patricio is: 61
    The cloudiness for san patricio is: 0
    The wind speed for san patricio is: 2.36
    The latitude for san patricio is: 9.771132203653153
    bluff
    nz
    The temperature for bluff is: 285.743
    The humidity for bluff is: 95
    The cloudiness for bluff is: 76
    The wind speed for bluff is: 9.14
    The latitude for bluff is: -87.29268191516904
    kodiak
    us
    The temperature for kodiak is: 298.15
    The humidity for kodiak is: 22
    The cloudiness for kodiak is: 1
    The wind speed for kodiak is: 3.1
    The latitude for kodiak is: 45.408113455651176
    milford
    us
    The temperature for milford is: 286.15
    The humidity for milford is: 100
    The cloudiness for milford is: 90
    The wind speed for milford is: 4.1
    The latitude for milford is: 38.79975148688874
    praya
    id
    The temperature for praya is: 301.343
    The humidity for praya is: 97
    The cloudiness for praya is: 0
    The wind speed for praya is: 3.99
    The latitude for praya is: -10.86655610823641
    ponta do sol
    pt
    The temperature for ponta do sol is: 290.743
    The humidity for ponta do sol is: 100
    The cloudiness for ponta do sol is: 8
    The wind speed for ponta do sol is: 9.21
    The latitude for ponta do sol is: 37.46855188113851
    yellowknife
    ca
    The temperature for yellowknife is: 277.143
    The humidity for yellowknife is: 94
    The cloudiness for yellowknife is: 92
    The wind speed for yellowknife is: 5.56
    The latitude for yellowknife is: 71.56109504841746
    oranjemund
    na
    The temperature for oranjemund is: 288.643
    The humidity for oranjemund is: 100
    The cloudiness for oranjemund is: 76
    The wind speed for oranjemund is: 2.19
    The latitude for oranjemund is: -31.07412941590904
    klaksvik
    fo
    The temperature for klaksvik is: 277.893
    The humidity for klaksvik is: 100
    The cloudiness for klaksvik is: 24
    The wind speed for klaksvik is: 0.79
    The latitude for klaksvik is: 74.51045643615828
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -83.86745123188453
    hutchinson
    us
    The temperature for hutchinson is: 297.15
    The humidity for hutchinson is: 55
    The cloudiness for hutchinson is: 75
    The wind speed for hutchinson is: 9.3
    The latitude for hutchinson is: 37.97979149465624
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -75.42796237232594
    freire
    cl
    The temperature for freire is: 286.593
    The humidity for freire is: 67
    The cloudiness for freire is: 0
    The wind speed for freire is: 1.16
    The latitude for freire is: -38.89538302085902
    la baneza
    es
    The temperature for la baneza is: 290.993
    The humidity for la baneza is: 54
    The cloudiness for la baneza is: 92
    The wind speed for la baneza is: 0.76
    The latitude for la baneza is: 42.2968695275828
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -44.34984328434614
    cabo san lucas
    mx
    The temperature for cabo san lucas is: 297.143
    The humidity for cabo san lucas is: 88
    The cloudiness for cabo san lucas is: 76
    The wind speed for cabo san lucas is: 0.94
    The latitude for cabo san lucas is: 8.078320697819805
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -30.74545922218268
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -72.25656772962947
    khandbari
    np
    The temperature for khandbari is: 276.293
    The humidity for khandbari is: 78
    The cloudiness for khandbari is: 76
    The wind speed for khandbari is: 0.34
    The latitude for khandbari is: 29.568393380673257
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -83.16671128959352
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -50.55868402616073
    grindavik
    is
    The temperature for grindavik is: 279.15
    The humidity for grindavik is: 93
    The cloudiness for grindavik is: 75
    The wind speed for grindavik is: 5.7
    The latitude for grindavik is: 60.1996029774682
    tuatapere
    nz
    The temperature for tuatapere is: 284.293
    The humidity for tuatapere is: 100
    The cloudiness for tuatapere is: 64
    The wind speed for tuatapere is: 6.11
    The latitude for tuatapere is: -51.92038308137337
    magnitka
    ru
    The temperature for magnitka is: 268.643
    The humidity for magnitka is: 92
    The cloudiness for magnitka is: 0
    The wind speed for magnitka is: 2.11
    The latitude for magnitka is: 55.30507295020527
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -79.73698328484531
    iqaluit
    ca
    The temperature for iqaluit is: 259.493
    The humidity for iqaluit is: 90
    The cloudiness for iqaluit is: 0
    The wind speed for iqaluit is: 3.59
    The latitude for iqaluit is: 62.66337861997775
    cabo san lucas
    mx
    The temperature for cabo san lucas is: 297.143
    The humidity for cabo san lucas is: 88
    The cloudiness for cabo san lucas is: 76
    The wind speed for cabo san lucas is: 0.94
    The latitude for cabo san lucas is: 16.710179545107763
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -24.705989461676566
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -40.02678861100748
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 6.728412247652187
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -80.22683630208257
    kolda
    sn
    The temperature for kolda is: 306.043
    The humidity for kolda is: 30
    The cloudiness for kolda is: 64
    The wind speed for kolda is: 3.61
    The latitude for kolda is: 12.63749694389135
    port hedland
    au
    The temperature for port hedland is: 296.643
    The humidity for port hedland is: 86
    The cloudiness for port hedland is: 64
    The wind speed for port hedland is: 1.49
    The latitude for port hedland is: -17.21973549073411
    hilo
    us
    The temperature for hilo is: 297.15
    The humidity for hilo is: 83
    The cloudiness for hilo is: 90
    The wind speed for hilo is: 2.6
    The latitude for hilo is: 13.761695551531318
    nanortalik
    gl
    The temperature for nanortalik is: 272.593
    The humidity for nanortalik is: 96
    The cloudiness for nanortalik is: 8
    The wind speed for nanortalik is: 5.84
    The latitude for nanortalik is: 57.417915373302435
    koungou
    yt
    The temperature for koungou is: 300.15
    The humidity for koungou is: 78
    The cloudiness for koungou is: 0
    The wind speed for koungou is: 3.6
    The latitude for koungou is: -9.772912284317414
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -52.3579515457328
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 28.28717937698616
    edmundston
    ca
    The temperature for edmundston is: 291.15
    The humidity for edmundston is: 22
    The cloudiness for edmundston is: 1
    The wind speed for edmundston is: 5.1
    The latitude for edmundston is: 47.823697628528066
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -66.64903446888093
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -15.319313313592403
    kanadukathan
    in
    The temperature for kanadukathan is: 296.493
    The humidity for kanadukathan is: 85
    The cloudiness for kanadukathan is: 0
    The wind speed for kanadukathan is: 1.14
    The latitude for kanadukathan is: 10.258055798499896
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: 2.249258002839653
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 9.485971239627887
    okha
    ru
    The temperature for okha is: 274.143
    The humidity for okha is: 84
    The cloudiness for okha is: 24
    The wind speed for okha is: 7.51
    The latitude for okha is: 55.157375509088354
    saskylakh
    ru
    The temperature for saskylakh is: 261.243
    The humidity for saskylakh is: 86
    The cloudiness for saskylakh is: 64
    The wind speed for saskylakh is: 5.51
    The latitude for saskylakh is: 77.70143914342685
    bambous virieux
    mu
    The temperature for bambous virieux is: 297.15
    The humidity for bambous virieux is: 88
    The cloudiness for bambous virieux is: 75
    The wind speed for bambous virieux is: 2.1
    The latitude for bambous virieux is: -26.370543197391598
    yellowknife
    ca
    The temperature for yellowknife is: 277.143
    The humidity for yellowknife is: 94
    The cloudiness for yellowknife is: 92
    The wind speed for yellowknife is: 5.56
    The latitude for yellowknife is: 80.78288113519898
    nome
    us
    The temperature for nome is: 300.15
    The humidity for nome is: 39
    The cloudiness for nome is: 1
    The wind speed for nome is: 3.1
    The latitude for nome is: 65.34008133908833
    butaritari
    ki
    The temperature for butaritari is: 301.843
    The humidity for butaritari is: 99
    The cloudiness for butaritari is: 80
    The wind speed for butaritari is: 3.29
    The latitude for butaritari is: 21.57291212476086
    kapaa
    us
    The temperature for kapaa is: 298.15
    The humidity for kapaa is: 69
    The cloudiness for kapaa is: 1
    The wind speed for kapaa is: 2.6
    The latitude for kapaa is: 15.37864542006406
    det udom
    th
    The temperature for det udom is: 296.993
    The humidity for det udom is: 96
    The cloudiness for det udom is: 80
    The wind speed for det udom is: 2.86
    The latitude for det udom is: 14.00908072094552
    san patricio
    mx
    The temperature for san patricio is: 302.193
    The humidity for san patricio is: 61
    The cloudiness for san patricio is: 0
    The wind speed for san patricio is: 2.36
    The latitude for san patricio is: 1.790225680408156
    tual
    id
    The temperature for tual is: 301.993
    The humidity for tual is: 100
    The cloudiness for tual is: 76
    The wind speed for tual is: 6.34
    The latitude for tual is: -4.968380846981063
    ambunti
    pg
    The temperature for ambunti is: 297.293
    The humidity for ambunti is: 100
    The cloudiness for ambunti is: 92
    The wind speed for ambunti is: 1.11
    The latitude for ambunti is: -4.845261805206434
    ziyang
    cn
    The temperature for ziyang is: 287.893
    The humidity for ziyang is: 98
    The cloudiness for ziyang is: 100
    The wind speed for ziyang is: 4.96
    The latitude for ziyang is: 29.913282135488757
    busselton
    au
    The temperature for busselton is: 287.743
    The humidity for busselton is: 100
    The cloudiness for busselton is: 8
    The wind speed for busselton is: 1.71
    The latitude for busselton is: -73.56071946008709
    ixtapa
    mx
    The temperature for ixtapa is: 302.993
    The humidity for ixtapa is: 47
    The cloudiness for ixtapa is: 0
    The wind speed for ixtapa is: 1.29
    The latitude for ixtapa is: 9.183793703523136
    pevek
    ru
    The temperature for pevek is: 262.193
    The humidity for pevek is: 91
    The cloudiness for pevek is: 0
    The wind speed for pevek is: 1.51
    The latitude for pevek is: 79.19378898685454
    quelimane
    mz
    The temperature for quelimane is: 297.15
    The humidity for quelimane is: 83
    The cloudiness for quelimane is: 20
    The wind speed for quelimane is: 2.1
    The latitude for quelimane is: -19.69564543641428
    bay city
    us
    The temperature for bay city is: 291.15
    The humidity for bay city is: 59
    The cloudiness for bay city is: 90
    The wind speed for bay city is: 4.6
    The latitude for bay city is: 43.623566849250864
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -78.63197082982921
    ribeira grande
    pt
    The temperature for ribeira grande is: 290.543
    The humidity for ribeira grande is: 99
    The cloudiness for ribeira grande is: 32
    The wind speed for ribeira grande is: 3.19
    The latitude for ribeira grande is: 28.70312437239042
    nikolskoye
    ru
    The temperature for nikolskoye is: 277.993
    The humidity for nikolskoye is: 92
    The cloudiness for nikolskoye is: 92
    The wind speed for nikolskoye is: 2.51
    The latitude for nikolskoye is: 38.82096684670472
    ilulissat
    gl
    The temperature for ilulissat is: 272.15
    The humidity for ilulissat is: 80
    The cloudiness for ilulissat is: 75
    The wind speed for ilulissat is: 2.1
    The latitude for ilulissat is: 76.48225177379626
    pierre
    us
    The temperature for pierre is: 278.15
    The humidity for pierre is: 86
    The cloudiness for pierre is: 90
    The wind speed for pierre is: 7.7
    The latitude for pierre is: 44.43752333305082
    ajdabiya
    ly
    The temperature for ajdabiya is: 289.593
    The humidity for ajdabiya is: 64
    The cloudiness for ajdabiya is: 0
    The wind speed for ajdabiya is: 4.19
    The latitude for ajdabiya is: 30.1537104667549
    calama
    cl
    The temperature for calama is: 298.15
    The humidity for calama is: 16
    The cloudiness for calama is: 0
    The wind speed for calama is: 11.8
    The latitude for calama is: -23.653145841744575
    bluff
    nz
    The temperature for bluff is: 285.743
    The humidity for bluff is: 95
    The cloudiness for bluff is: 76
    The wind speed for bluff is: 9.14
    The latitude for bluff is: -71.090300130142
    ribeira grande
    pt
    The temperature for ribeira grande is: 290.543
    The humidity for ribeira grande is: 99
    The cloudiness for ribeira grande is: 32
    The wind speed for ribeira grande is: 3.19
    The latitude for ribeira grande is: 28.37724925456496
    yellowknife
    ca
    The temperature for yellowknife is: 277.143
    The humidity for yellowknife is: 94
    The cloudiness for yellowknife is: 92
    The wind speed for yellowknife is: 5.56
    The latitude for yellowknife is: 84.71068900423916
    port alfred
    za
    The temperature for port alfred is: 289.843
    The humidity for port alfred is: 100
    The cloudiness for port alfred is: 32
    The wind speed for port alfred is: 1.39
    The latitude for port alfred is: -50.98527427457037
    mittagong
    au
    The temperature for mittagong is: 280.993
    The humidity for mittagong is: 95
    The cloudiness for mittagong is: 0
    The wind speed for mittagong is: 1.14
    The latitude for mittagong is: -34.15098958534275
    albany
    au
    The temperature for albany is: 282.693
    The humidity for albany is: 91
    The cloudiness for albany is: 8
    The wind speed for albany is: 2.34
    The latitude for albany is: -77.24158242986495
    punta arenas
    cl
    The temperature for punta arenas is: 284.15
    The humidity for punta arenas is: 53
    The cloudiness for punta arenas is: 0
    The wind speed for punta arenas is: 9.3
    The latitude for punta arenas is: -74.26677932554635
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -39.17973207116866
    kirillov
    ru
    The temperature for kirillov is: 273.693
    The humidity for kirillov is: 61
    The cloudiness for kirillov is: 32
    The wind speed for kirillov is: 5.34
    The latitude for kirillov is: 60.39455579880294
    mar del plata
    ar
    The temperature for mar del plata is: 287.643
    The humidity for mar del plata is: 47
    The cloudiness for mar del plata is: 0
    The wind speed for mar del plata is: 5.79
    The latitude for mar del plata is: -56.0286066228256
    hamilton
    bm
    The temperature for hamilton is: 292.193
    The humidity for hamilton is: 100
    The cloudiness for hamilton is: 48
    The wind speed for hamilton is: 8.91
    The latitude for hamilton is: 30.714734022661688
    ulladulla
    au
    The temperature for ulladulla is: 290.143
    The humidity for ulladulla is: 100
    The cloudiness for ulladulla is: 0
    The wind speed for ulladulla is: 2.41
    The latitude for ulladulla is: -39.802268427948746
    vardo
    no
    The temperature for vardo is: 276.643
    The humidity for vardo is: 94
    The cloudiness for vardo is: 76
    The wind speed for vardo is: 6.56
    The latitude for vardo is: 85.76211865423133
    port hawkesbury
    ca
    The temperature for port hawkesbury is: 284.143
    The humidity for port hawkesbury is: 56
    The cloudiness for port hawkesbury is: 24
    The wind speed for port hawkesbury is: 5.04
    The latitude for port hawkesbury is: 38.48121030791003
    atuona
    pf
    The temperature for atuona is: 300.643
    The humidity for atuona is: 100
    The cloudiness for atuona is: 0
    The wind speed for atuona is: 6.44
    The latitude for atuona is: 4.883677330793688
    ushuaia
    ar
    The temperature for ushuaia is: 285.15
    The humidity for ushuaia is: 54
    The cloudiness for ushuaia is: 40
    The wind speed for ushuaia is: 7.7
    The latitude for ushuaia is: -64.64718412484474
    hithadhoo
    mv
    The temperature for hithadhoo is: 302.843
    The humidity for hithadhoo is: 100
    The cloudiness for hithadhoo is: 92
    The wind speed for hithadhoo is: 7.41
    The latitude for hithadhoo is: -19.109184449380322
    hermanus
    za
    The temperature for hermanus is: 282.043
    The humidity for hermanus is: 93
    The cloudiness for hermanus is: 24
    The wind speed for hermanus is: 0.81
    The latitude for hermanus is: -83.25634997525678
    tazovskiy
    ru
    The temperature for tazovskiy is: 264.243
    The humidity for tazovskiy is: 83
    The cloudiness for tazovskiy is: 92
    The wind speed for tazovskiy is: 1.39
    The latitude for tazovskiy is: 66.8330504813498
    rikitea
    pf
    The temperature for rikitea is: 298.693
    The humidity for rikitea is: 100
    The cloudiness for rikitea is: 56
    The wind speed for rikitea is: 9.41
    The latitude for rikitea is: -38.7094854932936
    chapais
    ca
    The temperature for chapais is: 282.543
    The humidity for chapais is: 71
    The cloudiness for chapais is: 88
    The wind speed for chapais is: 1.96
    The latitude for chapais is: 54.09148188599448
    vaini
    to
    The temperature for vaini is: 298.543
    The humidity for vaini is: 100
    The cloudiness for vaini is: 8
    The wind speed for vaini is: 7.24
    The latitude for vaini is: -83.57308369114904
    pirovskoye
    ru
    The temperature for pirovskoye is: 273.393
    The humidity for pirovskoye is: 95
    The cloudiness for pirovskoye is: 48
    The wind speed for pirovskoye is: 2.74
    The latitude for pirovskoye is: 57.699109019869724
    upernavik
    gl
    The temperature for upernavik is: 270.393
    The humidity for upernavik is: 100
    The cloudiness for upernavik is: 88
    The wind speed for upernavik is: 2.11
    The latitude for upernavik is: 88.5926983675337
    saint george
    bm
    The temperature for saint george is: 292.193
    The humidity for saint george is: 100
    The cloudiness for saint george is: 48
    The wind speed for saint george is: 8.91
    The latitude for saint george is: 27.57844106194031
    kruisfontein
    za
    The temperature for kruisfontein is: 286.493
    The humidity for kruisfontein is: 89
    The cloudiness for kruisfontein is: 0
    The wind speed for kruisfontein is: 1.84
    The latitude for kruisfontein is: -55.332575572682074
    


```python
Temps = {
    "Latitude": latitude_list,
    "Humidity": humidity_list,
    "City": city_list,
    "Cloudiness": cloudiness_list,
    "Country": country_list,
    "Max Temperature": temp_list,
    "Wind Speed": wind_speed_list,
    "Latitude": latitude_list,
    "Longitude": longitude_list,
    "Date": date_list
}
Temps_df = pd.DataFrame(data=Temps)
Temps_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Cloudiness</th>
      <th>Country</th>
      <th>Date</th>
      <th>Humidity</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Max Temperature</th>
      <th>Wind Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>seminole</td>
      <td>1</td>
      <td>us</td>
      <td>1524597300</td>
      <td>11</td>
      <td>27.618262</td>
      <td>-83.666757</td>
      <td>306.150</td>
      <td>5.10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>dalton</td>
      <td>90</td>
      <td>us</td>
      <td>1524600000</td>
      <td>63</td>
      <td>34.854226</td>
      <td>-84.867577</td>
      <td>294.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>2</th>
      <td>atuona</td>
      <td>0</td>
      <td>pf</td>
      <td>1524600707</td>
      <td>100</td>
      <td>-12.593860</td>
      <td>-125.936151</td>
      <td>300.643</td>
      <td>6.44</td>
    </tr>
    <tr>
      <th>3</th>
      <td>souillac</td>
      <td>75</td>
      <td>mu</td>
      <td>1524596400</td>
      <td>88</td>
      <td>-50.907224</td>
      <td>74.738352</td>
      <td>297.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>petatlan</td>
      <td>8</td>
      <td>mx</td>
      <td>1524600968</td>
      <td>82</td>
      <td>15.046688</td>
      <td>-102.078873</td>
      <td>301.643</td>
      <td>4.71</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.scatter(temp_list, latitude_list, facecolors="red", edgecolors="black", linewidth=1, marker='o', alpha=0.8)
plt.title('Temperature (F) vs. Latitude')
plt.xlabel("Latitude")
plt.ylabel('Max Temperature')
plt.savefig("Temperature_(F)_vs._Latitude.png")
plt.show()
```


![png](output_4_0.png)



```python
plt.scatter(humidity_list, latitude_list, facecolors="purple", edgecolors="black", linewidth=1, marker='o', alpha=0.8)
plt.title('Humidity(%) vs. Latitude')
plt.xlabel("Latitude")
plt.ylabel('Humidity')
plt.savefig("Humidity_(%)_vs._Latitude.png")
plt.show()
```


![png](output_5_0.png)



```python
plt.scatter(cloudiness_list, latitude_list, facecolors="blue", edgecolors="black", linewidth=1, marker='o', alpha=0.8)
plt.title('Cloudiness (%) vs. Latitude')
plt.xlabel("Latitude")
plt.ylabel('Cloudiness (%)')
plt.savefig("Cloudiness_(%)_vs._Latitude.png")
plt.show()
```


![png](output_6_0.png)



```python
plt.scatter(wind_speed_list, latitude_list, facecolors="green", edgecolors="black", linewidth=1, marker='o', alpha=0.8)
plt.title('Wind Speed (mph) vs.Latitude')
plt.xlabel("Latitude")
plt.ylabel('Wind Speed (mph)')
plt.savefig("Wind_Speed_(mph)_vs._Latitude.png")
plt.show()
```


![png](output_7_0.png)



```python
Temps_df.to_csv("WeatherAPI.csv", encoding='utf-8', index=False)

```
