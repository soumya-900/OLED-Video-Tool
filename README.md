# Fellow Inventor OLED Video Tool

**ESP32 WiFi Player & .OLV Converter, by Fellow Inventor**

Turn videos, GIFs and images into tiny `.olv` files, upload them over WiFi to an ESP32, and play them on an OLED screen. Optional WS2812B LED effects included. The converter runs 100% offline in your browser, and no external libraries are needed on the ESP32.

▶️ **Live tool:** https://soumya-900.github.io/OLED-Video-Tool/

## Features

- **Converter:** MP4, MOV, WebM, animated GIF, PNG, JPG and WebP to `.olv`
- Trim, flip, frame rate, scaling (fit / fill / stretch), dithering (Floyd–Steinberg, Bayer, Threshold) and auto-optimize
- **Screens:** 128×64, 128×32, 64×48, 96×16, 132×64 (SH1106) or custom size. SSD1306 and SH1106 chips.
- **Boards:** ESP32, ESP32-C3, ESP32-S3, ESP32-S2
- **WiFi upload page** at `192.168.4.1` with live OLED brightness control
- **WS2812B LED effects:** Solid, Breathe, Blink, Chase, Rainbow, Sparkle. 1–150 LEDs, with colour and brightness control.
- Change the LED effect live from the ESP32 page, or save it inside the `.olv` file
- About 1.7 MB of video storage (2 MB LittleFS)
- Built-in samples: 3D Cube, Audio Equalizer, Starfield

## Quick start

1. **Flash the player once.** Open the tool → **WiFi Player (.ino)** tab → choose your board, OLED chip and size, set your WiFi name and password, then download `ESP32_OLED_WiFi_Player.ino`. (No need to find the code in this repo. The tool generates it.)
2. **Arduino IDE settings:**
   - Board: **ESP32 Dev Module**
   - Partition Scheme: **No OTA (2MB APP / 2MB SPIFFS)**
   - USB CDC On Boot: **Default (Disabled)**
3. **Convert media.** On the **Convert Media** tab, add a video, GIF or image, pick an optional LED effect, and download the `.olv` file.
4. **Upload.** Join the ESP32's WiFi (default: `ESP32-OLED`, password `12345678`), open `http://192.168.4.1`, and upload your `.olv`.
5. Tap the ESP32's **BOOT** button (GPIO0) to switch between saved videos.

## OLED wiring (default ESP32)

| OLED | ESP32 |
|------|-------|
| GND  | GND   |
| VCC  | 3V3   |
| SDA  | GPIO 21 |
| SCL  | GPIO 22 |

Pins and I2C address (usually `0x3C`) can be changed in the tool's Advanced settings.

## WS2812B LEDs (optional)

- **Data pin:** GPIO **18** by default (changeable in the tool)
- Wire strip DIN → GPIO18 through a ~330 Ω resistor, kept short
- Power the strip from its **own 5 V supply**, not the ESP32 5V pin
- **Join the supply GND to the ESP32 GND** (common ground)
- Add a 1000 µF capacitor across the strip's +5 V/GND where the supply connects
- Budget about 60 mA per LED at full white (60 LEDs ≈ 3.6 A, 150 LEDs ≈ 9 A). Lower the brightness slider to cut this.
- If the first LEDs flicker, add a 74AHCT125 or 74HCT245 level shifter on the data line

## Troubleshooting

- **Screen blank?** Check SDA/SCL wires, try SSD1306 ↔ SH1106, and check the I2C address (0x3C or 0x3D).
- **Upload fails?** Confirm the partition scheme is **No OTA (2MB APP / 2MB SPIFFS)** and delete old videos on `192.168.4.1`.

## License

Free to use. © Fellow Inventor. Rebranding or removing the Fellow Inventor attribution is not allowed.

## Follow Fellow Inventor

- YouTube: **Fellow Inventor**
- Instagram: **@fellow_inventor_diy**

## Support

This tool is free. If it helps you, a small donation helps me make
more phone-friendly tools and projects. 🙏

UPI: fellowinventor@naviaxis
