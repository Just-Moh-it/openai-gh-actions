# OpenAI Commit Github Action v0.0.1

Github Action to easily integrate OpenAI's API (Chat+Completions) into workflows. Empower your project with OpenAI's language model for intelligent response generation in just a few steps.

## Usage

In your Github Actions workflow, add the following YAML code to utilize the action:

```
- name: OpenAI
  uses: Just-Moh-it/openai-gh-actions@v0.0.1
  with:
    openai-api-key: ${{ secrets.OPENAI_API_KEY }}
    openai-prompt: <your-prompt>
    model: <model-id>
  id: openai
```

## Inputs

The action requires the following inputs:

- `openai-api-key`: Your OpenAI API key. This should be stored as a secret in your Github repository.
- `openai-prompt`: The text prompt to be passed to the OpenAI API.
- `model`: The ID of the OpenAI model to be used. (optional, default is text-davinci-003)

## Outputs

The output of the action is a response generated by OpenAI API. You can access the response by logging the output of the action.

```
${{ steps.openai.outputs.text}}
```

## Quick start

1. Create a new Github repository or navigate to an existing one.
2. Go to the "Actions" tab and click on "Set up a workflow yourself".
3. Copy and paste the code below into the workflow file.

```
name: OpenAI Action
on:
  push:
    branches:
      - main
jobs:
  deploy:
    name: OpenAI
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v1
        with:
          node-version: 14
      - name: OpenAI
        uses: riccardolinares/openai-commit@v0.0.1
        with:
          openai-api-key: ${{ secrets.OPENAI_API_KEY }}
          openai-prompt: "Write a description for this git commit: \n${{ github.event.head_commit.message }}"
        id: openai
```

4. Go to the "Settings" tab and click on "Secrets".
5. Add a new secret named `OPENAI_API_KEY` with your OpenAI API key.
6. Use the following code to access the response generated by OpenAI API.
7. Commit the changes to your repository.

## Limitations

The action is limited by the usage limits of your OpenAI API key.

## Support

If you have any questions or need help with this Github Action, please open an issue in the repository.

## Contributing

If you find any bugs or have suggestions for improvements, feel free to open an issue or create a pull request.