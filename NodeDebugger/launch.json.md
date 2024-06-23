# Comment Section

json

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387

  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "skipFiles": ["<node_internals>/**"],
      "program": "${file}"
    }
  ]
}
```

Explanation of the Comment

1. IntelliSense:

- IntelliSense is a feature in VSCode that provides code completions, parameter info, quick info, and member lists.

- When you are editing the launch.json file, IntelliSense helps you by suggesting possible attributes and providing descriptions for them. This makes it easier to configure the debugger correctly.

  .

2. Hover for Descriptions:

- If you hover over an attribute in the launch.json file, a tooltip will appear with a description of what the attribute does. This is particularly useful for understanding the purpose of each configuration option.

3. More Information:

- The URL provided (https://go.microsoft.com/fwlink/?linkid=830387) leads to the official documentation for Visual Studio Code debugging. This page contains comprehensive information about configuring and using the debugger in VSCode.

# Configuration Section

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "skipFiles": ["<node_internals>/**"],
      "program": "${file}"
    }
  ]
}
```

##### Explanation of the Configuration

1. version:

- Specifies the version of the configuration schema. Currently, "0.2.0" is used.

2. configurations:

- An array of configurations. Each configuration object defines a debugging setup.

  3.type:

- Specifies the type of debugger to use. In this case, it's "node" for Node.js debugging.

4 request:

- Defines the type of request. "launch" means the debugger will launch a new program. Another common value is "attach", which attaches the debugger to an already running program.

5. name:

- A friendly name for the configuration. This name will appear in the dropdown menu in the Debug view.

6. skipFiles:

An array of file patterns to skip when debugging. "<node_internals>/\*\*" skips all internal Node.js files, making it easier to focus on your own code.

7. program:

- Specifies the path to the program to debug. ${file} is a variable that refers to the currently active file in the editor. If you open a file in the editor and start debugging, this configuration will run that file.

##### Configuration Section

Now let's look at the actual configuration:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "skipFiles": ["<node_internals>/**"],
      "program": "${file}"
    }
  ]
}
```

Explanation of the Configuration

1. version:

- Specifies the version of the configuration schema. Currently, "0.2.0" is used.

2. configurations:

- An array of configurations. Each configuration object defines a debugging setup.

3. type:

- Specifies the type of debugger to use. In this case, it's "node" for Node.js debugging.

4. request:

- Defines the type of request. "launch" means the debugger will launch a new program. Another common value is "attach", which attaches the debugger to an already running program.

5. name:

- A friendly name for the configuration. This name will appear in the dropdown menu in the Debug view.

6. skipFiles:

- An array of file patterns to skip when debugging. "<node_internals>/\*\*" skips all internal Node.js files, making it easier to focus on your own code.

7. program:

- Specifies the path to the program to debug. ${file} is a variable that refers to the currently active file in the editor. If you open a file in the editor and start debugging, this configuration will run that file.

# Customizing the Debug Configuration

If you want to customize your debug configuration further, here are some additional attributes you might find useful:

cwd:

- Specifies the working directory for the program being debugged.

```json
"cwd": "${workspaceFolder}"
```

env:

- Defines environment variables for the debuggee.

```json
  "env": {
  "NODE_ENV": "development"
  }
```

args:

- An array of command-line arguments to pass to the program.

```json
"args": ["arg1", "arg2"]
```

outputCapture:

- Specifies which output streams to capture and show in the Debug Console. Possible values are "console", "stderr", or "stdout".

```json
"outputCapture": "console"
```

## General Guidelines

1. Broad Configurations: Create configurations that can cover multiple files or entire functional areas. This avoids the need for adding a new configuration for every single file.

2. Specific Scenarios: If certain parts of your application require unique debugging setups (e.g., different environment variables, specific command-line arguments), create additional configurations for those scenarios.

3. Environment-Specific Configurations: You might have different configurations for development, testing, and production environments.

### Example: Comprehensive launch.json

Here’s an example of a more comprehensive launch.json that includes various configurations for different scenarios:

```json
Copy code
{
"version": "0.2.0",
"configurations": [
{
"type": "node",
"request": "launch",
"name": "Launch Program",
"skipFiles": ["<node_internals>/**"],
"program": "${workspaceFolder}/app.js",
      "env": {
        "NODE_ENV": "development"
      }
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Specific File",
      "skipFiles": ["<node_internals>/**"],
      "program": "${file}"
},
{
"type": "node",
"request": "launch",
"name": "Run Tests",
"skipFiles": ["<node_internals>/**"],
"program": "${workspaceFolder}/node_modules/jest/bin/jest.js",
      "args": ["--watchAll"]
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Launch with Environment Variables",
      "skipFiles": ["<node_internals>/**"],
      "program": "${workspaceFolder}/app.js",
"env": {
"NODE_ENV": "production",
"API_KEY": "your-api-key-here"
}
}
]
}

```

### Explanation of the Configurations

1. Launch Program:

- This is the main configuration for launching your application. It runs app.js with the NODE_ENV set to development.

2. Launch Specific File:

- This configuration allows you to launch the currently active file in the editor. It's useful for quickly debugging different scripts without changing the main configuration.

3. Run Tests:

- This configuration is set up to run your Jest tests. The args array includes --watchAll to keep the test runner active and watch for changes.

4. Launch with Environment Variables:

- This configuration runs your application with specific environment variables, suitable for scenarios like production or when specific API keys are needed.

#### Adding Configurations for New Functional Areas

When adding new functional areas, consider the following:

1. Functional Area Configurations:

- If a new functional area requires unique settings (e.g., different environment variables or arguments), add a new configuration for that area.

2. Shared Configurations:

- Use existing configurations where possible. For example, if a new module is just another Express route or controller, the main configuration (Launch Program) will likely cover it.

#### Example: Adding a New Functional Area

Suppose you add a new feature that interacts with the CTA API and requires specific environment variables. You can add a new configuration for this:

```json
{
  "type": "node",
  "request": "launch",
  "name": "Launch CTA Feature",
  "skipFiles": ["<node_internals>/**"],
  "program": "${workspaceFolder}/ctaFeature.js",
  "env": {
    "NODE_ENV": "development",
    "CTA_API_KEY": "your-cta-api-key-here"
  }
}
```
