# Zexus Language Design 🚀

Welcome to the official design repository for **Zexus** — a simple, powerful, and unified programming language. Our goal is to reimagine software development by solving modern pain points with an intuitive, readable, and highly integrated language.

---

## 🧠 What is Zexus?

Zexus is a new programming language designed from the ground up to be **declarative** and **intent-based**. Instead of writing complex, step-by-step instructions, you describe **what** you want to achieve, and the Zexus compiler handles the **how**.

It aims to make coding feel like a natural conversation with the machine — enabling both beginners and experts to build robust, secure, and complex applications effortlessly.

---

## 🔷 Core Principles

The design of Zexus is guided by four main principles:

- **Natural Language First**  
  Syntax consists of readable words, not cryptic symbols, making code easy to write and understand.

- **Declarative & Intent-Based**  
  Focus on the *what*, not the *how*. Describe your desired end state, and let the language handle the implementation.

- **Context is King**  
  The compiler is smart. It knows if you're writing UI, backend logic, security rules, or data — and adapts automatically.

- **Everything is a Module**  
  Every file, library, and component is a self-contained, pluggable module. This promotes clean and organized codebases.

---

## 🧩 Key Features: Solving Real Pain Points

- **Unified Stack**  
  Define frontend, backend, database, and styling in one language.

- **Verifiable Security**  
  The compiler can mathematically prove that certain bugs and security flaws are impossible.

- **Fearless Concurrency**  
  Run tasks in parallel using simple syntax — no threading bugs or boilerplate.

- **Context-Aware State Management**  
  Zexus handles UI/backend data flow automatically.

---

## ⚡ Zexus in Action: Code Examples

### 🌐 Web Development (Frontend + Backend)


# File: login_screen.zx

use backend "./auth_handler.zx"

screen Login:
  background: {
    color: "#1A1A1A"
    accent: "#00FF80"
  }

  initial_state: :loading

  state :loading {
    spinner { design: "looping circle" }
    on "load": wait 2 seconds, then change_state(:form)
  }

  state :form {
    form on "submit" call auth_handler.loginUser:
      input username: ~enter your name
      input password: ~enter your password {
        validation: max_length(4), message: "Password must be 4 characters."
      }
      button "Login"

      on "success" (event): redirect_to(event.redirectURL)
      on "error" (event): display popup(message: event.message)
  }


---



🗃️ Database Definition

# File: main.zxdb

database LocalUsers:
  entity User:
    username: text
    email: email_string
    password: hashed_string(max: 4)

  retention_policy: expires_after 24 hours

  permissions:
    allowed_access_from: "./auth_handler.zx"
    requires_secret: env("DB_ACCESS_KEY")


---



⛓️ Smart Contracts (Blockchain)

# File: zexus_coin.zxc

verifiable entity ZexusCoin:
  public final let totalSupply = 1_000_000
  private let balances: Map<Address, Integer>

  action transfer(from: Address, to: Address, amount: Integer):
    require balances[from] >= amount, message: "Insufficient balance."
    balances[from] -= amount
    balances[to] += amount
    return success()


---



🧠 AI & Data Science

# File: image_classifier.zxai

use "zexus_ai_kit"
let dataset = ai.load_image_dataset(from: "./images")

let model = ai.vision_model {
  layer "convolutional", filters: 32, size: 3
  layer "pooling"
  output "softmax", classes: dataset.class_names
}

action trainModel:
  in parallel: model.train(on: dataset, epochs: 10)


---



🧾 Simple Scripting

# File: count_words.zx

use "filesystem"
let document = filesystem.read_file("./my_document.txt")
let wordCount = document.split(" ").count()
print "The document has {wordCount} words."


---

🧮 Basic Command Reference

Keyword / Concept	Purpose	Example

""" ... """	Multi-line comment or docstring	""" This is my file. """
#	Single-line comment	# This is a comment
use	Import file or library	use "./colors.zx"
let	Declare variable	let appName = "Zexus"
screen	UI container/page	screen Login: ...
state	A state inside a screen	state :loading { ... }
action	A function block	action loginUser(): ...
database	Declare a database	database LocalUsers: ...
entity	Define a data model	entity User { name: text }
if / else	Conditional logic	if user: print "Hi"
for each	Loop through list	for each u in users: print u



---

🧰 Command-Line Tools

To manage and run Zexus projects, use the following tools:

▶️ zx - Zexus Runner

Run .zx files from your terminal.

# Run the main application file
zx main.zx

📦 zpm - Zexus Package Manager

Install and manage Zexus libraries.

# Install a library from the official registry
zpm install CoolUI


---

🤝 How to Contribute

Zexus is in active design and development. We welcome all contributions!

You can:

🗨️ Open an Issue to propose ideas or report problems

🍴 Fork the repo and submit a Pull Request with suggestions or additions

📚 Help refine the language docs and examples


Let’s build the future of programming — together.