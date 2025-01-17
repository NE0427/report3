# 【金融风控项目-05】：信贷业务审批流程介绍
11124101林宥慈 11124102林宥君

# 1 信贷业务审批流程

![1](https://github.com/user-attachments/assets/ba9aad5a-3fa0-4662-b264-504f72a710b3)
![Screenshot_37](https://github.com/user-attachments/assets/09bd3719-ce22-448b-ac4c-4fc92b3ab293)



准入策略、信用风险策略、反欺诈策略：一系列的if-else条件，满足条件可以继续进行下一步，不满足条件就直接拒绝。

# 1.1 互联网金融风控体系组成
互联网金融风控体系主要由三部分组成：

用户数据：用户基本信息、用户行为信息、用户授权信息、外部接入信息

策略体系：反欺诈规则、准入规则、运营商规则、风险名单、网贷规则

机器学习模型：欺诈检测模型、准入模型、授信模型、风险定价、额度管理、流失预警、失联修复

# 1.2 用户数据
用户注册：上传个人信息
身份核验：身份证、银行卡、手机号、人脸识别等
授信协议：授权获取央行征信等

用户数据：

![f6fb2cf6864c48fbb90160328bec7143](https://github.com/user-attachments/assets/4b237f5c-8f3f-43f5-9a84-e9d4b9501577)

![螢幕擷取畫面 2025-01-05 025109](https://github.com/user-attachments/assets/532dc422-4c93-4a3c-a361-b134c114a397)

# 1.3 特征库构建
数据平台和特征库是实时联动的：

数据平台可以根据特征库的变量体系需求进行数据产品的采集
特征库也可以根据数据平台可提供的数据维度进行变量衍生、特征库扩充
特征库：正是用于衔接丰富的数据资源与业务场景，特征库构建的意义在于将采集到的原始数据赋予业务含义。

特征库可以简单的理解为是一张具有业务逻辑的数据字典表格。根据特征库，可以将数据平台中非结构化数据标准换为能够表征风险水平的字段表。
 ![89bb3aee958345c1a54c544eddc9ed00](https://github.com/user-attachments/assets/2b258221-119f-4755-8d81-2559d4062d82)


# 1.5 身份验证
实名认证：二要素、三要素、四要素验证

短信认证：验证码

活体检测：人脸识别

地址校验：常住地址、单位地址、户籍地址、手机号归属地、IP地址、GPS定位、基站定位

其他校验：运营商信息、车辆信息、邮箱信息

# 1.6 策略及模型体系
![443caf4abdcf4546a8ad2c7279ed275d](https://github.com/user-attachments/assets/6bc33593-b8c1-4e34-ba3b-1cc75cea5f4a)



# 1.6.1 准入策略
年龄：年龄太小或太大的用户禁入
区域：特定区域的用户禁入
重复申请：短时间内多次申请或已存在在途订单的用户禁入
频繁拒绝：历史多次申请被拒绝的用户禁入
异常关联：身份证、手机号关联异常的用户拒绝
联系人关联风险：联系人有在途订单或历史申请多次获历史申请被拒绝多次的用户禁入
行内黑名单：命中行内黑名单的用户禁入
历史逾期：历史逾期严重的用户禁入
# 1.6.2 分群策略
线上客群时常有较大变化，基于精准的用户画像和用户分群可以制定差异化策略， 取得更好的风控成果
 ![3cb07f0566ad44ce937560b0454c7e17](https://github.com/user-attachments/assets/409b8eb0-a904-488b-8cd7-7fcb84c5589a)



# 1.6.3 反欺诈策略
风险名单：失信、违约、欠税等不良行为记录名单

设备指纹：通过技术手段获取，定位设备的唯一性

用户画像：IP画像、手机号画像、APP使用习惯等

多头借贷：跨平台大数据，包括多头申请、多头共债等

运营商报告：在网状态、在网时长、实名认证等

人行征信：历史查询（次数、机构数等）、历史违约记录（最长逾期、被追偿信息等）、公共信息（民事判决、欠税等）等

数据埋点：用户操作行为，用户操作行为时间戳，操作环境信息，操作设备信息等

欺诈标签：欺诈类型标签，欺诈手法标签，认定方式标签等

涉赌情况：赌博类App、彩票类App数量等

# 1.6.4 信用风险策略
人行征信：查询记录、信贷交易违约信息等

百行征信：多头申请、贷款逾期记录、查询历史等

多头借贷：多头申请、多头共债等

运营商报告：话费套餐、月消费账单金额、充值记录等

公积金：缴存单位数、缴存时长、缴存金额等

消费记录：银联消费、电商消费记录等

信用分险策略开发:决策树(CART回归树)
![2006e7fd5a73435bb91dc64b55be377b](https://github.com/user-attachments/assets/7210b1ab-55cc-4adf-b05f-4c1776c71845)

 
# 1.6.5 信用评分卡
数据维度: 同信用风险策略

开发方法: 基于逻辑回归 和 集成学习模型

逻辑回归（Logistic Regression）
XGB（XGBoost，eXtreme Gredient Boosting）
LGB（LightGBM，Light Gredient Boosting Machine）
# 1.6.6 策略模型迭代优化
规则和模型为信贷业务提供了决策的依据，能够规避绝大多数风险点

但没有完全适合任何场景、任何信贷产品和任何客群的风控策略，因此需要对策略进行更新迭代，不断优化。

优化的依据主要来自贷后的资产监控、回收监控、规则模型监控等，监控报表能够直观地呈现业务的变化情况

策略人员可以判断出信贷产品的特点、各渠道客群质量、规则模型适配性等，综合判断得出管理措施，调整、完善策略。

# 1.6.7 风控策略与风控模型之间的区别
风控模型和风控策略都是信贷风险管理的重要组成部分，但是它们的角色和功能是不同的。风控模型为决策提供了量化的风险评估，而风控策略则定义了如何做出具体的业务决策。

风控模型：通常由数据、算法和模型训练过程组成。
风控策略：可能包括一系列的业务规则、阈值、策略框架和决策流程。
# 1.7 监控体系
业务监控

业务报表: 进件, 授信, 动支, 复借, 应还, 逾期,催收报表

客群稳定性

各环节转化率

拒绝原因

逾期分布

策略监控

策略执行监控报表

规则名中情况报表

单一规则监控报表

热点规则监控报表

特增稳定性监控报表

策略稳定性监控报表

策略区分度监控报表

模型监控

特征稳定性报表

模型稳定性报表

模型区分度报表

# 1.8 风控系统架构
![10a3806d5ad942e1aa24b7684a83352b](https://github.com/user-attachments/assets/4352cf36-45dc-4e2b-aa4e-9e7622f83fca)

 

# 1.9 小结
信贷业务的基本流程：
注册 - 申请 - 审批 - 放贷 - 还款 - 再次申请 - 复贷审批
信贷审批流程
准入策略 - 分群策略 - 反欺诈策略 - 信用风险策略 - 申请评分卡 - 综合决策

參考網站：https://blog.csdn.net/weixin_51385258/article/details/143812360
