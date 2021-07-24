# optimising-unifi-performance
Below are the key settings that I apply on any unifi installation for optimal performance.

This guide makes the following assumptions:
- You are located in Australia
- You have multiple U6-Lite access points.
- They are positioned appropriately per a professional site survey.
- You are using the latest controller software as of time of writing.

## Settings

### Settings > WiFi > YOUR-NETWORK-HERE > Advanced
- Ensure `UAPSD` is enabled
- Ensure `BSS Transition` is enabled
- Ensure `Enable Fast Roaming` is enabled

### Settings WiFi > YOUR-NETWORK-HERE > Advanced > Security
- Ensure `Security Protocol` is set to `WPA-2`
- Ensure `PMF` is set to `Disabled`
- Ensure `Group Rekey Interval` is configured appropriately:
  - `Group Rekey Interval`: Enabled
  - `GTK Rekeying every`: 3600 seconds

### Settings WiFi > YOUR-NETWORK-HERE > Advanced > 802.11 Rate and Beacon Controls
- Ensure `Override DTIM Period` is enabled
  - Ensure `DTIM 2G Period` is set to 3
  - Ensure `DTIM 5G Period` is set to 3
  - Ensure `2G Data Rate Control` is disabled
  - Ensure `5G Data Rate Control` is disabled

### Settings > Systems Settings > Maintenance

- Ensure `Automatic Firmware Upgrades` is enabled

### Settings > System Settings > Backup / Restore

- Ensure `Backup Scheduler` is configured appropriately:
  - Every: Month
  - On The: 1
  - At: 12 0 AM
  - Data Retention Days: Settings Only
  - Maximum number of Files: 6

### Settings > Advanced Features > WiFi AI

- Ensure `WiFi AI` is configured appropriately:
  - `WiFi AI`: enabled
  - `Frequency`: Daily
  - `Scan Time`: 5 30 AM
  - `Advanced Settings` > `Exclude 2.4GHz Channels`: 2, 3, 4, 5, 7, 8, 9, 10, 12, 13

## Devices

Complete this section for each access point you have.

### Devices > YOUR-ACCESS-POINT-HERE > RF
- Ensure the 2.4GHz Radio is configured appropriately:
  - `Channel Width`: HT20
  - `Channel`: 1, 6, or 11
  - `Transit Power`: Auto
  - `Enable Minimum RSSI`: Disabled
- Ensure the 5GHz Radio is configured appropriately:
  - `Channel Width`: HT80
  - `Channel`: 36, 40, 44, 48, or 153
  - `Transit Power`: Auto
  - `Enable Minimum RSSI`: Disabled
- Ensure `Band Steering` is set to Prefer 5G
