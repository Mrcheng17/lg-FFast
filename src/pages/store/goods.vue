
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
        {name: 'name', type: 'text', span: 12, label: '商品名称', rules: {required: true}},
        {name: 'merchantCityGoodsNo', type: 'text', span: 12, label: '序列号'} 
      ],
      [{name: 'description', type: 'text', span: 24, label: '商品描述', rules: {required: true}}],
      [
        {name: 'categoryCode', type: 'select', dataUrl: '/admin/category/list', textField: 'cName', valField: 'id', span: 12, label: '商品类别', rules: {required: true}},
        {name: 'brandCode', type: 'select', dataUrl: '/admin/brand/list', textField: 'bName', valField: 'id', span: 12, label: '品牌', rules: {required: true}}
      ],
      [
        {name: 'priceMember', type: 'text', span: 8, label: '会员价', rules: {required: true,}},
        {name: 'priceJifen', type: 'text', span: 8, label: '积分价', rules: {required: true}},
        {name: 'priceSettlement', type: 'text', span: 8, label: '结算价', rules: {required: true}},
      ],
      [
        {name: 'labels1', type: 'text', span: 8, label: '标签1', rules: {required: true}},
        {name: 'labels2', type: 'text', span: 8, label: '标签2', rules: {required: true}},
        {name: 'labels3', type: 'text', span: 8, label: '标签3', rules: {required: true}},
      ],
      [
        {name: 'repertoryNym', type: 'text', span: 12, label: '库存', value: 0, rules: {required: true}},
        {name: 'status', type: 'switch', span: 12, label: '状态', openText:'上架', closeText: '下架', trueValue: 1, falseValue: 0, value: 1, rules: {required: true, type: 'number'}},
      ],
      [
        {name: 'innerSort', type: 'text', span: 24, label: '内部排序', rules: {required: true}},
      ],
      [
        {name: 'frontCover', type: 'imgUpload', label: '封面图', max: 2, rules: {required: true}},
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
      {key: 'name',title: '商品名称',align: 'center'},
      {key: 'id', title: '商品序列号', align: 'center'},
      {key: 'repertoryNym',title: '库存',align: 'center'},
      {key: 'description',title: '商品描述',align: 'center'},
      {key: 'status',title: '商品状态',align: 'center'},
      {key: 'categoryCode',title: '商品类别',align: 'center'},
      {key: 'brandCode',title: '商品品牌',align: 'center'},
      {key: 'priceMember',title: '会员价',align: 'center'},
      {key: 'priceJifen',title: '积分价',align: 'center'},
      {key: 'priceSettlement',title: '结算价',align: 'center'},
      {key: 'labels1',title: '标签1',align: 'center'},
      {key: 'labels2',title: '标签2',align: 'center'},
      {key: 'labels3',title: '标签3',align: 'center'},
    ],
    searchDynamic: [
      [
        {name: 'cCode', type: 'text', span: 4, label: '商品序列号'},
        {name: 'cName', label: '商品名称', span: 4, type: 'text'},
        {name: 'status', label: '商品状态', span: 4, type: 'text'},
        {name: 'description', label: '商品描述', span: 4, type: 'text'},
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
