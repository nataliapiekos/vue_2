<template>
<div id="container-fluid">
    <nav class="navbar navbar-dark bg-dark">
      <span class="navbar-text">
        Participants list
      </span>
    </nav>
    <div class="participant-list">
     <h1>List</h1>
    <div v-if="participants.length > 0">
    <div v-for="participant in participants" :key="participant.id">
      {{ participant.name}} {{ participant.lastName}} 
      <button type="submit" class="btn btn-primary" v-on:click.prevent="deleteParticipant(participant)">Delete</button>
      </div>
    </div>
    <div v-else class="alert alert-dark" role="alert">
      No participants yet!
    </div>
    </div>
    <div class="participant-add-form">
      <form>
        <h1>Add participants</h1>
        <div class="form-group">
          <label for="participant-name">Name</label>
          <input class="form-control" id="participant-name" placeholder="Enter name" v-model="newParticipantName">
        </div>
        <div class="form-group">
          <label for="participant-last-name">Last name</label>
          <input class="form-control" id="participant-last-name"  placeholder="Enter last name" v-model="newParticipantLastName">
        </div>
        <button type="submit" class="btn btn-primary" v-on:click.prevent="addParticipant()">Submit</button>
      </form>
      </div>
</div>

</template>

<script>
export default {
  data: function (){
    return {
      participants: [],
      newParticipantName: null,
      newParticipantLastName: null,
    }
  }, 
  methods: {
    addParticipant: function(){
      var newParticipant = { name: this.newParticipantName, lastName: this.newParticipantLastName };
    newParticipant.id = Math.random();
      this.participants.push(newParticipant);
      this.newParticipantName = null;
      this.newParticipantLastName = null;
    },
    deleteParticipant: function(participant){
      this.participants = this.participants.filter((added) => added.id !== participant.id);
    }
  }
}
</script>

<style>
  .container-fluid {
    margin:0;
    padding:0
   }

   .participant-list {
     margin: 1rem;
   }
   .participant-add-form {
     margin: 1rem;
   }

   .participant-add-form h1 {
     background-color: #76A0B0;
     color:white;
     width:50%;
     margin-left: auto; 
     margin-right: auto;
     text-align: center;
     border-radius: 5px;
   }

</style>

