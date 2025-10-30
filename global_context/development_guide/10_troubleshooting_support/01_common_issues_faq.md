# Common Issues & FAQ

This document lists frequently encountered issues during development and provides solutions or troubleshooting steps.

## 1. Local Development Setup Issues

### Issue: `docker-compose up` fails or services don't start.
*   **Possible Causes:**
    *   Docker Desktop not running.
    *   Port conflicts with other applications on your machine.
    *   Corrupted Docker images/volumes.
*   **Solutions:**
    *   Ensure Docker Desktop is running and up-to-date.
    *   Check for port conflicts using `lsof -i :<PORT_NUMBER>` (Linux/macOS) or Resource Monitor (Windows). Change conflicting ports in `docker-compose.local.yml` if necessary.
    *   Try cleaning Docker: `docker-compose down --volumes --rmi all` followed by `docker-compose up -d`.
    *   Check Docker logs for specific error messages: `docker-compose logs <service_name>`.

### Issue: Frontend application not compiling or showing errors.
*   **Possible Causes:**
    *   Missing Node.js dependencies.
    *   Incorrect Node.js version.
    *   Linting/TypeScript errors.
*   **Solutions:**
    *   Run `npm install` (or `yarn install`) in the frontend directory.
    *   Ensure you are using the recommended Node.js LTS version (`nvm use --lts`).
    *   Address any reported linting or TypeScript errors in your code.

### Issue: Backend service not starting or database connection errors.
*   **Possible Causes:**
    *   Missing Python dependencies.
    *   Incorrect Python environment activated.
    *   Database service not running in Docker.
    *   Incorrect database credentials in `.env` file.
*   **Solutions:**
    *   Ensure your Python virtual environment is activated and `pip install -r requirements.txt` has been run.
    *   Verify Docker Compose services are running (`docker-compose ps`).
    *   Double-check database credentials in the service's `.env` file against `docker-compose.local.yml`.
    *   Check backend service logs for specific error messages.

## 2. Git & Version Control Issues

### Issue: Merge conflicts when rebasing or merging.
*   **Solution:** Follow standard Git conflict resolution procedures. Use `git status` to identify conflicting files, manually edit them, `git add` the resolved files, and `git rebase --continue` or `git commit`.

### Issue: Accidentally committed sensitive information.
*   **Solution:** Do NOT push the commit. If already pushed, immediately contact a senior developer or team lead. Use `git filter-repo` or `BFG Repo-Cleaner` to remove the sensitive data from history (this is a destructive operation and requires coordination).

## 3. Testing Issues

### Issue: Tests failing unexpectedly.
*   **Possible Causes:**
    *   Recent code changes introduced a bug.
    *   Test data is outdated or incorrect.
    *   Environment-specific issues.
*   **Solutions:**
    *   Run tests locally to reproduce the failure.
    *   Review recent code changes and associated PRs.
    *   Verify test data. Consider refreshing local test data.
    *   Check logs and debug output from the failing tests.

## 4. Performance Issues

### Issue: Application is slow in local development.
*   **Possible Causes:**
    *   Resource constraints on your machine.
    *   Inefficient queries or code.
    *   Too many services running.
*   **Solutions:**
    *   Ensure your machine meets [Prerequisites](../01_prerequisites.md).
    *   Use profiling tools (e.g., Python's `cProfile`, browser developer tools) to identify bottlenecks.
    *   Temporarily stop unnecessary Docker services.

## 5. General Troubleshooting Steps

1.  **Check Logs:** Always start by checking the application logs (frontend, backend, database) for error messages.
2.  **Restart Services:** Sometimes, a simple restart of the affected service or Docker containers can resolve transient issues.
3.  **Search Documentation:** Consult this Development Guide, service-specific READMEs, and external documentation.
4.  **Ask for Help:** If you're stuck, don't hesitate to ask your team members (see [Getting Help & Escalation](./02_getting_help_escalation.md)).

This FAQ will be continuously updated based on common issues encountered by the team.