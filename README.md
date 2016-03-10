# Heroku Buildpack Tesseract

This package provide a custom Heroku buildpack providing the [Tesseract OCR](https://code.google.com/p/tesseract-ocr/) binary and all the required libraries to Heroku apps. Training data for English, Dutch and Finnish language is provided. 

## Configuration

The first step consists in allowing your Heroku app to use multiple buildpacks. We use the excellent [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) as follows:

1. add a configuration variable as 
    ```
    heroku config:set
    BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi
    ```
	
    or (equivalently) change the default buildpack as   
    ```
    heroku buildpacks:set https://github.com/ddollar/heroku-buildpack-multi
    ```
2. create a file called `.buildpacks` inside your app as  
    ```
    https://github.com/heroku/heroku-buildpack-LANG
    https://github.com/matteotiziano/heroku-buildpack-tesseract
    ```
	
    where `LANG` is the language used by your app (e.g., `ruby`, `python`, or `nodejs`). A complete list of Heroku buildpacks can be found [here](https://devcenter.heroku.com/articles/buildpacks).
