<template>
  <div>
    <template v-if="total">
      <ul>
        <li v-for="(item, index) in data" :key="index">{{ item.id }}</li>
      </ul>
      <wy-pagination
        :page-number="pageNumber"
        :total="total"
        :page-size="pageSize"
        @change="pageChange"
      >
      </wy-pagination>
    </template>
  </div>
</template>

<script>
import Pagination from '../../../src/Pagination'
export default {
  components: {
    'wy-pagination': Pagination
  },
  data() {
    return {
      pageNumber: 1,
      total: 0,
      pageSize: 3,
      data: []
    }
  },
  mounted() {
    this.getList(this.pageNumber)
  },
  methods: {
    getList(pageNumber) {
      // 应该从接口获得数据，这里使用假数据。获取到的数据是由当前页数和每页的数据条数决定的
      this.total = 24
      this.data = [
        { id: `第${pageNumber}页-${pageNumber * 10}` },
        { id: `第${pageNumber}页-${pageNumber * 10 + 1}` },
        { id: `第${pageNumber}页-${pageNumber * 10 + 2}` }
      ]
    },
    pageChange(pageNumber) {
      this.pageNumber = pageNumber
      this.getList(this.pageNumber)
    }
  }
}
</script>

<style></style>
