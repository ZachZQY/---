# 洗护门店端＆工厂端解决方案文档

## 1. 项目概述

### 1.1 应用场景
- **门店端**：洗护门店日常运营管理
- **工厂端**：洗护工厂衣物处理流程管理

### 1.2 核心价值
- 提升门店运营效率
- 优化工厂生产流程
- 增强客户体验
- 实现数据驱动的精细化运营

## 2. 系统架构设计

### 2.1 技术架构
```
前端层：React/Vue.js + TypeScript
后端层：Node.js/Python + Express/FastAPI
数据库：MySQL + Redis
消息队列：RabbitMQ/Kafka
文件存储：阿里云OSS/腾讯云COS
```

### 2.2 系统模块划分
```
洗护管理系统
├── 门店端模块
│   ├── 数据大盘
│   ├── 衣物下单
│   ├── 验券系统
│   ├── 商品管理
│   ├── 订单管理
│   ├── 财务管理
│   ├── 用户管理
│   └── 营销系统
└── 工厂端模块
    ├── 数据大盘
    └── 衣物订单流转
```

## 3. 门店端功能设计

### 3.1 数据大盘
#### 3.1.1 核心指标
- **订单数据统计**
  - 日/周/月订单量
  - 订单金额统计
  - 订单状态分布
  - 客户复购率
  - 平均客单价

- **衣物状态数据**
  - 各类衣物处理量
  - 处理时效统计
  - 异常订单统计
  - 客户满意度

#### 3.1.2 数据可视化
- 实时数据看板
- 趋势图表分析
- 自定义报表生成
- 数据导出功能（Excel/PDF）

#### 3.1.3 权限控制
- 角色权限管理
- 数据访问控制
- 操作日志记录

### 3.2 衣物下单系统
#### 3.2.1 订单创建流程
```
1. 客户信息录入/选择
2. 衣物信息录入
   - 衣物类型（衣服、鞋子、奢侈品等）
   - 颜色、材质、品牌
   - 特殊要求
3. 洗涤工艺选择
   - 普洗、精洗、干洗等
4. 价格计算
5. 支付方式选择
6. 生成订单
```

#### 3.2.2 硬件集成
- **水洗唛打印机**
  - 自动生成衣物编码
  - 打印衣物标签
  - 标签信息包含：编码、客户信息、洗涤要求

- **小票打印机**
  - 打印订单小票
  - 包含订单详情、价格、取衣时间

### 3.3 验券系统
#### 3.3.1 第三方平台对接
- **美团验券**
  - API接口对接
  - 券码验证
  - 自动核销

- **抖音验券**
  - 扫码验证
  - 券状态检查
  - 自动下单

#### 3.3.2 验券流程
```
1. 扫描券码
2. 验证券有效性
3. 检查使用条件
4. 自动生成订单
5. 核销券码
6. 发送确认信息
```

### 3.4 商品管理
#### 3.4.1 商品分类体系
```
商品分类
├── 衣物类
│   ├── 上衣
│   ├── 裤子
│   ├── 外套
│   └── 内衣
├── 鞋类
│   ├── 运动鞋
│   ├── 皮鞋
│   └── 休闲鞋
└── 奢侈品
    ├── 皮具
    ├── 珠宝
    └── 手表
```

#### 3.4.2 洗涤工艺管理
- 普洗、精洗、干洗
- 特殊处理工艺
- 价格体系配置

### 3.5 订单管理
- 订单状态跟踪
- 订单修改/取消
- 订单查询/筛选
- 批量操作功能

### 3.6 财务管理
- 收入统计
- 成本分析
- 利润报表
- 跨店结算

### 3.7 用户管理
- 客户信息管理
- 会员等级管理
- 消费记录查询
- 客户标签管理

## 4. 工厂端功能设计

### 4.1 数据大盘
#### 4.1.1 工厂运营数据
- 生产订单统计
- 设备利用率
- 人员效率分析
- 质量控制数据

