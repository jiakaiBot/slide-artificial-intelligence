---
# 标题
titleTemplate: "人工智能课程汇报"
# 图标
favicon: "https://static.gujiakai.top/static/slide/deep-learning/images/favicon.png"
theme: seriph
# 背景图像
background: https://static.gujiakai.top/static/slide/artificial-intelligence/images/portrait-of-edmond-belamy.webp
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## 人工智能课程汇报
# persist drawings in exports and build
drawings:
  persist: false
download: true
---

## 基于文本转图像技术的综述

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br mb-25 mr-13 flex gap-2">
 汇报人：顾佳凯
</div>

<div class="abs-br m-15 mr-3 flex gap-2">
汇报日期：2022.6.24
</div>

<div class="abs-br mr-10 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/gujiakai-dev/slide-artificial-intelligence" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
大家好，今天我汇报的主题是基于文本转图像技术的综述。
这里面涉及到一项目前人工智能领域较火的技术—文本转图像。

什么是文本转图像呢？顾名思义，就是你给出文本提示信息，计算机根据你的文本提示信息生成相应的图像。
幻灯片封面是全球第一幅被拍卖的人工智能创作的图像，这幅图像在2018年以40多万美元的价格成交。

该图像使用GAN算法生成。
-->

---
preload: false
---

# 一、文本转图像技术简史
<div grid="~ cols-2 gap-4">
<div>

- 2015年，文本转图像技术首次被提出，研究团队认为该技术未来潜力无限。
- 2018年，第一幅人工智能创作的图像—Edmond de Belamy，以40多万美元的价格售出。
- 2021年，OpenAI推出DALL·E。
- 2021年，清华大学（唐杰团队）、阿里巴巴达摩院、北京智源人工智能研究院推出CogView。
- 2021年底，百度推出ERNIE-VILG这一全球最大中文跨模态生成模型。
- 2022年4月，OpenAI推出DALL·E 2。
- 2022年5月，Google Brain推出Imagen。

<br/>

[清华大学科研团队成员知乎回答](https://www.zhihu.com/question/438082738)

</div>
<div>

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/warriors.webp" class="absolute bottom-15 right-20 w-65">

<div v-if="$slidev.nav.currentPage === 2"
  v-motion
  :initial="{ x: 500}"
  :enter="{ x: 225,
            y:397,
            transition:{
              delay:1000,
          }}" class="opacity-50 text-base">
  
  Wombo生成的图像

  </div>

</div>
</div>

<!-- 
首先，我来介绍一下文本转图像技术的简史。
......

其中不得不提一嘴清华大学的科研团队，我在知乎上看到了他们团队大哥的回答，
被他的科研精神所折服。大家如果有兴趣的话，可以观摩一下这位大哥的知乎回答，
幻灯片的链接，放在最后面了。

6月17日，金州勇士夺得了NBA总冠军。因为我是勇迷，所以那天我用wombo这款在线工具
创作了一幅关于金州勇士的图像。当时我在文本框里面输入的提示信息是：Golden Gate Bridge、
Warriors、Summer，不到10s钟，就生成了右边这张图像。
 -->


---
preload: false
---

# 二、Zero Shot Learning(零样本学习)

## 1.原理

<div grid="~ cols-2 gap-5">
<div>

在深度学习领域，纯监督学习需要足够多的样本才能训练出足够好的模型，如利用猫狗训练出来的分类器，只能对猫狗进行分类，其他物种无法识别。
这样的模型显然不符合我们对人工智能的终极想象，我们希望机器具有推理能力，能识别新类别。

而Zero-shot learning就能让机器具有推理能力，实现真正的智能。

举一个简单的例子来说明零样本学习。

某个周末，爸爸带小明到动物园玩，看到了马，爸爸告诉他：“这是马。”之后又看到了老虎，告诉他：“看，这种身上有条纹的家伙就是老虎。”
最后，又带他去看了熊猫，对他说：“你看，熊猫是黑白色的。”
</div>
<div>

