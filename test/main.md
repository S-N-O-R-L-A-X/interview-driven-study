# HTML

- [HTML](#html)
  - [测试的重要性](#测试的重要性)
  - [单元测试](#单元测试)
    - [测试框架](#测试框架)
      - [Jest](#jest)
      - [Mocha](#mocha)
      - [Ava](#ava)
      - [Jasmine](#jasmine)
      - [Karma](#karma)
  - [如何对 canvas 做单测](#如何对-canvas-做单测)

## 测试的重要性
* 提高代码质量
* 准确定位问题
* 迭代、重构时，对以往功能有很好的检验效果
* 最大程度保证产品符合预期
* 减少回归流程
* 提升开发者信心和安全感

## 单元测试

### 测试框架
<table>
  <th>框架名</th>
  <th>断言</th>
  <th>仿真</th>
  <th>快照</th>
  <th>异步测试</th>
  <tr>
    <td>Mocha</td>
    <td>默认不支持，可配置</td>
    <td>默认不支持，可配置</td>
    <td>默认不支持，可配置</td>
    <td>友好</td>
  </tr>
  <tr>
    <td>Ava</td>
    <td>默认支持</td>
    <td>不支持，需第三方配置</td>
    <td>默认支持</td>
    <td>友好</td>
  </tr>
  <tr>
    <td>Jasmine</td>
    <td>默认支持</td>
    <td>默认支持</td>
    <td>默认支持</td>
    <td>不友好</td>
  </tr>
  <tr>
    <td>Jest</td>
    <td>默认支持</td>
    <td>默认支持</td>
    <td>默认支持</td>
    <td>友好</td>
  </tr>
  <tr>
    <td>Karma</td>
    <td>不支持，需第三方配置</td>
    <td>不支持，需第三方配置</td>
    <td>不支持，需第三方配置</td>
    <td>不支持，需第三方配置</td>
  </tr>
</table>

#### Jest
Jest 基于 Jasmine, 做了大量修改并添加了很多特性，同样开箱即用，但异步测试支持良好。

#### Mocha
Mocha 是生态最好，使用最广泛的单测框架，但是他需要较多的配置来实现它的高扩展性。

#### Ava

#### Jasmine
Jasmine 是单测框架的“元老”，开箱即用，但是异步测试支持较弱。

#### Karma

reference: https://juejin.cn/post/6844904194600599560

## 如何对 canvas 做单测