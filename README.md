# ⚡ C-Wire

> A program that analyses an electrical distribution data file to detect stations in a state of overconsumption.

C-Wire processes a data file and calculates, for a given station, the consumption of all the components connected to it — helping determine whether an electrical station is overloaded.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Station Types](#-station-types)
- [Usage](#-usage)
- [Accepted Formats](#-accepted-formats)
- [Unavailable Formats](#-unavailable-formats)

---

## 🔎 Overview

The program analyses a data file to determine whether an electrical station is in a state of **overconsumption**, by calculating the components linked to that station.

---

## 🏭 Station Types

There are three types of stations, organised in a hierarchy:

| Station | Supplies... |
| ------- | ----------- |
| **HV-B** | Companies that need a lot of electricity, and HV-A stations |
| **HV-A** | Companies that need less electricity, and LV stations |
| **LV**   | Individuals and small companies |

---

## 🚀 Usage

The command accepts **3 arguments** (or **4** to analyse the stations of a specific power plant — the 4th argument is optional).

```bash
bash c-wire.sh filepath.csv type_of_station_to_analyse components_to_analyse (number_of_power_plant)
```

**Examples :**

```bash
bash c-wire.sh input/c-wire_v25.dat hvb comp 1
bash c-wire.sh c-wire_v00.csv lv all
```

---

## ✅ Accepted Formats

Only **five combinations** of the second and third arguments are accepted (independently of the power plant number). The average execution time is indicated for each:

| Format       | Average Execution Time |
| ------------ | ---------------------- |
| `hvb comp`   | 1 second |
| `hva comp`   | 11–26 seconds |
| `lv comp`    | 15–30 seconds |
| `lv indiv`   | 30–50 seconds |
| `lv all`     | 30–50 seconds |

> 📊 The `lv all` format also generates a graph in the **graph** directory, displaying the ten stations with the **least** consumption and the ten with the **most** consumption.

---

## ⛔ Unavailable Formats

The following combinations are **NOT** available:

- `hvb indiv`
- `hvb all`
- `hva indiv`
- `hva all`
