## Development Process (作为developer)
- Dev阶段使用本地环境，可能使用docker
- Test/Integration
- UAT(User Acceptance Testing) 需要DevOps帮助 测试是否满足Acceptance Criteria

## Terraform + Lambda + API Gateway + Nodejs架构
- 尝试这个模式
- Cloudformation
- Lambda很切合Nodejs

## 流程
- 按feature创建branch
- 发送pull request (描述一定要专业)
- 将ticket移动到code review列
- Code review approval后，进行merge
- 将ticket移动到testing，由ba ui等进行测试，确定满足所有Acceptance Criteria
- 有时会出现code conflict，需要自行解决

## Jira相关
- 创建时选择Scrum
- 通过ticket可以直接创建branch
- 可以直接从master检出branch, 也可以创建一个dev branch

## ticket相关
- 有一个ticket作为一个界面的底座，这类ticket通常较小，要提前完成，否则会block后续的ticket
- 界面上每一部分作为不同ticket分别开发
- 尽量分开开发减少conflict
- 如果需要，一个ticket可以创建多个branch
- 要经常进行rebase 最好每天
- squash rebase

## Rebase流程
- 第一步:切换到正在开发的branch
- 第二步:pull最新代码到本地分支
- 第三步:从master rebase本地
- 第四部:push到远程
- [tutorial: atlassian git rebase vs merge](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
