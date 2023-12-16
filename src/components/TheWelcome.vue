<template>
    <div>
        <blocks-tree :data="treeData" :horizontal="treeOrientation=='1'"  :collapsable="true"></blocks-tree>
    </div>
</template>
<script>
import { defineComponent,ref,reactive } from 'vue';

export default defineComponent({

    setup() {

        let selected = ref([]);
        let treeOrientation = ref("0");
        let treeData = reactive({
          'children': [
            {
              'children': [],
              'expand': false,
              'id': 2,
              'label': 'Выручка АМП'
            },
            {
              'children': [
                {
                  'children': [
                    {'children': [
                      {'children': [
                        {'children': [],
                          'expand': false,
                          'id': 16,
                          'label': 'Выручка ОДО На 1 А/М'
                        }],
                        'expand': false,
                        'id': 15,
                        'label': 'ВД ОДО На 1 А/М'
                      }],
                      'expand': false,
                      'id': 11,
                      'label': 'Норма ВД ОДО'
                    },
                    {'children': [],
                      'expand': false,
                      'id': 12,
                      'label': 'Бонусы ОДО'
                    }],
                  'expand': false,
                  'id': 6,
                  'label': 'ВД ОДО Продажа'
                }
              ],
              'expand': false,
              'id': 3,
              'label': 'Выручка ОДО Продажа'
            },
            {
              'children': [
                {
                  'children': [
                    {
                      'children': [],
                      'expand': false,
                      'id': 13,
                      'label': 'Бонусы ФС'
                    },
                    {
                      'children': [],
                      'expand': false,
                      'id': 14,
                      'label': 'Норма ВД ФС'
                    }
                  ],
                  'expand': false,
                  'id': 7,
                  'label': 'ВД ФС'
                }
              ],
              'expand': false,
              'id': 4,
              'label': 'Выручка ФС'
            },
            {
              'children': [
                {
                  'children': [],
                  'expand': false,
                  'id': 8,
                  'label': 'Выручка Марка1'
                },
                {
                  'children': [],
                  'expand': false,
                  'id': 9,
                  'label': 'Выручка Марка3'
                },
                {
                  'children': [],
                  'expand': false,
                  'id': 10,
                  'label': 'Выручка Марка2'
                }
              ],
              'expand': false,
              'id': 5,
              'label': 'Выручка ОПА'
            }
          ],
          'expand': true,
          'id': 1,
          'label': 'Выручка Продажа'
        })

        const toggleSelect = (node, isSelected) => {
          isSelected ? selected.value.push(node.some_id) : selected.value.splice(selected.value.indexOf(node.some_id), 1);
          if(node.children && node.children.length) {
              node.children.forEach(ch=>{
                  toggleSelect(ch,isSelected)
              })
          }
        }

        return {
            treeData,
            selected,
            toggleSelect,
            treeOrientation
        }
    }
})

</script>
