# OhEarningsCal

<a href="https://trendshift.io/repositories/8148" target="_blank"><img src="https://trendshift.io/api/badge/repositories/8148" alt="jason5ng32%2FOhEarningsCal | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>

这个项目本来是我自用的一个小工具，功能是，将我关注的美股公司的财报日程，自动导入到我的日历（比如 Google Calendar）中。

啊，我就是不喜欢打开炒股 app 看，我就是喜欢在日历中看。

或许这个工具对你也有用，所以我把它开源了。

代码很粗糙的，但是能用（毕竟我是个产品经理啊）。

## 直接使用

打开 [https://stock.retire.money/](https://stock.retire.money/)，找到已经生成的 ics 文件，复制链接，然后在你的日历软件中，添加一个新的日历，输入这个链接，就可以了。

备注：仅仅包含美国市场的财报日历。日历内容只包含当天前后 30 天的，再多其实没有意义。

## 关于更新

项目已经设置了使用 Github Actions 自动更新：

1. 每天 2 次从纳斯达克定时抓取未来 30 天的财报日历
2. 每天 2 次生成对应的 ics 订阅文件

通常，更新会自动执行。不过，实测发现，有时候 Github Actions 会出现延迟，有时候甚至可能因为高负荷而错过执行。

如果你发现了这种情况，可以通过 Github API 触发手动执行。

## 关于 ics 清单

默认情况下，程序会生成 6 个 ics 文件，分别是：

1. `all.ics`: 包含所有公司的财报日历
2. `nasdaq100.ics`: 包含纳斯达克 100 指数成分股的财报日历
3. `sp500.ics`: 包含标普 500 指数成分股的财报日历
4. `dow30.ics`: 包含道琼斯 30 指数成分股的财报日历
5. `customstock.ics`: 项目作者，也就是我自己，关注的一些个股的财报日历
6. `selected.ics`: 2-5 的合集

## 自己部署

如果你想自己部署这个项目，可以参考以下步骤：

实际上，程序本身是可以在本地使用 npm 进行部署到，这部分代码我也已经写了，不过我还是比较鼓励使用 Github 进行部署并执行自动化。

1. Fork 这个项目
2. 自行修改 `api/datas/cusomstock.json` 文件，将你关注的个股代码添加进去
3. 在 Github 项目的环境变量中，根据 `env.example` 创建对应的环境变量
4. 看看你创建的名称和 `github/workflows` 的 yml 文件中环境名称和对应的环境变量名称是否一致
5. 然后就可以了
