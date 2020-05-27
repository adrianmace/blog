# optimising-unifi-performance
Below are the key settings that I apply on any unifi installation for optimal performance.

## Settings
### Settings > Site
- Ensure `Enable Advanced Features` is enabled  
This allows you to follow along with the guide in it's entirety.

- Ensure `Automatically Optimise Network and WiFi performance` is disabled  
These settings will do a better job.

### Settings > Wireless Networks > YOUR-NETWORK-HERE > Edit
- Ensure `Fast Roaming` is disabled  
It creates a lot more 'noise' on the dashboard in the form of anomalies when you have more than one access point within a home environment, and is useless if you only have a single one.  
At the time of writing it's also a BETA feature.

- Ensure `Combine 2 GHz and 5 GHz WiFi Network Names into one` is enabled  
With these optimised settings you'll see devices only using 2.4GHz if they either a) don't support 5GHz (thanks Google!) or b) are too far away to maintain a reliable connection.

- Ensure `Connects high performance clients to 5 GHz only` is disabled  
With these optimised settings you'll see devices always prefer 5GHz, and at the time of writing, the current method to detect 'high performance clients' is not reliable.

- Ensure `DTIM Mode` default values is disabled  
This is the interval in which the access point polls the devices to check if they're alive. For many Apple / iOS devices, this causes them to not sleep correctly which both causes anomalies on the dashboard and kills the device battery life.
  - Set DTIM 2G Period to 3
  - Set DTIM 5G Period to 3

### Settings > Try New Settings > WiFi AI
- Ensure `Enable WiFi AI` is disabled  
This is a great feature, but I found it to be choosing channels that were DFS (radar in the area causes intermittent dropouts of your network) or just not selecting channels 1 / 6 / 11.

## Devices
### Devices > YOUR-ACCESS-POINT-HERE > Config > Radios
- Ensure `Channel Width` is set to the following
  - Radio 2G should be set to `HT20`
  - Radio 5G should be set to `VHT80` or `VHT160` (HD series)  

- Ensure `Transmit Power` is set to the following
  - Radio 2G should be set to `Medium`
  - Radio 5G should be set to `High`

- Ensure `Channel` is set appropriately  
Run a WiFi scanning utility and pick the least congested channel. This is outside the scope of this doc.

### Devices > YOUR-ACCESS-POINT-HERE > Config > Band Steering
- Ensure `Band Steering` is set to Prefer 5G  
This ensures that clients will connect on the 5GHz channel when available.

### Devices > YOUR-ACCESS-POINT-HERE > Config > Airtime Fairness
- Ensure `Airtime Fairness` is set to On  
This ensures that the access point shares data between connected clients on a time division multiplexing basis, rather than the default which allows a certain amount of bandwidth to be transferred before moving on.  
_In practice if this is not enabled, a small Raspberry Pi connected to a far-away AP at 54Mbps will drag every other connected device's effective bandwidth down to 54Mbps until the Pi is powered off or moved to a different AP._