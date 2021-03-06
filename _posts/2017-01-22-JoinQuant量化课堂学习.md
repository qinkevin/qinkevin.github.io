---
layout:     post
title:      "JoinQuant量化课堂学习笔记"
subtitle:
date:       2017-1-22 18:00:00
author:     "随机漫步的傻瓜"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 量化投资
---

# JoinQuant量化课堂学习笔记
- 量化选股就是用量化的方法选择确定的投资组合。常用的选股方法有多因子选股、行业轮动选股、趋势跟踪选股等
- 多因子选股采用一系列的因子（比如市盈率、市净率、市销率等）作为选股标准，满足这些因子的股票被买入，不满足的被卖出
- 风格轮动选股是利用市场风格特征进行投资，市场在某个时刻偏好大盘股，某个时刻偏好小盘股，如果发现市场切换偏好的规律，并在风格转换的初期介入，就可能获得较大的收益
- 行业轮动选股是由于经济周期的原因，有些行业启动后会有其他行业跟随启动，通过发现这些跟随规律，我们可以在前者启动后买入后者获得更高的收益，不同的宏观经济阶段和货币政策下，都可能产生不同特征的行业轮动特点
- 资金流动股是利用资金的流向来判断股票走势。如果资金流入，股票应该会上涨，如果资金流出，股票应该下跌。所以根据资金流向就可以构建相应的投资策略
- 动量反转选股方法是利用投资者投资行为特点而构建的投资组合。动量效应就是前一段强势的股票在未来一段时间继续保持强势。在正反馈到达无法持续的阶段，价格就会崩溃回顾，在这样的环境下就会出现反转特征，就是前一段时间弱势的股票，未来一段时间会变强
- 趋势跟踪策略：当股价在出现上涨趋势的时候进行买入，而在出现下降趋势的时候进行卖出，本质上是一种追涨杀跌的策略，很多市场由于羊群效用存在较多的趋势，如果可以控制好亏损时的额度，坚持住对趋势的捕捉，长期下来是可以获得额外收益的
- 量化择时是指采用量化的方式判断买入卖出点。如果判断是上涨，则买入持有；如果判断是下跌，则卖出清仓；如果判断是震荡，则进行高抛低吸
- 仓位管理就是在你决定投资某个股票组合时，决定如何分批入场，又如何止盈止损离场的技术
- 止盈，顾名思义，在获得收益的时候及时卖出，获得盈利；止损，在股票亏损的时候及时卖出股票，避免更大的损失。
- 移动平均线可分为“算术移动平均线”、“加权移动平均线”、“指数平滑移动平均线”三种。
- 算术移动平均线是简单而普遍的移动平均线。平均线是指算术平均数，计算方法为一组数字相加，除以该组数据的组成个数
- 加权移动平均线：加权的原因是基于移动平均线中，最近一日的收盘价对未来价格波动的影响最大，因此赋予它较大的权值
- 指数移动平均（英语：Exponential Moving Average，EMA或EWMA）是以指数式递减加权的移动平均。各数值的加权影响力随时间而指数式递减，越近期的数据加权影响力越重，但较旧的数据也给予一定的加权值
- MACD 是根据移动平均线较易掌握趋势变动的方向之优点所发展出来的，它是利用二条不同速度（一条变动的速率快──短期的移动平均线，另一条较慢──长期的移动平 均线）的指数平滑移动平均线来计算二者之间的差离状况（DIF）作为研判行情的基础，然后再求取其DIF之9日平滑移动平均线，即MACD线。MACD实际就是运用快速与慢速移动平均线聚合与分离的征兆，来研判买进与卖进的时机和讯号。
- MACD图形的计算方法：先利用收盘价的指数移动平均值（12日／26日）计算出差离值（DIF值）；计算出DIF后，会再画一条“讯号线”，通常是DIF的9日指数移动平均值（DEM值，又称MACD值）；接着，将DIF与DEM的差画成“柱形图”（MACD bar / OSC）
- 随机指标(KDJ)一般是根据统计学的原理，通过一个特定的周期（常为9日、9周等）内出现过的最高价、最低价及最后一个计算周期的收盘价及这三者之间的比例关系，来计算最后一个计算周期的未成熟随机值RSV，然后根据平滑移动平均线的方法来计算K值、D值与J值，并绘成曲线图来研判股票走势。
- 随机指标(KDJ)是以最高价、最低价及收盘价为基本数据进行计算，得出的K值、D值和J值分别在指标的坐标上形成的一个点，连接无数个这样的点位，就形成一个完整的、能反映价格波动趋势的KDJ指标。它主要是利用价格波动的真实波幅来反映价格走势的强弱和超买超卖现象，在价格尚未上升或下降之前发出买卖信号的一种技术工具。它在设计过程中主要是研究最高价、最低价和收盘价之间的关系，同时也融合了动量观念、强弱指标和移动平均线的一些优点，因此，能够比较迅速、快捷、直观地研判行情。
- KDJ三条线,J线往上与DK两线形成交叉,为金叉,相反为死叉. 短期的均线向上穿越长期均线叫金叉.反之为死叉.但如果长期均线向下或变缓同时短期均线向上穿越就不能叫金叉.死叉也如此. 在股市中，金叉代表某种指标向上运行并有50%以上概率持续。反之叫死叉。均线和指标都有，金死叉的概念，就是短的和长的相交。其实更简单的方法：你回顾下历史看看，二根线交叉之后，指数向上多的，则代表金叉，向下多的就是死叉。
- 相对强弱指数（RSI）是通过比较一段时期内的平均收盘涨数和平均收盘跌数来分析市场买沽盘的意向和实力，从而作出未来市场的走势
- 能量潮指标（On Balance Volume，OBV）是将股市的人气——成交量与股价的关系数字化、直观化，以股市的成交量变化来衡量股市的推动力，从而研判股价的走势
- 投资中面临着系统性风险（即Beta）和非系统性风险（即Alpha），Alpha是投资者获得与市场波动无关的回报。比如投资者获得了15%的回报，其基准获得了10%的回报，那么Alpha或者价值增值的部分就是5%.Beta（贝塔）表示投资的系统性风险，反映了策略对大盘变化的敏感性。
- Sharpe（夏普比率）表示每承受一单位总风险，会产生多少的超额报酬，可以同时对策略的收益与风险进行综合考虑。
- Sortino（索提诺比率）表示每承担一单位的下行风险，将会获得多少超额回报
- Information Ratio（信息比率）衡量单位超额风险带来的超额收益。信息比率越大，说明该策略单位跟踪误差所获得的超额收益越高，因此，信息比率较大的策略的表现要优于信息比率较低的基准。合理的投资目标应该是在承担适度风险下，尽可能追求高信息比率
- Algorithm Volatility（策略波动率）用来测量策略的风险性，波动越大代表策略风险越高。
- Benchmark Volatility（基准波动率）用来测量基准的风险性，波动越大代表基准风险越高。
- Max Drawdown（最大回撤）描述策略可能出现的最糟糕的情况，最极端可能的亏损情况。
- Downside Risk（下行波动率）和普通收益波动率相比，下行标准差区分了好的和坏的波动。
- 胜率(%)：盈利次数在总交易次数中的占比。
- 日胜率(%)：盈利超过基准的日数在总交易数中的占比。
- 盈亏比：周期盈利亏损的比例。
- 复权就是对股价和成交量进行权息修复，按照股票的实际涨跌绘制股价走势图,并把成交量调整为相同的股本口径
- 上市开放式基金(lof)与交易所交易基金(etf)是一个比较容易混淆的概念。因为他们都具备开放式基金可申购、赎回和份额可在场内交易的特点。实际上两者存在本质区别。ETF指可在交易所交易的基金。ETF通常采用完全被动式管理方法，以拟合某一指数为目标。它为投资者同时提供了交易所交易以及申购、赎回两种交易方式：一方面，与封闭式基金一样，投资者可以在交易所买卖ETF，而且可以像股票一样卖空和进行保证金交易(如果该市场允许股票交易采用这两种形式)；另一方面，与开放式基金一样，投资者可以申购和赎回ETF，但在申购和赎回时，ETF与投资者交换的是基金份额和“一篮子”股票。ETF具有税收优势、成本优势和交易灵活的特点。LOF是对开放式基金交易方式的创新，其更具现实意义的一面在于：一方面，LOF为“封转开”提供技术手段。对于封闭转开放，LOF是个继承了封闭式基金特点，增加投资者退出方式的解决方案，对于封闭式基金采取LOF完成封闭转开放，不仅是基金交易方式的合理转型，也是开放式基金对封闭式基金的合理继承。另一方面，LOF的场内交易减少了赎回压力。此外，LOF为基金公司增加销售渠道，缓解银行的销售瓶颈。
- 融资融券又称“证券信用交易”，是指投资者向证券公司提供担保物，借入资金买入证券或借入证券卖出的行为。包括券商对投资者的融资、融券和金融机构对券商的融资、融券。融资是借钱买证券，证券公司借款给客户购买证券，客户到期偿还本息，客户向证券公司融资买进证券称为“买空”；融券是借证券来卖，然后以证券归还，证券公司出借证券给客户出售，客户到期返还相同种类和数量的证券并支付利息，客户向证券公司融券卖出称为“卖空”
- 市价单: 不论价格, 直接下单, 直到交易全部完成；限价单: 指定一个价格, 买入时不能高于它, 卖出时不能低于它, 如果不满足, 则等待满足后再交易
- 双均线策略:通过建立m天移动平均线，n天移动平均线，则两条均线必有交点。若m>n，n天平均线“上穿越”m天均线则为买入点，反之为卖出点。该策略基于不同天数均线的交叉点，抓住股票的强势和弱势时刻，进行交易
- 海龟交易策略主要捕捉的是趋势，其采用突破法来确定趋势，当价格突破时认为有买入的信号，而随着价格离当初突破的价格越来越远，我们认为趋势成立的概率就越来越高，加仓！在海龟的系统的止盈止损中，实际上就是借助了唐奇安通道。上线=Max（前N个交易日的最高价），下线=Min（前N个交易日的最低价），中线=（上线+下线）/2，每个交易日结束之后更新当天的数据。这里N一般默认取20。那么唐奇安通道就是这个上线和下线所形成的走势区间。所谓的突破，也就是指今日盘中股价高过了上线。
- APT定价理论是CAPM的一个推广，它们都是均衡状态下的模型，不同的是：CAPM把收益单纯的归为市场变化这一个因子引起的。APT把收益归因在不同的因子上面
- 期现套利是指某种期货合约，当期货市场与现货市场在价格上出现差距，从而利用两个市场的价格差距，低买高卖而获利。理论上，期货价格是商品未来的价格，现货价格是商品目前的价格，按照经济学上的同一价格理论，两者间的差距，即“基差”（基差＝现货价格－期货价格）应该等于该商品的持有成本。一旦基差与持有成本偏离较大，就出现了期现套利的机会。其中，期货价格要高出现货价格，并且超过用于交割的各项成本，如运输成本、质检成本、仓储成本、开具发票所增加的成本等等
-  业内常用所谓的“3sigma”原则，也就是先根据因子样本计算出标准差，然后将其中大于u+3sigma的置换为u+3sigma,将小于u-3sigma的置换为u-3sigma,这样做的好处是可以消除因子极值对因子实际效果造成的不必要影响
- 由于原始因子数据是所有行业的，这里可能按照行业分类，对因子进行了行业中性处理
- 配对交易：寻找走势相关且股价相近的一对股票，根据其价格变动买卖
- 动量模型：业绩好的股票会继续保持其上涨的势头，业绩差的股票会保持其下跌的势头
- 构建因子选股的模型需要如下过程：1.大类配置：根据宏观判断市场，进行市场判断（根据不同市场选择不同因子）、资产配置（不同风险性证券的配比选择，不同热度的行业配比选择）和策略选择（市场中性、单边做多等）。2.选股-alpha端：对选股因子进行有效性分析，包括单因子的预测性、尹子健相关性，构建多因子模型使得选股有尽可能高的alpha;3.选股-风险端：对alpha端的多因子模型进行风险评估，根据风险因子优化模型，使模型尽可能达到有效边界；4.择时-买卖时点：对根据因子模型选出的股票进行择时分析，进一步筛选投资组合中的股票及判断作何操作
- 波动率VIX指数是跟踪市场波动性的指数，一般通过标的期权的隐含波动率计算得来，以芝加哥期权交易所的VIX指数为例，如标的期权的隐含波动率较高，则VIX指数相应较高，一般而言，该指数反映出投资者愿意付出多少成本去对冲投资风险。业内认为，当VIX越高时，表示市场参与者预期后市波动程度会更加激励，同时也反映其不安的心里状态；相反，VIX越低时，则反映市场参与者预期后市波动程度会趋于缓和的心态。因此，VIX又被称为投资人恐慌指标                                                 
