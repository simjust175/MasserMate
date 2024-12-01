<template>
    <v-card class="bg-grey-lighten-3 pa-8 pt-10" width="100%" height="335" rounded-sm>
      <div class="d-flex flex-column">
        <v-form v-model="valid" ref="form">
          <v-text-field
            v-model="amount"
            :success-messages="['Success']"
            label="Amount"
            :rules="amountRules"
            required
          ></v-text-field>
  
          <v-text-field
            v-model="description"
            label="Description(optional)"
          ></v-text-field>
        </v-form>
      </div>
      <template v-slot:actions>
        <v-btn
          :loading="loading"
          class="flex-grow-1 bg-primary"
          height="48"
          variant="tonal"
          @click="load"
        >
          Add {{ inputMethod }}
        </v-btn>
      </template>
    </v-card>
  </template>
  
  <script>
  export default {
    props: {
      inputMethod: String,
    },
    data: () => ({
      valid: false,
      amount: '',
      description: '',
      loading: false,
      amountRules: [
        (value) => {
          if (value) return true;

          return 'Please enter an amount.';
        }, (value)=>{
            if (value.typeOf === Number) return true

            return 'Please enter a valid amount'
        }
      ],
    }),
    methods: {
      load() {
        this.$refs.form.validate();
        if (this.valid) {
          this.loading = true;
          setTimeout(() => (this.loading = false), 3000);
        } else {
          console.log('Form is not valid');
        }
      },
    },
  };
  </script>
  