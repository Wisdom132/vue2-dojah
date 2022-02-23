## Install
`npm i vue2-dojah --save`

## Usage

    <template>
    <div id="app">
    <Vue2Dojah
        AppId="<your appID>"
        PKey="<your pkey>"
        type="<type>" // 'identification', 'verification', 'liveness'
        @onSuccess="dojahSuccess"
        @onClose="dojahClose"
        @onError="dojahError"
        >
        <button>Open Dojah</button>
    </Vue2Dojah>
    </div>
    </template>

    <script>
    import Vue2Dojah from 'vue2-dojah'
    export default {
    name: 'App',
    components: {
        Vue2Dojah,
    },
    methods:{
        dojahSuccess(response) {
        console.log(response)
        },
        dojahClose() {
        alert('this is error')
        console.log('closed')
        },
        dojahError(error) {
        console.log(error)
        }

    }
    }
    </script>
