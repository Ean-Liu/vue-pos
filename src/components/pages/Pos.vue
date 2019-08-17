<template>
  <div class="pos">
    <div>
        <el-row>
            <el-col :span="10" id="order-list">
                订单拦
                <el-tabs>
                    <el-tab-pane label="点餐">
                        点餐
                    </el-tab-pane>
                    <el-tab-pane label="挂单">
                        挂单
                    </el-tab-pane>
                    <el-tab-pane label="外卖">
                        外卖
                    </el-tab-pane>
                </el-tabs>

                <el-table :data="tableData" border show-summary style="width: 100%" >
                    <el-table-column prop="goodsName" label="商品" ></el-table-column>
                    <el-table-column prop="count" label="量" width="50"></el-table-column>
                    <el-table-column prop="price" label="金额" width="70"></el-table-column>
                    <el-table-column  label="操作" width="100" fixed="right">
                        <template scope>
                            <el-button type="text" size="small" >删除</el-button>
                            <el-button type="text" size="small">增加</el-button>
                        </template>
                    </el-table-column>
                </el-table>

                <el-button type="warning" >挂单</el-button>
                <el-button type="danger" >删除</el-button>
                <el-button type="success" >结账</el-button>

            </el-col>
          
            <el-col :span="14">
                <div class="often-goods">
                    <div class="title">常用商品</div>
                    <div class="often-goods-list">
                        <ul>
                            <li>
                                <span>鸡腿堡</span>
                                <span class="o-price">￥12</span>
                            </li>
                        </ul>
                    </div>
                </div>
                
                <div class="goods-type">
                    <el-tabs>
                        <el-tab-pane label="汉堡">
                            汉堡
                        </el-tab-pane>
                        <el-tab-pane label="小食">
                            小食
                        </el-tab-pane>
                        <el-tab-pane label="饮料">
                            饮料
                        </el-tab-pane>
                        <el-tab-pane label="套餐">
                            套餐
                        </el-tab-pane>
                    </el-tabs>
                </div>


                

                <li v-for="g in typeGoods" :key="g.id" class="item-li" @click="addOrderList(g)">
                    <img :src="g.goodsImg" class="item-img"  >
                    <span class="foodName">{{g.goodsName}}</span>
                    <span class="foodPrice">￥{{g.price}}元</span>
                </li>               

            </el-col>
        </el-row>
    </div>
  </div>
</template>
 
<script>
import axios from 'axios'

const oftenGoodsUrl = 'https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/oftenGoods'
const typeGoodsUrl = 'https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/typeGoods'


export default {
  name: 'Pos',

  created() {
    //   axios.get(oftenGoodsUrl).then(response => {
    //     //   console.log('response==',response.data)
    //       this.oftenGoods = response.data
    //   }).catch(e => {
    //       console.log('error',e)
    //   })
  },

  data(){
      return {
        tableData: [
            {
                goodsName: '可口可乐',
                price: 8,
                count:1
            }, 
            {
                goodsName: '香辣鸡腿堡',
                price: 15,
                count:1
            }, 
            {
                goodsName: '爱心薯条',
                price: 8,
                count:1
            }, 
            {
                goodsName: '甜筒',
                price: 8,
                count:1
            }
        ],
        oftenGoods:[
          {
              goodsId:1,
              goodsName:'香辣鸡腿堡',
              price:18
          }, {
              goodsId:2,
              goodsName:'田园鸡腿堡',
              price:15
          }, {
              goodsId:3,
              goodsName:'和风汉堡',
              price:15
          }, {
              goodsId:4,
              goodsName:'快乐全家桶',
              price:80
          }, {
              goodsId:5,
              goodsName:'脆皮炸鸡腿',
              price:10
          }, {
              goodsId:6,
              goodsName:'魔法鸡块',
              price:20
          }, {
              goodsId:7,
              goodsName:'可乐大杯',
              price:10
          }, {
              goodsId:8,
              goodsName:'雪顶咖啡',
              price:18
          }, {
              goodsId:9,
              goodsName:'大块鸡米花',
              price:15
          }, {
              goodsId:20,
              goodsName:'香脆鸡柳',
              price:17
          }
        ],
        typeGoods:[
          {
              goodsId:1,
              goodsImg:"https://images.unsplash.com/photo-1500622944204-b135684e99fd?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&w=1000&q=80",
              goodsName:'香辣鸡腿堡',
              price:18
          }, {
              goodsId:2,
              goodsImg:"https://images.unsplash.com/photo-1500622944204-b135684e99fd?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&w=1000&q=80",
              goodsName:'田园鸡腿堡',
              price:15
          }, {
              goodsId:3,
              goodsImg:"https://images.unsplash.com/photo-1500622944204-b135684e99fd?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&w=1000&q=80",
              goodsName:'和风汉堡',
              price:15
          }, {
              goodsId:4,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'快乐全家桶',
              price:80
          }, {
              goodsId:5,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'脆皮炸鸡腿',
              price:10
          }, {
              goodsId:6,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'魔法鸡块',
              price:20
          }, {
              goodsId:7,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'可乐大杯',
              price:10
          }, {
              goodsId:8,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'雪顶咖啡',
              price:18
          }, {
              goodsId:9,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'大块鸡米花',
              price:15
          }, {
              goodsId:20,
               goodsImg:"https://images.unsplash.com/photo-1441239372925-ac0b51c4c250?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=60",
              goodsName:'香脆鸡柳',
              price:17
          }
        ],
      }
  },
  methods:{
    addOrderList(goods){
        this.totalCount = 0
        this.totalMoney = 0
        let isHave = false 

        for(let i = 0 ; i < this.totalCount.length; i ++){
            if(this.tableData[i].goodsId === goods.goodsId){
                isHave = true 
            }
        }

        if(isHave){
            let arr = this.tableData.filters( o => o.goodsId === goods.goodsId)
            arr[0].count ++ 
        }else {
            let newGoods={
                goodsId:goods.goodsId,
                goodsName:goods.goodsName,
                price:goods.price,
                count:1
            };
            this.tableData.push(newGoods);
        }

        this.tableData.forEach(ele => {
            this.totalCount +=ele.count
            this.totalMoney = this.totalMoney + ele.price * ele.count
        })
    }  

    // deleteGoods(id){
    //     this.tableData = this.tableData.filters( o => o.goodsId !== id)
    // }
  },


  
  

}
</script>
<style scoped>
    .title{
        height: 20px;
        border-bottom: 1px solid #d3dce6;
        background-color: #f9fafc;
        padding: 10px;
    }
    .often-goods-list ul li{
        list-style: none;
        float: left;
        border:1px solid #E5E9F2;
        padding:10px;
        margin:5px;
        background-color:#fff;
   }
  .o-price{
        color:#58B7FF; 
   }


   .cookList li{
       list-style: none;
       width:23%;
       border:1px solid #E5E9F2;
       height: auot;
       overflow: hidden;
       background-color:#fff;
       padding: 2px;
       float:left;
       margin: 2px;
   }
   .cookList li span{
       
        display: block;
        float:left;
   }
   .foodImg{
       width: 100px;
       height: 30px;
   }
   .item-img{
        width: 100px;
        height: 30px;
   }
   .foodName{
       font-size: 18px;
       padding-left: 10px;
       color:brown;
   }
   .foodPrice{
       font-size: 16px;
       padding-left: 10px;
       padding-top:10px;
   }

   .item-li{
       list-style: none;
   }

</style>