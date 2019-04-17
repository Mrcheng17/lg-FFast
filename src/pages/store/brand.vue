
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
      [{name: 'bCode', type: 'number', span: 12, label: '品牌编号'}],
      [{name: 'bName', type: 'text', span: 12, label: '品牌名称', rules: {required: true}}],
    ]
  };
  /**
   * 表格参数
   */
  const tableOptions = {
    selection: [],
    pageSize: 20,
    labelWidth: 70,
    title: '品牌管理',
    permsPrefix: 'brand',
    editOptions: tableEditOptions,
    dataUrl: '/admin/brand/list',
    createUrl: '/admin/brand/create',
    deleteUrl: '/admin/brand/delete',
    updateUrl: '/admin/brand/update',
    param: {},
    columns: [
      {type: 'selection', width: 60, align: 'center'},
      {key: 'bCode', title: '品牌编号', align: 'center'},
      {key: 'bName',title: '品牌名称',align: 'center'},
    ],
    searchDynamic: [
      [
        {name: 'bCode', type: 'text', span: 4, label: '品牌编号'},
        {name: 'bName', label: '品牌名称', span: 4, type: 'text'},
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
