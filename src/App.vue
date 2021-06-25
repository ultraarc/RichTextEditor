<template>
  <div id="app">
    <h2>富文本编辑器DEMO</h2>
    <ckeditor
      :editor="editor"
      v-model="editorData"
      :config="editorConfig"
      @ready="onReady"
    ></ckeditor>
    <button class="save-button" @click="save">save</button>
  </div>
</template>

<script>
import DecoupledEditor from "@ckeditor/ckeditor5-build-decoupled-document";
// import Font from "@ckeditor/ckeditor5-font/src/font";
// import FontFamily from "@ckeditor/ckeditor5-font/src/fontfamily";

export default {
  name: "App",
  components: {},
  data() {
    return {
      editor: DecoupledEditor,
      editorData: "<p>Content of the editor.</p>",
      editorConfig: {
        ckfinder: {
          uploadUrl: "http://www.mypage.com/api/uploadckeditor",
        },
        toolbar: {
          items: [
            "heading",
            "|",
            "fontSize",
            "fontFamily",
            "fontColor",
            "fontBackgroundColor",
            "imageInsert",
            "|",
            "bold",
            "italic",
            "underline",
            "strikethrough",
            "highlight",
            "removeFormat",
            "|",
            "alignment",
            "|",
            "numberedList",
            "bulletedList",
            "|",
            "indent",
            "outdent",
            "|",
            "todoList",
            "link",
            "blockQuote",
            "imageUpload",
            "insertTable",
            "mediaEmbed",
            "|",
            "undo",
            "redo",
            "CKFinder",
          ],
        },
        language: "cs",
        // image: {
        //   toolbar: [
        //     "imageTextAlternative",
        //     "imageStyle:full",
        //     "imageStyle:side",
        //     "linkImage",
        //   ],
        // },
        table: {
          contentToolbar: ["tableColumn", "tableRow", "mergeTableCells"],
        },
        licenseKey: "",
      },
    };
  },
  methods: {
    save() {
      console.log(this.editorData);
    },

    onReady(editor) {
      // Insert the toolbar before the editable area.
      editor.ui
        .getEditableElement()
        .parentElement.insertBefore(
          editor.ui.view.toolbar.element,
          editor.ui.getEditableElement()
        );
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
