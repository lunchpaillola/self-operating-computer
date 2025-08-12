# Self-Operating Computer Framework

<p align="center">
  <strong>A multimodal AI framework that enables autonomous computer operation through vision and natural language understanding.</strong>
</p>

<p align="center">
  The Self-Operating Computer Framework represents a breakthrough in human-computer interaction, allowing AI models to perceive, understand, and interact with computer interfaces just like humans do. By combining computer vision, natural language processing, and automated input control, this framework enables AI to operate computers autonomously to accomplish complex tasks.
</p>

<div align="center">
  <img src="https://github.com/OthersideAI/self-operating-computer/blob/main/readme/self-operating-computer.png" width="750"  style="margin: 10px;"/>
</div>

## 🚀 What is Self-Operating Computer?

The Self-Operating Computer Framework is an innovative open-source project that bridges the gap between AI language models and computer interfaces. Released in November 2023, it was one of the first implementations to successfully demonstrate multimodal AI models operating computers through visual understanding and automated control.

**Core Concept**: The framework works by taking screenshots of your computer screen, analyzing them with multimodal AI models (like GPT-4 Vision, Claude 3, or Gemini), and then executing the appropriate mouse clicks, keyboard inputs, and other actions to accomplish user-defined objectives.

**Key Innovation**: Unlike traditional automation tools that rely on pre-programmed scripts or element selectors, this framework uses AI vision to understand interfaces dynamically, making it adaptable to any application or website without prior configuration.

## ✨ Key Features & Capabilities

### 🤖 **Multi-Model Support**
- **OpenAI Integration**: GPT-4o, GPT-4.1, o1 models with advanced vision capabilities
- **Google AI**: Gemini Pro Vision for diverse AI perspectives
- **Anthropic**: Claude 3 with sophisticated visual reasoning
- **Open Source Options**: Qwen-VL and LLaVa through Ollama for local deployment
- **Extensible Architecture**: Easy integration of new multimodal models

### 🎯 **Advanced Interaction Methods**
- **Optical Character Recognition (OCR)**: Enhanced text detection and clickable element mapping
- **Set-of-Mark (SoM) Prompting**: Visual grounding with YOLOv8-based element detection
- **Voice Input**: Natural language voice commands for hands-free operation
- **Grid-based Positioning**: Precise coordinate-based interaction system

### 🖥️ **Cross-Platform Compatibility**
- **macOS**: Full native support with accessibility permissions
- **Windows**: Complete functionality with Windows-specific optimizations
- **Linux**: X11 server support for desktop environments

### 🔧 **Flexible Operation Modes**
- **Interactive Mode**: Real-time conversation and task execution
- **Batch Mode**: Direct prompt input for automated workflows
- **Voice Mode**: Hands-free operation with speech recognition
- **Verbose Mode**: Detailed logging for debugging and analysis

## 🏗️ Architecture & Workflow

### High-Level Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   User Input    │───▶│  AI Model API    │───▶│  Action Engine  │
│ (Text/Voice)    │    │ (Vision + NLP)   │    │ (Mouse/Keyboard)│
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                        │                        │
         │                        ▼                        │
         │              ┌──────────────────┐               │
         │              │  Screenshot      │               │
         └──────────────│  Analysis        │◀──────────────┘
                        │  & OCR/SoM       │
                        └──────────────────┘
