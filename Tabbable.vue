<template>
    <div>
        <ul class="nav nav-tabs" id="myTab" role="tablist">
            <li class="nav-item" v-for="links in this.header" :key="links">
                <a class="nav-link" :id="links+'-tab'" data-toggle="tab" :href="'#'+links" role="tab" :aria-controls="links">{{ links }}</a>
            </li>
        </ul>
        <div class="tab-content" id="myTabContent">
            <div class="tab-pane fade show" v-for="(links, index) in this.header" :key="links" :id="links" role="tabpanel" :aria-labelledby="links+'-tab'">
                {{ content[index] }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Tabbable',
    props: {
        header:{
            type: Array,
            required: true,
        },
        content:{
            type: Array,
            required: true,
        }
    },
    mounted() {
        $('#myTab a').on('click', function (e) {
            e.preventDefault()
            $(this).tab('show')
        })
    },
}
</script>