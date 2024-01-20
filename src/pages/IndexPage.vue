<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="name"
<<<<<<< HEAD
        label="ชื่อ-สกุล *"
        hint="ชื่อและนามสกุล"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'กรุณาพิมพ์ชื่อ']"
      />

=======
        label="名字 姓氏"
        hint="名字和姓氏"
        lazy-rules
        :rules="[ val => val && val.length > 0 || '請輸入名字和姓氏。']"
      />
     
>>>>>>> Chinese-lang
      <q-input
        filled
        type="number"
        v-model="age"
<<<<<<< HEAD
        label="อายุ *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'กรุณาใส่อายุ',
          val => val > 0 && val < 100 || 'กรุณาใส่อายุจริง'
=======
        label="你的年齡*"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || '請輸入您的年齡',
          val => val > 0 && val < 100 || '請輸入真實年齡'
>>>>>>> Chinese-lang
        ]"
      />

      <q-toggle v-model="accept" label="ยอมรับ" />

      <div>
        <q-btn label="ยอมรับ" type="submit" color="primary"/>
        <q-btn label="ยกเลิก" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

  </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)
    return {
      name,
      age,
      accept,
      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'คุณจำเป็นต้องยอมรับ'
          })
        }
        else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'ข้อมูลได้รับการยืนยัน'
          })
        }
      },
      onReset () {
        name.value = null
        age.value = null
        accept.value = false
      }
    }
  }
}
</script>