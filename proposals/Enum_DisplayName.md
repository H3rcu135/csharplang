# Enum Display Name

* [x] Proposed
* [ ] Prototype: [Complete](https://github.com/PROTOTYPE_OWNER/roslyn/BRANCH_NAME)
* [ ] Implementation: [In Progress](https://github.com/dotnet/roslyn/BRANCH_NAME)
* [ ] Specification: [Not Started](pr/1)

## Summary
[summary]: #summary

Usage of an optional attribute (found in System.ComponentModel) on enum values, that if present would change the way that the string is presented to when using Enum.ToString()

## Motivation
[motivation]: #motivation

It would allow developers to define more user-friendly values when presenting them with the options in an enum.

## Detailed design
[design]: #detailed-design

sample syntax:
```C#
public enum Colors
{
 [DisplayName("Alice Blue")]AliceBlue,
 [DisplayName("Antique White")]Antique White,
 Aqua
}

Console.WriteLine(Colors.AliceBlue) // Outputs: "Alice Blue" instead of "AliceBlue"
Console.WriteLine(Colors.Aqua) // Outputs: "Aqua"

and for f

public enum Colors
{
 [DisplayName("Alice Blue")]AliceBlue,
 [DisplayName("Antique White")]Antique White,
 [DisplayName("Aqua")]Aqua
}

Console.WriteLine(Colors.AliceBlue | Colors.Aqua) // Outputs: "Alice Blue, Aqua" instead of "AliceBlue, Aqua"
```

I'm not really sure how to explain the proposal other than to show how it would/should work.

## Drawbacks
[drawbacks]: #drawbacks

I can see potential conversion issues regarding Enum.Parse and Enum.TryParse, albiet they could be modified to use the display names (either as defined or the default value) as the basis for conversion.

## Alternatives
[alternatives]: #alternatives

An alternative would be to create an extension class that implements a method like ```ToFriendlyString<T>(this T enumValue)```

## Unresolved questions
[unresolved]: #unresolved-questions


## Design meetings
