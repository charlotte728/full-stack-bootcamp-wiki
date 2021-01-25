**Lightman：** 然后你们所有组的code review，我们会安排Tutor @Heming  来看大家的代码，每个组的组员·在pull request的时候，不但要把所有的组员加上也要把tutor @Heming 加上，tutor会帮助所有的组看代码，heming不讲课。

**提问：** 先把heming拉到我们组的bitbucket，然后每个pull request在heming打了approve之后才能merge吗？

**Lightman：** 然后除了heming’外，所有的组的代码也都可以找老师看，点播也比较快，所有的pull request应该根据代码规范来做，pull request后，你们可以有至少两个人approval后，才能merge，然后先要review代码，comments问题的地方，改完之后reviewer有两个人点了approval，之后才能merge，不是review整个项目的代码，所有的代码都是在pull request阶段review代码，如果已经merge到master了，相当于代码已经属于 production级别的代码了。

**锤姐：** code review都是merge之前必须做的，直接merge进去，就成了tech debt。

**Lightman：** 各位组长明白吗，review代码是要在pull request阶段review，不要一上来就merge，到时候代码问题会很大，然后没有人能够提高。pull request阶段可能能持续2-5天没有办法merge。然后branch代码要每天至少一次commit，和要让branch在rebase on master，保持你们的branch是最新的代码。

**提问：** 这样如果每天做的话，组长的工作量很大，需要写自己的部分，还要review其他人的部分，如果代码不合规，还要与组员一起解决？

**Lightman：** code review是所有的组员要进行，不只是组长。

**锤姐：** team里每个dev都有code review的职责，一个dev写了，另外的dev们review。

**Lightman：** review代码，维护repo是每个developer最最基本的素质要求。

**提问：** 一个pull request里，组员都可以点approve，在xx行代码下写评论，如果一个组员有点approve或者写评论，就说明他参与了review，是这样吗？

**Lightman：** 就是希望所有的developer都要review代码，然后看看代码有什么问题么。个人觉得代码可以通过就点approval。

**Lightman：** 比如常见错误： typo，拼错了单词；用for循环，没有用es6的循环方式；function或者class写的太冗长，没有结构，需要重构；api没有按照swagger写comments；function name之类的命名不准确，看不懂function做什么，比如有些css已经写过了定义过了，比如button，应该css可以直接用，而不是另一个developer又写了一遍。

**Lightman：** 建议api部分和前端部分都要写unit testing，尤其是API部分。最后项目快做完的时候，就要开始用aws，后端放ec2，前端放s3，如果可以用CI/CD的话推荐build起来。最后项目deliver需要在route 53再买个域名。

**锤姐：** Pull Request 之后dev分头去review这是一种方式。还有另一种方式可以是大家一起开个会，专门做code review，这样做几次，大家就能够对code review的标准有个统一的认知。一般刚开始的可以试试一起review，毕竟review meeting也是成本很高的（对一个公司而言）

**锤姐：** https://codereviewchecklist.com/  给大家参考。按照checklist做的时候，tips是，每次只看一个点，看完一遍code，再进行第二个点。如果逻辑错误，单元测试都不能通过，就不要commit。注意别把名字和路径写错，typo是非常常见的错误，而且有的时候真的不那么容易发现，如果自己测试不过，就有PR的话，这种typo的问题在code review的时候也不能很容易的就发现了，只有大家一起debug才能解决问题。

