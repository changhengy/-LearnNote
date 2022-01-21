# 四、Best Practices [最佳实践]

## 1. Conversation-Driven Development [会话驱动开发]

### 1.1 What is CDD?[#](https://rasa.com/docs/rasa/conversation-driven-development#what-is-cdd)

Conversation-Driven Development (CDD) is the process of listening to your users and using those insights to improve your AI assistant. It is the overarching best practice approach for chatbot development.

Developing great AI assistants is challenging because users will always say something you didn't anticipate. The principle behind CDD is that in every conversation users are telling you—in their own words—exactly what they want. By practicing CDD at every stage of bot development, you orient your assistant towards real user language and behavior.

```
对话驱动开发（CDD）是一个倾听用户并使用这些见解来改进人工智能助理的过程。它是聊天机器人开发的总体最佳实践方法。

开发伟大的人工智能助手是具有挑战性的，因为用户总是会说一些你没有预料到的事情。CDD背后的原则是，在每一次对话中，用户都在告诉你--他们自己的话--他们想要什么。通过在机器人开发的每个阶段进行CDD练习，你可以让你的助手面向真实的用户语言和行为。
```

CDD includes the following actions:

- **Share** your assistant with users as soon as possible
- **Review** conversations on a regular basis
- **Annotate** messages and use them as NLU training data
- **Test** that your assistant always behaves as you expect
- **Track** when your assistant fails and measure its performance over time
- **Fix** how your assistant handles unsuccessful conversations

> 1.  尽快与 assistant  **Share** 您的助手
> 2.  经常性地 **Review**  conversations 
> 3. **注释**信息并将其作为NLU训练数据使用
> 4. **测试**你的助手总是按照你的期望行事。
> 5. **跟踪**你的助手何时失败，并衡量其长期的表现
> 6. **修复**你的助手如何处理不成功的对话

CDD is not a linear process; you'll circle back to the same actions over and over as you develop and improve your bot.

