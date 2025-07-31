# AiNiee Project Information for Claude

This file contains essential information about the AiNiee project to help Claude understand and work with the codebase effectively.

## Project Overview

**AiNiee** is an AI-powered translation tool specializing in translating complex long-text content such as games, books, subtitles, and documents. It features:

- **Multi-format support**: Games (Mtool, Renpy, Translator++, etc.), eBooks (EPUB/TXT), subtitles (SRT/VTT/LRC), documents (Word/PDF/MD)
- **Smart translation**: Chain-of-thought translation, AI glossaries, contextual awareness
- **Quality features**: AI refinement, formatting, terminology extraction
- **Multi-platform API support**: OpenAI, DeepSeek, Google, Anthropic, local models, and many more

## Project Structure

```
/Users/turygo/code/python/AiNiee/
├── AiNiee.py                    # Main entry point
├── AiNiee.spec                  # PyInstaller build configuration
├── requirements.txt             # Python dependencies
├── README.md                    # Chinese documentation
├── README_EN.md                 # English documentation
├── Base/                        # Core base classes
│   ├── Base.py                  # Core constants and event definitions
│   ├── EventManager.py          # Event system
│   └── PluginManager.py         # Plugin management
├── ModuleFolders/              # Core modules
│   ├── Cache/                  # Translation caching system
│   ├── FileAccessor/           # File access utilities
│   ├── FileConverter/          # File format converters
│   ├── FileOutputer/           # Output file writers
│   ├── FileReader/             # Input file readers
│   ├── LLMRequester/           # LLM API clients
│   ├── PromptBuilder/          # Prompt construction
│   ├── RequestLimiter/         # Rate limiting
│   ├── ResponseChecker/        # Response validation
│   ├── TaskExecutor/           # Translation task execution
│   └── TextProcessor/          # Text processing utilities
├── UserInterface/              # PyQt5 GUI components
│   ├── AppFluentWindow.py      # Main window
│   ├── Settings/               # Settings pages
│   ├── TranslationSettings/    # Translation configuration
│   └── Table/                  # Table management (glossary, etc.)
├── Widget/                     # Custom UI widgets
├── PluginScripts/              # Plugin system
├── Resource/                   # Resources and configuration
│   ├── config.json            # Main configuration file
│   ├── Localization/          # UI translations
│   ├── Prompt/                # Translation prompts
│   ├── Regex/                 # Text processing patterns
│   └── platforms/preset.json  # Platform presets
├── StevExtraction/            # Game text extraction tool
└── Tools/                     # Build and utility scripts
```

## Key Components

### 1. Main Application (`AiNiee.py`)
- Entry point for the GUI application
- Initializes PyQt5 application with high DPI support
- Loads configuration from `Resource/config.json`
- Displays splash screen during startup

### 2. Event System (`Base/EventManager.py`, `Base/Base.py`)
- Event-driven architecture for loose coupling
- Key events: `TASK_START`, `TASK_UPDATE`, `TASK_STOP`, `TASK_COMPLETED`
- Status states: `IDLE`, `TASKING`, `STOPING`, `TASKSTOPPED`

### 3. File Processing Pipeline
- **Readers** (`FileReader/`): Parse various input formats
- **Cache** (`Cache/`): Store translation progress
- **Executors** (`TaskExecutor/`): Process translation tasks
- **Writers** (`FileOutputer/`): Generate output files

### 4. LLM Integration (`LLMRequester/`)
Supports multiple AI providers:
- **Local**: SakuraLLM, LocalLLM (via OpenAI API)
- **Online**: OpenAI, Anthropic, Google, DeepSeek, Cohere, Amazon Bedrock, and more
- **Chinese**: Volcengine, Dashscope, Zhipu, Yi, Moonshot

### 5. Plugin System (`PluginScripts/`)
Extensible architecture for custom functionality:
- Language filters
- Text normalizers
- Bilingual output
- Custom text processing

## Key Commands and Workflows

### Running the Application
```bash
# Install dependencies
pip install -r requirements.txt

# Run the application
python AiNiee.py
```

### Building Executable
```bash
# Build using PyInstaller
pyinstaller AiNiee.spec
```

### Configuration
- Main config: `Resource/config.json`
- Platform presets: `Resource/platforms/preset.json`
- UI translations: `Resource/Localization/*.json`

## Translation Workflow

1. **Configure API**: Set up AI provider credentials
2. **Input Files**: Drag folder with source files into the application
3. **Configure Translation**: Set target language and translation parameters
4. **Start Translation**: Click start button to begin processing
5. **Export Results**: Translations saved to output folder

## Development Guidelines

### Code Style
- Use type hints where appropriate
- Follow existing code patterns
- No unnecessary comments unless requested
- Security: Never expose API keys or secrets

### File Format Support
- Game formats: Mtool, Renpy, Translator++, ParaTranz, VNText, SExtractor
- Document formats: EPUB, TXT, DOCX, PDF, MD
- Subtitle formats: SRT, VTT, LRC
- Data formats: JSON (I18Next), PO files

### Testing
Check README or search codebase for testing approach before running tests.

### Linting and Type Checking
Run appropriate linting commands (npm run lint, ruff, etc.) after making changes.

## Important Files

- `AiNiee.py:84` - Main application entry point
- `Base/Base.py:68` - Core base class with events and status
- `ModuleFolders/TaskExecutor/TaskExecutor.py:26` - Main translation executor
- `Resource/config.json` - Application configuration
- `Resource/platforms/preset.json` - AI platform presets

## Notes for Claude

1. This is a PyQt5-based desktop application for AI translation
2. The project uses an event-driven architecture for component communication
3. Multiple file formats are supported through a plugin-like reader/writer system
4. The application supports both online and local AI models
5. Configuration is stored in JSON files under the Resource directory
6. The project includes comprehensive Chinese and English documentation