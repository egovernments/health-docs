---
description: A scanner package used for scanning QR codes and GS1 barcodes.
---

# DIGIT Scanner Package

Link to the Pub Package:&#x20;

{% embed url="https://pub.dev/packages/digit_scanner" %}

## How to Use the Scanner Package

![Scanner](https://lh7-us.googleusercontent.com/docsz/AD_4nXfqw2MsAFIHQ7kbq4PWzy4K5bFka8dC0S5-iXcVPY3RawaU4fYGUkzF3AGERbff5xp3iAyixyufy3SQdqTt67blPsMH5N0iwp_VMizw2rvt_lIjFs0-exCjsD1SpHzywM9vfrbPulZioTF9adn0tatLea4?key=nRsEb7PUeQBtAxHnNiKkvA)

To use the digit\_scanner package, add the following dependency to your pubspec.yaml file:

```
dependencies:
  digit_scanner: ^latest
```

#### Initialise DigitScannerBloc Provider

To initialise the DigitScannerBloc provider in your application, add the following code:

```dart
BlocProvider(
                create: (_) {
                  return DigitScannerBloc(
                    const DigitScannerState(),
                  );
                },
              ),
```

#### Clear the Scanner State

To clear the scanner state, use the following code:

```dart
context.read<DigitScannerBloc>().add(
    const DigitScannerEvent.handleScanner(),
);
```

#### Navigate to the DIGIT Scanner Page

To navigate to the Digit Scanner page, use this code snippet:

```dart
context.router.push(DigitScannerRoute(
                              quantity: 1, // Max no. of codes to be scanned
                              isGS1code: false, // Set Flag to true for scanning GS1 barcode
                              singleValue: true, // Set Flag to false for scanning multiple codes
                            ));
```

#### Wrap the DigitScannerListener or DigitScannerBuilder

Wrap the DigitScannerListener or DigitScannerBuilder in your widget tree wherever you need to read the scanned codes from the scanner state:

```dart
BlocListener<DigitScannerBloc, DigitScannerState>(
                  listener: (context, scannerState) {
                  if (scannerState.qrCodes.isNotEmpty) {
                  //
                  }
                  },
                  child: BlocBuilder<DigitScannerBloc, DigitScannerState>(
                  builder: (context, scannerState) {
                  if(scannerState.qrCodes.isNotEmpty){
                  return Text(scannerState.qrCodes.last); ///Get the scanned codes after scanning from the scanner State
                  }
                  else {
                  return Container();}
                  }
                  ));
```

Find out about usage at the example implementation.
