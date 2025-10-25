# CurrencyKeyboardView

## Description
A simple and lightweight SwiftUI decimalPad keyboard component for handling currency input seamlessly on watchOS 26+

CurrencyKeyboardView introduces a fully custom numeric keyboard — .decimalPad is not available natively on watchOS

![Screenshot](https://github.com/matvdg/CurrencyTextFieldKit/blob/8835ee3ab5e3c9d667721bbf28a00fee32250300/Screenshots/demo.png)


## Install

Add the following dependency to your Package.swift:
```swift
dependencies: [
    .package(url: "https://github.com/matvdg/CurrencyTextField.git", from: "1.0.0")
]
```

### Localization

To fully support localization of placeholders and toggle labels, add the following keys to your String Catalog (or `Localizable.strings`) in your project:

```text
"amount" = "Amount";
"overdrawn" = "Overdrawn";
```

Then import it in your SwiftUI file:
```swift
import CurrencyKeyboardView
```

## Usage Example

![Screenshot](https://github.com/matvdg/CurrencyTextFieldKit/blob/9d696ceeb9aa73d30b47283cd9755cb531cc8ec0/Screenshots/watchOS_recording.mov)
![Screenshot](https://github.com/matvdg/CurrencyTextFieldKit/blob/8835ee3ab5e3c9d667721bbf28a00fee32250300/Screenshots/iOS_recording.mov)


When `signMode` is set to `.both`, a toggle allows switching between positive and negative values.  
When you use `.positiveOnly` or `.negativeOnly`, the toggle is automatically hidden, and the sign is forced accordingly.


```swift
#if os(watchOS)
import SwiftUI
import CurrencyTextField

struct WatchCurrencyView: View {
    @State private var amount: Double?

    var body: some View {
        CurrencyKeyboardView(value: $amount)
    }
}
#endif
```

You can also hide the currency symbol inside the decimal pad if needed using the optional parameter `displayCurrency`:

```swift
CurrencyKeyboardView(value: $amount, signMode: .both, displayCurrency: false)
```

This approach gives you a full numeric keyboard experience on watchOS, which does not exist natively.

## Key Features
* ✅ Smart currency formatting with optional minus sign and dynamic color (red, primary, or green)
* ✅ Supports multiple currency symbols ($, €, …)
* ✅ Automatically inserts thousands separators (X XXX XXX.XX)
* ✅ Prevents leading zeros (e.g. 00 → 0, 06 → 6, 0.6 → 0.6)
* ✅ Adds a zero before a starting decimal point (.6 → 0.6)
* ✅ Converts "." to the appropriate decimal separator according to Locale *(on macOS, input comes from a physical keyboard)*
* ✅ Limits decimals to two digits (e.g. 0.999 → 0.99)
* ✅ Includes a toggle to switch between positive and negative values when `signMode = .both`



## Feedbacks / feature request / bug

Feel free to create an issue on GitHub or contact me: matvdg@me.com