```

### Workflow Process

1. **Objective Input**: User provides a natural language goal (e.g., "Book a flight to Paris")
2. **Screen Capture**: Framework takes a screenshot of the current desktop state
3. **Visual Analysis**: AI model analyzes the screenshot to understand the interface
4. **Action Planning**: Model determines the sequence of actions needed
5. **Execution**: Framework performs mouse clicks, keyboard inputs, or other actions
6. **Feedback Loop**: Process repeats until the objective is accomplished or user intervention is needed

### Core Components

- **`operate/main.py`**: Entry point and command-line interface
- **`operate/operate.py`**: Main orchestration logic and execution loop
- **`operate/models/apis.py`**: AI model integrations and API management
- **`operate/utils/`**: Utility modules for screenshots, OCR, and OS interactions
- **`operate/config.py`**: Configuration management and model validation

## 📦 Installation & Setup

### Quick Start (Recommended)

1. **Install via pip** (easiest method):
   ```bash
   pip install self-operating-computer
   ```

2. **Run the framework**:
   ```bash
   operate
   ```

3. **Configure API Key**: On first run, you'll be prompted to enter your OpenAI API key
   - Get your key from [OpenAI Platform](https://platform.openai.com/account/api-keys)
   - The key will be saved locally in a `.env` file

4. **Grant Permissions** (macOS):
   - System will request "Screen Recording" and "Accessibility" permissions
   - Navigate to: System Preferences → Security & Privacy → Privacy
   - Enable permissions for Terminal (or your terminal application)

### Development Setup

For contributors or advanced users who want to modify the code:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/OthersideAI/self-operating-computer.git
   cd self-operating-computer
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Install in development mode**:
   ```bash
   pip install -e .
   ```

4. **Run from source**:
   ```bash
   python -m operate.main
   ```

### Voice Mode Setup (Optional)

For voice input capabilities:

1. **Install audio dependencies**:
   ```bash
   pip install -r requirements-audio.txt
   ```

2. **Install system audio libraries**:
   
   **macOS**:
   ```bash
   brew install portaudio
   ```
   
   **Linux (Ubuntu/Debian)**:
   ```bash
   sudo apt install portaudio19-dev python3-pyaudio
   ```

3. **Run with voice mode**:
   ```bash
   operate --voice
   ```

## 🎮 Usage Examples & Common Commands

### Basic Usage

```bash
# Run with default GPT-4 + OCR model
operate

# Run with specific model
operate -m gpt-4o

# Direct prompt input (no interactive mode)
operate --prompt "Open Gmail and check for unread emails"

# Enable verbose logging
operate --verbose

# Use voice input
operate --voice
```

### Model-Specific Commands

```bash
# OpenAI Models
operate -m gpt-4o              # GPT-4 Omni (default)
operate -m o1-with-ocr         # OpenAI o1 with OCR
operate -m gpt-4.1-with-ocr    # GPT-4.1 with OCR

# Other AI Providers
operate -m gemini-pro-vision   # Google Gemini
operate -m claude-3            # Anthropic Claude
operate -m qwen-vl             # Alibaba Qwen-VL

# Local Models (requires Ollama)
operate -m llava               # LLaVa via Ollama
```

### Advanced Features

```bash
# OCR Mode (default, best performance)
operate -m gpt-4-with-ocr

# Set-of-Mark visual prompting
operate -m gpt-4-with-som

# Combine voice input with specific model
operate -m claude-3 --voice

# Batch processing with verbose output
operate --prompt "Create a new document and type 'Hello World'" --verbose
```

### Example Objectives

Try these sample objectives to test the framework:

- **Web Browsing**: "Go to Wikipedia and search for 'Artificial Intelligence'"
- **File Management**: "Create a new folder called 'AI Projects' on the desktop"
- **Application Usage**: "Open Calculator and compute 15 * 24"
- **Content Creation**: "Open TextEdit and write a haiku about technology"
- **Email Tasks**: "Check my Gmail inbox for emails from today"

## 🛠️ Configuration & Customization

### API Key Management

```bash
# View current configuration
cat .env

# Edit configuration manually
vim .env

# Environment variables
export OPENAI_API_KEY="your-key-here"
export GOOGLE_API_KEY="your-gemini-key"
export ANTHROPIC_API_KEY="your-claude-key"
```

### Model Configuration

The framework automatically handles model-specific configurations, but you can customize:

- **Temperature settings** for response creativity
- **Max tokens** for response length
- **Timeout values** for API calls
- **Screenshot quality** and processing options

## 🧪 Testing & Evaluation

### Automated Testing

Run the built-in evaluation suite:

```bash
python evaluate.py
```

This will:
- Execute a series of common tasks
- Evaluate success/failure automatically
- Provide detailed performance feedback
- Generate test reports with screenshots

### Manual Testing

Test basic functionality:

1. **Simple Task**: "Take a screenshot" → Should capture and save screen
2. **Navigation**: "Open a web browser" → Should launch default browser
3. **Text Input**: "Type 'Hello World'" → Should input text at cursor location

## 🤝 Contributing

We welcome contributions from the community! This project follows the [Software 2.0](https://karpathy.medium.com/software-2-0-a64152b37c35) philosophy, emphasizing AI-driven development.

### Quick Contribution Guide

1. **Fork** the repository on GitHub
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/self-operating-computer.git
   ```
