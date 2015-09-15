# pingo-iron-ajax-localstorage
An element that encapsulates iron-ajax and iron-localstorage into one.  Use ajax to fetch, then store in localstorage for later retrieval.  Cache busting is up to you by what params you pass in.


### Usage
````
>  bower install --save ghstahl/pingo-iron-ajax-localstorage
````

```
<link rel="import" href="../pingo-iron-ajax-localstorage/pingo-iron-ajax-localstorage.html">
<dom-module id="pingo-content-md-loader-iron-ajax-localstorage">
    <template>
        <pingo-iron-ajax-localstorage  
            id="ironAjaxLocalstorage"  
            params="{{params}}"  
            handle-as="text"  
            last-response="{{ajaxResponse}}">  
        </pingo-iron-ajax-localstorage>

        <marked-element id="content"></marked-element>
    </template>
    <script>
        Polymer({
            is: "pingo-pingo-content-md-loader-iron-ajax-localstorage",
            properties: {
                ajaxResponse: {
                    type: Object,
                    observer: 'onAjaxResponse'
                },
                filePath: {
                    type: String,
                    observer: 'loadFile'
                },
                value: {
                    type: Object
                },
                params: {
                    type: Object
                }
            },
            onAjaxResponse: function (path) {
                this.$.content.markdown = path;
            },

            loadFile: function (path) {
                if (this.filePath) {
                    this.$.ironAjaxLocalstorage.dataUrl = this.filePath;
                }
            }
        });
    </script>
</dom-module>
```