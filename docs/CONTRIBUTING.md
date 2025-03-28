# Contributing to Marketplace Platform

Thank you for your interest in contributing to this project! Please follow the guidelines below to ensure a smooth collaboration.

## How to Contribute

### 1. Fork the Repository

-   Click the **Fork** button on the repository's GitHub page.
-   Clone your fork locally:
    ```sh
    git clone https://github.com/your-username/marketplace-platform.git
    cd marketplace-platform
    ```
-   Add the original repository as a remote:
    ```sh
    git remote add upstream https://github.com/original-repo/marketplace-platform.git
    ```

### 2. Set Up the Environment

-   Install dependencies:
    ```sh
    yarn install
    ```
-   Run the services using Docker:
    ```sh
    docker-compose up --build
    ```

### 3. Create a Feature Branch

-   Before making changes, create a new branch:
    ```sh
    git checkout -b feature-branch-name
    ```

### 4. Commit Your Changes

-   Follow conventional commit messages:
    ```sh
    git commit -m "feat: add new authentication method"
    ```
-   Push changes to your fork:
    ```sh
    git push origin feature-branch-name
    ```

### 5. Create a Pull Request (PR)

-   Go to the original repository and open a Pull Request.
-   Add a **clear description** of your changes.
-   Request a review from the maintainers.

## Code Guidelines

-   Follow **ESLint & Prettier** for JavaScript/TypeScript.
-   Use **PEP8** for Python code.
-   Write **unit tests** for all major functionality.

## Issues & Discussions

-   Before opening an issue, check if it already exists.
-   Provide clear descriptions when reporting bugs.

We appreciate your contributions! 🎉
