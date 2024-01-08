# Nano Bots

![Nano Bot](https://user-images.githubusercontent.com/113217272/237534390-3f0e0dc7-1f92-4490-a12d-bfc9d145cddb.png)
_Image artificially created by Midjourney through a prompt generated by a Nano Bot specialized in Midjourney._

**Nano Bots** is an open specification that can be implemented in any programming language. It specifies a configuration file with human-readable instructions for creating small and specialized AI-powered bots that can be effortlessly shared as a single, lightweight file.

- [Full Specification](https://spec.nbots.io)
- [Implementations](#implementations)
  - [Projects](#projects)
- [Example](#example)

## Implementations

Implementations of this specification:

- [Nano Bots CLI (Ruby)](https://github.com/icebaker/ruby-nano-bots)

### Projects

- [Nano Bots CLI (Ruby)](https://github.com/icebaker/ruby-nano-bots)
- [Nano Bots for Sublime Text](https://github.com/icebaker/sublime-nano-bots)
- [Nano Bots for Visual Studio Code](https://github.com/icebaker/vscode-nano-bots)
- [Nano Bots for Obsidian](https://github.com/icebaker/obsidian-nano-bots)
- [Nano Bots API](https://github.com/icebaker/nano-bots-api)
  - [Public API](https://api.nbots.io)
- [Nano Bots Clinic (Live Editor)](https://clinic.nbots.io)
- [Nano Bots Marketplace](https://nbots.io)

## Example

Here's what a Nano Bot _Cartridge_ looks like:

```yaml
---
meta:
  symbol: 🤖
  name: Nano Bot Name
  author: Your Name
  version: 1.0.0
  license: CC0-1.0
  description: A helpful assistant.

behaviors:
  interaction:
    directive: You are a helpful assistant.

provider:
  id: openai
  credentials:
    address: ENV/OPENAI_API_ADDRESS
    access-token: ENV/OPENAI_API_KEY
  settings:
    user: ENV/NANO_BOTS_END_USER
    model: gpt-4-1106-preview
```

Here's what a fully-functional implementation of Nano Bots feels like:

```bash
nb - - eval "hello"
# => Hello! How may I assist you today?

nb to-en-us-translator.yml - eval "Salut, comment ça va?"
# => Hello, how are you doing?

nb midjourney.yml - eval "happy cyberpunk robot"
# => A cheerful and fun-loving robot is dancing wildly amidst a
#    futuristic and lively cityscape. Holographic advertisements
#    and vibrant neon colors can be seen in the background.

nb lisp.yml - eval "(+ 1 2)"
# => 3

cat article.txt |
  nb to-en-us-translator.yml - eval |
  nb summarizer.yml - eval
# -> LLM stands for Large Language Model, which refers to an
#    artificial intelligence algorithm capable of processing
#    and understanding vast amounts of natural language data,
#    allowing it to generate human-like responses and perform
#    a range of language-related tasks.
```

```bash
nb - - repl

nb assistant.yml - repl
```

```text
🤖> Hi, how are you doing?

As an AI language model, I do not experience emotions but I am functioning
well. How can I assist you?

🤖> |
```

Nano Bots can also be powered by _Tools_ (Functions):

```yaml
---
tools:
  - name: random-number
    description: Generates a random number between 1 and 100.
    fennel: |
      (math.random 1 100)
```

```
🤖> please generate a random number

random-number {} [yN] y

random-number {}
59

The randomly generated number is 59.

🤖> |
```

Check out the full specification for Nano Bots: https://spec.nbots.io
