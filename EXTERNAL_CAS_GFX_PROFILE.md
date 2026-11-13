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

A third opt-in switch, `set_source_gfx_drop_excess_as3_args(true)`, ignores
surplus arguments only for AS3 bytecode methods. Missing required arguments,
typed coercion errors, native builtin arity checks and variadic collection keep
the original path. It defaults false. Actual source event dispatchers pass a
payload to original zero-argument methods, establishing the source-specific
producer/consumer need. Independent native GFx equivalence remains unclaimed.
The own-source ExcessArgsFixture compares the same bytes in both modes and
retains strict 1063, missing 1063, coercion 1034, native 1063 and rest semantics.
Eight adapter VM fixtures passed before this source-only promotion. No private
depth guard, native binary, installed script or game asset is included.


A fourth explicit source-profile switch,
`set_source_gfx_loader_content_detach(true)`, permits only transferring a
Loader's exposed original content out of that Loader, and returning that same
detached content to its own empty Loader before original replacement cleanup.
Unknown children, another Loader, wrong parent, addChildAt, removeChildAt and
setChildIndex retain 2069. The ordinary/default Loader path stays unchanged.
The source ImageLoader/AssetLoader call this sequence; their scripts are not
patched, bundled or redistributed here. This qualifies the observed source
contract, not an assertion that all Scaleform Loader behavior is implemented.

An optional ExternalInterfaceProvider bitmap observer defaults disabled. For
an explicitly observed bitmap only, it attempts fallible renderer registration
and reports before/after the original COMPLETE handlers. Upload errors are
reported separately. The observer never calls back into AVM2. The host may use
this boundary to invoke original source completion after returning from the VM;
fetch resolution alone is not a completion signal.

Own GPU fixtures checked default 2069, seven forbidden mutation cases, exact
RGBA pixels, successful own-content return and withheld native completion when
the original COMPLETE handler throws. A private, read-only installed component
check ran unchanged original AssetLoader and ImageLoader through initial load
and replacement: two source COMPLETE events, one final child, zero VM errors,
and source DDS versus GPU premultiplied pixels within one byte per channel.
No original game asset, source script or native binary is included in this fork.
