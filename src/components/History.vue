<template>
    <div class="well">
        <h3>History</h3>
        <ul class="list-group text-left" >
            <li class="list-group-item" v-for="type in historyList" v-bind:key="type">>
                <div>
                  <strong>{{type}} </strong>
                </div>
            </li> 


        </ul>

    </div>
</template>

<script>
export default {
  props : ["historyList"],

}
</script>
