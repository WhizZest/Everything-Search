# ES Search Usage Examples

This document provides practical examples of using ES (Everything Search) command-line tool for various file search scenarios on Windows.

## Quick Start Examples

### Basic File Search

```bash
# Search for a specific file
es myfile.txt

# Search for files by extension
es *.pdf
es *.jpg
es *.docx

# Search with wildcard
es report*
es *data*
```

### Search with Limits

```bash
# Limit results to 10 files
es -n 10 *.log

# Show only first 5 results
es -count 5 package.json

# Get exact count without showing results
es -get-result-count *.js
```

## Advanced Search Patterns

### Case-Sensitive Search

```bash
# Case-sensitive search
es -i "MyFile"

# Case-sensitive whole word
es -i -w "Important"
```

### Whole Word Search

```bash
# Match whole words only
es -w "test"

# Case-sensitive whole word
es -i -w "Data"
```

### Regular Expression Search

```bash
# Search for pattern
es -r "test_\d+\.txt"

# Search for date patterns
es -r "\d{4}-\d{2}-\d{2}"

# Search for version numbers
es -r "v\d+\.\d+\.\d+"
```

### Path-Based Search

```bash
# Search in specific directory
es -path "C:\Users\Documents" *.pdf

# Search in parent path
es -parent-path "C:\Projects" *.js

# Search with full path matching
es -match-path "C:\Windows\System32"
```

## File Type Filtering

### Search by File Type

```bash
# Folders only
es /ad -n 20

# Files only (exclude folders)
es /a-d -n 50

# Search for hidden files
es /aH -n 10

# Search for system files
es /aS -n 10

# Search for read-only files
es /aR -n 10

# Exclude hidden files
es /a-H -n 20

# Combine attributes
es /a-d /a-H -n 30
```

## Sorting Examples

### Sort by Name

```bash
# Sort by name (ascending)
es -sort name *.log

# Sort by name (descending)
es -sort name-descending *.log

# Alternative syntax
es /on *.log
es /o-n *.log
```

### Sort by Size

```bash
# Find largest files
es -n 20 -sort size-descending -size -name *

# Find smallest files
es -n 20 -sort size -size -name *

# Alternative syntax
es /os *  # size ascending
es /o-s *  # size descending
```

### Sort by Date

```bash
# Most recently modified files
es -n 20 -sort date-modified-descending *

# Oldest files
es -n 20 -sort date-modified *

# Alternative syntax
es /od *  # date ascending
es /o-d *  # date descending
```

### Sort by Extension

```bash
# Group by file type
es -sort extension *

# Alternative syntax
es /oe *
es /o-e *
```

## Display Options

### Custom Columns

```bash
# Show specific columns
es -name -size -extension *.js

# Show path and date
es -path-column -date-modified *.log

# Show full path and name
es -full-path-and-name *.txt

# Multiple columns
es -name -size -date-modified -extension *.pdf
```

### Output Formats

```bash
# CSV format
es -csv *.js

# JSON format (with readable dates)
es -json -date-format 1 *.txt

# TSV format
es -tsv *.log

# Plain text format
es -txt *.ini
```

### Highlighting

```bash
# Highlight matches
es -highlight *.js

# Custom highlight color
es -highlight-color 0x0a *.js
```

## Export Examples

### Export to CSV

```bash
# Export search results to CSV
es -export-csv results.csv *.js

# Export without header
es -export-csv results.csv -no-header *.txt

# Export specific columns
es -export-csv files.csv -name -size -date-modified *.pdf
```

### Export to JSON

```bash
# Export to JSON with readable dates
es -export-json results.json -date-format 1 *.txt

# Export to JSON with UTC dates
es -export-json results.json -date-format 3 *.log

# Export to JSON with milliseconds
es -export-json results.json -date-format 5 *.js
```

### Export to Other Formats

```bash
# Export to TSV
es -export-tsv results.tsv *.log

# Export to plain text
es -export-txt results.txt *.ini

# Export with UTF-8 BOM
es -export-csv results.csv -utf8-bom *.js
```

## Practical Use Cases

### Development Workflow

```bash
# Find all JavaScript files in project
es -n 100 -path "C:\Projects\MyApp" -name -size -date-modified *.js

# Find configuration files
es -n 20 *.config
es -n 20 *.json
es -n 20 *.yaml
es -n 20 *.yml

# Find test files
es -n 50 *.test.js
es -n 50 *.spec.ts
```

### Log File Management

```bash
# Find large log files
es -n 20 -sort size-descending -size -name *.log

# Find recently modified logs
es -n 30 -sort date-modified-descending *.log

# Find logs in specific directory
es -path "C:\Logs" -n 50 *.log

# Export log file list
es -export-csv log_files.csv -path "C:\Logs" -name -size -date-modified *.log
```

