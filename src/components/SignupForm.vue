<template>
    <form @submit.prevent="handleSubmit">
        <label for="email">Email:</label>
        <input type="email" name="email" id="email" required v-model="email">

        <label for="password">Password:</label>
        <input type="password" name="password" id="password" required v-model="password">
        <div v-if="passwordError" class="error">{{  passwordError  }}</div>

        <label for="role">Role:</label>
        <select name="role" id="role" v-model="role" required>
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>

        <label for="skills">Skills:</label>
        <input type="text" name="skills" id="skills" v-model="tempSkill" @keyup="addSkill">
        <div class="add">skills (press comma to add)</div>
        <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkill(skill)">{{  skill  }}</span>
        </div>

        <div class="terms">
            <input type="checkbox" name="terms" id="terms" required v-model="term">
            <label for="terms">Accept terms and conditions</label>
        </div>
        <div class="submit">
            <button>Create an Account</button>
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: 'developer',
            term: false,
            tempSkill: '',
            skills: [],
            passwordError: '',
        }
    },
    methods: {
        addSkill(e) {
            if (e.key === ',' && this.tempSkill) {
                if (this.skills.find(skill => skill === this.tempSkill.slice(0, -1))) {
                    // alert("You add this skill before!");
                    this.tempSkill = "";
                    return;
                }
                this.skills.push(this.tempSkill.slice(0, -1));
                this.tempSkill = "";
            }

        },
        deleteSkill(skillDel) {
            console.log(skillDel);
            this.skills = this.skills.filter((skill) => {
                return skillDel !== skill
            });
        },
        handleSubmit() {
            this.passwordError = this.password.length > 5 ? '' : 'Please enter valid password(more than 5 chars)'
        }
    }
}
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}

label,
.add {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}

input,
select {
    display: block;
    padding: 10px 6px;
    box-sizing: border-box;
    width: 100%;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}

button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}

.submit {
    text-align: center;
}

.error {
    color: red;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}
</style>