然后，爸爸给小明安排了一个任务，让他在动物园里找一种叫斑马的动物，由于小明没有见过斑马，于是爸爸给他讲了一下斑马的大概情况：
“斑马形状像马，身上有老虎一样的条纹，而且它像熊猫一样是黑白色的。”

结果，根据爸爸的描述，小明在动物园里轻松地找到了斑马。

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/zebro.webp" class="absolute bottom-30 right-15 w-100">

<div v-if="$slidev.nav.currentPage === 3"
  v-motion
  :initial="{ y: 300}"
  :enter="{ x: 150,
             y:120,
             transition: {
             delay: 1000,
          }}" 
  class="opacity-50 text-base">
  由提示找到斑马
  </div>
</div>
</div>

<!-- 
接下来，我将简要介绍文本转图像这一技术涉及到的技术点及其应用。
第一个技术点是：零样本学习。

前一段时间，优必选的工程师来线上授课，教我们用opencv实现识别狗，用到的是纯监督学习。
当时用到了几百张图片，postive、negative文件夹......

......
 -->


---
layout: image-right
image: https://static.gujiakai.top/static/slide/artificial-intelligence/images/dalle.webp
preload: false
---

## 2.应用

OpenAI的DALL· E、DALL·E 2、Google Brain的Imagen就采用了零样本学习。

人类在文本提示框中输入想要生成图像的对应文本提示信息，
文本提示信息可能是这些模型从来没有学习过的事物，但这并不会妨碍图像的生成，模型会使用零样本学习来预测文本提示信息对应的图像。

如你输入的文本提示信息为——“穿着太空服的浣熊”，这在现实世界中并不存在，但模型会将太空服、浣熊的特征进行整合，生成文本提示信息对应的图像。

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/raccoon.webp" class="absolute bottom-8 left-60 w-35">

<div
  v-if="$slidev.nav.currentPage === 4"
  v-motion
  :initial="{ x: -300 }"
  :enter="{ x: 15, 
            y:50,
            transition:{
              delay:1000,
          }}" 
          class="text-normal opacity-50">
  由DALL·E mini<br/>
  生成的太空浣熊图
</div>

<!-- 
零样本学习的应用......
这张图片是由开源项目DALL·E mini生成的太空浣熊图片，看起来还挺逼真的。
-->

---
preload: false
---

# 三、GPT-3

<div grid="~ cols-2 gap-4">
<div>

## 1.原理

GPT-3(Generative Pre-trained Transformer 3)，是一个源自OpenAI的自回归（预测自己）语言模型，给定一些输入文本，它可以预测接下来你想输入的内容。

该模型设计基于Google开发的Transformer模型。GPT-3的神经网络包含1750亿个神经，为全世界参数最多的神经网络模型。

去年GitHub推出的Github Copilot这一人工智能编程工具，就用到了GPT-3模型。

编程时，刚定义完函数，GitHub Copilot就自动预测出该函数对应的函数体内容，如果符合你的预期，一个Tab键就解决了函数体的编写，这不得不让人感慨人工智能的强大。

</div>
<div>

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/github-copilot.webp" class="absolute bottom-15 right-95 h-20">

<div
  v-if="$slidev.nav.currentPage === 5"
  v-motion
  :initial="{ x: 500 }"
  :enter="{ x: 125, 
            y:340,
            transition:{
              delay:1000,
          }}" 
          class="text-2xl opacity-50">
  GitHub Copilot
</div>

## 2.应用

DALL·E是GPT-3的120亿个参数版本（GPT-3的扩展），经过训练，可以使用文本-图像对数据集，从文本描述中生成图像。

在很多方面，GPT-3像是一个自动补全程序：从几个单词或句子开始，预测接下来可能出现的单词或句子。DALL·E只是用像素代替了文字而已。当它收到了一个文本提示，它通过预测接下来最有可能出现的像素字符串来匹配该文本，从而产生一幅图像。


</div>
</div>

<!-- 
第二个技术点是GPT-3模型，它是......

不知道大家编程有没有用上GitHub Copilot这一ai工具，目前这款工具已经在6月22号正式上线，
定价为100$/m，如果你通过了GitHub的学生认证，可以免费使用。

