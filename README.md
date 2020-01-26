## What is this?
This is a simple proof-of-concept which allows users to do basic integration between their [Home-Assistant](https://www.home-assistant.io/) and [Camect](https://camect.com/) using the [Home-Assistant Community Store (aka HACCS)](https://hacs.xyz/)

I did NOT create the integration. I simply created *this* repo to simplify the installation of the integration through the use of HACS.

Once you've installed this via HACS, you must still add following to $ha_config_dir/configuration.yaml

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

To view the Camect streams within the Lovelace interface, use the HACS-camect-home-assistant-custom_card for Lovelace at https://github.com/pfunkmallone/HACS-camect-home-assistant-custom_card
