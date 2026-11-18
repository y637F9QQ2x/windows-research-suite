# windows-research-suite

Independent tools for Windows security research with AI agents. Each tool is
its own repository, with its own README, tests and license. This repository
collects them as git submodules, so that one clone gets all of them.

## Tools

| Tool | What it does | License |
|---|---|---|
| [binja-agent-mcp](https://github.com/y637F9QQ2x/binja-agent-mcp) | An MCP (Model Context Protocol) server for Binary Ninja, built for LLM agents. It lets an MCP client find functions, read decompiled code, follow cross-references and calls, query data flow, and add names, types and comments. | GPL-3.0-or-later |
| [windbg-hyperv-mcp](https://github.com/y637F9QQ2x/windbg-hyperv-mcp) | An MCP server for Windows kernel and user-mode debugging of one Hyper-V guest. It uses DbgEng over KDNET or a serial pipe, SSH and SCP into the guest, fixed host tasks for VM control, and optionally Frida, dbgsrv and TTD. | MIT |
| [hyperv-lpe-lab](https://github.com/y637F9QQ2x/hyperv-lpe-lab) | PowerShell scripts for a headless Hyper-V lab in which a Windows local privilege escalation is shown from a standard-user SSH session in the guest. | MIT |
| [win-agent-probes](https://github.com/y637F9QQ2x/win-agent-probes) | Command-line PowerShell probes for Windows security research. Each probe prints one JSON document. | MIT |
| [winremote-session-ext](https://github.com/y637F9QQ2x/winremote-session-ext) | An extension for winremote-mcp, the MCP server that controls a Windows desktop. It adds four read-only tools that report the state of the Windows logon session the server runs in, and it restricts how the server's HTTP endpoint can be exposed. | MIT |

Each README lists the tool's requirements, its security and trust model, and
its limitations. Read it before you install the tool.

## How they fit together

binja-agent-mcp gives an agent access to the static analysis in Binary Ninja.
windbg-hyperv-mcp gives it kernel and user-mode debugging of a Hyper-V guest.
Its VM tools run the host tasks that hyperv-lpe-lab installs, and its guest
tools use the lab's guest SSH setup. In that lab, a proof runs in the guest
from a standard-user SSH session.

win-agent-probes are meant for a lab VM. Each probe prints its result as one
JSON document. Several of them do from a command line what is usually done in
a GUI tool, such as a Process Monitor capture, an RPC trace or a crash dump
triage.

winremote-session-ext adds session tools to winremote-mcp, which controls a
Windows desktop. With them, an agent can check which account, integrity level
and logon session the server runs in, and wait for a window to appear.

## Clone

```powershell
git clone --recursive https://github.com/y637F9QQ2x/windows-research-suite
```

After a clone without `--recursive`, run `git submodule update --init`. Each
submodule is pinned to one commit of the tool's repository. Each tool's
requirements and install steps are in its own README.

## Authorized use

The tools are for authorized security research in your own isolated lab. Use
them only on hosts and virtual machines that you own or are allowed to test.

## Licenses

Every tool keeps its own license, listed in the table above and in the
LICENSE file of its repository. This repository's own files are under the MIT
license. See [LICENSE](LICENSE).

Two tools are modified versions of other projects: binja-agent-mcp of
[Binary Ninja MCP](https://github.com/fosdickio/binary_ninja_mcp) by fosdickio
and CX330Blake, and windbg-hyperv-mcp of
[windbg-mcp](https://github.com/memoryforensics1/windbg-mcp) by
memoryforensics1. winremote-session-ext extends
[winremote-mcp](https://github.com/dddabtc/winremote-mcp) by dddabtc and the
winremote contributors, and contains no upstream files. Each tool's README
gives the full credits.

Binary Ninja is a trademark of Vector 35 Inc. Windows, Hyper-V and WinDbg are
trademarks of Microsoft. This repository is not affiliated with or endorsed
by Vector 35, Microsoft or the upstream authors.

## Author

Kazuma Matsumoto ([y637F9QQ2x](https://github.com/y637F9QQ2x)).
Blog: [y637f9qq2x.com](https://y637f9qq2x.com).
