## 登录业务的相关技术点

- http是无状态的
- 通过cookie在客户端进行记录
- 通过session在服务端记录状态
- 通过token方式维持状态

### 1.1（cookie和session）与token之间如何选择

> 前端和服务器端没有接口问题，接口之间不存在跨域问题（相同的URL），推荐使用cookie和session记录登录状态。反之，像vue这种前端会自动开启一个服务，**与服务器之间存在跨域问题，推荐使用token记录登录状态**