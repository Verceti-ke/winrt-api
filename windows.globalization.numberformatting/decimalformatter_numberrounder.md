---
-api-id: P:Windows.Globalization.NumberFormatting.DecimalFormatter.NumberRounder
-api-type: winrt property
---

<!-- Property syntax
public Windows.Globalization.NumberFormatting.INumberRounder NumberRounder { get;  set; }
-->

# Windows.Globalization.NumberFormatting.DecimalFormatter.NumberRounder

## -description
Gets or sets the current rounding strategy to be used when formatting numbers.

## -property-value
A number rounder object: [IncrementNumberRounder](incrementnumberrounder.md) or [SignificantDigitsNumberRounder](significantdigitsnumberrounder.md).

## -remarks
When a **Format** method is called, the appropriate rounding function from the number rounder object manipulates the input prior to it being formatted.

## -examples

## -see-also