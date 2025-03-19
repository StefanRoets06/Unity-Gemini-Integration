# Unity-Gemini-Integration

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Unity Version](https://img.shields.io/badge/Unity-6-blue)](https://unity.com/releases)
[![Open Issues](https://img.shields.io/github/issues/StefanRoets06/Unity-Gemini-Integration)](https://github.com/StefanRoets06/Unity-Gemini-Integration/issues)
[![Open Pull Requests](https://img.shields.io/github/issues-pr/StefanRoets06/Unity-Gemini-Integration)](https://github.com/StefanRoets06/Unity-Gemini-Integration/pulls)
[![Last Commit](https://img.shields.io/github/last-commit/StefanRoets06/Unity-Gemini-Integration)](https://github.com/StefanRoets06/Unity-Gemini-Integration/commits/main)
[![View Count](https://komarev.com/ghpvc/?username=StefanRoets06&repo=Unity-Gemini-Integration&label=Views)](https://github.com/StefanRoets06/Unity-Gemini-Integration)

This Unity package provides a simple and efficient way to integrate the Google Gemini API into your Unity projects for text generation.

## Features

* **Easy Integration:** Seamlessly send text prompts to the Gemini API.
* **Conversation Management:** Automatically handles conversation history for context-aware responses.
* **Custom Personality:** Define custom personality prompts to tailor AI responses.
* **Error Handling:** Robust error handling and logging for debugging.
* **Asynchronous Operations:** Uses Unity's `UnityWebRequest` and coroutines for non-blocking API calls.
* **Inspector Setup:** Easily configure API key and personality prompts within the Unity Inspector.

## Installation

1.  Download the `GeminiIntegration.cs` script.
2.  Place the script in your Unity project's `Assets` folder.
3.  Create a new GameObject and attach the `GeminiIntegration` script to it.
4.  In the Inspector, enter your Google Gemini API key.
5.  Optionally, customize the `personalityPrompt`.

## Usage

1.  Create a reference to the `GeminiIntegration` component in your script.

    ```csharp
    public GeminiIntegration geminiIntegration;
    ```

2.  Use the `SendPromptToGemini` coroutine to send prompts and receive responses.

    ```csharp
    using System.Collections;
    using UnityEngine;

    public class ExampleUsage : MonoBehaviour
    {
        public GeminiIntegration geminiIntegration;

        public void SendPrompt(string prompt)
        {
            StartCoroutine(geminiIntegration.SendPromptToGemini(prompt, HandleResponse));
        }

        private void HandleResponse(string response)
        {
            if (response != null)
            {
                Debug.Log("Gemini Response: " + response);
            }
            else
            {
                Debug.LogError("Failed to get response from Gemini API.");
            }
        }
    }
    ```

3.  To use a custom personality prompt:

    ```csharp
    StartCoroutine(geminiIntegration.SendPromptToGemini(prompt, HandleResponse, "You are a pirate that speaks in rhyme."));
    ```

4.  To clear the conversation history:

    ```csharp
    geminiIntegration.ClearConversationHistory();
    ```

5.  To set a new personality prompt during runtime.

    ```csharp
    geminiIntegration.SetPersonalityPrompt("You are a friendly robot.");
    ```

## Dependencies

* Unity Engine (2020.1+ and Unity 6 Compatible)
* UnityWebRequest

## API Key

You will need a Google Gemini API key to use this package. Ensure you have set up your Google Cloud project and enabled the Gemini API.

## Notes

* Ensure your API key is kept secure.
* Handle potential API errors and rate limits appropriately.

## License

MIT License

Copyright (c) 2025 Stefan Roets
