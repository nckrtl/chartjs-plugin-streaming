# Migration

## Migrating to v3.0.0

### Chart.js v4 Support

Version 3.0.0 of chartjs-plugin-streaming adds support for Chart.js v4 and drops support for Chart.js v3. If you are still using Chart.js v3, please continue using version 2.x of this plugin.

### Breaking Changes

Make sure to also read the [Chart.js v4 migration guide](https://www.chartjs.org/docs/latest/migration/v4-migration.html) since you may be impacted by more general breaking changes due to this new Chart.js version.

#### Key Changes from Chart.js v3 to v4

1. **ESM-only package**: Chart.js v4 is now an ESM-only package. Ensure your build system supports ES modules.

2. **Scale configuration**: If you're using custom scale configurations, note that grid border options have been renamed:
   - `grid.drawBorder` → `border.display`
   - `grid.borderWidth` → `border.width`
   - `grid.borderColor` → `border.color`
   - `grid.borderDash` → `border.dash`
   - `grid.borderDashOffset` → `border.dashOffset`

3. **Plugin hooks**: The `destroy` hook has been replaced with `afterDestroy`. This plugin has been updated accordingly.

4. **Time scale changes**: If using `time.stepSize`, it should be migrated to `ticks.stepSize`.

#### Migration Steps

1. Update your Chart.js dependency to v4.0.0 or later
2. Update chartjs-plugin-streaming to v3.0.0
3. Update any other Chart.js plugins to their v4-compatible versions
4. Review your chart configurations for any deprecated options
5. Test your streaming charts thoroughly

## Migrating to v2.0.0

### Breaking Changes

Make sure to also read the [Chart.js v3 migration guide](https://www.chartjs.org/docs/latest/getting-started/v3-migration.html) since you may be impacted by more general breaking changes due to this new Chart.js version.

#### Explicit Plugin Registration

As described in the [getting started](getting-started.md#module), it's now required to manually register this plugin when building using module bundlers:

```js
import {Chart} from 'chart.js';
import ChartStreaming from 'chartjs-plugin-streaming';

Chart.register(ChartStreaming);
```

#### Default Options

The plugin default options are now accessible in `Chart.defaults.plugins.streaming.*` instead of `Chart.defaults.global.plugins.streaming.*` and can be modified using:

```js
Chart.defaults.set('plugins.streaming', {
  duration: 20000,
  // ...
});
```

See [Getting Started &rsaquo; Configuration](getting-started.html#configuration) for details.

#### Time scale override

Due to historical reasons, auto-scrolling was enabled for not only 'realtime' scales but also 'time' scales in the previous version. In version 2.x, auto-scrolling is enabled only for 'realtime' scales.

#### Transition Mode for Update

When you append data outside the `onRefresh` callback function, `chart.update()` needs to be called explicitly. To avoid interrupting the current animation, the previous version provided support for the `preservation` config property for the `update` function, but it is no longer supported.

Chart.js v3 introduced the transition mode argument, and this plugin now supports the `'quiet'` mode for this purpose.

```js
chart.update('quiet');
```

See [Data Feed Models &rsaquo; Pull Model (Polling Based) - Asynchronous](data-feed-models.html#pull-model-polling-based-asynchronous) for details.

