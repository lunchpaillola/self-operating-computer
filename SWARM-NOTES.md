# SWARM-NOTES.md

This file provides essential context, conventions, and setup instructions for AI agents and new developers contributing to this repository.

---

## 1. Project Overview

- **Purpose**: A framework to enable multimodal models to operate a computer by viewing the screen and deciding on mouse and keyboard actions to reach objectives
- **Tech Stack**: Python 3.8+, OpenAI GPT-4o/4.1/o1, Claude 3, Gemini Pro Vision, Qwen-VL, LLaVa, PyAutoGUI, EasyOCR, Ultralytics YOLO, PIL
- **Structure**: Python package with command-line interface distributed via PyPI

## 2. Project Goals & Scope

- :large_green_circle: Focus: Multimodal AI computer operation, screen analysis, and automation
- :large_green_circle: In Scope: Adding new multimodal models, improving performance, cross-platform compatibility
- :red_circle: Out of Scope: Major refactoring until main.py exceeds 1000 lines (Software 2.0 approach)
- :hammer_and_wrench: Avoid introducing major dependencies without review

---

## 3. Key Directories & Architecture

- `/operate`: Main package containing all core functionality
  - `/operate/models`: AI model APIs and prompts (`apis.py`, `prompts.py`)
  - `/operate/models/weights`: YOLO model weights for Set-of-Mark prompting (`best.pt`)
  - `/operate/utils`: Utility modules (screenshot, OCR, OS operations, styling)
  - `operate.py`: Core operating logic and main loop
  - `main.py`: CLI entry point with argument parsing
  - `config.py`: Configuration management with singleton pattern
  - `exceptions.py`: Custom exception classes
- `/readme`: Documentation assets and images
- `/.github`: GitHub workflows and templates
- **Entry point**: `operate` command (via setup.py console script)

---

## 4. Coding Style & Conventions

- **Language**: Python 3.8+ (specified in GitHub workflow)
- **Code Organization**: Follow Software 2.0 principles - avoid premature refactoring
- **Imports**: Use absolute imports for internal modules (`from operate.utils.style import ...`)
- **Configuration**: Singleton pattern used for Config class
- **CLI**: Use argparse for command-line interface with descriptive help text
- **Error Handling**: Custom exceptions defined in `exceptions.py`
- **File Naming**: Use snake_case for Python files and modules
- **No formal linting/formatting tools enforced** - follow existing code style

---

## 5. Framework & Library Usage

- **AI Models**: Integrated with OpenAI (GPT-4o, GPT-4.1, o1), Claude 3, Gemini Pro Vision, Qwen-VL, LLaVa via Ollama
- **Computer Vision**: EasyOCR for text recognition, Ultralytics YOLO for object detection
- **Screen Automation**: PyAutoGUI for mouse/keyboard control, mss for screenshots
- **UI**: prompt-toolkit for interactive CLI prompts and dialogs
- **Environment**: python-dotenv for API key management
- **Async**: Limited async usage - avoid async/await patterns unless necessary
- **Dependencies**: Use only packages listed in `requirements.txt` and `requirements-audio.txt`

---

## 6. Running the Project

```bash
# Install from PyPI (recommended)
pip install self-operating-computer

# Run with default GPT-4o model
operate

# Run with specific models
operate -m o1-with-ocr
operate -m gpt-4.1-with-ocr
operate -m claude-3
operate -m gemini-pro-vision
operate -m qwen-vl
operate -m llava

# Development setup (from source)
git clone https://github.com/OthersideAI/self-operating-computer.git
cd self-operating-computer
pip install -r requirements.txt
pip install .

# Voice mode (requires additional setup)
pip install -r requirements-audio.txt
# macOS: brew install portaudio
# Linux: sudo apt install portaudio19-dev python3-pyaudio
operate --voice

# Other options
operate --verbose  # Enable verbose logging
operate --prompt "your objective"  # Direct prompt input
```

---

## 7. Testing Instructions

- **Test runner**: Custom evaluation system using `evaluate.py`
- **Location**: Main test file is `evaluate.py` in root directory
- **Test approach**: Automated objective completion with GPT-4v evaluation

### Running Tests

```bash
# Run evaluation tests
python3 evaluate.py
```

### Test Process
- Automatically prompts `operate` to perform simple objectives
- Takes screenshots after completion
- Uses GPT-4v to evaluate if objectives were successfully met
- Outputs `[PASSED]` or `[FAILED]` with justification

### Adding New Tests
- Modify `TEST_CASES` dictionary in `evaluate.py`
- Format: `"Objective for operate": "Guideline for passing evaluation"`
- Include evaluation screenshot in PRs that could impact performance

### Current Test Cases
- "Go to Github.com": Validates Github page is visible
- "Go to Youtube.com and play a video": Validates YouTube video player is visible

---

## 8. Repository Workflow

- **Branching**: Use descriptive feature branch names (e.g., `my-new-feature`)
- **Commits**: Write descriptive commit messages in imperative tense
  - Example: `Add some feature`
- **PRs**: 
  - Fork repository and create feature branch
  - Include evaluation screenshots for performance-impacting changes
  - Follow standard GitHub PR process
- **Release**: Automated PyPI publishing via GitHub Actions on version tags (`v*`)

### Standard Workflow
```bash
git checkout -b my-new-feature
git commit -am 'Add some feature'  
git push origin my-new-feature
# Create Pull Request on GitHub
```

---

## 9. Known Issues / Warnings

- **API Keys**: Must be stored in `.env` file - required for operation
- **Permissions**: macOS requires Terminal app permissions for "Screen Recording" and "Accessibility" 
- **Platform Support**: Some Linux and Windows compatibility issues remain
- **Model Requirements**: GPT-4o requires minimum $5 API credit spend to unlock access
- **LLaVA Performance**: Very high error rates when using LLaVA model
- **Screenshot Handling**: PNG files are gitignored to avoid committing test screenshots
- **Voice Mode**: Requires additional audio dependencies and platform-specific setup
- **Refactoring Policy**: Avoid major file restructuring until main.py exceeds 1000 lines
- **OCR Mode**: Default mode uses EasyOCR for better performance than vanilla GPT-4
- **Model Weights**: YOLOv8 model weights (`best.pt`) included for Set-of-Mark prompting