# Claude AI Best Practices

> **Critical instructions for Claude AI to prevent recurring failures based on analysis of 96 real documented errors**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

## 🎯 What is this?

This repository contains a comprehensive set of mandatory instructions for Claude AI, developed after analyzing **96 documented failures** across real-world usage. These instructions address **20 recurring error patterns** that cause the most problems in production environments.

## 📊 Background

After 6+ months of intensive Claude AI usage across multiple projects (cybersecurity consulting, automation systems, web development), we documented every significant failure. The analysis revealed:

- **96 serious errors** across diverse use cases
- **20 recurring patterns** that accounted for 80%+ of failures
- **Most common issue:** Assuming without verification (~40 instances)
- **Most critical issue:** Data destruction without permission (2 severe cases)

This document is the result of that empirical analysis.

## 🔍 What Makes This Different?

Unlike generic Claude AI guidelines, this document:

- ✅ **Empirically validated** - Based on real failures, not theory
- ✅ **Prevention-focused** - Stops problems before they happen
- ✅ **Actionable** - Concrete workflows and examples
- ✅ **Comprehensive** - Covers code, databases, security, diagnostics, communication
- ✅ **Evidence-based** - Requires proof, not assumptions
- ✅ **Multi-platform** - Linux, macOS, Windows support

## 📋 What's Covered

### Critical Areas

1. **🔍 Current Best Practices** - Mandatory web search before implementation
2. **📚 Skills Reading** - Document creation best practices
3. **📋 Pre-flight Checks** - Verification before any action
4. **💾 Backup Procedures** - Standardized backup workflows
5. **🚫 Permission Requirements** - What requires explicit approval
6. **🔧 Code Validation** - Credentials, rate limits, testing
7. **🩺 Diagnostics** - Complete logs, evidence-based testing
8. **🗃️ Database Safety** - Backup, testing, rollback strategies
9. **🌐 Web & SEO** - Cross-browser validation, best practices
10. **🔒 Security** - Firewall, fail2ban, IP management
11. **📊 Real Validation** - Evidence requirements
12. **🎯 Mandatory Workflow** - 0-6 step process
13. **💬 Precise Communication** - Eliminating ambiguity
14. **🏭 Production vs Dev** - Critical differentiation
15. **✅ Confirmation Checklist** - 11-point pre-work verification

### Top 5 Most Common Errors Addressed

1. **Assuming without verification** (~40 cases) - Now requires explicit verification
2. **Not reading complete files** (8+ cases) - Mandatory complete file reading
3. **MCP Server instability** (10+ cases) - Documented workarounds
4. **Erroneous diagnosis** (7+ cases) - Requires complete logs + evidence
5. **Directionless iterations** (6+ cases) - Stop and analyze after 3 failures

## 🚀 Quick Start

### Option 1: Automatic Enforcement (Recommended)

**Want Claude to automatically follow these rules? Install our MCP connector:**

```bash
npx @optimaquantum/claude-critical-rules-mcp
```

Add to your `claude_desktop_config.json`:

**macOS:** `~/Library/Application\ Support/Claude/claude_desktop_config.json`  
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "critical-rules": {
      "command": "npx",
      "args": ["-y", "@optimaquantum/claude-critical-rules-mcp"]
    }
  }
}
```

**Features:**
- ✅ Rules always available to Claude
- ✅ Compliance verification tool
- ✅ Works in Claude Desktop & Code
- ✅ Auto-updates

📦 **[View MCP Connector Repository →](https://github.com/optimaquantum/claude-critical-rules-mcp)**

---

### Option 2: Manual Usage

1. **Copy the instructions:** Use [`CRITICAL-RULES.md`](CRITICAL-RULES.md) (English) or [`REGLAS-CRITICAS.md`](REGLAS-CRITICAS.md) (Spanish)

2. **Add to your project:** Place at root or reference in system prompts

3. **Tell Claude:** "Read CRITICAL-RULES.md and confirm you understand all sections before we begin"

### For API Integration

```python
# Load instructions into system prompt
with open('CRITICAL-RULES.md', 'r') as f:
    critical_rules = f.read()

