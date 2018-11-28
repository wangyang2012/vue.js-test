<template>
    <div class="test">
        <input type="text" v-model="title"><br/>
        <h1>{{title}}</h1>
        <p v-if="showName">{{user.firstName}}</p>
        <p v-else="showName">{{user.lastName}}</p>
        <p v-text="user.firstName"></p>
        <p v-html="title"></p>

        <ul>
            <li v-for="item in  items">{{item.title}}</li>
        </ul>

        <button v-on:click="greet('Hello world')">Say Greeting</button>
        <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">

        <hr/>

        <label>First name: </label><input type="text" v-model="user.firstName">
        <br/>
        <label>Last name: </label><input type="text" v-model="user.lastName">
        <h3>{{fullName}}</h3>
        <h2>{{msg}}</h2>
    </div>
</template>

<script>
    export default {
        name: 'Test',
        props: {
            msg: {
                type: String,
                default: 'Foobar'
            }
        },
        data() {
            return {
                title: '<h1>Hello world</h1>',
                user: {
                    firstName: 'John',
                    lastName: 'Doe'
                },
                showName: true,
                items: [
                    {title: 'Item one'},
                    {title: 'Item two'},
                    {title: 'Item three'}
                ]
            }
        },
        methods: {
            greet: function(greeting) {
                console.log('Hello');
                console.log(greeting);

            },
            pressKey: function(e) {
                console.log(e.target.value);
            },
            enterHit: function() {
                console.log('You hit enter');
            }
        },
        computed: {
            fullName: function() {
                return this.user.firstName + ' ' + this.user.lastName;
            }
        }
    }
</script>

<style scoped></style>