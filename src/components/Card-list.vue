<template>
 <div class="card" style="width: 18rem;">
 <h3>{{data.name}}</h3>
   <div class="card-body">
 <h5 class="card-title">{{data.username}}</h5>
  <h5 class="card-title">{{data.email}}</h5>
   </div>
</div>

</template>

<script>
export default {
  props: ['data']
}
</script>