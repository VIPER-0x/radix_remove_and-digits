# radix_remove_and-digits
algorithm_in_c_sharp
This `C#` program demonstrates how to analyze a floating-point number (`double`) by breaking it down into its whole number and fractional parts, counting the digits, and manipulating its representation. Let's examine each part of the code step by step:

---

### **Code Explanation**

#### **1. Initializing the Number**

```csharp
double number = 456.25784; // You can change this number to test with different values
```

The variable `number` is declared and assigned a floating-point value `456.25784`. This value will be used for the subsequent analysis.

---

#### **2. Converting to String**

```csharp
string strNumber = number.ToString();
```

To analyze the digits and parts of the number easily, it is first converted to a **string representation** using `ToString()`. For the given `number = 456.25784`, it becomes `"456.25784"`. Working with strings makes it easier to separate the integral and fractional parts.

---

#### **3. Splitting into Whole Number and Fractional Parts**

```csharp
string[] parts = strNumber.Split('.');
```

The `Split('.')` method splits the string `strNumber` into two parts based on the decimal point (`.`). It produces a string array `parts`. For example:

- If `number = 456.25784`, `parts` becomes:
  - `parts[0] = "456"` (Whole number part)
  - `parts[1] = "25784"` (Fractional part)

If there is no decimal point (e.g., `number = 42`), `parts` will only contain one element (`parts[0] = "42"`).

---

#### **4. Calculating the Number of Digits Before and After the Decimal Point**

```csharp
int digitsBeforeRadix = parts[0].Length;
```

To calculate the **number of digits before the decimal point**, the **length** of the `parts[0]` (whole number string) is obtained. For example:

- `parts[0] = "456"` → `digitsBeforeRadix = 3`.

```csharp
int digitsAfterRadix = parts.Length > 1 ? parts[1].Length : 0;
```

This checks if there is a fractional part (i.e., when `parts.Length > 1`), and if so, calculates the **number of digits after the decimal point** by taking the length of `parts[1]`. If there is no fractional part, `digitsAfterRadix` is set to `0`.

Example:

- For `number = 456.25784`, `digitsAfterRadix = 5` (length of `"25784"`).
- For `number = 42`, `digitsAfterRadix = 0` (no fractional part).

---

#### **5. Calculating the Total Number of Digits**

```csharp
int totalDigits = digitsBeforeRadix + digitsAfterRadix;
```

The total number of digits in the input number is the sum of `digitsBeforeRadix` and `digitsAfterRadix`.

For example:
- `number = 456.25784` → `totalDigits = 3 + 5 = 8`.
- `number = 42` → `totalDigits = 2 + 0 = 2`.

---

#### **6. Removing the Decimal Point**

```csharp
string wholeNumberWithoutDecimal = strNumber.Replace(".", "");
```

The program removes the **decimal point** (`"."`) from the string representation of the number using the `Replace()` method. This produces a string that contains only the digits of the number.

For example:
- `number = 456.25784` → `wholeNumberWithoutDecimal = "45625784"`.
- `number = 42` → `wholeNumberWithoutDecimal = "42"`.

---

#### **7. Converting the Modified String Back to Integer (Optional)**

```csharp
long intNumber = long.Parse(wholeNumberWithoutDecimal);
```

The program converts `wholeNumberWithoutDecimal` (which contains only numerical digits) back to a numeric type (`long`). This allows the program to safely handle very large numbers without truncation.

For example:
- `wholeNumberWithoutDecimal = "45625784"` → `intNumber = 45625784` (as `long`).
- `wholeNumberWithoutDecimal = "42"` → `intNumber = 42`.

---

#### **8. Printing the Results**

```csharp
Console.WriteLine($"Original Number: {number}");
Console.WriteLine($"Whole Number Part: {parts[0]}");
Console.WriteLine($"Fractional Part: { (parts.Length > 1 ? parts[1] : "None")}");
Console.WriteLine($"Digits Before the Decimal Point: {digitsBeforeRadix}");
Console.WriteLine($"Digits After the Decimal Point: {digitsAfterRadix}");
Console.WriteLine($"Total Digits in the Input: {totalDigits}");
Console.WriteLine($"Whole Number Without Decimal: {wholeNumberWithoutDecimal}");
Console.WriteLine($"Integer Value: {intNumber}");
```

The program prints the results of each calculation:

1. **Original Number** - The input number as a floating-point value.
2. **Whole Number Part** - The part of the number before the decimal point.
3. **Fractional Part** - The part of the number after the decimal point (or `"None"` if it doesn't exist).
4. **Digits Before the Decimal Point** - Count of digits in the whole number part.
5. **Digits After the Decimal Point** - Count of digits in the fractional part.
6. **Total Digits in the Input** - Sum of the digits in both parts.
7. **Whole Number Without Decimal** - The number treated as a whole integer string (all digits, no decimal point).
8. **Integer Value** - The same number converted to a `long` integer.

---

### **Program Behavior With Example Input**

#### Example 1: Input `456.25784`

- `Whole Number Part` = `456`
- `Fractional Part` = `25784`
- `Digits Before the Decimal Point` = `3`
- `Digits After the Decimal Point` = `5`
- `Total Digits` = `8`
- `Whole Number Without Decimal` = `"45625784"`
- `Integer Value` = `45625784`

#### Example 2: Input `42`

- `Whole Number Part` = `42`
- `Fractional Part` = `None`
- `Digits Before the Decimal Point` = `2`
- `Digits After the Decimal Point` = `0`
- `Total Digits` = `2`
- `Whole Number Without Decimal` = `"42"`
- `Integer Value` = `42`

---

### **Main Concepts in the Code**
1. Handling floating-point numbers.
2. String manipulation (`ToString`, `Split`, `Replace`).
3. Calculating string lengths for digit counts.
4. Converting between data types (`string` to `long`).
5. Conditional statements (`?: operator`).

This program showcases how to analyze and manipulate numbers effectively in a `C#` environment.
