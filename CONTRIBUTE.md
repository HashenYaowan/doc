# 贡献指南

如果您还不想被学校开盒, 那么下边是一些匿名协作基本要求, 请知悉.

如果您对下面的文字具有理解困难, 可以向您信任且能够理解下文的人要求代为投稿.
如果您足够信任 @HashenUPill 且敢于冒该帐号被其他人恶意抢占的风险, 您可以直接向组织邮箱发送邮件说明投稿内容.

请尽量不要在邮件沟通中透露个人信息, 过多的信息暴露对暴露方和被暴露方都是风险.
请知悉邮箱发送方是非常容易被伪造的, 请不要轻信任何来自本组织的邮件, 尤其是涉及个人信息的钓鱼邮件.
特定情况下, 本组织会公开一些短期的 GPG digest 以在特定时刻以 GPG 签名之内容 (邮件/commit) 证明身份, 但不是现在.  

请不要过于相信本仓库中的内容, 尤其是当其以特定 commit 的链接方式出现时, 
伪造 GitHub 仓库中特定人物的特定 commit 不仅可能, 甚至是容易的.

## 邮箱与 GitHub 帐号

显然, 您不会希望使用学校给您提供的 `@*.hit.edu.cn` 邮箱来为本项目贡献的. 
请前往一些注册宽松的境外邮件服务提供商注册一个 (或者一些!) 帐号, 
帐号的名字显然也不能是您的常用 ID, 最好与其毫无关系, 而非简单的变形.

本指南推荐使用 [ProtonMail](), 其为欧洲原子能组织 (CERN) 开发的加密邮件服务,
虽然它之前也有一些漏犯罪数据给 (国外) 政府机关的黑料, 但是对于学校而言应当足够安全.
帐号名可以随机使用字母拼凑而成, 比如 "LiTianSuo" 之类, 
或是直接使用校内知名人物的名字 (比如您某位不甚友好的授课老师) 以增加追查成本.

同理 GitHub 帐号请使用您刚刚注册的邮箱注册, 请绝对不要使用您的主力 GitHub 帐号.
GitHub 帐号中填充的信息请尽可能地少, 头像也请使用随机生成的, 避免二次元头像等具体特征.

## SSH 与 `git config`

显然, 您也不会希望您的大名就直接出现在 commit 信息中. 
请创建新的 ssh 密钥对并 **仅** 将该密钥对用于向本项目贡献中.
同时, 请 **不要** 直接使用 `git clone` 来获取本项目, 
以防止您的全局 `user.name` 和 `user.email` 被无意中泄露.
请充分利用 `git config` 的 pre-repo 设置功能.

下面是可供参考的步骤:

```bash
# 生成新的密钥对, 存放于 ~/.ssh/pill 和 ~/.ssh/pill.pub
ssh-keygen -t ed25519 -f "${HOME}/.ssh/pill"

# 创建新的文件夹
cd "一个合适的文件夹"
mkdir pill
cd pill

# 初始化 git 仓库并进行相关设置
git init
git config user.name "您新注册的 GitHub 帐号名"
git config user.email "您新注册的邮箱"
# 防止无意中使用 GPG 签名
git config commit.gpgsign false 
# 指定使用且仅使用您新生成的密钥对
git config core.sshCommand "ssh -i ${HOME}/.ssh/pill.private -o IdentitiesOnly=yes" 

# 添加本仓库为远端并进行相关操作
git remote add origin git@github.com:HashenYaowan/hsyw.github.io.git
git fetch origin
git checkout -b main origin/main
git branch --set-upstream-to=origin/main main
```

您可以将密钥对以及本仓库的副本存放于移动介质之中, 并在紧急情况下将其物理销毁.

## 图片处理

请审慎地对待您上传的每一张照片与截图. 图片是最容易被识别的信息之一.

请检查图片的 EXIF 元信息, 并使用[工具](https://www.verexif.com/en/)将其清除,
尤其是微信内的截图与您手机摄像头拍摄的相片.

对于室外相片而言, 请充分考虑拍摄时位置的人流量与您拍摄的姿势是否亮眼.
根据室外照片的光照和拍摄角度, 有可能会被识别出您的身高和拍摄时间与地点, 
随后便可能根据校内或校外的监控找到您. 请避免照片中出现特定角度的光照之类的非常具体的特征.

对于室内相片而言, 请避免拍到您的与他人的任何个人物品.

对于截图而言, 请尽可能考虑隐水印等问题. 飞书的截图中会包含您的飞书 ID 与手机号码, 
微信小程序中的截图会包含微信小程序 ID, QQ 中的截图相对安全, 但是也不要掉以轻心. 
请注意马赛克是可以使用 AI 等技术猜测出下面的内容的, 请不要使用马赛克遮盖您的个人信息, 而应当使用纯色块.
或者, 您也可以使用马赛克遮盖错误的个人信息. 人对于自己花费了精力获取的情报往往深信不疑, 可借此误导追查者.

目前处理隐水印的方法包括: 

- 尽量减少截图范围
- 使用拍屏而不是截屏
- 使用他人的设备进行截屏
- 在图片处理软件中针对色调和饱和度进行调整
- 扣掉了文字之外的所有部分, 随后将文字迁移至另一张纯色图片中

请注意上面的方法都不是完美的, 即使全部完成, 您仍然可能因为截图而被发现, 在上传截图时请做好心理准备.

## 文字风格

请不要使用您惯用的语言风格与颜文字等特征, 或恶意混入其他人的风格特征以增加追查成本.
如果您不确定您的风格是否会被他人识别, 请尽可能地使用简单且礼貌 (或者是阴阳怪气) 的语言风格, 
或使用任意 AI 模型对您的文字进行润色. 

请避免在文字中提及任何能直接或间接反映您个人信息的内容, 除非不可避免.
譬如, 在本指南中, 编写者就不可避免地令人知晓其为本校相关人生 (知道学校邮箱格式), 且具有一定技术水平.
当您在文字中提及任何您从公开渠道看到的信息时 (譬如从某个 QQ 水群中看到的特定人发送的 "妙句"), 
请仔细思考看到过该信息的人士数量. 如果该信息仅被少数人看到, 那么请尽可能地改写该信息.

要清楚地知悉该文档本身也是公开的, 因此学校方面很可能会根据该文档反向追查, 祝您好运.
