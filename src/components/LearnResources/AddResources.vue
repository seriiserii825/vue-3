<template>
    <base-modal title="Error in inputs" v-if="inputIsInvalid" @close="inputIsInvalid = false">
        <template #default>
            <p>Enter in each input some values</p>
        </template>
        <template #actions>
            <base-button @click="confirmError">Ok</base-button>
        </template>
    </base-modal>
    <base-card>
        <form @submit.prevent="addData">
            <div class="form-control">
                <label for="title">Title:</label>
                <input type="text" v-model="inputTitle" name="title" id="title">
            </div>
            <div class="form-control">
                <label for="description">Description:</label>
                <textarea name="description" v-model="inputDesc" id="description"></textarea>
            </div>
            <div class="form-control">
                <label for="link">Link:</label>
                <input type="url" name="link" id="link" v-model="inputLink">
            </div>
            <base-button type="submit">Add resource</base-button>
        </form>
    </base-card>
</template>

<script>
import BaseCard from "@/components/UI/BaseCard";
import BaseModal from "@/components/UI/BaseModal";
import BaseButton from "@/components/UI/BaseButton";

export default {
    inject: ['addResource'],
    emits: ['close'],
    data() {
        return {
            inputTitle: '',
            inputDesc: '',
            inputLink: '',
            inputIsInvalid: false
        }
    },
    methods: {
        addData() {
            const inputTitle = this.inputTitle
            const inputDesc = this.inputDesc
            const inputLink = this.inputLink
            if (inputTitle === '' || inputDesc === '' || inputLink === '') {
                this.inputIsInvalid = true
                return false;
            } else {
                this.addResource(inputTitle, inputDesc, inputLink);
                this.inputTitle = ''
                this.inputDesc = ''
                this.inputLink = ''
            }
        },
        confirmError() {
            this.inputIsInvalid = false
        }
    },
    components: {
        BaseCard,
        BaseModal,
        BaseButton
    }
}
</script>

<style scoped lang="scss">
label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
}

input,
textarea {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px solid #ccc;
}

input:focus,
textarea:focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
}

.form-control {
    margin: 1rem 0;
}
</style>
