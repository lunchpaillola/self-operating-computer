<h1 align="center">Self-Operating Computer Framework</h1>

<p align="center">
  <strong>A framework to enable multimodal models to operate a computer using the same inputs and outputs as a human operator.</strong>
</p>

<p align="center">
  Using vision, speech, and text capabilities, the model views the screen and decides on a series of mouse and keyboard actions to reach an objective. Released Nov 2023, the Self-Operating Computer Framework was one of the first examples of using a multimodal model to view the screen and operate a computer.
</p>

<div align="center">
  <img src="https://github.com/OthersideAI/self-operating-computer/blob/main/readme/self-operating-computer.png" width="750"  style="margin: 10px;"/>
</div>

<!--
:rotating_light: **OUTAGE NOTIFICATION: gpt-4o**
**This model is currently experiencing an outage so the self-operating computer may not work as expected.**
-->

## 🎯 Project Purpose & Goals

The Self-Operating Computer Framework enables AI models to autonomously interact with desktop environments by:

- **Viewing and understanding** screen content through computer vision
- **Planning and executing** mouse and keyboard actions to complete objectives
- **Supporting multiple modalities** including vision, speech, and text inputs
- **Maintaining human-like interaction patterns** for natural computer operation

### High-Level Goals
- Enable seamless AI-computer interaction across platforms (macOS, Windows, Linux)
- Support extensible multimodal model integrations
- Provide a robust foundation for computer automation research and applications
- Maintain security, privacy, and safety in AI-driven computer operations

## ✨ Key Features & Supported Modalities

### Core Capabilities
- **Cross-Platform Support**: Native compatibility with macOS, Windows, and Linux
- **Multiple AI Model Integration**: GPT-4o, GPT-4.1, o1, Gemini Pro Vision, Claude 3, Qwen-VL, and LLaVA
- **Advanced Computer Vision**: YOLOv8-based object detection and EasyOCR text recognition
- **Intelligent Click Targeting**: OCR-based element mapping and Set-of-Mark (SoM) prompting
- **Voice Input Support**: Speech-to-text for natural language objectives
- **Real-time Screen Analysis**: Live screenshot processing and decision making

### Supported Input Modalities
- **Vision**: Screenshot analysis, object detection, text recognition
- **Speech**: Voice commands for objectives (with additional audio dependencies)
- **Text**: Direct command-line prompts and interactive input
- **Hybrid**: Combination of multiple modalities for enhanced accuracy

### Output Capabilities
- **Mouse Actions**: Precise clicking, dragging, scrolling
- **Keyboard Input**: Text typing, keyboard shortcuts, navigation
- **System Integration**: Cross-platform automation with native OS APIs

## Demo
https://github.com/OthersideAI/self-operating-computer/assets/42594239/9e8abc96-c76a-46fb-9b13-03678b3c67e0

## 🚀 Getting Started

### Prerequisites
- **Python 3.7+** with pip package manager
- **Operating System**: macOS, Windows, or Linux (with X server)
- **API Keys**: At least one of the following:
  - OpenAI API key for GPT models
  - Google AI Studio API key for Gemini
  - Anthropic API key for Claude
  - Qwen API key for Qwen-VL
- **System Permissions**: Screen recording and accessibility permissions (required on macOS)

### Quick Installation

1. **Install via pip** (recommended)
```bash
pip install self-operating-computer
```

2. **Or install from source**
```bash
git clone https://github.com/OthersideAI/self-operating-computer.git
cd self-operating-computer
pip install -e .
```

### Setup & Configuration

1. **Run the framework**
```bash
operate
```

