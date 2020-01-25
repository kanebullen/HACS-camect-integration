# Integrate Camect with home-assistant
======================================

## Configure
Please follow the following instructions:
- Copy file "camect-card.js" to $ha_config_dir/www.
- Copy folder "camect" to $ha_config_dir/custom_components.
- Add following to $ha_config_dir/configuration.yaml
```yaml
camect:
  - host: YOUR_CAMECT_HOME_LOCAL_IP
    port: 443
    username: admin
    password: admin_PASSWORD
    camera_ids: YOUR_CAMERA_IDS_SEPARATED_BY_COMMA
    id: (optional)    // provide this is you have multiple device so you could
                      // tell which camera is from which home.
```
Your camera_ids can be found in the Camect web GUI. Click the camera settings icon, and select the **<sup>i</sup>** next to the Camera Name header. You will find the id for that camera in the pop-up window.

- If you are using lovelace, put following into $ha_config_dir/ui-lovelace.yaml
```yaml
resources:
  - url: /local/camect-card.js
    type: module

views:
  - title: Camect
    cards:
      - type: "custom:camect-card"
        entity: camera.camect_YOUR_CAMERA_ID
```
  If you don't have ui-lovelace.yaml yet, add the following into $ha_config_dir/configuration.yaml
```yaml
lovelace:
   mode: yaml
```

## Listen to events
<pre>
hass.bus.listen('camect_event', lambda evt: print(evt))
</pre>
Sample event:
<pre>
type=alert
desc=Camera Driveway just saw a car.
url=https://home.camect.com/home/xxxxxxxx/camera?id=yyyyyyy&ts=1556228517560
</pre>
