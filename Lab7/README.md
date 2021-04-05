# Lab 7: Cloud Platforms

## ThingSpeak

After creating cpu_loop channel with cpu_pc and mem_avail_mb fields and using my API key, thingspeak_feed.py generates this:

![image](https://user-images.githubusercontent.com/32800667/113621931-4bd56080-962a-11eb-9f19-6ccef10a35b8.png)

## Google Sheets

- Use Google Cloud Platform
- Credential > Create Credentials > Create service account key > Service account > rpidata > JSON key type > Create > download rpidata-xxxxxxxxxxxx.json
- Transfer the json file to the rpi
- Edit the rpi_spreadsheet.py file to the following:

![image](https://user-images.githubusercontent.com/32800667/113622450-05343600-962b-11eb-8b5b-6de6b42ffbb3.png)

Running rpi_spreadsheet.py yields the following:

![image](https://user-images.githubusercontent.com/32800667/113623621-9b1c9080-962c-11eb-98c4-85d1053db331.png)


