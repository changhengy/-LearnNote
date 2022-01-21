# 七、Rasa Glossary [Rasa  术语表]

## [Action](https://rasa.com/docs/rasa/actions)[#](https://rasa.com/docs/rasa/glossary#action)

A single step that a bot takes in a conversation (e.g. calling an API or sending a response back to the user).

## [Action Server](https://rasa.com/docs/action-server/)[#](https://rasa.com/docs/rasa/glossary#action-server)

The server that runs custom action code, separate from Rasa Open Source. Rasa maintains the Rasa SDK in Python for implementing custom actions, although it's also possible to write custom actions in other languages.

## Annotation[#](https://rasa.com/docs/rasa/glossary#annotation)

Adding labels to messages and conversations so that they can be used to train a model.

## [Business Logic](https://rasa.com/docs/rasa/business-logic)[#](https://rasa.com/docs/rasa/glossary#business-logic)

Conditions that need to be fulfilled due to business requirements. For example: requiring a first and last name, an address, and a password before an account can be created. In a Rasa assistant, business logic is implemented using rule-based actions like [forms](https://rasa.com/docs/rasa/forms).

## [Chitchat](https://rasa.com/docs/rasa/chitchat-faqs)[#](https://rasa.com/docs/rasa/glossary#chitchat)

A conversation pattern where the user says something that isn't directly related to their goal. This can include things like greetings, asking how you are etc. Read about handling [Chitchat and FAQs](https://rasa.com/docs/rasa/chitchat-faqs) to learn how to implement this with Rasa Open Source.

## CMS[#](https://rasa.com/docs/rasa/glossary#cms)

A way to store bot responses externally instead of including them directly in the domain. Content Management Systems decouple response text from training data. For more information, see [NLG Servers](https://rasa.com/docs/rasa/nlg).

## [Conversation-Driven Development (CDD)](https://rasa.com/docs/rasa/conversation-driven-development)[#](https://rasa.com/docs/rasa/glossary#conversation-driven-development-cdd)

The process of using user messages and conversation data to influence the design of an assistant and train the model, combined with engineering best practices. There are 6 steps that make up CDD: Share, Review, Annotate, Fix, Track, and Test.

## [Conversation Tests](https://rasa.com/docs/rasa/testing-your-assistant)[#](https://rasa.com/docs/rasa/glossary#conversation-tests)

Modified story format that includes the full text of the user message in addition to the intent label. Test conversations are saved to a test set file (conversation_tests.md), which is used to evaluate the model’s predictions across an entire conversation.

## [Component](https://rasa.com/docs/rasa/components)[#](https://rasa.com/docs/rasa/glossary#component)

An element in the an assistant's [NLU pipeline](https://rasa.com/docs/rasa/tuning-your-model#how-to-choose-a-pipeline) in the [Model Configuration](https://rasa.com/docs/rasa/model-configuration).

Incoming messages are processed by a sequence of components called a pipeline. A component can perform tasks ranging from entity extraction to intent classification to pre-processing.

## [Conditional Response Variation](https://rasa.com/docs/rasa/responses#conditional-response-variations)[#](https://rasa.com/docs/rasa/glossary#conditional-response-variation)

Response variation that can only be used when the current dialogue state satisfies some constraints as defined in the domain or responses files. If there's a match between the constraints and the dialogue state, Rasa can use this variation.

## [Custom Action](https://rasa.com/docs/rasa/actions#custom-actions)[#](https://rasa.com/docs/rasa/glossary#custom-action)

An action written by a bot developer that can run arbitrary code, mainly to interact with external systems and APIs.

## [Default Action](https://rasa.com/docs/rasa/actions#default-actions)[#](https://rasa.com/docs/rasa/glossary#default-action)

A built-in action that comes with predefined functionality.

## [DIET](https://rasa.com/docs/rasa/components#dietclassifier)[#](https://rasa.com/docs/rasa/glossary#diet)

Dual Intent and Entity Transformer. The default NLU architecture used by Rasa Open Source, which performs both intent classification and entity extraction.

## [Domain](https://rasa.com/docs/rasa/domain)[#](https://rasa.com/docs/rasa/glossary#domain)

Defines the inputs and outputs of an assistant.

It includes a list of all the intents, entities, slots, actions, and forms that the assistant knows about.

## [Entity](https://rasa.com/docs/rasa/training-data-format#entities)[#](https://rasa.com/docs/rasa/glossary#entity)

Keywords that can be extracted from a user message. For example: a telephone number, a person's name, a location, the name of a product

## [Event](https://rasa.com/docs/action-server/events)[#](https://rasa.com/docs/rasa/glossary#event)

Something that happens in a conversation. For instance, a `UserUttered` event represents a user entering a message, and an `ActionExecuted` event represents the assistant executing an action. All conversations in Rasa are represented as a sequence of events.

## FAQs[#](https://rasa.com/docs/rasa/glossary#faqs)

Frequently asked questions (FAQs) are common questions that your users ask. In the context of building an assistant, this typically means the user sends a message and the assistant send a response without needing to consider the context of the conversation. Read about handling [Chitchat and FAQs](https://rasa.com/docs/rasa/chitchat-faqs) to learn how to implement this with Rasa Open Source.

## [Form](https://rasa.com/docs/rasa/forms)[#](https://rasa.com/docs/rasa/glossary#form)

A type of custom action that asks the user for multiple pieces of information.

For example, if you need a city, a cuisine, and a price range to recommend a restaurant, you can create a restaurant form to collect the information. You can describe [business logic](https://rasa.com/docs/rasa/glossary#business-logic) inside a form, like offering the customer a different set of menu options if they mention a food allergy.

## Happy / Unhappy Paths[#](https://rasa.com/docs/rasa/glossary#happy--unhappy-paths)

Terms used to describe whether the user’s input is expected or unexpected. If your assistant asks a user for some information and the user provides it, we call that a happy path. Unhappy paths are all possible edge cases. For example, the user refusing to give the requested input, changing the topic of conversation, or correcting something they said earlier.

## [Intent](https://rasa.com/docs/rasa/nlu-training-data)[#](https://rasa.com/docs/rasa/glossary#intent)

In a given user message, the thing that a user is trying to convey or accomplish (e,g., greeting, specifying a location).

## [Interactive Learning](https://rasa.com/docs/rasa/writing-stories#using-interactive-learning)[#](https://rasa.com/docs/rasa/glossary#interactive-learning)

In Rasa X or the Rasa CLI, a training mode where the developer corrects and validates the assistant’s predictions at every step of the conversation. The conversation can be saved to the story format and added to the assistant’s training data.

## [Knowledge Base / Knowledge Graph](https://rasa.com/docs/action-server/knowledge-bases)[#](https://rasa.com/docs/rasa/glossary#knowledge-base--knowledge-graph)

A queryable database that represents complex relationships and hierarchies between objects. Knowledge Base Actions allow Rasa Open Source to fetch information from a knowledge base and use it in responses.

## [Level 3 Assistant](https://blog.rasa.com/5-levels-of-conversational-ai-2020-update/)[#](https://rasa.com/docs/rasa/glossary#level-3-assistant)

An assistant that can handle conversations more complex than simple back-and-forth exchanges. Level 3 assistants are capable of using the context of previous conversation turns to choose the appropriate next action.

## [Messaging Channels](https://rasa.com/docs/rasa/messaging-and-voice-channels)[#](https://rasa.com/docs/rasa/glossary#messaging-channels)

Connectors that integrate Rasa Open Source with external messaging platforms, where end-users can send and receive messages. Rasa Open Source includes built-in messaging channels like Slack, Facebook Messenger, and web chat, as well as the ability to create custom connectors.

## [Minimum Viable Assistant](https://rasa.com/docs/rasa/conversation-driven-development#cdd-in-early-stages-of-development)[#](https://rasa.com/docs/rasa/glossary#minimum-viable-assistant)

A basic assistant that can handle the most important happy path stories.

## [NLG](https://rasa.com/docs/rasa/nlg)[#](https://rasa.com/docs/rasa/glossary#nlg)

Natural Language Generation (NLG) is the process of generating natural language messages to send to a user.

Rasa uses a simple template-based approach for NLG. Data-driven approaches (such as neural NLG) can be implemented by creating a custom NLG component.

## [NLU](https://rasa.com/docs/rasa/nlu-training-data)[#](https://rasa.com/docs/rasa/glossary#nlu)

Natural Language Understanding (NLU) deals with parsing and understanding human language into a structured format.

## [NLU Inbox](https://rasa.com/docs/rasa-x/user-guide/annotate-nlu-examples)[#](https://rasa.com/docs/rasa/glossary#nlu-inbox)

The area within Rasa X where new user messages are collected for review and annotation. Only messages not already represented in the training data will appear in the NLU Inbox.

## [Pipeline](https://rasa.com/docs/rasa/tuning-your-model)[#](https://rasa.com/docs/rasa/glossary#pipeline)

The list of NLU components (see [NLU Component](https://rasa.com/docs/rasa/glossary#nlu-component)) that defines a Rasa assistant’s NLU system. A user message is processed by each component one by one, before returning the final structured output.

## [Policy](https://rasa.com/docs/rasa/policies)[#](https://rasa.com/docs/rasa/glossary#policy)

Rasa Open Source components that predict the dialogue system’s next actionPolicies make decisions about how the conversation flow should proceed. A typical configuration includes multiple policies, and the policy with the highest confidence decides the next action to be taken in the conversation.

## Rasa Core[#](https://rasa.com/docs/rasa/glossary#rasa-core)

(Outdated - Rasa Core and Rasa NLU were merged into one package in 1.x. The functionality of Core is now referred to as dialogue management)

The dialogue engine that decides what to do next in a conversation based on the context. Part of the Rasa Open Source library.

## Rasa NLU[#](https://rasa.com/docs/rasa/glossary#rasa-nlu)

(Outdated - Rasa Core and Rasa NLU were merged into one package in 1.x. The functionality of Rasa NLU is now referred to as NLU)

Rasa NLU is the part of Rasa Open Source that performs Natural Language Understanding ([NLU](https://rasa.com/docs/rasa/glossary#nlu)), including intent classification and entity extraction.

## [NLU Component](https://rasa.com/docs/rasa/components)[#](https://rasa.com/docs/rasa/glossary#nlu-component)

An element in the Rasa NLU pipeline (see [Pipeline](https://rasa.com/docs/rasa/glossary#pipeline)) that processes incoming messages. Components perform tasks ranging from entity extraction to intent classification to pre-processing.

## [Rasa X](https://rasa.com/docs/rasa-x/)[#](https://rasa.com/docs/rasa/glossary#rasa-x)

A tool for [conversation-driven development](https://rasa.com/docs/rasa/conversation-driven-development). Rasa X helps teams share and test an assistant built with Rasa Open Source, annotate user messages, and view conversations.

## [Retrieval Intent](https://rasa.com/docs/rasa/chitchat-faqs)[#](https://rasa.com/docs/rasa/glossary#retrieval-intent)

A special type of intent that can be divided into smaller sub-intents. For example, an FAQ retrieval intent has sub-intents that represent each individual question the assistant knows how to answer.

## [REST Channel](https://rasa.com/docs/rasa/connectors/your-own-website)[#](https://rasa.com/docs/rasa/glossary#rest-channel)

A messaging channel used to build custom connectors. Includes an input channel, where user messages can be posted to Rasa Open Source, and the ability to specify a callback URL, where the bot’s response actions will be sent.

## [Response / Template / Utterance](https://rasa.com/docs/rasa/responses)[#](https://rasa.com/docs/rasa/glossary#response--template--utterance)

A message that an assistant sends to a user. This can include text, buttons, images, and other content.

## [Rules](https://rasa.com/docs/rasa/rules)[#](https://rasa.com/docs/rasa/glossary#rules)

Special training data to specify rule-like behavior, where a specific condition always predicts a specific next action. Examples include answering FAQs, filling [Forms](https://rasa.com/docs/rasa/forms), or handling [Fallbacks](https://rasa.com/docs/rasa/fallback-handoff#fallbacks).

## [Share Your Bot](https://rasa.com/docs/rasa-x/user-guide/share-assistant)[#](https://rasa.com/docs/rasa/glossary#share-your-bot)

Rasa X feature that generates a link to a chat UI for test users. **Share your bot** allows test users to talk to an assistant while it’s still in development.

## [Slot](https://rasa.com/docs/rasa/domain#slots)[#](https://rasa.com/docs/rasa/glossary#slot)

A key-value store that Rasa uses to track information over the course of a conversation.

## [Story](https://rasa.com/docs/rasa/stories)[#](https://rasa.com/docs/rasa/glossary#story)

Training data format for the dialogue model, consisting of a conversation between a user and a bot. The user's messages are represented as annotated intents and entities, and the bot’s responses are represented as a sequence of actions.

## [Talk to Your Bot](https://rasa.com/docs/rasa-x/user-guide/share-assistant#talk-to-your-bot)[#](https://rasa.com/docs/rasa/glossary#talk-to-your-bot)

Chat interface within Rasa X that allows bot developers to talk to, test, and correct their assistant. Can be enabled in strict Interactive Learning mode, which requires each prediction to be confirmed before the conversation can proceed.

## [TED Policy](https://rasa.com/docs/rasa/policies#ted-policy)[#](https://rasa.com/docs/rasa/glossary#ted-policy)

Transformer Embedding Dialogue Policy. TED is the default machine learning-based dialogue policy used by Rasa Open Source. TED complements rule-based policies by handling previously unseen situations, where no rule exists to determine the next action.

## [Template / Response / Utterance](https://rasa.com/docs/rasa/responses)[#](https://rasa.com/docs/rasa/glossary#template--response--utterance)

A message template used to respond to a user. Can include text, buttons, images, and other attachments.

## [Tracker](https://rasa.com/docs/rasa/tracker-stores)[#](https://rasa.com/docs/rasa/glossary#tracker)

Rasa Open Source component that maintains the state of the dialogue, which is represented as a JSON object listing the events from the current session.

## User Goal[#](https://rasa.com/docs/rasa/glossary#user-goal)

The overall goal that a user wants to achieve, e.g. looking up the answer to a question, booking an appointment, or purchasing an insurance policy.

Some tools refer to the user goal as the “intent,” but in Rasa terminology, an intent is associated with each individual user message.

## Word embedding / Word vector[#](https://rasa.com/docs/rasa/glossary#word-embedding--word-vector)

A vector of floating point numbers that represent the meaning of a word. Words that have similar meanings tend to have similar vectors. Word embeddings are often used as an input to machine learning algorithms.