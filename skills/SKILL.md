---
name: "everything-search"
description: "Provides comprehensive guidance for using ES (Everything Search) command-line tool. Invoke when user asks about file searching, needs help with es commands, or wants to search files efficiently using Everything."
---

# Everything Search Command Helper

This skill provides comprehensive guidance for using the ES (Everything Search) command-line interface tool.

## IMPORTANT: Always Use -help First

**CRITICAL**: Before attempting any ES command, always run `es -help` to get the most up-to-date information. The ES tool is actively maintained and options may change. Using `-help` ensures you have the latest syntax and available options.

```bash
es -help
```

## What is ES?

ES is a command-line interface to Everything, a powerful file search utility for Windows. It provides fast, efficient file searching with advanced filtering and sorting capabilities.

## Installation

### Check if Everything and ES are Installed

Before using ES, verify that Everything and ES are installed:

```bash
# Check Everything version
es -get-everything-version

# Check ES version
es -version

# Check if es command is available
es -help
```

If these commands fail, you need to install Everything and ES.

### Install Everything and ES using Windows Package Manager (winget)

**RECOMMENDED**: Use winget for easy installation on Windows 10/11.

#### Check winget availability:
```bash
winget --version
```

#### Search for Everything and ES:
```bash
winget search Everything
```

Expected results:
- `voidtools.Everything` - Everything (main application)
- `voidtools.Everything.Cli` - ES (Everything CLI)

#### Install Everything:
```bash
winget install voidtools.Everything
```

#### Install ES (Everything CLI):
```bash
winget install voidtools.Everything.Cli
```

**Note**: ES depends on Everything, so installing ES will automatically install Everything if it's not already installed.

#### Verify installation:
```bash
es -version
es -get-everything-version
```

### Install using Scoop

If you use Scoop package manager:

```bash
# Install Everything
scoop install everything

# ES is typically included with Everything
# Verify installation
es -version
```

### Install using Chocolatey

If you use Chocolatey package manager:

```bash
# Install Everything
choco install everything

# ES is typically included with Everything
# Verify installation
es -version
```

### Manual Installation

If package managers are not available, download manually:

1. **Download Everything**:
   - Visit: https://www.voidtools.com/
   - Download the latest version
   - Run the installer

2. **Download ES (Everything CLI)**:
   - Visit: https://github.com/voidtools/ES/releases
   - Download the latest ES-x64.zip
   - Extract to a directory in your PATH (e.g., `C:\Program Files\Everything\ES`)

3. **Add ES to PATH** (if needed):
   - Right-click "This PC" → Properties → Advanced system settings
   - Environment Variables → System variables → Path → Edit
   - Add the ES directory
   - Restart your terminal

### Post-Installation Setup

After installation:

1. **Start Everything**: Launch Everything from Start menu or run `Everything.exe`
2. **Configure Everything**:
   - Let Everything index your files (usually quick)
   - Configure settings as needed (File → Settings)
3. **Verify ES connection**:
   ```bash
   es -help
   ```
   If this works, ES is properly connected to Everything.

### Troubleshooting Installation

#### ES command not found after installation:
- Restart your terminal/command prompt
- Verify ES is in your PATH: `where es`
- Reinstall ES: `winget install voidtools.Everything.Cli --force`

#### Everything not running:
- Start Everything manually from Start menu
- Check if Everything is running in Task Manager
- Configure Everything to start with Windows (Settings → General → Start Everything on system startup)

#### ES cannot connect to Everything:
- Ensure Everything is running
- Restart Everything
- Check Everything settings: Options → General → Allow ES to connect

## Basic Usage

### Simple Search
```bash
es <search-term>
```

### Limit Results
```bash
es -n 10 *.js
es -count 5 package.json
```

### Search by Extension
```bash
es ext:exe;ini
es *.txt
es *.js
```

## Search Options

### Pattern Matching
- `-r <pattern>` or `-regex <pattern>`: Use regular expressions
- `-i` or `-case`: Match case (case-sensitive)
- `-w` or `-whole-word`: Match whole words only
- `-p` or `-match-path`: Match full path
- `-prefix`: Match start of words
- `-suffix`: Match end of words

### Path Filtering
- `-path <path>`: Search in specific path
- `-parent-path <path>`: Search in parent of path
- `-parent <path>`: Search files with specific parent path

### File Type Filtering
- `/ad`: Folders only
- `/a-d`: Files only
- `/a[RHSDAVNTPLCOIEUPM]`: DIR style attributes search
  - R: Read only
  - H: Hidden
  - S: System
  - D: Directory
  - A: Archive
  - Use `-` prefix to exclude: `/a-H` (non-hidden)

## Sorting Options

### Sort by Property
```bash
es -sort name <search-term>
es -sort size <search-term>
es -sort date-modified <search-term>
es -sort extension <search-term>
```

### Sort Order
```bash
es -sort name-ascending <search-term>
es -sort size-descending <search-term>
```

### DIR Style Sorts
- `/on` or `/o-n`: Sort by name (ascending/descending)
- `/os` or `/o-s`: Sort by size (ascending/descending)
- `/oe` or `/o-e`: Sort by extension (ascending/descending)
- `/od` or `/o-d`: Sort by date modified (ascending/descending)

