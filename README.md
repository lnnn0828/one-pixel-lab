# Season Detective · 季节小侦探

A small, playful classifier that uses **month and temperature** to predict **Spring, Summer, Fall, or Winter** in the Northern Hemisphere. It helps visitors explore how learning examples influence a prediction and see the evidence behind an answer.

一个简单、有趣的北半球季节分类器：根据**月份和气温**预测**春、夏、秋、冬**，帮助访问者理解学习例子如何影响预测，并查看答案背后的证据。

## Open and use · 打开与使用

1. Download this repository and unzip it, or use your existing local project folder. Double-click **[season-classifier.html](season-classifier.html)** to open it in Edge, Chrome, Firefox, or Safari. On GitHub, download the files first; the file listing shows source code rather than running the page.
   下载并解压仓库，或打开已有的本地项目文件夹。双击 **season-classifier.html**，用浏览器打开。在 GitHub 上请先下载文件，文件列表展示的是源码。
2. Choose a month, then move the temperature slider or type a number. Both controls stay synchronized and accept **−60°C to 60°C in 0.1°C steps**.
   选择月份，再拖动滑块或输入温度。两种输入方式保持同步，范围为 **−60°C～60°C，步进0.1°C**。
3. Read the calendar season and the model prediction. Below them, inspect the votes, the three nearest examples, and their distances. The full table shows all **24 learning examples, six per season**.
   查看月份对应的季节与模型预测，然后查看投票、三个最近例子及其距离。完整表格展示**24个学习例子，每季6个**。
4. Try April at **18.2°C**, then the **July at −5°C** button. Keep one input fixed and change the other to see how the evidence changes.
   试试**4月18.2°C**，再点击**7月−5°C**按钮。固定一个输入，改变另一个，观察预测证据如何变化。

The page is one self-contained HTML file and works offline. No API keys, paid services, installation, or build step are needed. `one-pixel.html` is the original starter lab.

页面是一个独立HTML文件，可以离线使用，无需API密钥、付费服务、安装依赖或构建。`one-pixel.html` 是原始入门实验文件。

## How it predicts · 如何预测

The classifier remembers 24 invented, labeled examples from an imaginary temperate Northern Hemisphere town. For a new input, it compares both the month and temperature with every example, selects the **three most similar examples**, and lets each cast one vote. The season with the most votes becomes the prediction. This method is called **3-nearest neighbors**.

分类器记住24个虚构的北半球温带小镇例子，每个例子都有月份、气温和季节标签。收到新输入时，它与所有例子比较月份和温度，选出**最相似的三个例子**，每个例子投一票，票数最多的季节成为预测。这种方法叫作**3近邻**。

A smaller distance means a closer match. A difference of three months has the same weight as a difference of 15°C. Months wrap around, so December and January are one month apart. If votes tie, the tied season with the closest example wins; exact distance ties follow the table order. Votes are evidence, **not probabilities**.

距离越小，例子越相似。相差3个月与相差15°C的影响相同；月份循环计算，所以12月和1月只差1个月。票数相同时，由最近例子所属的候选季节胜出；距离完全相同时按表格顺序决定。票数是证据，**不是概率**。

The separate calendar display uses a simple Northern Hemisphere meteorological-season rule: March–May is spring, June–August summer, September–November fall, and December–February winter. This display depends only on the month; it does not override the model's vote.

单独的月份季节显示采用北半球气象季节规则：3–5月为春季，6–8月为夏季，9–11月为秋季，12–2月为冬季。这个显示只由月份决定，不会覆盖模型的投票结果。

## A limitation I discovered · 我发现的一个局限

Unusual temperatures can confuse the model. For example, a freezing July can produce a prediction other than summer, even though July is summer under the calendar rule. Our small, invented training set cannot represent every location or unusual weather event. The page explains disagreements and flags inputs outside the examples' **−4.5°C to 33.2°C** range. It cannot tell whether an unusual temperature is a typing mistake or real local weather.

异常气温可能让模型困惑。例如，7月输入零下气温，模型可能预测成其他季节，但按月份规则7月仍是夏季。这个小型虚构训练集无法覆盖所有地区或异常天气。页面会解释预测与月份季节的分歧，并提示超出学习例子 **−4.5°C～33.2°C** 范围的输入。它无法判断异常气温是输入错误，还是真实的当地天气。

## Short development log · 简短开发记录

I used Codex to help build and revise the page. The two development checkpoints were saved after the changes were made.

我使用 Codex 帮助创建和修改页面，并在修改完成后补存了两个开发检查点。

| Commit | Checkpoint · 开发检查点 |
| --- | --- |
| `bc8357e` | Saved the original One Pixel starter files. 保存原始 One Pixel 入门文件。 |
| `7d9631d` | Added the bilingual season classifier with 12 examples, expanded temperature to −60–60°C, and separated the calendar season from the model prediction to explain unusual inputs. 加入双语季节分类器和12个例子，将温度范围扩大到−60～60°C，并区分月份季节与模型预测，解释异常输入。 |
| `ace44bf` | Added 0.1°C precision and a synchronized number input; expanded to 24 visible examples. Checked decimal entry, slider synchronization, presets, and invalid-input feedback in the browser. 加入0.1°C精度和同步数字输入框，扩充到24个可见例子；在浏览器中检查小数输入、滑块同步、预设按钮及无效输入提示。 |

## Credits · 致谢

Created by **Xinyan Luo** with help from **Codex**, based on the One Pixel ML assignment in [CPSC 1710 Labs](https://github.com/xiuyechen/cpsc1710-labs).

由 **Xinyan Luo** 在 **Codex** 的帮助下完成，基于 CPSC 1710 的 One Pixel ML 作业。

Original starter materials are by [Xiuye Chen](https://github.com/xiuyechen), developed with Codex, and shared under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

原始入门材料由 Xiuye Chen 使用 Codex 开发，按 CC BY 4.0 许可共享。
