**************************************** Start Gulp *******************************************


1) Download and install node.js  


2) Install Gulp global
npm install --global gulp-cli
or
npm i -g gulp


3) Create a package.json in project directory
npm init


4)Install Gulp in project local
npm i gulp --save-dev


5) Create a gulpfile - gulpfile.js

 ^^^^^^^^^^^ initial gulp in gulpfile.js ^^^^^^^^^
var gulp = require('gulp');



********************************** Gulp Plugins **************************************************


1) gulp-autoprefixer --   npm install --save-dev gulp-autoprefixer 

var autoprefixer = require('gulp-autoprefixer');
gulp.task('default', () =>
    gulp.src('src/app.css')
        .pipe(autoprefixer({
            browsers: ['last 2 versions'],
            cascade: false
        }))
        .pipe(gulp.dest('dist'))
);


2) browsersync --    npm install -g browser-sync

*start browsersync static*                          
                            --   browser-sync start --server --files "css/*.css"

*start browsersync dynamic(Use local server example Open Server)*
                             --   browser-sync start --proxy "myproject.dev" --files "css/*.css"



3) gulp-clean-css --     npm install gulp-clean-css --save-dev

var cleanCSS = require('gulp-clean-css');
gulp.task('minify-css', () => {
  return gulp.src('styles/*.css')
    .pipe(cleanCSS({compatibility: 'ie8'}))
    .pipe(gulp.dest('dist'));
});



4) pump  --     npm install pump

var pump = require('pump');



5) gulp-uglify --   npm install --save-dev gulp-uglify

var gulp = require('gulp');
var uglify = require('gulp-uglify');
var pump = require('pump');
 
gulp.task('compress', function (cb) {
  pump([
        gulp.src('lib/*.js'),
        uglify(),
        gulp.dest('dist')
    ],
    cb
  );
});


6) gulp-sourcemaps --   npm install --save-dev gulp-sourcemaps

var gulp = require('gulp');
var plugin1 = require('gulp-plugin1');
var plugin2 = require('gulp-plugin2');
var sourcemaps = require('gulp-sourcemaps');
 
gulp.task('javascript', function() {
gulp.src(['src/test.js', 'src/testdir/test2.js'], { base: 'src' })
    .pipe(sourcemaps.init())
      .pipe(plugin1())
      .pipe(plugin2())
    .pipe(sourcemaps.write('../maps'))
    .pipe(gulp.dest('dist'));
});