3. **Create** a feature branch:
   ```bash
   git checkout -b my-new-feature
   ```
4. **Make** your changes and test them:
   ```bash
   pip install -e .
   operate  # Test your changes
   python evaluate.py  # Run test suite
   ```
5. **Commit** and push:
   ```bash
   git commit -am 'Add amazing new feature'
   git push origin my-new-feature
   ```
6. **Submit** a Pull Request

### Contribution Ideas

- **🎯 Performance Optimization**: Improve screenshot grid systems and action accuracy
- **🌐 Platform Support**: Enhance Linux and Windows compatibility
- **🤖 Model Integration**: Add support for new multimodal AI models
- **🔒 Security Features**: Implement confirmation prompts for sensitive actions
- **📊 Analytics**: Add performance metrics and success rate tracking
- **🎨 UI/UX**: Improve user interaction and feedback systems

### Development Guidelines

- Keep core logic in `operate/main.py` until it exceeds 1000 lines
- Include evaluation screenshots with performance-impacting PRs
- Follow existing code style and documentation patterns
- Test across different operating systems when possible

For detailed guidelines, see [CONTRIBUTING.md](CONTRIBUTING.md).

## 📚 Additional Resources

### Community & Support

- **Discord Community**: Join our active community for real-time support
  - Existing members: [#self-operating-computer](https://discord.com/channels/877638638001877052/1181241785834541157)
  - New users: [Join Discord Server](https://discord.gg/YqaKtyBEzM) → Navigate to #self-operating-computer

- **Social Media**: Stay updated with latest developments
  - Twitter: [@HyperWriteAI](https://twitter.com/HyperWriteAI)
  - LinkedIn: [HyperWriteAI Company](https://www.linkedin.com/company/othersideai/)

### Documentation & Learning

- **Research Paper**: [Set-of-Mark Prompting](https://arxiv.org/abs/2310.11441) - Learn about SoM visual prompting
- **Ollama Integration**: [Ollama GitHub](https://www.github.com/ollama/ollama) - Local model deployment
- **OpenAI Documentation**: [Rate Limits Guide](https://platform.openai.com/docs/guides/rate-limits?context=tier-one)

## ⚙️ System Requirements & Compatibility

### Operating Systems
- **macOS**: Full native support (10.14+ recommended)
- **Windows**: Complete functionality (Windows 10+ recommended)  
- **Linux**: X11 server required for desktop environments

### Hardware Requirements
- **RAM**: 4GB minimum, 8GB recommended
- **Storage**: 2GB free space (additional for local models)
- **Network**: Stable internet connection for cloud AI models

### API Requirements
- **OpenAI**: GPT-4 access requires $5+ in API credits ([Learn more](https://platform.openai.com/docs/guides/rate-limits?context=tier-one))
- **Google AI**: Free tier available through [AI Studio](https://makersuite.google.com/app/apikey)
- **Anthropic**: Claude API access through [Console](https://console.anthropic.com/dashboard)

## ⚠️ Important Notes

### Security Considerations
- The framework can perform any action a human user can perform
- Always review objectives before execution, especially for sensitive operations
- Consider running in a sandboxed environment for testing

### Rate Limiting
- Cloud AI models have rate limits and usage costs
- Monitor your API usage to avoid unexpected charges
- Consider local models (LLaVa) for extensive testing

### Performance Notes
- First-time model downloads may take several minutes
- Screenshot processing and AI inference add latency to actions
- Performance varies significantly between different AI models

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for GPT-4 Vision capabilities
- Anthropic for Claude 3 multimodal support
- Google for Gemini Pro Vision
- The open-source community for continuous improvements and feedback
- All contributors who have helped make this project possible

---

**Ready to get started?** Install with `pip install self-operating-computer` and run `operate` to begin your journey with AI-powered computer operation!
