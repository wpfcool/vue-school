<template>
  <div class="container">

    <div class="login">
      sdfsdofjsd;fjsdop
    </div>

    <div class="login-dialog">

      <div class="dialog">
        <div>信息验证</div>
        <van-form @submit="onSubmit">
          <van-field readonly
                     label-width='40px'
                     clickable
                     name="city"
                     :value="city"
                     label="城市"
                     placeholder="请选择学校所在地"
                     @click="showCityPicker = true" />

          <van-field readonly
                     label-width='40px'
                     clickable
                     name="school"
                     :value="school"
                     label="学校"
                     placeholder="请选择学校所在地"
                     @click="showSchoolPicker = true" />

          <van-field readonly
                     label-width='40px'
                     clickable
                     name="grade"
                     :value="grade"
                     label="年级"
                     placeholder="请选择年级"
                     @click="showGradePicker = true" />

          <van-field v-model="phone"
                     label-width='40px'
                     type="tel"
                     name="phone"
                     label="手机号"
                     placeholder="请输入手机号"
                     :rules="[{ required: true, message: '请填写手机号' }]" />

          <van-field v-model="sms"
                     label-width='40px'
                     name='sms'
                     center
                     clearable
                     label="验证码"
                     placeholder="请输入验证码">
            <template #button>
              <van-button size="small"
                          type="primary">发送验证码</van-button>
            </template>
          </van-field>

          <van-button class="submit"
                      type="info">验证</van-button>

        </van-form>
      </div>

    </div>

    <van-popup v-model="showCityPicker"
               position="bottom">
      <van-picker show-toolbar
                  :columns="columns"
                  @confirm="onCityConfirm"
                  @cancel="showCityPicker = false" />
    </van-popup>

    <van-popup v-model="showSchoolPicker"
               position="bottom">
      <van-picker show-toolbar
                  :columns="schools"
                  @confirm="onSchoolsConfirm"
                  @cancel="showSchoolPicker = false" />
    </van-popup>

    <van-popup v-model="showGradePicker"
               position="bottom">
      <van-picker show-toolbar
                  :columns="grades"
                  @confirm="onGradeConfirm"
                  @cancel="showGradePicker = false" />
    </van-popup>
  </div>
</template>

<script>
export default {
  data () {
    return {
      city: '',
      school: '',
      grade: '',
      phone: '',
      sms: '',
      columns: ['杭州', '宁波', '温州', '嘉兴', '湖州'],
      showCityPicker: false,

      schools: ['杭州', '宁波d', '温州', '嘉兴', '湖州'],
      showSchoolPicker: false,

      grades: ['杭州', '宁波d', '温州', '嘉兴', '湖州'],
      showGradePicker: false
    }
  },
  components: {

  },
  methods: {
    onSubmit (res) {
      console.log('onSubmit', res)
    },
    onCityConfirm (value) {
      this.showCityPicker = false
      this.city = value
    },
    onSchoolsConfirm (value) {
      console.log('onSchoolsConfirm', value)
      this.showSchoolPicker = false
      this.school = value
    },
    onGradeConfirm (value) {
      this.showGradePicker = false
      this.grade = value
    }
  }
}
</script>

<style>
.container {
  height: 100%;
}
.login {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
}
.login-dialog {
  /* width: 50%; */
  /* height: 200px; */
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  /* transform: translate(-50%,-50%); */
  background: #00000009;
}

.dialog {
  width: 60%;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 10px;
  box-shadow: 5px 5px 5px #f0f0f0;
  border-radius: 5px;
}
.van-field__label {
  width: auto;
  margin-right: 10px;
}
.van-cell {
  padding: 0;
  margin-top: 10px;
  /* margin-right: 10px; */
  border-bottom: 1px solid #f0f0f001;
}
.van-button {
  width: auto;
  padding: 0;
  color: blue;
  background: none;
  border: none;
}

.submit {
  /* width: auto; */
  padding: 5px;
  color: white;
  background: blue;
  border: none;
  width: 100%;
  height: 35px;
  margin-top: 10px;
}
</style>
