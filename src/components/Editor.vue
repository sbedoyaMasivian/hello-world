<!--<template>
	<div id="app">
        <div id="wraper">
            <ckeditor :editor="editor" v-model="editorData" :config="editorConfig" @ready="onReady"></ckeditor>
        </div>
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
                document.getElementById("app").appendChild( editor.ui.view.toolbar.element );
                document.getElementById("app").appendChild( editor.ui.view.editable.element );
			}
		}
	}
</script>-->
<template>
    <div id="app">
        <div class="document-editor">
            <div id="toolbar" class="document-editor__toolbar"></div>
            <div class="document-editor__editable-container">
            <div class="document-editor__editable">
                <ckeditor toolbar-container="#toolbar" :editor="editor" v-model="editorData" @ready="onReady" ></ckeditor>
            </div>
            </div>
        </div>
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
            onReady( editor ) {
                document.getElementById("toolbar").appendChild( editor.ui.view.toolbar.element );
            }
        }
    }
</script>