messages = [
    {
        "role": "system", 
        "content": critical_rules
    },
    {
        "role": "user",
        "content": "Your task here..."
    }
]
```

### For Claude Projects (claude.ai)

1. Create a new Project
2. Add `CRITICAL-RULES.md` to Project Knowledge
3. Reference in Custom Instructions: "Always follow guidelines in CRITICAL-RULES.md"

## 📚 Documentation

- **[CRITICAL-RULES.md](CRITICAL-RULES.md)** - Complete English version (636 lines)
- **[REGLAS-CRITICAS.md](REGLAS-CRITICAS.md)** - Complete Spanish version (636 lines)
- **[examples/](examples/)** - Implementation examples (coming soon)
- **[templates/](templates/)** - Pre-flight checklists (coming soon)

## 🎓 Key Principles

### 1. Verify, Don't Assume
```
❌ BAD: "The file probably exists at /path/file"
✅ GOOD: "Checking if file exists... [runs ls -la /path/file] ... File confirmed"
```

### 2. Evidence-Based Testing
```
❌ BAD: "The service should work now"
✅ GOOD: "Service verified working. Evidence: systemctl status nginx → active (running) 2min"
```

### 3. Stop on Errors
```
❌ BAD: nginx test failed, but continuing with restart...
✅ GOOD: nginx test failed. ERROR on line 12. How should I proceed?
```

### 4. Complete Context
```
❌ BAD: Reading first 20 lines of 500-line config file
✅ GOOD: Reading complete file (500 lines) before making changes
```

### 5. Mandatory Backups
```
✅ ALWAYS: cp file.conf file.conf.backup_$(date +%Y%m%d_%H%M%S)
```

## 💡 Use Cases

### Cybersecurity Consulting
- Server hardening procedures
- Firewall configuration
- Security audit workflows
- Incident response protocols

### Web Development
- Multi-environment deployments (dev/staging/prod)
- Database migrations
- SEO optimization
- Performance monitoring

### Automation Systems
- API integrations with rate limits
- Data processing pipelines
- Scheduled task management
- Error handling and recovery

### System Administration
- Configuration management
- Service monitoring
- Log analysis
- Disaster recovery

## 📈 Expected Impact

Based on our analysis, following these guidelines can:

- **Reduce failures by 70-80%** (eliminates most common patterns)
- **Decrease debugging time by 50%** (better diagnostics + evidence)
- **Prevent data loss** (mandatory backups + permission checks)
- **Improve code quality** (validation requirements + best practices search)
- **Accelerate development** (clear workflows + error prevention)

## 🤝 Contributing

We welcome contributions! If you've documented Claude AI failures not covered here:

1. Fork the repository
2. Add your case study to `examples/failures/`
3. Propose rule additions/modifications
4. Submit a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 📊 Statistics

- **96** documented errors analyzed
- **20** recurring patterns identified
- **6+** months of real-world usage
- **4** different environments (cybersecurity, web dev, automation, sysadmin)
- **3** platforms supported (Linux, macOS, Windows)
- **636** lines of actionable guidance

## 🏢 About

Created by [Optima Quantum Services](https://optimaquantum.com) - Cybersecurity and AI consulting firm based in Dubai, UAE.

### Author

**Cesco** - Technical Director
- 15+ years cybersecurity & system administration
- Extensive Claude AI usage across enterprise projects
- Focus: Preventing AI-induced failures in production

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- **Website:** [optimaquantum.com](https://optimaquantum.com)
- **Blog Post:** [How We Spent €200/Month Testing Claude AI](https://optimaquantum.com/blog/claude-ai-failures-analysis) (coming soon)
- **Related Tools:** [WhatsIA.io](https://whatsia.io) - WhatsApp AI automation
- **Support:** [support@optimaquantum.com](mailto:support@optimaquantum.com)

## ⭐ Star This Repo

If these guidelines helped prevent failures in your projects, please star this repo to help others discover it!

## 🙏 Acknowledgments

- Anthropic for Claude AI
- The broader AI community for feedback and testing
- All the production incidents that taught us these lessons 😅

---

**Made with 🔒 by [Optima Quantum Services](https://optimaquantum.com)**

*Preventing AI failures since 2024*
