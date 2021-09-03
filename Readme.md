## Home Assistant Elektrik Sayacı 🌟

<!-- PROJECT SHIELDS -->
![Project Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE)
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]

[![GitHub Activity][commits-shield]][commits]
[![GitHub Last Commit][last-commit-shield]][commits]
[![Contributors][contributors-shield]][contributors-url]

Home Assistant **2021.8** sürümünden itibaren yayınlanan [energy dashboard][energy] paneline veri üretmek üzere oluşturulmuş sensör devresidir.

<p align="center">
  <img width="80%" src="images/home-assistant-glow.jpg">
</p>

<details>
  <summary>Çalışma aşamasını izlemek için tıklayınız!</summary>

  <p align="center">
    <img src="images/glow_sensor_testing.gif" alt="Sayaç Test" width="40%"/><img src="images/glow_in_action.gif" alt="Sayaç Çalışması" width="40%"/>
  </p>
</details>

Home Assistant Elektrik Sayacı, Akıllı Sayaçlar üzerinde (yarı akıllı) bulunan ve elektril tüketimine bağlı yanıp sönen pulse LED okuma esasına dayalı ESPHOME yazılımı ile çelışarak Home Assistant a entegre olan bir sensor devresidir. 3D printer ile basım yaparak imal edebileceğiniz bir kutu tasarımı da beraberinde verilmiştir. 


### Sayacım buna uygun mu? nasıl anlarım?

Sayacınızın Home Assistant Elektrik Sayacı ile çalışacağından emin olmak için **imp/kWh** değerini aramanız gerekir (Pulse LED altındaki değer - resme bakın). Bunu not edin, çünkü yaml dosyasını yapılandırmak için daha sonraki aşamada bu değere ihtiyacınız olacak.

<p align="center">
  <img width="60%" src="images/pulse_rate.png">
</p>

## Elektronik Bileşenler

İlk olarak, kullanılacak parçaları aşağıdaki linklerden temin edebilirsiniz 🛒 yada elinizdeki mevcutları kullanabilirsiniz.

- [ESP32](https://www.robolinkmarket.com/esp32-wroom-wifi-ve-bluetooth-modulu)
- [Dupont Kablolar](https://www.robolinkmarket.com/arama?q=dupont&ps=4) İhtiyaca göre adedi belirleyerek satın alınız
- 3D baskı proje kutusu (bakınız [case](/case) klasörü)
- [Photodiyod](https://www.robolinkmarket.com/lm393-fotodiyot-sensor)
- [RGB LED 5mm-Ortak Katot](https://www.robolinkmarket.com/rgb-led-5mm-ortak-katot)

### Bağlantılar

Aşağıdaki bağlantı noktalarını dupont kablolar yardımı ile bağlayınız

#### Photodiyod

| PHOTODIYOD | ESP32        |
|------------|--------------|
| A0         | NOT USING    |
| DO         | D12 (GPIO12) |
| VCC        | 3V3          |
| GND        | GND          |

#### LED

How the status led is connected to the ESP32. For each measured pulse, the LED will briefly flash red and in case of no WiFi connection, the LED will continue to flash blue.

| LED    | ESP32      |
|--------|------------|
| RED    | D2 (GPIO2) |
| GREEN  | D4 (GPIO4) |
| BLUE   | D5 (GPIO5) |
| GND    | GND        |

## Başlayalım

Tüm donanımı bağladığınızda, ESPHome için yükleme ve knfigürasyona başlayacağız. Bu repoda, Home Assistant yapılandırmanızın 'esphome' klasörüne kopyalayabileceğiniz [home_assistant_glow.yaml][file] dosyasını bulacaksınız. **substitutions** altındaki "pulse_rate" değerini sayacınızda LED altında yazan değere ayarlayın ([imp/kWh oranımı nasıl bulurum?](#sayacım-buna-uygun-mu-nasıl-anlarım )), varsayılan olarak yaml dosyasında "1000" değeri kullanılır. Son olarak ESPHome kurulum sihirbazından geçin ve ESP32/8266 devrenize kodu yükleyin.

## Lisans

MIT License

Copyright (c) 2021 Klaas Schoute

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

<!-- MARKDOWN LINKS & IMAGES -->
[file]: /home_assistant_glow.yaml
[esphome]: https://esphome.io
[nc]: https://www.nabucasa.com
[energy]: https://home-assistant.io/docs/energy/

[maintenance-shield]: https://img.shields.io/maintenance/yes/2021.svg
[contributors-shield]: https://img.shields.io/github/contributors/klaasnicolaas/home-assistant-glow.svg
[contributors-url]: https://github.com/klaasnicolaas/home-assistant-glow/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/klaasnicolaas/home-assistant-glow.svg
[forks-url]: https://github.com/klaasnicolaas/home-assistant-glow/network/members
[stars-shield]: https://img.shields.io/github/stars/klaasnicolaas/home-assistant-glow.svg
[stars-url]: https://github.com/klaasnicolaas/home-assistant-glow/stargazers
[issues-shield]: https://img.shields.io/github/issues/klaasnicolaas/home-assistant-glow.svg
[issues-url]: https://github.com/klaasnicolaas/home-assistant-glow/issues
[license-shield]: https://img.shields.io/github/license/klaasnicolaas/home-assistant-glow.svg
[commits-shield]: https://img.shields.io/github/commit-activity/y/klaasnicolaas/home-assistant-glow.svg
[commits]: https://github.com/klaasnicolaas/home-assistant-glow/commits/master
[last-commit-shield]: https://img.shields.io/github/last-commit/klaasnicolaas/home-assistant-glow.svg
