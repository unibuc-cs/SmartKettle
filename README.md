# Smart Kettle App

### Requirements

```asm
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
```asm
g++ smart_kettle.cpp -o main -lpistache -Lmosquitto -lcrypto -lssl -lpthread  -std=c++17

./main
```


