# What is this?
This is a simple proof-of-concept which allows users to do very basic integration between their [Home-Assistant](https://www.home-assistant.io/) and [Camect](https://camect.com/) using the [Home-Assistant Community Store (aka HACS)](https://hacs.xyz/)

**I did NOT create this integration**. I simply created *this* repo to simplify the installation of the integration via [Home Assistant Community Store (aka HACS)](https://hacs.xyz/). The original proof-of-concept integration (written by one of the Camect developers) is located [HERE](https://github.com/camect/home-assistant-integration). The Camect developers don't use Home Assistant and have no desire to maintain or improve the integration or custom card. They hope that users in the Home Assistant community will take on the responsibility to improve it and keep it up-to-date with Home Assistant. **I am not a developer**, so I'm incapable of doing so.

## Prerequisites:
- A [Camect](https://camect.com) Home Security recorder
- [Home Assistant](https://home-assistant.io)
- [Home Assistant Community Store (HACS)](https://hacs.xyz)

## Installation Steps:
- Add this repo to HACS (as type "integration")
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
**NOTE** Your camera_ids can be found in the Camect web GUI. Click the camera settings icon, and select the **<sup>i</sup>** next to the Camera Name header. You will find the id for that camera in the pop-up window.
- Check your config
- Restart Home Assistant


To view the Camect streams within the Lovelace interface, use the HACS-camect-custom_card for Lovelace at https://github.com/pfunkmallone/HACS-camect-custom_card