GitHub Copilot就用到了GPT-3模型，你刚写了一部分代码或者注释，它就会预测接下来你想要的输入。
这个工具使用GitHub上所有公开仓库的代码作为训练集。

GPT-3模型在文本转图像技术中的应用是OpenAI推出的DALL·E模型，当DALL·E收到了一个文本提示，它通过预测接下来可能出现的像素字符串来匹配该文本，从而产生一幅图像。
 -->

---
class: px-20
preload: false
---

# 四.Diffusion(扩散模型)P

## 1.原理

<div grid="~ cols-2 gap-4">
<div>

扩散模型的执行流程：

存在一系列高斯噪声（T轮），将输入图片x<sub>0</sub>变为高斯噪声x<sub>T</sub>，而扩散模型负责将x<sub>T</sub>复原回图片x<sub>0</sub>。
要强调的是，扩散模型中噪声x<sub>T</sub>与图片x<sub>0</sub>是同维度的。

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/diffusion.webp" class="absolute bottom-35 w-100">

<div v-if="$slidev.nav.currentPage === 6"
  v-motion
  :initial="{ y: 300}"
  :enter="{ x: 100,
            y: 125,
            transition:{
              delay:1000,
          }}" 
  class="opacity-50 text-base">
  扩散模型执行流程图
</div>
</div>

<div>

下面用一个例子来说明扩散模型。

为了训练一个扩散模型，我们首先将高斯噪声添加到数以千计的图像中，逐步增加噪声，直至得到各个方向上高斯噪声尽可能接近的图像。

接着用扩散模型复原图像，当扩散模型复原图像时，学习的过程发生了，它会尽可能创建一个逼近原图像的图像，故扩散模型也被称为生成模型。

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/diffusion-demo.webp" class="absolute bottom-20 w-100">

<div v-if="$slidev.nav.currentPage === 6"
  v-motion
  :initial="{ y: 300}"
  :enter="{ x: 25,
            y: 125,
            transition:{
              delay:2000,
          }}" 
  class="opacity-50 text-base">
  梅花图像经添加噪声，再去除噪声，生成新图像。
</div>

</div>
</div>

<!-- 
第三个技术点是扩散模型，它的执行流程是......
 -->

---
preload: false
---

## 2.应用

<div grid="~ cols-2 gap-4">
<div>

DALL·E 2使用了扩散模型，从一个点开始，以越来越多的细节填充图案。

Google Brain的Imagen模型不仅包含了扩散生成模型的部分，还包含超分辨率扩散模型，利用该模型可以实现增加图像的分辨率。

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/diffusion-gif.gif" class="absolute bottom-20 w-50 left-60">

<div v-if="$slidev.nav.currentPage === 7"
  v-motion
  :initial="{ x: -300}"
  :enter="{ x: -20,
            y: 100,
            transition:{
              delay:1000,
          }}" 
  class="opacity-50 text-base">
  使用扩散模型，<br/>
  从一个点开始，<br/>
  以越来越多的细节填充图案。
</div>


</div>
<div>

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/imagen-structure.webp" class="absolute bottom-20 w-100 right-20">

<div v-if="$slidev.nav.currentPage === 7"
  v-motion
  :initial="{ y: 600}"
  :enter="{ x: 100,
            y: 400,
            transition:{
              delay:2000,
          }}" 
  class="opacity-50 text-base">
  Imagen使用超分辨率扩散模型，<br/>
  增加图像的分辨率。
</div>

</div>
</div>

<!-- 
扩散模型的应用是......
 -->


---
preload: false
---

# 五、不足与挑战

<div grid="~ cols-2 gap-4">
<div>

## 1)不足

使用文本转图像技术的不足之处是生成的人物图像会掉san值（人看到了对心理造成严重的负面冲击的画面，就可以说san值狂掉，表示自己特别害怕）。
<div v-if="$slidev.nav.currentPage === 8"
  v-motion
  :initial="{ y: 800}"
  :enter="{ x: 50,
            y: 350,
            transition:{
              delay:3000,
          }}" 
  >
