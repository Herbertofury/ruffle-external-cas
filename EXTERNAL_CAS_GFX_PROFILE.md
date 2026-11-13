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


An independent native-host dependability policy,
`Player::set_source_gfx_max_call_depth(Some(128))`, bounds source interpreter
calls before a recursive source failure can exhaust the worker's native stack.
It raises the existing genuine VerifyError 1023. The per-Player RAII counter
unwinds after caught and uncaught errors. `None` is the ordinary Flash default;
an explicit bound accepts 1 through 256. Existing time/instruction limits stay.
The built-in error constructor is temporarily exempted so reporting overflow
cannot recursively overflow the same guard. No successful source result or
missing service is substituted, and this does not qualify native GFx limits.

Own source tests retain a 32-call result, caught and uncaught infinite recursion
with 1023, a succeeding later callback, a reset depth counter, and isolation of
another default Player. Private debug measurement at depth 128 used 394,208
native stack bytes in the own fixture and 343,392 in the actual unresolved CAS
trial-data cycle. The latter survived 120 frames while retaining its UI-loading
and source-error state. No diagnostic guard, tracing or original asset is copied
into this checkpoint. Fixing each missing source host contract remains required.

An additional, narrowly selected source-profile switch,
`Player::set_source_gfx_missing_label_no_scene(true)`, permits native-source
continuation for a missing String frame label on a nested SpriteDef with no
explicit scene. Ordinary Flash stays strict; valid and numeric targets,
explicit scenes, non-String coercions and root/dynamic clips keep their paths.

Read-only isolated execution of the installed native label/scene helper and
its actual lookup/scene kernels covered 15 cases and 5,709 original instructions.
The native helper ignores a failed lookup and accepts the no-scene SpriteDef
case. The failed lookup leaves its caller out-frame unchanged. This proves
acceptance and continuation, not a deterministic target frame: the native
caller has no observed initializer for that stack value.

The adapter explicitly retains the current frame and honors the requested
Play/Stop mode. Each occurrence emits the warning marker
`SOURCE_GFX_UNQUALIFIED_MISSING_LABEL_FRAME_POLICY`, including retained frame
and `native_target_frame=undefined`. The host must retain a policy counter and
keep visual fidelity unqualified. No source label is renamed, no original
script is patched, and no widget visibility or lifecycle completion is forced.
The External CAS own two-frame fixture checks strict 2109, uncaught failure,
continued source execution, stable-frame policy, playback mode, unaffected
valid/numeric/explicit-scene/object/dynamic cases and disabling the profile.


`Player::set_source_gfx_missing_initial_visibility(true)` is an additional
narrow source-profile parser policy. It retains a new PlaceObject3 character
placement only when its final declared visibility byte is absent. All prior
fields must be complete; Modify/Replace, later declared fields, missing cache
bytes and PlaceObject4 remain strict. The ordinary/default parser is unchanged.
Queued replay is bounded to the original tag length so it cannot consume the
next tag as a visibility value. Original flags are retained in the diagnostic.

Isolated read-only native execution accepted the observed placement and name
for four different adjacent arena bytes (2,804 instructions, no hooks). The
native parser reads one byte beyond the authored payload; its value is not
qualified. This adapter leaves the absent visibility field as None rather than
synthesizing a Boolean. Each occurrence emits
`SOURCE_GFX_UNQUALIFIED_INITIAL_VISIBILITY` with `initial_visibility=unobserved`;
the host must retain a sticky counter and keep visual fidelity unqualified.
The default display object state is not asserted to match that unobserved byte.

Three own-byte parser tests check strict failure, placement/name/rawflags
retention, every earlier truncation, unsupported forms and complete byte values
0/1/127/255. An own-source MovieClip fixture checks default placement failure,
opt-in queued placement and an authored visibility assignment. The same AS3
constructor converges to false for all four complete byte values. No original
asset bytes, native binary, source scripts or padding values are redistributed.
Original CAS initialization and visual-state convergence remain separate gates.