### Document Management

```bash
# Find all PDF documents
es -n 100 -sort date-modified-descending *.pdf

# Find Office documents
es -n 50 *.docx
es -n 50 *.xlsx
es -n 50 *.pptx

# Find documents by date range
es -n 30 -sort date-modified *.docx

# Export document inventory
es -export-json documents.json -date-format 1 *.docx *.pdf *.xlsx
```

### System Administration

```bash
# Find system files
es -path "C:\Windows\System32" -n 20 *.dll

# Find executable files
es -n 30 *.exe

# Find configuration files
es -n 20 *.ini
es -n 20 *.cfg

# Find recently created files
es -n 50 -sort date-created *
```

### Backup and Archive

```bash
# Create file list for backup
es -export-csv backup_list.csv -path "C:\Important\Files" *

# Find files modified in last 24 hours
es -n 100 -sort date-modified-descending *

# Get total size of directory
es -get-folder-size "C:\Projects"

# Find large files for cleanup
es -n 30 -sort size-descending -size -name *
```

### Media File Management

```bash
# Find image files
es -n 100 *.jpg
es -n 100 *.png
es -n 100 *.gif

# Find video files
es -n 50 *.mp4
es -n 50 *.avi
es -n 50 *.mkv

# Find audio files
es -n 50 *.mp3
es -n 50 *.wav
es -n 50 *.flac

# Find media by size
es -n 20 -sort size-descending -size -name *.mp4
```

## Statistics and Information

### Get File Counts

```bash
# Count JavaScript files
es -get-result-count *.js

# Count by different extensions
es -get-result-count *.py
es -get-result-count *.txt
es -get-result-count *.log

# Count in specific path
es -path "C:\Projects" -get-result-count *.js
```

### Get Size Information

```bash
# Get total size of matching files
es -get-total-size *.log

# Get folder size
es -get-folder-size "C:\Users\Documents"

# Get size of specific file type
es -get-total-size *.pdf
```

### Version Information

```bash
# Check ES version
es -version

# Check Everything version
es -get-everything-version

# Get help
es -help
```

## Complex Searches

### Multiple Criteria

```bash
# Search with multiple filters
es -n 20 -path "C:\Projects" -sort size-descending -size -name *.js

# Combine attributes and extensions
es /a-d /a-H -n 30 *.txt

# Case-sensitive regex in specific path
es -i -r "test_\d+" -path "C:\Logs" *.log
```

### Chained Operations

```bash
# Find and export
es -export-csv large_files.csv -n 50 -sort size-descending -size -name *

# Search and count
es -path "C:\Projects" -get-result-count *.js

# Find recent files and export
es -export-json recent.json -n 100 -sort date-modified-descending -date-format 1 *
```

## Tips and Tricks

### Performance Optimization

```bash
# Always limit results for large searches
es -n 100 *

# Use path filters to narrow scope
es -path "C:\Specific\Directory" *.log

# Export large result sets instead of printing
es -export-csv large_results.csv *
```

### Date Formatting

```bash
# Always use date-format for exports
es -export-json results.json -date-format 1 *.txt

# Use UTC for timezone-aware applications
es -export-json results.json -date-format 3 *.log

# Use high resolution for precise timestamps
es -export-json results.json -date-format 5 *.js
```

### Pattern Matching

```bash
# Use quotes for special characters
es "file with spaces.txt"

# Escape special characters
es file\(1\).txt

# Use whole word for exact matches
es -w "config"
```

## Troubleshooting Examples

### No Results Found

```bash
# Check if Everything is running
es -get-everything-version

# Try broader search
es *

# Check search pattern
es -help
```

### Command Not Found

```bash
# Verify ES is in PATH
where es

# Check ES version
es -version

# Reinstall if needed
winget install voidtools.Everything.Cli --force
```

### Connection Issues

```bash
# Verify Everything is running
es -get-everything-version

# Restart Everything
es -exit
# Then start Everything manually

# Check Everything settings
# Options → General → Allow ES to connect
```

## Best Practices

1. **Always check `-help` first** - ES options may change
2. **Use `-n` to limit results** - Prevent overwhelming output
3. **Specify columns explicitly** - Get only information you need
4. **Use appropriate output format** - CSV/JSON for programmatic use
5. **Combine filters** - Use path, extension, and attributes together
6. **Export for large result sets** - Use `-export-*` options
7. **Use `-date-format` for exports** - Ensure readable dates
8. **Quote special characters** - Escape spaces and special chars

---

For complete documentation, see [SKILL.md](SKILL.md) or run `es -help` for the most up-to-date information.