# HomeAssistant_DSMR_SolarEdge
Combine DSMR and SolarEdge to calculate power consumption and production.

After installing solar panels on my roof I wanted to get more info on the power consumption and production in Home Assistant.
The obvious step was to include the two data sources:
- SolarEdge Monitoring API [https://www.home-assistant.io/integrations/solaredge]
- DSMR Slimme Meter [https://www.home-assistant.io/integrations/dsmr]

Based on the discussion in the [thread in the Home Assistant Community](https://community.home-assistant.io/t/how-to-calculate-daily-power-consumption-from-dsmr-sensors/37696/11) I created an expanded version.
My version supports Low and Normal tarifs, and also power consumption and power production. The naming of the entities has become a mixture of English and Dutch:
- Tarif1, aka Low, in Dutch written as 'Laag' 
- Tarif2, aka Normal, aka High, in Dutch written as 'Hoog' 

Every midnight the counters are reset. Beware that SolarEdge allows for a limited number of API calls per day. The displayed solar power produced will have a slight delay as it is updated once every 10 minutes. Because of that the Lovelace card will temporarily show old data shortly after the reset at midnight.

## Installing
* Create a backup and download it to your computer: Supervisor -> Snapshots
* Open the File Editor in Home Assistant
* Modify the files `automations.yaml` and `configuration.yaml` by adding the content
* Create a file `input_number.yaml` in the folder `config` and copy the contents of the file to it
* Validate your configuration: Configuration -> Server Controls -> Check configuration
* Restart Home Assistant
* Add a card in Lovelace
* Put the card in yaml edit mode and replace the content with the contents of the card-file


## Example
![Example of Lovelace card](/images/example.png)
