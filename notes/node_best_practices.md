# NodeJS Best Practices

## Practices
- Callback convention
回调函数约定首个参数为Err. Modules should expose an error-first callback interface.
- Always check for errors in callbacks
回调中优先检查错误
- Return on callbacks
回调的同时return
- Use try-catch in sync code only
只有同步执行的代码才能使用try-catch
- Try to avoid this and new
尽量避免使用this和new, node中多使用回调和高阶函数控制流程，容易出现上下文指代问题
- Create small modules
尽量遵循unix设计原则 unix-way
- Use good async patterns
选择顺手的异步模式
- Error handling
错误处理，区分operational errors和programmer errors(bugs)
- 初始化工程使用 npm init
- 指定开始和测试脚本 npm start/test



## Refs
- [Node.js Best Practices - Part1](https://blog.risingstack.com/node-js-best-practices)
- [Node.js Best Practices - Part2](https://blog.risingstack.com/node-js-best-practices-part-2/)
- [1](1)
