# Browser AI Prompt Adapter

An open-source project aimed at solving the challenge of adapting AI prompts across different `window.ai` implementations.

## Problem Statement

With the introduction of `window.ai` and the potential for different browsers to use various AI models, developers face a significant challenge: a prompt that works well with one model might perform poorly with another. This project aims to create a system that automatically adapts prompts for optimal performance across different `window.ai` implementations, ensuring consistent behavior regardless of the underlying AI model.

## Vision

Our goal is to develop a tool that:

- [ ] Automatically adapts prompts for different AI models
- [ ] Provides a benchmark system to verify adapted prompt performance
- [ ] Offers easy integration with existing `window.ai` applications
- [ ] Allows for saving and loading of adapted prompts
- [ ] Abstracts away browser-specific implementations

## Desired Workflow

1. Define the source model system prompt
2. Create test suites for the desired behavior
3. Run the adapter to automatically generate prompts for other models
4. Execute benchmarks to confirm performance across models
5. Save adapted prompts for future use

## Proposed Usage

```javascript
const PromptAdapter = require('prompt-adapter');

// Initialize the adapter
const adapter = new PromptAdapter();

// Define your source prompt
const sourcePrompt = `You are a helpful assistant...`;

// Define your test suites
const testSuites = [
  {
    input: "What's the capital of France?",
    expectedOutput: "The capital of France is Paris."
  },
  // Add more test cases...
];

// Run the adapter
const adaptedPrompts = await adapter.adapt(sourcePrompt, testSuites);

// Save adapted prompts
await adapter.save(adaptedPrompts, 'my_adapted_prompts.json');

// Load adapted prompts (in a different session or application)
const loadedPrompts = await PromptAdapter.load('my_adapted_prompts.json');

// Use the adapted prompt (browser abstraction)
const result = await adapter.run(loadedPrompts, "What's the capital of France?");
console.log(result); // Should output something similar across different browsers

// Run benchmarks
const benchmarkResults = await adapter.runBenchmarks(loadedPrompts, testSuites);
console.log(benchmarkResults);
```

## How It Works (Proposed)

1. The adapter will use a larger AI model to generate adapted prompts for different `window.ai` implementations.
2. Benchmarks will run automatically to verify that the adapted prompts produce results similar to the source model.
3. Results will be provided, showing how well each adapted prompt performs against the test suites.
4. Adapted prompts can be saved and loaded, allowing for reuse and sharing.

## Contributing

This project is in the conceptual stage. We welcome discussions, ideas, and potential collaborations to bring this vision to life. Please open an issue to start a conversation or propose features.

## License

This project is intended to be licensed under the MIT License.

## Acknowledgments

- This project is inspired by the introduction of `window.ai` and the challenges it presents for cross-browser AI development.
- The save/load functionality is inspired by projects like [DSPy](https://github.com/stanfordnlp/dspy), aiming to make prompt management more efficient.
