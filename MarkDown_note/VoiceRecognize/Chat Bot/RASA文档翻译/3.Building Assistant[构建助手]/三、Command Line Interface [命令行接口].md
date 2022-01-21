# 三、Command Line Interface [命令行接口]

## Cheat Sheet[备忘纸条]

| Command                 | Effect                                                       |
| :---------------------- | :----------------------------------------------------------- |
| `rasa init`             | Creates a new project with example training data, actions, and config files.<br />创建一个新的项目，包括训练数据、动作和配置文件的例子。 |
| `rasa train`            | Trains a model using your NLU data and stories, saves trained model in `./models`.<br />使用你的NLU数据和故事训练一个模型，将训练好的模型保存在`./models`中。 |
| `rasa interactive`      | Starts an interactive learning session to create new training data by chatting to your assistant.<br />启动交互式学习课程，通过与您的助手聊天来创建新的训练数据。 |
| `rasa shell`            | Loads your trained model and lets you talk to your assistant on the command line.<br />加载你训练好的模型，让你在命令行上与你的助手对话。 |
| `rasa run`              | Starts a server with your trained model.<br />用你训练的模型启动一个服务器。 |
| `rasa run actions`      | Starts an action server using the Rasa SDK.<br />启动一个Rasa 的Action 服务器 |
| `rasa visualize`        | Generates a visual representation of your stories.<br />生成你的故事的视觉表示图。 |
| `rasa test`             | Tests a trained Rasa model on any files starting with `test_`.<br />在任何以`test_`开头的文件上测试训练好的Rasa模型。 |
| `rasa data split nlu`   | Performs a 80/20 split of your NLU training data.<br />对你的NLU训练数据进行80/20分割。 |
| `rasa data convert`     | Converts training data between different formats.<br />在不同的格式之间转换训练数据。 |
| `rasa data migrate`     | Migrates 2.0 domain to 3.0 format.<br />将2.0域迁移到3.0格式。 |
| `rasa data validate`    | Checks the domain, NLU and conversation data for inconsistencies.<br />检查领域、NLU和对话数据是否存在不一致。 |
| `rasa export`           | Exports conversations from a tracker store to an event broker.<br />将对话从跟踪器商店导出到事件代理。 |
| `rasa evaluate markers` | Extracts markers from an existing tracker store.<br />从现有的跟踪器存储中提取标记。 |
| `rasa x`                | Launches Rasa X in local mode.<br />在本地模式下启动Rasa X。 |
| `rasa -h`               | Shows all available commands.<br />显示所有可用的命令。      |

## rasa init[#](https://rasa.com/docs/rasa/command-line-interface#rasa-init)

This command sets up a complete assistant for you with some example training data:

```
这个命令为你设置了一个完整的助手，有一些训练数据的例子。
```

```shell
rasa init  或者 rasa init --no-prompt
```

It creates the following files:

```markdown
.
├── actions
│   ├── __init__.py
│   └── actions.py
├── config.yml
├── credentials.yml
├── data
│   ├── nlu.yml
│   └── stories.yml
├── domain.yml
├── endpoints.yml
├── models
│   └── <timestamp>.tar.gz
└── tests
   └── test_stories.yml
```

It will ask you if you want to train an initial model using this data. If you answer no, the `models` directory will be empty.

Any of the default CLI commands will expect this project setup, so this is the best way to get started. You can run `rasa train`, `rasa shell` and `rasa test` without any additional configuration.

```
它将问你是否要用这些数据训练一个初始模型。如果你回答不，`models`目录将是空的。

任何默认的CLI命令都会想到这个项目设置，所以这是开始的最好方法。你可以运行`rasa train`, `rasa shell`和`rasa test`而不需要任何额外的配置。
```

## rasa train[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-train)

The following command trains a Rasa Open Source model:

```
rasa train
```

If you have existing models in your directory (under `models/` by default), only the parts of your model that have changed will be re-trained. For example, if you edit your NLU training data and nothing else, only the NLU part will be trained.

If you want to train an NLU or dialogue model individually, you can run `rasa train nlu` or `rasa train core`. If you provide training data only for one one of these, `rasa train` will fall back to one of these commands by default.

`rasa train` will store the trained model in the directory defined by `--out`, `models/` by default. The name of the model by default is `<timestamp>.tar.gz`. If you want to name your model differently, you can specify the name using the `--fixed-model-name` flag.

The following arguments can be used to configure the training process:

