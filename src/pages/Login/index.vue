<template>
  <div class="container">
    <div class="leftPanel">
      <div class="leftTop">
        <div class="brandMark">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <rect width="28" height="28" rx="7" fill="white" fill-opacity="0.15" />
            <path d="M7 14L12 9L17 14L12 19L7 14Z" fill="white" fill-opacity="0.9" />
            <path d="M13 14L18 9L21 12V16L18 19L13 14Z" fill="white" fill-opacity="0.5" />
          </svg>
        </div>
        <span class="brandName">Nexus</span>
      </div>

      <div class="charactersArea">
        <AnimatedCharacters
          :is-typing="isTyping"
          :show-password="showPassword"
          :password-length="passwordValue.length"
          :is-password-guard-mode="isPasswordGuardMode"
        />
      </div>

      <div class="decorBlur1" />
      <div class="decorBlur2" />
      <div class="decorGrid" />
    </div>

    <div class="rightPanel">
      <div class="formWrapper">
        <p class="panelTag">WELCOME BACK</p>
        <div class="mobileLogo">
          <div class="mobileLogoIcon">
            <svg width="20" height="20" viewBox="0 0 28 28" fill="none">
              <path d="M7 14L12 9L17 14L12 19L7 14Z" fill="#1E40AF" fill-opacity="0.9" />
              <path d="M13 14L18 9L21 12V16L18 19L13 14Z" fill="#3B82F6" fill-opacity="0.7" />
            </svg>
          </div>
          <span>Nova Console</span>
        </div>

        <div class="formHeader">
          <h1 class="formTitle">进入 Nova 控制台</h1>
          <p class="formSubtitle">集中管理你的任务、项目与实时状态面板</p>
        </div>

        <a-form
          ref="formRef"
          name="login"
          :model="formState"
          :rules="rules"
          autocomplete="off"
          size="large"
          class="form"
          @finish="handleLogin"
        >
          <div class="fieldLabel">邮箱 / 用户名</div>
          <a-form-item name="username">
            <a-input
              :value="formState.username"
              placeholder="name@example.com"
              @update:value="updateUsername"
              @focus="isTyping = true"
              @blur="isTyping = false"
            >
              <template #prefix>
                <UserOutlined class="prefixIcon" />
              </template>
            </a-input>
          </a-form-item>

          <div class="fieldLabel">访问密钥</div>
          <a-form-item name="password">
            <a-input
              :value="formState.password"
              :type="showPassword ? 'text' : 'password'"
              placeholder="请输入访问密钥"
              @update:value="updatePassword"
              @change="onPasswordChange"
              @click="onPasswordClick"
              @focus="onPasswordFocus"
              @blur="onPasswordBlur"
            >
              <template #prefix>
                <LockOutlined class="prefixIcon" />
              </template>
              <template #suffix>
                <span class="eyeToggle" @click="showPassword = !showPassword">
                  <EyeOutlined v-if="showPassword" />
                  <EyeInvisibleOutlined v-else />
                </span>
              </template>
            </a-input>
          </a-form-item>

          <div v-if="error" class="errorBox">{{ error }}</div>

          <a-form-item :style="{ marginBottom: 0 }">
            <a-button type="primary" html-type="submit" :loading="loading" block class="submitBtn">
              {{ loading ? '安全验证中...' : '进入工作空间' }}
            </a-button>
          </a-form-item>
        </a-form>

        <p class="footerHint">By continuing, you agree to open collaboration and transparent development.</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, reactive, ref } from 'vue';
import { message, type FormInstance } from 'ant-design-vue';
import { EyeInvisibleOutlined, EyeOutlined, LockOutlined, UserOutlined } from '@ant-design/icons-vue';
import AnimatedCharacters from '../../components/AnimatedCharacters.vue';
import './index.css';

async function mockLogin(_values: { username: string; password: string }) {
  await new Promise((resolve) => setTimeout(resolve, 800));
  return { data: { access_token: `mock_token_${Date.now()}` } };
}

const loading = ref(false);
const showPassword = ref(false);
const isTyping = ref(false);
const passwordFocused = ref(false);
const passwordValue = ref('');
const error = ref('');
const formRef = ref<FormInstance>();
const isPasswordGuardMode = computed(() => passwordFocused.value);

const formState = reactive({
  username: '',
  password: '',
});

const rules: Record<string, { required?: boolean; min?: number; message: string; trigger: string }[]> = {
  username: [
    { required: true, message: '请输入邮箱或用户名', trigger: 'blur' },
    { min: 3, message: '用户名长度不能少于3个字符', trigger: 'blur' },
  ],
  password: [
    { required: true, message: '请输入访问密钥', trigger: 'blur' },
    { min: 6, message: '访问密钥长度不能少于6个字符', trigger: 'blur' },
  ],
};

const updateUsername = (v: string) => {
  formState.username = v;
};

const updatePassword = (v: string) => {
  formState.password = v;
  passwordValue.value = v;
};

const onPasswordChange = (e: Event) => {
  const target = e.target as HTMLInputElement | null;
  passwordValue.value = target?.value ?? '';
};

const onPasswordClick = () => {
  passwordFocused.value = true;
};

const onPasswordFocus = () => {
  passwordFocused.value = true;
};

const onPasswordBlur = () => {
  passwordFocused.value = false;
};

const handleLogin = async (values: { username: string; password: string }) => {
  loading.value = true;
  error.value = '';
  try {
    const { data } = await mockLogin(values);
    localStorage.setItem('access_token', data.access_token);
    message.success('登录成功');
    setTimeout(() => {
      window.location.href = '/';
    }, 500);
  } catch {
    error.value = '账号或密码有误，请重新输入';
  } finally {
    loading.value = false;
  }
};
</script>
