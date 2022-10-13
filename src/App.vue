<!--
 * @Author: lzp
 * @Date: 2022-06-15 18:09:08
 * @Description: file content
-->
<template>
  <div class="container">
    <vue-power-tree :data="dataSource" :props="defaultProps" :expand-on-click-node="false" tree-type="org" default-expand-all @node-expand="onExpand" @node-collapse="onCollapse">
      <template v-slot="{ node, data }">
        <div class="card-container">
          <div class="card-header">
            {{ data.task.taskName }}
          </div>
        </div>
      </template>
      <template v-slot:icon-node="{ node }">
        <div class="expand-icon">
          <div v-if="node.expanded" class="minus">-</div>
          <div v-else class="plus">
            {{ node.childNodes.length }}
          </div>
        </div>
      </template>
    </vue-power-tree>
  </div>
</template>
<script lang="ts" setup>
import VuePowerTree from '../packages/index.ts'

interface Tree {
  id?: number
  label: string
  children?: Tree[]
}

interface Task {
  id: string | number
  taskCode: string
  taskName: string
  ruleDescription: string
}

interface TreeNode {
  task?: Task
  sonTaskList?: TreeNode[]
  expandNode?: Boolean
}

const dataSource: TreeNode[] = [
  {
    task: {
      id: '1',
      taskCode: 'PATROL.enterprise.explosibility',
      taskName: '企业易爆品查询',
      ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
    },
    sonTaskList: [
      {
        task: {
          id: '1-1',
          taskCode: 'PATROL.enterprise.explosibility',
          taskName: '企业易爆品查询',
          ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
        },
        sonTaskList: [
          {
            task: {
              id: '1-1-1',
              taskCode: 'PATROL.enterprise.explosibility',
              taskName: '企业易爆品查询',
              ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
            }
          },
          {
            task: {
              id: '1-1-2',
              taskCode: 'PATROL.enterprise.explosibility',
              taskName: '企业易爆品查询',
              ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
            }
          },
          {
            task: {
              id: '1-1-3',
              taskCode: 'PATROL.enterprise.explosibility',
              taskName: '企业易爆品查询',
              ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
            }
          },
          {
            task: {
              id: '1-1-4',
              taskCode: 'PATROL.enterprise.explosibility',
              taskName: '企业易爆品查询',
              ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
            }
          }
        ]
      },
      {
        task: {
          id: '1-2',
          taskCode: 'PATROL.enterprise.explosibility',
          taskName: '企业易爆品查询',
          ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
        }
      },
      {
        task: {
          id: '1-3',
          taskCode: 'PATROL.enterprise.explosibility',
          taskName: '企业易爆品查询',
          ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
        }
      },
      {
        task: {
          id: '1-4',
          taskCode: 'PATROL.enterprise.explosibility',
          taskName: '企业易爆品查询',
          ruleDescription: '芋道源码,对企业易爆品巡查超过100个'
        }
      }
    ]
  }
]

function onExpand() {
  console.log('onExpand', )
}

function onCollapse() {
  console.log('onCollapse', )
}

const defaultProps = {
  children: 'sonTaskList',
  label: 'taskName'
}
</script>
<style lang="scss">
.container {
  width: 800px;
  border: 1px solid red;
  height: 800px;
  overflow: auto;
}

.card-container {
  width: 388px;
  height: 341px;
  border-radius: 8px;
  border: 1px solid #d7dae2;
  overflow: hidden;
  text-align: left;

  .card-header {
    background: #f7f8fb;
    font-size: 18px;
    font-weight: 600;
    color: #323640;
    padding: 24px 32px;
  }
}
.expand-icon {
  font-size: 12px;
  border: 1px solid #ccc;
  border-radius: 50%;
  width: 20px;
  height: 20px;
  line-height: 20px;
  color: #777;
}
</style>