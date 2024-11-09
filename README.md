
本篇参考：[https://help.salesforce.com/s/articleView?id\=sf.data\_sandbox\_selective\_access.htm\&type\=5](https://github.com)


**背景：**最近同事刷新sandbox发现点击create不生效，并且无任何提示（后续可能优化）。


![](https://img2024.cnblogs.com/blog/910966/202411/910966-20241108135306755-320671330.png)


习惯了直接创建或者刷新的老司机们可能看不出来Sandbox Access标红提示来着，恰巧当前的org还没有使用group，所以提了case，然后得到的回复是针对Developer 以及Developer Pro sandbox，最新的release需要选择group才可以创建，这个group的人才可以使用当前的sandbox。 


步骤很简单。


1\. setup 搜索group然后创建一个group，group选择user需要访问当前sandbox的user。


![](https://img2024.cnblogs.com/blog/910966/202411/910966-20241108135831723-788984327.png)


 2\. sandbox 新建或者刷新最后步骤选择需要的group即可。


![](https://img2024.cnblogs.com/blog/910966/202411/910966-20241108140353332-626394337.png)


 问题： 这个变化对我的影响大吗？这个需要确定你当前的sandbox类型以及你的操作，其实最大的变化是针对developer / developer pro的心间sandbox的变化，以下是一览图。




| Sandbox 操作类型 | 访问Sandbox的User Group | 谁可以访问Sandbox | 备注 |
| --- | --- | --- | --- |
| Create(Partial / Full sandbox) | All User | 和production user相同 | Partial 以及full sandbox不严格要求创建group，可以选择All User选项，和未更新前相同 |
| Create(所有类型) | User Group | User Group | 当创建sandbox选择user group时，只有这些user默认active，其他user默认deactive |
| Refresh |  | 和production user相同 | 针对dev以及dev pro sandbox，虽然我们选择了指定的group，但是刷新以后拥有production访问权限的人也可以访问这个sandbox |


 **总结：**篇中主要介绍最新release中的sandbox创建和刷新的变化，虽然官方在 Sandbox Access标住了红色，但是报错信息前端报错导致UI没显示还是不太友好，相信很快就会修复。针对这个变化，其实对于开发人员影响有限，如果遇到同样的情况的小伙伴可以当做一个快速参考即可。篇中错误的地方欢迎指出，有不懂欢迎留言。


 本博客参考[westworld加速](https://tianchuang88.com)。转载请注明出处！
