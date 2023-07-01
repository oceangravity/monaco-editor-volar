<template>
  <div id="app">
    <div id="monaco-editor"></div>
  </div>
</template>

<script setup lang="ts">
import * as monaco from 'monaco-editor-core';

const value = `
function hello() {
  alert('Hello world!')
}
`;

const globalContext = `let b = 10`;

monaco.languages.typescript.typescriptDefaults.addExtraLib(globalContext);

const editor = monaco.editor.create(document.getElementById('monaco-editor'), {
  value,
  language: 'typescript',
  automaticLayout: true,
});

editor.setHiddenAreas([
  new monaco.Range(
    editor.getModel().getLineCount(),
    0,
    editor.getModel().getLineCount(),
    0
  ),
  new monaco.Range(0, 0, 0, 0),
]);
</script>
