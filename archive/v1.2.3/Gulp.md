Styles and scripts processed by gulp.  
1. All development **dependencies and plugins** listed in file `package.json`. It's **ok to edit this file** when you need any new front plugin/lib or don't need existing.  
2. File `gulpfile.js` contain **gulp tasks**. Usually this file __should be unchanged__ unless you need any custom gulp features.  
3. File `config.js` contain **configs**. This file **MUST be changed** - at least for to setup you own local development domain.
<br><br>



### Code
* json: `package.json` - dev dependencies
* js:
     * `gulpfile.js` - gulp functions
     * `config.js` - configs which used in file just above