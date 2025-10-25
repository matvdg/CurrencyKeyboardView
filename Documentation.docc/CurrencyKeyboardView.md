# ``CurrencyKeyboardView``

A simple and lightweight SwiftUI decimalPad keyboard component for handling currency input seamlessly on watchOS 26+


## Overview

CurrencyKeyboardView introduces a fully custom numeric keyboard — .decimalPad is not available natively on watchOS

## Installation

Add CurrencyKeyboardView to your project using Swift Package Manager by adding the following URL to your dependencies:

```swift
https://github.com/matvdg/CurrencyKeyboardView.git
```

Alternatively, clone the repository and include the package manually in your project.

## Localization

CurrencyKeyboardView automatically detects and applies the user's current locale settings, including currency symbol, decimal separators, and grouping separators. You can also customize the locale and currency settings programmatically to support multiple currencies within your app.

## Usage Example

This example demonstrates how to use `CurrencyKeyboardView` in a SwiftUI view. The text field automatically formats the input as currency based on the current locale.

```swift
#if os(watchOS)
import SwiftUI
import CurrencyKeyboardView

struct WatchCurrencyView: View {
    @State private var amount: Double?

    var body: some View {
        NavigationStack {
            CurrencyKeyboardView(amount: $amount)
        }
    }
}
#endif
```

You can also hide the currency symbol inside the decimal pad if needed using the optional parameter `displayCurrency`:

```swift
CurrencyKeyboardView(value: $amount, signMode: .both, displayCurrency: false)
```
```

This view presents a currency keyboard optimized for watchOS, allowing users to input currency values efficiently.

## Notes on Sign Modes and Forms

CurrencyKeyboardView supports different sign modes to control how positive and negative signs are displayed and handled:

- `.both`: Always show the sign.
- `.onlyPositive`: Never show the sign.
- `.onlyNegative`: Show the sign only when negative.

Additionally, the text field supports different forms of currency display, such as standard, accounting, or custom formats, which can be configured to suit your app’s requirements.


## Key Features

- Locale-aware currency formatting and symbol display  
- Real-time input validation and formatting  
- Support for multiple currencies and locales  
- Easy integration with SwiftUI  
- Configurable sign modes and currency display forms  
