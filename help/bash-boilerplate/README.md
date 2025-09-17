# Bash script boilerplate

Boilerplate for starting bash scripts. 

## Code

```bash
#!/usr/bin/env bash
# -*- coding: utf-8 -*-
# shellcheck disable=SC2155,SC2312
#
# Script:    myscript.sh
# Purpose:   Short description of what this script does.
# Usage:     myscript.sh [-h] [-v] [-n] -i <input> [-o <output>]
# Example:   myscript.sh -v -i data.txt -o out.bin
# Requires:  bash >= 4, coreutils

set -Eeuo pipefail
IFS=$'\n\t'

# --------------- config (edit me) ----------------
VERSION="0.1.0"
REQ_CMDS=(awk sed grep mktemp)
# -------------------------------------------------

# Colors (auto-disabled if not a tty)
if [[ -t 1 ]]; then
  BOLD=$'\e[1m'; RED=$'\e[31m'; YELLOW=$'\e[33m'; BLUE=$'\e[34m'; RESET=$'\e[0m'
else
  BOLD=""; RED=""; YELLOW=""; BLUE=""; RESET=""
fi

# Logging helpers
log()  { printf '%s\n' "$*"; }
info() { printf '%sINFO:%s %s\n'   "$BLUE"   "$RESET" "$*"; }
warn() { printf '%sWARN:%s %s\n'   "$YELLOW" "$RESET" "$*" >&2; }
err()  { printf '%sERROR:%s %s\n'  "$RED"    "$RESET" "$*" >&2; }
die()  { err "$*"; exit 1; }

# Cleanup (runs on EXIT)
_tmp_dir=""
cleanup() {
  local ec=$?
  [[ -n "${_tmp_dir:-}" && -d "$_tmp_dir" ]] && rm -rf -- "$_tmp_dir"
  exit "$ec"
}
trap cleanup EXIT

# Better error messages (runs on ERR)
on_err() {
  local ec=$? line=${BASH_LINENO[0]} cmd=${BASH_COMMAND}
  err "Command failed (exit $ec) at line $line: ${BOLD}${cmd}${RESET}"
}
trap on_err ERR

usage() {
  cat <<EOF
${BOLD}Usage:${RESET} $(basename "$0") [options]

Options:
  -i FILE   Input file (required)
  -o FILE   Output file (default: stdout)
  -n        Dry-run (show actions, don't change anything)
  -v        Verbose logging
  -h        Show this help and exit
  --version Print version and exit

Examples:
  $(basename "$0") -i in.txt -o out.bin
EOF
}

version() { echo "$(basename "$0") v$VERSION"; }

check_deps() {
  for c in "${REQ_CMDS[@]}"; do
    command -v "$c" >/dev/null 2>&1 || die "Missing required command: $c"
  done
}

# Globals set by flags
INPUT=""
OUTPUT=""
DRYRUN=0
VERBOSE=0

# Parse args (short flags via getopts; handle --version manually)
if [[ "${1:-}" == "--version" ]]; then version; exit 0; fi
while getopts ":i:o:nvh" opt; do
  case "$opt" in
    i) INPUT=$OPTARG ;;
    o) OUTPUT=$OPTARG ;;
    n) DRYRUN=1 ;;
    v) VERBOSE=1 ;;
    h) usage; exit 0 ;;
    \?) die "Unknown option: -$OPTARG";;
    :)  die "Option -$OPTARG requires an argument";;
  esac
done
shift $((OPTIND - 1))

# Validate args
[[ -z "$INPUT"  ]] && { usage; die "Missing required -i FILE"; }
[[ ! -r "$INPUT" ]] && die "Input not readable: $INPUT"

# Prepare environment
check_deps
_tmp_dir="$(mktemp -d -t "$(basename "$0")".XXXXXX)"
[[ $VERBOSE -eq 1 ]] && info "Temp dir: $_tmp_dir"

# Helper to run commands respecting dry-run
run() {
  [[ $VERBOSE -eq 1 ]] && info "RUN: $*"
  if [[ $DRYRUN -eq 1 ]]; then
    printf '[dry-run] %s\n' "$*"
  else
    eval "$@"
  fi
}

main() {
  info "Starting $(basename "$0")"
  [[ $VERBOSE -eq 1 ]] && set -x

  # ---- your logic here ----
  # Example: transform input to output (or stdout)
  if [[ -n "${OUTPUT:-}" ]]; then
    run "awk '{print NR \":\" \$0}' \"$INPUT\" > \"$OUTPUT\""
    info "Wrote: $OUTPUT"
  else
    run "awk '{print NR \":\" \$0}' \"$INPUT\""
  fi
  # -------------------------

  info "Done."
}

main "$@"
```
