# Smart Kettle App

### Requirements

```bash
// boost
sudo apt-get install libboost-dev

// g++
sudo apt install g++


// nlohmann - json formatter
sudo apt-get install nlohmann-json3-dev

// Pistache
sudo add-apt-repository ppa:pistache+team/unstable
sudo apt update
sudo apt install libpistache-dev
```

### Compile and run

```bash
g++ smart_kettle.cpp -o main -lpistache -lmosquitto -lcrypto -lssl -lpthread  -std=c++17

./main
```

### HHTP

#### 1. Warm liquid at the specified temperature

GET /warmLiquid/temperature/scale

#### 2. Find the viscosity of the containing liquid and set the recommended boiling temperature

GET /boilLiquidByViscosity

The kettle uses the information from the viscosity sensor to find the optimal temperature of the containing liquid.

```json
{
  "message": "The temperature has been set to 90 degrees",
  "timestamp": "Tue May 25 09:27:18 2021"
}
```

#### 3. Make tea

POST /makeTea
<hr/>
The kettle boils the water to the specified temperature, inserts the tea infuser into the water for a certain amount of time and after the infusion it keeps your tea warm.

Input format:

```json
{
  "keepWarm": true,
  "temperature": {
    "temperature": "100",
    "scale": "C"
  },
  "time": 5
}
```

Output format:

```json
{
  "message": "Preparing your tea...The temperature has been set to 100 C degrees. Infusion time: 5 minutes. ",
  "timestamp": "Tue May 25 09:33:03 2021"
}
```

#### 4. Set a recurrent boiling schedule

POST /warmLiquidByDate
<hr/>

Set a recurring event if you want to prepare your drink at a certain hour of the day.

Input format:

```json
{
  "recurrent": true,
  "temperature": {
    "temperature": "30",
    "scale": "F"
  },
  "hour": "22:30"
}
```

Output format:

```json

{
  "message": "Scheduler is set at 22:30. Temperature: 50 degrees F. ",
  "timestamp": "Tue May 25 09:41:48 2021"
}
```

#### 5. Stir the liquid at the specified rpm

GET /stirLiquid/rmp
<hr/> 


### MQTT

#### 1. Required libraries

```bash
sudo apt install mosquitto
sudo apt install mosquitto-client
```

#### 2. Interacting with the device

1. Warm tea

```bash
mosquitto_sub -t kettle/temp/70/C -C 1
```

2. Get scheduler settings

```bash
mosquitto_sub -t kettle/scheduler -C 1
```

3. Get viscosity of the coWntaining liquid and the recommended temperature

```bash
mosquitto_sub -t kettle/viscosity -C 1
```


### Team Members
<hr/>

- Busuioc Andrei
- Iamandii Ana-Maria
- Manea Cristina Larisa
- Nazare Daniela Andreea
- Rusu Iuliana
- Talmacel Sergiu-Victor



