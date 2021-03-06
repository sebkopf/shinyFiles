shinyFiles
==========

This package extends the functionality of shiny by providing an API for client side access to the server file system. As many shiny apps are run locally this is equivalent to accessing the filesystem of the users own computer, without the overhead of copying files to temporary locations that is tied to the use of fileInput().

The package can be installed from CRAN using `install.packages('shinyFiles')`.

Usage
----------
The pacakge is designed to make it extremely easy to implement. A barebone example would be:

In the ui.R file
```R
shinyUI(bootstrapPage(
    shinyFilesButton('files', label='File select', title='Please select a file', multiple=FALSE)
))
```
In the server.R file
```R
shinyServer(function(input, output) {
    shinyFileChoose(input, 'files', root='.', filetypes=c('', '.txt'))
})
```

It is equally simple to implement directly in your custom html file as it only requires a single `<button>` element. The equivalent of the above in raw html would be:
```html
<button id="files" type="button" class="shinyFiles btn" data-title="Please select a file" data-selecttype="single">
    File select
</button>
```

Credit
----------
The file icons used in the file system navigator is taken from FatCows Farm-Fresh Web Icons (http://www.fatcow.com/free-icons)
