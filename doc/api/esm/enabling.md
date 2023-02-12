## Enabling

<!-- type=misc -->

Node.js has two module systems: [CommonJS][] modules and ECMAScript modules.

Authors can tell Node.js to use the ECMAScript modules loader
via the `.mjs` file extension, the `package.json` [`"type"`][] field, or the
[`--input-type`][] flag. Outside of those cases, Node.js will use the CommonJS
module loader. See [Determining module system][] for more details.

<!-- Anchors to make sure old links find a target -->

<i id="esm_package_entry_points"></i><i id="esm_main_entry_point_export"></i><i id="esm_subpath_exports"></i><i id="esm_package_exports_fallbacks"></i><i id="esm_exports_sugar"></i><i id="esm_conditional_exports"></i><i id="esm_nested_conditions"></i><i id="esm_self_referencing_a_package_using_its_name"></i><i id="esm_internal_package_imports"></i><i id="esm_dual_commonjs_es_module_packages"></i><i id="esm_dual_package_hazard"></i><i id="esm_writing_dual_packages_while_avoiding_or_minimizing_hazards"></i><i id="esm_approach_1_use_an_es_module_wrapper"></i><i id="esm_approach_2_isolate_state"></i>
