---
title: "Tweaking fastai tabular for time series data"
author: "Ozell Paukert"
date: "2025-02-03"
categories: [fastai, kaggle, tips]
draft: true
---

You can make your model considerably more powerful by careful feature engineering for timeseries data.

Sources:
- <https://www.kaggle.com/learn/time-series>
- <https://www.kaggle.com/competitions/playground-series-s5e1>

Main ideas:
- Add calendar periodic features
  - Need to combine test and train data together for this to work properly
- Add autoregressive features
- Augment with external data:
  - Currency exchange rate
  - Census (there are predictive data for this)


