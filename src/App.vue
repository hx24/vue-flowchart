<!--
 * @Author: lzp
 * @Date: 2022-06-15 18:09:08
 * @Description: file content
-->
<template>
  <div class="container1">
    <vue-power-tree :data="dataSource" :props="defaultProps" tree-type="org" default-expand-all>
      <template v-slot="{ node, data }">
        <div class="card-container">
          <div class="card-header">
            {{ data.task.taskName }}
          </div>
        </div>
      </template>
    </vue-power-tree>

    <!-- <vue-power-tree :data="data" tree-type="org" default-expand-all>
      <template v-slot:icon-node="slotProps">
        <div></div>
      </template>
    </vue-power-tree> -->
  </div>
</template>
<!-- <template v-slot:icon-node="slotProps">
  <div v-if="slotProps.node.expanded" class="minus">
    -</div>
  <div v-else class="plus">
    +
  </div>
</template> -->
<script lang="ts" setup>
import VuePowerTree from '../packages/index.ts'
// import VuePowerTree from "vue-power-tree"
// import "vue-power-tree/dist/style.css"
import { ref, computed } from 'vue'

interface Tree {
  id?: number,
  label: string
  children?: Tree[]
}

var arr = [
  {
    task: {},
    sonTaskList: [
      {
        task: {},
        sonTaskList: []
      },
      {
        task: {},
        sonTaskList: []
      }
    ]
  }
]

interface Task {
  "id": string | number,
  "taskCode": string,
  "taskName": string,
  "ruleDescription": string,
}

interface TreeNode {
  task?: Task,
  sonTaskList?: TreeNode[],
  expandNode?: Boolean
}

const expanded = ref(false)

const dataSource: TreeNode[] = [
  {
    task: {
      "id": "1",
      "taskCode": "PATROL.enterprise.explosibility",
      "taskName": "企业易爆品查询",
      "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
    },
    sonTaskList: [
      {
        task: {
          "id": "1-1",
          "taskCode": "PATROL.enterprise.explosibility",
          "taskName": "企业易爆品查询",
          "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
        },
        sonTaskList: [
          {
            task: {
              "id": "1-1-1",
              "taskCode": "PATROL.enterprise.explosibility",
              "taskName": "企业易爆品查询",
              "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
            }
          },
          {
            task: {
              "id": "1-1-2",
              "taskCode": "PATROL.enterprise.explosibility",
              "taskName": "企业易爆品查询",
              "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
            }
          },
          {
            task: {
              "id": "1-1-3",
              "taskCode": "PATROL.enterprise.explosibility",
              "taskName": "企业易爆品查询",
              "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
            }
          },
          {
            task: {
              "id": "1-1-4",
              "taskCode": "PATROL.enterprise.explosibility",
              "taskName": "企业易爆品查询",
              "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
            }
          },
        ]
      },
      {
        task: {
          "id": "1-2",
          "taskCode": "PATROL.enterprise.explosibility",
          "taskName": "企业易爆品查询",
          "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
        }
      },
      {
        task: {
          "id": "1-3",
          "taskCode": "PATROL.enterprise.explosibility",
          "taskName": "企业易爆品查询",
          "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
        }
      },
      {
        task: {
          "id": "1-4",
          "taskCode": "PATROL.enterprise.explosibility",
          "taskName": "企业易爆品查询",
          "ruleDescription": "芋道源码,对企业易爆品巡查超过100个",
        }
      },
    ]
  }
]


function getExpandedCount(): number {
  const secondLevel = dataSource[0].son
  return 0
}

const formatedDataSource = computed((): TreeNode[] => {
  if(expanded) return dataSource


  return []
})

console.log(dataSource)


const data: Tree[] = [
  {
    id: 0,
    label: '主活动',
    children: [
      {
        id: 2,
        label: '子活动1',
        children: [
          {
            id: 5,
            label: '客群规则1'
          },
          {
            id: 6,
            label: '客群规则2'
          }

        ]
      },
      {
        id: 3,
        label: '子活动2',
        children: [
          {
            id: 7,
            label: '客群规则3'
          },
          {
            id: 8,
            label: '客群规则4'
          }
        ]
      },
      {
        id: 4,
        label: '子活动3'
      },
      {
        id: 9,
        label: '子活动4'
      }
    ]
  }
]


const defaultProps = {
  children: 'sonTaskList',
  label: 'taskName',
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
  border: 1px solid #D7DAE2;
  overflow: hidden;
  text-align: left;

  .card-header {
    background: #F7F8FB;
    font-size: 18px;
    font-weight: 600;
    color: #323640;
    padding: 24px 32px;
  }
}
</style>