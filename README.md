
name: BLNCO AI Codex

on:
  workflow_dispatch:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  contents: read

jobs:
  codex:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
        with:
          persist-credentials: false

      - name: Run BLNCO AI Codex
        uses: openai/codex-action@v1
        with:
          openai-api-key: ${{ secrets.OPENAI_API_KEY }}
          prompt: |
            You are BLNCO AI's coding assistant.
            Analyze this repository.
            Identify bugs, security issues,
            performance problems and improvements.
            Provide actionable recommendations.
          permission-profile: ":read-only"
          safety-strategy: drop-sudo
