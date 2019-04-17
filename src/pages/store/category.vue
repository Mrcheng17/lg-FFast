
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
      [{name: 'cCode', type: 'number', span: 12, label: '类别编号'}],
      [{name: 'cName', type: 'text', span: 12, label: '类别名称', rules: {required: true}}],
    ]
  };
  /**
   * 表格参数
   */
  const tableOptions = {
    selection: [],
    pageSize: 20,
    labelWidth: 70,
    title: '类别管理',
    permsPrefix: 'category',
    editOptions: tableEditOptions,
    dataUrl: '/admin/category/list',
    createUrl: '/admin/category/create',
    deleteUrl: '/admin/category/delete',
    updateUrl: '/admin/category/update',
    param: {},
    columns: [
      {type: 'selection', width: 60, align: 'center'},
      {key: 'cCode', title: '类别编号', align: 'center'},
      {key: 'cName',title: '类别名称',align: 'center'},
    ],
    searchDynamic: [
      [
        {name: 'cCode', type: 'text', span: 4, label: '类别编号'},
        {name: 'cName', label: '类别名称', span: 4, type: 'text'},
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
