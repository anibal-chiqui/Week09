<template>
    <div>
        <div id="app">

            <!-- DONE show error alert -->
            <div class = "alert alert-danger" v-show="errors.length > 0">
                <li v-for="error in errors">{{error}}</li>
            </div>
            <div class="card add-student m-2 p-2">
                <h4 class="card-title">Add new student</h4>

                <div class="form-group">
                    <label for="name">Name</label>
                    <!-- DONE v-model -->
                    <input id="name" class="form-control" v-model="newStudentName">
                </div>
                <div class="form-group">
                    <label for="starID">Star ID</label>
                    <!-- DONE v-model -->
                    <input id="starID" class="form-control" v-model="newStarID">
                </div>

                <!-- DONE v-on:click event handler -->
                <button class="btn btn-primary" v-on:click="addStudent">Add</button>
            </div>
        </div>
    </div>
</template>

<script>

export  default {
    name: 'NewStudentForm',
    data() {
        return {
            newStudentName: '',
            newStarID: '',
            errors: []
        }
    },
    methods: {
        addStudent() {
            this.errors = []
            if (this.newStudentName && this.newStarID) {
                let student = {name: this.newStudentName, starID: this.newStarID}
                this.$emit('student-added', student)
                this.newStudentName = ''
                this.newStarID = ''
            } else {
                this.errors.push('Name and StarID are both required.')
            }

        }
    }
}

</script>

<style>

</style>