#### 4.1.2 衣物状态跟踪
- 实时状态更新
- 处理进度监控
- 异常预警

### 4.2 衣物订单流转
#### 4.2.1 入场管理
- 衣物接收确认
- 数量核对
- 质量初检

#### 4.2.2 拍照系统
- 衣物拍照存档
- 损坏记录
- 处理前后对比

#### 4.2.3 质检流程
- 洗涤质量检查
- 修复效果评估
- 合格/不合格判定

#### 4.2.4 反洗处理
- 不合格品重新处理
- 特殊要求处理
- 返工记录

## 5. 营销系统设计

### 5.1 会员等级体系
#### 5.1.1 等级定义
```
等级1（充值500元）
- 衣物订单：7折
- 鞋类订单：7折
- 奢侈品：原价

等级2（充值1000元）
- 衣物订单：5折
- 鞋类订单：7折
- 奢侈品：9折
```

#### 5.1.2 升级机制
- 自动升级
- 手动调整
- 等级有效期

### 5.2 营销活动
#### 5.2.1 充值活动
- 充1000赠100
- 阶梯充值奖励
- 限时优惠

#### 5.2.2 兑换券类型
1. **余额兑换券**
   - 有效期设置
   - 使用限制
   - 自动到账

2. **实物兑换券**
   - 商品兑换
   - 库存管理
   - 兑换记录

3. **赠送金额券**
   - 余额卡形式
   - 有效期管理
   - 消费限制

4. **会员等级券**
   - 等级提升
   - 权益变更
   - 有效期设置

### 5.3 跨店结算系统

#### 5.3.1 保证金机制
```
门店保证金设置
- 基础保证金：500元
- 动态调整
- 预警机制
```

#### 5.3.2 结算流程
```
跨店消费流程
1. 客户在A店办卡储值
2. 客户在B店消费
3. 系统自动计算结算金额
4. 从B店保证金扣除
5. 转账给A店
6. 生成结算记录
```

#### 5.3.3 结算比例配置
- 可自定义结算比例
- 不同商品类型不同比例
- 节假日特殊比例

## 6. 数据库设计

### 6.1 核心表结构

