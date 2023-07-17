# go-clean-arch-sample
this is a sample that combine go-clean-arch &amp; go-standard-layout

### `/cmd`
根据 [go-standard-layout](https://githu.com/golang-standards/project-layout/blob/master/cmd/README.md) 里面的 `/cmd` 的描述，该目录下是主要的应用程序， `/cmd` 目录下的项目。

例如 (`/cmd/incu`) 里面有一个 `main` 函数，引入 `/internal` 和 `/pkg` 。

### `/pkg`
同样的也是根据 [go-standard-layout](https://githu.com/golang-standards/project-layoufat/blob/master/cmd/README.md) 放入外部程序可以用的代码。

例如 `/pkg/logs` 封装一些通用 `logs` 的代码 `/pkg/push` 封装一些通用的极光推送代码之类的。可以让外部程序调用的代码。
但是如果日志和极光推送代码和项目强绑定的话，请放到 `/internal` 下。 

### `/internal`
也是根据 [go-standard-layout](https://githu.com/golang-standards/project-layoufat/blob/master/cmd/README.md) 私有的应用程序代码库。这些是不希望被其他人导入的代码。在该目录下进行实际项目代码的开发。

例如 `/internal/controller` 放入项目相关的 controller 层代码。

#### `/internal/configs`
放入项目的对应的所有配置，MySQL、Redis、之类放入到该目录下。

#### `/internal/domain`
根据 [go-clean-arch](https://github.com/bxcodec/go-clean-arch) 这里存放着不同模块 `delivery` `usecase` `repository` 的 `interface` 的定义，以及不同模块的 `model` 定义。

例如 `/internal/domain/user.go` 里面存放着 `user` 的 `model` 定义，以及 `user_respository` `user_usecase` `user_delivery` 层对应的接口定义。

##### `/internal/domain/mocks`
根据 [go-clean-arch](https://github.com/bxcodec/go-clean-arch) 这里存放对应 `usecase` `repository` 层相关代码的 mocks 和 subs。

例如 `/internal/domain/mocks/user_repository.go` 存放对应 `user_repository` `mock` 的代码。

#### `/internal/pkg`

根据 [go-standard-layout](https://githu.com/golang-standards/project-layoufat/blob/master/cmd/README.md) 放置在项目中共享的代码模块。

例如 `/internal/pkg/push` 可以放入和代码强绑定的极光推送代码模块。

#### `/internal/user`

这是一个例子目录，根据 [go-clean-arch](https://github.com/bxcodec/go-clean-arch) 表示 `/internal/user` 下是 `user` 板块相关的代码。

##### `/internal/user/delivery`

放置的是 `controller` 层相关的代码，以及 `user` 板块的 `router` 配置。

##### `/internal/user/usecase`

放置的是 `service` 层相关的代码，具体业务逻辑的代码。

##### `/internal/user/repository`

放置的是 `dao` 层，数据库交互的代码，可以 以不同数据库名字名字结尾表示不同的数据库实现 `repository` `interface` 

例如 `/internal/user/repository/user_mysql.go` 表示是 `MySQL` 实现 `user` 板块的 `repository` 层。
    `/internal/user/repository/user_mongodb.go` 表示的是 `MongoDB` 实现 `user` 板块的 `repository` 层。

