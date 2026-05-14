# MoneyTracker 项目开发规范

## 注释规范

- **所有注释必须使用中文**，包括类注释、方法注释、行内注释、TODO 标记等
- 每个类、接口、结构体、枚举的开头必须有中文注释说明其用途
- 每个公共方法/函数必须有中文注释说明功能、参数和返回值
- 复杂逻辑或非显而易见的代码块必须加中文行内注释
- 事件和委托的声明必须有中文注释

## 命名规范

| 类型 | 规范 | 示例 |
|------|------|------|
| 命名空间 | PascalCase | `MoneyTracker.Models` |
| 类 / 结构体 | PascalCase | `TransactionRecord` |
| 接口 | PascalCase，以 I 开头 | `ITransactionService` |
| 方法 / 函数 | PascalCase | `CalculateTotal()` |
| 属性 | PascalCase | `TotalAmount` |
| 事件 | PascalCase | `DataChanged` |
| 私有字段 | _camelCase，下划线开头 | `_transactionList` |
| 局部变量 | camelCase | `totalAmount` |
| 常量 | PascalCase | `MaxItemCount` |
| 枚举成员 | PascalCase | `Income` |
| 异步方法 | PascalCase，以 Async 结尾 | `LoadDataAsync()` |

## C# 版本兼容注释规则

当使用 C# 4.0 中不具备的语法特性时，**必须在该行下方以中文注释形式写出 C# 4.0 的等效实现**。以下是需要标注的常见情况：

| C# 新特性（版本） | 说明 |
|-------------------|------|
| 字符串插值 `$"..."` (C# 6.0) | 注释写出 `string.Format()` 等效写法 |
| 空条件运算符 `?.` / `?[]` (C# 6.0) | 注释写出 `if (obj != null)` 等效写法 |
| 表达式体成员 `=>` (C# 6.0/7.0) | 注释写出完整方法体写法 |
| 模式匹配 `is` / `switch` (C# 7.0+) | 注释写出传统 `as` + `if` 写法 |
| 元组 `(int, string)` (C# 7.0) | 注释写出 `Tuple<T1,T2>` 或 `out` 参数写法 |
| 本地函数 (C# 7.0) | 注释写出私有方法或委托写法 |
| `??=` 空合并赋值 (C# 8.0) | 注释写出 `if (x == null) x = ...` 等效写法 |
| Switch 表达式 (C# 8.0) | 注释写出传统 `switch` 语句写法 |
| `using` 声明 (C# 8.0) | 注释写出 `using` 块写法 |
| `record` (C# 9.0) | 注释写出等效 `class` 写法 |
| `init` 访问器 (C# 9.0) | 注释写出只读属性的等效写法 |
| `new()` 目标类型推断 (C# 9.0) | 注释写出显式类型 `new XXX()` 写法 |
| `global using` (C# 10.0) | 注释写出每个文件的 `using` 声明 |
| 文件范围命名空间 (C# 10.0) | 注释写出传统命名空间块写法 |
| 原始字符串字面量 `"""..."""` (C# 11.0) | 注释写出 `@"..."` 或转义写法 |

## 注释格式示例

```csharp
// 正确示例：
string message = $"总金额：{total}";
// C# 4.0 等效写法：
// string message = string.Format("总金额：{0}", total);

// 错误示例（没有 C# 4.0 注释）：
string message = $"总金额：{total}";
```

## 通用要求

- 优先保持代码简洁清晰，避免过度设计
- 记账数据相关的类型（交易记录、分类等）优先使用类而非结构体
- UI 逻辑放在 `.xaml.cs` 代码后置中，业务逻辑独立成服务类
