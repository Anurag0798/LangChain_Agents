# LangChain Agents

This repository demonstrates how to build autonomous agents and multi-agent systems using **LangChain**. It covers creating agents that can call tools (functions), interact with databases, and coordinate multiple specialized agents under a supervisor.

## Key Concepts and Objectives

- **Agent Definition:** An agent is an autonomous entity that can perform tasks, make decisions, and invoke tools as needed.
- **LangChain:** A powerful Python library to create LLM-powered agents, manage tools, and orchestrate workflows.
- **Tools:** Python functions wrapped as callable utilities that agents use to accomplish specific tasks (e.g., fetching data, performing calculations).
- **LLMs:** Large Language Models (e.g., OpenAI GPT models) provide reasoning and decision-making capabilities to agents.
- **Prompts:** Instructions guiding agent behavior, roles, and constraints.
- **Multi-Agent Systems:** Multiple specialized agents working collaboratively, coordinated by a supervisor agent.
- **Database Interaction:** Agents accessing and manipulating real-time data from databases such as Neon (PostgreSQL-based).

## Simple Agent Creation

The project begins with building a basic agent to illustrate core concepts:

- Import necessary modules from `os`, `langchain`, `langchain.tools`, `langchain.agents`, and `langchain_core.prompts`.
- Set your **OpenAI API key** as an environment variable.
- Define Python functions to serve as tools:
  - `getCourseSchedule(course_name)`: Returns the schedule for a specified course.
  - `calculateDiscountedPrice(original_price, discount_percentage)`: Calculates the discounted price.
  - `recommendNext(topic)`: Suggests the next learning step based on a topic.
- Decorate these functions with `@tool` to register them as callable tools for the agent.
- Group tools into a list for agent use.
- Create an LLM instance with `ChatOpenAI`, specifying model and temperature.
- Define a prompt instructing the agent’s role and expected behavior.
- Use `create_tool_calling_agent` to build the agent with the LLM, tools, and prompt.
- Wrap the agent in an `AgentExecutor` to run it.
- Test the agent with demo queries using `executor.invoke()`.

## Multi-Agent System with Database Interaction

The project advances to a multi-agent system integrating with a real database:

- Use **Neon DB** (PostgreSQL cloud database) as the data source.
- Setup includes:
  - Creating a Neon DB project and obtaining the connection string.
  - Defining tables: `students`, `courses`, `course_schedule`, `orders`, and `support_tickets`.
  - Inserting sample data via SQL inserts.
- Create multiple specialized agents:
  - **Academic Agent:** Handles course schedules and academic queries.
  - **Support Agent:** Manages payment issues, access problems, and support ticket creation.
  - **Sales Agent:** Provides business insights, top courses, and purchase trend analysis.
- Define specific tools for each agent, such as:
  - `getCourseScheduleDB(course_name)`: Fetches course schedules from the database.
  - `getStudentOrder(email_id)`: Fetches student order details.
  - `listOpenTickets()`: Lists current open support tickets.
  - `createTicket(subject, description, email_id)`: Creates a new support ticket.
  - `getSalesInsight()`: Retrieves sales-related insights.
- Implement a **Supervisor Agent (Agent Zero)**:
  - Acts as a router to delegate user queries to the appropriate specialized agent.
  - Uses tools to invoke the academic, support, or sales agents based on query context.
- Test the multi-agent system with various queries showcasing routing and decision-making.

## Key Takeaways

- Agents automate complex workflows by making decisions and interacting with external tools and databases.
- LangChain provides a flexible and powerful framework to build sophisticated agent-based applications.
- Well-crafted prompts are essential to define agent behavior and ensure accurate task execution.
- Multi-agent systems enable specialization and efficient handling of diverse user requests.
- Integrating agents with live databases extends their capabilities to real-time data access and manipulation.
- The project lays foundation for further enhancements like dynamic SQL query generation and chat interface integration.

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/Anurag0798/LangChain_Agents.git
   
   cd LangChain_Agents
   ```

2. Set your OpenAI API key:

3. Install dependencies as mentioned in the jupyter notebooks

4. Configure your Neon DB instance and update connection strings as needed.

5. Run example scripts or notebooks demonstrating single and multi-agent workflows.

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your improvements.

## License

This project is open-source. See the `LICENSE` file for details.