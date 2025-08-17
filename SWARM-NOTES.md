# SWARM-NOTES.md

This file provides essential context, conventions, and setup instructions for AI agents and new developers contributing to this repository.

---

## 1. Project Overview

- **Purpose**: A framework to enable multimodal models to operate a computer using the same inputs and outputs as a human operator
- **Tech Stack**: Python 3.x, PyAutoGUI, PIL/Pillow, OpenAI API, Google AI, Anthropic Claude, Qwen-VL, LLaVA via Ollama, EasyOCR, YOLOv8
- **Structure**: Monolithic Python package with modular utilities for cross-platform computer automation

---

## 2. Project Goals & Scope

- 🟢 **Focus**: Enabling AI models to view screenshots and execute mouse/keyboard actions to complete objectives
- 🟢 **Scope**: Cross-platform support (macOS, Windows, Linux), multiple AI model integrations, OCR and computer vision capabilities
- 🔴 **Out of Scope**: Web UI, mobile support, complex application-specific integrations
- 🛠️ **Do not introduce**: Major dependencies without review, breaking changes to the core operation flow

---

## 3. Key Directories & Architecture

- `/operate/`: Main package containing core functionality
  - `/operate/main.py`: CLI entry point and argument parsing
  - `/operate/operate.py`: Core orchestration logic and main loop
  - `/operate/config.py`: Configuration management and API key handling
  - `/operate/models/`: AI model integrations and prompt management
    - `/operate/models/apis.py`: API clients for various AI services
    - `/operate/models/prompts.py`: System prompts and user interaction templates
    - `/operate/models/weights/`: YOLOv8 model weights for object detection
  - `/operate/utils/`: Utility modules
    - `/operate/utils/operating_system.py`: Cross-platform mouse/keyboard automation
    - `/operate/utils/screenshot.py`: Screen capture utilities
    - `/operate/utils/ocr.py`: Optical character recognition functions
    - `/operate/utils/label.py`: YOLO-based object labeling and detection
    - `/operate/utils/style.py`: Terminal styling and ANSI color codes
- **Entry point**: `operate` command (installed via pip) or `python -m operate.main`

---

## 4. Coding Style & Conventions

- **Imports**: Group standard library, third-party, and local imports with blank lines between groups
- **Error handling**: Use try-catch blocks with specific exception types, print error messages with context
- **Logging**: Use `config.verbose` flag for debug output, prefix log messages with module context
- **Naming**: Use descriptive variable names, snake_case for functions and variables
- **Comments**: Include docstrings for public functions, inline comments for complex logic
- **Formatting**: Follow PEP 8 standards, use consistent indentation (4 spaces)

---

## 5. Framework & Library Usage

- **Automation**: PyAutoGUI for cross-platform mouse/keyboard control
- **Image processing**: PIL/Pillow for screenshot manipulation and OCR
- **AI Models**: OpenAI GPT-4, Google Gemini, Anthropic Claude, Qwen-VL, LLaVA via Ollama
- **Computer Vision**: YOLOv8 for object detection, EasyOCR for text recognition
- **Async**: Limited async support - most operations are synchronous
- **3rd-party**: Use dependencies listed in `requirements.txt` only, avoid adding new packages without review

---

## 6. Running the Project

```bash
# Install dependencies
pip install -r requirements.txt

# Install the package locally
pip install -e .

# Run with default model (GPT-4 with OCR)
operate

# Run with specific model
operate -m gpt-4-with-ocr
operate -m gemini-pro-vision
operate -m claude-3
operate -m qwen-vl
operate -m llava

# Run with voice input
operate --voice

# Run with direct prompt
operate --prompt "Go to google.com"

# Run in verbose mode
operate --verbose

# Run evaluation tests
python evaluate.py
```

---

## 7. Testing Instructions

- **Test runner**: Use `python evaluate.py` for automated testing
- **Location**: Tests are defined in `evaluate.py` in the root directory
- **Test cases**: Currently includes "Go to Github.com" and "Go to Youtube.com and play a video"
- **Evaluation**: GPT-4 evaluates screenshots against success criteria
- **Before committing code**:
  - Run `python evaluate.py` to ensure all test cases pass
  - Include screenshot of evaluation output in PRs that could impact performance
- **Adding new tests**:
  - Add test case to `TEST_CASES` dictionary in `evaluate.py`
  - Define clear success criteria for each test
  - Ensure tests are simple and reproducible

---

## 8. Repository Workflow

- **Branching**: Use descriptive feature branch names (e.g., `feat/add-new-model`, `fix/linux-compatibility`)
- **Commits**: Write descriptive commit messages explaining what was changed and why
- **PRs**: Include evaluation test results for performance-impacting changes
- **Testing**: Run `python evaluate.py` before submitting PRs
- **Code review**: Focus on maintaining cross-platform compatibility and performance

---

## 9. Known Issues / Warnings

- **Linux compatibility**: Some issues with Linux and Windows compatibility exist - PRs to fix are encouraged
- **Dependencies**: Avoid adding major new dependencies without team review
- **Performance**: Screenshot grid overlay is critical for click accuracy - changes require evaluation
- **Security**: Framework executes arbitrary mouse/keyboard actions - use with caution
- **API keys**: Multiple API keys required for different models (OpenAI, Google, Anthropic, Qwen)
- **Voice mode**: Requires additional `requirements-audio.txt` and system dependencies (portaudio)
- **Ollama**: LLaVA integration has high error rates, intended as experimental base for local models
- **YOLOv8**: Model weights (`best.pt`) are included - users can swap in improved models
