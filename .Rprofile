# Configure reticulate to use the project's Python virtual environment
# Cross-platform: handles both Windows and Unix paths
if (.Platform$OS.type == "windows") {
  python_path <- file.path(getwd(), ".venv", "Scripts", "python.exe")
} else {
  python_path <- file.path(getwd(), ".venv", "bin", "python")
}
Sys.setenv(RETICULATE_PYTHON = python_path)