#### 6.1.1 用户表（users）
```sql
CREATE TABLE users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    phone VARCHAR(20) UNIQUE,
    member_level INT DEFAULT 1,
    balance DECIMAL(10,2) DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

#### 6.1.2 订单表（orders）
```sql
CREATE TABLE orders (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    order_no VARCHAR(50) UNIQUE NOT NULL,
    user_id BIGINT,
    store_id BIGINT,
    total_amount DECIMAL(10,2),
    discount_amount DECIMAL(10,2),
    final_amount DECIMAL(10,2),
    status ENUM('pending', 'processing', 'completed', 'cancelled'),
    payment_method ENUM('cash', 'card', 'voucher', 'balance'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (store_id) REFERENCES stores(id)
);
```

#### 6.1.3 衣物表（garments）
```sql
CREATE TABLE garments (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    order_id BIGINT,
    garment_code VARCHAR(50) UNIQUE,
    category ENUM('clothing', 'shoes', 'luxury'),
    sub_category VARCHAR(50),
    color VARCHAR(50),
    material VARCHAR(100),
    wash_type ENUM('normal', 'premium', 'dry_clean'),
    price DECIMAL(10,2),
    status ENUM('received', 'processing', 'completed', 'returned'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (order_id) REFERENCES orders(id)
);
```

#### 6.1.4 门店表（stores）
```sql
CREATE TABLE stores (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    address TEXT,
    deposit_balance DECIMAL(10,2) DEFAULT 500,
    settlement_ratio DECIMAL(5,4) DEFAULT 0.8,
    status ENUM('active', 'inactive'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 6.1.5 营销券表（vouchers）
```sql
CREATE TABLE vouchers (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    voucher_code VARCHAR(50) UNIQUE,
    type ENUM('balance', 'goods', 'gift', 'membership'),
    amount DECIMAL(10,2),
    valid_from TIMESTAMP,
    valid_to TIMESTAMP,
    used_at TIMESTAMP NULL,
    user_id BIGINT NULL,
    status ENUM('active', 'used', 'expired'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## 7. 业务流程设计

### 7.1 门店下单流程
```
1. 客户到店
2. 店员录入客户信息
3. 录入衣物信息
4. 选择洗涤工艺
5. 系统计算价格
6. 选择支付方式
7. 生成订单
8. 打印小票和水洗唛
9. 衣物送至工厂
```

### 7.2 验券下单流程
```
1. 客户出示券码
2. 店员扫码验证
3. 系统验证券有效性
4. 自动生成订单
5. 核销券码
6. 打印小票和水洗唛
7. 衣物送至工厂
```

### 7.3 工厂处理流程
```
1. 接收衣物
2. 拍照存档
3. 质量检查
4. 洗涤处理
5. 再次质检
6. 包装整理
7. 返回门店
```

## 8. 系统集成

### 8.1 第三方平台集成
- 美团API对接
- 抖音API对接
- 支付接口集成
- 短信通知服务

### 8.2 硬件设备集成
- 水洗唛打印机
- 小票打印机
- 扫码枪
- 称重设备

## 9. 安全与权限

### 9.1 用户权限管理
- 角色权限配置
- 数据访问控制
- 操作日志记录
- 敏感信息加密

### 9.2 数据安全
- 数据备份策略
- 传输加密
- 存储加密
- 访问审计

## 10. 部署与运维

### 10.1 部署架构
- 负载均衡
- 数据库主从
- 缓存集群
- 文件存储

### 10.2 监控告警
- 系统性能监控
- 业务指标监控
- 异常告警
- 日志分析

## 11. 项目计划

### 11.1 开发阶段
1. **第一阶段**：核心功能开发（8周）
   - 用户管理
   - 订单管理
   - 基础数据统计

2. **第二阶段**：营销系统开发（6周）
   - 会员等级
   - 营销活动
   - 跨店结算

3. **第三阶段**：工厂端开发（4周）
   - 衣物流转
   - 质检流程

4. **第四阶段**：系统集成与测试（4周）
   - 第三方平台对接
   - 硬件设备集成
   - 系统测试

### 11.2 技术栈选择
- 前端：React + TypeScript + Ant Design
- 后端：Node.js + Express + TypeScript
- 数据库：MySQL 8.0
- 缓存：Redis
- 消息队列：RabbitMQ
- 文件存储：阿里云OSS

## 12. 风险评估与应对

### 12.1 技术风险
- 第三方API稳定性
- 硬件设备兼容性
- 数据一致性

### 12.2 业务风险
- 跨店结算复杂性
- 营销活动合规性
- 客户数据安全

### 12.3 应对策略
- 完善的异常处理
- 数据备份机制
- 合规性审查
- 安全审计

## 13. 总结

本解决方案涵盖了洗护门店端和工厂端的完整业务流程，重点解决了数据统计的灵活性、营销系统的可配置性以及跨店结算的自动化问题。系统设计充分考虑了实际业务场景，提供了完整的会员等级体系、营销活动管理和跨店结算机制。

通过模块化设计和灵活的配置系统，可以满足不同门店的个性化需求，同时保证系统的可扩展性和维护性。

### 13.1 核心亮点
1. **灵活的数据统计**：支持自定义报表和权限控制
2. **完善的营销体系**：多层级会员制度和多样化营销活动
3. **自动化跨店结算**：保证金机制解决门店间结算问题
4. **完整的业务流程**：从下单到工厂处理的端到端管理

### 13.2 技术优势
1. **模块化架构**：便于维护和扩展
2. **高可用设计**：支持负载均衡和容灾
3. **安全可靠**：完善的数据安全和权限控制
4. **易于集成**：标准化的API接口和硬件集成方案
