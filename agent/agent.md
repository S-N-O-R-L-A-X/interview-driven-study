- [Agent](#agent)
  - [现代agent架构](#现代agent架构)
    - [主流](#主流)
    - [冷门](#冷门)
  - [memory](#memory)
    - [使用方式](#使用方式)


# Agent

## 现代agent架构

### 主流

<table>
  <thead>
    <tr>
      <th>架构类别</th>
      <th>决策风格</th>
      <th>典型应用场景</th>
      <th>架构特点</th>
      <th>优点</th>
			<th>缺点</th>
      <th>常见实现</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ReAct (Reasoning + Action) / 工具调用</td>
      <td>推理-行动紧密交替</td>
      <td>知识问答、自动化任务</td>
      <td>推理-行动-观察 循环，上下文即工作记忆</td>
      <td>推理与执行紧密耦合，每一步根据最新反馈灵活调整</td>
      <td>错误累积与幻觉连锁，上下文窗口消耗极快</td>
      <td>ReAct框架，LangChain工具调用</td>
    </tr>
    <tr>
      <td>Reflexion / 反思型</td>
      <td>事后总结，将失败转化为语义反馈写入长期记忆</td>
      <td>代码生成、数学推理</td>
      <td>执行后反思，自我修正</td>
      <td>学习和改进性能</td>
			<td>反思本身可能出错，依赖明确的成功/失败信号</td>
      <td>Reflexion论文方法</td>
    </tr>
    <tr>
      <td>Plan-Execute</td>
      <td>先计划后执行</td>
      <td>复杂多步问题、机器人任务</td>
      <td>先规划，然后执行计划</td>
      <td>结构化，适合复杂任务</td>
			<td>抗干扰能力差：执行阶段面对意料外的环境变化时，无法灵活调整</td>
      <td>Plan-and-Execute模式</td>
    </tr>
  </tbody>
</table>

### 冷门

<table>
  <thead>
    <tr>
      <th>架构类别</th>
      <th>决策风格</th>
      <th>典型应用场景</th>
      <th>架构特点</th>
      <th>优点</th>
			<th>缺点</th>
      <th>常见实现</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>多 Agent 协作</td>
      <td>分工、辩论、角色扮演</td>
      <td>软件开发、内容生产、复杂模拟</td>
      <td>多个agent分工合作</td>
      <td>并行处理，模拟人类团队</td>
			<td>通信与计算开销巨大，调试与复现极其困难，幻觉扩散与误传</td>
      <td>Multi-Agent Systems，如CrewAI</td>
    </tr>
    <tr>
      <td>CoALA 认知架构 (Cognitive Architectures for Language Agents)</td>
      <td>模块化认知循环</td>
      <td>长期自主 Agent 设计蓝图</td>
      <td>模块化记忆组件，结构化的行动空间，通用的决策循环</td>
      <td>灵活，适用于长期任务</td>
			<td>抽象框架，缺乏具体实现指导</td>
      <td>CoALA框架</td>
    </tr>
    <tr>
      <td>AutoGPT 自主任务拆解</td>
      <td>自动生成与调度子任务</td>
      <td>开放式目标实现、研究助手</td>
      <td>自动拆解任务并调度</td>
      <td>自主性强</td>
			<td>缺乏优先级和收敛判断，长期记忆与状态管理糟糕</td>
      <td>AutoGPT项目</td>
    </tr>
  </tbody>
</table>

## memory

### 使用方式

<table>
  <thead>
    <tr>
      <th>使用方式</th>
      <th>说明</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>作为“上下文”复用</td>
      <td>在每次会话或处理新任务时，Agent首先检索并加载相关记忆至其上下文窗口，作为决策的“前情提要”。这能直接提升对话的连贯性和个性化程度。</td>
    </tr>
    <tr>
      <td>作为“知识”复用</td>
      <td>原始对话被提炼成结构化的知识单元，复用更加精准。例如，AWS的“Solutions Memory”方案，通过构建跨用户共享的“成功案例库”，解决了相似问题答复不一致的痛点，实现了服务知识的标准化复用。</td>
    </tr>
    <tr>
      <td>作为“技能”复用</td>
      <td>Agent不仅能复用“知识”，还能复用“经验”。它通过观察任务执行过程，自动提炼出包含“触发条件→操作序列”的可复用技能模块并存入“技能库”。当类似场景再次出现时，可直接调用该技能，跳过完整的推理过程。这种机制能将重复任务的处理效率提升数倍。</td>
    </tr>
  </tbody>
</table>