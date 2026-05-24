# AITools for learning

## Custom Agents

### Pattern Recognizer

A specialized agent that scans your entire codebase and identifies common coding patterns, code duplication, design patterns, and architectural insights.

#### How to Use

1. **Open VS Code** in your AITools workspace
2. **Open the Chat** (Copilot Chat)
3. **Type `/`** to see available commands
4. **Select "Pattern Recognizer"** from the agent list
5. **Describe what you want to analyze** or simply ask it to scan the codebase

#### What It Does

- 🔍 **Identifies Patterns** - Finds recurring code structures and idioms
- 🔄 **Finds Duplications** - Locates repeated code that could be consolidated
- 🏗️ **Analyzes Architecture** - Understands component interactions and design patterns
- 💡 **Suggests Refactoring** - Recommends improvements and opportunities
- 📊 **Generates Reports** - Provides structured insights on code patterns

#### Example Queries

- "Scan the codebase and identify patterns"
- "Find code duplication in this project"
- "What design patterns are being used here?"
- "Show me refactoring opportunities"
- "Analyze the architecture and identify patterns"

#### Output

The agent provides structured reports including:
- **Pattern Type** - Category of pattern (Design Pattern, Duplication, Convention, etc.)
- **Location** - Files and line numbers affected
- **Description** - What the pattern is
- **Suggestion** - Optional refactoring recommendations
- **Frequency** - How many times it appears

---

### Class Diagram Maintainer

A specialized agent that scans your Java codebase for all classes, interfaces, and their relationships, then automatically generates and maintains a Mermaid class diagram.

#### How to Use

1. **Update Diagram Manually**
   - Open Copilot Chat
   - Type `/` and select "Class Diagram Maintainer"
   - Ask: "Update the class diagram" or "Generate a class diagram for my Java code"

2. **Watch for Changes**
   - Ask: "Watch for new classes and suggest diagram updates"
   - Agent will monitor for changes and suggest updates

#### What It Does

- 🔍 **Scans Java Files** - Finds all classes, interfaces, and enums
- 🔗 **Maps Relationships** - Identifies inheritance and implementation relationships
- 📊 **Generates Diagram** - Creates a Mermaid class diagram
- 📝 **Updates README** - Automatically inserts/updates the diagram section
- ⏰ **Tracks Changes** - Can watch for new classes and suggest updates

#### Example Queries

- "Generate a class diagram for this Java project"
- "Update the class diagram with new classes"
- "Show me the architecture in a class diagram"
- "Watch for new Java classes and update the diagram"
- "Add a class diagram to README.md"

#### Output

Mermaid class diagram showing:
- **Class Definitions** - Names and visibility
- **Relationships** - Inheritance (extends), implementations (implements)
- **Key Methods** - Important public methods
- **Key Properties** - Important attributes
- **Update Timestamp** - When the diagram was last updated

---

## Class Diagram

_The class diagram will be automatically generated here by the Class Diagram Maintainer agent when you run it for the first time._

---

## Prompts

### Job Seeker Tracker

A comprehensive Spring Boot application template for job seekers to track their job application journey.

**What's Included:**
- 📋 Complete data model (JobApplication, Interview, Outcome entities)
- 🔌 RESTful API endpoints for all operations
- 📊 Statistics and analytics endpoints
- 🏗️ Recommended project structure
- ✅ Setup instructions
- 🧪 Testing strategy
- 🚀 Future enhancement ideas

**Features Covered:**
- Track job positions applied for
- Schedule and manage interviews
- Record interview prep notes and impressions
- Log interview outcomes (accepted, rejected, pending)
- Filter and search applications
- View application statistics and success rates

**Technology Stack:**
- Spring Boot 3.x
- Java 17+
- PostgreSQL/MySQL
- RESTful API
- Spring Data JPA

**How to Use:**
1. Open Copilot Chat
2. Type `/job-seeker-tracker` or search for "Job Seeker Tracker"
3. Select the prompt and ask for help scaffolding the project
4. Use it as a reference for building your Spring Boot application 
