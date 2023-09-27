# Wire Formats for Anoma
This repository aims to contain exhaustive, human readable, specifications of all Anoma wire formats in BNF metasyntax.

## Number Encoding
We are currently using borsh serialization, meaning numbers are stored in little endian format.

For example, storing 512 as a 16-bit integer works as follows:

```
u16 ::= <byte> <byte>
512  =  (255, 1)
``` 

## Deviations from BNF to improve UX
Since we are optimizing for human readability at the moment, we use some constructs that are not included in formal BNF and define them in this section.
These will be removed before a production release, or we will pick a different BNF derivative that supports them (or equivalent ones) if they turn out to be required.

### Array
Let `Array(<number>, <term>)` represent `<number>` elements of data `<term>` packed next to each other

### Repetition operator `*`
`<number> <term>*` specifies the repetition of `<term>` `<number>` times

## Roadmap
In this stage, we specify the currently implemented wire format used in Taiga (which uses [borsh](https://borsh.io/)), as well as wire formats for basic types from the he anoma spec, such as `Resources`, `Partial Transactions`, `Transactions` and `Intents`. 
In the current stage, we're focusing on human readability and flatness of formats for robust and quick prototyping.

In the long run, we want to specify machine readable representations of all formats to generate secure parsers. (E)BNF would give us some flexibility in choosing which toolchains to use during that stage.
