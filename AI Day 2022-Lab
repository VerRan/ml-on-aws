# **GCR AI/ML Game Day**

# **中文版**

**机器学习之旅**

![](RackMultipart20220516-1-ckon21_html_8c78522110170fd4.png)我们很高兴您能接受AI/ML 挑战来帮助我们优化独角兽的运营。

为了优化我们的业务运营，您将使用Amazon Forecast 来预测我们应在库存中保留的最优独角兽数量。货架上的独角兽太多或太少将会损害我们的业务。管理层不会对此感到高兴。但是，如果你的预测有助于提高客户满意度和公司的业务业绩，你将获得奖励积分。

技术团队确实可以使用一些帮助来实施他们的机器学习模型部署。我们在机器学习模型中使用Sagemaker 中的Jupiter notebook。手动部署和测试模型是一件痛苦的事情。你将成为帮助团队自动化部署过程的英雄。同时，这个也可以让您获积分。

祝你好运！

**介绍**

[**Amazon Forecast**](https://catalog.us-east-1.prod.workshops.aws/workshops/704cb6e9-5dcc-4976-ba2a-e778cec6b4dc/en-US/intro#amazon-forecast)

在今天的游戏中，您将使用Amazon Forecast、Amazon SageMaker、Amazon Lex 以及其他一些支持服务来完成今天的任务。

当前独角兽公司在预测未来业务成果方面，使用了包括简单的电子表格，复杂的财务规划软件，用于准确预测未来的业务成果，例如产品需求、资源需求或财务绩效。这些工具通过查看一系列历史数据（称为时间序列数据）来构建预测。例如，这些工具试图通过查看上一年的数据，然后预测未来的能源消耗，这里基本的假设是未来由过去决定。这种方法在具有不规则趋势的大型数据集场景下，很难生成准确的预测。此外，它无法轻松地将随时间变化的数据系列（例如价格、折扣、天气模式、人口增长...）与相关的自变量（例如产品功能和商店位置）结合起来。

基于与 [Amazon.com](http://amazon.com/) 相同的技术， **Amazon Forecast**  **使用机器学习将时间序列数据与其他变量结合起来以构建预测** 。Amazon Forecast 不需要任何机器学习经验即可开始使用。您只需要提供历史数据，以及您认为可能会影响预测的任何其他数据。例如，您将预测独角兽的出租数量可能会随着季节和商店位置的变化而变化。这种复杂的关系很难单独确定，但机器学习非常适合识别它。在您提供数据后，Amazon Forecast 将自动对数据进行检查，确定有意义的内容，并生成一个预测模型，该模型能够做出比单独查看时间序列数据准确率高出50% 的预测模型。

要了解有关亚马逊预测的更多信息，请访问 [https://aws.amazon.com/forecast/resources/](https://aws.amazon.com/forecast/resources/)

[**Amazon Sagemaker**](https://catalog.us-east-1.prod.workshops.aws/workshops/704cb6e9-5dcc-4976-ba2a-e778cec6b4dc/en-US/intro#amazon-sagemaker)

借助Amazon SageMaker，数据科学家和机器学习工程师可以快速轻松地构建和训练机器学习模型，然后将模型直接部署到生产就绪的托管环境中。它提供了一个集成的Jupyter notebook 实例，可轻松访问数据源以进行探索和分析，因此您无需管理服务器。请访问 [https://docs.aws.amazon.com/sagemaker/index.html](https://docs.aws.amazon.com/sagemaker/index.html) 了解有关SageMaker 的更多信息。

为了更好的完成今天的游戏，我们已经对Sagemaker notebook 进行了设置，因此您无需具备广泛的机器学习背景即可成功使用它。按照提示操作，你的团队将知道该如何完成任务。

[**Amazon Lex**](https://catalog.us-east-1.prod.workshops.aws/workshops/704cb6e9-5dcc-4976-ba2a-e778cec6b4dc/en-US/intro#amazon-lex)

Amazon Lex 使用与Amazon Alexa 相同的深度学习技术，借助自动语音识别(ASR) 和自然语言理解(NLU) 等高级深度学习功能，帮助客户打造高度吸引人的用户体验和逼真的对话互动。

在智能聊天机器人模块中，您将构建一个自助聊天机器人来接受独角兽租赁订单并帮助客户解决常见问题。

现在让我们开始吧。

**环境访问**

**访问看板**

- 前往 [https://dashboard.eventengine.run/](https://dashboard.eventengine.run/)
- 输入提供给你的12位数的团队哈希值

![](RackMultipart20220516-1-ckon21_html_a55eeb1c4248c24b.png)

**访问环境**

在GameDay 模块的 &quot;输出&quot; 部分下，仪表板将显示有关源环境的详细信息，如下所示：

 ![](RackMultipart20220516-1-ckon21_html_81606f9dbdc7955d.png)

**访问**** AWS **** 账户**

要访问您的AWS 账户，请单击AWS 控制台按钮，如下所示：
 ![](RackMultipart20220516-1-ckon21_html_25e8604808702b53.png)弹出窗口将要求您选择打开控制台（在当前浏览器中打开AWS 控制台）或复制登录链接（将其粘贴到其他浏览器中）。

**预测**

[**独角兽需求预测**](https://catalog.us-east-1.prod.workshops.aws/workshops/704cb6e9-5dcc-4976-ba2a-e778cec6b4dc/en-US/forecast#unicorn-demand-forecasting)

公司已要求你构建用于预测独角兽未来4小时销量的预测功能，你可能也听说过，我们的数据科学团队已经离开了公司。数据科学团队在离开之前，我收集了一些有关如何获取和利用预测的说明。他们使用了名为 &quot;Forecast&quot; 的AWS 服务。作为其中的一部分，他们能够创建我们独角兽数据的数据集，并能够定义算法并训练模型。此详细信息位于Forecast 服务的predictor部分。

默认参数用于训练predictor。现在，下一步将是 &quot;创建预测&quot; 和 &quot;预测导出&quot; 以获取预测数据。他们让我有20 分钟的时间来处理这个问题。历史需求数据，存放在我们的S3 存储桶中的一个名为 &quot;event-dataset.csv&quot; 的文件中找到

_为了提交预测 __/__ 预测，您需要确保数据格式正确，并遵循某些存储最佳实践。_
 ![](RackMultipart20220516-1-ckon21_html_eca95b370cafdd00.png)

1. 创建预测：创建预测时，您可以指定多个分位数值。Forecast 为输出文件提供对应于标有 &quot;p90&quot;、&quot;p50&quot; 等的列的值。

- 这个意味着真实值（该列中的值）预计将分别低于预测值的90％、50％等。这些被称为分位数。
- 企业根据其场景针对各种分位数进行选取。例如-取决于企业中的资本成本（过度预测）或缺少客户需求（预测不足）之间的权衡。对于 &quot;p10&quot; 预测，实际值预计会在10% 的时间内低于预测值。如果投资资本成本很高（例如，产品库存过多），那么 &quot;p10&quot; 分位数预测对于订购相对较少的商品很有用。同样，对于 &quot;p90&quot; 预测，预计真实值将在90% 的时间内低于预测值。如果缺少客户需求会导致大量收入损失或客户体验不佳，那么p90 预测更有用。

1. 创建预测导出：创建预测时，为了将数据转换为可读的CSV，您需要启动 &quot;预测导出作业&quot;。

![](RackMultipart20220516-1-ckon21_html_38d9486f5fe3bd57.png)

- 对于IAM 角色，您可以选择创建IAM 角色并逐步完成创建新IAM 角色的过程
- 对于S3 位置，您可以选择从中获取 &quot;event-dataset.csv&quot; 文件的同一存储桶。只要确保在 &quot;S3预测导出位置&quot; 中指定具有适当名称的类似文件夹的结构即可。例如 — &#39;3://john-bucket/forecast-exports&#39;
- 导出任务完成后，您可以在创建导出任务时在指定的S3 位置看到一些新文件。需要注意的一点是，这些导出有时会为相同的数据创建多个CSV文件，即将整个预测切成多个CSV文件。你会注意到，如果创建了多个CSV，它们之间是时间关联的。你可以将这些文件下载到您的计算机上。

![](RackMultipart20220516-1-ckon21_html_9a8d23888a3f0bea.png) ![](RackMultipart20220516-1-ckon21_html_fdfe2eb6c21aad29.png)

1. 当你提交时，CSV 文件需要具有列标题 — &quot;item\_id&quot;、&quot;date&quot; 和 &quot;demand&quot;

- 作为发送CSV 进行评估的一部分，请务必删除所有不必要的列。仅保留三列-您可以根据自己的直觉选择任何分位数作为需求

![](RackMultipart20220516-1-ckon21_html_b1fa284c6dc16c1b.png)

- CSV 需要具有4 小时或240 分钟的 &quot;demand&quot; 值[FORECAST HORIZON]，也就是说，我们预计独角兽的需求将达到4 个小时。

![](RackMultipart20220516-1-ckon21_html_d01dcd504d66be2a.png)

1. 创建要提交的文件后，您需要将其上传到S3。使用导出结果和历史 &quot;event-dataset.csv&quot; 文件的相同存储桶。在那里上传最终提交后，请务必记下此新对象的S3 路径（格式-s3: //john-bucket/submission.csv）。当你点击该文件旁边的复选框时，你可以使用 &quot;复制路径&quot; 按钮将该路径复制到剪贴板。

![](RackMultipart20220516-1-ckon21_html_51139580a981a5e4.png)

1. 获得最终预测提交的S3 对象路径后，请返回Event Engine团队仪表板并将其粘贴到本模块 &quot;输入&quot; 部分下的 &quot;S3 URL&quot; 空间中。点击 &quot;更新&quot; 进行提交。

_成功完成本部分后，您将获得 __10,000__ 点积分！要获得额外的积分，你可以提交一个新文件，将_ _&quot; __需求__&quot;_ _作为你认为可能更接近真实值的不同分位数。另外，您可以查看奖金部分，了解更多调整预测的方法。_

_如果您没有看到积分奖励或收到有关格式错误的消息，请仔细检查您的 __csv__ 格式以匹配列标题 __-&quot;item\_id&quot;__ 、 __&quot;__ 日期 __&quot;_ _和_ _&quot;__ 需求 __&quot;__ 。_

**奖金**

_在我们的一次战略会议上，提出了关于提高预测准确性的构想。_

自从数据科学团队离开公司以来，Amazon Forecast 现在可以使用最适合您的数据的机器学习算法组合，这个功能将使预测结果的准确度提高多达40%。此功能称为AutoPredictor。在许多情况下，机器学习专家会为其数据集的不同部分训练单独的模型，以提高预测的准确性。对于非机器学习专家而言，对数据进行细分和应用不同算法的过程可能非常具有挑战性。Forecast 使用ML 不仅可以学习每个项目的最佳算法，还可以学习每个项目的最佳算法组合，从而使预测的准确性提高多达40％。

要使用此新功能，您只需从Forecast 控制台（如下所示）中的predictor页面升级现有predictor即可。
 ![](RackMultipart20220516-1-ckon21_html_1330a0832bb988d0.png)
这项新功能还提供了可解释性，可帮助您更好地了解数据集中的属性（如价格、类别或假日）如何影响预测值。

但是，此数据集不支持可解释性功能，因为predictor没有以下选项：相关时间序列、项目元数据或附加数据集（如Holidays and Weather Index）。（我责怪数据科学团队！他们没叫我们获取这些信息）。因此，不要启用可解释性（如下所示）。
 ![](RackMultipart20220516-1-ckon21_html_c9053156174b490.png)

升级到AutoPredictor 后，原始predictor将保持活动状态，升级后的predictor将具有单独的predictor ARN。这使您能够比较两个predictor之间的准确度量度，并且您仍然可以使用原始predictor生成预测。

_平均而言，升级到 __AutoPredictor_ _可能需要__ 3_ _个小时。在此期间，您可以随意使用其他模块。_

**应用机器学习管道**

欢迎加入独角兽租赁数据科学团队！

我们的营销团队建议我们实施高级会员计划，目的是进一步增加从客户侧获得收益。该会员计划将允许会员只需支付少量月租费，从而在每次租赁时可以获得高级独角兽。

我们认为这确实会很有作用，但事实证明，许多客户并不了解优质独角兽体验有多棒。因此，我们决定定位那些我们认为最有可能注册促销活动的用户： **&quot;**** 一次免费的高级独角兽体验活动 ****&quot;** 。

但是，这些独角兽游并不是免费的，因此我们只想定位注册概率很高的用户。之前我们聘请了一位数据科学家，他能够为我们创建这个模型，但我们从未将该模型投入生产。

我们需要你从他们停下来的地方继续前行！部署模型并创建终端节点，然后确保模型始终能够获取最新数据并进行训练，以便模型继续保持良好的性能。

当然，这样做一定会带来您想要的积分-\_-。

_一旦你的 __SageMaker_ _端点启动并运行，你将获得__ 10,000_ _点积分！只要您的 __SageMaker_ _端点在每次评分检查期间可用，您就可以继续赚取额外__ 250_ _点积分。_

**模块一**

我们最近聘请了一位数据科学家来为我们构建机器学习模型。她准备了创建数据集的脚本，并训练了一个非常可靠的模型，但是这个模型我们还没有真正在生产上运行过。然后她就离开了我们公司，并去了一家热门的机器学习初创公司工作_..._ _做一些关于热狗的事情__..._

与此同时，我们聘请了一名实习生。他让我们开始了这件事情，但说实话，我认为他只是复制并粘贴了本教程中的内容：[https://www.youtube.com/watch?v=0kMdOi69tjQ。这个链接也许值得一看](https://www.youtube.com/watch?v=0kMdOi69tjQ%26%2312290%3B%26%2320063%3B%26%2335768%3B%26%2320540%3B%26%2324471%3B%26%2319968%3B%26%2330475%3B%26%2325110%3B%26%2332773%3B%26%2325105%3B%26%2326377%3B%26%2320160%3B%26%2320040%3B)（_国内访问不了也没关系，不影响我们继续前行_）。

不管他做了什么，效果倒是有一写，他为部署创建了某种管道？他总是会继谈论如何使用Step Function Data Science SDK。我发誓我听见他这么说了一百万遍了。

不幸的是，有人删除了我们账户中几乎所有的重要内容（这种事情发生的频率比我们想承认的要多），所以我们需要你修复它。创建一个新的sagemaker 笔记本实例并运行以下[笔记本](https://s3.amazonaws.com/ee-assets-prod-us-east-1/modules/e6f688a502b84187b74055f1de9e0514/v1/Deploy_Model_Workflow.ipynb)。根据他在最后一天留在麦当劳收据上的乱写笔记，这个应该可以重新创建管道并部署模型。

**提示**

如果你遇到问题，请确保你使用的是以下内核：conda\_amazonei\_mxnet\_p36。

要创建sagemaker 笔记本，请遵循以下指南（从标有 &quot;启动笔记本实例&quot; 的部分开始）：[https://sagemaker-workshop.com/introduction/notebook.html](https://sagemaker-workshop.com/introduction/notebook.html)

请务必为IAM 选择teamRole。

**模块**** 2**

现在你已经完成了所有设置，让我们对工作流程进行一些改进。最值得注意的是，我们的脚本每隔一段时间就会运行一次，这些脚本会将新的train.csv 文件拖放到指定的S3 存储桶中。真正棒的是，如果每次有新的训练数据集时，它都会启动新的训练作业并取代我们的旧端点。

我与一位AWS 解决方案架构师进行了交谈，她详细说明了我应该做什么。不幸的是我的互联网信号不稳定，所以我只能听见大部分内容。但看起来重要的部分是这样的：

设置方法是 &quot;Event... 什么？&quot;（EventRoad？EventPass？记不起来了），这个是用于S3 来触发我们Step Functions的。

当SA 谈论这个问题时，她在聊天中粘贴了这个：配置输入-输入转换器在第一个框中：{&quot;eventID&quot;: &quot;$.detail.eventID&quot;} 在第二个框中：{&quot;eventID&quot;:\&lt;eventID\&gt;}

她说这些信息对我来说就足够了呢。你也许可以从这些信息中完成上面的配置。

**提示**

你需要设置EventBridge 规则才能使用S3 触发StepFunctions 工作流程。请按照以下屏幕截图了解配置细节。
 ![](RackMultipart20220516-1-ckon21_html_513f11bfbe2ccf2d.png)
 ![](RackMultipart20220516-1-ckon21_html_2266a2799c0c7b4d.png)
 ![](RackMultipart20220516-1-ckon21_html_1155430776552b6e.png)

**智能聊天机器人**

目前我们的租赁网站已宕机，我们无法接受独角兽租赁订单。本季度对独角兽的需求很高，我们需要让客户满意。

工程团队在离开之前提到了名为Amazon Lex 的AWS 服务。他们表示，使用Amazon Lex 轻松构建自助聊天机器人、虚拟代理、对话式IVR 系统和信息机器人。他们还表示，Amazon Lex提供了先进的深度学习功能，例如自动语音识别（ASR）和自然语言理解（NLU）。

_完成第 __1_ _部分和第__ 2_ _部分即可赚取 __10,000_ _点积分！完成奖励部分后，向活动工作人员展示您的聊天机器人，即可额外赚取__ 20,000__点积分！_

感谢您让我们恢复运行状态。我们迫不及待想试试你的AI 聊天机器人！

**第一部分**

我们需要你的帮助，构建一个聊天机器人来接受包含独角兽大小和类型的租赁订单。聊天机器人的示例输出如下。
 ![](RackMultipart20220516-1-ckon21_html_62ffb629cb8321b.png)
_注意：在测试之前，请记得在聊天机器人上启动构建。_

**提示**

工程团队表示，我们可以使用此[链接](https://docs.aws.amazon.com/lex/latest/dg/gs-bp-create-bot.html)开始构建自定义机器人。他们建议使用Amazon Lex V2 控制台。

**第二部分**

对于我们的租赁网站给您带来的不便，客户可以根据自己的意愿保留租金，然后在我们的任何自助独角兽停车场将独角兽归还给我们。我们创建了一个常见问题列表，以帮助客户度过租用自己喜欢的独角兽的艰难时期。

我们需要你的帮助，在你开发的聊天机器人上显示这些有用的常见问题解答。工程团队提到了另一项名为[Amazon Kendra](https://aws.amazon.com/kendra/)的AWS服务，该服务使用机器学习提供智能搜索服务。

我们已在您团队的AWS 账户中创建了Kendra 索引和常见问题解答。通过向聊天机器人添加Kendra 搜索意图，将您的Lex 聊天机器人与Kendra 常见问题集成。

输出应类似于以下内容。
 ![](RackMultipart20220516-1-ckon21_html_939c4ee953a2c7ce.png)

_聊天机器人准备就绪后，在团队控制面板中输入 __Amazon Lex V2_ _机器人__ ID __，然后输入__ Bot Alias ID __。例如：__ DBGBABCAZD __、__ TSTXYZASID_

**提示**

为了从Kendra 检索常见问题解答，工程团队说你可以在KendrasearchIntent 内置意图中添加以下内容作为结束回复消息。
((x-amz-lex: kendra-search-response-question\_answer-answer-1))
 ![](RackMultipart20220516-1-ckon21_html_ecf7033da9a4cd41.png)

**奖励**

_通过在聊天机器人中创建响应卡来提供租赁意向和常见问题解答，额外赚取 __20,000__ 点积分__。_

响应卡的示例输出。
 ![](RackMultipart20220516-1-ckon21_html_5753c5d2eaa3031b.png)

**更多资源**

了解更多AWS 资源，用于在AWS 上构建和运行应用程序：

[Sagemaker 研讨会1](https://www.sagemakerworkshop.com/introduction)-在本次研讨会中，您将探索AWS 上机器学习模型的开发周期。

[Sagemaker 研讨会2](https://sagemaker-workshop.com/introduction.html)-在本次研讨会中，您将探索使用AWS Sagemaker 构建客户算法和保护数据科学环境的内置算法。

[AWS 示例 ](https://github.com/aws-samples?q=sagemaker&amp;type=&amp;language=)— 示例和更多研讨会。
