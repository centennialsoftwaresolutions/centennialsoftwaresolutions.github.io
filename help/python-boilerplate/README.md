# Python Boilerplate

Boilerplate to start a Python script for Python versions at or above 3.7.

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
myscript.py

Description:
    Short description of what this script does.

Usage:
    python myscript.py -i input.txt -o output.txt -v

Requirements:
    Python >= 3.7
"""

import argparse
import logging
import os
import sys
from pathlib import Path
from typing import Optional

__version__ = "0.1.0"


# ---------------- Logging ----------------
def setup_logging(verbose: bool = False) -> None:
    """Configure logging format and level."""
    log_level = logging.DEBUG if verbose else logging.INFO
    logging.basicConfig(
        level=log_level,
        format="%(asctime)s [%(levelname)s] %(message)s",
        datefmt="%Y-%m-%d %H:%M:%S",
    )


# ---------------- CLI ----------------
def parse_args() -> argparse.Namespace:
    """Parse command line arguments."""
    parser = argparse.ArgumentParser(
        description="Example Python script boilerplate",
        formatter_class=argparse.ArgumentDefaultsHelpFormatter,
    )
    parser.add_argument("-i", "--input", required=True, help="Input file")
    parser.add_argument("-o", "--output", help="Output file (default: stdout)")
    parser.add_argument("-n", "--dry-run", action="store_true", help="Dry-run mode")
    parser.add_argument("-v", "--verbose", action="store_true", help="Enable verbose logging")
    parser.add_argument("--version", action="version", version=f"%(prog)s {__version__}")
    return parser.parse_args()


# ---------------- Helpers ----------------
def run_task(input_file: Path, output_file: Optional[Path], dry_run: bool = False) -> None:
    """Main processing logic goes here."""
    logging.info("Processing input: %s", input_file)

    if not input_file.exists():
        logging.error("Input file does not exist: %s", input_file)
        sys.exit(1)

    # Example: prefix each line with line numbers
    with input_file.open("r", encoding="utf-8") as fin:
        lines = [f"{idx+1}: {line}" for idx, line in enumerate(fin)]

    if dry_run:
        logging.info("Dry-run enabled, not writing output")
        return

    if output_file:
        with output_file.open("w", encoding="utf-8") as fout:
            fout.writelines(lines)
        logging.info("Wrote output to %s", output_file)
    else:
        sys.stdout.writelines(lines)


# ---------------- Main ----------------
def main() -> None:
    args = parse_args()
    setup_logging(args.verbose)

    input_path = Path(args.input)
    output_path = Path(args.output) if args.output else None

    try:
        run_task(input_path, output_path, dry_run=args.dry_run)
    except Exception as e:
        logging.exception("Unhandled exception: %s", e)
        sys.exit(1)


if __name__ == "__main__":
    main()
```
