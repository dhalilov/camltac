<div align="center">

  ![Camltac][camltac-logo]

  OCaml as a Tactic Language for the [Rocq Prover][rocq-website]
  <br />
  <strong>[Follow the tour »][tour-link]</strong>
  
  [Tutorials][tutorials-link]
  ·
  [How-to guides][how-tos-link]
  ·
  [Docs][docs-link]
  ·
  [Master's thesis][master-thesis-link]

</div>

## Overview

Camltac is an **OCaml plugin for Rocq that lets you run OCaml code within Rocq scripts**. Camltac makes it possible to define OCaml meta-programs and tactics, and run them in the current Rocq state without the friction and boilerplate of setting up a plugin.

Camltac is both a tactic and a meta-programming language:

1. As a tactic language, Camltac provides constructs inspired by Ltac2, including term quotations (`{%constr| … |}`), pattern matching (`match%rocq`), and antiquotations using [`ppx_rocq`](https://github.com/epfl-systemf/ppx_rocq). Camltac makes it easy to define new tactics by providing the usual tacticals from Ltac2, and a dedicated <abbr title="Foreign Function Interface">FFI</abbr> with [Ltac](src/api/ltac.ml) and [Ltac2](src/api/ltac2.ml).

2. As a meta-programming language, Camltac offers a complete meta-programming experience by allowing access to Rocq's internal APIs and state. To ensure stability, Camltac includes the [Ltac2 APIs](https://github.com/epfl-systemf/mltac2) which provide a simple entry point to meta-programming in OCaml.

Have a look at the [tour of Camltac](./examples/Tour.v) for an overview of Camltac's features, or the [`examples`](./examples) directory for self-contained examples of using Camltac.

## Features

<div align="center">
  <img src="etc/showcase.png" width="75%" alt="Showcase image of Camltac" />
</div>

* **Quotations** for building terms: `{%constr| … |}`, `{%open_constr| … |}`, `{%preterm| … |}`, etc;

* **Antiquotations**, e.g., `{%constr| %{x} + %{y} |}`;

* **Pattern-matching over terms**: `match%rocq x with`, `match%lazy x with`, `match%multi x with`;

* **Pattern-matching over goals**: `match%rocq goal with`, `match%lazy goal with`, `match%multi goal with`;

* **Modules**: `Camltac Module M := ocaml:{{ … }}.`;

* **Interoperability with Ltac2**;

* **Ltac2 APIs** and **tacticals**;

* Support for **OCaml libraries and preprocessors**;

* Access to **Rocq state and APIs**;

* …

## Quickstart

Camltac is available on Rocq's opam repository and supports Rocq ≥ 9.0. To use Camltac:

1. Add the `rocq-released` opam repository:

   ```sh
   opam update
   opam repo add rocq-released https://rocq-prover.github.io/opam/released/
   ```

2. Install Camltac:

   ```sh
   opam pin add https://github.com/epfl-systemf/camltac.git
   ```
   
   **Note**: If you wish to install `camltac-examples`, you'll need Rocq 9.2 and OCaml 5.4.
   
3. Import Camltac in your Rocq files:
   ```rocq
   Require Import Camltac.Camltac.
   ```
   
4. You're ready to go! 🎉

## Contributing

Have a look at our [contributing guide][contributing].

## License

Camltac is free software under the [GNU LGPL 2.1 license][license], which is the license followed by Rocq itself.

[camltac-logo]: ./etc/logo.png
[camltac-showcase-image]: ./etc/showcase.png
[rocq-website]: https://rocq-prover.org

[tour-link]: ./examples/Tour.v
[tutorials-link]: ./tutorials
[how-tos-link]: ./how-tos
[docs-link]: ./docs
[master-thesis-link]: https://infoscience.epfl.ch/entities/publication/926430ae-7511-4498-bb12-5c8cf559ec33

[license]: LICENSE
[contributing]: CONTRIBUTING.md