Read more about these actions and the concept of CDD on the [Rasa Blog](https://blog.rasa.com/conversation-driven-development-a-better-approach-to-building-ai-assistants/).

You can also check out [Rasa X](https://rasa.com/docs/rasa-x/), a purpose-built tool for CDD.

> CDD不是一个线性过程；当你开发和改进你的机器人时，你会一次又一次地回到相同的行动。

### 1.2 CDD in early stages of development[#](https://rasa.com/docs/rasa/conversation-driven-development#cdd-in-early-stages-of-development)

If you're at the earliest stage of bot development, it might seem like CDD has no role to play - after all, you have no conversations yet! However, there are CDD actions you can take at the very beginning of bot development:

> 如果你处于机器人开发的最早阶段，CDD似乎没有什么作用--毕竟，你还没有对话！然而，在机器人开发的最初阶段，你可以采取一些CDD行动。

1. See the best practices for [NLU data](https://rasa.com/docs/rasa/generating-nlu-data) and [Stories](https://rasa.com/docs/rasa/writing-stories) for details on creating training data with CDD in mind.

2. Give your bot to test users early on.

   CDD is all about listening to your users, so the earlier you find some, the better.

   Test users can be anyone who doesn't already know how your bot works from the inside. People on the bot development team should not be test users, since they know exactly what the bot can and can't do. Don't overinstruct your test users; they should have only as much knowledge of the bot's domain as your end users will have.

3. Set up a CI/CD pipeline.

   CDD leads to frequent, smaller updates to your bot as you gather insights from bot conversations. [Setting up a CI/CD pipeline](https://rasa.com/docs/rasa/setting-up-ci-cd) early on in development will enable you to act quickly on what you see in conversations.

> 1. 参见NLU数据和Stories的最佳实践，以了解在创建训练数据时考虑到CDD的细节。
>
> 2. 尽早把你的机器人交给测试用户。
>
>    CDD是关于倾听你的用户，所以你越早找到一些用户越好。
>
>    测试用户可以是任何还没有从内部了解你的机器人如何工作的人。机器人开发团队的人不应该成为测试用户，因为他们清楚地知道机器人能做什么，不能做什么。不要过度指导你的测试用户；他们对机器人领域的了解应该和你的终端用户一样多。
>
>
> 3. 建立一个CI/CD管道。
>
>    当你从机器人对话中收集洞察力时，CDD会导致对你的机器人进行频繁的、较小的更新。在开发的早期建立一个CI/CD管道将使你能够根据你在对话中看到的东西迅速采取行动。

At this stage, you can install Rasa X in local mode to make it easier to share your bot with test users, collect conversations, and apply NLU and Story best practices based on the conversations you collect.

> 在这个阶段，你可以在本地模式下安装Rasa X，以便更容易与测试用户分享你的机器人，收集对话，并根据你收集的对话应用NLU和Story最佳实践。

### 1.3 CDD with a bot in production[#](https://rasa.com/docs/rasa/conversation-driven-development#cdd-with-a-bot-in-production)

Once your bot is in production, you'll have more conversations to gain insights from. Then you can fully apply CDD actions. At this stage, you can [install Rasa X on a server](https://rasa.com/docs/rasa-x/installation-and-setup/installation-guide/#helm-chart) to both deploy your bot and enable CDD with a bot in production.

> 一旦你的机器人投入生产，你将有更多的对话来获得洞察力。然后你就可以完全应用CDD行动。在这个阶段，你可以在服务器上安装Rasa X，以部署你的机器人，并在生产中启用机器人的CDD。

#### Review[#](https://rasa.com/docs/rasa/conversation-driven-development#review)

Look in conversations for what users are really asking for.

>  **在对话中寻找用户的真正需求。**

Your test users had at least some instruction about what the bot was intended to do; real users often either have no idea, or ignore instructions given to them. You can't cater to every unexpected user behavior, but you can try to address the main friction points you notice. Here are some things you could consider looking for:

- Look at conversations where an “out_of_scope” intent or fallback behavior occurred. These could indicate a potential new skill, or just a misclassified user utterance.

- Look for user frustration, such as requests for transfer to a human.

- If the assistant was trained with [`UnexpecTEDIntentPolicy`](https://rasa.com/docs/rasa/policies#unexpected-intent-policy) included in the pipeline, you can look for conversations where `action_unlikely_intent` is predicted at any conversation turn. An `action_unlikely_intent` is predicted when the last intent expressed by the user is unexpected in the current conversation context. You can also filter out such conversations by running a [standalone script](https://gist.github.com/alwx/b426b7b573ff963c85c65ea6466528d7) which does the following:

  - Fetch real conversations from a tracker store.
  - Run `rasa test` on the fetched conversations and filter conversations containing `action_unlikely_intent` in a separate warnings file. You can read more on [how to interpret these warnings](https://rasa.com/docs/rasa/testing-your-assistant#interpreting-the-generated-warnings).

  Reviewing this subset of conversations can help you understand if real users have taken a conversation path which is not present in the training data and hence "surprising" for machine learning policies like `TEDPolicy`. Adding these conversation paths (with potential corrections if `TEDPolicy` subsequently failed) as training stories will result in more robust action prediction by policies such as `TEDPolicy`. Users are encouraged to [adjust the `tolerance` parameter of `UnexpecTEDIntentPolicy`](https://rasa.com/docs/rasa/policies#tuning-the-tolerance-parameter) to control how "surprising" a conversation should be to be included in the warnings file.

> 你的测试用户至少有一些关于机器人要做什么的指示；真正的用户往往要么不知道，要么忽视给他们的指示。你不能迎合每一个意外的用户行为，但你可以尝试解决你注意到的主要摩擦点。以下是一些你可以考虑寻找的东西：
>
> * 看看那些发生了 "超出范围 "的意图或回退行为的对话。这些可能表明一个潜在的新技能，或者只是一个错误分类的用户话语。
>
> * 寻找用户的挫折感，例如要求转移到一个人身上。
>
> * 如果助手是用管道中包含的UnexpecTEDIntentPolicy训练的，你可以寻找在任何对话中预测到行动_不可能_意图的对话。当用户所表达的最后一个意图在当前的对话环境中是出乎意料的时候，就会预测到一个不可能的行动。你也可以通过运行一个独立的脚本来过滤掉这样的对话，该脚本的作用如下。
>   - 从跟踪器商店中获取真实的对话。
>   - 在获取的对话中运行`rasa test`，并在一个单独的警告文件中过滤含有action_unlikely_intent的对话。你可以阅读更多关于如何解释这些警告的信息
>
> 审查这个对话子集可以帮助你了解真实的用户是否采取了训练数据中没有的对话路径，因此对TEDPolicy这样的机器学习策略来说是 "令人惊讶的"。添加这些对话路径（如果TEDPolicy后来失败了，可能会进行修正）作为训练故事，将使TEDPolicy等策略的行动预测更加稳健。我们鼓励用户调整UnexpecTEDIntentPolicy的容忍度参数，以控制对话在多大程度上 "令人惊讶 "才能被纳入警告文件。

#### Annotate[#](https://rasa.com/docs/rasa/conversation-driven-development#annotate)

Continue to follow [best practices for NLU](https://rasa.com/docs/rasa/generating-nlu-data) as you add new user utterances from real conversations to your training data. Be careful not to overfit your NLU model to utterances like those already in your training data. This can happen when you continuously add user utterances that were already predicted correctly and with high confidence to your training data. To avoid overfitting and help your model generalize to more diverse user utterances, add only user utterances that the model previously predicted incorrectly or with low confidence.

> 当你从真实的对话中添加新的用户语料到你的训练数据时，继续遵循NLU的最佳实践。注意不要让你的NLU模型与训练数据中已经存在的那些语料过度匹配。当你不断地在你的训练数据中添加已经被正确预测的、具有高置信度的用户语料时，就会发生这种情况。为了避免过度拟合，并帮助你的模型推广到更多不同的用户语料，只添加模型之前预测错误或信心不足的用户语料。

#### Test[#](https://rasa.com/docs/rasa/conversation-driven-development#test)

Add successful user conversations to your [test conversations](https://rasa.com/docs/rasa/testing-your-assistant). Doing this consistently will help ensure you don't introduce regressions as you make other fixes to your bot.

> 将成功的用户对话添加到你的测试对话中。持续这样做将有助于确保你在对机器人进行其他修复时不会引入回归。

#### Track[#](https://rasa.com/docs/rasa/conversation-driven-development#track)

Look for clues to success and failure to help you track your bot's performance.

Some metrics are external to your bot. For example, if you are building a bot to relieve demand on a customer service call center, one metric for success could be the reduction in traffic to the call center. Others you can get directly from conversations, such as whether a user reaches a certain action that represents achieving the user goal.

Automatically tracked metrics are by nature proxy metrics; the only way to get a true measure of success would be to individually review and rate every single conversation with your bot. While this clearly isn't realistic, just keep in mind that no metric is a perfect representation of your bot's performance, so don't rely only on metrics to see where your bot needs improvement.

> 寻找成功和失败的线索，以帮助你跟踪你的机器人的表现。
>
> 有些指标是你的机器人的外部指标。例如，如果你正在建立一个机器人来缓解对客户服务呼叫中心的需求，一个成功的指标可以是呼叫中心的流量减少。其他的指标你可以直接从对话中获得，比如用户是否达到了某个代表实现用户目标的行动。
>
> 自动跟踪的指标本质上是代理指标；获得真正的成功衡量标准的唯一方法是单独审查和评价与你的机器人的每一次对话。虽然这显然是不现实的，但只要记住，没有一个指标能完美地代表你的机器人的表现，所以不要只依靠指标来了解你的机器人需要改进的地方。	

#### Fix[#](https://rasa.com/docs/rasa/conversation-driven-development#fix)

Continue to follow [best practices for Stories](https://rasa.com/docs/rasa/writing-stories) as you expand and improve your bot's skills. Let user demand guide which skills you add and which fixes you make. Make smaller changes frequently rather than making big changes only once in a while. This will help you gauge the effectiveness of changes you're making, since you'll get user feedback more frequently. Your [CI/CD pipeline](https://rasa.com/docs/rasa/setting-up-ci-cd) should allow you to do so with confidence.

> 在你扩展和改进你的机器人的技能时，继续遵循Story的最佳实践。让用户需求指导你增加哪些技能，进行哪些修复。经常做一些小改动，而不是偶尔才做一次大改动。这将有助于你衡量你所做的改变的有效性，因为你会更频繁地得到用户的反馈。你的CI/CD管道应该允许你自信地这样做。

## 2. Generating NLU Data [生成NLU数据]



## 3. Writing Conversation Data [编写对话数据]