<script>

let person = {
    name:"Robert",
    age:21,
    adddress:{
        country:"Honduras"
    }
}
</script>
{person.adddress.country}
<button on:click={()=>person.adddress.country = "US"}>change name</button>


<style>

</style>