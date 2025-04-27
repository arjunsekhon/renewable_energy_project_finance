# Renewable Energy Project Finance – Excel Workshop

This renewable energy project finance workshop with Excel is primarily for students learning solar & wind finance. Only basic Excel or Google
Sheets skills are required (no VBA or macros).

---

## Repository Contents

| File                           | Description                                                                                                                                    |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `Renewable_Project_Model.xlsx` | Two-sheet Excel workbook (Inputs & Model) that compares a 1 MW solar project with a 1 MW wind project and returns LCOE, NPV, IRR, and Payback. |

---

## Quick-Start

1. Clone or download the repo and open `Renewable_Project_Model.xlsx` in Excel,
   or upload it to Google Sheets.
2. Go to the **Inputs** tab and edit any of the seven input cells (CapEx, OpEx,
   Capacity Factor, Lifetime, Discount Rate, Power Price).
3. Switch to the **Model** tab—the yearly cash-flows table and the metrics
   summary (LCOE, NPV, IRR, Payback) update automatically.

---

## Sensitivity Experiments

| #   | Experiment             | Steps                                                                                          | What to Observe                                                               |
| --- | ---------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| 1   | Breakeven Check        | Set **Power Price** equal to the simple LCOE shown in row 33 and set **Discount Rate** to 0 %. | NPV ≈ 0, IRR ≈ 0 %, and Payback extends to the full project life.             |
| 2   | Price Sweep            | Change **Power Price** in $10 increments (e.g. 40 → 90 $/MWh).                                 | LCOE remains constant; NPV and IRR rise roughly linearly with price.          |
| 3   | Discount-Rate Impact   | Test 0 %, 8 %, and 15 % in **Discount Rate**.                                                  | A higher rate shrinks NPV and raises Discounted LCOE, while IRR is unchanged. |
| 4   | Capacity-Factor Upside | Increase the solar capacity factor from 0.20 to 0.25.                                          | Solar LCOE falls and solar IRR rises; wind metrics remain unchanged.          |
| 5   | CapEx Reduction        | Reduce solar CapEx by 15 %.                                                                    | Solar becomes more competitive; compare the new LCOE and IRR versus wind.     |
| 6   | OpEx Shock             | Double wind OpEx from 25 to 50 $/kW-yr.                                                        | Wind LCOE and NPV deteriorate; Payback lengthens.                             |

---

## Metric Definitions

**Levelized Cost of Energy (LCOE)** - The all‑in cost to generate one megawatt‑hour over the plant’s life.  It rolls CapEx and lifetime OpEx into a single $ / MWh figure, letting you compare different technologies on a "fuel‑agnostic" basis.

**Discounted LCOE** - Same idea, but both costs and energy are discounted to today's value so timing differences (e.g., a front‑loaded solar profile versus a steadier wind profile) are reflected.

**Net Present Value (NPV)** - The present‑day dollar value of all future net cash flows, discounted at your required rate of return.  A positive NPV means the project adds value; negative NPV destroys value.

**Internal Rate of Return (IRR)** - The discount rate that would set NPV to zero.  Compare it to your hurdle (cost of capital).  If IRR ≥ hurdle, the project clears the percentage‑return test.

**Payback Period** - The year in which cumulative net cash flow first turns positive.  Useful as a liquidity check but should never override NPV/IRR when the two conflict.

In summary LCOE benchmarks long‑run cost; NPV measures absolute value; IRR captures percentage return; and Payback shows capital recovery speed.

---

## Key Metrics

| Metric          | Excel Cell                | Meaning                                                                                     |
| --------------- | ------------------------- | ------------------------------------------------------------------------------------------- |
| LCOE            | `Model!B33` / `Model!C33` | Lifetime cost per MWh (undiscounted). Lower is better.                                      |
| Discounted LCOE | `Model!B32` / `Model!C32` | LCOE adjusted for the time value of money. Increases with the discount rate.                |
| NPV             | `Model!B34` / `Model!C34` | Present-value created at the chosen discount rate. Positive values indicate value creation. |
| IRR             | `Model!B35` / `Model!C35` | Break-even rate of return. Compare with your hurdle rate.                                   |
| Payback         | `Model!B36` / `Model!C36` | Years until cumulative net cash-flow turns positive.                                        |

---

### Interpretation Rules of Thumb

1. If **Price > LCOE**, the project earns a positive margin per MWh.
2. **NPV > 0** at your discount rate means the project adds value.
3. An **IRR** that meets or exceeds the discount rate satisfies the required
   return.
4. **Discounted LCOE** is always greater than simple LCOE when the discount rate
   is above zero.

Use these relationships—together with the sensitivity experiments—to see how
each assumption shapes project finance.

## Sample Analysis & Recommendation

After populating the workbook with the default inputs (CapEx = 1200 $/kW for
solar, 1400 $/kW for wind, price = 50 $/MWh, discount rate = 8 %), the **Model**
tab returns:

| Metric                  | Solar   | Wind   |
| ----------------------- | ------- | ------ |
| Discounted LCOE ($/MWh) | 75.6    | 50.9   |
| NPV @ 8 % ($/MW)        | – 478 k | – 30 k |
| IRR                     | 3 %     | 8 %    |
| Payback (years)         | 18      | 11     |

### Interpretation

- Wind’s discounted LCOE sits nearly at break-even with the \$50/MWh tariff;
  solar is 51 % above.
- Wind meets the 8 % hurdle IRR and could achieve positive NPV with a \$2–3 /MWh
  price premium.
- Solar fails the hurdle return and ties up capital for 18 years.

### Board Recommendation

Proceed with the wind project and defer solar until power pricing or CapEx
improves (target ≤ \$1 000 /kW). If diversification is desired, consider a
smaller solar tranche backed by a premium corporate PPA.

This example shows how each metric (LCOE, NPV, IRR, Payback) feeds directly into
an investment decision—students can replicate the process for any set of
assumptions.
