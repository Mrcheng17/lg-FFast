
<template>
  <CrudView ref='crudView' :tableOptions='tableOptions'>
  </CrudView>
</template>

<script>

import {CrudView, DataTree} from 'components/';
import utils from '@/utils/common';
  /**
   * 弹出式表单参数
   */
  const tableEditOptions = {
    width: 600,
    labelWidth: 70,
    dynamic: [
      [
        {name: 'name', type: 'text', span: 12, label: '名称', rules: {required: true}},
      ],
      [
        {name: 'name', type: 'text', span: 12, label: '价格', rules: {required: true}},
      ],
      [
        {name: 'name', type: 'text', span: 12, label: '积分数', rules: {required: true}},
      ],
      [
        {name: 'name', type: 'text', span: 12, label: '有效天数', rules: {required: true}},
      ],
      
    ]
  };
  /**
   * 表格参数
   */
  const tableOptions = {
    selection: [],
    pageSize: 20,
    labelWidth: 70,
    title: '商品管理',
    permsPrefix: 'goods',
    editOptions: tableEditOptions,
    dataUrl: '/admin/goods/list',
    createUrl: '/admin/goods/create',
    deleteUrl: '/admin/goods/delete',
    updateUrl: '/admin/goods/update',
    param: {},
    columns: [
      {type: 'selection', width: 60, align: 'center'},
      {key: 'name',title: '名称',align: 'center'},
      {key: 'id', title: '价格', align: 'center'},
      {key: 'repertoryNym',title: '积分数',align: 'center'},
      {key: 'description',title: '有效天数',align: 'center'},
    ],
    searchDynamic: [
      [
        {name: 'cCode', span: 4, label: '名称', type: 'text'},
        {name: 'cName', label: '价格', span: 4, type: 'text'},
        {name: 'status', label: '积分数', span: 4, type: 'text'},
        {name: 'description', label: '有效天数', span: 4, type: 'text'},
      ]
    ]
  };
  
  export default {
    data () {
      return {
        tableOptions,
        editVisible: false,
        editLoading: true,
      };
    },
    components: {CrudView, DataTree},
    methods: {
      
    },
  };
</script>

<style scoped>
  .sd {
    display: block;
  }
</style>
