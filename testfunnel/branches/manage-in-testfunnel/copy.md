# Copy

[Vale](https://vale.sh/) is a linting tool that helps you maintain the highest standards in your technical documents. It's designed to catch spelling errors, grammatical mistakes, and style inconsistencies. With Vale, you can enforce a unified writing style, adhere to industry-specific guidelines, and enhance the overall readability and professionalism of your content.

This guide walks you through the process of installing and configuring Vale for your project.

## Prerequisites

Install [VS Code](https://code.visualstudio.com/) and open your project in it.

## Install Chocolatey

To install Chocolatey, see [Vale's official documentation](https://vale.sh/docs/vale-cli/installation/).

## Create and initialize a configuration file


The `.vale.ini` file is a configuration file meant for customizing Vale's behavior when checking documents. You typically place this file in the root directory of your project. The following is an example of `.vale.ini`:

```ini title="Example .vale.ini file"
StylesPath = styles

MinAlertLevel = suggestion

Packages = Google

[*.{md}]

BasedOnStyles = Google
```

| VARIABLE           | DESCRIPTION                                                                                               |
|-------------------|-----------------------------------------------------------------------------------------------------------|
| `StylesPath`      | Specifies the path to the directory containing custom styles or rule configurations. |       |
| `MinAlertLevel`   | Sets the minimum alert level for issues detected by Vale. In this example, it's set to `suggestion`, which means Vale provides suggestions but doesn't raise errors or warnings for less severe issues. |
| `Packages`        | Lists the style packages or rule sets that Vale uses. In this case, it's using the [Google deloper documentation style guide](https://developers.google.com/style) package. |
| `[*.{md}]`        | Defines the file patterns that Vale should apply its rules to. In this example, it specifies that Vale checks all Markdown files in your project. |
| `BasedOnStyles`   | Specifies which style package or rule set should be the basis for your custom configuration. Here, it's based on the Google deloper documentation style guide package. |

:::info 

You can customize your `.vale.ini` file to tailor Vale's linting rules, alert levels, and file scope to meet your specific project requirements and writing guidelines.

:::

To create and initialize `.vale.ini`, follow these steps:

1. At https://vale.sh/, navigate to **Resources&nbsp;<span aria-label="and then">></span> Config Generator**.
2. In **Config Configurator** that opens, select **Base style**, **Supplementary styles**, and **Static Site Generator** and copy the configuration.
3. In the root folder of your project, create the `.vale.ini` file, add the values from the previous step, and save it.
4. Initialize the configuration file: 
```bash
vale sync
```

## Install and configure the Vale extension

When you have `.vale.ini` created and initialized, you need to install and configure the Vale extension:

1. In the **Extensions** menu, find and install **Vale VSCode**.
2. Right-click the extension and select **Extension Settings**.
3. In the **User** tab, enter the following values:
   1. For **Vale > Vale CLI: Config**, enter `${workspaceFolder}/.vale.ini`.
   2. For **Vale › Vale CLI: Min Alert Level**, select `inherited`.
   3. For **Vale › Vale CLI: Path**, enter `vale`.
4. In the **Workspace** tab, repeat substeps i-iii of the previous step.
5. To apply the settings, relaunch VS Code.

Now you can use Vale to lint Markdown files in the project.


