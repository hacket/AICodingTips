# AI 代码调优技巧

## 魔咒 prompt

 Allen_Xuxu 分享了一条对 Vibe coding 非常有效的咒语： `"Do a deep-dive on the code and understand how [insert feature] works. Once you understand it, let me know, and I will provide the task I have for you."`

- **示例**

```
Do a deep-dive on the code and understand how 购物车商品行 works.   
Once you understand it, let me know, and I will provide the task I have for you."  
the task I have for you.
```

## 等待 cursor 生成代码完成通知

等 cursor 改代码的时候，常常不知道它什么时候完成了，看会 B 站，就得滑回去看一下。  
于是乎，想价格 mcp ，让 cursor 完成任务后自动通知。  
一搜索，果然已经有人做了。  

配置好 mcp ，在 cursor rules 里增加一句：  
" 每次你任务执行完成，调用 notify mcp 发送通知 "
