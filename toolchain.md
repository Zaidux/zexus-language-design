## Outlining the zpm Commands

The list of commands consists of:

| Command | Description | Example |
|---|---|---|
| zpm init | Creates a new zexus.json file in your project directory by asking you questions. | zpm init |
| zpm install | Reads zexus.json and installs all listed dependencies. | zpm install |
| zpm install <package> | Installs a specific package and adds it to your zexus.json file. | zpm install CoolUI |
| zpm publish | Publishes your library to the Zexus Registry for others to use. | zpm publish |
| zpm run <script> | Runs a custom script defined in the "scripts" section of zexus.json. This is how you would handle building, testing, and deploying. | zpm run deploy:ton |
| zpm test | A shortcut that runs the "test" script from your zexus.json file. | zpm test |