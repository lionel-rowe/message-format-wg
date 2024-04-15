# Maintaining the Function Registry

Status: **Proposed**

<details>
	<summary>Metadata</summary>
	<dl>
		<dt>Contributors</dt>
		<dd>@aphillips</dd>
		<dt>First proposed</dt>
		<dd>2024-02-12</dd>
		<dt>Pull Requests</dt>
		<dd>#000</dd>
	</dl>
</details>

## Objective

_What is this proposal trying to achieve?_

Describe how MFv2 will manage the default function registry
as well was related function registries intended to promot interoperability.

## Background

_What context is helpful to understand this proposal?_

> [!NOTE]
> This design proposal is for the Tech Preview period.

MessageFormat v2 envisions providing a "default registry" that all conformant
implementations are required to implement.
Our goal is to be as universal as possible, 
making MFv2's message syntax available to developers in many different
runtimes in a wholly consistent manner.
Because we want broad adoption in many different programming environments
and because the capabilities 
and functionality available in these environments vary widely,
the default function registry must be conservative in what it requires.

At the same time, we want to promote message interoperability.
Even though a feature cannot be adopted by all platforms,
diversity in the function names, operands, options, error behavior,
and so forth remains undesirable.
This suggests that there exist a registry at a lower level of normativeness
with "templates" for functions that implementations can implement 
when they have the wherewithal to support them.

An example of this might be "personal name formatting",
whose functionality is new in CLDR and ICU.
Few if any non-ICU implementations are currently prepared to implement
a function such as `:person`
and implementation and usage experience is limited in ICU.
Where functionality is made available, we don't want it to vary from
platform to platform.

Finally, we need to establish mechanisms for managing proposals
for the various types of function registry.

## Use-Cases

_What use-cases do we see? Ideally, quote concrete examples._

## Requirements

_What properties does the solution have to manifest to enable the use-cases above?_

## Constraints

_What prior decisions and existing conditions limit the possible design?_

## Proposed Design

_Describe the proposed solution. Consider syntax, formatting, errors, registry, tooling, interchange._

To address the above problem, in addition to the default registry,
create a template for registry functions
and a process for proposing and evaluating these functions for inclusion
into the MessageFormat v2 function registry.

There would be three levels of expected maturity:

- **Default Registry** includes functions that are normatively required by all implementations.
  Such entries will be limited in scope to functions that can be
  implemented in nearly any programming environment.
  > Examples: `:string`, `:number`, `:date`
- **Recommended for General Implementation**
  ("RGI", deliberately similar to RGI in emoji, tho' we may want to change the name)
  includes functions that are not
  normatively required but whose names, operands, and options are recommended.
  Implementations are _strongly_ encouraged to use these function signatures
  when implementing the described functionality.
  This will promote message interoperability
  and reduce the learning curve for developers, tools, and translators.
  > Examples: We don't currently have any, but potential work here
  > might includes personal name formatting, gender-based selectors, etc.
- **Unicode Extensions** includes optional functionality that implementations
  may adopt at their discretion.
  These are provided as a reference.
  Unicode extensions use the namespace `:u` (which should be reserved).
  This is also intended as a useful means of incubating functionality before
  adding it to the default or RGI registries in future releases.
  > Examples: Number and date skeletons are an example of Unicode extension
  > possibilities.
  > Providing a well-documented shorthand to augment "option bags" is
  > popular with some developers,
  > but it is not universally available and could represent a barrier to adoption
  > if normatively required.

## Alternatives Considered

_What other solutions are available?_
_How do they compare against the requirements?_
_What other properties they have?_
