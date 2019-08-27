<template>
	<div id="app">
		<ckeditor :editor="editor" v-model="editorData" :config="editorConfig" @ready="onReady"></ckeditor>
	</div>
</template>

<script>
	import DecoupledEditor from '@ckeditor/ckeditor5-build-decoupled-document';
	
	export default {
		name: 'app',
		data() {
			return {
				editor: DecoupledEditor,
				editorData: '<p>Content of the editor.</p>',
				editorConfig: {
				}
			};
		},
		methods: {
			onReady( editor )  {
                document.body.appendChild( editor.ui.view.toolbar.element );
                document.body.appendChild( editor.ui.view.editable.element );
			}
		}
	}
</script>