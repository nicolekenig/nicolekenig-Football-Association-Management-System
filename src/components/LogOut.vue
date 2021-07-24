<template>
    <div>

    </div>
</template>

<script>
    export default {
            name: "LogOut",
            methods: {
            async logut() {
        try { 
                const response = await this.axios.post(
                "http://localhost:3000/logout",
            {
            }
            );
            this.$root.store.logout();
            this.$router.push("/");
        } catch (err) {
            console.log(err.response);
            this.form.submitError = err.response.data.message;
        }
    }  
},

mounted(){
    this.logut();
  } 

};
</script>

<style lang="scss" scoped>

</style>