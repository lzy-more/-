<template>
    <div class="container">
   <p>{{msg}}</p>
    </div>
</template>
<script>

export default {

    data(){
        return{
            msg:'欢迎来到魔兽世界'
        }
    },
    methods: {
        clickHandle(){
            this.msg='点击了我'
        },

    },
}
</script>
<style scoped>

.message{color: brown;padding: 10px;text-align: center;}
.navlink {
  text-decoration: underline;
}

</style>