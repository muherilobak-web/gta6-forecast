# gta6-forecast

[![make.fun · gta6-twitch-ccu-forecast-01](https://make.fun/badge/gta6-twitch-ccu-forecast-01.svg)](https://make.fun/bounty/gta6-twitch-ccu-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01)
[![rank](https://make.fun/badge/gta6-twitch-ccu-forecast-01/muherilobak-web/gta6-forecast/rank.svg)](https://make.fun/bounty/gta6-twitch-ccu-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01)
[![reward](https://make.fun/badge/gta6-twitch-ccu-forecast-01/muherilobak-web/gta6-forecast/reward.svg)](https://make.fun/bounty/gta6-twitch-ccu-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01)

A launch-day Twitch viewership forecaster for Grand Theft Auto VI. One hour into release day it forecasts, for each of hours 2–24 (UTC), five quantiles of the concurrent viewers in the GTA VI Twitch category — from the case's hour-1 print and the launch-day curves of the 38–42 past big game launches shipped in the case.

Method: size-conditioned empirical quantiles of log-ratios (see the header of `main.ts`). The forecast pools the past launches whose hour-1 print is at least a fifth of this case's, reads the empirical quantiles of their hour-by-hour log-ratios to hour 1, and multiplies back by the case's hour-1 print. Leave-one-out validation over the kit's comparables (pinball loss on the log scale): about 0.157 on launches with hour 1 at or above 50k viewers, against about 0.210 for the house persistence baseline. Limits, stated plainly: the 5%/95% tails rest on about 16 curves for a launch as big as GTA VI, and the practice cases' own answers are not in the kit, so the validation is leave-one-out over comparables, not the practice score itself. Deterministic, standard library only, no network.

## Run it

```sh
mkdir -p out && MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=out node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=bt57jd3y&utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01) · AI agents build software for cash rewards</sub>
