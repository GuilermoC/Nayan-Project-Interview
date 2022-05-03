<template>
    <div class="newsletter">
        <div>
            <h2>Can't wait until Black Friday?</h2>
            <div>Sign up to our VIP newsletter and we’ll let you know when our Black Friday pre-sale starts! Plus you’ll always be kept up to date with the latest sales and promotions throughout the year with exclusive access to private sales and special discounts.</div>
            <div class="newsletter__form">
                <div>
                    <label for="email"></label>
                    <input type="email" v-model="form.email" placeholder="Enter your email">
                    <button type="submit" @click="submitEmail()">►</button>
                </div>
                <div class="message" v-if="form.message">{{ form.message }}</div>
            </div>
            
        </div>
    </div>
</template>

<script>
export default {

    data() {
        return {
            form: {
                email: "",
                message: "" // Errormessage
            }
            
        }
    },

    methods: {
        submitEmail() {
            // Check if email is filled in
            if (!this.form.email || !this.form.email.includes("@") || !this.form.email.includes(".") ) { // TODO: improve validation
                return this.form.message = "Valid email required.";
            }
            
            // Assign url and body
            const url = "/api/newsletter";
            const body = JSON.stringify( { "emailAddress": this.form.email } )

            // POST request
            try {
                fetch(url, { 
                    method: 'post', 
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: body 
                })
                    .then( response => response.json() )
                    .then( data => {
                        if (!data.success) {
                            if (!data.errorMessage) return this.form.message = "Something went wrong, try again."; // didnt went through and no error message was provided
                            return this.form.message = data.errorMessage; // didnt went through but with an error message
                        } 
                        return this.form.message = `${this.form.email} added to newsletter.`; // email successfully added
            });
            } catch (error) {
                console.error("Something went wrong, try again.", error);
                return this.form.message = "Something went wrong, try again."; // Something went wrong while requesting
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    @import './Newsletter.scss';
</style>