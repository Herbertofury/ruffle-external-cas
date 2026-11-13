# External CAS source-GFx experiment

This fork retains Ruffle's MIT OR Apache-2.0 license and notices. The ordinary
Flash path and both new compatibility switches default to false. The changes
contain no game movie, font, image, script, package or user data.

Only an explicitly selected original-source GFx profile may enable:

- `Player::set_source_gfx_early_class_publication(true)`: publish the actual
  class identity into its own initially null/undefined global const slot before
  cinit re-enters that class. A failing cinit restores the original slot. No
  bytecode, fields, defaults, or exceptions are replaced.
- `Player::set_source_gfx_soft_public_reads(true)`: after ordinary lookup fails,
  a missing public read on a sealed instance yields Undefined. Getter errors,
  private names and sealed writes keep the existing semantics.

Own-source fixtures exercise the separate-ABC circular cinit (strict mode keeps
1009; opt-in calls the real method returning 37) and optional sealed reads
(strict 1069; opt-in Undefined; original throwing getter and write 1056 unchanged).
The External CAS adapter retains the accompanying own AS3 source and compiled
small fixtures. Seven VM fixture tests passed before this source-only patch was
promoted from exact base 86f1fc8e1425edeec9e79328d3d867d1490d713b.

The original native trope producer and original typed source consumer establish
an actual optional-public-field read requirement. Independent native GFx class
initialization equivalence is not claimed. Complete original CAS initialization,
host-service behavior and all editing states remain qualification gates. These
switches are never a global Flash default or a substitute for missing host data.