2. **Configure API Key**: On first run, you'll be prompted to enter your API key. You can obtain keys here:
   - [OpenAI API Key](https://platform.openai.com/account/api-keys)
   - [Google AI Studio API Key](https://makersuite.google.com/app/apikey)
   - [Anthropic API Key](https://console.anthropic.com/dashboard)

<div align="center">
  <img src="https://github.com/OthersideAI/self-operating-computer/blob/main/readme/key.png" width="300"  style="margin: 10px;"/>
</div>

3. **Grant System Permissions** (macOS): The Terminal app will request permissions for "Screen Recording" and "Accessibility" in System Preferences > Security & Privacy.

<div align="center">
  <img src="https://github.com/OthersideAI/self-operating-computer/blob/main/readme/terminal-access-1.png" width="300"  style="margin: 10px;"/>
  <img src="https://github.com/OthersideAI/self-operating-computer/blob/main/readme/terminal-access-2.png" width="300"  style="margin: 10px;"/>
</div>

### Voice Mode Setup (Optional)

For voice input capabilities, install additional dependencies:

```bash
# Install audio requirements
pip install -r requirements-audio.txt

# Install system dependencies
# macOS:
brew install portaudio

# Linux:
sudo apt install portaudio19-dev python3-pyaudio
```

## 💡 Example Use Cases

The Self-Operating Computer Framework can automate a wide variety of desktop tasks:

### **Web Browsing & Research**
- Navigate to websites and extract information
- Fill out forms and submit data
- Compare products across multiple sites
- Download files and organize content

### **Productivity & Office Tasks**
- Create and edit documents in various applications
- Manage email and calendar appointments
- Organize files and folders
- Take screenshots and create presentations

### **Development & Testing**
- Automate software testing workflows
- Set up development environments
- Execute repetitive coding tasks
- Validate UI/UX across different applications

### **Creative & Media Tasks**
- Edit images and videos using desktop applications
- Create content across multiple platforms
- Manage digital asset libraries
- Automate social media posting workflows

## 🛠️ Usage & Model Selection

### Basic Usage

```bash
# Run with default model (GPT-4 with OCR)
operate

# Run with voice input
operate --voice

# Run with direct prompt
operate --prompt "Go to google.com"

# Run in verbose mode for debugging
operate --verbose
```

### Available AI Models

#### OpenAI Models
```bash
# Default: GPT-4 with OCR (recommended)
operate
operate -m gpt-4-with-ocr

# Latest GPT-4.1 model
operate -m gpt-4.1-with-ocr

# OpenAI's o1 model
operate -m o1-with-ocr

# GPT-4 with Set-of-Mark prompting
operate -m gpt-4-with-som
```

#### Google Gemini
```bash
operate -m gemini-pro-vision
```
**Setup**: Requires [Google AI Studio API key](https://makersuite.google.com/app/apikey) and [desktop application credentials](https://ai.google.dev/palm_docs/oauth_quickstart).

#### Anthropic Claude
```bash
operate -m claude-3
```
**Setup**: Requires [Anthropic API key](https://console.anthropic.com/dashboard).

#### Qwen-VL
```bash
operate -m qwen-vl
```
**Setup**: Requires [Qwen API key](https://bailian.console.aliyun.com/).

#### Local Models (LLaVA via Ollama)
```bash
# Install Ollama from https://ollama.ai/download
ollama pull llava
ollama serve

# Run with LLaVA
operate -m llava
```
**Note**: LLaVA has high error rates and is experimental. Requires ~5GB storage.

### Advanced Features

#### Optical Character Recognition (OCR) Mode
The default `gpt-4-with-ocr` mode provides enhanced accuracy by:
- Creating a hash map of clickable elements by coordinates
- Enabling text-based element selection
- Improving click precision through OCR analysis

#### Set-of-Mark (SoM) Prompting
The `gpt-4-with-som` mode uses visual prompting to enhance grounding:
- YOLOv8-based object detection for UI elements
- Visual markers overlaid on screenshots
- Improved spatial understanding for complex interfaces

Learn more: [SoM Prompting Research Paper](https://arxiv.org/abs/2310.11441)

#### Voice Input Mode
Enable natural language voice commands:
```bash
operate --voice
```
Requires additional audio dependencies (see Voice Mode Setup above).

## 🏗️ Technical Architecture & Implementation Guidelines

### Critical Design Constraints

Based on the project's technical requirements, the following constraints must be maintained:

1. **Modularity**: Maintain modular design for adding/removing input/output modalities
2. **Human-like Simulation**: Ensure all interactions can be simulated as a human operator would
3. **Extensibility**: Support extensibility for new input/output types and AI models
4. **Security & Privacy**: Prioritize security and privacy of user data and system access
5. **Minimal Dependencies**: Keep dependencies minimal and well-documented
6. **API Documentation**: Document all APIs and extension points thoroughly
7. **Error Handling**: Provide robust error handling and comprehensive logging
8. **Cross-Platform**: Ensure compatibility across macOS, Windows, and Linux

### Key Technical Patterns

The framework follows established patterns for maintainability and extensibility:

- **Modular AI Model Integration**: Each model (GPT-4, Gemini, Claude, etc.) is implemented as a separate module in `/operate/models/`
- **Utility-Based Architecture**: Core functionality is separated into focused utility modules (`screenshot.py`, `ocr.py`, `operating_system.py`, etc.)
- **Configuration Management**: Centralized configuration handling in `config.py` for API keys and settings
- **Cross-Platform Abstraction**: Platform-specific code is abstracted in `operating_system.py`
- **Prompt Engineering**: Systematic prompt management in `prompts.py` for consistent AI interactions
- **Computer Vision Pipeline**: Integrated OCR and object detection for enhanced screen understanding
- **Error Recovery**: Graceful handling of API failures and system permission issues

### Project Structure

```
self-operating-computer/
├── operate/                    # Main package
│   ├── main.py                # CLI entry point
│   ├── operate.py             # Core orchestration logic
│   ├── config.py              # Configuration management
│   ├── models/                # AI model integrations
│   │   ├── apis.py           # API clients for AI services
│   │   ├── prompts.py        # System prompts and templates
│   │   └── weights/          # YOLOv8 model weights
│   └── utils/                 # Utility modules
│       ├── operating_system.py  # Cross-platform automation
│       ├── screenshot.py        # Screen capture utilities
│       ├── ocr.py              # Text recognition
│       ├── label.py            # Object detection
│       └── style.py            # Terminal styling
├── evaluate.py               # Automated testing framework
├── requirements.txt          # Core dependencies
├── requirements-audio.txt    # Voice mode dependencies
└── SWARM-NOTES.md           # Technical guidelines
```

## 🧪 Testing & Evaluation

### Running Tests

The framework includes an automated evaluation system to ensure consistent performance:

```bash
# Run all test cases
python evaluate.py
```

### Test Cases
- **Basic Navigation**: "Go to Github.com"
- **Interactive Tasks**: "Go to Youtube.com and play a video"
- **Custom Evaluations**: GPT-4 evaluates screenshots against success criteria

### Before Contributing
- Run `python evaluate.py` to ensure all test cases pass
- Include evaluation screenshots in PRs that could impact performance
- Test across multiple platforms when possible

## 🤝 Contributing

We welcome contributions to improve the Self-Operating Computer Framework!

### How to Contribute

1. **Fork the repository** and create a feature branch
2. **Make your changes** following the coding conventions in [SWARM-NOTES.md](SWARM-NOTES.md)
3. **Test your changes** using `python evaluate.py`
4. **Submit a Pull Request** with evaluation screenshots for performance-impacting changes

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

### Priority Contribution Areas

- **Performance Optimization**: Improve screenshot grid overlay for better click accuracy
- **Cross-Platform Compatibility**: Fix remaining Linux and Windows compatibility issues
- **New Model Integration**: Add support for additional multimodal models
- **Enhanced Security**: Implement confirmation prompts for potentially harmful actions
- **Prompt Engineering**: Improve system prompts for better model performance

### Development Workflow

```bash
# Clone and setup development environment
git clone https://github.com/OthersideAI/self-operating-computer.git
cd self-operating-computer
pip install -e .

# Make changes and test
python evaluate.py

# Follow conventional commit format
git commit -m "feat: add new model integration"
```

## ⚠️ Security & Safety Considerations

**Important**: This framework executes arbitrary mouse and keyboard actions on your computer. Use with caution and awareness:

- **Supervised Operation**: Monitor the framework during operation, especially in production environments
- **API Key Security**: Store API keys securely and never commit them to version control
- **Permission Management**: Grant only necessary system permissions
- **Data Privacy**: Be aware that screenshots and actions may be sent to AI model APIs
- **Testing Environment**: Use in isolated or test environments when possible

## 🔧 System Compatibility & Requirements

### Operating System Support
- **macOS**: Full support with native permission handling
- **Windows**: Supported (some compatibility issues being addressed)
- **Linux**: Supported with X server (some compatibility issues being addressed)

### Hardware Requirements
- **RAM**: Minimum 4GB (8GB recommended for local models)
- **Storage**: 1GB for framework + 5GB additional for local LLaVA model
- **Network**: Internet connection required for cloud-based AI models
- **Display**: Standard desktop display (multi-monitor setups supported)

### Known Limitations
- **Linux/Windows**: Some platform-specific issues exist (contributions welcome)
- **LLaVA/Ollama**: High error rates, intended as experimental foundation
- **API Rate Limits**: OpenAI requires $5 minimum spend for GPT-4 access
- **Performance**: Screenshot processing may have latency on slower systems

## 📚 Additional Resources

### Documentation
- [SWARM-NOTES.md](SWARM-NOTES.md) - Technical guidelines and conventions
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contribution guidelines and workflow
- [Set-of-Mark Research Paper](https://arxiv.org/abs/2310.11441) - SoM prompting methodology

### Community & Support
- **Discord**: Join our [Discord Server](https://discord.gg/YqaKtyBEzM) for real-time discussions in [#self-operating-computer](https://discord.com/channels/877638638001877052/1181241785834541157)
- **Twitter**: Follow [@HyperWriteAI](https://twitter.com/HyperWriteAI) for updates
- **LinkedIn**: Connect with [HyperWriteAI](https://www.linkedin.com/company/othersideai/)
- **Feedback**: Reach out to [Josh](https://twitter.com/josh_bickett) for project input

### API Documentation & Rate Limits
- **OpenAI**: Requires $5 minimum API spend for GPT-4 access. [Learn more](https://platform.openai.com/docs/guides/rate-limits?context=tier-one)
- **Google AI**: Free tier available with rate limits. [Get API key](https://makersuite.google.com/app/apikey)
- **Anthropic**: Usage-based pricing. [Get API key](https://console.anthropic.com/dashboard)

## 📋 Future Roadmap & TODOs

### Planned Enhancements
- [ ] Enhanced security features with user confirmation for sensitive actions
- [ ] Improved Linux and Windows compatibility
- [ ] Additional multimodal model integrations
- [ ] Performance optimization for screenshot processing
- [ ] Enhanced error handling and recovery mechanisms
- [ ] Mobile platform support exploration
- [ ] Web UI for remote operation (currently out of scope)

### Research Areas
- [ ] Optimal screenshot grid configuration for improved click accuracy
- [ ] Advanced prompt engineering for better model performance
- [ ] Local model performance improvements
- [ ] Multi-step task planning and execution
- [ ] Integration with specialized computer vision models

---

*For technical implementation details, development patterns, and safety guidelines, please review [SWARM-NOTES.md](SWARM-NOTES.md) before contributing.*