<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/beautiful-girl.webp" class="absolute bottom-15 w-70">
</div>



</div>
<div>

## 2.挑战 

文本转图像技术面临的问题
- 版权问题
- 代表的文化片面
- 艺术家的忧虑
- 不良图像


</div>
</div>

<!-- 
下面这部分，我将介绍文本转图像技术存在的不足与挑战
该技术的不足之处是......
下面这张图片由DALL·E mini生成，我输入的文本提示信息是beautiful girl。
但下图看上去有点恐怖，眼睛变形严重。

该技术面临的挑战有以下4点。
- 版权问题
如果大众提供的文本提示信息中包含艺术家的名字，则生成的画作会复制艺术家的风格。那这幅画版权到底归谁？即谁才是画家？是计算机？还是机器模仿风格的画家？亦或是提供文本提示信息的大众。
- 代表的文化片面(西方国家的模型一般只接受英文输入，清华大学搞出来的cogview只接受简体中文输入，cogview2，简体中文和英文都支持)
一些厂商使用的数据集未知（如OpenAI），但我们知道互联网整体上是偏向于英语和西方
世界的。因此AI画出来的图像并没有代表整个世界的文化。
- 艺术家的忧虑
目前而言，文本转图像技术虽已经让人称叹，但还没有超越人类艺术家的水平。随着技术的进一步发展，难免会有超越人类艺术家的可能。如果真的有这么一天，艺术家会不会丢了饭碗呢？
- 不良图像
文本转图像技术，会产生很多不良图像。有些图像可能对大众而言，具有误导性；有些图像可能包含色情、暴力、血腥的内容。这些都亟待掌握文本转图像技术的厂商想方设法去完善。
 -->

---
preload: false
---

# 六、总结与展望

<div grid="~ cols-2 gap-4">

<div>

## 1)意义

文本转图像技术的意义在于，它使我们任何人都能够指挥机器，想象我们希望它看到的信息。文本提示信息消除了想法和图像之间的障碍，最终消除了视频、动画和整个虚拟世界之间的障碍。

<img src="https://static.gujiakai.top/static/slide/artificial-intelligence/images/ai-artist.webp" class="absolute bottom-12 w-100 left-15">

<div v-if="$slidev.nav.currentPage === 9"
  v-motion
  :initial="{ x: -500}"
  :enter="{ x: 125,
            y: 250,
            transition:{
              delay:1000
            }}" 
  class="opacity-50 text-base">
  AI机器人成为了画家。
</div>

</div>

<div>

## 2)展望

其实，艺术家们大可不必杞人忧天。有时间去焦虑机器人是否会抢了自己的饭碗，还不如多去学习并掌握文本生成图像这种技术，提升自己的知识面，这样才能在未来的人工智能渗透中站稳脚本，不被时代淘汰。

在我看来，这项技术的未来前景一片光明。文本转图像技术成熟后，会激起艺术领域的又一次百家争鸣，艺术品会以一个极快的增速成长，人人皆画家的时代必将到来。

- [云幻灯片链接](https://slide-ai.gujiakai.top)<br/>
- [汇报补充资料链接](https://flowus.cn/jiakai/share/793c503c-2e38-492d-b725-6d11bf3062da)<br/>
- [项目源文件链接](https://gitee.com/gujiakai/artificial-intelligence-homework)

</div>
</div>

<!-- 
文本转图像技术的意义在于...

最后给出我的展望...

旁边左下角的这幅画是我用google disco diffusion模型生成的图像，当时我给出的文本提示信息是
一个AI机器人成为了画家。图像生成的过程就可以明显感知到diffusion模型在起作用。可以点击
这张幻灯片右侧的第2个链接，链接跳转的页面里面有我前几天使用国内外模型生成图像的案例，以及左侧
这张图像的生成过程视频，生成这张图像一共花了我20多分钟，经过后期的剪辑，我把生成该图像视频时长缩减为
一首歌曲，感兴趣的同学可以去拜访一下。

感谢大家的聆听！
 -->

