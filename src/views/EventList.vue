<template>
  <h1>Events for Good</h1>
  <div class="events">
    <img alt="Vue logo" src="../assets/logo.png" />
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/eventService.js";

export default {
  name: "EventList",
  components: {
    EventCard
  },
  created(){
    EventService.getEvents()
    .then( response =>{
      this.events = response.data
    })
    .catch( error =>{
      console.log(error);
    })
  },
  data() {
    return {
      events: null
    };
  }
};
</script>
<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
