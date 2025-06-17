# Fyltr

**Fyltr** is a fast, lightweight, and extensible Data Loss Prevention (DLP) engine written in Rust.  
It scans data streams, files, and structured inputs for sensitive content — such as PII, credentials, secrets, and custom-defined patterns — and enables prevention, alerting, or redaction in real time.

## ✨ Features

- 🔍 High-performance content scanning with pattern matching
- 🔐 Built-in detectors for PII (emails, phone numbers, credit cards, etc.)
- 🧩 Plugin-based architecture for custom detectors
- 🧪 Configurable detection rules via JSON/YAML
- 🧵 Support for multithreaded scanning
- 📁 Input support for text, JSON, CSV, and more
- 🛡️ Redaction or alerting support for identified sensitive data

## 🚀 Getting Started

### Prerequisites

- Rust (version >= 1.70)
- Cargo (comes with Rust)

### Installation

```bash
git clone https://github.com/your-org/fyltr.git
cd fyltr
cargo build --release
````

### Usage

```bash
fyltr scan ./example.txt
```

Or scan from stdin:

```bash
cat file.txt | fyltr scan
```

### Example Output

```json
{
  "file": "example.txt",
  "matches": [
    {
      "type": "email",
      "value": "john.doe@example.com",
      "line": 12
    },
    {
      "type": "credit_card",
      "value": "4111 1111 1111 1111",
      "line": 20
    }
  ]
}
```

## 🔧 Configuration

Fyltr supports detection rule customization through config files.

```yaml
detectors:
  - type: regex
    name: "API Key"
    pattern: "AKIA[0-9A-Z]{16}"
  - type: pii
    enabled: true
```

## 🛠️ Developing

To run tests:

```bash
cargo test
```

To build the CLI with debug logging:

```bash
cargo run -- scan ./test.txt --verbose
```

## 📦 Roadmap

* [ ] Streaming support for large file processing
* [ ] Redaction output modes (e.g., masked, hashed)
* [ ] Integration with S3/GCS/Azure blob stores
* [ ] GUI frontend or web API (optional)

## 🤝 Contributing

Pull requests, issues, and suggestions are welcome!

1. Fork the project
2. Create your feature branch (`git checkout -b feature/my-detector`)
3. Commit your changes (`git commit -am 'Add cool feature'`)
4. Push to the branch (`git push origin feature/my-detector`)
5. Open a pull request

## 📄 License

This project is licensed under the MIT License.

---

**Fyltr** – Catch it before it leaks.