## Display Options

### Show Specific Columns
```bash
es -name -size -extension *.js
es -path-column -date-modified -size *.log
es -full-path-and-name *.txt
```

### Available Columns
- `-name`: File name
- `-path-column`: Path
- `-full-path-and-name`: Full path and name
- `-extension` or `-ext`: File extension
- `-size`: File size
- `-date-created` or `-dc`: Creation date
- `-date-modified` or `-dm`: Modification date
- `-date-accessed` or `-da`: Last access date
- `-attributes`: File attributes
- `-run-count`: Run count
- `-date-run`: Last run date
- `-date-recently-changed` or `-rc`: Recently changed date

### Output Formats
```bash
es -csv *.js
es -json *.txt
es -tsv *.log
es -txt *.ini
```

### Highlighting
```bash
es -highlight *.js
es -highlight-color 0x0a *.js
```

### Date Format (IMPORTANT for JSON/CSV exports)

**CRITICAL**: When using `-json`, `-csv`, or other export formats, dates are displayed as FILETIME integers by default, which are not human-readable. Use `-date-format` to convert to readable format.

```bash
# Default (FILETIME - not readable)
es -n 2 -json *.ts
# Output: "date_modified":133564093868587796

# ISO-8601 (local time) - RECOMMENDED
es -n 2 -json -date-format 1 *.ts
# Output: "date_modified":"2024-04-01T09:43:06"

# ISO-8601 (UTC) - for timezone-aware applications
es -n 2 -json -date-format 3 *.ts
# Output: "date_modified":"2024-04-01T01:43:06Z"

# ISO-8601 with full resolution (milliseconds)
es -n 2 -json -date-format 5 *.ts
# Output: "date_modified":"2024-04-01T09:43:06.8587796"
```

**Available date formats:**
- `0` - auto (automatic selection)
- `1` - ISO-8601 (local time) - **RECOMMENDED**
- `2` - FILETIME (default, not readable)
- `3` - ISO-8601 (UTC) - for timezone-aware applications
- `4` - User Locale (system-specific format)
- `5` - ISO-8601 with full resolution (milliseconds)
- `6` - ISO-8601 (UTC) with full resolution

**Best practice**: Always use `-date-format 1` or `-date-format 3` when exporting to JSON or CSV for human-readable dates.

## Export Options

### Export to File
```bash
es -export-csv results.csv *.js
es -export-json results.json *.txt
es -export-txt results.txt *.log
es -export-tsv results.tsv *.ini
```

### Export Options
- `-no-header`: No column header in CSV/TSV files
- `-no-folder-append-path-separator`: No trailing separator for folders
- `-utf8-bom`: Add UTF-8 BOM to exported file

## Statistics and Information

### Get Result Count
```bash
es -get-result-count *.js
```

### Get Total Size
```bash
es -get-total-size *.log
```

### Get Folder Size
```bash
es -get-folder-size "C:\path\to\folder"
```

### Version Information
```bash
es -version
es -get-everything-version
```

## Advanced Examples

### Search and Sort
```bash
es -n 20 -sort size -size -name *.log
```

### Search in Specific Path with Custom Columns
```bash
es -n 10 -path "C:\Users" -name -size -date-modified *.pdf
```

### Case-Sensitive Whole Word Search
```bash
es -i -w "MyFile"
```

### Regex Search
```bash
es -r "test_\d+\.txt"
```

### Export Large Results
```bash
es -export-json all_files.json *
```

### Search for Folders Only
```bash
es /ad -n 20
```

### Search for Hidden Files
```bash
es /aH -n 10
```

## Everything Control

### Database Operations
```bash
es -save-db
es -reindex
```

### Exit Everything
```bash
es -exit
```

## Best Practices

1. **Always check `-help` first** - ES options may change
2. **Use `-n` to limit results** - Prevent overwhelming output
3. **Specify columns explicitly** - Get only the information you need
4. **Use appropriate output format** - CSV/JSON for programmatic use, default for human reading
5. **Combine filters** - Use path, extension, and attributes together for precise searches
6. **Export for large result sets** - Use `-export-*` options instead of printing to console

## Common Use Cases

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

## Troubleshooting

### No Results Found
- Check if Everything is running
- Verify the search pattern is correct
- Try a broader search term
- Use `-get-result-count` to verify search is working

### Command Not Found
- Ensure ES is installed and in PATH
- Check Everything is installed on your system

### Slow Performance
- Use `-n` to limit results
- Add path filters to narrow search scope
- Consider using `-export-*` for large result sets

## Notes

- Internal `-`'s in options can be omitted: `-nodigitgrouping`
- Switches can start with `/` instead of `-`
- Use double quotes to escape spaces and switches
- Switches can be disabled by prefixing with `no-`: `-no-size`
- Use `^` prefix or wrap with double quotes to escape special characters

## When to Use This Skill

Invoke this skill when:
- User asks about file searching on Windows
- User needs help with es command syntax
- User wants to search files efficiently
- User asks about Everything search tool
- User needs to export file lists
- User wants to find files by specific criteria (size, date, type, etc.)
- User mentions es command or Everything search
