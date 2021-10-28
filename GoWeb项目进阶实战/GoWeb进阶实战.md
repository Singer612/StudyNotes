# 投票功能的实现 - 依赖于Redis

谁（userid）给哪个帖子（postid）投了什么票（赞成还是反对）

* 按发布时间存储帖子的zset

  左侧是贴子id，右侧是时间戳

* 按评分存储帖子的zset

  左侧是评分，右侧是时间戳

  ```go
  KeyPostScoreZSet = "bluebell:post:score"
  ```

  有人用：，有人用/，有人用.，都可以作为分隔符

  redis key尽量使用命名空间的方式，区分不同的key，方便查询和拆分


omitempty ： JSON序列化的时候就如果为空就忽略这个值

基于用户投票的[相关算法](http://www.ruanyifeng.com/blog/algorithm)，推荐阅读

