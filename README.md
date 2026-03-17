# Everything Search CLI Helper Skill

[![GitHub stars](https://img.shields.io/github/stars/WhizZest/Everything-Search?style=social)](https://github.com/WhizZest/Everything-Search/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/WhizZest/Everything-Search?style=social)](https://github.com/WhizZest/Everything-Search/network/members)
[![GitHub issues](https://img.shields.io/github/issues/WhizZest/Everything-Search)](https://github.com/WhizZest/Everything-Search/issues)
[![GitHub license](https://img.shields.io/github/license/WhizZest/Everything-Search)](https://github.com/WhizZest/Everything-Search/blob/main/LICENSE)

> A comprehensive helper skill for ES (Everything Search) command-line tool on Windows - Fast, efficient file search utility with advanced filtering and sorting capabilities.

## 🚀 About

**Everything Search** is a specialized skill that provides comprehensive guidance for using the ES (Everything Search) command-line interface tool. Everything is a powerful file search utility for Windows that provides instant file search results through real-time indexing.

This skill serves as a complete reference and helper for:
- Learning ES command-line syntax and options
- Performing efficient file searches on Windows
- Understanding advanced filtering and sorting capabilities
- Exporting search results in various formats
- Troubleshooting common ES issues

## ✨ Features

- **Comprehensive Documentation**: Complete reference for all ES commands and options
- **Installation Guides**: Multiple installation methods (winget, scoop, chocolatey, manual)
- **Advanced Search Patterns**: Regex, case-sensitive, whole-word, and path-based searches
- **Export Capabilities**: JSON, CSV, TSV, TXT export options with proper date formatting
- **Sorting & Filtering**: Advanced sorting by name, size, date, extension with custom columns
- **Best Practices**: Optimized workflows for common search scenarios
- **Troubleshooting**: Solutions for common installation and usage issues

## 📋 Prerequisites

- Windows 10/11
- Everything Search application
- ES (Everything CLI) command-line tool

## 🔧 Installation

### Install with Skills CLI (Recommended for AI Agents)

```bash
# Install using npx skills
npx skills add WhizZest/Everything-Search

# This will automatically install the skill to your AI agent's skills directory
# Works with Claude Code, Cursor, GitHub Copilot, and other AI coding agents
```

### Quick Install with Windows Package Manager

```bash
# Install Everything
winget install voidtools.Everything

# Install ES (Everything CLI)
winget install voidtools.Everything.Cli

# Verify installation
es -version
es -get-everything-version
```

### Alternative Installation Methods

<details>
<summary>Scoop</summary>

```bash
scoop install everything
es -version
```

</details>

<details>
<summary>Chocolatey</summary>

```bash
choco install everything
es -version
```

</details>

<details>
<summary>Manual Installation</summary>

1. Download Everything from https://www.voidtools.com/
2. Download ES CLI from https://github.com/voidtools/ES/releases
3. Add ES to your PATH
4. Verify with `es -help`

</details>

## 🎯 Usage Examples

### Basic Search

```bash
# Simple search
es filename

# Search by extension
es *.js
es *.txt

# Limit results
es -n 10 *.log
```

### Advanced Search

```bash
# Case-sensitive whole word search
es -i -w "MyFile"

# Regex search
es -r "test_\d+\.txt"

# Search in specific path
es -path "C:\Users" -name -size -date-modified *.pdf

# Sort by size
es -n 20 -sort size -size -name *.log
```

### Export Results

```bash
# Export to CSV
es -export-csv results.csv *.js

# Export to JSON with readable dates
es -export-json results.json -date-format 1 *.txt

# Export to TSV
es -export-tsv results.tsv *.log
```

### Statistics

```bash
# Get result count
es -get-result-count *.js

# Get total size
es -get-total-size *.log

# Get folder size
es -get-folder-size "C:\path\to\folder"
```

## 📚 Documentation

For complete documentation, see [skills/SKILL.md](skills/SKILL.md) which includes:

- All ES command-line options
- Pattern matching and filtering
- Sorting and display options
- Export formats and date formatting
- Advanced usage examples
- Troubleshooting guide

**Important**: Always run `es -help` before using ES commands to get the most up-to-date information, as the tool is actively maintained.

## 🎨 Common Use Cases

### Find all JavaScript files in a project
```bash
es -n 100 -path "C:\project" -name -size -date-modified *.js
```

### Find recently modified files
```bash
es -n 50 -sort date-modified-descending *
```

### Find large log files
```bash
es -n 20 -sort size-descending -size -name *.log
```

### Export file list for backup
```bash
es -export-csv backup_list.csv -path "C:\important\files" *
```

### Count files by type
```bash
es -get-result-count *.js
es -get-result-count *.py
es -get-result-count *.txt
```

## 🛠️ Configuration

### Date Format for Export

When using `-json`, `-csv`, or other export formats, dates are displayed as FILETIME integers by default. Use `-date-format` to convert to readable format:

```bash
# ISO-8601 (local time) - RECOMMENDED
es -n 2 -json -date-format 1 *.ts

# ISO-8601 (UTC)
es -n 2 -json -date-format 3 *.ts

# ISO-8601 with milliseconds
es -n 2 -json -date-format 5 *.ts
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Related Resources

- [Everything Search Official Site](https://www.voidtools.com/)
- [ES CLI GitHub Repository](https://github.com/voidtools/ES)
- [Everything Documentation](https://www.voidtools.com/support/everything/)

## 🏷️ Topics

- [windows](https://github.com/topics/windows)
- [file-search](https://github.com/topics/file-search)
- [cli](https://github.com/topics/cli)
- [command-line](https://github.com/topics/command-line)
- [search](https://github.com/topics/search)
- [productivity](https://github.com/topics/productivity)
- [skills](https://github.com/topics/skills)
- [everything](https://github.com/topics/everything)
- [es-cli](https://github.com/topics/es-cli)
- [fast-search](https://github.com/topics/fast-search)

## ⭐ Star History

If you find this project helpful, please consider giving it a star! ⭐

---

**Note**: This skill is designed to work with AI assistants and development tools that support skill-based functionality. It provides comprehensive guidance for the ES command-line tool to help users perform efficient file searches on Windows.