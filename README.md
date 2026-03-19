# GitHub Actions Tutorial - Execution Flow

A comprehensive tutorial project demonstrating various GitHub Actions execution flow concepts including job dependencies, conditional execution, matrix strategies, and reusable workflows.

## 🎯 Project Overview

This project is a React-based web application that serves as a practical example for learning GitHub Actions execution flow patterns. It includes multiple workflow configurations that showcase different aspects of CI/CD pipeline orchestration.

## 🚀 Features

- **React Application**: Simple interactive web app built with Vite
- **Multiple Workflow Examples**: Five different GitHub Actions workflows demonstrating various execution patterns
- **Testing & Linting**: Automated code quality checks with ESLint and Vitest
- **Build & Deploy Pipeline**: Complete CI/CD pipeline with artifact management

## 📋 Workflow Examples

### 1. Basic Execution Flow (`execution-flow.yml`)
- **Purpose**: Demonstrates job dependencies and conditional execution
- **Features**:
  - Sequential job execution with `needs` dependencies
  - Conditional artifact upload on test failure
  - Failure reporting with GitHub context information

### 2. Continue on Error (`continue.yml`)
- **Purpose**: Shows how to handle failures gracefully
- **Features**:
  - Uses `continue-on-error: true` for test step
  - Always uploads test reports regardless of test outcome
  - Demonstrates workflow continuation after step failures

### 3. Matrix Strategy (`matrix.yml`)
- **Purpose**: Parallel execution across multiple environments
- **Features**:
  - Tests across multiple Node.js versions (12, 14, 16, 18)
  - Multiple operating systems (Ubuntu, Windows)
  - Matrix include/exclude configurations

### 4. Reusable Workflow (`reusable.yml`)
- **Purpose**: Demonstrates workflow reusability
- **Features**:
  - Accepts inputs and produces outputs
  - Can be called by other workflows
  - Supports secrets passing (commented examples)

### 5. Using Reusable Workflow (`use-reuse.yml`)
- **Purpose**: Shows how to consume reusable workflows
- **Features**:
  - Calls the reusable deployment workflow
  - Passes artifacts between workflows
  - Demonstrates output consumption

## 🛠 Tech Stack

- **Frontend**: React 18, Vite
- **Testing**: Vitest, Testing Library
- **Linting**: ESLint
- **CI/CD**: GitHub Actions
- **Package Manager**: npm

## 📦 Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd gha-tutorial-04-execution-flow
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

## 🧪 Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run test` - Run tests
- `npm run lint` - Lint and fix code

## ⚡ How to Trigger Workflows

### Automatic Triggers

Most workflows in this project are configured to trigger automatically:

#### 1. Push to Main Branch
The following workflows trigger on pushes to the `main` branch:
- `execution-flow.yml` - Website Deployment
- `continue.yml` - Continue Website Deployment  
- `use-reuse.yml` - Using Reusable Workflow

**To trigger these workflows:**
```bash
# Make any change to your code
git add .
git commit -m "Your commit message"
git push origin main
```

#### 2. Push to Any Branch
- `matrix.yml` - Matrix Demo triggers on any push to any branch

**To trigger this workflow:**
```bash
# Push to any branch
git push origin your-branch-name
```

### Manual Triggers

You can also trigger workflows manually through the GitHub UI:

1. Go to your repository on GitHub
2. Click on the **Actions** tab
3. Select the workflow you want to run
4. Click **Run workflow** button
5. Choose the branch and click **Run workflow**

### Reusable Workflow

The `reusable.yml` workflow cannot be triggered directly. It's designed to be called by other workflows using the `workflow_call` event. It's automatically used by the `use-reuse.yml` workflow.

### Testing Workflow Triggers Locally

To test your workflows without pushing to GitHub:

1. **Use Act** (GitHub Actions local runner):
```bash
# Install act
brew install act  # macOS
# or
curl https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash

# Run a specific workflow
act -W .github/workflows/execution-flow.yml

# Run workflows triggered by push
act push
```

2. **Validate workflow syntax**:
```bash
# Use GitHub CLI to validate
gh workflow view execution-flow.yml
```

### Workflow Status

You can monitor workflow runs:
- **GitHub UI**: Repository → Actions tab
- **GitHub CLI**: `gh run list` and `gh run view <run-id>`
- **Status badges**: Add workflow status badges to your README

## 🔄 GitHub Actions Workflows

All workflows are triggered on pushes to the `main` branch and demonstrate different execution patterns:

- **Parallel Execution**: Jobs that can run simultaneously
- **Sequential Execution**: Jobs with dependencies using `needs`
- **Conditional Execution**: Steps that run based on conditions
- **Matrix Builds**: Parallel execution across multiple configurations
- **Artifact Management**: Uploading and downloading build artifacts
- **Error Handling**: Different strategies for handling failures

## 📚 Learning Objectives

By studying this project, you'll learn:

1. **Job Dependencies**: How to control job execution order
2. **Conditional Logic**: Using `if` conditions and job outcomes
3. **Matrix Strategies**: Running jobs across multiple configurations
4. **Artifact Management**: Sharing data between jobs and workflows
5. **Reusable Workflows**: Creating and consuming reusable workflow components
6. **Error Handling**: Different approaches to handling failures
7. **Workflow Optimization**: Caching dependencies and optimizing build times
