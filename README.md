# webpack-teamcity-bundle-size-plugin #

A webpack plugin that reports individual bundle sizes to TeamCity using buildStatisticValue service messages.

## To Install

In your project run a npm install command:

``` npm install webpack-teamcity-bundle-size-plugin --save-dev ```

## Usage

Import the plugin at the top of your `webpack.config.js` file:

``` const WebpackTeamcityBundleSizePlugin = require('webpack-teamcity-bundle-size-plugin') ```  

In the plugins section of your config, add a new instance of this plugin:

```
{
    ...
    plugins: [
        new WebpackBundleSizeAnalyzerPlugin()
    ]
    ...
}
```

## Plugin Output

The plugin will only output messages if `TEAMCITY_VERSION` is present.  You can test the reporter by temporarily setting the environment variable:

`export TEAMCITY_VERSION="your_version"`

If you have this environment variable set locally, running your webpack build will output TeamCity service messages:

```
##teamcity[buildStatisticValue key='app.js' value='40241']
##teamcity[buildStatisticValue key='app.css' value='1762']
```

The key is set to the bundle file name, the value is the bundle file size in bytes.

## Reference Information

More about reporting build statistics on TeamCity: 
https://confluence.jetbrains.com/display/TCD10/Build+Script+Interaction+with+TeamCity#BuildScriptInteractionwithTeamCity-ReportingBuildStatisticsReportingBuildStatistics