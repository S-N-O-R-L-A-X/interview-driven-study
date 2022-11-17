<style>
.warning {
  background-color:rgba(239,111,27,0.1);
  border-left:4px solid orange;
}
</style>
# 测试

- [测试](#测试)
  - [测试的重要性](#测试的重要性)
  - [单元测试](#单元测试)
    - [测试框架](#测试框架)
      - [Jest](#jest)
        - [匹配器](#匹配器)
      - [Mocha](#mocha)
      - [Ava](#ava)
      - [Jasmine](#jasmine)
      - [Karma](#karma)
      - [Chai](#chai)
  - [如何对 canvas 做单测](#如何对-canvas-做单测)
  - [控制流测试](#控制流测试)
    - [基路径测试](#基路径测试)
  - [数据流测试](#数据流测试)

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
Jest 基于 Jasmine, 做了大量修改并添加了很多特性，同样开箱即用，但异步测试支持良好。Babel、 TypeScript、 Node、 React、 Angular、 Vue等等都在使用该框架。

##### 匹配器
* toBe() 使用 `Object.is`
* toEqual() 递归地检查每个域的值，适用于比较对象值和数组值
* toBeNull()
* toBeUndefined()
* toBeTruthy()
* toBeFalsy()
* toBeGreaterThan()
* toBeGreaterThanOrEqual()
* toBeLessThan()
* toBeLessThanOrEqual()
* toBeCloseTo() 对于浮点数，使用这个代替toEqual()
* toMatch() 可以用正则表达式匹配字符串
* toContain() 可以用于测试数组或迭代器是否有某个元素
* toThrow() 可以测试抛出的错误，内部可以用字符串，正则表达式，Error做参数

#### Mocha
Mocha 是生态最好，使用最广泛的单测框架，但是他需要较多的配置来实现它的高扩展性。

#### Ava

#### Jasmine
Jasmine 是单测框架的“元老”，开箱即用，但是异步测试支持较弱。

#### Karma

#### Chai
https://www.chaijs.com/
Chai 是一个BDD/TDD的断言库。

reference: https://juejin.cn/post/6844904194600599560

## 如何对 canvas 做单测

## 控制流测试

### 基路径测试
路径是节点的序列。
语句覆盖$\leftrightarrow$覆盖长度为0的边。
判定覆盖$\leftrightarrow$覆盖长度为1的边。

基路径：除了路径开始节点和终止节点以外，其他节点最多出现一次的路径
<blockquote class="warning">注意：基路径不一定是完整路径。</blockquote>


## 数据流测试
