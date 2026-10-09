# learning-sprint-2

Integer Overflow example

## Run the app

Download this repository and open `index.html` in a modern browser. No installation, build step, server, internet connection, or external libraries are required.

## Features

- Choose 4, 8, or 16 bits and signed or unsigned interpretation.
- Add, subtract, or multiply two values within the selected range.
- Compare the mathematical result with the modeled stored value.
- Inspect each bit and its positional weight.
- View the same bit pattern as signed and unsigned.
- Step the stored value up or down to explore the boundaries.
- Try four examples and answer four prediction challenges with feedback.
- Use keyboard-accessible controls and responsive layouts.

Changing the width or interpretation clamps existing operands to the new range. Invalid or empty operands show a message and hide the result until corrected. Challenges have their own stated width and interpretation, independent of the calculator settings.

## What to try

| Example | Mathematical result | Modeled stored value |
| --- | --- | --- |
| Unsigned 8-bit: 255 + 1 | 256 | 0 |
| Signed 8-bit: 127 + 1 | 128 | -128 |
| Unsigned 8-bit: 0 - 1 | -1 | 255 |
| Unsigned 8-bit: 20 × 20 | 400 | 144 |

The binary pattern `10000000` means 128 when unsigned and -128 when interpreted as signed 8-bit two's complement.

## How the model works

For a width of `n`, there are `2^n` possible bit patterns. The app first calculates the full mathematical result, then normalizes its remainder:

```text
raw = ((result % 2^n) + 2^n) % 2^n
```

For unsigned mode, the stored value is `raw`. For signed mode, values at or above `2^(n-1)` are interpreted as `raw - 2^n`. The app reports an out-of-range result when the mathematical answer falls outside the selected representable range. Negative out-of-range results also wrap in this model.

The app uses JavaScript `Number` and explicitly simulates narrow values. With widths limited to 16 bits and operands restricted to the selected range, every supported calculation is an exactly representable integer.

**Important limitation:** The signed mode is a two's-complement wraparound teaching model. It does not describe every programming language. C and C++ unsigned arithmetic wraps modulo `2^n`, but signed arithmetic overflow is undefined behavior. Do not assume a real signed C/C++ expression will wrap as shown here.

## Safety and purpose

This app is a local arithmetic visualization. It does not manipulate real memory, contain shellcode, perform exploitation, or send network requests. Overflow matters because unchecked arithmetic in counts or sizes can yield values smaller than intended. Real code should validate limits before calculation or use checked arithmetic.

## Project files

- `index.html`: Complete app, including HTML, CSS, and JavaScript.
- `reflection.md`: Short first-person reflection draft; review and personalize before submission.

## Development and AI use

Built with AI assistance to plan the lesson, generate the interface and arithmetic model, draft documentation, and help check boundary cases and browser interactions. The reflection is a draft rather than a verified account of the student's personal experience.

## Put it on GitHub

Create an empty repository named `integer-overflow-lab` on GitHub. Upload `index.html`, `README.md`, and `reflection.md` using **Add file → Upload files**, then commit the files. Keep the files at the repository root.

Optional: Enable GitHub Pages from **Settings → Pages**, choosing **Deploy from a branch**, the `main` branch, and the root folder. GitHub will display the browser app URL once deployment completes.

## Validation

The JavaScript passed a syntax check. The arithmetic model passed 648 boundary combinations across all three widths, both interpretations, and all three operations, using independent `BigInt` calculations as the reference. Simulated DOM checks passed for example buttons, boundary stepping, invalid inputs, operand clamping, and correct/incorrect quiz feedback. These checks do not verify actual browser rendering. A browser could not be installed in the development environment, so visual layout and real browser interactions still need a manual check by opening `index.html`.