```
如果你的目录中有现有的模型（默认在`models/`下），只有你的模型中发生变化的部分会被重新训练。例如，如果你编辑了你的NLU训练数据，而没有其他内容，只有NLU部分会被训练。

如果你想单独训练一个NLU或对话模型，你可以运行`rasa train nlu`或`rasa train core`。如果你只为其中之一提供训练数据，`rasa train`将默认返回到这些命令之一。

`rasa train`将把训练好的模型存储在`--out`定义的目录中，默认为`models/`。模型的名称默认为`<timestamp>.tar.gz`。如果你想以不同的方式命名你的模型，你可以使用`--fixed-model-name`标志指定名称。

以下参数可用于配置训练过程:
```

The following arguments can be used to configure the training process:

```
usage: rasa train [-h] [-v] [-vv] [--quiet] [--data DATA [DATA ...]]
                  [-c CONFIG] [-d DOMAIN] [--out OUT] [--dry-run]
                  [--augmentation AUGMENTATION] [--debug-plots]
                  [--num-threads NUM_THREADS]
                  [--fixed-model-name FIXED_MODEL_NAME] [--persist-nlu-data]
                  [--force] [--finetune [FINETUNE]]
                  [--epoch-fraction EPOCH_FRACTION]
                  {core,nlu} ...
positional arguments:
  {core,nlu}
    core                Trains a Rasa Core model using your stories.
    nlu                 Trains a Rasa NLU model using your NLU data.
```

### Incremental training[**增量学习**]

