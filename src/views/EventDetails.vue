<template>
  <div>
    <span>Event # {{ $route.params.id }}</span>
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "@/services/eventService";

export default {
  data() {
    return {
      event: {  },
    }
  },
  created(){
    EventService.getEvent(this.$route.params.id )
      .then( response =>{
        //console.log(response)
        this.event = response.data
      })
      .catch( error =>{
        console.log(error);
      })

  },
}
</script>