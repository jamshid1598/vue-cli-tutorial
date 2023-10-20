<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ done: status === 'done' }">
            <slot>modal heading and some text goes here</slot> <!-- text insight slot is default values -->

            <div class="auth_links">
                <slot name="links">auth links goes here</slot> <!-- text insight slot is default values -->
            </div>
        </div>
    </div>
</template>


<script>
export default {
    props: [
        'status',
    ],
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>


<style> /* `scoped` keyword is used for defining this style appleis only for elements of templates in this component  */
.modal {
    width: 400px;
    padding: 20px;
    margin: 200px auto;
    background: white;
    border-radius: 10px;
}

.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
}

.modal h1 { /* `.modal h1 {}` using selector to define exact html element  */
    color: #03cfb4;
    border: none;
    padding: 0;
}

.modal .auth_links {
    text-align: center;
    margin: 30px 0 10px 0;
}

.auth_links a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
}

.modal.done {
    background: crimson;
    color: white;
}

.modal.done h1 {
    color: white;
}

.modal.done .auth_links {
    color: white;
}

.modal.done .auth_links a {
    color: white;
}

</style>
