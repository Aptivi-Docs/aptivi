---
description: How do I use this library?
icon: flask
---

# How to use

In order to be able to use this library, you should install it to your project. Afterwards, you can do the following actions:

* Get all chemical substances from the entire periodic table
* Get a specific substance from the periodic table by:
  * Atomic number
  * Symbol or name
* Get a list of substances from the periodic table by period and group

***

## <mark style="color:$primary;">How to use the library</mark>

The above goals can be attained using the periodic table static class, `PeriodicTableParser`, responsible for loading information about every single substance. Expand one of the expandables below:

<details>

<summary>Obtaining substances</summary>

You can get a single substance or a list of substances using one of the following functions:

| Function                 | Description                                                                                                            |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| `GetSubstances()`        | Gets all the substances from the whole table, or gets a list of substances that are found within a period and a group. |
| `GetSubstanceFromName()` | Gets a chemical substance from its name (case-insensitive)                                                             |
| `GetSubstance()`         | Gets a chemical substance from either its symbol or its atomic number                                                  |

</details>

<details>

<summary>Checking substances</summary>

You can also check to see if a substance exists in the periodic table without having to handle exceptions thrown by the above functions using the following `IsRegistered()` functions:

* `AreSubstancesRegistered()`
  * Checks to see if there are substances within a period and a group
* `IsSubstanceRegisteredName()`
  * Checks to see if there is a chemical substance by its name (case-insensitive)
* `IsSubstanceRegistered()`
  * Checks to see if there is a chemical substance by either its symbol or its atomic number

</details>