> ##### NEW IN 2.2
>
> This feature is experimental. We introduce experimental features to get feedback from our community, so we encourage you to try it out! However, the functionality might be changed or removed in the future. If you have feedback (positive or negative) please share it with us on the [Rasa Forum](https://forum.rasa.com/).
>
> 这个功能是实验性的。我们推出实验性功能是为了从我们的社区获得反馈，所以我们鼓励你试一试! 然而，该功能在未来可能会被改变或删除。如果您有反馈意见（正面或负面），请在[Rasa论坛]（https://forum.rasa.com/）与我们分享。

In order to improve the performance of an assistant, it's helpful to practice [**CDD(Conversation-Driven Development  会话驱动开发)** ](https://rasa.com/docs/rasa/conversation-driven-development)and add new training examples based on how your users have talked to your assistant. You can use rasa train --finetune to initialize the pipeline with an already trained model and further finetune it on the new training dataset that includes the additional training examples. This will help reduce the training time of the new model.

By default, the command picks up the latest model in the models/ directory. If you have a specific model which you want to improve, you may specify the path to this by running rasa train --finetune <path to model to finetune>. Finetuning a model usually requires fewer epochs to train machine learning components like DIETClassifier, ResponseSelector and TEDPolicy compared to training from scratch. Either use a model configuration for finetuning which defines fewer epochs than before or use the flag --epoch-fraction. --epoch-fraction will use a fraction of the epochs specified for each machine learning component in the model configuration file. For example, if DIETClassifier is configured to use 100 epochs, specifying --epoch-fraction 0.5 will only use 50 epochs for finetuning.

You can also finetune an NLU-only or dialogue management-only model by using rasa train nlu --finetune and rasa train core --finetune respectively.

To be able to fine tune a model, the following conditions must be met:

1. The configuration supplied should be exactly the same as the configuration used to train the model which is being finetuned. The only parameter that you can change is epochs for the individual machine learning components and policies.

2. The set of labels(intents, actions, entities and slots) for which the base model is trained should be exactly the same as the ones present in the training data used for finetuning. This means that you cannot add new intent, action, entity or slot labels to your training data during incremental training. You can still add new training examples for each of the existing labels. If you have added/removed labels in the training data, the pipeline needs to be trained from scratch.

3. The model to be finetuned is trained with MINIMUM_COMPATIBLE_VERSION of the currently installed rasa version.

```
为了提高助手的性能，练习CDD并根据用户与助手的交谈情况增加新的训练例子是很有帮助的。你可以使用rasa train --finetune，用一个已经训练好的模型来初始化管道，并在包括额外训练例子的新训练数据集上进一步微调它。这将有助于减少新模型的训练时间。

默认情况下，该命令会拾取models/目录下的最新模型。如果你有一个想要改进的特定模型，你可以通过运行rasa train --finetune <要微调的模型路径>来指定这个路径。与从头开始训练相比，微调一个模型通常需要更少的历时来训练机器学习组件，如DIETClassifier、ResponseSelector和TEDPolicy。要么使用定义了比以前更少的epochs的模型配置来进行微调，要么使用标志--epoch-fraction。--epoch-fraction将使用在模型配置文件中为每个机器学习组件指定的历时的一部分。例如，如果DIETClassifier被配置为使用100个历时，指定--epoch-fraction 0.5将只使用50个历时来进行微调。

你也可以分别使用rasa train nlu --finetune和rasa train core --finetune来微调仅有NLU或仅有对话管理的模型。

为了能够对模型进行微调，必须满足以下条件。

1. 提供的配置应该与用于训练被微调的模型的配置完全相同。你可以改变的唯一参数是各个机器学习组件和策略的历时。
2. 训练基础模型的标签集（意图、行动、实体和槽）应该与用于微调的训练数据中的标签完全相同。这意味着在增量训练期间，你不能向训练数据添加新的意图、动作、实体或槽的标签。你仍然可以为每个现有的标签添加新的训练实例。如果你在训练数据中增加/删除了标签，管道需要从头开始训练。
3. 要微调的模型是用当前安装的rasa版本的MINIMUM_COMPATIBLE_VERSION来训练的。
```

## rasa interactive[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-interactive)

You can [use Rasa X in local mode](https://rasa.com/docs/rasa-x) to do interactive learning in a UI, check out the [docs](https://rasa.com/docs/rasa-x/user-guide/test-assistant#talk-to-your-bot) for more details.

If you'd rather use the command line,  you can start an interactive learning session by running:

```
你可以在本地模式下使用Rasa X在用户界面中进行交互式学习，查看文档以了解更多细节。
如果你愿意使用命令行，你可以启动一个交互式学习会话 by running:
```

```
rasa interactive
```

This will first train a model and then start an interactive shell session. You can then correct your assistants predictions as you talk to it. If [`UnexpecTEDIntentPolicy`](https://rasa.com/docs/rasa/policies#unexpected-intent-policy) is included in the pipeline, [`action_unlikely_intent`](https://rasa.com/docs/rasa/default-actions#action_unlikely_intent) can be triggered at any conversation turn. Subsequently, the following message will be displayed:

>这将首先训练一个模型，然后开始一个交互式 shell 会话。然后，你可以在与之交谈时纠正助手的预测。
>如果[UnexpecTEDIntentPolicy](https://rasa.com/docs/rasa/policies#unexpected-intent-policy)被包含在管道中，[action_unlikely_intent](https://rasa.com/docs/rasa/default-actions#action_unlikely_intent)可以在任何对话回合中被触发。随后，将显示以下信息。

>  The bot wants to run 'action_unlikely_intent' to indicate that the last user message was unexpected
>  at this point in the conversation. Check out UnexpecTEDIntentPolicy docs to learn more.
>
>  机器人想运行'action_unlikely_intent'来表示最后一个用户信息是意外的 在对话的这一点上。查看UnexpecTEDIntentPolicy文档以了解更多。

As the message states, this is an indication that you have explored a conversation path which is unexpected according to the current set of training stories and hence adding this path to training stories is recommended. Like other bot actions, you can choose to confirm or deny running this action.

If you provide a trained model using the `--model` argument, training is skipped and that model will be loaded instead.

During interactive learning, Rasa will plot the current conversation and a few similar conversations from the training data to help you keep track of where you are. You can view the visualization at http://localhost:5005/visualization.html as soon as the session has started. This diagram can take some time to generate. To skip the visualization, run rasa interactive --skip-visualization.

```
正如消息所说，这表明你已经探索了一条对话路径，根据当前的训练故事集，这是出乎意料的，因此建议将此路径添加到训练故事中。像其他机器人动作一样，你可以选择确认或拒绝运行这个动作。

如果你使用 `--model` 参数提供了一个训练过的模型，训练将被跳过，该模型将被加载。

在交互式学习过程中，Rasa会绘制当前对话和训练数据中的一些类似对话，以帮助你跟踪你的位置。一旦会话开始，你就可以在http://localhost:5005/visualization.html。这张图可能需要一些时间来生成。要跳过可视化，请运行rasa interactive --skip-visualization。
```

The following arguments can be used to configure the interactive learning session:

```shell
usage: rasa interactive [-h] [-v] [-vv] [--quiet] [--e2e] [-p PORT] [-m MODEL]
                        [--data DATA [DATA ...]] [--skip-visualization]
                        [--conversation-id CONVERSATION_ID]
                        [--endpoints ENDPOINTS] [-c CONFIG] [-d DOMAIN]
                        [--out OUT] [--augmentation AUGMENTATION]
                        [--debug-plots] [--finetune [FINETUNE]]
                        [--epoch-fraction EPOCH_FRACTION] [--force]
                        [--persist-nlu-data]
                        {core} ... [model-as-positional-argument]
```

## rasa shell[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-shell)

You can [use Rasa X in local mode](https://rasa.com/docs/rasa-x) to talk to your assistant in a UI. Check out the [Rasa X docs](https://rasa.com/docs/rasa-x/user-guide/test-assistant#talk-to-your-bot) for more details.

If you'd rather use the command line, you can start a chat session by running:

> 你可以[在本地模式下使用Rasa X](https://rasa.com/docs/rasa-x)，在用户界面中与你的助手对话。请查看 [Rasa X docs](https://rasa.com/docs/rasa-x/user-guide/test-assistant#talk-to-your-bot) 以了解更多细节。
>
> 如果你宁愿使用命令行，你可以通过运行来启动一个聊天会话。

```
rasa shell
```

By default this will load up the latest trained model. You can specify a different model to be loaded by using the --model flag.

If you start the shell with an NLU-only model, rasa shell will output the intents and entities predicted for any message you enter.

If you have trained a combined Rasa model but only want to see what your model extracts as intents and entities from text, you can use the command rasa shell nlu.

> 默认情况下，这将加载 latest trained model.  你可以通过使用  `--model  `flag 来指定一个不同的模型来加载。
>
> 如果你用一个 NLU-only model 启动 shell，`rasa shell `将输出你输入的任何信息的意图和实体预测。
>
> 如果你已经训练了一个组合的Rasa模型，但只想看看你的模型从文本中提取了哪些意图和实体，你可以使用 `rasa shell nlu`命令。

To increase the logging level for debugging, run:

```
rasa shell --debug
```

> ##### NOTE
>
> In order to see the typical greetings and/or session start behavior you might see in an external channel, you will need to explicitly send `/session_start` as the first message. Otherwise, the session start behavior will begin as described in [Session configuration](https://rasa.com/docs/rasa/domain#session-configuration).
>
> 为了能 在外部通道看到 典型问候和/或会话开始行为，你需要明确地发送/session_start作为第一条消息。否则，会话启动行为将按照会话配置中的描述开始。

The following arguments can be used to configure the command:

```
usage: rasa shell [-h] [-v] [-vv] [--quiet]
                  [--conversation-id CONVERSATION_ID] [-m MODEL]
                  [--log-file LOG_FILE] [--use-syslog]
                  [--syslog-address SYSLOG_ADDRESS]
                  [--syslog-port SYSLOG_PORT]
                  [--syslog-protocol SYSLOG_PROTOCOL] [--endpoints ENDPOINTS]
                  [-i INTERFACE] [-p PORT] [-t AUTH_TOKEN]
                  [--cors [CORS [CORS ...]]] [--enable-api]
                  [--response-timeout RESPONSE_TIMEOUT]
                  [--remote-storage REMOTE_STORAGE]
                  [--ssl-certificate SSL_CERTIFICATE]
                  [--ssl-keyfile SSL_KEYFILE] [--ssl-ca-file SSL_CA_FILE]
                  [--ssl-password SSL_PASSWORD] [--credentials CREDENTIALS]
                  [--connector CONNECTOR] [--jwt-secret JWT_SECRET]
                  [--jwt-method JWT_METHOD]
                  {nlu} ... [model-as-positional-argument]
```

## rasa run[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-run)

To start a server running your trained model, run:

```
rasa run
```

> By default the Rasa server uses HTTP for its communication. To secure the communication with SSL and run the server on HTTPS, you need to provide a valid certificate and the corresponding private key file. You can specify these files as part of the `rasa run` command. If you encrypted your keyfile with a password during creation, you need to add the `--ssl-password` as well.
>
> 默认情况下，Rasa服务器使用HTTP进行通信。为了用SSL保证通信安全并在HTTPS上运行服务器，你需要提供一个有效的证书和相应的私钥文件。你可以指定这些文件作为`rasa run`命令的一部分。如果你在创建过程中用密码加密了你的密钥文件，你也需要添加`--ssl-password`。

```
rasa run --ssl-certificate myssl.crt --ssl-keyfile myssl.key --ssl-password mypassword
```

> Rasa by default listens on each available network interface. You can limit this to a specific network interface using the `-i` command line option.
>
> Rasa默认监听每个可用的网络接口。你可以使用-i命令行选项将其限制在一个特定的网络接口。

```
rasa run -i 192.168.69.150
```

The following arguments can be used to configure your Rasa server:

```
usage: rasa run [-h] [-v] [-vv] [--quiet] [-m MODEL] [--log-file LOG_FILE]
                [--use-syslog] [--syslog-address SYSLOG_ADDRESS]
                [--syslog-port SYSLOG_PORT]
                [--syslog-protocol SYSLOG_PROTOCOL] [--endpoints ENDPOINTS]
                [-i INTERFACE] [-p PORT] [-t AUTH_TOKEN]
                [--cors [CORS [CORS ...]]] [--enable-api]
                [--response-timeout RESPONSE_TIMEOUT]
                [--remote-storage REMOTE_STORAGE]
                [--ssl-certificate SSL_CERTIFICATE]
                [--ssl-keyfile SSL_KEYFILE] [--ssl-ca-file SSL_CA_FILE]
                [--ssl-password SSL_PASSWORD] [--credentials CREDENTIALS]
                [--connector CONNECTOR] [--jwt-secret JWT_SECRET]
                [--jwt-method JWT_METHOD]
                {actions} ... [model-as-positional-argument]
```

> For more information on the additional parameters, see [Model Storage](https://rasa.com/docs/rasa/model-storage). See the Rasa [HTTP API](https://rasa.com/docs/rasa/http-api) page for detailed documentation of all the endpoints.
>
> 关于附加参数的更多信息，请参见模型存储。参见Rasa HTTP API页面，了解所有端点的详细文档。

## rasa run actions[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-run-actions)

To start an action server with the Rasa SDK, run:

```
rasa run actions
```

The following arguments can be used to adapt the server settings:

```
usage: rasa run actions [-h] [-v] [-vv] [--quiet] [-p PORT]
                        [--cors [CORS [CORS ...]]] [--actions ACTIONS]
                        [--ssl-keyfile SSL_KEYFILE]
                        [--ssl-certificate SSL_CERTIFICATE]
                        [--ssl-password SSL_PASSWORD] [--auto-reload]
```

## rasa visualize[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-visualize)

To generate a graph of your stories in the browser, run:

> **要在浏览器中生成你的故事图，请运行。**

```
rasa visualize
```

If your stories are located somewhere other than the default location `data/`, you can specify their location with the `--stories` flag.

> 如果你的故事位于默认位置`data/`以外的地方，你可以用`--stories`标志指定它们的位置。

## rasa test[#](https://rasa.com/docs/rasa/command-line-interface/#rasa-test)

To evaluate a model on your test data, run:

```shell
rasa test
```

This will test your latest trained model on any end-to-end stories you have defined in files with the `test_` prefix. If you want to use a different model, you can specify it using the `--model` flag.

> 这将在你在`test_`前缀的文件中定义的任何端到端故事上测试你最新训练的模型。如果你想使用一个不同的模型，你可以使用`--model`标志来指定它。

If you want to evaluate the dialogue and NLU models separately, you can use the commands below:

> 如果你想分别 evaluate  评估 对话和NLU模型，你可以使用下面的命令。

```
rasa test core 	&&   rasa test nlu
```

**You can find more details in [Evaluating an NLU Model](https://rasa.com/docs/rasa/testing-your-assistant#evaluating-an-nlu-model) and [Evaluating a Core Model](https://rasa.com/docs/rasa/testing-your-assistant#evaluating-a-dialogue-model).**

The following arguments are available for `rasa test`:

```
usage: rasa test [-h] [-v] [-vv] [--quiet] [-m MODEL] [-s STORIES]
                 [--max-stories MAX_STORIES] [--endpoints ENDPOINTS]
                 [--fail-on-prediction-errors] [--url URL]
                 [--evaluate-model-directory] [-u NLU]
                 [-c CONFIG [CONFIG ...]] [-d DOMAIN] [--cross-validation]
                 [-f FOLDS] [-r RUNS] [-p PERCENTAGES [PERCENTAGES ...]]
                 [--no-plot] [--successes] [--no-errors] [--no-warnings]
                 [--out OUT]
                 {core,nlu} ...
```

