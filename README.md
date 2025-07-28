# Zexus Language Design 🚀

Designing Zexus, a simple,powerful and unified programming language 

Welcome to the official design repository for Zexus, a simple, powerful, and unified programming language. Our goal is to reimagine software development by solving modern pain points with an intuitive, readable, and highly integrated language.

What is Zexus?
Zexus is a new programming language designed from the ground up to be declarative and intent-based. Instead of writing complex, step-by-step instructions, you describe what you want to achieve, and the Zexus compiler handles the how. It aims to make coding as close to a natural conversation with the computer as possible, empowering everyone from beginners to seasoned experts to build robust, secure, and complex applications with ease.
Core Principles
The design of Zexus is guided by four main principles:
 * Natural Language First: Syntax consists of readable words, not cryptic symbols, making code easy to write and understand.
 * Declarative & Intent-Based: Focus on the "what," not the "how." Describe your desired end state, and let the language handle the implementation details.
 * Context is King: The compiler is smart. It understands whether you're defining UI, backend logic, security rules, or data, and adapts accordingly.
 * Everything is a Module: Every file, library, and component is a self-contained, pluggable module, promoting clean and organized code.
Key Features (Solving Pain Points)
Zexus directly tackles common frustrations in modern development:
 * Unified Stack: No more juggling five different languages for one app. Define your frontend, backend, database, and styling in one cohesive language.
   
 * Verifiable Security: The language is designed to allow the compiler to mathematically prove that certain classes of bugs and security vulnerabilities are impossible, making your applications secure by default.
   
 * Fearless Concurrency: Write code that runs in parallel on modern multi-core processors using simple keywords, without the complexity and bugs of traditional threading.
   
 * Context-Aware State Management: Zexus automatically handles the flow of data between your UI and your backend, eliminating huge amounts of boilerplate code.
   
# Zexus in Action: Code Examples
Here’s a glimpse of what building with Zexus could look like.
Web Development (Frontend & Backend)
A single file can define a screen with multiple states (loading and form), handle user input, and call a secure backend action.
# File: login_screen.zx

use backend "./auth_handler.zx"

screen Login:
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
  
  ------------------

Database Definition
Define your database schema, retention policies, and access rules in a simple, readable file.
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

   -------------------

Smart Contracts (Blockchain)
Zexus's focus on verifiable security makes it ideal for building safe smart contracts.
# File: zexus_coin.zxc

verifiable entity ZexusCoin:
  public final let totalSupply = 1_000_000
  private let balances: Map<Address, Integer>

  action transfer(from: Address, to: Address, amount: Integer):
    require balances[from] >= amount, message: "Insufficient balance."
    balances[from] -= amount
    balances[to] += amount
    return success()
    
   --------------------

Artificial Intelligence & Data Science
Declaratively define and train complex AI models with ease.
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

 ----------------

Simple Scripting
Automate simple tasks with clear, minimal code.
# File: count_words.zx

use "filesystem"
let document = filesystem.read_file("./my_document.txt")
let wordCount = document.split(" ").count()
print "The document has {wordCount} words."

------------

Basic Command Reference
| Keyword / Concept | Purpose | Example |
|---|---|---|
| """ ... """ | Multi-line comment or file docstring. | """ This is my file. """ |
| # | Single-line comment for notes. | # This is a quick note |
| use | Import another file or an external library. | use "./colors.zx" |
| let | Declare a constant value or variable. | let appName = "Zexus" |
| screen | A UI container, representing a page or view. | screen Login: ... |
| state | Defines a specific state within a screen. | state :loading { ... } |
| action | A function that performs a task. | action loginUser(email, password): ... |
| database | Defines a database schema and its rules. | database LocalUsers: ... |
| entity | Defines the structure of data. | entity User { name: text } |
| if / else | Executes code based on a condition. | if user: print "Welcome" |
| for each | Loops over a list of items. | for each user in allUsers: print user.name |
How to Contribute
This project is in the early design phase. We welcome all ideas and contributions! Feel free to:
 * Open an Issue to discuss a new feature or ask a question.
   
 * Fork the repository and submit a Pull Request with your proposed changes or additions to this document.
Let's build the future of programming together!
