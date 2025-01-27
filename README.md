# Customer-Support-Agent-Langchain
Customer Support AI Agent system

This code creates an automatic customer support system using langchain, langchain_groq, langgraph and gradio libraries. It is designed to handle customer queries, classify them, analyse their tone and provide appropriate responses. Here are the main components and their functions:

1. Library import and state definition:

The required libraries

are imported:

TypedDict, StateGraph, END, ChatPromptTemplate, MermaidDrawMethod, Image, ChatGroq, gradio.
The state structure State is defined using TypedDict. This structure stores information about the query (query), category (category), sentiment (sentiment) and response (response).
2. Initialising the language model:

An instance of the ChatGroq language model (llm) is created. This requires an API key and a model name. This is where the AuthenticationError occurs, as the provided key is most likely invalid. You need to use the correct key in your working code.
3. Request processing functions (graph nodes):

categorize(state: State): Categorises a customer request into one of three categories: “Technical”, “Billing” or “General”. Uses ChatPromptTemplate to create a language model request.
analyze_sentiment(state: State): Analyses the tone of the request and returns one of the values: "Positive", "Neutral" or "Negative". Also uses ChatPromptTemplate.
handle_technical(state: State): Provides a technical response to the query.
handle_billing(state: State): Provides an answer to billing questions.
handle_general(state: State): Provides a general response to the query.
escalate(state: State): Escalates the query to a human agent if the tone is negative.
route_query(state: State): A routing function that determines which node in the graph should be executed next, based on the category and tone of the query.
4. Creating and customising

the workflow graph:

A workflow graph is created using StateGraph.
Nodes (workflow functions) are added to the graph.
Edges connecting the nodes are added. Add_conditional_edges is used for conditional routing based on the result of the route_query function.
The starting point of the graph is set (set_entry_point).
The graph is compiled into an executable application app.
5. Graph visualisation:

The code tries to visualise the graph using MermaidDrawMethod.API and display it as an image.
6. Client support

run function:

run_customer_support(query: str): A function that accepts a customer query, starts the execution of the graph, and returns a dictionary with category, tone, and response.
7. Creating a GUI using Gradio:

Uses the gradio library to create a simple web interface.
The gradio_interface function accepts a user request and displays the results of run_customer_support in Markdown format.
A Gradio application is created and run.
Key Points:

The code uses langgraph to create a flexible and extensible query processing workflow.
Conditional routing allows requests to be handled differently depending on their category and tone.
Gradio is used to create a simple user interface.
