<template>
  <div class="home">
    <div class="container-editor">
      <h1 class="py-4">Code Editor</h1>
      <select
          v-model="languageId"
          class="form-select"
          style="width: 50%"
          aria-label="Default select example"
          @change="changeLanguage()"
        >
        <option value="70" selected>Python</option>
        <option value="76">C++</option>
        <option value="62">Java</option>
        </select>

      <brace
        style="height: 500px; margin-top: 20px"
        :fontsize="'12px'"
        :theme="'tomorrow'"
        :mode="this.currentLanguage"
        :codefolding="'markbegin'"
        :softwrap="'free'"
        :selectionstyle="'text'"
        :highlightline="true" >
      </brace>
      <button class="btn btn-primary pt-2">
        Run Program
      </button>
    </div>
  </div>
</template>

<script>
import Brace from "vue-bulma-brace";

export default {
  name: "Home",
  data() {
    return {
      currentLanguage: "python",
      languageId: 70,
      languageMap: {
        70: "python",
        76: "cpp",
        62: "java",
      },
    };
  },
  components: {
    Brace,
  },
  methods: {
    evalue_code() {},
    preprocessing_code() {
      this.line_code = this.code.split("\n");
      console.log(this.line_code);
    },
    changeLanguage() {
      console.log("languageId", this.languageId);
      this.requestBody.language_id = this.languageId.toString();
      this.currentLanguage = this.languageMap[this.languageId];
    },
  },
};
</script>
<style lang="scss" scoped>
.container-editor {
  width: 100%;
  max-width: 1000px;
  margin: 0 auto;
}


</style>