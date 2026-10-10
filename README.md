# Numeric Multiplication Table

A configurable Java application that generates multiplication tables for different numeric types, including integers and floating-point numbers.

Developed as part of the Java Backend course at SHPP School.

## Features

- Generate multiplication tables for configurable numeric ranges.
- Support multiple numeric types: `byte`, `short`, `integer`, `long`, `float`, and `double`.
- Configure the range and increment using a properties file.
- Select the numeric type using a JVM system property.
- Validate configuration parameters before generating the table.
- Use separate arithmetic strategies for integer and decimal calculations.
- Log application events and calculation details using SLF4J.

## Technologies

- **Java** — application logic and object-oriented design
- **SLF4J** — logging
- **Java Properties** — configuration management
- **BigInteger** — integer arithmetic and range checking
- **BigDecimal** — decimal arithmetic and range checking

## Architecture

The application separates configuration loading, validation, arithmetic operations, and output.

| Component                       | Responsibility |
|---------------------------------|---|
| `NumericMultiplicationTable`    | Application entry point and orchestration |
| `PropertiesLoader`              | Loads configuration from a properties file |
| `NumericType`                   | Defines supported numeric types and parsing rules |
| `NumberStrategy`                | Defines arithmetic operations and comparisons |
| `IntegerStrategy`               | Performs integer calculations |
| `DecimalStrategy`               | Performs decimal calculations |
| `MultiplicationConfigValidator` | Validates configuration parameters |
| `MultiplicationConfig`          | Stores the validated table configuration |
| `MultiplicationTable`           | Generates and prints the multiplication table |
| `MultiplicationContainer`       | Represents a multiplication operation and its result |

## Configuration

Create a `numeric-multiplication-table.properties` file in `src/main/resources/`:

```properties
min=1
max=5
inc=1
```

The properties define the starting value, the upper bound, and the increment used to generate the table.

The increment can be positive or negative, provided that its direction is consistent with the configured range.

## Usage

### Select a numeric type

The application uses `integer` by default.

Set the `type` JVM system property to select another supported type:

```bash
-Dtype=double
```

Supported values:

- `byte`
- `short`
- `integer`
- `long`
- `float`
- `double`

Type names are case-insensitive.

### Example

With the following configuration:

```properties
min=1
max=3
inc=1
```

The generated multiplication operations include:

```text
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
2 * 2 = 4
2 * 3 = 6
3 * 3 = 9
```

The table contains unique operand pairs with the second operand greater than or equal to the first.

## Validation

Before generating the table, the application checks that:

- All required properties are present.
- The minimum and maximum values are different.
- The increment is not zero.
- The increment direction is consistent with the configured range.
- Arithmetic operations remain within the supported numeric range.
- Nonzero decimal results satisfy the configured normal-value constraint.

Invalid configuration or unsupported numeric types result in an error.

## Design Principles

This project demonstrates several Java development concepts:

- Object-oriented programming
- Separation of responsibilities
- Strategy design pattern
- Java enums with associated behavior
- Records for data representation
- Configuration loading and validation
- Numeric range checking
- Logging and exception handling

## Learning Objectives

The project was created to practise designing a configurable Java application, implementing reusable arithmetic strategies, validating user-defined settings, and working with different numeric representations.
