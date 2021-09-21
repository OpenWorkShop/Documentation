# Axes

The axes represent the dimensions in which the machine can move (most often, X/Y/Z).

## Min & Max Size

Each machine will have maximum dimensions for each axis.
For example, on a CNC router, a minimum Z-axis value of `-25.4mm` would mean that the tip of the [applicator](../hardware/applicator) cannot plunge more than 1" below the surface of the stock.

MakerHub uses the size of the axes to determine the bounds of the [visualizer](../interface/visualizer.md).

## Accuracy

The minimum amount in which the machine may move on a given axis.
For example, an axis with a value of `0.1` means that the machine may not travel in increments less than `0.1mm` on the axis.

## Precision

The number of decimal points for rounding values on a given axis.
For example, if the axis has a precision of `1`, then a value of `1.223mm` would be rounded to `1.2mm`.
