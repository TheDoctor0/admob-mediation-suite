# Cordova AdMob Mediation Suite

A smart, dynamic, and lightweight Cordova plugin to manage Google AdMob Mediation adapters for Android and iOS. 

This plugin dynamically injects only the mediation adapters you explicitly enable, ensuring your app remains lightweight and free of unnecessary SDK bloat. It also supports custom adapter versions and automatically handles `AndroidManifest.xml`, `build.gradle`, `Podfile`, and `Info.plist` injections.

---

## ⚠️ Prerequisites

**Important:** This plugin is an add-on and **will not work** without a compatible core AdMob plugin installed in your project. 

Please install one of the following recommended and compatible Cordova AdMob plugins before using this mediation suite:
* [community-admob-plus](https://github.com/EYALIN/community-admob-plus)
* [cordova-plugin-admob-nextgen](https://github.com/swaplab-engine/cordova-plugin-admob-nextgen)
* [admob-plus](https://github.com/admob-plus/admob-plus)
* [emi-indo-cordova-plugin-admob](https://github.com/EMI-INDO/emi-indo-cordova-plugin-admob)

---

## 🚀 Installation

### 1. Install your preferred Core AdMob Plugin
*Example using `community-cordova-plugin-admob`:*
```bash
cordova plugin add community-cordova-plugin-admob \
--variable APP_ID_ANDROID=ca-app-pub-xxxxxxxxxxxxxxxx~yyyyyyyyyy \
--variable APP_ID_IOS=ca-app-pub-xxxxxxxxxxxxxxxx~yyyyyyyyyy
```

### 2. Install AdMob Mediation Suite
Install this plugin and enable the specific ad networks you want to mediate. Only the enabled networks will be compiled into your app.

*Example: Enabling AppLovin and Meta (Facebook) Audience Network:*
```bash
cordova plugin add admob-mediation-suite --save \
--variable ENABLE_APPLOVIN="true" \
--variable KEY_APPLOVIN="YOUR_APPLOVIN_SDK_KEY" \
--variable ENABLE_FACEBOOK="true"
```

---

## ⚙️ Configuration Variables

You can customize the mediation networks by passing variables during installation. 

### Network Toggles
Set to `"true"` to enable the respective mediation adapter. By default, all networks are disabled (`false`).

| Network | Variable Name | Required Extra Variables |
| :--- | :--- | :--- |
| **Meta (Facebook)** | `ENABLE_FACEBOOK` | - |
| **AppLovin** | `ENABLE_APPLOVIN` | `KEY_APPLOVIN="Your_AppLovin_Key"` |
| **Unity Ads** | `ENABLE_UNITY` | - |
| **IronSource** | `ENABLE_IRONSOURCE` | - |
| **Vungle (Liftoff)**| `ENABLE_VUNGLE` | - |

> **Note on AppLovin:** If you enable AppLovin, you **must** provide your AppLovin SDK Key using the `KEY_APPLOVIN` variable. The plugin will intelligently inject this key into your Android `AndroidManifest.xml` and iOS `Info.plist`.

### Customizing Adapter Versions
The plugin uses tested default adapter versions. However, if you need to use a specific version of a mediation adapter, you can override the defaults using the following variables:

**Android Version Variables:**
* `VER_ANDROID_FACEBOOK` (Default: 6.16.0.0)
* `VER_ANDROID_APPLOVIN` (Default: 11.11.3.0)
* `VER_ANDROID_UNITY` (Default: 4.9.2.0)
* `VER_ANDROID_VUNGLE` (Default: 7.4.3.0)
* `VER_ANDROID_IRONSOURCE` (Default: 8.7.0.0)

**iOS Version Variables:**
* `VER_IOS_FACEBOOK` (Default: 6.12.0.0)
* `VER_IOS_APPLOVIN` (Default: 11.11.3.0)
* `VER_IOS_UNITY` (Default: 4.9.0.0)
* `VER_IOS_VUNGLE` (Default: 7.4.4.0)
* `VER_IOS_IRONSOURCE` (Default: 8.7.0.0.0)

*Example overriding a version:*
```bash
cordova plugin add admob-mediation-suite \
--variable ENABLE_UNITY="true" \
--variable VER_ANDROID_UNITY="4.10.0.0"
```

---

## 📖 Step-by-Step AdMob UI Setup

Enabling the adapters in your app is only half the process. You must also configure the mediation groups and eCPM details inside your Google AdMob Dashboard. 

Follow the official Google AdMob step-by-step guides for the networks you enabled:

* **AppLovin:** [Android Setup](https://developers.google.com/admob/android/mediation/applovin) | [iOS Setup](https://developers.google.com/admob/ios/mediation/applovin)
* **Meta (Facebook):** [Android Setup](https://developers.google.com/admob/android/mediation/meta) | [iOS Setup](https://developers.google.com/admob/ios/mediation/meta)
* **Unity Ads:** [Android Setup](https://developers.google.com/admob/android/mediation/unity) | [iOS Setup](https://developers.google.com/admob/ios/mediation/unity)
* **ironSource:** [Android Setup](https://developers.google.com/admob/android/mediation/ironsource) | [iOS Setup](https://developers.google.com/admob/ios/mediation/ironsource)
* **Pangle:** [Android Setup](https://developers.google.com/admob/android/mediation/pangle) | [iOS Setup](https://developers.google.com/admob/ios/mediation/pangle) *(Note: Support setup requires manual adapter inclusion if not natively toggled)*

---

## ❓ Frequently Asked Questions (FAQ)

**1. Does the revenue from mediation networks go into my AdMob account?** **No.** AdMob only acts as a mediator that routes the ad requests. The actual revenue earned from third-party networks (like Meta, AppLovin, Unity, etc.) will be credited to your accounts on those respective platforms. You must set up payment details and reach the payout threshold individually on each network's dashboard.

**2. Should I enable all available mediation networks or just focus on a few?** **We highly recommend focusing on just 1 or 2 additional networks.** If you enable too many networks, your ad traffic will be split across multiple platforms. As a result, your earnings will be fragmented, and it will take a much longer time to reach the minimum payout threshold for each individual network.

**3. What are the best recommended networks to start with?** If you are just starting, we recommend **Meta (Facebook) Audience Network** and/or **AppLovin**. Both are known for having high fill rates, competitive eCPMs, and generally perform very well alongside Google AdMob.

---

## 📄 License
This project is licensed under the MIT License.