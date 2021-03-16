# model-driven app的url结构
+ 打开一个model-driven app，url结构如`https://orgf412d127.crm.dynamics.com/main.aspx?appid={appid}&recordSetQueryKey={recordSetQueryKey}&pagetype=entitylist&etn=cr6cb_pet&viewid={viewid}&viewType=1039`
+ url中的etn，是当前的entity name，注意包含prefix。
+ pagetype共两种，列表页是entitylist，详情页是entityrecord
+ sitemap配置的仅是左侧的导航条，手动修改url中的etn，可以查看其他entity