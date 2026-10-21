# Test output

Command: `python manage.py test -v 2` (Python 3.13.16, Django 5.2.18)

```
    Running deferred SQL...
System check identified no issues (0 silenced).
test_adhoc_bad_payloads (packing.tests.ApiTests.test_adhoc_bad_payloads) ... ok
test_adhoc_endpoint (packing.tests.ApiTests.test_adhoc_endpoint) ... ok
test_adhoc_unknown_sku (packing.tests.ApiTests.test_adhoc_unknown_sku) ... ok
test_no_box_fits_returns_null_box (packing.tests.ApiTests.test_no_box_fits_returns_null_box) ... ok
test_order_endpoint (packing.tests.ApiTests.test_order_endpoint) ... ok
test_unknown_order_404 (packing.tests.ApiTests.test_unknown_order_404) ... ok
test_cheapest_wins_even_if_not_smallest (packing.tests.PackerTests.test_cheapest_wins_even_if_not_smallest) ... ok
test_cost_tie_prefers_smaller_volume (packing.tests.PackerTests.test_cost_tie_prefers_smaller_volume) ... ok
test_empty_order (packing.tests.PackerTests.test_empty_order) ... ok
test_exact_fit_is_allowed (packing.tests.PackerTests.test_exact_fit_is_allowed) ... ok
test_item_needs_rotation (packing.tests.PackerTests.test_item_needs_rotation) ... ok
test_multiple_items_fit_together (packing.tests.PackerTests.test_multiple_items_fit_together) ... ok
test_single_small_item_picks_cheapest_box (packing.tests.PackerTests.test_single_small_item_picks_cheapest_box) ... ok
test_too_heavy_for_small_goes_to_medium (packing.tests.PackerTests.test_too_heavy_for_small_goes_to_medium) ... ok
test_too_long_for_every_box (packing.tests.PackerTests.test_too_long_for_every_box) ... ok
test_volume_ok_but_geometry_fails (packing.tests.PackerTests.test_volume_ok_but_geometry_fails) ... ok
test_weight_exactly_at_limit_is_allowed (packing.tests.PackerTests.test_weight_exactly_at_limit_is_allowed) ... ok

----------------------------------------------------------------------
Ran 17 tests in 0.022s

OK
Destroying test database for alias 'default' ('file:memorydb_default?mode=memory&cache=shared')...
```
