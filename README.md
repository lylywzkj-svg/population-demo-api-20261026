# Population Demo API

Static JSON demo values from the Figma Population test design. Public GET /api/population.json. Data does not update automatically.

- Seven indicators preserve the design display strings alongside numeric values.
- Four annual changes are signed percentages, e.g. 1.2 means 1.2%.
- Land area and density keep the design unit m^2 without validation.
- Nine trend points are estimated from dot geometry. x is a normalized position, not a year. The five year labels are separate.
- These are unverified design examples, not official statistics.

Edit api/population.json, commit, and push main to update GitHub Pages. index.html provides a request example and live response check.
