# EasyEffects preset: IdeaPad Speakers

An [EasyEffects](https://github.com/wwmm/easyeffects) output preset for Lenovo IdeaPad laptop speakers (Raptor Lake cAVS). It adds some body and clarity without the crispy distortion you get from stacking too much gain.

## Chain

1. **Bass Enhancer** with amount 3, scope 160 Hz and floor 40 Hz. It adds harmonics so bass the small drivers can't reproduce is still heard.
2. **Equalizer** (5-band IIR, −3 dB input)
   | Band | Type | Freq | Gain | Q |
   |---|---|---|---|---|
   | 1 | Hi-pass (x2) | 130 Hz | — | 0.707 |
   | 2 | Bell | 220 Hz | +3 dB | 1.0 |
   | 3 | Bell | 500 Hz | −2 dB | 1.2 |
   | 4 | Bell | 3 kHz | +2 dB | 1.0 |
   | 5 | Hi-shelf | 9 kHz | +2.5 dB | 0.707 |
3. **Compressor**, downward, with threshold −20 dB, ratio 3:1, attack 20 ms, release 150 ms and makeup +3 dB.
4. **Limiter** (Herm Thin) with threshold −1 dB, input gain 0 dB, lookahead 5 ms and release 20 ms.

## Install

```sh
cp "IdeaPad Speakers.json" ~/.local/share/easyeffects/output/
easyeffects -l "IdeaPad Speakers"
```

For a Flatpak install, use `~/.var/app/com.github.wwmm.easyeffects/data/easyeffects/output/` instead.

## Notes

The gain is kept low on purpose. Earlier versions used +7 dB of limiter input gain and +6 dB of compressor makeup, which drove the limiter hard enough to sound crispy. If it's too quiet, raise the system volume rather than the gain inside the chain.
