<template>
    <form>
        <label for="email">Email:</label>
        <input type="email" name="email" id="email" required v-model="email">

        <label for="password">Password:</label>
        <input type="password" name="password" id="password" required v-model="password">

        <label for="role">Role:</label>
        <input type="email" name="role" id="role" required>

    </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
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

label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}

input {
    display: block;
    padding: 10px 6px;
    box-sizing: border-box;
    width: 100%;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
</style>