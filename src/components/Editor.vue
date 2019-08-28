<template>
    <div id="app">
        <div class="document-editor">
            <div id="toolbar" class="document-editor__toolbar"></div>
            <div class="document-editor__editable-container">
                <div class="document-editor__editable">
                    <ckeditor toolbar-container="#toolbar" :editor="editor" v-model="editorData" :config ="editorConfig" @ready="onReady" ></ckeditor>
                </div>
            </div>
        </div>
        <h2>Editor data</h2>
        {{ editorData }}
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
                     ckfinder: {
                        // Upload the images to the server using the CKFinder QuickUpload command.
                        uploadUrl: '/ckfinder/core/connector/php/connector.php?command=QuickUpload&type=Images&responseType=json'
                    }
                },              
            };
        },
        methods: {
            onReady( editor ) {
                document.getElementById("toolbar").appendChild( editor.ui.view.toolbar.element );
            }
        }
    }
</script>
<style scoped>

.document-editor {
    border: 1px solid var(--ck-color-base-border);
    border-radius: var(--ck-border-radius);

    /* Set vertical boundaries for the document editor. */
    max-height: 700px;

    /* This element is a flex container for easier rendering. */
    display: flex;
    flex-flow: column nowrap;
}
.document-editor__toolbar {
    /* Make sure the toolbar container is always above the editable. */
    z-index: 1;

    /* Create the illusion of the toolbar floating over the editable. */
    box-shadow: 0 0 5px hsla( 0,0%,0%,.2 );

    /* Use the CKEditor CSS variables to keep the UI consistent. */
    border-bottom: 1px solid var(--ck-color-toolbar-border);
}

/* Adjust the look of the toolbar inside the container. */
.document-editor__toolbar .ck-toolbar {
    border: 0;
    border-radius: 0;
}
.document-editor__editable-container {
    padding: calc( 2 * var(--ck-spacing-large) );
    background: var(--ck-color-base-foreground);

    /* Make it possible to scroll the "page" of the edited content. */
    overflow-y: scroll;
}

.document-editor__editable-container .ck-editor__editable {
    /* Set the dimensions of the "page". */
    width: 15.8cm;
    min-height: 21cm;

    /* Keep the "page" off the boundaries of the container. */
    padding: 1cm 2cm 2cm;

    border: 1px hsl( 0,0%,82.7% ) solid;
    border-radius: var(--ck-border-radius);
    background: white;

    /* The "page" should cast a slight shadow (3D illusion). */
    box-shadow: 0 0 5px hsla( 0,0%,0%,.1 );

    /* Center the "page". */
    margin: 0 auto;
}
</style>

