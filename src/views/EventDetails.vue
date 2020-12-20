<template>
  <div v-if="event">
    <span></span>
    <h1>Event # {{ this.id }}: {{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
  <div v-else>loading...</div>
</template>

<script>
import EventService from "@/services/eventService";

export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created(){
    EventService.getEvent(this.id )
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