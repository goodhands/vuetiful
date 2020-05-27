<template>
    <div>
        <table class="table table-striped">
            <thead>
                <tr>
                    <th v-for="th in this.thead" :key="th"> {{ th }} </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="td in this.rows" :key="td">
                    <td class="py-1" v-for="th in thead" :key="th">
                        {{ td[th] }}
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'Table',
    props:{
        thead:{
            type: Array, //could be objects?
            required: true
        },
        tname:{
            type: String, //name of the table
            required: true
        },
        resourceUrl:{
            type: String,
            required: true,
        }
    },
    data() {
        return {
            rows: [],
        }
    },
    mounted() {
        axios.get(this.resourceUrl)
            .then(response => this.rows = response.data)
            .catch(error =>  console.log(error.data));
    },
}
</script>