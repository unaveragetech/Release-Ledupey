

# Release-Ledupey Overview

Welcome to the **Release-Ledupey** repository! This project, developed by Nbtguyoriginal, assists users in identifying and managing duplicates caused by plugins in Minecraft by utilizing GitHub's API and OpenAI's ChatGPT.

## Important Note
As of now, there are no public releases available. Instead, you can download the repository as a ZIP file.

### VirusTotal Scan
We recommend verifying the safety of the files. You can use the VirusTotal scan linked below to compare the file structure:
- [VirusTotal Scan](https://www.virustotal.com/gui/file/eab16896e02a3653818ed6e3a50e4c25391a6e9f5d455d382154bbb3c9441709)

## Prerequisites
Before getting started, ensure you have the following software installed:

- **Python**: Download from [python.org](https://www.python.org/)
- **Pillow**: Install via pip:
  ```bash
  pip install pillow
  ```
- **OpenAI**: Install via pip:
  ```bash
  pip install openai
  ```
- **PyGithub**: Install via pip:
  ```bash
  pip install PyGithub
  ```

or 
 **install all**: Install via pip:
  ```bash
  pip install openai
  pip install pillow
  pip install PyGithub
```

- **GitHub**: You’ll need a GitHub account and an API key (available in your GitHub settings).

- ```bash
## Obtaining a GitHub Account and API Key

To utilize the **Release-Ledupey** application, you will need a GitHub account and a GitHub API key. Here’s how to obtain both:

### 1. Creating a GitHub Account

If you don’t already have a GitHub account, follow these steps to create one:

- Visit the [GitHub Signup Page](https://github.com/join).
- Fill in your details, including username, email, and password.
- Complete the sign-up process by verifying your email address.

### 2. Generating a GitHub API Key

Once you have a GitHub account, you can generate a Personal Access Token (API key) to authenticate your requests to the GitHub API. Here’s how:

1. **Log in to GitHub**: Go to [GitHub](https://github.com) and log in with your account credentials.

2. **Access Developer Settings**:
- Click on your profile picture in the upper-right corner of the page.
- Select **Settings** from the dropdown menu.
- In the left sidebar, scroll down and click on **Developer settings**.

3. **Create a Personal Access Token**:
- In the Developer settings menu, click on **Personal access tokens**.
- Click the **Tokens (classic)** tab.
- Click on the **Generate new token** button.

4. **Set Token Permissions**:
- Give your token a descriptive name (e.g., "Release-Ledupey Token").
- Set the expiration time according to your needs.
- Under **Select scopes**, check the boxes for the permissions you need:
- **repo**: Full control of private repositories (required for repository access).
- **read:user**: Access to user profile information.
- After selecting the necessary scopes, click **Generate token** at the bottom.

5. **Copy Your Token**: Once generated, copy your Personal Access Token. **Important**: This token will only be displayed once. If you lose it, you’ll need to generate a new one.

6. **Store the Token Securely**: Treat your API key like a password. Do not share it publicly or expose it in your code.

### Example API Key Format
A GitHub API key typically looks like this:
```
ghp_16EXAMPLEiP5EqMVPd6wzXAi7D8hf03YH7E
```

### Further Reading
For more detailed instructions, refer to the official GitHub documentation on [creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

```

## Getting Started
Follow these steps to download and use the project:

1. Navigate to the repository: [Release-Ledupey on GitHub](https://github.com/Nbtguyoriginal/Release-Ledupey.git).
2. Click the `<> Code` button, then click the `Download ZIP` button.
3. Extract the ZIP file to your preferred location (recommended: Desktop).
4. Open your terminal/command prompt and navigate to the extracted folder. Alternatively, open the folder and type `cmd` in the address bar.
5. Install the required resources:
   ```bash
   pip install pillow PyGithub openai
   ```
6. **Insert API Keys**:
   - Open `ledupey.py` in a text editor.
   - Locate line 180 and replace the placeholder with your GitHub API key:
     ```python
     token = "Replace with your own key"
     ```
   - Create a file named `config.py` in the same directory and add your OpenAI API key:
     ```python
     API_KEY = "Your OpenAI API key"
     ```

Once set up, double-click `ledupey.py` to launch the application.

## Detailed Code Explanation

### Loading Screen
The function `show_loading_screen()` creates a loading GUI that informs users while the application installs any required libraries. This function:

- Creates a new `Toplevel` window for the loading screen.
- Attempts to display a logo by resizing it from the local directory.
- Uses a `ttk.Progressbar` to provide visual feedback on the loading status.
- Automatically closes after 3.5 seconds unless interrupted.

### Installing Requirements
The `install_requirements()` function checks for any missing packages specified in `requirements.txt`. It uses `subprocess.check_call()` to run pip commands, which ensures that necessary libraries are installed seamlessly.

### Main GUI Class: `GitHubSearchGUI`
The `GitHubSearchGUI` class builds the main user interface, allowing users to:

- **Input Repository**: Enter a GitHub repository name or URL.
- **Search Keywords**: Input keywords for issue searching.
- **Select Browser**: Choose a browser to open relevant links.
- **Display Results**: Show search results and allow clickable links for easy navigation.
- **Save and Load Repositories**: Save frequently used repositories for quick access.

**Key Functional Methods**:
- `search_issues()`: Queries GitHub for issues based on user input and keywords. It handles errors such as invalid repository names gracefully.
- `open_url()`: Opens links in the selected browser and ensures that the URL is valid.
- `clear_results()`: Clears the results text box for new searches.
- `save_repo()`: Saves the current repository name to a text file, ensuring no duplicates.
- `load_saved_repos()`: Loads previously saved repositories from a text file, handling the case where the file does not exist.

### ChatGPT Integration: `ChatGPTPopup`
The `ChatGPTPopup` class provides functionality for users to interact with ChatGPT.

**Key Features**:
- **Temperature and Token Sliders**: Users can adjust parameters for the model's responses, allowing for varied outputs.
- **Ask DupeBot**: Sends a question to the ChatGPT model and displays the response, while keeping a history of the conversation.

**Potential Edge Cases**:
- If the user enters a question but does not set the temperature or token limits, default values are applied.
- If the conversation history file does not exist when attempting to load, an error message is displayed.

## Example Usage
1. **Find a Plugin**: Log onto a Minecraft server and find a plugin.
2. **Search GitHub**: Type the plugin's name followed by "GitHub" (e.g., `https://github.com/GC-spigot/AdvancedEnchantments`).
3. **Input Repository**: Copy the repository link into the GUI and add relevant keywords (e.g., "dupe" or "glitch").
4. **Search for Issues**: Click "Findem" to search for related issues.
5. **Review Results**: Examine the results and identify potential duplication methods.
6. **Save Repositories**: Save repositories for quick access later.

### Additional Features
- **Color Picker**: Change the application's background color to personalize the interface.
- **Logo Customization**: Use a variety of logos to customize the loading screen.

## Contribution
We welcome contributions! Please refer to our contributing guidelines. For now, simply submit a pull request.

## Support
If you encounter any issues, please raise them on GitHub. Before submitting a new issue, check existing ones and ensure you have followed the installation steps correctly.

If you create a video or share this codebase, a shoutout would be appreciated! Have fun duplicating!

## License
This project is licensed under the Eclipse License, allowing anyone to use or modify the code as long as their code is also under the same license.

---
