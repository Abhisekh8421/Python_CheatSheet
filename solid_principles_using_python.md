

# SOLID Principles Using Python

## Technical Paper

---

# 1. Introduction

SOLID is a set of five object-oriented design principles.

These principles help developers:

* Write clean code
* Reduce bugs
* Improve maintainability
* Build scalable systems
* Design flexible software architecture

SOLID was introduced by Robert C. Martin (Uncle Bob).

---

# 2. What is SOLID?

SOLID stands for:

* S — Single Responsibility Principle
* O — Open/Closed Principle
* L — Liskov Substitution Principle
* I — Interface Segregation Principle
* D — Dependency Inversion Principle

Each principle focuses on writing better object-oriented code.

---

# 3. System Overview Used for Demonstration

This project reads a weather data file and finds the day with the smallest temperature difference.

The system contains:

* DataExtractor — reads and extracts data from file
* DataAnalyzer — analyzes extracted data
* Calculator — coordinates the process
* Main program — runs the calculation

---

# 4. Single Responsibility Principle (SRP)

## Definition

A class should have only one responsibility.
A class should have only one reason to change.

---

## DataExtractor

Responsible only for reading and extracting data.

```python
class DataExtractor:
    def __init__(self, file_path, key_column, value1_column, value2_column):
        self.file_path = file_path
        self.key_column = key_column
        self.value1_column = value1_column
        self.value2_columne = value2_column

    def extract(self):
        data = []
        with open(self.file_path) as fs:
            lines = fs.readlines()[1:]

            for line in lines:
                parts = line.split()

                key = parts[self.key_column]
                value1 = int(parts[self.value1_column])
                value2 = int(parts[self.value2_columne])
                data.append((key, value1, value2))
        return data
```

Responsibility:

* Open file
* Read lines
* Extract required columns
* Return structured data

---

## DataAnalyzer

Responsible only for analyzing data.

```python
class DataAnalyzer:
    def __init__(self, data):
        self.data = data

    def Analyze(self):
        minDiff = float("inf")
        result_key = None

        for key, value1, value2 in self.data:
            diff = abs(value2 - value1)

            if diff < minDiff:
                minDiff = diff
                result_key = key
        return result_key, minDiff
```

Responsibility:

* Compute temperature difference
* Identify minimum difference
* Return result

SRP is satisfied because:

* Extraction logic is separated
* Analysis logic is separated
* No class performs multiple unrelated tasks

---

# 5. Open/Closed Principle (OCP)

## Definition

Software entities should be:

* Open for extension
* Closed for modification

Meaning:

* You can add new features
* You should not modify existing working code

---

In this system:

If we want to:

* Analyze humidity
* Analyze rainfall
* Add new calculation logic

We can create a new analyzer class without changing DataExtractor or Calculator.

The system can grow without modifying stable components.

---

# 6. Liskov Substitution Principle (LSP)

## Definition

Objects of a subclass should be replaceable for objects of the parent class without breaking the program.

---

If we later create:

* TemperatureAnalyzer
* HumidityAnalyzer

They should behave in a way that any analyzer can be used inside Calculator without breaking execution.

The program should not need changes when replacing one analyzer with another.

---

# 7. Interface Segregation Principle (ISP)

## Definition

Clients should not be forced to depend on methods they do not use.

---

In this design:

* DataExtractor exposes only extract()
* DataAnalyzer exposes only Analyze()
* Calculator uses only required methods

Each class has a small, focused interface.

No class is forced to implement unnecessary methods.

---

# 8. Dependency Inversion Principle (DIP)

## Definition

High-level modules should not depend on low-level modules.
Both should depend on abstractions.

---

## Calculator Class

```python
from DataAnalyzer import DataAnalyzer
from DataExtractor import DataExtractor


class Calculator:
    def __init__(self, file_path, key_col, val1_col, val2_col):
        self.extractor = DataExtractor(file_path, key_col, val1_col, val2_col)

    def execute(self):
        data = self.extractor.extract()
        analyzer = DataAnalyzer(data)
        return analyzer.Analyze()
```

Responsibilities:

* Coordinates extraction and analysis
* Does not perform file reading
* Does not perform calculations

High-level logic is separated from low-level implementation details.

---

# 9. Main Execution

```python
from Calculator import Calculator

FILE_PATH = "data/weather.dat"

DAY_COLUMN = 0
MAX_TEMP_COLUMN = 1
MIN_TEMP_COLUMN = 2

weather_calculator = Calculator(FILE_PATH, DAY_COLUMN, MAX_TEMP_COLUMN, MIN_TEMP_COLUMN)

day, min_diff = weather_calculator.execute()

print(f"Day with smallest temperature spread: {day}")
print(f"Minimum temperature difference: {min_diff}")
```

Execution flow:

* Main creates Calculator
* Calculator uses DataExtractor
* Extracted data passed to DataAnalyzer
* Result returned and printed

---

# 10. Design Benefits

This architecture provides:

* Clear separation of responsibilities
* Low coupling between components
* Easy testing of individual classes
* Easy extension for future requirements
* Improved readability and maintainability

---

# 11. Conclusion

SOLID principles provide a foundation for clean and scalable object-oriented design.

Through:

* Single Responsibility
* Open/Closed design
* Proper substitution
* Small focused interfaces
* Reduced dependency




