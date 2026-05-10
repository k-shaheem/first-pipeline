To create a professional CI/CD pipeline with GitHub Actions, you can break it down into these core building blocks. Think of this as your Cloud Ops Cheat Sheet:
1. The Structure (Where it lives)
Location: Always store your configuration in .github/workflows/ at the root of your repo.
File Format: Use .yml (YAML). Indentation is critical; use spaces, never tabs.

3. The Trigger (on:)
This defines when the pipeline starts. Common triggers include:
push: Runs every time you send code to GitHub.
pull_request: Runs when you propose changes (ideal for testing).
schedule: Uses cron syntax (e.g., '0 * * * *') to run tasks like health checks or backups automatically.

5. The Runner (runs-on:)
This is the "machine" that executes your code.
Most Ops tasks use ubuntu-latest because it's fast and comes pre-loaded with tools like curl, git, and python.

7. The Steps (steps:)
These are the individual tasks the runner performs:
Checkout: Almost every pipeline starts with - uses: actions/checkout@v4 to pull your code onto the runner.
Actions: Pre-built tools from the GitHub Marketplace (like setup-node or setup-python).
Run Commands: Custom shell commands (like your curl health check) used for specific logic.

9. Security (secrets)
Never hardcode credentials.
Store API keys, passwords, or sensitive URLs in Settings > Secrets and variables > Actions.
Access them in your YAML using the syntax: ${{ secrets.SECRET_NAME }}.

11. The DevOps Workflow
Branching: Work in a feature branch first.
Validation: Use the Actions tab to watch for the green checkmark.
Merging: Only merge to main once the pipeline passes.
Final Tip for your Shift: If a pipeline fails, always check the Exit Code.
Exit Code 0: Success.
Exit Code 1+: Something went wrong in your script or configuration.
