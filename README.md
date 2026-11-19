# Problem Set 4: The Model That Fit Too Well

This model predicts each store’s monthly revenue from its floor area, floor area squared, foot traffic, local median income, and years open. The old version used 65 columns, including a near-duplicate of floor area plus foot traffic and 60 columns of pure noise, and it left out floor area squared, which is why it over-forecast the biggest stores by about 4.3% of their revenue while still showing an R-squared of 0.93 on the stores it was fitted to.

The honest expected error is about 23,606 dollars per store per month, which comes from nested cross-validation, so it covers both choosing the model and fitting it. That is the number to expect next month, not the old 0.94, which was measured on the same stores the model learned from.

The model will fail in two situations. The first is the largest stores, because revenue varies more as stores get bigger, so their forecasts will miss by more than the average error suggests. The second is any store bigger than the 2,000 to 40,000 square feet the model was built on, because the floor area squared term bends the forecast, and outside that range nothing checks whether the bend is still right.

Next, I would build error ranges that widen with store size so the biggest stores get honest warnings, and I would put effort into better features rather than more stores, since the learning curve showed that more stores barely help once floor area squared is in the model.
