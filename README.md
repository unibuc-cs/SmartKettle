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

#### 3. Make tea

POST /makeTea

#### 4. Set a recurrent boiling schedule 
POST /warmLiquidByDate

#### 5. Stir the liquid at the specified rpm
GET /stirLiquid/rmp

 

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

3. Get viscosity of the containing liquid and the recommended temperature

```bash
mosquitto_sub -t kettle/viscosity -C 1
```




