<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Note</label>
            <input v-model="text" type="text" name="text" placeholder="Add note...">
        </div>
        <div class="form-control">
            <label>Date & Time</label>
            <input v-model="day" type="text" name="day" placeholder="Add date & time...">
        </div>
        <div class="form-control form-control-check">
            <label>Check</label>
            <input v-model="reminder" type="checkbox" value="reminder">
        </div>
        <input type="submit" value="Save Task" class="btn btn-block">
    </form>
</template>
<script>
export default {
    name: 'AddATask',
    data() {
        return { // bu function orqali inputlarimizni ovoldik (v-model=== orqali)
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();
            if (!this.text) {
                alert('Please, add note! ')
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            this.$emit('add-task', newTask)

            this.text = ''
            this.day = ''
            this.reminder = false

        }


    }
}

</script>

<style scoped>
.add-form {
    margin-bottom: 40px;
}

.form-control {
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>