<template>
  <div class="i18n-select">
    <el-select
      :value="value"
      @change="doChangeLanguage"
      placeholder
      size="small"
      style="max-width: 100px"
    >
      <el-option
        :key="language.id"
        :label="language.label"
        :value="language.id"
        v-for="language in languages"
      ></el-option>
    </el-select>
  </div>
</template>

<script>
import { I18nUtil } from '@/shared/i18n/i18n-util';
import { getLanguages, getLanguageCode } from '@/i18n';

export default {
  name: 'app-i18n-select',

  data() {
    return {
      value: getLanguageCode(),
    };
  },

  computed: {
    languages() {
      return getLanguages();
    },
  },

  methods: {
    doChangeLanguage(language) {
      I18nUtil.doChangeLanguage(language);
    },
  },
};
</script>

<style>
.i18n-flags {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  margin-top: 24px;
}

.i18n-flags img {
  margin-right: 8px;
  cursor: pointer;
}
</style>
