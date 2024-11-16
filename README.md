# EXPERIMENT-05-TRANSFERRING-DATA-TO-IOT-NETWORK-USING-API-KEY

### NAME: YUVARANI T
### REGISTER NUMBER:212222110057
### DEPARTMENT:BE CSE(IOT)
### YEAR: III

## Aim:
To transfer sensor data to an IoT platform (ThingSpeak) using an API key.

## Apparatus Required:
ThingSpeak Channel ID and Write API Key: A valid ThingSpeak account and API key.
Microcontroller (e.g., ESP32/ESP8266, NodeMCU, etc.): For collecting sensor data and transmitting it to ThingSpeak.
Sensor Modules (e.g., Temperature, Humidity, etc.): For data collection.
Computer System: For writing and uploading the code to the microcontroller.
Internet Connection: To send the data to the ThingSpeak platform.
Theory:
IoT networks enable the exchange of data between devices through the internet. ThingSpeak is an IoT analytics platform that allows users to collect, store, and visualize sensor data using API keys. In this experiment, we use the ThingSpeak API to send sensor data periodically, allowing remote monitoring and analysis.

## Procedure:
Setup ThingSpeak Channel:</br>

Create a ThingSpeak account and generate a channel with the required fields (e.g., temperature, humidity).
Obtain the Write API Key for your channel, which is used for sending data.

Setup the Microcontroller and Sensors:</br>

Connect the required sensors (e.g., temperature sensor, humidity sensor) to the microcontroller.
Ensure the microcontroller is connected to the internet (using Wi-Fi or Ethernet).

Code for Sending Data:</br>

Write a Python script (or Arduino code, depending on the platform) to read data from sensors.
Construct the URL to send data to ThingSpeak using the API key and channel ID.
Use the requests library to send HTTP POST requests containing sensor data to ThingSpeak.
Code Implementation: Here’s the Python code that reads sensor data and sends it to ThingSpeak:

## python
```
import requests
import time
channel_id = "2746398"
write_api_key = "ZU0LOM1J0IRXI17A" 
url = f"https://api.thingspeak.com/update?api_key={write_api_key}"
field_1 = 23.5 
field_2 = 65    
payload = {
    'field1': field_1,
    'field2': field_2
}
def send_to_thingspeak(payload):
    try:
        response = requests.post(url, params=payload)
        if response.status_code == 200:
            print(f"Data sent successfully: {payload}")
        else:
            print(f"Failed to send data. Status Code: {response.status_code}")
    except Exception as e:
        print(f"Error: {e}")
while True:
    send_to_thingspeak(payload)
    time.sleep(15)
``` 

## Outputs:

![iiot(frount)](https://github.com/user-attachments/assets/0d7293b1-4106-44f3-be5f-dd64a4e58b44)

![iiot(api)](https://github.com/user-attachments/assets/5f367597-7943-4fbb-9c47-0dcc9fe0504b)

## Simulation Screenshots:

![Screenshot 2024-11-15 084445](https://github.com/user-attachments/assets/10a1be3e-ccaa-4520-9c2f-e3c1427414ae)

![Screenshot 2024-11-15 084159](https://github.com/user-attachments/assets/910add0e-fea3-42b5-ae24-d8d091e1d72a)

## Results:
The sensor data was successfully transferred to the ThingSpeak IoT platform using an API key. The experiment demonstrated how to send data from sensors to an IoT network and visualize it remotely using ThingSpeak. The periodic data updates were successfully logged and displayed on the ThingSpeak platform.
