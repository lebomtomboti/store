<template>
    <div>
      projects
        <di v-for="project in projectData()" :key="project.name">
          <h1>{{ project.name}}</h1>
        </di>
    </div>
</template>
<script>
export default {
  methods:{
    projectData(){
      return this.$store.state.projects
    }
  },
  computed:{
   getAboutMe(){
        return this.$store.dispatch('getAboutMe')
    }
  },
  mounted(){
  this.getAboutMe
 },
}
</script>
<style>
    
</style>