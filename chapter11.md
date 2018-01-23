## Chapter 11、When to change dev/test sets and metrics

**何时更改开发/测试集和评估指标**

当开始一个新项目时，我会试图快速选择开发/测试集 ，因为这样可以给团队制定一个明确的目标。

我通常会要求我的团队在不到一周之内（几乎不会更长）提供一个初始的开发/测试集和评估指标。提出一个不太完美的方案并迅速行动起来，比花过多时间去思考更好。但是一周这个时间线并不适用于成熟的应用。例如，反垃圾邮件（anti-spam）是一个成熟的深度学习应用。我曾经见过一些团队会花费数月时间在已经成熟的系统上，去获得更好的开发/测试集。

如果你之后发现初始的开发/测试集或评估指标与目标有失偏颇，那么使用一切手段快速更改它们。例如，如果在你的开发集和评估指标上分类器A比分离器B表现好，但你的团队认为分类器B在实际产品中表现的更优越，这可能表示你需要更改开发/测试集或评估指标。

有三个主要原因可能会造成开发集/评估指标不正确地把分类器A排得更高：

1. 你需要做得好的实际数据的分布和开发/测试集不同。 
   假设你的初始开发/测试集主要是一些成年猫的照片。你查看猫app，发现用户上传了比预期多很多的幼猫的照片。所以，开发/测试集的数据分布并不能代表你需要做好的实际的数据分布。这种情况下，更新你的开发/测试集，使其更具代表性。 
   ![这里写图片描述](http://oow6unnib.bkt.clouddn.com/myl-c2-0.jpg)
2. 你已经在开发集上过拟合了。 
   在开发集上反复评估想法的过程导致算法逐渐对开发集“过拟合”。当完成开发后，你将在测试集上评估你的算法。如果你的算法在开发集上的表现远好于在测试集上的表现，这意味着你已经过拟合开发集。这种情况下，更新开发集。 
   如果你需要跟踪团队的进度，你也可以在测试集上定期评估你的系统——每月或每周一次。但不要使用测试集来对算法做任何决定，包括是否回滚到上一周的系统。如果这样做，你将开始过拟合测试集，并且不能再依靠它来完全无偏见的评估系统的性能（你可能会在发表研究论文或做出重要商业决策是使用这个指标）。
3. 评估指标衡量的并不是项目所需要优化的东西。 
   假设对于你的猫app，你的评估指标是分类准确率。当前在该指标下分类器A优于分类器B。但是假设你尝试了这两种算法，发现分类器A会偶尔允许色情图片通过。那么即使分类器A准确率更高，偶尔的色情图片所带来的坏影响也意味着其表现是不可接受的。你需要做什么呢？ 
   这里，该评估指标不能辨别出对产品而言算法B比算法A更好这一事实。所以，你不能再相信该指标能挑选出最佳算法。是时候改变评估指标了。例如，你可以更改评估指标，严厉惩罚色情图片分类错误。我强烈建议你选择一个新的评估指标，并用新的标准来为团队明确定义一个新的目标，而不是在一个不可信的评估指标下处理太长时间，并恢复到手工选择分类器。

在项目中改变开发/测试集和评估指标是很常见的。拥有一个初始的开发/测试集和评估指标能帮助你快速迭代。如果你发现 开发/测试集和评估指标不再使你的团队在正确方向上前进，这不是什么大问题！只需要改变它们，并确保你的团队知道新的方向。