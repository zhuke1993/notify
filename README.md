消息通信中间件

概念：
    1、messageType
        消息名称。消息的最小分类属性，每个消息必须有一个可供订阅和发布的名称，并且在topic内唯一。
        多个同类的messageType可以整合
        
    2、topic
        某一类消息的集合。可以按照业务系统分类，也可以按照消息大类分类。
        一个topic可以包含多个messageType。
        topic必须申请拿到，不允许开发自行创建
        
    3、groupId
        应用ID/集群ID。
        sub/pub模式，同一个group，同一消息只有一台机器能处理。
        广播模式，不同group，同一消息每个group都会有一台机器收到该消息。
    
    4、死信队列
        每个messageType都会有一个DLQ队列，消息消费失败到一定次数怎会进入死信队列

组件：
    sender：支持普通消息发送、消息延迟发送。
    listener：支持单一消息接收，支持单一topic下所有消息接收。
              默认情况下，listener消费异常，MQ会重复发送一次。如果消费不掉，则进入死信队列。
        
    